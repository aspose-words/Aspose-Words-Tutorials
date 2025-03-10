---
title: Inhoud toevoegen met DocumentBuilder in Aspose.Words voor Java
linktitle: Inhoud toevoegen met DocumentBuilder
second_title: Aspose.Words Java Documentverwerkings-API
description: Master Document Creation met Aspose.Words voor Java. Een stapsgewijze handleiding voor het toevoegen van tekst, tabellen, afbeeldingen en meer. Maak moeiteloos verbluffende Word-documenten.
weight: 26
url: /nl/java/document-manipulation/adding-content-using-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inhoud toevoegen met DocumentBuilder in Aspose.Words voor Java


## Inleiding tot het toevoegen van inhoud met DocumentBuilder in Aspose.Words voor Java

In deze stapsgewijze handleiding gaan we onderzoeken hoe je Aspose.Words voor Java's DocumentBuilder kunt gebruiken om verschillende soorten content toe te voegen aan een Word-document. We behandelen het invoegen van tekst, tabellen, horizontale regels, formuliervelden, HTML, hyperlinks, inhoudsopgaven, inline en zwevende afbeeldingen, alinea's en meer. Laten we beginnen!

## Vereisten

 Voordat u begint, moet u ervoor zorgen dat u de Aspose.Words for Java-bibliotheek in uw project hebt ingesteld. U kunt deze downloaden van[hier](https://releases.aspose.com/words/java/).

## Tekst toevoegen

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Voeg een eenvoudige tekstparagraaf in
builder.write("This is a simple text paragraph.");

// Sla het document op
doc.save("path/to/your/document.docx");
```

## Tabellen toevoegen

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

//Start een tabel
Table table = builder.startTable();

// Cellen en inhoud invoegen
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// Maak de tafel af
builder.endTable();

// Sla het document op
doc.save("path/to/your/document.docx");
```

## Horizontale regel toevoegen

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Een horizontale regel invoegen
builder.insertHorizontalRule();

// Sla het document op
doc.save("path/to/your/document.docx");
```

## Formuliervelden toevoegen

### Tekst invoerformulier veld

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Een tekstinvoerveld invoegen
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Sla het document op
doc.save("path/to/your/document.docx");
```

### Selectievakje Formulierveld

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Een selectievakje in een formulierveld invoegen
builder.insertCheckBox("CheckBox", true, true, 0);

// Sla het document op
doc.save("path/to/your/document.docx");
```

### Keuzelijst met invoervakformulierveld

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Items voor de keuzelijst definiëren
String[] items = { "Option 1", "Option 2", "Option 3" };

// Een keuzelijst met invoervak invoegen
builder.insertComboBox("DropDown", items, 0);

// Sla het document op
doc.save("path/to/your/document.docx");
```

## HTML toevoegen

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// HTML-inhoud invoegen
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Sla het document op
doc.save("path/to/your/document.docx");
```

## Hyperlinks toevoegen

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Een hyperlink invoegen
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", onwaar);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Sla het document op
doc.save("path/to/your/document.docx");
```

## Een inhoudsopgave toevoegen

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Inhoudsopgave invoegen
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Documentinhoud toevoegen
// ...

// Inhoudsopgave bijwerken
doc.updateFields();

// Sla het document op
doc.save("path/to/your/document.docx");
```

## Afbeeldingen toevoegen

### Inline-afbeelding

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Een inline-afbeelding invoegen
builder.insertImage("path/to/your/image.png");

// Sla het document op
doc.save("path/to/your/document.docx");
```

### Zwevende afbeelding

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Een zwevende afbeelding invoegen
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Sla het document op
doc.save("path/to/your/document.docx");
```

## Alinea's toevoegen

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Alinea-opmaak instellen
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

// Een alinea invoegen
builder.writeln("This is a formatted paragraph.");

// Sla het document op
doc.save("path/to/your/document.docx");
```

## Stap 10: De cursor verplaatsen

 U kunt de cursorpositie binnen het document op verschillende manieren regelen, zoals:`moveToParagraph`, `moveToCell`en meer. Hier is een voorbeeld:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Verplaats de cursor naar een specifieke alinea
builder.moveToParagraph(2, 0);

// Voeg inhoud toe op de nieuwe cursorpositie
builder.writeln("This is the 3rd paragraph.");
```

Dit zijn enkele veelvoorkomende bewerkingen die u kunt uitvoeren met Aspose.Words voor Java's DocumentBuilder. Bekijk de documentatie van de bibliotheek voor meer geavanceerde functies en aanpassingsopties. Veel plezier met het maken van documenten!


## Conclusie

In deze uitgebreide gids hebben we de mogelijkheden van Aspose.Words voor Java's DocumentBuilder onderzocht om verschillende soorten content toe te voegen aan Word-documenten. We hebben tekst, tabellen, horizontale regels, formuliervelden, HTML, hyperlinks, inhoudsopgaven, afbeeldingen, paragrafen en cursorbewegingen behandeld.

## Veelgestelde vragen

### V: Wat is Aspose.Words voor Java?

A: Aspose.Words voor Java is een Java-bibliotheek waarmee ontwikkelaars Microsoft Word-documenten programmatisch kunnen maken, wijzigen en manipuleren. Het biedt een breed scala aan functies voor het genereren, opmaken en invoegen van inhoud van documenten.

### V: Hoe kan ik een inhoudsopgave aan mijn document toevoegen?

A: Om een inhoudsopgave toe te voegen, gebruikt u de`DocumentBuilder` om een inhoudsopgaveveld in uw document in te voegen. Zorg ervoor dat u de velden in het document bijwerkt nadat u inhoud hebt toegevoegd om de inhoudsopgave te vullen. Hier is een voorbeeld:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Voeg een inhoudsopgaveveld in
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Documentinhoud toevoegen
// ...

// Inhoudsopgave bijwerken
doc.updateFields();
```

### V: Hoe voeg ik afbeeldingen in een document in met Aspose.Words voor Java?

 A: U kunt afbeeldingen invoegen, zowel inline als zwevend, met behulp van de`DocumentBuilder`Hier zijn voorbeelden van beide:

#### Inline-afbeelding:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Een inline-afbeelding invoegen
builder.insertImage("path/to/your/image.png");
```

#### Zwevende afbeelding:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Een zwevende afbeelding invoegen
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### V: Kan ik tekst en alinea's opmaken wanneer ik inhoud toevoeg?

 A: Ja, u kunt tekst en alinea's opmaken met behulp van de`DocumentBuilder`. U kunt lettertype-eigenschappen, alinea-uitlijning, inspringing en meer instellen. Hier is een voorbeeld:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Lettertype en alinea-opmaak instellen
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

// Een opgemaakte alinea invoegen
builder.writeln("This is a formatted paragraph.");
```

### V: Hoe kan ik de cursor naar een specifieke locatie in het document verplaatsen?

 A: U kunt de cursorpositie regelen met behulp van methoden zoals`moveToParagraph`, `moveToCell`en meer. Hier is een voorbeeld:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Verplaats de cursor naar een specifieke alinea
builder.moveToParagraph(2, 0);

// Voeg inhoud toe op de nieuwe cursorpositie
builder.writeln("This is the 3rd paragraph.");
```

Dit zijn enkele veelvoorkomende vragen en antwoorden om u te helpen aan de slag te gaan met Aspose.Words voor Java's DocumentBuilder. Als u meer vragen hebt of verdere assistentie nodig hebt, raadpleeg dan de[documentatie van de bibliotheek](https://reference.aspose.com/words/java/) of zoek hulp bij de Aspose.Words-community en ondersteuningsbronnen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
