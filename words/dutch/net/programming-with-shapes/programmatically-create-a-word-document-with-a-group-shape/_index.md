---
category: general
date: 2026-09-27
description: Programmeermatig een Word‑document met een groepsvorm maken met Aspose.Words
  in C#. Volg deze stap‑voor‑stap gids om het bestand te genereren en leer handige
  tips.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- how to create group shape word
- Aspose.Words group shape
- C# Word automation
- StructuredDocumentTag example
language: nl
lastmod: 2026-09-27
og_description: Programmeermatig een Word‑document met een groepsvorm maken met Aspose.Words.
  Deze tutorial leidt je door de volledige C#‑code, legt elke stap uit en toont de
  uiteindelijke output.
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: Programmeermatig een Word‑document maken met een groepsvorm – C#‑gids
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  headline: Programmatically create a Word document with a group shape
  type: TechArticle
- description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  name: Programmatically create a Word document with a group shape
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works with .NET Framework 4.7+). - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`). - A C# IDE such as
      Visual Studio 2022 or VS Code with the C# extension.'
  - name: Expected output screenshot (conceptual)
    text: '``` +-----------------------------------------------------------+ | ┌───────────────────────────────────────────────┐
      | | │ [Enter text here] │ | | └───────────────────────────────────────────────┘
      | +-----------------------------------------------------------+ ```'
  - name: Adding more child shapes
    text: 'You can enrich the group by appending additional drawing objects, such
      as pictures or text boxes:'
  - name: Controlling wrapping style
    text: 'If you need the group shape to stay behind text or to have tight wrapping,
      set the `WrapType` property:'
  - name: 'Edge case: Empty group shape'
    text: A `GroupShape` without children renders as an invisible placeholder. Always
      verify that at least one child (e.g., an SDT or a picture) is added; otherwise
      Word may drop the group during saving.
  - name: Compatibility note
    text: Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`.
      If you target older versions, the `AppendChild` method may behave differently,
      and you might need to call `UpdatePageLayout` after saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Programmatig een Word‑document maken met een groepsvorm
url: /nl/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programma's om een Word-document met een groepsvorm te maken

Als je **programmatically een Word-document wilt maken** dat een gegroepeerde tekening bevat, laat deze gids je precies zien hoe je dit doet met Aspose.Words for .NET. Of je nu een contractgenerator, een rapportgenerator of een formulier‑invultool bouwt, je leert de volledige C#-code, waarom elke API‑aanroep belangrijk is, en hoe je veelvoorkomende randgevallen afhandelt.

Het maken van een gegroepeerde vorm in Word kan lastig aanvoelen omdat het Word-objectmodel groepsvormen behandelt als containers voor andere tekenobjecten. Deze tutorial beantwoordt niet alleen **hoe je een groepsvorm in Word maakt** documenten, maar laat ook zien hoe je een platte‑tekst StructuredDocumentTag (SDT) in de groep kunt insluiten zodat de vorm bewerkbare inhoud kan bevatten.

## Wat je zult bereiken

- Initialiseer een nieuw leeg Word-document met `Document` en `DocumentBuilder`.
- Voeg een `GroupShape` in op de huidige cursorpositie.
- Voeg een platte‑tekst `StructuredDocumentTag` (SDT) toe aan de groepsvorm.
- Sla het bestand op als een `.docx` die geopend kan worden in Microsoft Word.
- Begrijp de belangrijkste eigenschappen van `GroupShape` en `StructuredDocumentTag` voor toekomstige uitbreidingen.

### Vereisten

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.7+).
- Aspose.Words for .NET NuGet‑pakket (`Install-Package Aspose.Words`).
- Een C#‑IDE zoals Visual Studio 2022 of VS Code met de C#‑extensie.

---

## Programma's om een Word-document te maken – het project opzetten

1. **Maak een nieuw console‑project**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **Open het project in je IDE** en vervang de inhoud van `Program.cs` door de code die in de volgende secties wordt getoond.

> **Pro tip:** Houd je projectmap schoon; Aspose.Words schrijft het uitvoerbestand naar de werkmap tenzij je een absoluut pad opgeeft.

## Stap 1: Initialiseer het document en de builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

// Create a new blank document.
Document doc = new Document();

// DocumentBuilder gives you a cursor to insert nodes.
DocumentBuilder builder = new DocumentBuilder(doc);

// Optional: set the page size or margins if your shape must fit a specific area.
builder.PageSetup.PageWidth = 595;   // A4 width in points
builder.PageSetup.PageHeight = 842;  // A4 height in points
```

**Waarom dit belangrijk is:**  
`Document` vertegenwoordigt het volledige Word‑bestand, terwijl `DocumentBuilder` je in staat stelt nieuwe elementen te positioneren zonder handmatig door de knooppuntboom te navigeren. Het vroeg instellen van paginadimensies zorgt ervoor dat de groepsvorm niet over de pagina heen loopt.

## Stap 2: Voeg een GroupShape in op de huidige cursorlocatie

```csharp
// Create an empty GroupShape container.
GroupShape groupShape = new GroupShape(doc)
{
    // Give the group a size that comfortably holds its children.
    Width = 300,
    Height = 150,

    // Position the group relative to the page (you can also use RelativeHorizontalPosition).
    Left = 100,
    Top = 100
};

