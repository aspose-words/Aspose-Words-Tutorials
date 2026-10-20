---
date: 2026-01-01
description: Lär dig hur du skapar formulärfält och lägger till text, tabeller, bilder,
  hyperlänkar och mer med Aspose.Words för Java DocumentBuilder. En steg‑för‑steg‑guide
  för utvecklare.
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: Hur man skapar formulärfält och lägger till innehåll med DocumentBuilder i
  Aspose.Words för Java
url: /sv/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lägga till innehåll med DocumentBuilder i Aspose.Words för Java

## Introduktion till att lägga till innehåll med DocumentBuilder i Aspose.Words för Java

I den här steg‑för‑steg‑guiden kommer du att **skapa formulärfält** och lägga till en mängd olika innehåll—text, tabeller, horisontella linjer, HTML, hyperlänkar, bilder och mer—i ett Word‑dokument med Aspose.Words för Java. Oavsett om du bygger en rapport, en kontraktsmall eller ett interaktivt formulär, ger `DocumentBuilder`‑klassen dig fin‑granulär kontroll över varje element. Låt oss dyka ner!

## Snabba svar
- **Hur skapar jag formulärfält?** Använd `insertTextInput`, `insertCheckBox` eller `insertComboBox` på en `DocumentBuilder`.
- **Vilken metod lägger till vanlig text?** Anropa `builder.write("Your text")` eller `builder.writeln("Your text")`.
- **Kan jag infoga en horisontell linje?** Ja—`builder.insertHorizontalRule()` lägger till en linjeskiljare.
- **Hur bäddar jag in HTML?** Använd `builder.insertHtml("<p>HTML content</p>")`.
- **Hur lägger jag till en infogad bild?** `builder.insertImage("path/to/image.png")` placerar bilden i textflödet.

## Vad är DocumentBuilder och varför använda det för att skapa formulärfält?

`DocumentBuilder` är Aspose.Words flödande API för att programatiskt konstruera och redigera Word‑dokument. Det abstraherar den lågnivå OpenXML‑strukturen, så att du kan fokusera på *vad* du vill lägga till—såsom **form fields**—istället för *hur* XML‑en ser ut. Detta gör det idealiskt för att generera dynamiska formulär, kontrakt eller vilket dokument som helst som kräver användarinteraktion.

## Förutsättningar

Innan du börjar, se till att du har Aspose.Words för Java‑biblioteket installerat i ditt projekt. Du kan ladda ner det från [here](https://releases.aspose.com/words/java/).

## Lägga till text (hur man lägger till text)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Lägga till tabeller

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

## Lägga till en horisontell linje (lägg till horisontell linje)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## Lägga till formulärfält (skapa formulärfält)

### Textinmatningsformulärfält

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Kryssruta formulärfält

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Kombinationsruta formulärfält

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

## Lägga till HTML (infoga HTML)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## Lägga till hyperlänkar (hur man lägger till hyperlänk)

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

## Lägga till en innehållsförteckning

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

## Lägga till bilder

### Infogad bild (infoga infogad bild)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### Flytande bild

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## Lägga till stycken

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

## Flytta markören (Steg 10)

Du kan kontrollera markörens position i dokumentet med metoder som `moveToParagraph`, `moveToCell` osv.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Detta är några vanliga operationer du kan utföra med Aspose.Words för Java's `DocumentBuilder`. Utforska bibliotekets dokumentation för mer avancerade funktioner och anpassningsalternativ. Lycka till med dokumentskapandet!

## Slutsats

I den här omfattande guiden har vi visat hur man **skapar formulärfält** och lägger till olika typer av innehåll—text, tabeller, horisontella linjer, HTML, hyperlänkar, en innehållsförteckning, bilder, formaterade stycken och markörnavigering—med Aspose.Words för Java's `DocumentBuilder`. Du har nu en solid grund för att programatiskt generera dynamiska, interaktiva Word‑dokument.

## Vanliga frågor

### Q: Vad är Aspose.Words för Java?

A: Aspose.Words för Java är ett Java‑bibliotek som låter utvecklare skapa, modifiera och manipulera Microsoft Word‑dokument programatiskt. Det erbjuder ett brett spektrum av funktioner för dokumentgenerering, formatering och innehållsinsättning.

### Q: Hur kan jag lägga till en innehållsförteckning i mitt dokument?

A: För att lägga till en innehållsförteckning, använd `DocumentBuilder` för att infoga ett TOC‑fält och anropa sedan `doc.updateFields()` efter att du har lagt till ditt innehåll.

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

### Q: Hur infogar jag bilder i ett dokument med Aspose.Words för Java?

A: Du kan infoga bilder, både infogade och flytande, med hjälp av `DocumentBuilder`.

#### Infogad bild:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### Flytande bild:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q: Kan jag formatera text och stycken när jag lägger till innehåll?

A: Ja, du kan formatera text och stycken med `DocumentBuilder`. Ställ in teckensnittsegenskaper, styckejustering, indrag och mer innan du skriver innehåll.

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

### Q: Hur kan jag flytta markören till en specifik plats i dokumentet?

A: Använd metoder som `moveToParagraph`, `moveToCell` osv. för att placera markören innan du infogar nytt innehåll.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Dessa svar täcker de vanligaste scenarierna när du arbetar med Aspose.Words för Java's `DocumentBuilder`. För djupare detaljer, se [library's documentation](https://reference.aspose.com/words/java/) eller gå med i Aspose.Words‑gemenskapen för support.

---

**Senast uppdaterad:** 2026-01-01  
**Testat med:** Aspose.Words for Java 24.12  
**Författare:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}