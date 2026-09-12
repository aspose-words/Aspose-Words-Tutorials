---
category: general
date: 2026-09-11
description: Erfahren Sie, wie Sie die Fußnotenformatierung in Java mit Aspose.Words
  ändern. Dieser Leitfaden erklärt, wie Sie Fußnoten bearbeiten, den Fußnotenstil
  aktualisieren und den Fußnotentrennzeichen ändern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote formatting
- how to edit footnote
- update footnote style
- modify footnote separator
language: de
lastmod: 2026-09-11
og_description: Ändern Sie die Fußnotenformatierung in Java mit Aspose.Words. Folgen
  Sie diesem vollständigen Leitfaden, um Fußnoten zu bearbeiten, den Fußnotenstil
  zu aktualisieren und den Fußnotentrennzeichen zu ändern.
og_image_alt: Screenshot showing change footnote formatting in a Java editor
og_title: Fußnotenformatierung in Java ändern – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to change footnote formatting in Java with Aspose.Words.
    This guide explains how to edit footnote, update footnote style, and modify footnote
    separator.
  headline: How to change footnote formatting in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Footnote
- Document processing
title: Wie man die Fußnotenformatierung in einem Word‑Dokument mit Java ändert
url: /de/java/formatting-styles/how-to-change-footnote-formatting-in-a-word-document-using-j/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man die Fußnotenformatierung in einem Word-Dokument mit Java ändert

Wenn Sie die **Fußnotenformatierung** in einem Word-Dokument ändern müssen, führt Sie dieses Tutorial Schritt für Schritt mit Aspose.Words für Java. Egal, ob Sie eine Publishing-Pipeline aufbauen oder einfach nur **wie man Fußnoten bearbeitet** programmgesteuert, die nachstehende Lösung deckt alles ab, vom Laden der Datei bis zum Speichern der aktualisierten Version.

Sie lernen, wie Sie den **Fußnotenstil aktualisieren**, den Fußnoten‑Trenner fett formatieren und sogar die Eigenschaften des **Fußnoten‑Trenners** wie Schriftgröße oder Farbe **ändern** können. Der Leitfaden geht davon aus, dass Sie Grundkenntnisse in Java besitzen und über eine gültige Aspose.Words für Java‑Lizenz verfügen.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* Java 17 oder neuer installiert.
* Aspose.Words für Java (Version 23.12 oder höher) zum Klassenpfad Ihres Projekts hinzugefügt.
* Ein Word‑Dokument (`input.docx`), das mindestens eine Fußnote enthält.
* Eine IDE oder ein Build‑Tool (Maven/Gradle), um den Code zu kompilieren und auszuführen.

Falls Sie nicht sicher sind, wie Sie Aspose.Words zu einem Maven‑Projekt hinzufügen, fügen Sie die folgende Abhängigkeit in Ihre `pom.xml` ein:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Fußnotenformatierung mit Aspose.Words für Java ändern

Der Kern der Lösung ist ein kurzes Java‑Programm, das ein Dokument lädt, den Absatz des Fußnoten‑Trenners abruft, dessen Formatierung ändert und das Ergebnis speichert. Der Code ist vollständig eigenständig, sodass Sie ihn in eine neue Klasse kopieren und sofort ausführen können.

