---
category: general
date: 2026-08-07
description: Voeg een rechthoekvorm in C# toe met Aspose.Words en leer hoe je de vorm
  kunt verbergen, de vulkleur kunt instellen en efficiënt een rechthoekvorm aan een
  Word‑document kunt toevoegen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: nl
lastmod: 2026-08-07
og_description: Voeg een rechthoekvorm in een Word-document in met C#. Leer hoe je
  de vorm kunt verbergen, de vulkleur instelt en een rechthoekvorm toevoegt met Aspose.Words.
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: Rechthoekvorm invoegen in C# – volledige Aspose.Words‑tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: Rechthoekvorm invoegen in C# met Aspose.Words – stap‑voor‑stap gids
url: /nl/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoekvorm invoegen in C# met Aspose.Words – stapsgewijze handleiding

Als je een **rechthoekvorm** in een Word‑document wilt invoegen vanuit C#, laat deze gids je precies zien hoe dat moet. Je ziet hoe je de vulkleur instelt, de vorm verbergt zodat deze niet verschijnt in de uiteindelijke lay‑out, en het bestand opslaat – alles met slechts een paar regels code.

In de volgende secties behandelen we alles wat je moet weten: vereisten, de volledige code‑listing, uitleg per stap, en tips voor veelvoorkomende variaties zoals het weer zichtbaar maken van de vorm of het gebruiken van een andere kleur. Aan het einde kun je **rechthoekvorm** programmatisch toevoegen aan elk .docx‑bestand.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

* **Aspose.Words for .NET** (versie 23.10 of later). Je kunt het installeren via NuGet:

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK of later geïnstalleerd op je machine.
* Een basisbegrip van C# en Visual Studio (of een andere IDE naar keuze).

Er zijn geen extra bibliotheken nodig – de vorm‑gerelateerde API’s maken deel uit van het kern‑pakket van Aspose.Words.

## Rechthoekvorm invoegen met Aspose.Words

De kern van de oplossing is een kort, zelfstandig programma dat een leeg document maakt, een rechthoek invoegt, deze kleurt, verbergt en vervolgens het bestand opslaat. Hieronder staat de volledige broncode met inline‑commentaren die het *waarom* achter elke regel uitleggen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### Wat elke stap doet

| Stap | Reden |
|------|-------|
| **Create a new document** | Provides a clean canvas; you can also load an existing .docx by passing a file path to `new Document(path)`. |
| **Initialize DocumentBuilder** | `DocumentBuilder` is the high‑level helper that lets you insert text, tables, and shapes without dealing with low‑level node trees. |
| **Insert rectangle shape** | The `InsertShape` method returns a `Shape` object that you can further customize (size, position, borders, etc.). |
| **Set fill color** | The `FillColor` property controls the interior color; you could use any `Color` value (`Color.Red`, `Color.FromArgb(255, 0, 255, 0)`, etc.). |
| **Hide the shape** | `Hidden = true` tells Word to ignore the shape during layout while still keeping it in the document’s XML. This is the standard way to store invisible objects. |
| **Save the document** | Persists the changes to a .docx file. The saved file will contain the hidden rectangle shape. |

## Hoe vulkleur instellen voor een vorm

De vulkleur wijzigen is zo simpel als een `System.Drawing.Color` toewijzen aan de `FillColor`‑eigenschap. Als je een aangepaste tint nodig hebt, gebruik je `Color.FromArgb`:

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*Waarom dit belangrijk is*: De vulkleur wordt opgeslagen in de XML van de vorm (`<w:fill>`‑attribuut). Wanneer de vorm verborgen is, blijft de kleur bestaan, wat nuttig kan zijn voor downstream‑verwerking (bijv. metadata extraheren op basis van kleurcodes).

## Hoe een vorm verbergen in het uiteindelijke document

De `Hidden`‑vlag is een boolean‑eigenschap op de `Shape`‑klasse. Deze op `true` zetten zorgt ervoor dat Word de vorm negeert tijdens het lay‑outproces.

