---
"description": "Bemästra dokumentskapande med Aspose.Words för Java. En steg-för-steg-guide för att lägga till text, tabeller, bilder och mer. Skapa fantastiska Word-dokument utan ansträngning."
"linktitle": "Lägga till innehåll med hjälp av DocumentBuilder"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Lägga till innehåll med DocumentBuilder i Aspose.Words för Java"
"url": "/sv/java/document-manipulation/adding-content-using-documentbuilder/"
"weight": 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lägga till innehåll med DocumentBuilder i Aspose.Words för Java


## Introduktion till att lägga till innehåll med DocumentBuilder i Aspose.Words för Java

I den här steg-för-steg-guiden utforskar vi hur man använder Aspose.Words för Javas DocumentBuilder för att lägga till olika typer av innehåll i ett Word-dokument. Vi går igenom hur man infogar text, tabeller, horisontella linjer, formulärfält, HTML, hyperlänkar, innehållsförteckningar, inbäddade och flytande bilder, stycken och mer. Nu sätter vi igång!

## Förkunskapskrav

Innan du börjar, se till att du har konfigurerat Aspose.Words för Java-biblioteket i ditt projekt. Du kan ladda ner det från [här](https://releases.aspose.com/words/java/).

## Lägga till text

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

// Starta en tabell
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

## Lägga till horisontell linje

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga en horisontell linje
builder.insertHorizontalRule();

// Spara dokumentet
doc.save("path/to/your/document.docx");
```

## Lägga till formulärfält

### Textinmatningsfält

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga ett textinmatningsfält i formuläret
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Spara dokumentet
doc.save("path/to/your/document.docx");
```

### Kryssruta Formulärfält

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga ett kryssruteformulärfält
builder.insertCheckBox("CheckBox", true, true, 0);

// Spara dokumentet
doc.save("path/to/your/document.docx");
```

### Kombinationsruta Formulärfält

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

## Lägga till HTML

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
builder.insertHyperlink("Aspose Website", "http://"www.aspose.com", falskt);
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

### Inline-bild

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga en inbäddad bild
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

Du kan styra markörens position i dokumentet med olika metoder, som till exempel `moveToParagraph`, `moveToCell`och mer. Här är ett exempel:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Flytta markören till ett specifikt stycke
builder.moveToParagraph(2, 0);

// Lägg till innehåll vid den nya markörpositionen
builder.writeln("This is the 3rd paragraph.");
```

Här är några vanliga operationer du kan utföra med Aspose.Words för Javas DocumentBuilder. Utforska bibliotekets dokumentation för mer avancerade funktioner och anpassningsalternativ. Lycka till med dokumentskapandet!


## Slutsats

I den här omfattande guiden har vi utforskat möjligheterna med Aspose.Words för Javas DocumentBuilder för att lägga till olika typer av innehåll i Word-dokument. Vi har gått igenom text, tabeller, horisontella linjer, formulärfält, HTML, hyperlänkar, innehållsförteckningar, bilder, stycken och markörrörelser.

## Vanliga frågor

### F: Vad är Aspose.Words för Java?

A: Aspose.Words för Java är ett Java-bibliotek som låter utvecklare skapa, modifiera och manipulera Microsoft Word-dokument programmatiskt. Det erbjuder ett brett utbud av funktioner för dokumentgenerering, formatering och innehållsinsättning.

### F: Hur kan jag lägga till en innehållsförteckning i mitt dokument?

A: För att lägga till en innehållsförteckning, använd `DocumentBuilder` för att infoga ett fält för innehållsförteckning i ditt dokument. Se till att uppdatera fälten i dokumentet efter att du har lagt till innehåll för att fylla innehållsförteckningen. Här är ett exempel:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga ett fält för innehållsförteckning
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Lägg till dokumentinnehåll
// ...

// Uppdatera innehållsförteckningen
doc.updateFields();
```

### F: Hur infogar jag bilder i ett dokument med Aspose.Words för Java?

A: Du kan infoga bilder, både inbäddade och flytande, med hjälp av `DocumentBuilder`Här är exempel på båda:

#### Inbäddad bild:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Infoga en inbäddad bild
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

A: Ja, du kan formatera text och stycken med hjälp av `DocumentBuilder`Du kan ange teckensnittsegenskaper, styckejustering, indentering med mera. Här är ett exempel:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Ange teckensnitt och styckeformatering
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

A: Du kan styra markörens position med metoder som `moveToParagraph`, `moveToCell`och mer. Här är ett exempel:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Flytta markören till ett specifikt stycke
builder.moveToParagraph(2, 0);

// Lägg till innehåll vid den nya markörpositionen
builder.writeln("This is the 3rd paragraph.");
```

Här är några vanliga frågor och svar som hjälper dig att komma igång med Aspose.Words för Javas DocumentBuilder. Om du har fler frågor eller behöver ytterligare hjälp kan du läsa mer på [bibliotekets dokumentation](https://reference.aspose.com/words/java/) eller sök hjälp från Aspose.Words-communityn och supportresurserna.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}