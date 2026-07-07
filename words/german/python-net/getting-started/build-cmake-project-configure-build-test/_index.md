---
category: general
date: 2026-07-06
description: Erstelle ein CMake‑Projekt Schritt für Schritt. Lerne, wie man CMake
  konfiguriert, wie man CMake baut und wie man CTest für zuverlässige Tests ausführt.
draft: false
keywords:
- build cmake project
- how to configure cmake
- how to build cmake
- how to run ctest
- cmake build and test
language: de
og_description: Erstelle CMake-Projekte schnell mit klaren Schritten. Dieser Leitfaden
  zeigt, wie man CMake konfiguriert, wie man CMake baut und wie man CTest ausführt.
og_title: 'CMake‑Projekt erstellen: Konfiguration, Build & Test‑Anleitung'
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Build CMake project step‑by‑step. Learn how to configure CMake, how
    to build CMake, and how to run CTest for reliable testing.
  headline: 'Build CMake Project: Configure, Build & Test'
  type: TechArticle
tags:
- cmake
- ctest
- build-system
title: 'CMake-Projekt erstellen: Konfigurieren, Bauen & Testen'
url: /de/python/getting-started/build-cmake-project-configure-build-test/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# CMake-Projekt bauen: Konfigurieren, Bauen & Testen

Haben Sie sich jemals gefragt, wie man ein **CMake-Projekt baut**, ohne Stunden damit zu verbringen, auf StackOverflow zu suchen? Sie sind nicht allein. Die meisten Entwickler stoßen auf dasselbe Problem, wenn sie von einer einfachen `CMakeLists.txt` zu einer reproduzierbaren Build-Pipeline wechseln.

In diesem Tutorial führen wir Sie durch den gesamten Prozess—*wie man CMake konfiguriert*, *wie man CMake baut* und *wie man CTest ausführt*—so dass Sie am Ende ein sauberes, wiederholbares Build erhalten, das Sie auf jeder Maschine ausführen können. Am Ende haben Sie ein funktionierendes Beispiel, das Sie in Ihr eigenes Repository kopieren‑und‑einfügen können, ohne zusätzliche Skripte.

## Voraussetzungen — Was Sie benötigen, bevor Sie beginnen

- Eine aktuelle CMake-Version (3.20 oder neuer) – ältere Versionen fehlen einige der Flags, die wir verwenden werden.
- Ein von Ihrer Plattform unterstützter C++‑Compiler (gcc, clang, MSVC usw.).
- Ein Terminal oder eine Eingabeaufforderung mit Zugriff auf `cmake` und `ctest`.
- (Optional) Git, um das Beispiel-Repository zu klonen, falls Sie dem genauen Quellcode folgen möchten.

Falls einer davon fehlt, holen Sie ihn sich jetzt; sonst erhalten Sie später „command not found“-Fehler, und das macht keinen Spaß.

## Schritt 1: CMake-Projekt konfigurieren (Release‑Konfiguration)

Das Erste, was Sie tun, wenn Sie *wie man CMake konfiguriert*, ist CMake mitzuteilen, wo der Quellcode liegt und wohin die Build‑Artefakte gehen sollen. Das `-S`‑Flag verweist auf das Quellverzeichnis, `-B` erstellt einen separaten Build‑Ordner, und `-D CMAKE_BUILD_TYPE=Release` erzwingt ein optimiertes Build.

```bash
# Replace YOUR_DIRECTORY with the path to your project root
cmake -S YOUR_DIRECTORY/Examples/DocsExamples \
      -B YOUR_DIRECTORY/Examples/DocsExamples/build \
      -D CMAKE_BUILD_TYPE=Release
```

**Warum das wichtig ist:** Das Trennen von Quell- und Build‑Dateien (`out‑of‑source`‑Builds) verhindert versehentliche Änderungen am Quellcode und macht das spätere Aufräumen des Build‑Verzeichnisses trivial. Das `Release`‑Flag weist den Compiler außerdem an, Optimierungen zu aktivieren, was Sie normalerweise für ein finales Binary wollen.

