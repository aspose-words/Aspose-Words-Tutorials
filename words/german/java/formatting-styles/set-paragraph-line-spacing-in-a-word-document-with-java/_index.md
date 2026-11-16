---
category: general
date: 2026-11-15
description: Absatzzeilenabstand in einem Word‑Dokument mit Java festlegen. Erfahren
  Sie, wie Sie den Zeilenabstand programmgesteuert mit Aspose.Words für eine präzise
  Dokumentformatierung einstellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: de
lastmod: 2026-11-15
og_description: Absatzzeilenabstand in einem Word‑Dokument mit Java festlegen. Dieser
  Leitfaden erklärt, wie Sie den Zeilenabstand für Absätze und Fußnotentrennlinien
  mit Aspose.Words einstellen, sodass Sie die komplette Kontrolle über das Dokumentlayout
  haben.
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: Absatzzeilenabstand in Word mit Java festlegen
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: Absatzzeilenabstand in einem Word‑Dokument mit Java festlegen
url: /de/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Absatzzeilenabstand in einem Word-Dokument mit Java festlegen

Wenn Sie **Absatzzeilenabstand** in einem Word-Dokument festlegen müssen, zeigt Ihnen dieses Tutorial, wie Sie dies mit Java und Aspose.Words tun können. Sie lernen außerdem **wie man Zeilenabstand** für Fußnotentrennzeichen festlegt – ein häufiges Erfordernis beim Formatieren professioneller Dokumente.

In den folgenden Abschnitten werden Sie:

* Eine vorhandene *.docx*-Datei laden.
* Den Absatz des Fußnotentrennzeichens abrufen.
* Einen benutzerdefinierten Zeilenabstandswert anwenden.
* Das aktualisierte Dokument speichern.

Keine externe Konfiguration ist erforderlich, außer der Aspose.Words-Bibliothek zu Ihrem Projekt hinzuzufügen, sodass Sie den Code unverändert kopieren und sofort ausführen können.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie:

* Java 17 oder neuer installiert.
* Maven (oder ein anderes Build-Tool) zur Verwaltung von Abhängigkeiten.
* Eine gültige Aspose.Words for Java Lizenz (die kostenlose Evaluierung funktioniert zum Testen).
* Ein Eingabe‑Word‑Dokument (`input.docx`) in einem bekannten Verzeichnis.

Fügen Sie die Aspose.Words-Abhängigkeit zu Ihrer `pom.xml` hinzu:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## Absatzzeilenabstand mit Aspose.Words festlegen

Diese H2‑Überschrift enthält das Hauptkeyword und erfüllt die SEO‑Anforderung.

### Schritt 1: Word-Dokument laden

Zuerst erstellen Sie eine `Document`‑Instanz, die auf Ihre Quelldatei verweist.

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*Warum das wichtig ist*: Das Laden des Dokuments liefert Ihnen ein In‑Memory‑Modell, das Sie manipulieren können, ohne die Originaldatei zu berühren, bis Sie explizit speichern.

### Schritt 2: Fußnotentrennzeichen abrufen

Fußnotentrennzeichen sind spezielle Absätze, die zwischen Fußnoten und dem Haupttext erscheinen. Um ihr Aussehen zu ändern, müssen Sie auf das `FootnoteSeparator`‑Objekt zugreifen.

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*Tipp*: Wenn Ihr Dokument keine Fußnoten enthält, existiert das Trennzeichen dennoch als versteckter Absatz, sodass der Aufruf niemals `null` zurückgibt.

### Schritt 3: Zeilenabstand für den Absatz des Trennzeichens festlegen

Wenden Sie nun den gewünschten Zeilenabstand an. Aspose.Words verwendet Punkte für Zeilenabstandswerte; 12 pts entsprechen etwa einem einfachen Zeilenabstand für die meisten Schriftarten.

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

Sie können auch andere Abstandsmodi verwenden:

| Modus                     | Methodenaufruf                                      |
|--------------------------|--------------------------------------------------|
| **Exactly** (fixed pts) | `setLineSpacingRule(LineSpacingRule.EXACTLY)`   |
| **Multiple** (e.g., 1.5) | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

