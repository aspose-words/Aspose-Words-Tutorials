---
category: general
date: 2026-07-16
description: Das cmake‑build‑x64‑Tutorial zeigt, wie man CMake verwendet, um eine
  Visual‑Studio‑2022‑Lösung zu erzeugen und ein VS‑Projekt auf einem 64‑Bit‑Host zu
  bauen. Enthält Schritte zum Festlegen des Quellverzeichnisses.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: de
lastmod: 2026-07-16
og_description: 'cmake build x64 erklärt: Erfahren Sie, wie Sie das Quellverzeichnis
  festlegen, eine Visual‑Studio‑2022‑Lösung generieren und ein VS‑Projekt auf einem
  64‑Bit‑Host kompilieren.'
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: cmake build x64 – Schritt‑für‑Schritt‑Anleitung zum Generieren & Erstellen
  von VS 2022‑Lösungen
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: cmake build x64 tutorial shows how to use CMake to generate a Visual
    Studio 2022 solution and build a VS project on a 64‑bit host. Includes set source
    directory steps.
  headline: cmake build x64 – Complete Guide to Generating and Building VS 2022 Projects
  type: TechArticle
tags:
- cmake
- visual-studio
- x64
- build-automation
title: cmake build x64 – Vollständige Anleitung zum Erzeugen und Erstellen von VS 2022‑Projekten
url: /de/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – Vollständiger Leitfaden zum Erzeugen und Bauen von VS 2022 Projekten

Haben Sie sich jemals gefragt **how to use CMake**, um eine 64‑Bit Visual Studio‑Lösung zu erzeugen, ohne sich die Haare zu raufen? Sie sind nicht allein. In diesem Tutorial führen wir Sie durch einen **cmake build x64**‑Workflow, der das Quellverzeichnis festlegt, den Generator für Visual Studio 2022 ausführt und schließlich das VS‑Projekt baut – alles mit ein paar sauberen Bash‑Befehlen.

Am Ende des Leitfadens haben Sie ein reproduzierbares Skript, das Sie in jedes Repository einfügen können, sowie ein fundiertes Verständnis der zugrunde liegenden Konzepte, sodass Sie es an Ihre eigenen Bedürfnisse anpassen können.

---

## Was Sie lernen werden

- **Set source directory** korrekt setzen, damit CMake weiß, wo Ihre `CMakeLists.txt` liegt.  
- **cmake generate visual studio** – den Visual Studio 2022‑Generator mit den richtigen Host‑ und Architektur‑Flags aufrufen.  
- Führen Sie ein **cmake build x64** der erzeugten Lösung aus, optional mit der Release‑Konfiguration.  
- Verstehen Sie häufige Fallstricke, wenn Sie versuchen, ein **build vs project** auf einer 64‑Bit‑Maschine zu erstellen.  

Keine vorherige CMake‑Magie erforderlich; nur ein Terminal und eine aktuelle Visual‑Studio‑Installation.

---

## Voraussetzungen

| Anforderung | Warum es wichtig ist |
|-------------|----------------------|
| CMake ≥ 3.20 | Unterstützt die für 64‑Bit‑Builds verwendeten Flags `-Thost=` und `-Ax64`. |
| Visual Studio 2022 (Community, Professional, or Enterprise) | Der Generator `Visual Studio 17 2022` verweist auf diese Version. |
| A Bash‑compatible shell (Git Bash, WSL, PowerShell with `bash` alias) | Das untenstehende Skript verwendet Bash‑Syntax zur Klarheit. |
| Source tree containing a valid `CMakeLists.txt` | CMake kann ohne diese Datei keine Lösung erzeugen. |

Falls einer dieser Punkte fehlt, installieren Sie ihn zuerst – CMake von <https://cmake.org/download/> und VS 2022 über den Microsoft‑Installer.

---

## Schritt 1 – Quell‑ und Build‑Verzeichnisse festlegen (`set source directory`)

Bevor Sie CMake aufrufen, müssen Sie ihm **sagen**, wo es nach den Projektdateien suchen soll. Das Hard‑Coden von Pfaden macht das Skript spröde, daher verwenden wir Umgebungsvariablen, die Sie pro Projekt anpassen können.

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **Warum das wichtig ist:**  
> CMake behandelt das *source directory* (`SRC_DIR`) als Wurzel des Projekts. Das *build directory* (`BUILD_DIR`) ist der Ort, an dem alle Zwischendateien, Caches und die finale `.sln` liegen. Durch die Trennung wird verhindert, dass Ihr Quellbaum verschmutzt wird, und das Aufräumen wird trivial (`rm -rf "$BUILD_DIR"`).

Sie können `YOUR_DIRECTORY` durch einen beliebigen absoluten oder relativen Pfad ersetzen; stellen Sie nur sicher, dass der Ordner eine `CMakeLists.txt` enthält.

---

## Schritt 2 – Visual Studio 2022‑Lösung erzeugen (`cmake generate visual studio`)

Jetzt bitten wir CMake, eine VS 2022‑Lösung zu erzeugen, die **x64** anvisiert. Die wichtigsten Flags sind:

- `-G "Visual Studio 17 2022"` – wählt den VS 2022‑Generator aus.  
- `-Thost=x64` – teilt CMake mit, dass der *Host* (die IDE) als 64‑Bit‑Prozess läuft.  
- `-Ax64` – zwingt das erzeugte Projekt, für die x64‑Architektur zu bauen.

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **Was passiert im Hintergrund?**  
> CMake liest `CMakeLists.txt` aus `$SRC_DIR`, löst alle Aufrufe von `add_executable()` und `add_library()` auf und erstellt anschließend eine `.sln`‑Datei sowie eine Reihe von `.vcxproj`‑Dateien in `$BUILD_DIR`. Diese Projektdateien können nun in Visual Studio geöffnet oder über die Befehlszeile gebaut werden.