```java
import com.aspose.words.*;

public class ChangeFootnoteFormatting {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.getFootnoteSeparator();

        // Defensive check – the separator may be empty in some documents
        if (footnoteSeparator.getRuns().getCount() == 0) {
            // Create a new run so we have something to format
            Run run = new Run(doc);
            run.setText("\u2022"); // bullet character as placeholder
            footnoteSeparator.appendChild(run);
        }

        // Step 3: Change the first run's formatting – this is where we
        //          modify footnote separator appearance
        Run firstRun = footnoteSeparator.getRuns().get(0);
        Font font = firstRun.getFont();
        font.setBold(true);                // make the separator bold
        font.setItalic(true);              // optional: also italic
        font.setSize(10.0);                // set font size to 10 pt
        font.setColor(java.awt.Color.GRAY); // change color to a subtle gray

        // Step 4: Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Warum jeder Schritt wichtig ist

* **Laden des Dokuments** (`new Document`) erzeugt eine In‑Memory‑Repräsentation, die Aspose.Words manipulieren kann.  
* **Abrufen des Fußnoten‑Trenners** (`getFootnoteSeparator`) gibt Ihnen direkten Zugriff auf den Absatz, der Fußnoten vom Haupttext trennt. Dies ist das Element, das Sie anvisieren müssen, wenn Sie die **Fußnotenformatierung** ändern möchten.  
* **Formatieren des Runs** (`setBold`, `setItalic`, `setSize`, `setColor`) zeigt, wie Sie die Eigenschaften des **Fußnoten‑Trenners** **ändern** können. Sie können hier weitere Schriftattribute wie Unterstreichung oder Hervorhebung hinzufügen, um das Aussehen vollständig zu steuern.  
* **Speichern des Dokuments** schreibt die Änderungen zurück auf die Festplatte und erzeugt eine neue Datei (`output.docx`), die den aktualisierten Fußnotenstil widerspiegelt.

> **Profi‑Tipp:** Wenn Ihr Quelldokument einen benutzerdefinierten Fußnoten‑Trenner verwendet, der mehrere Runs enthält (z. B. eine Kombination von Symbolen), iterieren Sie über `footnoteSeparator.getRuns()` und wenden Sie dieselben `Font`‑Einstellungen auf jeden Run an, um ein konsistentes Styling zu gewährleisten.

## Wie man den Fußnoten‑Trenner programmgesteuert bearbeitet

Manchmal müssen Sie nicht nur den Trenner, sondern auch den eigentlichen Fußnotentext bearbeiten. Mit derselben API können Sie jede Fußnote abrufen, deren Absatzformatierung anpassen oder den Nummerierungsstil ändern.

```java
for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
    // Example: make all footnote text italic and 9 pt
    for (Paragraph para : (Iterable<Paragraph>) footnote.getParagraphs()) {
        para.getParagraphFormat().setStyleIdentifier(StyleIdentifier.FOOTNOTE_TEXT);
        para.getRuns().forEach(run -> {
            Font f = run.getFont();
            f.setItalic(true);
            f.setSize(9.0);
        });
    }
}
```

Das obige Snippet zeigt, **wie man Fußnoten** nach dem **Ändern der Fußnotenformatierung** für den Trenner bearbeitet. Durch das Durchlaufen von `doc.getFootnotes()` stellen Sie sicher, dass jede Fußnote denselben Stil übernimmt, was für ein professionell aussehendes Dokument unerlässlich ist.

## Fußnotenstil für ein einheitliches Dokumentaussehen aktualisieren

Wenn Sie lieber mit Stilen statt mit einzelnen Runs arbeiten, ermöglicht Ihnen Aspose.Words das Erstellen oder Ändern eines `Style`‑Objekts, das Sie anschließend auf Fußnoten und den Trenner anwenden können. Dieser Ansatz ist nützlich, wenn Sie den **Fußnotenstil** in vielen Dokumenten **aktualisieren** müssen.

```java
// Create or retrieve a style named "MyFootnoteStyle"
Style footnoteStyle = doc.getStyles().add(StyleType.PARAGRAPH, "MyFootnoteStyle");
footnoteStyle.getFont().setBold(true);
footnoteStyle.getFont().setSize(10);
footnoteStyle.getFont().setColor(java.awt.Color.DARK_GRAY);

// Apply the style to the separator
footnoteSeparator.getParagraphFormat().setStyle(footnoteStyle);

