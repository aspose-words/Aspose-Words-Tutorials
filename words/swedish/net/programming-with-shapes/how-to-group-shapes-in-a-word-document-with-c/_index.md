---
category: general
date: 2026-08-14
description: Hur man grupperar former i ett Word‑dokument med C#. Lär dig att skapa
  Word‑dokument, infoga rektangelform, gruppera former i Word och spara dokumentet
  som docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
language: sv
lastmod: 2026-08-14
og_description: Hur man grupperar former i ett Word-dokument med C#. Följ den här
  kompletta handledningen för att skapa en Word-fil, infoga en rektangel, gruppera
  former i Word och spara resultatet som en docx.
og_image_alt: Screenshot showing how to group shapes in a Word document using C#
og_title: Hur man grupperar former i ett Word‑dokument med C# – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  headline: How to group shapes in a Word document with C#
  type: TechArticle
- description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  name: How to group shapes in a Word document with C#
  steps:
  - name: Create a new blank document
    text: The first thing you do when you want to **create Word document** programmatically
      is instantiate a `Document` object. This object represents the entire .docx
      file in memory.
  - name: Insert a rectangle shape
    text: To demonstrate **insert rectangle shape**, we use the `InsertShape` method.
      The rectangle will act as the first member of the group.
  - name: Insert an ellipse shape
    text: Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will
      be the second member of the group.
  - name: Group the rectangle and ellipse
    text: Now we answer the central question **how to group shapes** in a Word document.
      Aspose.Words provides `AppendGroupShape` to create a group container, and then
      you call `Group()` on that container.
  - name: Save the document as a DOCX file
    text: The final step is to **save document as docx**. You can choose any path
      you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should
      replace with a real folder.
  - name: Expected output
    text: When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue
      rectangle and a light‑coral ellipse locked together. Clicking either shape selects
      both, allowing you to move or resize them as a single unit.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Hur man grupperar former i ett Word‑dokument med C#
url: /sv/net/programming-with-shapes/how-to-group-shapes-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man grupperar former i ett Word‑dokument med C#

Om du behöver **gruppera former** i ett Word‑dokument, visar den här guiden de exakta stegen med C# och Aspose.Words‑biblioteket. Du får se hur du skapar ett Word‑dokument, infogar en rektangel, grupperar former i Word och slutligen **spara dokumentet som docx** – allt i ett enda körbart program.

Att skapa och manipulera former är ett vanligt krav när man genererar rapporter, kontrakt eller marknadsföringsbroschyrer programatiskt. I slutet av den här handledningen har du ett återanvändbart kodsnutt som du kan lägga in i vilket .NET‑projekt som helst.

## Förutsättningar

- .NET 6.0 eller senare installerat  
- Visual Studio 2022 (eller någon IDE som stödjer .NET)  
- En Aspose.Words för .NET‑licens (eller en gratis provversion)  
- Grundläggande kunskap om C#‑syntax  

Inga ytterligare NuGet‑paket krävs utöver `Aspose.Words`.

## Så grupperar du former i ett Word‑dokument

Kärnan i lösningen är en femstegsprocess. Varje steg förklaras i detalj, och den kompletta källkoden finns i slutet av artikeln.

### Steg 1: Skapa ett nytt tomt dokument

Det första du gör när du vill **skapa ett Word‑dokument** programatiskt är att instansiera ett `Document`‑objekt. Detta objekt representerar hela .docx‑filen i minnet.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Obtain a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Varför detta är viktigt:** `DocumentBuilder` är ett hög‑nivå‑hjälpmedel som låter dig infoga text, tabeller och former utan att manuellt hantera det underliggande nodträdet.

### Steg 2: Infoga en rektangel

För att demonstrera **infoga en rektangel**, använder vi metoden `InsertShape`. Rektangeln kommer att fungera som den första medlemmen i gruppen.

```csharp
// Insert a rectangle (100x50 points) at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Optional: set a fill color so the shape is visible
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

**Varför detta är viktigt:** Former placeras relativt till infogningspunkten. Att sätta en fyllningsfärg hjälper dig att se formen när du öppnar det resulterande dokumentet.

### Steg 3: Infoga en ellips

Därefter **infogar vi en ellips** (API‑et kallar den `Ellipse`). Detta blir den andra medlemmen i gruppen.

```csharp
// Insert an ellipse (80x40 points) right after the rectangle
Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

**Varför detta är viktigt:** Genom att infoga ellipsen omedelbart efter rektangeln hamnar båda formerna i samma stycke, vilket förenklar gruppering senare.

### Steg 4: Gruppera rektangeln och ellipsen

Nu svarar vi på den centrala frågan **hur man grupperar former** i ett Word‑dokument. Aspose.Words tillhandahåller `AppendGroupShape` för att skapa en gruppbehållare, och sedan anropar du `Group()` på den behållaren.

