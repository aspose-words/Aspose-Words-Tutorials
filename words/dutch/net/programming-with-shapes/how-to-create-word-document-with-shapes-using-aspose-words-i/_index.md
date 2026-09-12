---
category: general
date: 2026-09-11
description: Leer hoe je een Word‑document maakt, een rechthoekvorm toevoegt en de
  afmetingen van de vorm instelt met Aspose.Words. Stapsgewijze C#‑gids voor precieze
  vormafmetingen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: nl
lastmod: 2026-09-11
og_description: Maak een Word-document met Aspose.Words in C#. Deze gids laat zien
  hoe je een rechthoekvorm toevoegt, de vormgrootte instelt en de afmetingen van de
  vorm via code beheert.
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: Maak een Word‑document met vormen – Aspose.Words C#‑handleiding
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Hoe maak je een Word‑document met vormen met Aspose.Words in C#
url: /nl/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een Word‑document met vormen te maken met Aspose.Words in C#

Als je een **Word-document maken** moet die aangepaste grafische elementen bevat, kun je dat volledig in code doen. Deze tutorial leidt je door het maken van een Word‑bestand, het toevoegen van een rechthoekvorm, en het beheersen van elke dimensie van de vorm. Aan het einde heb je een herbruikbare code‑fragment die je in elk .NET‑project kunt gebruiken.

Je leert hoe je **add rectangle shape**, **set shape size**, en **set shape dimensions** binnen een gegroepeerde container. Het voorbeeld gebruikt Aspose.Words 13.9, maar de concepten zijn ook van toepassing op latere versies. Er is geen eerdere ervaring met de Aspose‑teken‑API vereist—alleen basiskennis van C#.

## Vereisten

- .NET 6.0 of later geïnstalleerd  
- Aspose.Words for .NET NuGet‑pakket (`Install-Package Aspose.Words`)  
- Een IDE zoals Visual Studio 2022 (elke editor die C# ondersteunt werkt)  

Deze tools klaar hebben stelt je in staat de code direct uit te voeren zonder extra configuratie.

## Stap 1: Initialiseer het document en de builder – basis van een Word‑document maken

De eerste handeling is het aanmaken van een `Document`‑object en een `DocumentBuilder`. Het `Document` vertegenwoordigt het bestand zelf, terwijl de `DocumentBuilder` een vloeiende API biedt voor het invoegen van inhoud.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Waarom dit belangrijk is:**  
Het document van tevoren maken geeft je een schoon canvas. De cursor van de builder start bij de eerste alinea, waar we later **vormen in Word maken**.

## Stap 2: Bouw een GroupShape om meerdere grafische elementen te bevatten

Een `GroupShape` fungeert als een container; je kunt de hele groep verplaatsen, roteren of de grootte aanpassen als één eenheid. Hier definiëren we de breedte en hoogte van de container in punten (1 pt ≈ 1/72 in).

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**Waarom dit belangrijk is:**  
Het groeperen van vormen vereenvoudigt het beheer van de lay‑out. Als je later meer vormen moet toevoegen (bijv. cirkels of tekstvakken), erven ze de positie en schaal van de groep.

## Stap 3: Maak een rechthoekvorm en configureer de afmetingen

Nu voegen we de daadwerkelijke rechthoek toe. De `Shape`‑constructor vereist de documentreferentie en het vormtype. Na het aanmaken stellen we expliciet **set shape size** en **set shape dimensions** in.

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**Waarom dit belangrijk is:**  
Het specificeren van breedte, hoogte, links en boven geeft je pixel‑perfecte controle over de vorm. Dit is essentieel wanneer het document moet overeenkomen met een designspecificatie of een afgedrukt formulier.

## Stap 4: Stel de groep samen door de rechthoek toe te voegen

Het toevoegen van de rechthoek aan de `GroupShape` maakt deze een kind‑node. Je kunt zoveel kinderen toevoegen als nodig is voordat je de groep in het document invoegt.

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**Tip:** Als je van plan bent een tweede vorm toe te voegen, maak deze dan op dezelfde manier aan en roep `group.AppendChild(secondShape)` aan. Alle kinderen delen het coördinatensysteem van de groep.

## Stap 5: Voeg de gegroepeerde vorm in het document in en sla op

Met de volledig opgebouwde groep plaatsen we deze in de huidige alinea. De `CurrentParagraph`‑eigenschap van de builder geeft directe toegang tot de onderliggende node‑boom.

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Waarom dit belangrijk is:**  
Het toevoegen van de groep aan een alinea zorgt ervoor dat de vorm inline verschijnt met de tekststroom. Het opslaan van het document voltooit de **Word-document maken** bewerking.

## Veelvoorkomende variaties en randgevallen

| Scenario | Aanpassing |
|----------|------------|
| **Different page orientation** | Set `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` before creating the group. |
| **Multiple rectangles** | Create additional `Shape` objects and call `group.AppendChild(newRect)` for each. |
| **Dynamic size based on content** | Compute width/height from image dimensions or text metrics, then assign to `rectangle.Width` / `rectangle.Height`. |
| **Export to PDF** | After `doc.Save`, call `doc.Save("GroupShape.pdf", SaveFormat.Pdf);`. |
| **Compatibility with older Word versions** | Save using `SaveFormat.Doc` instead of `Docx` for Word 97‑2003 compatibility. |

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren, plakken en uitvoeren. Het bevat alle `using`‑directieven, een `Main`‑instappunt, en commentaren die elke regel uitleggen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Verwachte output:**  
Wanneer je *GroupShape.docx* opent, toont de eerste pagina een grijs‑omrande rechthoek die 50 pt van de linker‑/bovenkantmarge is gepositioneerd, waarbij de rechthoek zelf 10 pt binnen de groep is verschoven. De afmetingen komen overeen met de waarden die in de code zijn ingesteld.

## Conclusie

Je weet nu hoe je **Word-document maakt**, **add rectangle shape**, en nauwkeurig **set shape size** en **set shape dimensions** gebruikt met Aspose.Words. De gegroepeerde‑vorm aanpak houdt je lay‑out flexibel en klaar voor toekomstige uitbreidingen zoals extra grafische elementen of tekstvakken.

Verken vervolgens gerelateerde onderwerpen zoals **create shapes in word** voor cirkels, pijlen of aangepaste SVG‑paden, en leer hoe je **set shape fill color** of **apply rotation** kunt toepassen. Experimenteer met verschillende meeteenheden om te zien hoe Word punten versus centimeters rendert, en integreer de code in grotere document‑generatie‑pijplijnen.

Veel plezier met coderen, en voel je vrij dit patroon aan te passen aan elk geautomatiseerd rapportage‑ of formulier‑invulscenario dat je tegenkomt!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}