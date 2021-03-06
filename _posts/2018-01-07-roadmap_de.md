---
layout: post
title: "Cryptomator Roadmap Early 2018"
date: 2018-01-07
author: Sebastian Stenzel
authorlink: https://github.com/overheadhunter
authorimg: https://avatars0.githubusercontent.com/u/1204330?s=96
tags: [cryptomator, desktop]
stylesheets: ['/css/blog-post.css']

published: true
language: de
---
Da verständlicherweise nicht alle unsere Nutzer alle Entwicklungsaktivitäten auf GitHub verfolgen können, möchte ich an dieser Stelle ein paar Absätze dazu schreiben, welche technischen Neuerungen 2018 bei Cryptomator anstehen und wie sie sich auf die Nutzung auswirken.

### FUSE
Die größte anstehende Änderung ist die Implementierung von FUSE-basierten Laufwerken. Diese wird es _zusätzlich_ zu WebDAV geben und sie werden die neue Standardeinstellung werden. Die [notwendige Bibliothek](https://github.com/cryptomator/fuse-nio-adapter){:target="_blank"} entwicklen wir gerade. Sie basiert auf [jnr-fuse](https://github.com/SerCeMan/jnr-fuse){:target="_blank"}, was bedeutet, dass _FUSE for macOS_ bzw. unter Windows _WinFsp_ installiert sein muss. Der Linux-Kernel unterstützt FUSE out-of-the-box.

Eine große Baustelle ist derzeit noch, wie wir _WinFsp_ bzw. _FUSE for macOS_ im Installer mit einbinden. Erste Testversionen werden daher vmtl. die manuelle Installation genannter Bibliotheken erfordern.

Der Benefit vom Einsatz von FUSE liegt neben Performancesteigerungen (die im derzeitigen Entwicklungsstand für einige Datei-/Verzeichnis-Operationen schon deutlich messbar sind) vor allem in der zu erwartenden Steigerung der Kompatibilität mit Drittanbietersoftware. Probleme im Zusammenhang mit dem WebDAV-Laufwerk gibt es einige, wie sich in [unserer Issue-Liste sehen lässt](https://github.com/cryptomator/cryptomator/issues?q=is%3Aopen+is%3Aissue+label%3Amisc%3Awebdav){:target="_blank"}.

### Java 9
Über die Weihnachtstage habe ich sämtliche Bibliotheken sowie der Desktop-Anwendung kompatibel zu Java 9 gemacht. Unsere [CI-Builds](https://travis-ci.org/cryptomator/){:target="_blank"} laufen jetzt einheitlich mit JDK 9 in Containern. Der Code wird aber weiterhin für ältere Java-Versionen kompiliert, nicht zuletzt weil unsere Android-App darauf angewiesen ist.

Was soll das bringen? Java 9 ist ein Riesenschritt in der Entwicklung der Java-Platform. Neben diversen Bugfixes, von denen Cryptomator-Nutzer direkt profitieren, z.B. der besseren Unterstützung von HiDPI-Displays unter Windows und Linux, gab es massive Refactorings, welche die Grundlage für ein neues Release-Modell der Java-Platform mit neuen [Feature-Releases im Sechs-Monatstakt](https://blogs.oracle.com/java-platform-group/faster-and-easier-use-and-redistribution-of-java-se){:target="_blank"} bildet. Das bedeutet, dass wir zukünftig schneller von neuen Features profitieren können, ohne auf unstabile Testversionen setzen zu müssen.

Die Umstellung auf Java 9 mit Cryptomator 1.4.0 ist aber auch Grundlage für die Nutzung des Java Platform Module Systems ab Cryptomator 1.5.0, wodurch [deutlich kleinere Anwendungen](http://openjdk.java.net/jeps/275){:target="_blank"} gebaut werden können. In einem ersten Test konnte die Größe der Cryptomator-Anwendung für macOS von über 200 MiB (im installierten Zustand) auf ca. 70 MiB reduziert werden.

### IntelliJ
Unsere Build-Platform haben wir von Eclipse auf IntelliJ gewechselt, da die mit JDK 9 kompatiblen Versionen von Eclipse Änderungen am Compiler beinhalten, welche nicht mit dem [von Dagger generierten Code klar kamen](https://github.com/google/dagger/issues/949){:target="_blank"}.

Des Weiteren sind unsere Android-Entwickler ohnehin IntelliJ gewohnt, so dass wir hier unsere Werkzeuge etwas harmonisieren können.

### 64 Bit
Da sowohl WinFsp als auch JDK 9 64 Bit erfordern, wird Cryptomator ab Version 1.4.0 keine 32-Bit-Systeme mehr unterstützen. Dies ist zwar einerseits schade, beschleunigt aber auch den Entwicklungsprozess, da weniger Systeme getestet werden müssen.

Cryptomator 1.3.x wird 100% kompatibel zu 1.4.0 sein. Das heißt, dass Nutzer, die auf 32-Bit-Software angewiesen sind, auch weiterhin Cryptomator-Tresore nutzen können.

---

Fanden Sie diesen Einblick interessant? Sollen wir künftig zu jedem größeren Meilenstein einen Ausblick geben? Gerne würden wir Ihre Meinung in den Kommentaren hören!