```csharp
// Get the first paragraph of the document (where the shapes live)
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;

// Create a group shape that contains the rectangle and ellipse
Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });

// Turn the container into a true group – the shapes will move and scale together
groupedShape.Group();
```

**Varför detta är viktigt:** När de är grupperade påverkar varje transformation (flytt, storleksändring, rotation) som appliceras på `groupedShape` automatiskt både rektangeln och ellipsen. Detta är avgörande för att behålla layout‑konsistens i genererade dokument.

### Steg 5: Spara dokumentet som en DOCX‑fil

Det sista steget är att **spara dokumentet som docx**. Du kan välja vilken sökväg du vill; exemplet använder en platshållare `"YOUR_DIRECTORY"` som du bör ersätta med en riktig mapp.

```csharp
// Define the output path (ensure the directory exists)
string outputPath = @"C:\Temp\groupedShapes.docx";

// Save the document in DOCX format
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

**Varför detta är viktigt:** Att spara som DOCX bevarar grupperingens metadata, så när du öppnar filen i Microsoft Word ser du rektangeln och ellipsen agera som ett enda objekt.

## Fullt, körbart exempel

Nedan är det kompletta programmet som kombinerar alla fem steg. Kopiera det till ett nytt konsolprojekt, återställ Aspose.Words‑NuGet‑paketet och kör det.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a rectangle shape (100x50 points)
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangleShape.FillColor = System.Drawing.Color.LightBlue;

            // Step 3: Insert an ellipse shape (80x40 points)
            Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
            ellipseShape.FillColor = System.Drawing.Color.LightCoral;

            // Step 4: Group the rectangle and ellipse
            Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
            Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });
            groupedShape.Group();

            // Step 5: Save the document as DOCX
            string outputPath = @"C:\Temp\groupedShapes.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

### Förväntat resultat

När du öppnar `groupedShapes.docx` i Microsoft Word ser du en ljusblå rektangel och en ljuskorallfärgad ellips låsta ihop. När du klickar på någon av formerna markeras båda, vilket låter dig flytta eller ändra storlek på dem som en enhet.

## Vanliga frågor och kantfall

| Fråga | Svar |
|----------|--------|
| **Kan jag gruppera fler än två former?** | Ja. Skicka valfritt antal `Shape`‑objekt till `AppendGroupShape`. Metoden accepterar en array, så du kan bygga en samling dynamiskt. |
| **Vad händer om jag vill att gruppen ska förankras i en tabellcell?** | Infoga formerna i cellens stycke, och anropa sedan `AppendGroupShape` på det stycket. Gruppen ärver cellens förankring. |
| **Påverkar gruppering den underliggande XML‑en?** | Aspose.Words skriver ett `<w:grpSp>`‑element som innehåller de underordnade formerna. Word känner igen detta som en grupp och bevarar relativ positionering. |
| **Hur avgrupperar jag senare?** | Anropa `groupedShape.Ungroup()`; metoden returnerar de enskilda formerna så att du kan manipulera dem separat. |
| **Finns det någon prestandapåverkan när man grupperar många former?** | Gruppering i sig är billig, men rendering av mycket stora grupper (hundratals former) kan öka filstorleken. Överväg att platta till bilder om storleken blir ett problem. |

## Proffstips

- **Ange explicita positioner** (`Left`, `Top`) om du behöver exakt justering innan gruppering.  
- **Använd `Shape.WrapType = WrapType.Inline`** när du vill att gruppen ska fungera som ett stycke‑element snarare än ett flytande objekt.  
- **Applicera en linjestil** på gruppen (`groupedShape.LineFormat`) för att ge hela samlingen en ram.  
- **Återanvänd gruppen**: efter att ha anropat `Group()` kan du klona `groupedShape` och infoga klonen någon annanstans i dokumentet.

## Nästa steg

Nu när du vet **hur man grupperar former** i ett Word‑dokument kan du utforska relaterade ämnen som:

- **Infoga en rektangel** med anpassad text eller bilder i formen.  
- **Skapa komplexa diagram** genom att nästla grupper (grupp en grupp).  
- **Exportera dokumentet som PDF** samtidigt som du bevarar formgrupperingen (`doc.Save("output.pdf", SaveFormat.Pdf)`).  

Var och en av dessa bygger på samma grunder som behandlats här, så du är väl rustad att utöka ditt Word‑automatiseringsverktyg.

## Slutsats

Denna handledning demonstrerade **hur man grupperar former** i ett Word‑dokument med C#. Du lärde dig att **skapa ett Word‑dokument**, **infoga en rektangel**, **gruppera former i Word** och slutligen **spara dokumentet som docx**. Med det kompletta, körbara exemplet och de praktiska tipsen kan du integrera formgruppering i vilken dokument‑genereringsprocess som helst. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Skapa gruppform i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Infoga former i Word-dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Skapa rektangel i Word med C# – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}