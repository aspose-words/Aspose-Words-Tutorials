---
category: general
date: 2026-11-22
description: Erfahren Sie, wie Sie mit Aspose.Words für Java Formen zu Word hinzufügen
  – ein Rechteck einfügen und es programmgesteuert ausblenden.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: de
lastmod: 2026-11-22
og_description: Fügen Sie Word mit Aspose.Words für Java eine Form hinzu. Dieses Tutorial
  zeigt, wie man ein Rechteck einfügt, die Form ausblendet und das Dokument speichert.
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: Form zu Word mit Aspose.Words hinzufügen – Java‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Wie man Formen zu Word-Dokumenten mit Aspose.Words für Java hinzufügt
url: /de/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# So fügen Sie Word‑Dokumenten mit Aspose.Words für Java Formen hinzu

Wenn Sie **Formen zu Word**‑Dokumenten programmgesteuert **hinzufügen** möchten, macht Aspose.Words für Java das ganz einfach. In diesem Leitfaden lernen Sie **wie man eine Form einfügt**, ihre Sichtbarkeit steuert und **wie man eine Form ausblendet**, sodass die endgültige Datei genau so aussieht, wie Sie es erwarten.

Sie gehen ein komplettes, ausführbares Beispiel durch, das ein vorhandenes `.docx` lädt, ein Rechteck einfügt, es ausblendet und das Ergebnis speichert. Keine externen Skripte oder manuellen Schritte sind nötig, und das Tutorial behandelt gängige Varianten wie das Erstellen eines neuen Dokuments von Grund auf oder das Ausblenden einer Form nur beim Drucken.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* Java 17 (oder neuer) installiert – frühere Versionen funktionieren, aber das aktuelle LTS bietet bessere Performance.  
* Maven 3.8+ für das Abhängigkeitsmanagement.  
* Eine gültige Aspose.Words für Java‑Lizenz (die kostenlose Evaluation reicht für Lernzwecke).  
* Eine IDE oder einen Texteditor Ihrer Wahl (z. B. IntelliJ IDEA, VS Code).

## Schritt 1: Aspose.Words zu Ihrem Maven‑Projekt hinzufügen

Fügen Sie die folgende Abhängigkeit zu Ihrer `pom.xml` hinzu. Damit wird die neueste stabile Version (Stand November 2026) eingebunden.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Pro‑Tipp:** Verwenden Sie ein `<scope>provided</scope>`‑Element, wenn Sie das JAR mit Ihrer eigenen Lizenzlogik ausliefern möchten.

## Form zu Word hinzufügen – Dokument initialisieren

Der erste funktionale Schritt besteht darin, ein `Document`‑Objekt zu erhalten. Sie können entweder eine vorhandene Datei laden oder ein frisches Dokument erstellen.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*Warum das wichtig ist*: Die `Document`‑Klasse ist der Einstiegspunkt für alle Word‑Manipulationen. Das Laden einer bestehenden Datei bewahrt Formatvorlagen, Kopf‑ und Fußzeilen, während ein neues Dokument Ihnen ein leeres Blatt bietet.

## Wie man eine Form in ein Word‑Dokument einfügt

Erstellen Sie als Nächstes einen `DocumentBuilder`, um den Inhalt des Dokuments zu ändern. Der Builder stellt Methoden zum Einfügen von Text, Tabellen und **Formen** bereit.

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

Der Aufruf `insertShape` liefert ein `Shape`‑Objekt, das Sie weiter konfigurieren können (Farbe, Rahmen, Text usw.). Die Abmessungen werden in Punkten angegeben (1 pt = 1/72 in).

*Warum Sie ein Rechteck verwenden könnten*: Rechtecke sind der häufigste Behälter für Anmerkungen, Wasserzeichen oder Platzhalter. Sie können `ShapeType.RECTANGLE` durch `ShapeType.ELLIPSE`, `ShapeType.LINE` usw. ersetzen, um unterschiedliche visuelle Anforderungen zu erfüllen.

## Wie man eine Form in Word ausblendet

Manchmal muss eine Form für Layout‑Berechnungen existieren, aber in der endgültigen Darstellung nicht erscheinen. Aspose.Words stellt die Methode `setHidden(true)` bereit, um dies zu erreichen.

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

Das Hidden‑Flag funktioniert wie die **Ausgeblendet**‑Formatoption in Microsoft Word: Die Form wird aus dem visuellen Layout entfernt, bleibt aber im Objektmodell des Dokuments erhalten. Das ist nützlich für:

* Das Speichern von Metadaten oder Markern, die Ihre Anwendung später ausliest.  
* Das Erstellen von Platzhaltern, die kurz vor der Veröffentlichung entfernt werden.  
* Die Steuerung der Sichtbarkeit für verschiedene Ausgabeformate (z. B. im HTML ausblenden, aber im PDF behalten).

> **Hinweis:** Ausgeblendete Formen werden standardmäßig trotzdem nach PDF exportiert. Wenn Sie sie auch aus dem PDF entfernen wollen, setzen Sie `rectangle.getWrapType() = WrapType.NONE` und passen die `Hidden`‑Eigenschaft entsprechend an.

## Schritt 4: Das modifizierte Dokument speichern

Speichern Sie abschließend die Änderungen in einer neuen Datei.

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

Wenn Sie `output.docx` in Microsoft Word öffnen, ist das Rechteck nicht sichtbar, bleibt aber Teil des Dokumentbaums. Sie können seine Existenz programmgesteuert prüfen, indem Sie die Datei erneut laden und `Shape.isHidden()` abfragen.

### Erwartete Ausgabe

* Die Datei `output.docx` öffnet sich ohne sichtbare Formen.  
* Wenn Sie das Dokument mit Aspose.Words untersuchen (z. B. `doc.getChildNodes(NodeType.SHAPE, true).size()`), beträgt die Form‑Anzahl **1**, was bestätigt, dass die Form existiert, aber ausgeblendet ist.

## Erweiterte Varianten und Sonderfälle

### 1. Eine Form in einem neuen Dokument erstellen

Wenn Sie von Grund auf beginnen, ersetzen Sie die Lade‑Zeile durch:

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. Die Form exakt positionieren

Standardmäßig platziert `insertShape` die Form an der aktuellen Cursor‑Position. Für eine absolute Positionierung:

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. Sichtbarkeit je nach Ausgabeformat steuern

Wenn die Form in der Word‑Benutzeroberfläche sichtbar, beim Export nach PDF jedoch ausgeblendet sein soll, verwenden Sie `Shape.setWrapType(WrapType.NONE)` zusammen mit `Hidden`:

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. Text in die Form einfügen

Ein Rechteck kann einen Text‑Frame enthalten:

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

Den Text‑Box können Sie dann mit demselben Aufruf `setHidden(true)` ausblenden.

## Häufige Stolperfallen und wie man sie vermeidet

| Symptom | Ursache | Lösung |
|---------|---------|--------|
| Form erscheint trotz `setHidden(true)` | Das Dokument wurde gespeichert, bevor das Hidden‑Flag gesetzt wurde. | Stellen Sie sicher, dass Sie `setHidden(true)` **vor** `doc.save()` aufrufen. |
| Formgröße wirkt verzerrt | Verwechslung von Punkten und Pixeln auf hochauflösenden Bildschirmen. | Verwenden Sie Punkte (72 pt = 1 in) für konsistente Größen über alle Plattformen hinweg. |
| Ausgeblendete Form wird trotzdem gedruckt | Einige Drucker ignorieren das Hidden‑Flag. | Setzen Sie `Shape.setWrapType(WrapType.NONE)` und deaktivieren Sie zusätzlich `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)`. |

## Fazit

Sie wissen jetzt, wie Sie **Formen zu Word**‑Dokumenten mit Aspose.Words für Java **hinzufügen**, **wie Sie Formen einfügen** und **wie Sie Formen ausblenden**, sodass sie für Endbenutzer unsichtbar bleiben, aber dennoch Teil der Dokumentstruktur sind. Das vollständige Beispiel oben lädt eine Datei, fügt ein Rechteck ein, blendet es aus und speichert das Ergebnis – sowohl für typische Anwendungsfälle als auch für mehrere Sonderfälle.

Ab hier können Sie verwandte Themen erkunden, etwa **wie man Formen mit benutzerdefinierten Füllfarben einfügt**, **wie man Formen in Word für bedingtes Drucken ausblendet** oder die automatisierte Massenverarbeitung von Dokumenten mit Aspose.Words. Experimentieren Sie mit verschiedenen `ShapeType`‑Werten, Positionierungsoptionen und Sichtbarkeitsflags, um Ihren spezifischen Workflow zu unterstützen.

Viel Spaß beim Coden und genießen Sie die Flexibilität, die die programmgesteuerte Word‑Manipulation Ihren Java‑Anwendungen bietet!


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Ein Word‑Dokument programmgesteuert erstellen, eine Form hinzufügen und ausblenden in Java mit Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [Wie man eine Form in einem Word‑Dokument mit Java ausblendet](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Ein leeres .docx‑Word‑Dokument erstellen und ein verstecktes Rechteck mit Aspose.Words hinzufügen](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}