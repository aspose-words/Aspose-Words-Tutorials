---
category: general
date: 2026-09-08
description: Leer hoe je vormen groepeert in Word met een DocumentBuilder, een leeg
  Word‑document maakt en een rechthoekvorm invoegt in slechts een paar regels C#‑code.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: nl
lastmod: 2026-09-08
og_description: Groep vormen in Word met DocumentBuilder. Deze tutorial laat zien
  hoe je een leeg Word‑document maakt, een rechthoekvorm invoegt en vormen combineert
  tot een GroupShape.
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: Groep vormen in Word met DocumentBuilder – compleet C#‑voorbeeld
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hoe vormen te groeperen in Word met DocumentBuilder – stap‑voor‑stap gids
url: /nl/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe vormen groeperen in Word met DocumentBuilder – stapsgewijze handleiding

Als je **vormen in Word** programmatically wilt **groeperen**, toont deze tutorial een complete oplossing in C#. Je ziet hoe je een **leeg Word‑doc** maakt, **DocumentBuilder** gebruikt, en een **rechthoekvorm** invoegt voordat je deze groepeert met een ellips. Het resultaat is een enkele `GroupShape` die je als één object kunt verplaatsen, van grootte kunt wijzigen of stijlen.

Deze gids behandelt alles wat je moet weten om een Word‑document met gegroepeerde grafische elementen te genereren met behulp van de Aspose.Words for .NET‑bibliotheek. Aan het einde van het artikel heb je een uitvoerbaar project dat `GroupedShapes.docx` produceert, met een rechthoek en een ellips gecombineerd tot één vorm.

## Vereisten

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.7.2+)
- Aspose.Words for .NET NuGet‑pakket (`Aspose.Words`) – versie 23.12 of nieuwer
- Een C#‑IDE zoals Visual Studio 2022 of Visual Studio Code
- Basiskennis van C#‑syntaxis en objectgeoriënteerd programmeren

> **Pro tip:** Installeer het NuGet‑pakket via de opdrachtregel om je project netjes te houden:  
> `dotnet add package Aspose.Words --version 23.12.0`

## Stap 1: Maak een leeg Word‑document

De eerste handeling is het instantieren van een `Document`‑object, dat een leeg Word‑bestand vertegenwoordigt, en een `DocumentBuilder` waarmee je inhoud kunt toevoegen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Waarom dit belangrijk is:** `Document` levert de bestandscontainer, terwijl `DocumentBuilder` een fluïde API biedt voor het invoegen van tekst, afbeeldingen en vormen. Zonder een `DocumentBuilder` zou je de node‑boom van het document handmatig moeten manipuleren, wat foutgevoelig is.

## Stap 2: Een rechthoekvorm invoegen

Een rechthoek is een veelvoorkomend bouwblok voor diagrammen. Gebruik `InsertShape` met `ShapeType.Rectangle` en specificeer breedte en hoogte in punten (1 pt ≈ 1/72 in).

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**Waarom dit belangrijk is:** Het instellen van `Left` en `Top` positioneert de rechthoek nauwkeurig op de pagina, wat essentieel is wanneer je deze later met andere vormen groepeert. De `InsertShape`‑methode voegt de vorm automatisch toe aan de huidige alinea.

## Stap 3: Een ellipsvorm invoegen

Voeg vervolgens een ellips toe die naast de rechthoek zal staan.

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**Waarom dit belangrijk is:** Het gebruik van een ander `ShapeType` toont aan hoe dezelfde `DocumentBuilder`‑API verschillende grafische elementen kan maken. Het positioneren van de ellips zodat deze de rechthoek overlapt, maakt het groepeereffect duidelijk.

## Stap 4: De twee vormen groeperen

Een `GroupShape` functioneert als een container. Door de rechthoek en ellips als kinderen toe te voegen, gedragen ze zich als één object.

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**Waarom dit belangrijk is:** De `Bounds`‑eigenschap vertelt Word waar de groep op de pagina staat. Door de kindvormen toe te voegen, behoud je hun individuele opmaak terwijl je collectieve transformaties (verplaatsen, roteren, schalen) mogelijk maakt.

## Stap 5: Het document opslaan

Schrijf tenslotte het document naar schijf. Je kunt het pad naar elke gewenste map wijzigen.

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Wanneer je `GroupedShapes.docx` opent in Microsoft Word, zie je een rechthoek en een ellips gegroepeerd. Het selecteren van de groep markeert beide vormen, zodat je ze als één geheel kunt slepen of van grootte kunt wijzigen.

### Verwachte output

- Een Word‑bestand genaamd **GroupedShapes.docx**
- De eerste pagina bevat een **rechthoek** (100 pt × 50 pt) op positie (50, 50)
- Een **ellips** (80 pt × 80 pt) op positie (200, 70)
- Beide vormen maken deel uit van een **GroupShape** met een omvattende rechthoek van 300 pt × 200 pt

## Veelvoorkomende variaties en randgevallen

| Scenario | Aanpassing |
|----------|------------|
| **Andere paginagrootte** | Stel `document.Sections[0].PageSetup.PageWidth` en `PageHeight` in vóór het invoegen van vormen. |
| **Meer dan twee vormen** | Maak extra `Shape`‑objecten aan en roep `groupShape.AppendChild(newShape)` voor elk aan. |
| **Vulkleur toepassen** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **De groep roteren** | `groupShape.Rotation = 45;` (graden) |
| **Exporteren naar PDF** | Na het opslaan van de DOCX, roep `document.Save("GroupedShapes.pdf");` aan. |

## Volledige broncode (klaar om uit te voeren)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Kopieer de code naar een nieuw console‑project, herstel het Aspose.Words‑NuGet‑pakket, en voer uit. De console bevestigt de bestandslocatie, en het openen van het bestand toont de gegroepeerde grafische elementen.

## Conclusie

Je weet nu **hoe je vormen in Word** kunt groeperen met de Aspose.Words `DocumentBuilder`. De tutorial heeft stap voor stap laten zien hoe je een **leeg Word‑doc** maakt, een **rechthoekvorm** invoegt, een ellips toevoegt, en ze combineert tot een `GroupShape`. Met deze basis kun je rijkere diagrammen, stroomdiagrammen of aangepaste grafische elementen rechtstreeks vanuit C# bouwen.

### Wat is het volgende?

- Verken **hoe je DocumentBuilder** kunt gebruiken voor tabellen, kopteksten en voetteksten.
- Combineer **insert rectangle shape Word**‑technieken met tekstvakken voor geannoteerde diagrammen.
- Gebruik **create blank word doc** als sjabloon voor geautomatiseerde rapportgeneratie.

Voel je vrij om te experimenteren met kleuren, verlopen en extra vormen. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Maak groepsvorm in Word‑document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vormen invoegen in Word‑documenten met Aspose.Words voor .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Rechthoekvorm maken in Word met C# – Stapsgewijze handleiding](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}