---
"description": "Meistern Sie die Dokumenterstellung mit Aspose.Words für Java. Eine Schritt-für-Schritt-Anleitung zum Hinzufügen von Text, Tabellen, Bildern und mehr. Erstellen Sie mühelos beeindruckende Word-Dokumente."
"linktitle": "Hinzufügen von Inhalten mit DocumentBuilder"
"second_title": "Aspose.Words Java-Dokumentverarbeitungs-API"
"title": "Hinzufügen von Inhalten mit DocumentBuilder in Aspose.Words für Java"
"url": "/de/java/document-manipulation/adding-content-using-documentbuilder/"
"weight": 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hinzufügen von Inhalten mit DocumentBuilder in Aspose.Words für Java


## Einführung in das Hinzufügen von Inhalten mit DocumentBuilder in Aspose.Words für Java

In dieser Schritt-für-Schritt-Anleitung erfahren Sie, wie Sie mit Aspose.Words für Javas DocumentBuilder verschiedene Inhalte in ein Word-Dokument einfügen. Wir behandeln das Einfügen von Text, Tabellen, horizontalen Linien, Formularfeldern, HTML, Hyperlinks, Inhaltsverzeichnissen, Inline- und Floating-Bildern, Absätzen und mehr. Los geht’s!

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass die Bibliothek Aspose.Words für Java in Ihrem Projekt eingerichtet ist. Sie können sie hier herunterladen: [Hier](https://releases.aspose.com/words/java/).

## Text hinzufügen

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Einfügen eines einfachen Textabsatzes
builder.write("This is a simple text paragraph.");

// Speichern des Dokuments
doc.save("path/to/your/document.docx");
```

## Hinzufügen von Tabellen

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Einen Tisch eröffnen
Table table = builder.startTable();

// Zellen und Inhalte einfügen
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// Beenden Sie den Tisch
builder.endTable();

// Speichern des Dokuments
doc.save("path/to/your/document.docx");
```

## Horizontale Linie hinzufügen

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Einfügen einer horizontalen Linie
builder.insertHorizontalRule();

// Speichern des Dokuments
doc.save("path/to/your/document.docx");
```

## Hinzufügen von Formularfeldern

### Texteingabeformularfeld

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Einfügen eines Texteingabeformularfelds
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Speichern des Dokuments
doc.save("path/to/your/document.docx");
```

### Kontrollkästchen-Formularfeld

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Einfügen eines Kontrollkästchen-Formularfelds
builder.insertCheckBox("CheckBox", true, true, 0);

// Speichern des Dokuments
doc.save("path/to/your/document.docx");
```

### Kombinationsfeld-Formularfeld

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Definieren von Elementen für das Kombinationsfeld
String[] items = { "Option 1", "Option 2", "Option 3" };

// Einfügen eines Kombinationsfeld-Formularfelds
builder.insertComboBox("DropDown", items, 0);

// Speichern des Dokuments
doc.save("path/to/your/document.docx");
```

## HTML hinzufügen

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// HTML-Inhalt einfügen
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Speichern des Dokuments
doc.save("path/to/your/document.docx");
```

## Hinzufügen von Hyperlinks

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Einfügen eines Hyperlinks
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Speichern des Dokuments
doc.save("path/to/your/document.docx");
```

## Hinzufügen eines Inhaltsverzeichnisses

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Einfügen eines Inhaltsverzeichnisses
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Dokumentinhalt hinzufügen
// ...

// Aktualisieren Sie das Inhaltsverzeichnis
doc.updateFields();

// Speichern des Dokuments
doc.save("path/to/your/document.docx");
```

## Bilder hinzufügen

### Inline-Bild

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Einfügen eines Inline-Bildes
builder.insertImage("path/to/your/image.png");

// Speichern des Dokuments
doc.save("path/to/your/document.docx");
```

### Schwebendes Bild

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Einfügen eines schwebenden Bildes
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Speichern des Dokuments
doc.save("path/to/your/document.docx");
```

## Absätze hinzufügen

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Festlegen der Absatzformatierung
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

// Einfügen eines Absatzes
builder.writeln("This is a formatted paragraph.");

// Speichern des Dokuments
doc.save("path/to/your/document.docx");
```

## Schritt 10: Bewegen des Cursors

Sie können die Cursorposition innerhalb des Dokuments mit verschiedenen Methoden steuern, wie zum Beispiel `moveToParagraph`, `moveToCell`und mehr. Hier ist ein Beispiel:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Bewegen Sie den Cursor zu einem bestimmten Absatz
builder.moveToParagraph(2, 0);

// Fügen Sie Inhalt an der neuen Cursorposition hinzu
builder.writeln("This is the 3rd paragraph.");
```

Dies sind einige gängige Operationen, die Sie mit Aspose.Words für Javas DocumentBuilder durchführen können. Weitere erweiterte Funktionen und Anpassungsmöglichkeiten finden Sie in der Dokumentation der Bibliothek. Viel Spaß beim Erstellen Ihrer Dokumente!


## Abschluss

In diesem umfassenden Leitfaden haben wir die Möglichkeiten von Aspose.Words für Javas DocumentBuilder untersucht, um Word-Dokumenten verschiedene Inhaltstypen hinzuzufügen. Wir haben Text, Tabellen, horizontale Linien, Formularfelder, HTML, Hyperlinks, Inhaltsverzeichnis, Bilder, Absätze und Cursorbewegungen behandelt.

## Häufig gestellte Fragen

### F: Was ist Aspose.Words für Java?

A: Aspose.Words für Java ist eine Java-Bibliothek, mit der Entwickler Microsoft Word-Dokumente programmgesteuert erstellen, ändern und bearbeiten können. Sie bietet zahlreiche Funktionen zur Dokumenterstellung, Formatierung und Inhaltseinfügung.

### F: Wie kann ich meinem Dokument ein Inhaltsverzeichnis hinzufügen?

A: Um ein Inhaltsverzeichnis hinzuzufügen, verwenden Sie das `DocumentBuilder` um ein Inhaltsverzeichnis in Ihr Dokument einzufügen. Achten Sie darauf, die Felder im Dokument nach dem Hinzufügen von Inhalten zu aktualisieren, um das Inhaltsverzeichnis zu füllen. Hier ein Beispiel:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Einfügen eines Inhaltsverzeichnisfelds
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Dokumentinhalt hinzufügen
// ...

// Aktualisieren Sie das Inhaltsverzeichnis
doc.updateFields();
```

### F: Wie füge ich mit Aspose.Words für Java Bilder in ein Dokument ein?

A: Sie können Bilder sowohl eingebettet als auch schwebend einfügen, indem Sie `DocumentBuilder`. Hier sind Beispiele für beides:

#### Inline-Bild:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Einfügen eines Inline-Bildes
builder.insertImage("path/to/your/image.png");
```

#### Schwebendes Bild:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Einfügen eines schwebenden Bildes
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### F: Kann ich beim Hinzufügen von Inhalten Text und Absätze formatieren?

A: Ja, Sie können Text und Absätze formatieren mit dem `DocumentBuilder`Sie können Schrifteigenschaften, Absatzausrichtung, Einrückung und mehr festlegen. Hier ein Beispiel:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Schriftart und Absatzformatierung festlegen
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

// Einfügen eines formatierten Absatzes
builder.writeln("This is a formatted paragraph.");
```

### F: Wie kann ich den Cursor an eine bestimmte Stelle im Dokument bewegen?

A: Sie können die Cursorposition mit Methoden wie diesen steuern. `moveToParagraph`, `moveToCell`und mehr. Hier ist ein Beispiel:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Bewegen Sie den Cursor zu einem bestimmten Absatz
builder.moveToParagraph(2, 0);

// Fügen Sie Inhalt an der neuen Cursorposition hinzu
builder.writeln("This is the 3rd paragraph.");
```

Dies sind einige häufig gestellte Fragen und Antworten, die Ihnen den Einstieg in Aspose.Words für Javas DocumentBuilder erleichtern. Wenn Sie weitere Fragen haben oder weitere Hilfe benötigen, lesen Sie die [Dokumentation der Bibliothek](https://reference.aspose.com/words/java/) oder suchen Sie Hilfe bei der Aspose.Words-Community und den Supportressourcen.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}