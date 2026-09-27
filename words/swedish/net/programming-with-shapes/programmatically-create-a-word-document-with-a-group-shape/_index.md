---
category: general
date: 2026-09-27
description: Skapa ett Word‑dokument med en gruppform programatiskt med Aspose.Words
  i C#. Följ den här steg‑för‑steg‑guiden för att generera filen och lära dig användbara
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
language: sv
lastmod: 2026-09-27
og_description: Skapa ett Word-dokument med en gruppform programatiskt med Aspose.Words.
  Denna handledning guidar dig genom den kompletta C#‑koden, förklarar varje steg
  och visar det slutgiltiga resultatet.
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: Skapa ett Word-dokument med en gruppform programatiskt – C#‑guide
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
title: Skapa ett Word‑dokument med en gruppform programatiskt
url: /sv/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programmera ett Word‑dokument med en gruppform

Om du behöver **programmera ett Word‑dokument** som innehåller en grupperad ritning, visar den här guiden exakt hur du gör det med Aspose.Words för .NET. Oavsett om du bygger en kontraktgenerator, en rapportgenerator eller ett formulär‑fyllningsverktyg, får du den kompletta C#‑koden, varför varje API‑anrop är viktigt och hur du hanterar vanliga edge‑cases.

Att skapa en grupperad form i Word kan kännas knepigt eftersom Word‑objektmodellen behandlar gruppformer som behållare för andra ritobjekt. Denna handledning svarar inte bara på **hur man skapar group shape word**‑dokument, utan visar också hur du bäddar in en plain‑text StructuredDocumentTag (SDT) i gruppen så att formen kan hålla redigerbart innehåll.

## Vad du kommer att uppnå

- Initiera ett nytt tomt Word‑dokument med `Document` och `DocumentBuilder`.
- Infoga en `GroupShape` på den aktuella markörpositionen.
- Lägg till en plain‑text `StructuredDocumentTag` (SDT) i gruppformen.
- Spara filen som en `.docx` som kan öppnas i Microsoft Word.
- Förstå de viktigaste egenskaperna hos `GroupShape` och `StructuredDocumentTag` för framtida utökningar.

### Förutsättningar

- .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.7+).
- Aspose.Words för .NET NuGet‑paket (`Install-Package Aspose.Words`).
- En C#‑IDE såsom Visual Studio 2022 eller VS Code med C#‑tillägget.

---

## Programmera ett Word‑dokument – sätt upp projektet

1. **Skapa ett nytt konsolprojekt**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **Öppna projektet i din IDE** och ersätt innehållet i `Program.cs` med koden som visas i nästa avsnitt.

> **Proffstips:** Håll din projektmapp ren; Aspose.Words skriver utdatafilen till arbetskatalogen om du inte anger en absolut sökväg.

## Steg 1: Initiera dokumentet och buildern

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

**Varför detta är viktigt:**  
`Document` representerar hela Word‑filen, medan `DocumentBuilder` låter dig placera nya element utan att manuellt navigera i nodträdet. Att sätta sidmått tidigt säkerställer att gruppformen inte överskrider sidan.

## Steg 2: Infoga en GroupShape på den aktuella markörpositionen

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

**Förklaring:**  
En `GroupShape` är ett ritobjekt som kan innehålla andra former, bilder eller textrutor. Genom att sätta `Width`, `Height`, `Left` och `Top` styr du dess exakta placering på sidan. Metoden `InsertNode` placerar formen i huvudflödet, som ett flytande objekt.

## Steg 3: Lägg till en plain‑text StructuredDocumentTag (SDT) i gruppen

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

**Varför använda en SDT?**  
StructuredDocumentTags är Words inbyggda innehållskontroller. De låter användare redigera texten direkt i det sparade dokumentet, och de kan nås programatiskt senare för datautvinning. Att placera en SDT i en gruppform låter dig kombinera visuell gruppering med redigerbart innehåll.

## Steg 4: Spara dokumentet

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**Resultat:**  
När du öppnar `GroupShapeDemo.docx` i Microsoft Word visas en flytande rektangel (gruppformen) som innehåller en textplatshållare med texten “Enter text here”. Användare kan klicka i formen och skriva direkt.

### Förväntad utskriftsbild (konceptuell)

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

Den yttre rutan är `GroupShape`; det inre gråa området är `StructuredDocumentTag`.

---

## Hur man skapar group shape word – ytterligare överväganden

### Lägga till fler underordnade former

Du kan berika gruppen genom att lägga till ytterligare ritobjekt, såsom bilder eller textrutor:

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

### Styrning av omslagsstil

Om du vill att gruppformen ska ligga bakom text eller ha tät omslagning, sätt egenskapen `WrapType`:

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### Edge case: Tom gruppform

En `GroupShape` utan barn renderas som en osynlig platshållare. Verifiera alltid att minst ett barn (t.ex. en SDT eller en bild) har lagts till; annars kan Word ta bort gruppen vid sparning.

### Kompatibilitetsnotering

Aspose.Words 23.10+ stödjer fullt ut `GroupShape` och `StructuredDocumentTag`. Om du riktar dig mot äldre versioner kan metoden `AppendChild` fungera annorlunda, och du kan behöva anropa `UpdatePageLayout` efter sparning.

---

## Fullständigt körbart exempel

Kopiera hela kodsnutten nedan till `Program.cs` och kör projektet. Koden innehåller alla stegen ovan i ett enda, självständigt program.

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


## Vad bör du lära dig härnäst?


Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Skapa gruppform i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Skapa rektangelform i Word med C# – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Skapa tomt Word‑dokument med Aspose.Words – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}