---
category: general
date: 2026-09-21
description: Lär dig hur du grupperar former i Word med Aspose.Words för C#. Denna
  steg‑för‑steg‑guide täcker skapande, placering och sparande av grupperade former.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: sv
lastmod: 2026-09-21
og_description: Gruppera former i Word med Aspose.Words för C#. Följ den här kortfattade
  handledningen för att skapa, placera och spara grupperade former programatiskt.
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: Gruppera former i Word med Aspose.Words – komplett C#‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Hur man grupperar former i Word med Aspose.Words för C#
url: /sv/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man grupperar former i Word med Aspose.Words för C#

Om du behöver **gruppera former i Word** programatiskt gör Aspose.Words det enkelt. Denna handledning visar hur du skapar två rektangel‑former, placerar dem sida‑vid‑sida, kombinerar dem till en `GroupShape` och sparar resultatet som en DOCX‑fil.

Du får ett komplett, körbart exempel, förklaringar till varför varje steg är viktigt samt tips för att hantera vanliga kantfall som överlappande former eller dynamisk storlek. När du är klar med den här guiden kan du integrera formgruppering i vilket Word‑automatiseringsprojekt som helst.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 (eller senare) installerat – Aspose.Words stöder .NET Standard 2.0+, .NET Core och .NET Framework.
* En giltig Aspose.Words för .NET‑licens (eller en tillfällig utvärderingsnyckel) – biblioteket fungerar utan licens men lägger till ett vattenmärke.
* Visual Studio 2022 (eller någon C#‑IDE) för att kompilera och köra exemplet.

Inga ytterligare NuGet‑paket krävs utöver `Aspose.Words`.

## Hur man grupperar former i Word med Aspose.Words

Kärnan i lösningen är ett **`GroupShape`**‑objekt som fungerar som en behållare för enskilda former. Nedan delar vi upp processen i tydliga steg.

### Steg 1: Skapa ett tomt dokument och en `DocumentBuilder`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Varför detta steg?*  
`Document` representerar hela DOCX‑filen, medan `DocumentBuilder` tillhandahåller flytande metoder (t.ex. `InsertShape`) som automatiskt placerar nya element vid den aktuella markörpositionen.

### Steg 2: Infoga den första rektangel‑formen

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

`InsertShape`‑anropet lägger till formen i dokumentet och returnerar ett `Shape`‑objekt som du kan konfigurera vidare (färg, kantlinje osv.). Storleken anges i punkter (1 pt ≈ 1/72 tum).

### Steg 3: Infoga den andra rektangeln och förskjut den

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

Genom att sätta `Left` positioneras formen relativt sidmarginalen. Förskjutningen måste vara större än den första formens bredd (100 pt) för att undvika överlappning; vi använder 120 pt för att lämna ett litet mellanrum.

### Steg 4: Skapa en `GroupShape` som är tillräckligt stor för båda rektanglarna

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape` tar den ägande `Document` och behållarens dimensioner. Behållarens bredd bör överstiga den längst till höger placerade formens kant; annars skulle den andra formen kapas av.

### Steg 5: Lägg till de enskilda formerna i gruppen

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

Att lägga till (append) flyttar formerna till gruppens interna samling. Efter detta anrop är formerna inte längre oberoende objekt i dokumentträdet – de tillhör gruppen.

### Steg 6: Infoga den grupperade formen tillbaka i dokumentet

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode` placerar hela `GroupShape` där markören för närvarande befinner sig. Om du behöver gruppen i ett specifikt stycke, flytta först `DocumentBuilder` till det stycket.

### Steg 7: Spara dokumentet

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

Den resulterande filen innehåller två rektanglar som beter sig som ett enda objekt – du kan flytta, ändra storlek eller ta bort dem tillsammans i Microsoft Word.

## Fullständig källkod

När alla steg sätts ihop får du ett självständigt program:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**Förväntat resultat:** När du öppnar *GroupedShapes.docx* i Microsoft Word visas två rektanglar sida vid sida, behandlade som ett enda markerbart objekt. Att dra gruppen flyttar båda rektanglarna samtidigt.

## Vanliga variationer och kantfall

| Situation | Rekommenderad justering |
|-----------|------------------------|
| **Fler än två former** | Skapa ytterligare `Shape`‑objekt, placera dem enligt behov och lägg till varje i samma `GroupShape`. |
| **Dynamisk storlek** | Beräkna gruppens bredd/höjd baserat på maximala `Right`‑ och `Bottom`‑värden för de underordnade formerna. |
| **Olika formtyper** | `ShapeType.Ellipse`, `ShapeType.Triangle` osv. kan infogas på samma sätt; gruppbehållaren bryr sig inte om typen. |
| **Roterade former** | Sätt `shape.Rotation = 45;` innan du lägger till; rotationen bevaras i gruppen. |
| **Spara som PDF** | Anropa `doc.Save("GroupedShapes.pdf");` – gruppen behålls i PDF‑renderingen. |

**Proffstips:** Efter gruppering kan du fortfarande ändra enskilda former genom att nå `group.GetChildNodes(NodeType.Shape, true)`. Detta är användbart när du vill ändra fyllningsfärgen på en rektangel utan att bryta gruppen.

## Hur du verifierar gruppering programatiskt

Om du behöver bekräfta att formerna är korrekt grupperade (t.ex. i enhetstester), inspektera dokumentets nodhierarki:

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

Utdata bör vara:

```
Number of groups: 1
Children in first group: 2
```

Detta bekräftar att **grupperade former i Word** skapades som förväntat.

## Slutsats

Du vet nu hur du **grupperar former i Word** med Aspose.Words för C#. Processen innebär att skapa enskilda former, positionera dem, omsluta dem i en `GroupShape` och infoga gruppen tillbaka i dokumentet. Med det kompletta exemplet ovan kan du utöka tekniken till valfritt antal former, olika typer eller till och med kombinera dem med textrutor och bilder.

Utforska sedan relaterade ämnen såsom **Aspose.Words shape grouping**, **C# Word shape manipulation** och **DocumentBuilder insert shape** för mer avancerade dokumentautomatiseringsscenarier. Experimentera med dynamisk storlek, villkorlig gruppering och export till PDF för att fullt utnyttja kraften i Aspose.Words.

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}