// Insert the group shape into the document where the builder is currently positioned.
builder.InsertNode(groupShape);
```

**Uitleg:**  
Een `GroupShape` is een tekenobject dat andere vormen, afbeeldingen of tekstvakken kan bevatten. Door `Width`, `Height`, `Left` en `Top` in te stellen, bepaal je de exacte plaatsing op de pagina. De `InsertNode`‑methode plaatst de vorm in de hoofd‑documentstroom, zich gedragend als een zwevend object.

## Stap 3: Voeg een platte‑tekst StructuredDocumentTag (SDT) toe binnen de groep

```csharp
// Create a plain‑text SDT that will act as a content placeholder.
StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Provide a helpful tag title that appears as a tooltip in Word.
    Title = "GroupShapeText",
    // Set default placeholder text.
    PlaceholderName = "Enter text here"
};

// Append the SDT to the group shape's child collection.
groupShape.AppendChild(sdtTag);
```

**Waarom een SDT gebruiken?**  
StructuredDocumentTags zijn de native content‑controls van Word. Ze stellen gebruikers in staat de tekst direct in het opgeslagen document te bewerken, en ze kunnen later programmatically worden benaderd voor data‑extractie. Het plaatsen van een SDT binnen een groepsvorm stelt je in staat visuele groepering te combineren met bewerkbare inhoud.

## Stap 4: Sla het document op

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**Resultaat:**  
Het openen van `GroupShapeDemo.docx` in Microsoft Word toont een zwevend rechthoek (de groepsvorm) met een tekst‑placeholder die “Enter text here” weergeeft. Gebruikers kunnen in de vorm klikken en direct typen.

### Verwachte output screenshot (conceptueel)

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

De buitenste doos is de `GroupShape`; het binnenste grijze gebied is de `StructuredDocumentTag`.

---

## Hoe een groepsvorm in Word te maken – aanvullende overwegingen

### Meer kindvormen toevoegen

Je kunt de groep verrijken door extra tekenobjecten toe te voegen, zoals afbeeldingen of tekstvakken:

```csharp
// Example: add a picture inside the same group.
Shape picture = new Shape(doc, ShapeType.Image)
{
    ImageData = ImageData.FromFile("logo.png"),
    Width = 100,
    Height = 50,
    Left = 10,
    Top = 80
};
groupShape.AppendChild(picture);
```

### De omloopstijl regelen

Als je wilt dat de groepsvorm achter de tekst blijft of een strakke omloop heeft, stel dan de `WrapType`‑eigenschap in:

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### Randgeval: Lege groepsvorm

Een `GroupShape` zonder kinderen wordt weergegeven als een onzichtbare placeholder. Controleer altijd dat er minstens één kind (bijv. een SDT of een afbeelding) is toegevoegd; anders kan Word de groep tijdens het opslaan verwijderen.

### Compatibiliteitsopmerking

Aspose.Words 23.10+ ondersteunt `GroupShape` en `StructuredDocumentTag` volledig. Als je oudere versies target, kan de `AppendChild`‑methode zich anders gedragen, en moet je mogelijk `UpdatePageLayout` aanroepen na het opslaan.

---

## Volledig uitvoerbaar voorbeeld

Kopieer de volledige code‑snippet hieronder naar `Program.cs` en voer het project uit. De code bevat alle bovenstaande stappen in één enkel, zelf‑voorzienend programma.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.PageSetup.PageWidth = 595;
        builder.PageSetup.PageHeight = 842;

        // 2️⃣ Create and insert a GroupShape.
        GroupShape groupShape = new GroupShape(doc)
        {
            Width = 300,
            Height = 150,
            Left = 100,
            Top = 100
        };
        builder.InsertNode(groupShape);

        // 3️⃣ Add a plain‑text StructuredDocumentTag (SDT) inside the group.
        StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
        {
            Title = "GroupShapeText",
            PlaceholderName = "Enter text here"
        };
        groupShape.AppendChild(sdtTag);

        // 4️⃣ Optional: add a picture to demonstrate multiple children.
        // Uncomment and adjust the path if you want to test this.
        /*
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            ImageData = ImageData.FromFile("logo.png"),
            Width = 100,
            Height = 50,
            Left


## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Groepsvorm maken in Word-document met Aspose.Words voor .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Rechthoekvorm maken in Word met C# – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Leeg Word-document maken met Aspose.Words – Stapsgewijze gids](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}