---
category: general
date: 2026-09-18
description: Maak een rechthoekvorm in een Word‑document met C#. Leer hoe je meerdere
  vormen toevoegt, vormen aan een groep toevoegt en een groepsvorm invoegt met Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: nl
lastmod: 2026-09-18
og_description: Maak een rechthoekvorm in een Word‑bestand met C#. Deze gids laat
  zien hoe je meerdere vormen toevoegt, vormen aan een groep toevoegt en een groepsvorm
  invoegt met Aspose.Words.
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: Maak een rechthoekvorm en groepeer vormen in C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: Maak een rechthoekvorm en groepeer meerdere vormen in C#
url: /nl/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoekvorm maken en meerdere vormen groeperen in C#

Als u een **create rectangle shape** in een Word‑document moet maken, toont deze tutorial een volledige oplossing. U ziet hoe u **add multiple shapes**, **add shapes to group**, en **insert group shape** kunt gebruiken met de Aspose.Words API voor .NET.

Werken met vormen is een veelvoorkomende vereiste bij het programmatically genereren van rapporten, contracten of marketingmateriaal. Aan het einde van deze gids heeft u een uitvoerbare C# console‑applicatie die een `.docx`‑bestand produceert met een rechthoek, een ellips en een groep die beide vormen bevat.

De enige vereisten zijn een recente .NET SDK (6.0 of hoger) en een gelicentieerde kopie van Aspose.Words voor .NET. Er zijn geen extra tools nodig.

## Prerequisites

- .NET 6.0 SDK of nieuwer  
- Aspose.Words voor .NET (NuGet‑pakket `Aspose.Words`)  
- Basiskennis van C#‑syntaxis  

U kunt het pakket installeren met de volgende opdracht:

```bash
dotnet add package Aspose.Words
```

## Stap 1: Rechthoekvorm maken met Aspose.Words

De eerste stap is het maken van een `Shape`‑object van het type `Rectangle`. Dit object vertegenwoordigt de visuele rechthoek die in het document zal verschijnen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**Waarom dit belangrijk is:** `ShapeType.Rectangle` vertelt Aspose.Words om een geometrische rechthoek te renderen. Het instellen van `Width` en `Height` bepaalt de grootte in points (1 point = 1/72 inch). Het toevoegen van vul‑ en lijnkleuren maakt de vorm zichtbaar zonder extra opmaak.

## Stap 2: Meerdere vormen toevoegen aan het document

Na de rechthoek kunt u een willekeurig aantal extra vormen maken. In dit voorbeeld voegen we een ellips toe om te demonstreren hoe **add multiple shapes** werkt.

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**Waarom dit belangrijk is:** Elke aanroep van `new Shape` creëert een onafhankelijk tekenobject. Door ze opeenvolgend in te voegen bouwt u een verzameling vormen op die later gegroepeerd of individueel gepositioneerd kan worden.

## Stap 3: Vormen aan een groep toevoegen

Het groeperen van vormen vereenvoudigt lay‑outbeheer omdat de groep zich gedraagt als één knooppunt. Deze stap toont hoe u **add shapes to group** kunt gebruiken met `GroupShape`.

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**Waarom dit belangrijk is:** `GroupShape` fungeert als een container. Wanneer u de groep verplaatst, roteert of de grootte wijzigt, volgen alle onderliggende vormen dit automatisch. De omvattende doos (200 × 200 points) definieert de coördinatenruimte voor de onderliggende vormen.

## Stap 4: Groepsvorm invoegen in het document

Nu de groep de rechthoek en ellips bevat, moet u **insert group shape** op de gewenste locatie invoegen. De builder heeft de lege groep al geplaatst, maar u kunt deze ook elders invoegen indien nodig.

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**Waarom dit belangrijk is:** Het aanpassen van `Left` en `Top` verplaatst de hele groep binnen de pagina. Het opslaan van het document schrijft de vormhiërarchie naar een `.docx`‑bestand dat geopend kan worden in Microsoft Word, LibreOffice of een andere compatibele viewer.

## Volledig uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat alle stappen combineert. Kopieer de code naar een nieuw console‑project en voer het uit om `GroupShapeExample.docx` te genereren.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Verwacht resultaat:**  
Het openen van `GroupShapeExample.docx` toont een enkele groep met een lichtblauwe rechthoek en een lichtkoraal‑ellips, beide gepositioneerd binnen een container van 200 × 200 points. De groep kan als één object worden geselecteerd in Word, wat bevestigt dat **add shapes to group** is geslaagd.

## Veelvoorkomende variaties en randgevallen

| Situatie | Aanbevolen aanpassing |
|----------|-----------------------|
| Verschillende vormtypes (bijv. `ShapeType.Line`) | Maak de vorm met het gewenste `ShapeType` en stel de geometrie dienovereenkomstig in. |
| Vorm moet worden geroteerd | Gebruik `shape.Rotation = 45;` (graden) voordat u deze aan de groep toevoegt. |
| Grotere documenten met veel groepen | Hergebruik een enkele `DocumentBuilder`‑instantie; vermijd het maken van een nieuwe builder voor elke groep om het geheugenverbruik te verminderen. |
| Opslaan als PDF in plaats van DOCX | Roep `doc.Save("output.pdf", SaveFormat.Pdf);` aan nadat de groep is ingevoegd. |

**Pro tip:** Stel altijd expliciete `Left`‑ en `Top`‑waarden in voor de groep wanneer u een precieze plaatsing nodig heeft. Als u deze weglaten, erft de groep de huidige cursorpositie van de builder, wat kan leiden tot onverwachte lay‑outrésultaten.

## Conclusie

U weet nu hoe u **create rectangle shape**, **add multiple shapes**, **add shapes to group**, en **insert group shape** in een Word‑document kunt gebruiken met C#. Het volledige voorbeeld toont de volledige workflow van het maken van een document tot het opslaan van het uiteindelijke bestand.  

Vervolgens kunt u gerelateerde onderwerpen verkennen, zoals **positioning shapes relative to text**, **applying text wrapping**, en **exporting grouped shapes to PDF**. Deze uitbreidingen stellen u in staat om geavanceerde, programmatische documentlay‑outs te bouwen met Aspose.Words.

## Wat moet u hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om u te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in uw eigen projecten te verkennen.

- [Rechthoekvorm maken in Word met C# – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Groepsvorm maken in Word‑document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Leeg Word‑document maken met schaduwrijke rechthoekvorm – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}