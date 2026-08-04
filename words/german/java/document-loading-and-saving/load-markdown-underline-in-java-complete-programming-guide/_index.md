---
category: general
date: 2026-08-04
description: Lade Markdown‑Unterstreichungen in Java und bewahre die Markdown‑Formatierung
  beim Laden von Markdown in ein Dokument. Befolge dieses Schritt‑für‑Schritt‑Tutorial.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load markdown underline
- load markdown into document
- preserve markdown formatting
language: de
lastmod: 2026-08-04
og_description: Lade Markdown‑Unterstreichungen in Java und bewahre die Markdown‑Formatierung.
  Erfahre, wie du Markdown mit voller Unterstreichungsunterstützung in ein Dokument
  lädst.
og_image_alt: Diagram showing load markdown underline process
og_title: Markdown‑Unterstreichung in Java laden – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  headline: Load markdown underline in Java – complete programming guide
  type: TechArticle
- description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  name: Load markdown underline in Java – complete programming guide
  steps:
  - name: Create `LoadOptions` for the document
    text: '`LoadOptions` lets you customize how the library parses the source file.
      Creating a fresh instance gives you a clean slate for later settings.'
  - name: Enable detection of underline formatting while loading
    text: By default the viewer may ignore underline tags because they are less common
      in Markdown. Enabling this flag tells the parser to keep underline spans intact.
  - name: Load the Markdown file using the configured options
    text: Now you can load the file. Pass the `loadOptions` object to the `Document`
      constructor so the parser respects the underline flag.
  - name: Verify that underline formatting is preserved
    text: A quick sanity check helps you confirm that **preserve markdown formatting**
      worked. The following snippet prints the text of each paragraph and marks underlined
      fragments with a tilde (`~`) for visibility.
  type: HowTo
tags:
- markdown
- Java
- document-processing
title: Markdown‑Unterstreichung in Java laden – vollständiger Programmierleitfaden
url: /de/java/document-loading-and-saving/load-markdown-underline-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Markdown‑Unterstreichungen in Java laden – vollständiger Programmierleitfaden

Wenn Sie **load markdown underline** benötigen, während Sie eine Markdown‑Datei in ein `Document`‑Objekt konvertieren, zeigt Ihnen dieser Leitfaden genau, wie Sie das tun. Sie lernen außerdem, wie Sie **load markdown into document** ohne Verlust von Unterstreichungsformatierungen durchführen, sodass die ursprüngliche Markdown‑Formatierung vollständig erhalten bleibt.

Das Tutorial deckt alles ab, was Sie wissen müssen: erforderliche Bibliotheken, jeden Konfigurationsschritt und wie Sie überprüfen können, dass die Unterstreichungsformatierung den Import überlebt hat. Am Ende haben Sie ein wiederverwendbares Code‑Snippet, das Sie in jedes Java‑Projekt einbinden können.

## Voraussetzungen

- Java 17 oder höher installiert (das Beispiel verwendet das moderne Modulsystem)
- Die neueste Version von **GroupDocs.Viewer** (oder eine kompatible Bibliothek, die `LoadOptions` und `Document` bereitstellt)
- Eine Markdown‑Datei (`sample.md`), die unterstrichenen Text enthält, z. B. `<u>underlined</u>` oder die GitHub‑flavored Syntax `__underlined__`
- Eine IDE wie IntelliJ IDEA oder VS Code, obwohl jeder Texteditor funktioniert

Diese Voraussetzungen stellen sicher, dass der Code ohne zusätzliche Konfiguration ausgeführt werden kann.

## Markdown‑Unterstreichungen laden – Schritt‑für‑Schritt‑Anleitung

Der Prozess besteht aus drei Kernaktionen: Erstellen einer `LoadOptions`‑Instanz, Aktivieren der Unterstreichungserkennung und schließlich Laden der Markdown‑Datei mit diesen Optionen. Jeder Schritt wird nachfolgend erläutert.

### Schritt 1: `LoadOptions` für das Dokument erstellen

`LoadOptions` ermöglicht es Ihnen, anzupassen, wie die Bibliothek die Quelldatei analysiert. Das Erstellen einer neuen Instanz gibt Ihnen eine saubere Basis für spätere Einstellungen.

```java
import com.groupdocs.viewer.options.LoadOptions;

// Step 1: Create load options for the document
LoadOptions loadOptions = new LoadOptions();
```

Das `LoadOptions`‑Objekt ist der Einstiegspunkt für alle importbezogenen Anpassungen. Sie werden es im nächsten Schritt verwenden, um die Unterstreichungserkennung zu aktivieren.

### Schritt 2: Erkennung der Unterstreichungsformatierung beim Laden aktivieren

Standardmäßig kann der Viewer Unterstreichungs‑Tags ignorieren, da sie in Markdown weniger verbreitet sind. Das Aktivieren dieses Flags weist den Parser an, Unterstreichungs‑Spans unverändert zu behalten.

```java
// Step 2: Enable detection of underline formatting while loading
loadOptions.setImportUnderlineFormatting(true);
```

Durch das Setzen von `setImportUnderlineFormatting(true)` wird sichergestellt, dass jedes `<u>`‑HTML‑Tag oder die GitHub‑flavored Unterstreichungssyntax in das `Document`‑Modell als Unterstreichungsstil übersetzt wird. Dies ist die zentrale Aktion, die **load markdown underline** wie erwartet funktionieren lässt.

### Schritt 3: Die Markdown‑Datei mit den konfigurierten Optionen laden

