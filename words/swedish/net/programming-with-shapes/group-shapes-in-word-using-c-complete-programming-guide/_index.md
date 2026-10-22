---
category: general
date: 2026-10-13
description: Gruppera former i Word med C# – lär dig hur du grupperar former och lägger
  till former i en grupp med Aspose.Words på några enkla steg.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- add shapes to group
language: sv
lastmod: 2026-10-13
og_description: gruppera former i Word med C# och Aspose.Words. Följ den här guiden
  för att lära dig hur du grupperar former och lägger till former i en grupp i ett
  Word‑dokument.
og_image_alt: Screenshot of a Word document showing two shapes combined into a single
  grouped shape
og_title: Gruppera former i Word med C# – steg‑för‑steg guide
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  headline: Group shapes in Word using C# – complete programming guide
  type: TechArticle
- description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  name: Group shapes in Word using C# – complete programming guide
  steps:
  - name: Load the Word document
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Retrieve the shapes you want to group
    text: '```csharp // Get the first shape (index 0) and second shape (index 1) from
      the whole document. Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0,
      true); Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true); ```'
  - name: Create a new `GroupShape` container
    text: '```csharp GroupShape groupShape = new GroupShape(doc); ```'
  - name: Add the individual shapes to the group
    text: '```csharp groupShape.AppendChild(firstShape); groupShape.AppendChild(secondShape);
      ```'
  - name: Insert the group shape into the document body
    text: '```csharp // Insert the group as the last child of the first paragraph.
      Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph; firstParagraph.AppendChild(groupShape);
      ```'
  - name: Save the modified document
    text: '```csharp string outputPath = @"YOUR_DIRECTORY\output.docx"; doc.Save(outputPath);
      ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Gruppera former i Word med C# – komplett programmeringsguide
url: /sv/net/programming-with-shapes/group-shapes-in-word-using-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gruppera former i Word med C# – komplett programmeringsguide

Om du behöver **gruppera former i Word** programatiskt, visar den här guiden exakt hur. Vid slutet av de två första meningarna kommer du att känna till den nödvändiga koden, resonemanget bakom varje steg och hur du **lägger till former i en grupp** utan överraskningar.

Vi kommer att gå igenom allt från att läsa in en `.docx`-fil till att spara det uppdaterade dokumentet. Handledningen förutsätter att du har grundläggande kunskaper i C# och en referens till Aspose.Words for .NET-biblioteket. Ingen extern dokumentation krävs – bara kopiera, klistra in och kör.

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.7+)
- Aspose.Words for .NET NuGet‑paket (`Install-Package Aspose.Words`)
- Ett Word‑dokument (`input.docx`) som redan innehåller minst två former (t.ex. bilder, AutoShapes)

> **Proffstips:** Om du testar, skapa en enkel Word‑fil med två rektanglar via Word‑gränssnittet. Spara den som `input.docx` i en mapp du har kontroll över.

## Gruppera former i Word – steg‑för‑steg‑guide

Nedan delar vi upp processen i fem logiska steg. Varje steg innehåller exakt C#‑kod, en förklaring till *varför* raden behövs och en kort notering om vanliga fallgropar.

### Steg 1: Läs in Word‑dokumentet

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
```

**Varför:** `Document` är ingångspunkten för all Word‑manipulation. Genom att ange den fullständiga filsökvägen läses dokumentet in i minnet, vilket gör att vi kan fråga och ändra dess nodträd.

**Fallgrop:** Att använda en relativ sökväg kan misslyckas när arbetskatalogen skiljer sig. Använd en absolut sökväg eller `Path.Combine` med `AppContext.BaseDirectory`.

### Steg 2: Hämta de former du vill gruppera

```csharp
// Get the first shape (index 0) and second shape (index 1) from the whole document.
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);
```

**Varför:** `GetChild` går igenom dokumentträdet och returnerar det *n‑:de* noden av den begärda typen. Genom att sätta `isDeep` till `true` söks i hela dokumentet, inte bara i den aktuella sektionen.

**Edge‑case:** Om dokumentet innehåller färre än två former kommer `firstShape` eller `secondShape` att vara `null` och ett undantag kastas när vi försöker kasta. Skydda mot detta:

```csharp
if (firstShape == null || secondShape == null)
    throw new InvalidOperationException("The document must contain at least two shapes to group.");
