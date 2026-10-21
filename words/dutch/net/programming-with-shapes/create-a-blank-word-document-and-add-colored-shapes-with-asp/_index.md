---
category: general
date: 2026-09-21
description: Maak een leeg Word‑document met Aspose.Words, stel de vormgrootte in,
  stel de vormpositie in, stel de vormkleur in en sla het docx‑bestand op in één doorloop.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: nl
lastmod: 2026-09-21
og_description: Maak een leeg Word‑document, stel de vormgrootte in, stel de vormpositie
  in, stel de vormkleur in, en sla het docx‑bestand met Aspose.Words in enkele minuten
  op.
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: Maak een leeg Word‑document en voeg gekleurde vormen toe – Aspose.Words‑gids
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Maak een leeg Word‑document en voeg gekleurde vormen toe met Aspose.Words
url: /nl/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een leeg Word‑document en voeg gekleurde vormen toe met Aspose.Words

Als je programmatically een **leeg Word‑document wilt maken**, laat deze gids je zien hoe met Aspose.Words. Je leert hoe je **de vormgrootte instelt**, **de vormpositie instelt**, **de vormkleur instelt**, en uiteindelijk **het docx‑bestand opslaat** zonder je IDE te verlaten.

Werken met Word‑bestanden in C# betekent vaak het jongleren met low‑level OpenXML‑aanroepen, maar Aspose.Words abstraheert de complexiteit. Aan het einde van deze tutorial heb je een volledig functioneel `.docx`‑bestand dat een gegroepeerde vorm bevat bestaande uit twee gekleurde rechthoeken — perfect voor rapporten, certificaten of aangepaste sjablonen.

## Prerequisites

- .NET 6.0 of hoger (de code werkt ook met .NET Framework 4.7+)
- Aspose.Words for .NET 23.9 of nieuwer (installeren via NuGet: `Install-Package Aspose.Words`)
- Basiskennis van C# en Visual Studio (of een andere C#‑editor)

Er is geen bestaand Word‑bestand nodig; de tutorial begint met **het maken van een leeg Word‑document** vanaf nul.

## Maak een leeg Word‑document met Aspose.Words

De eerste stap is het instantieren van een `Document`‑object. Dit object vertegenwoordigt een leeg Word‑bestand in het geheugen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` begint leeg, wat precies is wat je nodig hebt wanneer je **een leeg Word‑document maakt**. De `builder` wordt later gebruikt om de vormgroep in te voegen op de huidige cursorpositie.

## Stel vormgrootte in en maak een GroupShape

Een `GroupShape` werkt als een container die meerdere individuele vormen kan bevatten. Definieer eerst de totale afmetingen van de container.

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

Hier stellen we de **vormgrootte** in voor de groep zelf (300 × 200). Dezelfde eigenschapsnamen (`Width`, `Height`) worden gebruikt voor elke onderliggende vorm, waardoor je fijnmazige controle over elk element hebt.

## Voeg de eerste rechthoek toe en stel vormkleur in

Voeg nu een rechthoek toe aan de groep en geef deze een achtergrondkleur.

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

De eigenschap `FillColor` **stelt de vormkleur in**. Met `System.Drawing.Color` kun je elke vooraf gedefinieerde of aangepaste ARGB‑waarde kiezen.

## Voeg een tweede rechthoek toe, stel grootte, positie en kleur in

Een tweede rechthoek toont hoe je **de vormpositie** relatief aan de groep instelt en hoe je de kleur wijzigt.

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

Omdat de breedte van de groep 300 punten is, passen de twee rechthoeken van 120 punten comfortabel met een tussenruimte van 30 punten. Pas `Left` en `Top` aan als je een andere lay-out nodig hebt.

## Voeg de GroupShape in het document in

Met de groep volledig geconfigureerd, plaats je deze op de huidige cursorpositie.

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode` schrijft de vorm direct in de body van het document, waarbij de exacte **ingestelde vormpositie** die je eerder hebt gedefinieerd behouden blijft.

## Sla het docx‑bestand op

De laatste stap is het document op schijf op te slaan. Dit demonstreert de **save docx file**‑operatie.

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

Na het uitvoeren van het programma, open `GroupShape.docx` in Microsoft Word. Je zou een lege pagina moeten zien met een gegroepeerde vorm die twee gekleurde rechthoeken bevat, naast elkaar geplaatst.

### Verwachte output

- Een één‑pagina `.docx`‑bestand.
- De pagina bevat een groepsvorm die zich 100 pt van de linker‑ en bovenmarge bevindt.
- Binnen de groep bevindt zich een lichtblauwe rechthoek links en een lichtkoraalrode rechthoek rechts, elk 120 × 80 pt.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren‑en‑plakken in een console‑applicatie. Er zijn geen extra bestanden nodig.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Het uitvoeren van dit programma maakt het exacte document dat eerder is beschreven, en voldoet aan alle vier de doelstellingen: **leeg Word‑document maken**, **vormgrootte instellen**, **vormpositie instellen**, **vormkleur instellen**, en **docx‑bestand opslaan**.

## Veelvoorkomende variaties en randgevallen

| Scenario | Wat te wijzigen | Waarom het belangrijk is |
|----------|----------------|--------------------------|
| **Verschillende vormtypen** | Vervang `ShapeType.Rectangle` door `ShapeType.Ellipse`, `ShapeType.Triangle`, enz. | Staat je toe complexere grafische elementen te maken zonder externe afbeeldingen. |
| **Dynamische afmetingen** | Bereken `Width` en `Height` op basis van gebruikersinvoer of configuratiebestanden. | Maakt de oplossing herbruikbaar voor meerdere documenttemplates. |
| **Opslaan als PDF** | Roep `document.Save("output.pdf", SaveFormat.Pdf);` aan. | Als ontvangers een niet‑bewerkbaar formaat nodig hebben, is PDF een veilige keuze. |
| **Tekst toevoegen binnen een vorm** | Maak een `TextBox`‑vorm en stel `TextBox.Text` in. | Handig voor het maken van gelabelde badges of bijschriften. |
| **Meerdere groepen op één pagina** | Herhaal stappen 2‑5 met verschillende `Left`/`Top`‑waarden. | Staat je toe dashboards of lay‑outs met meerdere secties te bouwen. |

### Pro tip

Wanneer je vormen precies moet uitlijnen, gebruik dan de eigenschap `ShapeBase.WrapType = WrapType.Inline` vóór het invoegen van de groep. Dit dwingt de groep zich te gedragen als een alinea, waardoor onverwachte tekstomloop eromheen wordt voorkomen.

## Conclusie

Je weet nu hoe je met Aspose.Words een **leeg Word‑document kunt maken**, **vormgrootte kunt instellen**, **vormpositie kunt instellen**, **vormkleur kunt instellen**, en **het docx‑bestand kunt opslaan**. Het volledige voorbeeld toont een schoon, herbruikbaar patroon voor het toevoegen van gegroepeerde grafische elementen aan elk Word‑automatiseringsproject.

Vanaf hier kun je verkennen:

- Meer vormen of afbeeldingen toevoegen aan dezelfde `GroupShape` (**vormgrootte instellen**, **vormkleur instellen** variaties).
- `ShapeBase.Rotation` gebruiken om rechthoeken te roteren voor decoratieve effecten.
- Hetzelfde document exporteren als PDF of HTML om de distributie uit te breiden (**save docx file**‑alternatief).

Voel je vrij om te experimenteren met verschillende kleuren, groottes en lay‑outlogica om aan je specifieke rapportage‑ of sjabloonbehoeften te voldoen. Veel plezier met coderen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}