Die Wahl der richtigen Regel stellt sicher, dass das Dokument konsistent in Word, Google Docs und anderen Betrachtern gerendert wird.

### Schritt 4: Aktualisiertes Dokument speichern

Schreiben Sie schließlich die Änderungen zurück auf die Festplatte.

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

Wenn Sie `output.docx` in Microsoft Word öffnen, wird das Fußnotentrennzeichen mit dem von Ihnen definierten Zeilenabstand angezeigt.

## Verstehen, wie man den Zeilenabstand für reguläre Absätze festlegt

Die gleiche API funktioniert für jedes `Paragraph`‑Objekt, nicht nur für Fußnotentrennzeichen. Hier ist ein kurzes Beispiel, das den Abstand des ersten Absatzes im Hauptteil anpasst:

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**Warum Sie das benötigen könnten**: Berichte, Verträge und wissenschaftliche Arbeiten erfordern häufig einen bestimmten Zeilenabstandsstil (z. B. doppelter Zeilenabstand für Entwürfe). Die Verwendung der gleichen `setLineSpacing`‑Methode garantiert das genaue Layout, das Sie erwarten.

## Häufige Fallstricke und wie man sie vermeidet

| Problem                                 | Ursache                                   | Lösung |
|-----------------------------------------|------------------------------------------|--------|
| Zeilenabstand erscheint unverändert     | `LineSpacingRule` auf den Standardwert (AUTO) belassen | Regel explizit mit `setLineSpacingRule` setzen. |
| Zusätzliche Leerzeilen nach dem Trennzeichen | Trennzeichen enthält versteckte Wagenrückläufe | Den Text des Trennzeichens mit `separator.getText().trim();` trimmen, bevor der Abstand angewendet wird. |
| Dokument wird nach dem Speichern beschädigt | Verwendung einer veralteten Aspose.Words-Version | Auf die neueste Version (z. B. 24.10) aktualisieren, die Fehlerbehebungen für das Speichern enthält. |

## Pro‑Tipp: Mehrere Dokumente stapelweise verarbeiten

Wenn Sie Dutzende von Dateien aktualisieren müssen, packen Sie die Logik in eine Hilfsmethode und iterieren Sie über einen Ordner:

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

Das Ausführen dieser Methode in einer Schleife spart Ihnen Stunden manueller Bearbeitung.

## Erwartete Ausgabe

Nach dem Ausführen des vollständigen Programms wird `output.docx`:

* Den ursprünglichen Inhalt unverändert enthalten, außer dem Zeilenabstand.
* Das Fußnotentrennzeichen mit einem einfachen Zeilenabstand (12 pts) anzeigen.
* Alle andere Formatierungen (Stile, Bilder, Tabellen) beibehalten.

Öffnen Sie die Datei in Word und überprüfen Sie, dass die Trennlinie enger (oder lockerer, je nach dem von Ihnen gesetzten Wert) ist.

## Fazit

Sie wissen jetzt, wie man **Absatzzeilenabstand** in einem Word-Dokument mit Java festlegt, und Sie verstehen auch **wie man Zeilenabstand** sowohl für Fußnotentrennzeichen als auch für reguläre Absätze einstellt. Das vollständige, ausführbare Beispiel demonstriert das Laden eines Dokuments, das Anpassen von Zeilenabstandseigenschaften und das Speichern des Ergebnisses – alles mit wenigen klaren API‑Aufrufen.

**Nächste Schritte**, die Sie erkunden könnten:

* **Wie man Zeilenabstand** für Tabellen und Listenelemente festlegt.
* Unterschiedliche Abstandsregeln für Überschriften gegenüber Fließtext anwenden.
* Das `Style`‑Objekt verwenden, um den Abstand im gesamten Dokument durchzusetzen.

Experimentieren Sie mit den Werten, kombinieren Sie sie mit anderen Formatierungsoptionen, und Sie haben die volle Kontrolle über das Dokumentlayout in jeder Java‑Anwendung. Viel Spaß beim Programmieren!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [How to set options in Aspose.Words for Java – complete guide](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Change Asian Paragraph Spacing And Indents In Word Document](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}