---
category: general
date: 2026-09-11
description: Lär dig hur du skapar ett Word‑dokument, lägger till en rektangelform
  och ställer in formens dimensioner med Aspose.Words. Steg‑för‑steg C#‑guide för
  exakt formstorlek.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: sv
lastmod: 2026-09-11
og_description: Skapa Word-dokument med Aspose.Words i C#. Denna guide visar hur du
  lägger till en rektangelform, ställer in formens storlek och hanterar formens dimensioner
  programatiskt.
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: Skapa Word-dokument med former – Aspose.Words C#-handledning
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
title: Hur man skapar ett Word-dokument med former med Aspose.Words i C#
url: /sv/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar Word-dokument med former med Aspose.Words i C#

Om du behöver **skapa Word-dokument** som innehåller anpassad grafik kan du göra det helt i kod. Denna handledning guidar dig genom att skapa en Word‑fil, lägga till en rektangelform och kontrollera varje dimension av formen. I slutet har du ett återanvändbart kodsnutt som du kan klistra in i vilket .NET‑projekt som helst.

Du kommer att lära dig hur du **lägger till rektangelform**, **ställer in formens storlek** och **ställer in formens dimensioner** i en grupperad behållare. Exemplet använder Aspose.Words 13.9, men koncepten gäller även för senare versioner. Ingen förkunskap om Aspose‑rit‑API:n krävs—bara grundläggande C#‑kunskaper.

## Förutsättningar

- .NET 6.0 eller senare installerat  
- Aspose.Words for .NET NuGet‑paket (`Install-Package Aspose.Words`)  
- En IDE såsom Visual Studio 2022 (vilken editor som helst som stödjer C# fungerar)  

Att ha dessa verktyg redo låter dig köra koden omedelbart utan ytterligare konfiguration.

## Steg 1: Initiera dokumentet och builder – skapa grundläggande Word-dokument

Den första operationen är att instansiera ett `Document`‑objekt och en `DocumentBuilder`. `Document` representerar själva filen, medan `DocumentBuilder` tillhandahåller ett flytande API för att infoga innehåll.

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

**Varför detta är viktigt:**  
Att skapa dokumentet i förväg ger dig en ren canvas. Builderns markör startar i det första stycket, vilket är där vi senare **skapar former i Word**.

## Steg 2: Bygg en GroupShape för att hålla flera grafikobjekt

En `GroupShape` fungerar som en behållare; du kan flytta, rotera eller ändra storlek på hela gruppen som en enhet. Här definierar vi behållarens bredd och höjd i punkter (1 pt ≈ 1/72 in).

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**Varför detta är viktigt:**  
Att gruppera former förenklar layout‑hantering. Om du senare behöver lägga till fler former (t.ex. cirklar eller textrutor) kommer de att ärva gruppens position och skalning.

## Steg 3: Skapa en rektangelform och konfigurera dess dimensioner

Nu lägger vi till själva rektangeln. `Shape`‑konstruktorn kräver en referens till dokumentet och formtypen. Efter skapandet sätter vi explicit **formens storlek** och **formens dimensioner**.

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

**Varför detta är viktigt:**  
Att ange bredd, höjd, vänster och topp ger dig pixel‑perfekt kontroll över formen. Detta är avgörande när dokumentet måste följa en design‑specifikation eller ett tryckt formulär.

## Steg 4: Sätt ihop gruppen genom att lägga till rektangeln

Att lägga till rektangeln i `GroupShape` gör den till ett barn‑nod. Du kan lägga till så många barn som behövs innan du infogar gruppen i dokumentet.

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**Tips:** Om du planerar att lägga till en andra form, skapa den på samma sätt och anropa `group.AppendChild(secondShape)`. Alla barn delar gruppens koordinatsystem.

## Steg 5: Infoga den grupperade formen i dokumentet och spara

När gruppen är färdigbyggd placerar vi den i det aktuella stycket. `CurrentParagraph`‑egenskapen på buildern ger direkt åtkomst till det underliggande nodträdet.

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

**Varför detta är viktigt:**  
Att lägga till gruppen i ett stycke säkerställer att formen visas inline med textflödet. Att spara dokumentet slutför **skapa Word-dokument**‑operationen.

## Vanliga variationer och specialfall

| Scenario | Justering |
|----------|-----------|
| **Olika sidorientering** | Sätt `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` innan du skapar gruppen. |
| **Flera rektanglar** | Skapa ytterligare `Shape`‑objekt och anropa `group.AppendChild(newRect)` för varje. |
| **Dynamisk storlek baserat på innehåll** | Beräkna bredd/höjd från bilddimensioner eller textmått, och tilldela dem till `rectangle.Width` / `rectangle.Height`. |
| **Exportera till PDF** | Efter `doc.Save`, anropa `doc.Save("GroupShape.pdf", SaveFormat.Pdf);`. |
| **Kompatibilitet med äldre Word-versioner** | Spara med `SaveFormat.Doc` istället för `Docx` för Word 97‑2003‑kompatibilitet. |

Dessa variationer visar hur samma kärnlogik kan anpassas till många verkliga krav.

## Fullt, körbart exempel

Nedan är hela programmet som du kan kopiera, klistra in och köra. Det inkluderar alla `using`‑direktiv, en `Main`‑ingångspunkt och kommentarer som förklarar varje rad.

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

**Förväntat resultat:**  
När du öppnar *GroupShape.docx* visar första sidan en gråramad rektangel placerad 50 pt från vänster‑/toppmarginalen, med själva rektangeln förskjuten 10 pt inuti gruppen. Dimensionerna matchar de värden som satts i koden.

## Slutsats

Du vet nu hur du **skapar Word-dokument**, **lägger till rektangelform**, och exakt **ställer in formens storlek** samt **ställer in formens dimensioner** med Aspose.Words. Den grupperade‑form‑metoden håller din layout flexibel och redo för framtida utökningar såsom ytterligare grafik eller textrutor.

Nästa steg är att utforska relaterade ämnen som **skapa former i Word** för cirklar, pilar eller anpassade SVG‑vägar, och lära dig hur du **ställer in fyllningsfärg för formen** eller **tillämpa rotation**. Experimentera med olika måttenheter för att se hur Word renderar punkter jämfört med centimeter, och integrera koden i större dokument‑genereringspipeline.

Lycka till med kodningen, och känn dig fri att anpassa detta mönster till alla automatiserade rapporterings‑ eller formulärifyllningsscenarier du stöter på!

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Skapa rektangelform i Word med C# – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Skapa tomt Word-dokument med skuggad rektangelform – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Formskugga‑handledning – Lägg till en skugga på Word‑form i C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}