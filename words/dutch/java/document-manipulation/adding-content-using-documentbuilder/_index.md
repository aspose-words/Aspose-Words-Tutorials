---
date: 2026-01-01
description: Leer hoe u formuliervelden maakt en tekst, tabellen, afbeeldingen, hyperlinks
  en meer toevoegt met Aspose.Words for Java DocumentBuilder. Een stapsgewijze handleiding
  voor ontwikkelaars.
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: Hoe formuliervelden te maken en inhoud toe te voegen met DocumentBuilder in
  Aspose.Words voor Java
url: /nl/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inhoud toevoegen met DocumentBuilder in Aspose.Words voor Java

## Introductie tot het toevoegen van inhoud met DocumentBuilder in Aspose.Words voor Java

In deze stapsgewijze handleiding **maakt u formulier velden** en voegt u diverse soorten inhoud toe—tekst, tabellen, horizontale lijnen, HTML, hyperlinks, afbeeldingen en meer—aan een Word‑document met Aspose.Words voor Java. Of u nu een rapport, een contracttemplate of een interactief formulier bouwt, de `DocumentBuilder`‑klasse geeft u fijnmazige controle over elk element. Laten we beginnen!

## Snelle antwoorden
- **Hoe maak ik formulier velden?** Gebruik `insertTextInput`, `insertCheckBox` of `insertComboBox` op een `DocumentBuilder`.
- **Welke methode voegt platte tekst toe?** Roep `builder.write("Your text")` of `builder.writeln("Your text")` aan.
- **Kan ik een horizontale lijn invoegen?** Ja—`builder.insertHorizontalRule()` voegt een lijnscheiding toe.
- **Hoe HTML insluiten?** Gebruik `builder.insertHtml("<p>HTML content</p>")`.
- **Hoe een inline afbeelding toevoegen?** `builder.insertImage("path/to/image.png")` plaatst de afbeelding binnen de tekststroom.

## Wat is DocumentBuilder en waarom gebruiken voor het maken van formulier velden?

`DocumentBuilder` is Aspose.Words’ vloeiende API voor het programmatic matig construeren en bewerken van Word‑documenten. Het abstraheert de low‑level OpenXML‑structuur, zodat u zich kunt concentreren op *wat* u wilt toevoegen—zoals **formulier velden**—in plaats van *hoe* de XML eruitziet. Dit maakt het ideaal voor het genereren van dynamische formulieren, contracten of elk document dat gebruikersinteractie vereist.

## Voorvereisten

Voordat u begint, zorg ervoor dat u de Aspose.Words for Java‑bibliotheek in uw project heeft geïnstalleerd. U kunt deze downloaden van [hier](https://releases.aspose.com/words/java/).

## Tekst toevoegen (hoe tekst toe te voegen)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Tabellen toevoegen

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

## Horizontale lijn toevoegen (voeg horizontale lijn toe)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## Formulier velden toevoegen (formulier velden maken)

### Tekstinvoer formulier veld

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Selectievakje formulier veld

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Keuzelijst formulier veld

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

## HTML toevoegen (html woord invoegen)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## Hyperlinks toevoegen (hoe hyperlink toe te voegen)

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

## Inhoudsopgave toevoegen

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

## Afbeeldingen toevoegen

### Inline afbeelding (inline afbeelding invoegen)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### Zwevende afbeelding

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## Alinea's toevoegen

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

## Cursor verplaatsen (Stap 10)

U kunt de cursorpositie in het document regelen met methoden zoals `moveToParagraph`, `moveToCell`, enz.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Dit zijn enkele veelvoorkomende bewerkingen die u kunt uitvoeren met Aspose.Words for Java's `DocumentBuilder`. Verken de documentatie van de bibliotheek voor meer geavanceerde functies en aanpassingsopties. Veel plezier met het maken van documenten!

## Conclusie

In deze uitgebreide handleiding hebben we laten zien hoe u **formulier velden** maakt en verschillende soorten inhoud toevoegt—tekst, tabellen, horizontale lijnen, HTML, hyperlinks, een inhoudsopgave, afbeeldingen, opgemaakte alinea's en cursor‑navigatie—met behulp van Aspose.Words for Java's `DocumentBuilder`. U beschikt nu over een solide basis om dynamische, interactieve Word‑documenten programmatic matig te genereren.

## FAQ's

### Q: Wat is Aspose.Words for Java?

A: Aspose.Words for Java is een Java‑bibliotheek die ontwikkelaars in staat stelt Microsoft Word‑documenten programmatic matig te maken, te wijzigen en te manipuleren. Het biedt een breed scala aan functies voor documentgeneratie, opmaak en inhoudsinvoeging.

### Q: Hoe kan ik een inhoudsopgave aan mijn document toevoegen?

A: Om een inhoudsopgave toe te voegen, gebruikt u de `DocumentBuilder` om een TOC‑veld in te voegen en roept u daarna `doc.updateFields()` aan nadat u uw inhoud hebt toegevoegd.

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

### Q: Hoe voeg ik afbeeldingen in een document in met Aspose.Words for Java?

A: U kunt afbeeldingen, zowel inline als zwevend, invoegen met de `DocumentBuilder`.

#### Inline afbeelding:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### Zwevende afbeelding:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q: Kan ik tekst en alinea's opmaken bij het toevoegen van inhoud?

A: Ja, u kunt tekst en alinea's opmaken met de `DocumentBuilder`. Stel lettertype‑eigenschappen, alinea‑uitlijning, inspringing en meer in voordat u inhoud schrijft.

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

### Q: Hoe kan ik de cursor naar een specifieke locatie in het document verplaatsen?

A: Gebruik methoden zoals `moveToParagraph`, `moveToCell`, enz., om de cursor te positioneren voordat u nieuwe inhoud invoegt.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Deze antwoorden behandelen de meest voorkomende scenario's bij het werken met Aspose.Words for Java's `DocumentBuilder`. Voor meer details, raadpleeg de [library's documentation](https://reference.aspose.com/words/java/) of word lid van de Aspose.Words‑community voor ondersteuning.

---

**Last Updated:** 2026-01-01  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}