```csharp
rectangleShape.Hidden = true;
```

**Veelvoorkomende valkuilen**

* **Hidden vs. Visible** – Als je later de vorm wilt laten verschijnen, stel je simpelweg `Hidden = false` in.
* **Compatibility** – Oudere versies van Word (pre‑2007) kunnen verborgen tekenobjecten anders behandelen. Aspose.Words behoudt compatibiliteit door de vlag op te slaan in het juiste OOXML‑element.

## Hoe een vorm programmatisch invoegen

Hoewel het voorbeeld een rechthoek gebruikt, werkt dezelfde `InsertShape`‑methode voor vele andere vormen (ellipse, driehoek, lijn, enz.). Het eerste argument is een `ShapeType`‑enum‑waarde:

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**Tip**: Als je de vorm op een specifieke locatie op de pagina wilt plaatsen, gebruik dan `builder.MoveTo` om het invoegpunt in te stellen vóór het aanroepen van `InsertShape`.

## Rechthoekvorm toevoegen aan een bestaand document

Vaak verbeter je een sjabloon in plaats van vanaf nul te beginnen. Vervang stap 1 door:

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

Alle volgende stappen blijven identiek, en de rechthoek wordt toegevoegd waar de cursor van de builder zich bevindt (meestal aan het einde van het document standaard).

## Edge cases en variaties behandelen

### 1. De vorm weer zichtbaar maken

Als een later deel van je workflow de verborgen rechthoek moet tonen, kun je de vlag toggelen:

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. Een rand (stroke) toevoegen

Een verborgen vorm kan nog steeds een zichtbare rand hebben wanneer je besluit deze te tonen. Stel de `LineColor`‑ en `LineWidth`‑eigenschappen in:

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. De rechthoek absoluut positioneren

Voor precieze lay‑outcontrole, schakel de `WrapType` van de vorm naar `WrapType.Inline` (standaard) of `WrapType.TopBottom` en pas de `Left`/`Top`‑eigenschappen aan:

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. Een andere meeteenheid gebruiken

Aspose.Words werkt in points (1 pt = 1/72 inch). Als je liever centimeters gebruikt, converteer dan eerst:

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## Volledig uitvoerbaar voorbeeld

Hieronder staat het *volledige* programma dat je kunt kopiëren, plakken en uitvoeren. Het bevat alle benodigde `using`‑directives en gebruikt absolute paden die je moet aanpassen aan jouw omgeving.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Verwacht resultaat**: Het bestand `HiddenRectangleShape.docx` opent in Microsoft Word zonder zichtbare vorm, maar de verborgen rechthoek staat wel in de document‑XML. Je kunt de aanwezigheid verifiëren door het .docx‑bestand als zip‑archief te openen en `word/document.xml` te inspecteren op een `<w:shape>`‑element met `w:fill="yellow"` en `w:hidden="true"` attributen.

## Conclusie

Je weet nu hoe je een **rechthoekvorm** in een Word‑document kunt invoegen met C# en Aspose.Words, hoe je **vulkleur** instelt, en hoe je **vorm verbergt** zodat deze onzichtbaar blijft in de uiteindelijke lay‑out. Hetzelfde patroon werkt voor andere vormtypen, aangepaste kleuren en bestaande sjablonen. Experimenteer met randen, absolute positionering en verschillende meeteenheden om de vorm precies aan jouw eisen aan te passen.

### Volgende stappen

* Verken **hoe je vorm** kunt invoegen binnen tabellen of kop‑/voetteksten voor watermerken.
* Combineer **rechthoekvorm toevoegen** met content controls om dynamische placeholders te maken.
* Bekijk de **shape manipulation**‑API van Aspose.Words voor geavanceerde functies zoals rotatie, gradient‑vullingen en SVG‑import.

Voel je vrij om de code aan te passen aan je eigen project, en laat ons in de reacties weten welke vorm‑gerelateerde uitdaging je hierna hebt opgelost!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}