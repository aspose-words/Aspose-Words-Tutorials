---
title: Lägga till innehåll med DocumentBuilder i Aspose.Words för Java
linktitle: Lägga till innehåll med DocumentBuilder
second_title: Aspose.Words Java Document Processing API
description: Master Document Creation med Aspose.Words för Java. En steg-för-steg-guide för att lägga till text, tabeller, bilder och mer. Skapa fantastiska Word-dokument utan ansträngning.
weight: 26
url: /sv/java/document-manipulation/adding-content-using-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lägga till innehåll med DocumentBuilder i Aspose.Words för Java


## Introduktion till att lägga till innehåll med DocumentBuilder i Aspose.Words för Java

I den här steg-för-steg-guiden kommer vi att utforska hur man använder Aspose.Words för Javas DocumentBuilder för att lägga till olika typer av innehåll i ett Word-dokument. Vi täcker infogning av text, tabeller, horisontella regler, formulärfält, HTML, hyperlänkar, innehållsförteckning, infogade och flytande bilder, stycken och mer. Låt oss komma igång!

## Förutsättningar

 Innan du börjar, se till att du har Aspose.Words för Java-biblioteket inställt i ditt projekt. Du kan ladda ner den från[här](https://releases.aspose.com/words/java/).

## Lägger till text

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga ett enkelt textstycke
builder.write("This is a simple text paragraph.");

// Spara dokumentet
doc.save("path/to/your/document.docx");
```

## Lägga till tabeller

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

//Starta ett bord
Table table = builder.startTable();

// Infoga celler och innehåll
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// Avsluta bordet
builder.endTable();

// Spara dokumentet
doc.save("path/to/your/document.docx");
```

## Lägger till horisontell regel

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga en horisontell regel
builder.insertHorizontalRule();

// Spara dokumentet
doc.save("path/to/your/document.docx");
```

## Lägga till formulärfält

### Textinmatningsformulärfält

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga ett textinmatningsformulärfält
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Spara dokumentet
doc.save("path/to/your/document.docx");
```

### Kryssrutan Formulärfält

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga ett formulärfält för kryssruta
builder.insertCheckBox("CheckBox", true, true, 0);

// Spara dokumentet
doc.save("path/to/your/document.docx");
```

### Kombinationsruta formulärfält

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Definiera objekt för kombinationsrutan
String[] items = { "Option 1", "Option 2", "Option 3" };

// Infoga ett formulärfält med kombinationsruta
builder.insertComboBox("DropDown", items, 0);

// Spara dokumentet
doc.save("path/to/your/document.docx");
```

## Lägger till HTML

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga HTML-innehåll
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Spara dokumentet
doc.save("path/to/your/document.docx");
```

## Lägga till hyperlänkar

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga en hyperlänk
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Spara dokumentet
doc.save("path/to/your/document.docx");
```

## Lägga till en innehållsförteckning

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga en innehållsförteckning
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Lägg till dokumentinnehåll
// ...

// Uppdatera innehållsförteckningen
doc.updateFields();

// Spara dokumentet
doc.save("path/to/your/document.docx");
```

## Lägga till bilder

### Inline bild

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga en inline-bild
builder.insertImage("path/to/your/image.png");

// Spara dokumentet
doc.save("path/to/your/document.docx");
```

### Flytande bild

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga en flytande bild
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Spara dokumentet
doc.save("path/to/your/document.docx");
```

## Lägga till stycken

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Ställ in styckeformatering
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

// Infoga ett stycke
builder.writeln("This is a formatted paragraph.");

// Spara dokumentet
doc.save("path/to/your/document.docx");
```

## Steg 10: Flytta markören

 Du kan styra markörens position i dokumentet med olika metoder som`moveToParagraph`, `moveToCell`och mer. Här är ett exempel:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Flytta markören till ett specifikt stycke
builder.moveToParagraph(2, 0);

// Lägg till innehåll vid den nya markörpositionen
builder.writeln("This is the 3rd paragraph.");
```

Det här är några vanliga operationer du kan utföra med Aspose.Words för Javas DocumentBuilder. Utforska bibliotekets dokumentation för mer avancerade funktioner och anpassningsalternativ. Glad dokumentskapande!


## Slutsats

I den här omfattande guiden har vi utforskat funktionerna i Aspose.Words för Javas DocumentBuilder för att lägga till olika typer av innehåll till Word-dokument. Vi har täckt text, tabeller, horisontella regler, formulärfält, HTML, hyperlänkar, innehållsförteckning, bilder, stycken och markörrörelser.

## FAQ's

### F: Vad är Aspose.Words för Java?

S: Aspose.Words för Java är ett Java-bibliotek som låter utvecklare skapa, modifiera och manipulera Microsoft Word-dokument programmatiskt. Den tillhandahåller ett brett utbud av funktioner för dokumentgenerering, formatering och infogning av innehåll.

### F: Hur kan jag lägga till en innehållsförteckning i mitt dokument?

S: För att lägga till en innehållsförteckning, använd`DocumentBuilder` för att infoga ett innehållsförteckningsfält i ditt dokument. Se till att uppdatera fälten i dokumentet efter att du har lagt till innehåll för att fylla i innehållsförteckningen. Här är ett exempel:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga ett innehållsförteckningsfält
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Lägg till dokumentinnehåll
// ...

// Uppdatera innehållsförteckningen
doc.updateFields();
```

### F: Hur infogar jag bilder i ett dokument med Aspose.Words för Java?

 S: Du kan infoga bilder, både inline och flytande, med hjälp av`DocumentBuilder`. Här är exempel på båda:

#### Inbäddad bild:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga en inline-bild
builder.insertImage("path/to/your/image.png");
```

#### Flytande bild:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga en flytande bild
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### F: Kan jag formatera text och stycken när jag lägger till innehåll?

 S: Ja, du kan formatera text och stycken med hjälp av`DocumentBuilder`. Du kan ställa in teckensnittsegenskaper, styckejustering, indrag och mer. Här är ett exempel:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Ställ in teckensnitt och styckeformatering
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

// Infoga ett formaterat stycke
builder.writeln("This is a formatted paragraph.");
```

### F: Hur kan jag flytta markören till en specifik plats i dokumentet?

 S: Du kan styra markörens position med metoder som`moveToParagraph`, `moveToCell`och mer. Här är ett exempel:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Flytta markören till ett specifikt stycke
builder.moveToParagraph(2, 0);

// Lägg till innehåll vid den nya markörpositionen
builder.writeln("This is the 3rd paragraph.");
```

Det här är några vanliga frågor och svar som hjälper dig att komma igång med Aspose.Words för Javas DocumentBuilder. Om du har fler frågor eller behöver mer hjälp, se[bibliotekets dokumentation](https://reference.aspose.com/words/java/) eller sök hjälp från Aspose.Words-gemenskapen och stödresurser.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