Jetzt können Sie die Datei laden. Übergeben Sie das `loadOptions`‑Objekt dem `Document`‑Konstruktor, damit der Parser das Unterstreichungs‑Flag berücksichtigt.

```java
import com.groupdocs.viewer.Document;

// Step 3: Load the Markdown file using the configured options
Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);
```

Wenn der Konstruktor abgeschlossen ist, enthält `markdownDoc` eine vollständige In‑Memory‑Repräsentation der Markdown‑Quelle, einschließlich aller Unterstreichungs‑Abschnitte.

### Schritt 4: Überprüfen, dass die Unterstreichungsformatierung erhalten bleibt

Ein kurzer Plausibilitäts‑Check hilft Ihnen zu bestätigen, dass **preserve markdown formatting** funktioniert hat. Das folgende Snippet gibt den Text jedes Absatzes aus und markiert unterstrichene Fragmente mit einer Tilde (`~`) zur Sichtbarmachung.

```java
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;

for (Page page : markdownDoc.getPages()) {
    for (Paragraph paragraph : page.getParagraphs()) {
        StringBuilder line = new StringBuilder();
        for (TextFragment fragment : paragraph.getTextFragments()) {
            if (fragment.isUnderline()) {
                line.append("~").append(fragment.getText()).append("~");
            } else {
                line.append(fragment.getText());
            }
        }
        System.out.println(line.toString());
    }
}
```

**Erwartete Ausgabe** (angenommen, `sample.md` enthält `This is __underlined__ text`):

```
This is ~underlined~ text
```

Die Tilden zeigen, dass der Unterstreichungsstil den Import überlebt hat, was bestätigt, dass die **load markdown into document**‑Operation die ursprüngliche Formatierung erhalten hat.

## Häufige Fallstricke und wie man sie vermeidet

| Symptom | Ursache | Lösung |
|---|---|---|
| Unterstreichung verschwindet nach dem Laden | `setImportUnderlineFormatting` blieb auf dem Standardwert `false` | Stellen Sie sicher, dass Sie `loadOptions.setImportUnderlineFormatting(true)` aufrufen, bevor Sie das `Document` erstellen. |
| Nur ein Teil des Textes ist unterstrichen | Gemischte Markdown‑Syntax (z. B. HTML `<u>` gemischt mit `__underline__`) | Die Bibliothek unterstützt beides; prüfen Sie, dass die Quelldatei ein konsistentes Unterstreichungs‑Marker verwendet. |
| Dokument lässt sich nicht laden | Falscher Dateipfad oder fehlende Bibliotheksabhängigkeiten | Verwenden Sie einen absoluten Pfad oder platzieren Sie `sample.md` relativ zum Arbeitsverzeichnis; fügen Sie die Viewer‑JARs dem Klassenpfad hinzu. |

**Pro‑Tipp:** Wenn Sie zusätzlich fette oder kursive Stile beibehalten müssen, aktivieren Sie sie mit `setImportBoldFormatting(true)` bzw. `setImportItalicFormatting(true)`. Das Kombinieren dieser Flags liefert Ihnen einen vollständig getreuen Import der meisten gängigen Markdown‑Stile.

## Vollständiges ausführbares Beispiel

Nachfolgend finden Sie ein eigenständiges Java‑Programm, das alles zusammenführt. Kopieren Sie den Code in eine Datei namens `LoadMarkdownUnderlineDemo.java`, passen Sie den Dateipfad an und führen Sie ihn mit `java LoadMarkdownUnderlineDemo` aus.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;
import com.groupdocs.viewer.options.LoadOptions;

public class LoadMarkdownUnderlineDemo {

    public static void main(String[] args) {
        // 1️⃣ Create load options
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Enable underline detection
        loadOptions.setImportUnderlineFormatting(true);

        // 3️⃣ Load the Markdown file
        Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);

        // 4️⃣ Print each paragraph, marking underlined text with ~
        for (Page page : markdownDoc.getPages()) {
            for (Paragraph paragraph : page.getParagraphs()) {
                StringBuilder line = new StringBuilder();
                for (TextFragment fragment : paragraph.getTextFragments()) {
                    if (fragment.isUnderline()) {
                        line.append("~").append(fragment.getText()).append("~");
                    } else {
                        line.append(fragment.getText());
                    }
                }
                System.out.println(line.toString());
            }
        }
    }
}
```

Beim Ausführen des Programms wird der Dokumentinhalt mit Unterstreichungs‑Markierungen ausgegeben, was beweist, dass die **load markdown underline**‑Funktion funktioniert und dass Sie **preserve markdown formatting** über die gesamte Import‑Pipeline hinweg beibehalten können.

## Fazit

Sie wissen jetzt, wie Sie **load markdown underline** in Java **laden**, wie Sie **load markdown into document** durchführen, während Sie die ursprüngliche Formatierung beibehalten, und wie Sie überprüfen, dass die Unterstreichungsformatierung intakt ist. Dieser Ansatz funktioniert mit den neuesten GroupDocs.Viewer‑Versionen und kann erweitert werden, um zusätzliche Markdown‑Funktionen wie Fett, Kursiv und Tabellen zu unterstützen.

Als Nächstes können Sie verwandte Themen wie **preserve markdown formatting for tables**, **render Markdown to PDF** oder **custom styling of imported Markdown elements** erkunden. Passen Sie die `LoadOptions`‑Flags an die genauen Formatierungsanforderungen Ihrer Anwendung an, und Sie erhalten eine feinkörnige Kontrolle über jeden Importschritt. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Master Markdown Load Options with Aspose.Words for Java](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)
- [Master Markdown Load Options Aspose Words Java](/words/german/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}