```

### Steg 3: Skapa en ny `GroupShape`‑behållare

```csharp
GroupShape groupShape = new GroupShape(doc);
```

**Varför:** `GroupShape` fungerar som en föräldranod som kan hålla flera `Shape`‑objekt. Den ärver från `Shape`, så den kan infogas var som helst där en vanlig form är tillåten (t.ex. i ett stycke).

### Steg 4: Lägg till de enskilda formerna i gruppen

```csharp
groupShape.AppendChild(firstShape);
groupShape.AppendChild(secondShape);
```

**Varför:** `AppendChild` flyttar formerna från deras ursprungliga platser till den nya gruppen. Efter detta anrop finns de ursprungliga formerna inte längre som självständiga noder; de blir en del av `groupShape`.

**Tips:** Gruppering justerar automatiskt de relativa positionerna för barnformerna. Om du behöver en specifik layout, sätt `GroupShape.Bounds`‑egenskapen *innan* du lägger till barn.

```csharp
// Example: set the group to start at (100, 100) points and be 300x200 points large.
groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);
```

### Steg 5: Infoga gruppformen i dokumentkroppen

```csharp
// Insert the group as the last child of the first paragraph.
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
firstParagraph.AppendChild(groupShape);
```

**Varför:** En `GroupShape` måste placeras inuti ett stycke (eller en tabellcell) för att renderas. Genom att lägga till den i det första stycket garanterar vi synlig placering utan att störa befintlig layout.

### Steg 6: Spara det modifierade dokumentet

```csharp
string outputPath = @"YOUR_DIRECTORY\output.docx";
doc.Save(outputPath);
```

**Varför:** `Save` skriver de förändringar som finns i minnet tillbaka till en `.docx`‑fil. Du kan också spara till en ström eller till PDF genom att ändra överlagringen.

**Resultatverifiering:** Öppna `output.docx` i Microsoft Word. Du bör se de två ursprungliga formerna nu kombinerade till ett enda grupperat objekt. När du markerar gruppen visas de vanliga Word‑grupperingshandtagen.

## Så grupperar du former programatiskt – djupare insikter

- **Node ownership:** När du anropar `AppendChild` ändras formens `ParentNode`‑referens automatiskt. Detta förhindrar “föräldralösa” noder som kan korrupta dokumentet.
- **Preserving formatting:** Gruppering **förlorar inte** någon formatering (fyllningsfärg, linjestil osv.). Alla barnformer behåller sina ursprungliga egenskaper.
- **Nested groups:** `GroupShape` kan innehålla andra `GroupShape`‑objekt, vilket möjliggör flernivåhierarkier. Behandla bara den inre gruppen som vilken annan form som helst.

## Lägg till former i gruppen och hantera dem senare

Om du behöver lägga till fler former efter att den initiala gruppen skapats, kan du återanvända samma `GroupShape`‑instans:

```csharp
// Assume we have a third shape somewhere in the document.
Shape thirdShape = (Shape)doc.GetChild(NodeType.Shape, 2, true);
groupShape.AppendChild(thirdShape);
```

När du senare behöver avgruppera, iterera över `groupShape.GetChildNodes(NodeType.Shape, true)` och sätt in varje barn där du vill ha dem igen.

```csharp
foreach (Shape child in groupShape.GetChildNodes(NodeType.Shape, true))
{
    // Example: move each child back to the original paragraph.
    firstParagraph.AppendChild(child);
}
firstParagraph.RemoveChild(groupShape); // Remove the empty group container.
```

**Varför detta är viktigt:** Vissa arbetsflöden kräver tillfällig gruppering (t.ex. justering av flera objekt) följt av avgruppering för vidare individuella redigeringar.

## Komplett körbart exempel

Nedan är ett självständigt program som du kan kompilera och köra som det är. Ersätt `YOUR_DIRECTORY` med en faktisk mappväg på din maskin.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the document.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2. Retrieve the first two shapes.
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);

        if (firstShape == null || secondShape == null)
        {
            Console.WriteLine("Document must contain at least two shapes.");
            return;
        }

        // 3. Create a GroupShape container.
        GroupShape groupShape = new GroupShape(doc);

        // Optional: define the group’s bounding box.
        groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);

        // 4. Add the shapes to the group.
        groupShape.AppendChild(firstShape);
        groupShape.AppendChild(secondShape);

        // 5. Insert the group into the first paragraph.
        Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(groupShape);

        // 6. Save the result.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Grouped shapes saved to {outputPath}");
    }
}
```

**Förväntat resultat:** När du öppnar `output.docx` visas de två ursprungliga formerna som ett enda grupperat objekt. Att markera gruppen visar de välbekanta Word‑grupperingshandtagen, vilket låter dig flytta, ändra storlek eller rotera hela uppsättningen tillsammans.

## Slutsats

Du vet nu hur du **grupperar former i Word** med C# och Aspose.Words, och du har sett de exakta stegen för att **lägga till former i en grupp** och senare manipulera eller avgruppera dem. Denna teknik är idealisk för att automatisera rapportlayouter, skapa sammansatta diagram eller förbereda Word‑mallar som kräver exakt placering av flera objekt.

Nästa steg är att utforska relaterade ämnen som **hur man grupperar former** med olika ankartyper, tillämpa **avancerad formatering** på grupperade objekt, eller exportera det grupperade resultatet till PDF. Experimentera med nästlade grupper för att bygga komplex grafik programatiskt.

Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Infoga former i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Skapa gruppform i Word‑dokument med Aspose.Words för .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Lägg till skuggeffekt på Word‑former – komplett C#‑guide](/words/english/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}