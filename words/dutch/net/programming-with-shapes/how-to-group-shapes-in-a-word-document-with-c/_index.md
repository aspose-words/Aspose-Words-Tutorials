---
category: general
date: 2026-08-14
description: Hoe vormen groeperen in een Word-document met C#. Leer een Word-document
  maken, een rechthoekvorm invoegen, vormen groeperen in Word en het document opslaan
  als docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
language: nl
lastmod: 2026-08-14
og_description: Hoe vormen te groeperen in een Word‑document met C#. Volg deze complete
  tutorial om een Word‑bestand te maken, een rechthoekvorm in te voegen, vormen in
  Word te groeperen en het resultaat op te slaan als een docx.
og_image_alt: Screenshot showing how to group shapes in a Word document using C#
og_title: Hoe vormen te groeperen in een Word‑document met C# – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  headline: How to group shapes in a Word document with C#
  type: TechArticle
- description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  name: How to group shapes in a Word document with C#
  steps:
  - name: Create a new blank document
    text: The first thing you do when you want to **create Word document** programmatically
      is instantiate a `Document` object. This object represents the entire .docx
      file in memory.
  - name: Insert a rectangle shape
    text: To demonstrate **insert rectangle shape**, we use the `InsertShape` method.
      The rectangle will act as the first member of the group.
  - name: Insert an ellipse shape
    text: Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will
      be the second member of the group.
  - name: Group the rectangle and ellipse
    text: Now we answer the central question **how to group shapes** in a Word document.
      Aspose.Words provides `AppendGroupShape` to create a group container, and then
      you call `Group()` on that container.
  - name: Save the document as a DOCX file
    text: The final step is to **save document as docx**. You can choose any path
      you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should
      replace with a real folder.
  - name: Expected output
    text: When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue
      rectangle and a light‑coral ellipse locked together. Clicking either shape selects
      both, allowing you to move or resize them as a single unit.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Hoe vormen te groeperen in een Word‑document met C#
url: /nl/net/programming-with-shapes/how-to-group-shapes-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe vormen te groeperen in een Word‑document met C#

Als je **vormen wilt groeperen** in een Word‑document, laat deze gids je de exacte stappen zien met C# en de Aspose.Words‑bibliotheek. Je ziet hoe je een Word‑document maakt, een rechthoekvorm invoegt, vormen groepeert in Word, en uiteindelijk **document opslaat als docx** — alles in één uitvoerbaar programma.

Het maken en manipuleren van vormen is een veelvoorkomende eis bij het programmatic genereren van rapporten, contracten of marketingbrochures. Aan het einde van deze tutorial heb je een herbruikbaar code‑fragment dat je in elk .NET‑project kunt plaatsen.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

- .NET 6.0 of later geïnstalleerd  
- Visual Studio 2022 (of een andere IDE die .NET ondersteunt)  
- Een Aspose.Words for .NET‑licentie (of een gratis proefversie)  
- Basiskennis van C#‑syntaxis  

Er zijn geen extra NuGet‑pakketten nodig naast `Aspose.Words`.

## Hoe vormen te groeperen in een Word‑document

De kern van de oplossing bestaat uit een proces van vijf stappen. Elke stap wordt gedetailleerd uitgelegd en de volledige broncode staat aan het einde van het artikel.

### Stap 1: Maak een nieuw leeg document

Het eerste wat je doet wanneer je **een Word‑document wilt maken** via code, is een `Document`‑object instantieren. Dit object vertegenwoordigt het volledige .docx‑bestand in het geheugen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Obtain a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Waarom dit belangrijk is:** `DocumentBuilder` is een high‑level helper die je in staat stelt tekst, tabellen en vormen in te voegen zonder handmatig de onderliggende knoopstructuur te beheren.

### Stap 2: Voeg een rechthoekvorm toe

Om **een rechthoekvorm in te voegen** te demonstreren, gebruiken we de `InsertShape`‑methode. De rechthoek fungeert als het eerste lid van de groep.

```csharp
// Insert a rectangle (100x50 points) at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Optional: set a fill color so the shape is visible
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

**Waarom dit belangrijk is:** Vormen worden gepositioneerd ten opzichte van het invoegpunt. Het instellen van een vulkleur helpt je de vorm te zien wanneer je het resulterende document opent.

### Stap 3: Voeg een ellipsvorm toe

Vervolgens **voegen we een ellipsvorm toe** (de API noemt het `Ellipse`). Dit wordt het tweede lid van de groep.

```csharp
// Insert an ellipse (80x40 points) right after the rectangle
Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

**Waarom dit belangrijk is:** Door de ellips direct na de rechthoek in te voegen, komen beide vormen in dezelfde alinea terecht, wat het groeperen later vereenvoudigt.

### Stap 4: Groepeer de rechthoek en ellips

Nu beantwoorden we de centrale vraag **hoe vormen te groeperen** in een Word‑document. Aspose.Words biedt `AppendGroupShape` om een groepscontainer te maken, waarna je `Group()` aanroept op die container.