Wenn Sie den Befehl ausführen und eine lange Liste von Konfigurationsmeldungen sehen, die mit `-- Configuring done` und `-- Generating done` enden, haben Sie erfolgreich einen **cmake generate visual studio**‑Schritt durchgeführt.

---

## Schritt 3 – Die erzeugte Lösung bauen (`cmake build x64`)

Mit der Lösung vorliegen, ist der nächste logische Schritt, sie zu kompilieren. CMake kann den Build für Sie steuern und delegiert dabei im Hintergrund an MSBuild.

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **Warum `--config Release` verwenden?**  
> Visual‑Studio‑Projekte unterstützen mehrere Konfigurationen (Debug, Release, RelWithDebInfo usw.). Die Angabe von `Release` stellt sicher, dass die Binärdateien für die Produktion optimiert sind und dass die resultierende `.exe`‑ oder `.dll`‑Datei im Verzeichnis `Release/` des Build‑Baums liegt.

Wenn Sie lieber einen Debug‑Build möchten, ersetzen Sie `Release` durch `Debug`. Der Befehl funktioniert genauso, was beweist, dass **how to use CMake** für verschiedene Konfigurationen lediglich ein Austausch dieses Flags ist.

---

## Schritt 4 – Build überprüfen (`build vs project` Sanity‑Check)

Eine erfolgreiche Kompilierung sollte Ihnen eine ausführbare Datei oder Bibliothek hinterlassen. Lassen Sie uns prüfen, ob sie existiert:

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **Häufige Fallstricke:**  
> - Wenn Sie nach einer Änderung von `CMakeLists.txt` den Generator‑Schritt vergessen, schlägt diese Prüfung fehl.  
> - Das Mischen von 32‑Bit‑ und 64‑Bit‑Toolchains kann zu Linker‑Fehlern führen; halten Sie `-Ax64` immer konsistent.  
> - Wenn Sie „MSB3073“-Fehler sehen, bedeutet das meist, dass ein Post‑Build‑Schritt (wie das Kopieren von Ressourcen) fehlgeschlagen ist – prüfen Sie die Ausgabe auf Hinweise.

---

## Schritt 5 – Aufräumen und erneut ausführen (Iterieren über ein `cmake build x64`)

Während der Entwicklung müssen Sie häufig von Grund auf neu bauen. Der sauberste Weg ist, den Build‑Ordner zu löschen und neu zu beginnen:

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **Tipp:**  
> Das Hinzufügen von `-DCMAKE_BUILD_TYPE=Release` zum Generator‑Befehl ist für Multi‑Config‑Generatoren wie Visual Studio optional, kann aber praktisch sein, wenn Sie zu einem Single‑Config‑Generator wie Ninja wechseln.

---

## Schritt 6 – Skript erweitern (Erweiterte `cmake generate visual studio`‑Szenarien)

Was, wenn Ihr Projekt in einem Unterverzeichnis liegt oder Sie benutzerdefinierte Definitionen übergeben müssen? CMake ermöglicht dies mit `-D`‑Argumenten:

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

Jetzt wird die erzeugte VS‑Lösung das Makro `MyFeature_ENABLED` definiert haben, und das Install‑Target legt Dateien unter `/opt/myapp` ab. Dies demonstriert die Flexibilität von **how to use CMake** über den grundlegenden Drei‑Schritt‑Ablauf hinaus.

---

## Erwartete Ausgabe

Wenn Sie das komplette Skript von Anfang bis Ende ausführen, sollte das Terminal etwas Ähnliches anzeigen:

```
-- The C compiler identification is MSVC 19.35.31107.0
-- The CXX compiler identification is MSVC 19.35.31107.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
...
-- Configuring done
-- Generating done
-- Build files have been written to: /path/to/Examples/DocsExamples/build
...
[ 50%] Building CXX object CMakeFiles/MyApp.dir/main.cpp.obj
[100%] Linking CXX executable Release/MyApp.exe
✅ Build succeeded! Executable ready at /path/to/Examples/DocsExamples/build/Release/MyApp.exe
```

Falls etwas schiefgeht, gibt CMake Fehlermeldungen aus, die auf die fehlerhafte Zeile in `CMakeLists.txt` oder auf fehlende SDK‑Komponenten hinweisen – ideal für schnelles Debugging.

---

## Fazit

Wir haben alles behandelt, was Sie benötigen, um ein **cmake build x64** durchzuführen: das Festlegen des Quellverzeichnisses, das Aufrufen des **cmake generate visual studio**‑Schritts, das Kompilieren des resultierenden **build vs project** und das Verifizieren der Ausgabe. Das Skript ist kompakt, portabel und bereit für die Integration in CI‑Pipelines oder lokale Entwicklungs‑Workflows.

Als Nächstes könnten Sie erkunden:

- Einbinden der Ausführung von Unit‑Tests mit `ctest`.  
- Wechsel zum Ninja‑Generator für schnellere inkrementelle Builds (`-G Ninja`).  
- Verwendung von CMake‑Presets (`CMakePresets.json`), um die gerade eingegebenen Flags zu speichern.

Fühlen Sie sich frei, zu experimentieren, Dinge zu brechen und dann neu zu bauen – schließlich ist das der schnellste Weg, **how to use CMake** effektiv zu lernen. Viel Spaß beim Bauen!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Tabelle erstellen](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [Tabelle mit Stil erstellen](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [Tabelle mit Rahmen erstellen](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}