// Apply the same style to every footnote paragraph
for (Footnote fn : (Iterable<Footnote>) doc.getFootnotes()) {
    for (Paragraph p : (Iterable<Paragraph>) fn.getParagraphs()) {
        p.getParagraphFormat().setStyle(footnoteStyle);
    }
}
```

Die Verwendung eines dedizierten Stils erleichtert die zukünftige Wartung – ändern Sie den Stil einmal, und jede Fußnote sowie jeder Trenner werden automatisch aktualisiert. Diese Technik ist der empfohlene Weg, um den **Fußnotenstil** in groß angelegten Publishing‑Workflows **zu aktualisieren**.

## Fußnoten‑Trenner an Ihr Branding anpassen

Markenrichtlinien verlangen manchmal, dass der Fußnoten‑Trenner ein bestimmtes Zeichen (z. B. ein Sternchen) oder eine benutzerdefinierte Linie verwendet. Aspose.Words erlaubt es Ihnen, den Standard‑Trennerinhalt vollständig zu ersetzen.

```java
// Remove existing runs
footnoteSeparator.getRuns().clear();

// Insert a custom separator line
Run customRun = new Run(doc);
customRun.setText("--- Custom Separator ---");
Font customFont = customRun.getFont();
customFont.setBold(true);
customFont.setSize(8);
customFont.setColor(java.awt.Color.BLUE);
footnoteSeparator.appendChild(customRun);
```

Der obige Code **ändert den Fußnoten‑Trenner**, indem er vorhandene Runs löscht und einen neuen Run mit dem gewünschten Text und der gewünschten Formatierung einfügt. Sie können auch Unicode‑Zeichen wie `\u2022` (Aufzählungszeichen) oder `\u2014` (Gedankenstrich) verwenden, um den genauen visuellen Effekt zu erzielen, den Ihre Marke verlangt.

## Erwartetes Ergebnis

Nach dem Ausführen des Programms:

* Der Fußnoten‑Trenner in `output.docx` erscheint **fett**, **kursiv**, 10 pt und grau (oder in jeder von Ihnen festgelegten Farbe).  
* Alle Fußnoten‑Absätze übernehmen den von Ihnen definierten Stil und sorgen für ein einheitliches Erscheinungsbild im gesamten Dokument.  
* Wenn Sie den Trennertext ersetzt haben, ist die neue benutzerdefinierte Linie genau dort sichtbar, wo zuvor die ursprüngliche Linie stand.

Öffnen Sie die resultierende Datei in Microsoft Word oder LibreOffice Writer, um die Änderungen zu überprüfen. Sie sollten den aktualisierten Trenner direkt über der ersten Fußnote sehen, und der Fußnotentext sollte alle von Ihnen vorgenommenen Stiländerungen widerspiegeln.

## Häufige Fallstricke und wie man sie vermeidet

| Problem | Warum es passiert | Lösung |
|---------|-------------------|--------|
| `footnoteSeparator.getRuns().getCount() == 0` wirft eine Ausnahme | Einige Dokumente haben einen leeren Trenner‑Absatz. | Fügen Sie eine defensive Prüfung hinzu und erstellen Sie einen Run, falls keiner existiert (siehe Code‑Beispiel). |
| Schriftartänderungen sind nicht sichtbar | Das Dokument verwendet ein Theme, das direkte Formatierungen überschreibt. | Setzen Sie `font.setThemeFont(null)` oder wenden Sie stattdessen einen benutzerdefinierten Stil an. |
| Gespeicherte Datei spiegelt Änderungen nicht wider | Die Originaldatei ist noch in Word geöffnet und sperrt den Ausgabepfad. | Schließen Sie alle Instanzen der Datei, bevor Sie das Programm ausführen, oder |

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wortverarbeitung mit Fußnoten und Endnoten](/words/english/net/working-with-footnote-and-endnote/)
- [Fußnoten‑ und Endnoten‑Position festlegen](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Wie man Aspose.Words Versionsinformationen in Java anzeigt: Ein umfassender Leitfaden](/words/english/java/getting-started/aspose-words-java-version-info/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}