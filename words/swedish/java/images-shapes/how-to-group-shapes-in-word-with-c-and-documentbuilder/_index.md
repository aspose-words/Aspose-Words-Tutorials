---
category: general
date: 2026-10-04
description: Lär dig hur du grupperar former i Word med C#. Den här guiden visar hur
  du infogar en rektangel, grupperar flera former och skapar en tom Word‑fil programatiskt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: sv
lastmod: 2026-10-04
og_description: Gruppera former i Word med C#. Följ den här steg‑för‑steg‑guiden för
  att infoga en rektangel, gruppera flera former och skapa en tom Word‑fil med DocumentBuilder.
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: Gruppera former i Word med C# – komplett DocumentBuilder-handledning
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: Hur man grupperar former i Word med C# och DocumentBuilder
url: /sv/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to group shapes in Word with C# and DocumentBuilder

Om du behöver **gruppera former i Word** från en C#-applikation visar den här handledningen exakt hur du gör det. Du kommer att se hur du *infogar en rektangel‑form*, kombinerar flera ritningar till en enda grupp och slutligen **skapar en tom Word‑fil** som innehåller de grupperade objekten.

Att arbeta med former är ett vanligt krav när man genererar rapporter, fakturor eller anpassade mallar programatiskt. I slutet av den här guiden har du ett återanvändbart kodexempel som du kan lägga in i vilket .NET‑projekt som helst som refererar till Aspose.Words.

## What you’ll learn

- Skapa ett tomt Word‑dokument från grunden.  
- Infoga en rektangel‑form och en ellips med `DocumentBuilder`.  
- **Gruppera flera former** i en `GroupShape`.  
- Använd **append child to group** för att bygga hierarkin.  
- Spara filen till disk och verifiera resultatet.

Ingen förkunskap om Aspose.Words krävs, men du bör ha en grundläggande förståelse för C# och .NET‑utveckling.

## Prerequisites

| Krav | Orsak |
|------|-------|
| .NET 6.0 eller senare | Tillhandahåller runtime för C#‑koden. |
| Aspose.Words for .NET (senaste versionen) | Tillhandahåller `Document`, `DocumentBuilder` och formklasser. |
| En IDE såsom Visual Studio 2022 (eller VS Code) | Gör det enkelt att kompilera och köra exemplet. |
| Skrivbehörighet till en mapp på din maskin | Krävs för anropet `doc.save`. |

Installera Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Group shapes in Word – step‑by‑step guide

Nedan är det fullständiga, körbara programmet. Varje avsnitt förklaras i detalj så att du förstår **varför** koden är skriven på detta sätt, inte bara **vad** den gör.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Why each step matters

1. **Skapa en tom Word‑fil** – Att börja med ett rent dokument garanterar att ingen dold formatering stör formens placering.  
2. **Initiera DocumentBuilder** – `DocumentBuilder` abstraherar låg‑nivå nodmanipulation, så att du kan fokusera på layout.  
3. **Infoga individuella former** – Du behöver först separata objekt (`insert rectangle shape` och en ellips) innan du kan gruppera dem. Justering av `Left` och `Top` säkerställer att de visas sida‑vid‑sida.  
4. **Gruppera flera former** – Genom att skapa en `GroupShape` och använda **append child to group** förvandlar du två oberoende ritningar till en enda logisk enhet. Att flytta eller ändra storlek på gruppen påverkar båda barnen samtidigt.  
5. **Spara dokumentet** – Den slutliga filen, `GroupedShapes.docx`, kan öppnas i Microsoft Word för att verifiera att rektangeln och ellipsen faktiskt är grupperade (välj en, så flyttas båda tillsammans).

### Expected output

Öppna `GroupedShapes.docx` i Microsoft Word:

- Du kommer att se en rektangel och en ellips placerade bredvid varandra.  
- När du markerar någon av formerna markeras båda, vilket bekräftar att de tillhör samma grupp.  
- Gruppen kan dras, skalas eller formateras som ett enda objekt.

![Diagram av grupperad rektangel och ellips i ett Word-dokument](https://example.com/grouped-shapes.png){: .center-image alt="Diagram av grupperad rektangel och ellips i ett Word-dokument"}

*Skärmbilden illustrerar de slutliga grupperade formerna.*

---

## Insert rectangle shape – customizing size and style

Om du behöver en rektangel med en specifik fyllningsfärg eller kant, ändra `Shape`‑objektet efter infogning:

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

Dessa egenskaper är en del av `Shape`‑klassen och fungerar för alla formtyper, inte bara rektanglar. Att justera stilen innan du **append child to group** säkerställer att gruppen ärver de visuella egenskaper du har angett.

---

## Group multiple shapes – handling more than two objects

Exemplet grupperar en rektangel och en ellips, men du kan lägga till valfritt antal former:

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**Proffstips:** När du har byggt en komplex grupp kan du låsa dess layout för att förhindra oavsiktliga ändringar:

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – ordering matters

Den ordning du anropar `AppendChild` definierar Z‑ordningen (vilken form som visas överst). I exemplet läggs rektangeln först till, sedan ellipsen, så ellipsen lägger sig ovanpå rektangeln om de skär varandra. Att ändra ordning är så enkelt som att anropa `RemoveChild` och lägga till igen:

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## Create blank Word file – reusable helper method

Om din applikation ofta behöver ett nytt dokument, kapsla in skaplogiken:

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

Du kan sedan ersätta raden `new Document()` i huvudprogrammet med `CreateBlankWordFile()`. Detta demonstrerar konceptet **create blank word file** på ett återanvändbart sätt.

---

## Common pitfalls and how to avoid them

| Problem | Varför det händer | Lösning |
|---------|-------------------|---------|
| Former visas utanför sidan | Standardvärdena för `Left`/`Top` är 0, vilket placerar formen vid marginalen. | Ange explicit `Left` och `Top` efter infogning. |
| Gruppen förlorar formatering | Att ändra ett barnobjekt efter att det lagts till i en grupp kan bryta gruppens layout. | Tillämpa alla visuella egenskaper **innan** du anropar `AppendChild`. |
| Sparad fil är tom | `DocumentBuilder` användes aldrig för att lägga till en nod, eller `doc.Save` anropades på ett annat `Document`‑objekt. | Kontrollera att du sparar samma `Document` som du byggde. |
| Kompatibilitetsvarningar i Word | Användning av nyare formfunktioner som inte stöds |  |

## What Should You Learn Next?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa gruppform i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Infoga former i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Skapa rektangel‑form i Word med C# – steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}