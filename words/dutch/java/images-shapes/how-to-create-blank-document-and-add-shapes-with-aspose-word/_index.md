---
category: general
date: 2026-09-30
description: Maak een leeg document en voeg een rechthoekvorm, ellips en een groep
  meerdere vormen toe in C# met Aspose.Words. Leer hoe je vormen invoegt en hoe je
  een groep maakt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: nl
lastmod: 2026-09-30
og_description: Maak een leeg document in C# en leer hoe je vormen kunt invoegen en
  meerdere vormen kunt groeperen met Aspose.Words. Volg de stapsgewijze tutorial.
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: Maak een leeg document en groepeer vormen in C# – Aspose.Words-gids
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: Hoe een leeg document te maken en vormen toe te voegen met Aspose.Words in
  C#
url: /nl/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een leeg document te maken en vormen toe te voegen met Aspose.Words in C#

Als je een **leeg document moet maken** en dit wilt vullen met grafische elementen, laat deze gids je precies zien hoe. Je ziet hoe je een **rechthoekvorm kunt invoegen**, andere tekenobjecten kunt toevoegen, en vervolgens **meerdere vormen kunt groeperen** zodat ze zich als één geheel gedragen.

Werken met vormen is een veelvoorkomende eis bij het genereren van contracten, certificaten of aangepaste rapporten. In deze tutorial leer je de volledige workflow, van het initialiseren van het document tot het opslaan van het uiteindelijke bestand, met behulp van de Aspose.Words API voor .NET.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 (of later) SDK geïnstalleerd  
* Een geldige Aspose.Words voor .NET-licentie (de gratis proefversie werkt voor dit voorbeeld)  
* Een IDE zoals Visual Studio 2022 of Visual Studio Code  

Er zijn geen extra NuGet‑pakketten vereist naast `Aspose.Words`.

## Hoe een leeg document te maken en met vormen te werken

De eerste stap is het instantieren van een `Document`‑object. Dit object vertegenwoordigt het Word‑bestand in het geheugen en geeft je toegang tot de `DocumentBuilder`, die het primaire hulpmiddel is voor het invoegen van inhoud.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Waarom dit belangrijk is:** Een leeg document geeft je een schoon canvas. De `DocumentBuilder` houdt de huidige invoegpositie bij, zodat elke vorm die je toevoegt automatisch op de juiste pagina wordt geplaatst.

## Rechthoekvorm en andere vormen invoegen

Vervolgens voegen we een rechthoek en een ellips toe. Beide aanroepen gebruiken dezelfde `InsertShape`‑methode, die de aanbevolen manier is **om vormen in te voegen** in Aspose.Words.

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*De `InsertShape`‑methode positioneert de vorm automatisch op de huidige cursorlocatie.* Als je een precieze plaatsing nodig hebt, kun je `Shape.Left` en `Shape.Top` na het invoegen aanpassen.

## Meerdere vormen groeperen tot één object

Nu combineren we de rechthoek en de ellips tot één logische entiteit. Groeperen is handig wanneer je meerdere vormen tegelijk wilt verplaatsen of de grootte wilt aanpassen.

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**Hoe dit werkt:** `InsertGroupShape` maakt een container die zich gedraagt als elke andere `Shape`. Door `AppendChild` aan te roepen, verplaats je de bestaande vormen naar de container, die automatisch hun relatieve coördinaten bijwerkt.

### Praktische tip

Als je later programmatically **een groep moet maken** voor meer dan twee vormen, herhaal dan eenvoudig `AppendChild` voor elke extra `Shape`‑instantie. De groep kan een willekeurig aantal tekenobjecten bevatten, inclusief afbeeldingen, tekstvakken of zelfs andere groepen.

## Volledig voorbeeld – hoe vormen in te voegen en het document op te slaan

Hieronder staat het volledige, uitvoerbare programma dat elke tot nu toe besproken stap demonstreert. Het uitvoeren van de code genereert een `ShapesDemo.docx`‑bestand met een rechthoek, een ellips en een gegroepeerde vorm.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Verwachte output:** Het openen van `ShapesDemo.docx` in Microsoft Word toont één pagina met een blauwe rechthoek, een groene ellips en een omringende grijze rand die de groep vertegenwoordigt. Het verplaatsen van de groep verplaatst beide vormen tegelijk, wat bevestigt dat de **meerdere vormen groeperen**‑operatie geslaagd is.

## Veelgestelde vragen en afhandeling van randgevallen

| Vraag | Antwoord |
|----------|--------|
| *Wat als ik de vormen op een specifieke pagina nodig heb?* | Roep `builder.MoveToDocumentEnd();` aan voordat je de vormen invoegt, of gebruik `builder.MoveToSection(sectionIndex);` om een specifieke sectie te targeten. |
| *Kan ik tekst toevoegen binnen een gegroepeerde vorm?* | Ja. Maak een `Shape` van het type `ShapeType.TextBox`, configureer de tekst, en `AppendChild` deze vervolgens aan de `GroupShape`. |
| *Gebruiken vormafmetingen punten of pixels?* | Aspose.Words gebruikt **punten** (1 pt = 1/72 inch). Dit zorgt voor consistente afmetingen over printers en schermen. |
| *Hoe de rotatie van de groep te wijzigen?* | Stel `groupShape.RotationAngle = 45;` in (graden). Alle onderliggende vormen roteren rond de oorsprong van de groep. |

## Conclusie

Je weet nu hoe je een **leeg document kunt maken**, een **rechthoekvorm kunt invoegen**, **hoe je vormen kunt invoegen** zoals ellipsen, en **meerdere vormen kunt groeperen** tot één object met Aspose.Words voor .NET. Het volledige code‑voorbeeld toont de aanbevolen aanpak, en de bovenstaande tips helpen je de oplossing aan te passen aan complexere scenario's, zoals het toevoegen van tekstvakken of het roteren van groepen.

Klaar om meer te verkennen? Probeer een afbeeldingsvorm aan de groep toe te voegen, experimenteer met verschillende vulkleuren, of genereer een meer‑pagina rapport waarbij elke pagina zijn eigen gegroepeerde diagram bevat. Dezelfde principes gelden, zodat je dit patroon kunt opschalen naar elk document‑automatiseringsproject.

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Groepvorm maken in Word‑document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Vormen invoegen in Word‑documenten met Aspose.Words voor .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Leeg Word‑document maken met Aspose.Words – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}