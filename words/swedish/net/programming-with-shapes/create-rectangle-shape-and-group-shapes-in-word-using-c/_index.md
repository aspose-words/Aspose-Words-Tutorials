---
category: general
date: 2026-09-08
description: Skapa en rektangelform i ett Word‑dokument med C#. Lär dig att ställa
  in formens storlek, gruppera flera former och skapa ett tomt Word‑dokument programatiskt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: sv
lastmod: 2026-09-08
og_description: Skapa rektangelform i ett Word-dokument med C#. Denna guide visar
  hur du ställer in formens storlek, grupperar flera former och skapar ett tomt Word-dokument
  programatiskt.
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: Skapa rektangelform och gruppera former i Word med C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Skapa rektangelform och gruppera former i Word med C#
url: /sv/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangelform och gruppera former i Word med C#

Om du behöver **create rectangle shape** i en Word‑fil, ger den här handledningen en komplett, färdig‑att‑köra‑lösning. Du kommer att se hur du anger shape size, grupperar flera former och skapar ett tomt Word‑dokument från grunden—allt med Aspose.Words for .NET‑biblioteket.

Att arbeta med Word‑dokument programatiskt känns ofta som att jonglera många små detaljer. I slutet av den här guiden har du en enda metod som producerar en `.docx`‑fil som innehåller en rektangel och en ellips grupperade tillsammans, redo för vidare redigering eller utskrift.

## Förutsättningar

* .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.6+)
* En licensierad kopia av **Aspose.Words for .NET** (du kan använda en gratis utvärderingsnyckel)
* En IDE såsom Visual Studio 2022 eller Visual Studio Code
* Grundläggande kunskap om C#‑syntax

Inga ytterligare NuGet‑paket krävs utöver `Aspose.Words`.

## Steg 1: Skapa ett tomt Word‑dokument

Det första steget är att skapa ett tomt dokument som kommer att innehålla formerna. Detta uppfyller kravet *create blank word document*.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

Att skapa ett tomt dokument ger dig en ren arbetsyta. `Document`‑objektet representerar hela `.docx`‑filen, och dess `FirstSection.Body.FirstParagraph` är standardinfogningspunkten för nya noder.

## Steg 2: Skapa rektangelform

Nu kan du lägga till rektangeln. Det är här **create rectangle shape**‑operationen sker.

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

Att ange dimensionerna direkt svarar på nyckelordet **set shape size**. Alla storleksvärden uttrycks i punkter, vilket ger exakt kontroll över hur formen visas i det slutgiltiga dokumentet.

## Steg 3: Skapa en ytterligare form (ellips)

Ett typiskt användningsfall är att kombinera flera former. Här lägger vi till en ellips som senare kommer att dela samma behållare.

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

Båda formerna är fortfarande oberoende i detta skede. Nästa steg visar hur man **group multiple shapes** tillsammans.

## Steg 4: Gruppera former i Word

Att gruppera former låter dig flytta, ändra storlek eller formatera dem som en enhet. Detta uppfyller kraven **group shapes in word** och **group multiple shapes**.

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

`GroupShape.Bounds`‑egenskapen bestämmer koordinatsystemet för underordnade former. Genom att placera rektangeln och ellipsen i samma `GroupShape` kan du senare flytta eller rotera dem tillsammans med ett enda anrop.

## Steg 5: Spara dokumentet

Slutligen skriver du dokumentet till disk. Filen kommer att innehålla de grupperade formerna du just skapade.

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

Efter att ha kört programmet, öppna `GroupedShapes.docx` i Microsoft Word. Du bör se en rektangel och en ellips grupperade tillsammans; att markera en form markerar också den andra, vilket bekräftar att gruppering lyckades.

## Fullständig källkod

Kopiera följande kompletta program till ett nytt console‑app‑projekt och kör det. Ingen ytterligare kod krävs.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Förväntad output

När programmet körs produceras `GroupedShapes.docx`. Att öppna filen i Word visar:

* En **rectangle** (100 pt × 50 pt) med en blå kantlinje och ljusgrå fyllning.
* En **ellipse** (80 pt × 80 pt) med en mörkgrön kantlinje och ljusgul fyllning.
* Båda formerna är i en enda grupp, så att flytta en flyttar den andra.

## Vanliga frågor och edge cases

| Fråga | Svar |
|----------|--------|
| **Can I add more than two shapes to the group?** | Ja. Skapa ytterligare `Shape`‑objekt och anropa `group.AppendChild(yourShape)` för varje. |
| **What if I need to rotate the group?** | Ställ in `group.RotationAngle = 45;` (grader). Alla underordnade former roterar tillsammans. |
| **Is it possible to group shapes after the document is saved?** | Du måste ändra dokumentstrukturen innan du sparar; annars måste du ladda filen, lokalisera formerna och återskapa gruppen. |
| **Do I need to dispose of any objects?** | Aspose.Words hanterar sina egna resurser, men du bör disponera `FileStream`‑objekt om du öppnar strömmar manuellt. |
| **Will the code work with .doc (binary) format?** | Ja, ändra `doc.Save("output.doc")`. Gruppbeteendet är identiskt. |

## Slutsats

Du vet nu hur du **create rectangle shape**, **set shape size**, och **group multiple shapes** i en Word‑fil med C#. Detta tillvägagångssätt låter dig programatiskt bygga komplexa diagram, vattenstämplar eller mallbaserade rapporter utan manuell redigering.

### Nästa steg

* Utforska **group shapes in word** vidare genom att lägga till textrutor eller bilder i samma grupp.
* Använd `SetShapeSize`‑mönstret för att dynamiskt beräkna dimensioner baserat på sidlayout.
* Kombinera denna teknik med mail‑merge‑fält för att generera personliga dokument i stor skala.

Känn dig fri att experimentera med olika formtyper, färger och grupptransformationer. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa gruppform i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Skapa tomt Word‑dokument med skuggad rektangel‑form – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Skapa Word‑dokument med en skuggad rektangel – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}