---
date: 2026-01-01
description: Erfahren Sie, wie Sie Formularfelder erstellen und Text, Tabellen, Bilder,
  Hyperlinks und mehr mit Aspose.Words für Java DocumentBuilder hinzufügen. Eine Schritt‑für‑Schritt‑Anleitung
  für Entwickler.
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: Wie man Formularfelder erstellt und Inhalte mit DocumentBuilder in Aspose.Words
  für Java hinzufügt
url: /de/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inhalte hinzufügen mit DocumentBuilder in Aspose.Words für Java

## Einführung in das Hinzufügen von Inhalten mit DocumentBuilder in Aspose.Words für Java

In diesem Schritt‑für‑Schritt‑Leitfaden **erstellen Sie Formularfelder** und fügen eine Vielzahl von Inhalten – Text, Tabellen, horizontale Linien, HTML, Hyperlinks, Bilder und mehr – in ein Word‑Dokument mit Aspose.Words für Java ein. Egal, ob Sie einen Bericht, eine Vertragsvorlage oder ein interaktives Formular erstellen, die Klasse `DocumentBuilder` gibt Ihnen feinkörnige Kontrolle über jedes Element. Lassen Sie uns loslegen!

## Schnellantworten
- **Wie erstelle ich Formularfelder?** Verwenden Sie `insertTextInput`, `insertCheckBox` oder `insertComboBox` auf einem `DocumentBuilder`.
- **Welche Methode fügt einfachen Text hinzu?** Rufen Sie `builder.write("Your text")` oder `builder.writeln("Your text")` auf.
- **Kann ich eine horizontale Linie einfügen?** Ja – `builder.insertHorizontalRule()` fügt einen Trennstrich ein.
- **Wie bette ich HTML ein?** Verwenden Sie `builder.insertHtml("<p>HTML content</p>")`.
- **Wie füge ich ein Inline‑Bild hinzu?** `builder.insertImage("path/to/image.png")` platziert das Bild im Textfluss.

## Was ist DocumentBuilder und warum verwendet man es zum Erstellen von Formularfeldern?

`DocumentBuilder` ist Aspose.Words’ fluente API zum programmgesteuerten Erstellen und Bearbeiten von Word‑Dokumenten. Sie abstrahiert die Low‑Level‑OpenXML‑Struktur, sodass Sie sich auf *was* Sie hinzufügen möchten – wie **Formularfelder** – konzentrieren können, anstatt auf *wie* das XML aussieht. Das macht sie ideal für die Generierung dynamischer Formulare, Verträge oder jedes Dokuments, das Benutzerinteraktion erfordert.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass die Aspose.Words‑Bibliothek für Java in Ihrem Projekt installiert ist. Sie können sie von [hier](https://releases.aspose.com/words/java/) herunterladen.

## Text hinzufügen (how to add text)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Tabellen hinzufügen

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start a table
Table table = builder.startTable();

// Insert cells and content
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// End the table
builder.endTable();

// Save the document
doc.save("path/to/your/document.docx");
```

## Horizontale Linie hinzufügen (add horizontal rule)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## Formularfelder hinzufügen (create form fields)

### Text‑Eingabe‑Formularfeld

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Kontrollkästchen‑Formularfeld

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Kombinationsfeld‑Formularfeld

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Define items for the combo box
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insert a combo box form field
builder.insertComboBox("DropDown", items, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

## HTML hinzufügen (insert html word)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## Hyperlinks hinzufügen (how to add hyperlink)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a hyperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Inhaltsverzeichnis hinzufügen

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();

// Save the document
doc.save("path/to/your/document.docx");
```

## Bilder hinzufügen

### Inline‑Bild (insert inline image)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### Schwebendes Bild

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## Absätze hinzufügen

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a paragraph
builder.writeln("This is a formatted paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Cursor bewegen (Step 10)

Sie können die Cursor‑Position im Dokument mit Methoden wie `moveToParagraph`, `moveToCell` usw. steuern.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Dies sind einige gängige Operationen, die Sie mit Aspose.Words für Java's `DocumentBuilder` ausführen können. Erkunden Sie die Dokumentation der Bibliothek für weiterführende Funktionen und Anpassungsoptionen. Viel Spaß beim Erstellen von Dokumenten!

## Fazit

In diesem umfassenden Leitfaden haben wir gezeigt, wie man **Formularfelder erstellt** und verschiedene Arten von Inhalten – Text, Tabellen, horizontale Linien, HTML, Hyperlinks, ein Inhaltsverzeichnis, Bilder, formatierte Absätze und Cursor‑Navigation – mit Aspose.Words für Java's `DocumentBuilder` hinzufügt. Sie verfügen nun über eine solide Grundlage, um dynamische, interaktive Word‑Dokumente programmgesteuert zu erzeugen.

## FAQ's

### Q: Was ist Aspose.Words für Java?

A: Aspose.Words für Java ist eine Java‑Bibliothek, die Entwicklern ermöglicht, Microsoft‑Word‑Dokumente programmgesteuert zu erstellen, zu ändern und zu manipulieren. Sie bietet ein breites Spektrum an Funktionen für Dokumentengenerierung, Formatierung und Inhaltseinfügung.

### Q: Wie kann ich ein Inhaltsverzeichnis zu meinem Dokument hinzufügen?

A: Um ein Inhaltsverzeichnis hinzuzufügen, verwenden Sie den `DocumentBuilder`, um ein TOC‑Feld einzufügen, und rufen anschließend `doc.updateFields()` nach dem Hinzufügen Ihrer Inhalte auf.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents field
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();
```

### Q: Wie füge ich Bilder in ein Dokument mit Aspose.Words für Java ein?

A: Sie können Bilder, sowohl inline als auch schwebend, mit dem `DocumentBuilder` einfügen.

#### Inline‑Bild:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### Schwebendes Bild:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q: Kann ich Text und Absätze formatieren, wenn ich Inhalte hinzufüge?

A: Ja, Sie können Text und Absätze mit dem `DocumentBuilder` formatieren. Setzen Sie Schriftarteigenschaften, Absatzausrichtung, Einrückungen und mehr, bevor Sie Inhalte schreiben.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set font and paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a formatted paragraph
builder.writeln("This is a formatted paragraph.");
```

### Q: Wie kann ich den Cursor an eine bestimmte Stelle im Dokument bewegen?

A: Verwenden Sie Methoden wie `moveToParagraph`, `moveToCell` usw., um den Cursor zu positionieren, bevor Sie neuen Inhalt einfügen.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Diese Antworten decken die häufigsten Szenarien bei der Arbeit mit Aspose.Words für Java's `DocumentBuilder` ab. Für weiterführende Details lesen Sie die [Dokumentation der Bibliothek](https://reference.aspose.com/words/java/) oder treten Sie der Aspose.Words‑Community für Support bei.

---

**Zuletzt aktualisiert:** 2026-01-01  
**Getestet mit:** Aspose.Words für Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}