> **Pro‑Tipp:** Wenn Sie ein Debug‑Build zur Fehlersuche benötigen, tauschen Sie einfach `Release` gegen `Debug` aus. Der gleiche Befehl funktioniert – CMake kümmert sich um den Rest.

## Schritt 2: Konfiguriertes Projekt bauen

Da der Konfigurationsschritt nun alle notwendigen Makefiles oder Visual‑Studio‑Projektdateien erzeugt hat, können Sie den Code tatsächlich kompilieren. Die Option `--build` abstrahiert das zugrunde liegende Build‑Tool (`make`, `ninja`, `MSBuild` usw.), sodass derselbe Befehl unter Linux, macOS und Windows funktioniert.

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build
```

**Was im Hintergrund passiert:** CMake liest die im vorherigen Schritt erstellte `CMakeCache.txt`, bestimmt das passende Build‑Tool und ruft es mit den richtigen Flags auf. Das ist das Kernstück von *wie man CMake baut* – Sie müssen sich nicht merken, ob Sie `make` oder `ninja` verwenden; CMake erledigt das für Sie.

Wenn Sie auf Mehrkern‑Maschinen Zeit sparen möchten, fügen Sie nach dem Befehl `-- -j$(nproc)` (Linux/macOS) oder `-- /m` (Windows) hinzu:

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build -- -j$(nproc)
```

## Schritt 3: Beispieltests mit detaillierter Ausgabe ausführen

Testing ist der Moment, in dem sich die Theorie in die Praxis verwandelt. CMake liefert `ctest` mit, einen Test‑Treiber, der jeden über `add_test()` in Ihrer `CMakeLists.txt` hinzugefügten Test entdecken und ausführen kann. Um die Tests auszuführen und eine ausführliche Ausgabe zu sehen, verwenden Sie den Helfer `-E chdir`, um zuerst in das Build‑Verzeichnis zu wechseln:

```bash
cmake -E chdir YOUR_DIRECTORY/Examples/DocsExamples/build \
      ctest --verbose
```

**Warum `--verbose` verwenden?** Es gibt die Befehlszeile jedes Tests, den Rückgabecode und jede Ausgabe aus, die der Test selbst erzeugt. Das ist entscheidend, wenn Sie *wie man CTest ausführt* lernen, weil es genau zeigt, was im Hintergrund passiert.

Typische Ausgabe sieht so aus:

```
Test project /path/to/DocsExamples/build
    Start 1: MyFirstTest
1/1 Test #1: MyFirstTest .......................   Passed    0.02 sec

100% tests passed, 0 tests failed
```

Falls ein Test fehlschlägt, enthält das ausführliche Protokoll den fehlgeschlagenen Befehl und alle Fehlermeldungen, was das Debuggen deutlich beschleunigt.

## Schritt 4: Den gesamten Workflow automatisieren (Optional)

Für viele Projekte möchten Sie einen Einzeiler, der konfiguriert, baut und testet. Das können Sie mit einem einfachen Bash‑ (oder PowerShell‑)Skript erreichen:

```bash
#!/usr/bin/env bash
SRC=YOUR_DIRECTORY/Examples/DocsExamples
BUILD=$SRC/build

# 1️⃣ Configure
cmake -S "$SRC" -B "$BUILD" -D CMAKE_BUILD_TYPE=Release

# 2️⃣ Build
cmake --build "$BUILD" -- -j$(nproc)

# 3️⃣ Test
cmake -E chdir "$BUILD" ctest --verbose
```

Speichern Sie es als `run_all.sh`, machen Sie es ausführbar (`chmod +x run_all.sh`) und Sie haben eine reproduzierbare **cmake build and test**‑Pipeline, die Sie in jedes CI‑System einbinden können (GitHub Actions, GitLab CI, Azure Pipelines, wie Sie möchten).

## Randfälle & häufige Stolperfallen

