---
category: general
date: 2026-11-22
description: Programmeermatig een Word‑document maken in C# en een rechthoekvorm invoegen,
  meerdere vormen invoegen en de vormen naar Word schrijven met Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: nl
lastmod: 2026-11-22
og_description: Programmeermatig een Word‑document maken in C# door een rechthoekvorm
  in te voegen, meerdere vormen toe te voegen en vormen naar Word te schrijven met
  Aspose.Words.
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: Programmatig een Word‑document met vormen maken in C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Programmeermatig een Word‑document met vormen maken in C#
url: /nl/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programmatically create Word document with shapes in C#

Als je **programmatically create Word document** moet maken dat aangepaste grafische elementen bevat, laat deze gids je zien hoe je dat doet met Aspose.Words voor .NET. Je leert een rechthoekvorm in te voegen, extra vormen toe te voegen, ze te groeperen en uiteindelijk de vormen naar Word te schrijven — alles in een paar regels C#.

Het maken van een Word‑bestand met grafische elementen vereist niet langer handmatige bewerking of macro‑scripts. Aan het einde van deze tutorial heb je een herbruikbare methode die een `.docx`‑bestand produceert met een rechthoek en een ellips gegroepeerd, klaar voor verdere verwerking of rapportage.

## What you’ll need

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.6+)
- Aspose.Words voor .NET (NuGet‑pakket `Aspose.Words`)
- Een IDE zoals Visual Studio 2022 (elke editor die C# kan compileren is voldoende)

> **Pro tip:** Installeer het pakket met de CLI‑opdracht `dotnet add package Aspose.Words` voordat je begint met coderen.

## Programmatically create Word document – overview

De algehele stroom bestaat uit drie logische fasen:

1. **Initialize** een nieuw `Document` en een `DocumentBuilder`.  
2. **Insert multiple shapes** (een rechthoek en een ellips) en plaats ze in een `GroupShape`.  
3. **Write shapes to Word** door het `Document` op te slaan als een `.docx`‑bestand.

Elke fase is hieronder in een eigen stap ondergebracht, zodat je de code direct kunt copy‑pasten in je project.

![Programmatically create Word document with grouped shapes](grouped-shapes.png){: .align-center alt="Programmatically create Word document with grouped shapes"}

## Step 1: Initialize the document and builder

De `Document`‑klasse vertegenwoordigt het volledige Word‑bestand, terwijl `DocumentBuilder` een fluent API biedt om inhoud toe te voegen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters:* Het eerst aanmaken van het `Document` geeft je een schoon canvas. De `DocumentBuilder` houdt de huidige invoegpositie bij, wat essentieel is wanneer je later vormen aan een alinea‑hiërarchie koppelt.

## Step 2: Insert a group shape container

Een `GroupShape` laat je meerdere individuele vormen behandelen als één eenheid. Dit is handig wanneer je ze samen wilt verplaatsen of de grootte wilt aanpassen.

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*Explanation:* `InsertGroupShape` voegt een lege container in en maakt deze automatisch de huidige vorm. Alle volgende vorm‑invoegingen worden aan deze container toegevoegd totdat je de groep sluit.

## Insert rectangle shape

Nu voegen we de eerste grafiek toe — een rechthoek. Dit voldoet aan de **insert rectangle shape**‑vereiste.

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

De rechthoek erft de opmaakcontext van de groep, zodat hij binnen de `GroupShape` verschijnt. Je kunt later de lijnkleur, vulling of tekst instellen indien nodig.

## Insert multiple shapes

Om de **insert multiple shapes**‑functionaliteit te demonstreren, voegen we direct na de rechthoek een ellips toe. Je kunt zoveel vormen blijven toevoegen (bijv. driehoeken, sterren) voordat je de groep sluit.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

Op dit moment bevat de groep twee afzonderlijke vormen: een rechthoek en een ellips. Omdat ze dezelfde ouder delen, kun je ze als één geheel verplaatsen.

## Step 3: Attach the group shape to the paragraph hierarchy

Word‑documenten slaan inhoud op in een alinea‑boom. Om de groep zichtbaar te maken in het uiteindelijke bestand, moeten we hem aan de huidige alinea koppelen.

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*Why this step is required:* Zonder de groep aan een alinea toe te voegen, bestaan de vormen alleen in het geheugen en worden ze weggelaten bij het opslaan van het document.

## Step 4: Save the document – write shapes to Word

Tot slot slaan we het in‑geheugen `Document` op schijf op. Hiermee wordt het **write shapes to word**‑doel bereikt.

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Wanneer je `GroupShape.docx` opent in Microsoft Word, zie je een rechthoek en een ellips gegroepeerd, precies zoals de code heeft ingevoegd.

### Expected output

- Een bestand genaamd **GroupShape.docx** in de output‑map van het project.
- In het Word‑bestand: één alinea die een gegroepeerde rechthoek (100 pt × 50 pt) en een ellips (80 pt × 40 pt) bevat. Het selecteren van een van de vormen selecteert de hele groep.

## Handling common edge cases

| Situation | Recommendation |
|-----------|----------------|
| **Different DPI or page size** | Stel expliciet `builder.PageSetup.PaperSize` in vóór het invoegen van vormen om onverwachte schaalveranderingen te voorkomen. |
| **Need to position shapes precisely** | Gebruik `builder.MoveTo` om het invoerpunt te verplaatsen, en stel vervolgens `groupShape.Left` en `groupShape.Top` in (waarden zijn in points). |

## What Should You Learn Next?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create Word Document – Insert Rectangle Shape & Shadow in C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Create word document programmatically and group shapes in C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Programmatically create a Word document with a group shape](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}