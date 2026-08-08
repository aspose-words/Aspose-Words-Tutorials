---
category: general
date: 2026-08-07
description: Hoe vormen te groeperen in Word met Aspose.Words en vormen toe te voegen
  aan een Word‑document met C#. Volg deze stapsgewijze gids voor schone, herbruikbare
  code.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- add shapes to word document
language: nl
lastmod: 2026-08-07
og_description: Hoe vormen te groeperen in Word met Aspose.Words voor .NET. Deze tutorial
  laat zien hoe je vormen aan een Word‑document toevoegt, ze groepeert en het bestand
  opslaat met duidelijke C#‑code.
og_image_alt: Screenshot of a rectangle and ellipse grouped in a Word document created
  with Aspose.Words
og_title: Hoe vormen groeperen in Word – snelle C#‑gids
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  headline: How to group shapes in Word and add shapes to Word document
  type: TechArticle
- description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  name: How to group shapes in Word and add shapes to Word document
  steps:
  - name: Create a document and a builder
    text: A `Document` object represents the entire DOCX file. `DocumentBuilder` provides
      a convenient API for editing the document.
  - name: Add the rectangle shape
    text: A rectangle is created by specifying `ShapeType.Rectangle`. Width, height,
      and location are set in points (1 pt ≈ 1/72 in).
  - name: Add the ellipse shape
    text: The ellipse uses `ShapeType.Ellipse`. Its size and position are independent
      of the rectangle, which allows you to control the final layout of the group.
  - name: Group the two shapes
    text: '`GroupShape` acts as a container that treats its children as a single object.
      This is the essential operation for **how to group shapes in Word**.'
  - name: Insert the grouped shape into the document
    text: '`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor
      location. Because we have not moved the builder, the group appears at the start
      of the first page.'
  - name: Save the document
    text: Finally, write the DOCX file to disk. Use a full path that your application
      can write to.
  - name: Expected output
    text: Open `GroupShape.docx`. You will see a single visual object that contains
      a blue rectangle on the left and a green ellipse on the right. Selecting the
      object in Word highlights both shapes simultaneously—proof that **how to group
      shapes in Word** succeeded.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Hoe vormen te groeperen in Word en vormen aan een Word‑document toe te voegen
url: /nl/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe vormen groeperen in Word en vormen toevoegen aan een Word‑document

Als je **hoe vormen groeperen in Word** nodig hebt, leidt deze gids je door het volledige proces met behulp van Aspose.Words voor .NET. Je leert ook **vormen toevoegen aan een Word‑document** met een paar regels C#‑code, zodat het resultaat klaar is voor elke rapportage‑ of sjabloonsituatie.

De tutorial behandelt alles wat je nodig hebt: vereiste NuGet‑pakketten, een volledig bronbestand en een uitleg waarom elke stap belangrijk is. Aan het einde kun je een DOCX genereren die een rechthoek en een ellips bevat, gecombineerd tot één groepsvorm.

## Vereisten

* .NET 6.0 SDK of later geïnstalleerd  
* Visual Studio 2022 (of elke IDE die .NET ondersteunt)  
* Aspose.Words for .NET NuGet‑pakket (`Aspose.Words`) – de gratis proefversie werkt voor testen, maar een licentie verwijdert evaluatiewatermerken  

Deze items zijn de enige externe afhankelijkheden voor **vormen toevoegen aan een Word‑document**.

## Hoe vormen groeperen in Word

De kern van de oplossing is het maken van individuele vormen, ze op de pagina plaatsen en ze vervolgens in een `GroupShape` verpakken. De volgende stappen volgen de logische volgorde van de code.

### Stap 1: Een document en een builder maken

Een `Document`‑object vertegenwoordigt het volledige DOCX‑bestand. `DocumentBuilder` biedt een handige API voor het bewerken van het document.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create an empty Word document
Document doc = new Document();

// DocumentBuilder lets you insert nodes, text, and shapes
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Waarom dit belangrijk is*: De `Document` is de container voor alle Word‑elementen. De `DocumentBuilder` houdt de huidige cursorpositie bij, wat nodig is wanneer je later de gegroepeerde vorm invoegt.

### Stap 2: De rechthoekvorm toevoegen

Een rechthoek wordt gemaakt door `ShapeType.Rectangle` op te geven. Breedte, hoogte en locatie worden ingesteld in punten (1 pt ≈ 1/72 in).

```csharp
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;               // 100 pt wide
rectangleShape.Height = 50;               // 50 pt tall
rectangleShape.Left = 0;                  // X‑coordinate
rectangleShape.Top = 0;                   // Y‑coordinate
rectangleShape.StrokeColor = Color.Blue; // Outline color
```

*Waarom dit belangrijk is*: Het instellen van `StrokeColor` maakt de vorm zichtbaar wanneer het document wordt geopend. Je kunt de vorm ook vullen met `FillColor` als een solide binnenkant vereist is.

### Stap 3: De ellipsvorm toevoegen

