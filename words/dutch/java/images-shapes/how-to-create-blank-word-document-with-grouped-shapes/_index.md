---
category: general
date: 2026-09-08
description: Leer hoe je een leeg Word‑document maakt, een rechthoekvorm invoegt en
  meerdere vormen groepeert met C#. Volg deze stapsgewijze handleiding.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: nl
lastmod: 2026-09-08
og_description: Maak een leeg Word‑document, voeg een rechthoekvorm toe en groepeer
  meerdere vormen in C#. Deze tutorial leidt je door het volledige proces.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: Maak een leeg Word‑document met gegroepeerde vormen in C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Hoe maak je een leeg Word‑document met gegroepeerde vormen
url: /nl/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een leeg Word‑document met gegroepeerde vormen te maken

Als je een **blank Word document** moet maken dat aangepaste grafische elementen bevat, laat deze gids je precies zien hoe. Je leert **rectangle shape invoegen**, **meerdere vormen groeperen**, en **vormen aan een groep toevoegen** met Aspose.Words for .NET.

Een leeg document geeft je een schoon canvas, en het groeperen van vormen stelt je in staat ze als één geheel te verplaatsen, van grootte te wijzigen of te roteren. Deze tutorial behandelt elke stap — van het initialiseren van het document tot het opslaan van het uiteindelijke bestand—zodat je de code in je eigen project kunt kopiëren en direct resultaat ziet.

## Wat je nodig hebt

* .NET 6.0 of later (de code werkt ook met .NET Framework 4.6+)
* Een geldige Aspose.Words for .NET‑licentie (de gratis evaluatie werkt voor testen)
* Een IDE zoals Visual Studio 2022 of Visual Studio Code
* Basiskennis van C#‑syntaxis

Er zijn geen extra NuGet‑pakketten vereist naast `Aspose.Words`.

## Hoe een leeg Word‑document te maken

De eerste stap is het instantieren van een `Document`‑object. Dit object vertegenwoordigt een leeg `.docx`‑bestand dat je kunt bewerken met een `DocumentBuilder`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

De `Document`‑constructor maakt een **blank Word document** in het geheugen. De `DocumentBuilder` biedt een fluent API voor het invoegen van tekst, afbeeldingen en tekenobjecten.

## Rechthoekvorm in het document invoegen

Voeg vervolgens een rechthoekvorm toe. De rechthoek wordt het eerste kind van de groep die we later zullen maken.

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

Door `InsertShape` aan te roepen met `ShapeType.Rectangle` **voeg je een rechthoekvorm in** op de huidige cursorpositie. De breedte en hoogte worden uitgedrukt in punten (1 pt ≈ 1/72 in).

## Meerdere vormen samen groeperen

Een `GroupShape` werkt als een container. Alle kindvormen binnen de groep bewegen en transformeren samen. Maak eerst de groep aan, en voeg daarna de zojuist gebouwde rechthoek toe.

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

De `InsertGroupShape`‑methode plaatst een lege groep op de cursor van de builder. Door de rechthoek toe te voegen, **groeperen we meerdere vormen** — de rechthoek wordt onderdeel van de interne knooppuntcollectie van de groep.

## Vormen aan de groep toevoegen en het bestand opslaan

Voeg nu een tweede vorm — een ellips — toe om te laten zien hoe meerdere objecten dezelfde container delen. Sla daarna het document op.

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

De `InsertShape`‑aanroep **voegt vormen toe aan de groep** wanneer je de geretourneerde `Shape` aan de `GroupShape` toevoegt. Het opslaan van de `Document` schrijft een `.docx`‑bestand dat je kunt openen in Microsoft Word, LibreOffice of een andere compatibele viewer.

### Verwacht resultaat

Wanneer je *GroupShapeDemo.docx* opent, zie je een lege pagina met een gegroepeerd object dat een lichtblauwe rechthoek en een roze ellips bevat. Het selecteren van de groep laat je beide vormen samen verplaatsen, wat bevestigt dat **meerdere vormen groeperen** correct heeft gewerkt.

## Waarom een GroupShape gebruiken?

* **Atomic transformations** – Schalen, roteren of verplaatsen van de groep beïnvloedt alle kinderen uniform.
* **Logical organization** – Houdt gerelateerde grafische elementen bij elkaar, waardoor de documentstructuur makkelijker te onderhouden is.
* **Performance** – Het renderen van één container is vaak sneller dan het behandelen van vele onafhankelijke vormen.

Als je later een enkel kind wilt aanpassen, kun je het ophalen uit `group.ChildNodes` op index of via de `Name`‑eigenschap.

## Veelvoorkomende variaties en randgevallen

| Scenario                                 | Hoe de code aan te passen                                                            |
|------------------------------------------|--------------------------------------------------------------------------------------|
| **Different shape types**                | Vervang `ShapeType.Rectangle` of `ShapeType.Ellipse` door een andere `ShapeType`      |
| **Adding text inside a shape**           | Gebruik `Shape.TextPath.Text = "Hello"` na het invoegen van de vorm                  |
| **Setting a rotation angle**             | `group.Rotation = 45;` (graden)                                                      |
| **Saving as PDF instead of DOCX**        | `doc.Save("GroupShapeDemo.pdf");`                                                    |
| **Applying a border to the group**       | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`                   |

## Pro‑tips

* **Name your shapes** – `rectangle.Name = "MyRect";` maakt het later makkelijker om ze te vinden.
* **Use relative positioning** – Stel `group.RelativeHorizontalPosition` in op `RelativeHorizontalPosition.Page` als je wilt dat de groep verankerd blijft aan de paginamarges.
* **Dispose resources** – Plaats de `Document` in een `using`‑blok bij grotere toepassingen om onbeheerste geheugen snel vrij te geven.

## Volledige broncode voor snelle copy‑paste

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Kopieer de code naar een nieuw console‑project, herstel het `Aspose.Words` NuGet‑pakket en voer uit. Het uitvoerbestand verschijnt in de `bin/Debug/net6.0`‑map van het project (of een equivalente map).

## Volgende stappen

Nu je **een leeg Word‑document kunt maken**, **een rechthoekvorm kunt invoegen** en **meerdere vormen kunt groeperen**, kun je het volgende verkennen:

* Het toevoegen van **tekstvakken** binnen een groep om gelabelde diagrammen te maken.
* Het exporteren van de gegroepeerde grafiek naar een afbeelding met `doc.Save("image.png", SaveFormat.Png)`.
* Het combineren van groepen met tabellen voor rijk opgemaakte rapporten.

Experimenteer met verschillende vormeigenschappen, groepshiërarchieën en exportformaten om de tekenmogelijkheden van Aspose.Words volledig te benutten.

--- 

*Remember*: grouping shapes is a powerful way to keep your Word documents tidy and your code maintainable. Happy coding!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}