| Situation | Worauf zu achten ist | Lösung |
|-----------|----------------------|--------|
| **Fehlender Compiler** | CMake bricht ab mit „No CMAKE_CXX_COMPILER could be found.“ | Installieren Sie einen Compiler (`sudo apt install build-essential` unter Ubuntu, `xcode-select --install` unter macOS). |
| **Out‑of‑source‑Ordner existiert bereits** | CMake kann die Neukonfiguration verweigern, wenn der Ordner veraltete Dateien enthält. | Löschen Sie das `build`‑Verzeichnis (`rm -rf build`) oder führen Sie `cmake --fresh` aus (CMake 3.24+). |
| **CTest findet keine Tests** | `add_test()` wurde nie aufgerufen oder die Test‑Executable konnte nicht kompiliert werden. | Stellen Sie sicher, dass `add_test(NAME MyTest COMMAND MyTestExe)` in `CMakeLists.txt` vorkommt und dass das Ziel gebaut wird. |
| **Parallele Builds kollidieren bei benutzerdefinierten Befehlen** | Einige benutzerdefinierte Befehle sind nicht als `DEPENDS` markiert, was zu nichtdeterministischen Fehlern führt. | Fügen Sie korrekte `add_custom_command(... DEPENDS ...)`‑Einträge hinzu. |

Das Verständnis dieser Nuancen macht den Unterschied zwischen einem wackeligen Build und einer soliden CI‑Pipeline.

## Visuelle Übersicht (Alt‑Text enthält das Haupt‑Keyword)

![Diagramm, das den Ablauf von Konfiguration, Build und Test eines CMake-Projekts zeigt](/images/cmake-workflow.png "Build CMake Project Workflow-Diagramm")

## Rückblick – Was Sie gelernt haben

Wir begannen mit der Kernfrage: *wie man ein CMake‑Projekt von Grund auf baut*. Am Ende wissen Sie nun, wie man **CMake konfiguriert** mit einem sauberen Out‑of‑Source‑Build, **CMake baut** mit dem universellen `--build`‑Flag und **CTest ausführt** mit ausführlicher Ausgabe, um alles zu verifizieren. Sie haben außerdem ein sofort einsetzbares Skript, das die drei Schritte verbindet und Ihnen einen vollständigen **cmake build and test**‑Workflow liefert.

## Was kommt als Nächstes?

- **Coverage‑Berichterstellung hinzufügen** – `gcov` oder `llvm-cov` integrieren und CTest die Ergebnisse veröffentlichen lassen.
- **Cross‑Compilation** – `-DCMAKE_TOOLCHAIN_FILE` erkunden, um für Embedded‑Geräte zu bauen.
- **Paket-Erstellung** – `cpack` verwenden, um Ihre Binaries für die Verteilung zu bündeln.
- **CI‑Integration** – das Skript in einen GitHub‑Actions‑Workflow kopieren und beobachten, wie die Automatisierung bei jedem Pull‑Request läuft.

Fühlen Sie sich frei, mit verschiedenen Build‑Typen zu experimentieren, weitere Tests hinzuzufügen oder den Beispiel‑Quellcode durch Ihr eigenes Projekt zu ersetzen. Die heute vorgestellten Muster gelten für jede CMake‑basierte Codebasis, egal ob es sich um ein kleines Hilfsprogramm oder ein riesiges Multi‑Modul‑System handelt.

Viel Spaß beim Bauen, und möge Ihr CMake‑Build immer reproduzierbar sein!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man LaTeX aus Word exportiert – Schritt‑für‑Schritt‑Anleitung](/words/english/net/basic-conversions/how-to-export-latex-from-word-step-by-step-guide/)
- [Wie man Markdown aus DOCX speichert – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [Wie man die Aspose.Words‑Version in Python und .NET anzeigt : Eine Schritt‑für‑Schritt‑Anleitung](/words/english/python-net/document-properties-metadata/display-aspose-words-version-python-net/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}