---
layout: post
title: "Cryptomator Roadmap Early 2019"
date: 2019-01-14
author: Sebastian Stenzel
authorlink: https://github.com/overheadhunter
authorimg: https://avatars0.githubusercontent.com/u/1204330?s=96
tags: [cryptomator, desktop]
stylesheets: ['/css/blog-post.css']

published: true
language: de
---
Hey, es ist ein neues Jahr, also kommt hier in alter Tradition unser ~~viertel~~jährlicher :see_no_evil: Blick auf die Roadmap.


### OpenJDK und OpenJFX
Bisher haben wir das Oracle JDK verwendet, da dies die GUI-Bibliothek beinhaltete, die wir für Cryptomator verwendet haben: JavaFX. Ab JDK 11 planen wir die Umstellung auf OpenJDK und OpenJFX. JavaFX wird ohnehin nicht mehr im Oracle JDK enthalten sein und OpenJFX verspricht kürzere Release-Zyklen und wird - wie der Name schon sagt - in einem offenen Prozess entwickelt.

Da wir nicht mehr auf "unfreie" Software angewiesen sind, könnte Cryptomator in Debian-Repos theoretisch von "contrib" auf "main" wechseln. 

Wir hoffen auch, dass das Bauen von Cryptomators einfacher wird, da OpenJFX eine normale Abhängigkeit ist und das Oracle JDK mit enthaltenem JavaFX nicht mehr benötigt wird.


### Symlinks
Wir sind erfolgreich auf FUSE (Linux und macOS) und Dokany (Windows) umgestiegen. Jetzt ist es an der Zeit, die Dateisysteme zu verbessern. Eines der am häufigsten nachgefragten Features ist die Unterstützung von symbolischen Links. Keine Ahnung was das ist? Nicht weiter schlimm. :wink: Für alle, die darauf warten: Wir planen, Symlinks mit einem der kommenden 1.4.x Releases einzuführen.


### UI Redesign
Wir wollen die gesamte Benutzeroberfläche mit Cryptomator 1.5.0 von Grund auf neu gestalten. Um dies zu erreichen, freuen wir über Input aus der Community. Anregungen und Ideen dürfen gerne in unseren [Redesign-Thread](https://community.cryptomator.org/t/ui-redesign-thread/2850) einfließen.