```csharp
// Get the first paragraph of the document (where the shapes live)
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;

// Create a group shape that contains the rectangle and ellipse
Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });

// Turn the container into a true group – the shapes will move and scale together
groupedShape.Group();
```

**Waarom dit belangrijk is:** Eenmaal gegroepeerd, heeft elke transformatie (verplaatsen, grootte wijzigen, roteren) die op `groupedShape` wordt toegepast automatisch effect op zowel de rechthoek als de ellips. Dit is essentieel voor het behouden van lay‑outconsistentie in gegenereerde documenten.

### Stap 5: Sla het document op als een DOCX‑bestand

De laatste stap is om **het document op te slaan als docx**. Je kunt elk gewenst pad gebruiken; het voorbeeld maakt gebruik van een tijdelijke placeholder `"YOUR_DIRECTORY"` die je moet vervangen door een echte map.

```csharp
// Define the output path (ensure the directory exists)
string outputPath = @"C:\Temp\groupedShapes.docx";

// Save the document in DOCX format
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

**Waarom dit belangrijk is:** Opslaan als DOCX behoudt de groeperings‑metadata, zodat je bij het openen van het bestand in Microsoft Word de rechthoek en ellips als één enkel object ziet.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het complete programma dat alle vijf stappen combineert. Kopieer het naar een nieuw console‑project, herstel het Aspose.Words‑NuGet‑pakket en voer het uit.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a rectangle shape (100x50 points)
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangleShape.FillColor = System.Drawing.Color.LightBlue;

            // Step 3: Insert an ellipse shape (80x40 points)
            Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
            ellipseShape.FillColor = System.Drawing.Color.LightCoral;

            // Step 4: Group the rectangle and ellipse
            Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
            Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });
            groupedShape.Group();

            // Step 5: Save the document as DOCX
            string outputPath = @"C:\Temp\groupedShapes.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

### Verwachte output

Wanneer je `groupedShapes.docx` opent in Microsoft Word, zie je een lichtblauwe rechthoek en een lichtkoraal‑ellips die aan elkaar vastzitten. Door op één van de vormen te klikken, worden beide geselecteerd, zodat je ze als één geheel kunt verplaatsen of van grootte kunt veranderen.

## Veelgestelde vragen en randgevallen

| Vraag | Antwoord |
|----------|--------|
| **Kan ik meer dan twee vormen groeperen?** | Ja. Geef een willekeurig aantal `Shape`‑objecten door aan `AppendGroupShape`. De methode accepteert een array, zodat je dynamisch een collectie kunt opbouwen. |
| **Wat als ik de groep wil verankeren aan een tabelcel?** | Voeg de vormen toe binnen de alinea van de cel en roep vervolgens `AppendGroupShape` aan op die alinea. De groep erft de verankering van de cel. |
| **Heeft groeperen invloed op de onderliggende XML?** | Aspose.Words schrijft een `<w:grpSp>`‑element dat de onderliggende vormen bevat. Word herkent dit als een groep en behoudt de relatieve positionering. |
| **Hoe kan ik later degroeperen?** | Roep `groupedShape.Ungroup()` aan; de methode retourneert de individuele vormen zodat je ze afzonderlijk kunt manipuleren. |
| **Is er een prestatie‑impact bij het groeperen van veel vormen?** | Groeperen zelf is onkostbaar, maar het renderen van zeer grote groepen (honderden vormen) kan de bestandsgrootte verhogen. Overweeg afbeeldingen te flattenen als de grootte een probleem wordt. |

## Pro‑tips

- **Stel expliciete posities in** (`Left`, `Top`) als je precieze uitlijning nodig hebt vóór het groeperen.  
- **Gebruik `Shape.WrapType = WrapType.Inline`** wanneer je wilt dat de groep zich gedraagt als een alinea‑element in plaats van een zwevend object.  
- **Pas een lijnstijl toe** op de groep (`groupedShape.LineFormat`) om de hele collectie een rand te geven.  
- **Herbruik de groep**: na het aanroepen van `Group()` kun je `groupedShape` klonen en de kloon elders in het document invoegen.

## Volgende stappen

Nu je weet **hoe vormen te groeperen** in een Word‑document, kun je gerelateerde onderwerpen verkennen, zoals:

- **Rechthoekvorm invoegen** met aangepaste tekst of afbeeldingen binnen de vorm.  
- **Complexe diagrammen maken** door groepen te nesten (een groep in een groep).  
- **Het document exporteren als PDF** terwijl de vormgroepering behouden blijft (`doc.Save("output.pdf", SaveFormat.Pdf)`).  

Elk van deze onderwerpen bouwt voort op dezelfde basisprincipes die hier zijn behandeld, zodat je goed gepositioneerd bent om je Word‑automatiseringstoolkit uit te breiden.

## Conclusie

Deze tutorial heeft **hoe vormen te groeperen** in een Word‑document met C# gedemonstreerd. Je hebt geleerd om **een Word‑document te maken**, **een rechthoekvorm in te voegen**, **vormen in Word te groeperen**, en uiteindelijk **het document op te slaan als docx**. Met het volledige, uitvoerbare voorbeeld en de praktische tips kun je vormgroepering integreren in elke document‑generatieworkflow. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}