De ellips gebruikt `ShapeType.Ellipse`. De grootte en positie zijn onafhankelijk van de rechthoek, waardoor je de uiteindelijke lay‑out van de groep kunt bepalen.

```csharp
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;
ellipseShape.Height = 80;
ellipseShape.Left = 120;                  // Placed to the right of the rectangle
ellipseShape.Top = 0;
ellipseShape.StrokeColor = Color.Green;
```

*Waarom dit belangrijk is*: Door de ellips te positioneren op `Left = 120`, overlapt deze niet met de rechthoek, waardoor de groep visueel duidelijk is.

### Stap 4: De twee vormen groeperen

`GroupShape` fungeert als een container die zijn kinderen als één object behandelt. Dit is de essentiële bewerking voor **hoe vormen groeperen in Word**.

```csharp
GroupShape groupShape = new GroupShape(doc);
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);
```

*Waarom dit belangrijk is*: Groeperen maakt het mogelijk om beide vormen samen te verplaatsen, van grootte te wijzigen of te roteren. Elke transformatie die op `groupShape` wordt toegepast, wordt doorgegeven aan de kinderen.

### Stap 5: De gegroepeerde vorm in het document invoegen

`DocumentBuilder.InsertNode` plaatst de `GroupShape` op de huidige cursorlocatie. Omdat we de builder niet hebben verplaatst, verschijnt de groep aan het begin van de eerste pagina.

```csharp
builder.InsertNode(groupShape);
```

*Waarom dit belangrijk is*: Het direct invoegen van de node voorkomt de noodzaak van een apart alinea‑ of tabelcelformaat. De groep wordt onderdeel van de documentstroom.

### Stap 6: Het document opslaan

Schrijf tenslotte het DOCX‑bestand naar schijf. Gebruik een volledig pad waar jouw applicatie naar kan schrijven.

```csharp
doc.Save(@"C:\Temp\GroupShape.docx");
```

*Waarom dit belangrijk is*: `doc.Save` finaliseert alle wijzigingen. Het resulterende bestand kan worden geopend in Microsoft Word, LibreOffice of elke viewer die DOCX ondersteunt.

## Volledig bronbestand

Kopieer de code hieronder naar een nieuw console‑project (`dotnet new console`) en voer het uit. Het programma maakt een bestand genaamd `GroupShape.docx` aan dat een gegroepeerde rechthoek en ellips bevat.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeGrouping
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Define a rectangle shape
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
            rectangleShape.Width = 100;
            rectangleShape.Height = 50;
            rectangleShape.Left = 0;
            rectangleShape.Top = 0;
            rectangleShape.StrokeColor = Color.Blue;

            // Step 3: Define an ellipse shape
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
            ellipseShape.Width = 80;
            ellipseShape.Height = 80;
            ellipseShape.Left = 120;
            ellipseShape.Top = 0;
            ellipseShape.StrokeColor = Color.Green;

            // Step 4: Group the two shapes together
            GroupShape groupShape = new GroupShape(doc);
            groupShape.AppendChild(rectangleShape);
            groupShape.AppendChild(ellipseShape);

            // Step 5: Insert the grouped shape into the document
            builder.InsertNode(groupShape);

            // Step 6: Save the document
            doc.Save(@"C:\Temp\GroupShape.docx");
        }
    }
}
```

### Verwachte output

Open `GroupShape.docx`. Je ziet één visueel object dat een blauwe rechthoek links en een groene ellips rechts bevat. Het selecteren van het object in Word markeert beide vormen tegelijk — bewijs dat **hoe vormen groeperen in Word** geslaagd is.

## Veelgestelde vragen en randgevallen

* **Kan ik meer dan twee vormen toevoegen?**  
  Ja. Roep `groupShape.AppendChild` aan voor elke extra `Shape` voordat je de groep invoegt.

* **Wat als ik de groep moet roteren?**  
  Stel `groupShape.RotationAngle = 45;` (hoek in graden) in nadat de groep is opgebouwd.

* **Moet ik `doc.UpdatePageLayout()` aanroepen?**  
  Niet voor dit scenario. De lay‑out wordt automatisch bijgewerkt wanneer het document wordt opgeslagen.

* **Hoe beïnvloedt licentiëren de code?**  
  Met een geldige Aspose.Words‑licentie (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) bevat het gegenereerde document geen evaluatiewatermerk.

## Conclusie

Je weet nu **hoe vormen groeperen in Word** en **vormen toevoegen aan een Word‑document** met Aspose.Words voor .NET. De tutorial besprak het maken van een document, het definiëren van individuele vormen, het groeperen ervan, het invoegen van de groep en het opslaan van het bestand.  

Vanaf hier kun je experimenteren met:

* Tekstvakken of afbeeldingen aan de groep toevoegen  
* Vullingskleuren, lijntypen of schaduweffecten wijzigen  
* Vormen groeperen binnen tabellen of kop‑ en voetteksten  

Deze uitbreidingen stellen je in staat om geavanceerde Word‑sjablonen programmatisch te bouwen, terwijl de code schoon en onderhoudbaar blijft. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}