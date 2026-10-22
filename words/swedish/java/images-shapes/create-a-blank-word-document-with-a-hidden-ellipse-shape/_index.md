---
category: general
date: 2026-09-18
description: Skapa ett tomt Word‑dokument och dölj en ellipsform med Aspose.Words.
  Lär dig hur du döljer en form i Word, hur du infogar en ellips och hur du snabbt
  skapar en dold form.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- how to insert ellipse
- hide shape in word
- create hidden shape
language: sv
lastmod: 2026-09-18
og_description: Skapa ett tomt Word‑dokument och göm en ellipsform i Word. Den här
  guiden visar dig steg för steg hur du infogar en ellips, gömmer formen i Word och
  skapar en dold form med Aspose.Words.
og_image_alt: Screenshot of a blank Word document containing a hidden ellipse shape
  created with Aspose.Words
og_title: Skapa ett tomt Word-dokument med en dold ellipsform
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  headline: Create a blank Word document with a hidden ellipse shape
  type: TechArticle
- description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  name: Create a blank Word document with a hidden ellipse shape
  steps:
  - name: Pro tip
    text: If you later need to make the shape visible again, simply set `ellipse.Hidden
      = false;` and save the document.
  - name: What if the shape still appears?
    text: '* Ensure you are using Aspose.Words 23.9 or later – older versions had
      a bug where `Hidden` was ignored for some shape types. * Verify that you are
      not applying any additional formatting (e.g., `WrapType`) that forces the shape
      to occupy layout space.'
  - name: Can I hide other shape types?
    text: Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`,
      etc. Just replace `ShapeType.Ellipse` with the desired type.
  - name: How to list hidden shapes later?
    text: '```csharp foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
      { if (shape.Hidden) Console.WriteLine($"Hidden shape: {shape.ShapeType}"); }
      ```'
  - name: Next steps
    text: '* Explore **how to hide shape** conditionally based on document content.
      * Learn **how to unhide shape** when generating a final version of the document.
      * Combine hidden shapes with **custom document properties** to embed machine‑readable
      data.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Skapa ett tomt Word‑dokument med en dold ellipsform
url: /sv/java/images-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa ett tomt Word-dokument med en dold ellipsform

Om du behöver **skapa ett tomt Word-dokument** som innehåller en form som du inte vill ska visas i layouten, visar den här guiden exakt hur du gör. Genom att använda Aspose.Words för .NET kan du programatiskt infoga en ellips och sedan dölja formen så att dokumentet förblir visuellt tomt samtidigt som det behåller formdata.

I den här handledningen kommer du att lära dig:

* hur du **skapar ett tomt Word-dokument** objekt,
* hur du **infogar ellips** med `DocumentBuilder`,
* hur du **döljer en form i Word** så att den inte påverkar sidan,
* hur du **skapar dolda former** för senare bearbetning.

Stegen fungerar med .NET 6+ och den senaste Aspose.Words‑versionen (23.9 vid skrivtillfället). Ingen extra Office‑installation krävs.

## Förutsättningar

* Visual Studio 2022 (eller någon C#‑IDE)
* .NET 6 SDK eller senare
* Aspose.Words for .NET NuGet‑paket  
  ```bash
  dotnet add package Aspose.Words
  ```
* Grundläggande kunskap om C# och Word‑dokumentkoncept

## Steg 1: Skapa ett tomt Word-dokument

Det första du måste göra är att instansiera ett `Document`‑objekt. Detta objekt representerar en tom `.docx`‑fil och är grunden för alla vidare operationer.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document doc = new Document();   // <-- creates a blank Word document in memory
```

Att **skapa ett tomt Word-dokument** ger dig en ren canvas – inga stycken, inga sektioner, bara den underliggande paketstrukturen. Detta är den ideala startpunkten när du bara behöver en dold form och inget annat.

## Steg 2: Initiera en DocumentBuilder

`DocumentBuilder` tillhandahåller ett bekvämt API för att lägga till innehåll i ett `Document`. Det fungerar som en markör som du flyttar genom dokumentet.

```csharp
// Step 2: Initialise a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Buildern skapar automatiskt en standardförsta sektion och ett stycke, så att du kan börja infoga former utan att manuellt lägga till sektioner.

## Steg 3: Infoga en ellipsform

Nu **infogar vi ellips** med hjälp av `InsertShape`‑metoden. Metoden tar en `ShapeType`‑enumeration, bredden och höjden (i punkter).

```csharp
// Step 3: Insert an ellipse shape with a width of 100 points and a height of 50 points
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
```

Varför en ellips? En ellips är en vektorform som kan döljas utan att påverka omgivande textflöde. Bredden 100 pt och höjden 50 pt är godtyckliga; du kan justera dem efter dina senare bearbetningsbehov.

## Steg 4: Dölj formen så att den inte visas i layouten

För att **dölja en form i Word**, sätt `Hidden`‑egenskapen på `Shape`‑objektet till `true`. När dokumentet öppnas i Microsoft Word blir formen osynlig och tar inte upp utrymme i layouten.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
ellipse.Hidden = true;   // <-- this hides the shape in Word
```

`Hidden`‑flaggan lagras i formens XML (`<w:hidden/>`). Word respekterar detta attribut vid rendering, vilket är anledningen till att dokumentet ser helt tomt ut även om formen finns.

### Proffstips

Om du senare behöver göra formen synlig igen, sätt helt enkelt `ellipse.Hidden = false;` och spara dokumentet.

## Steg 5: Spara dokumentet med den dolda formen

Till sist, skriv dokumentet till disk. Filen blir ett vanligt `.docx`‑dokument som vilken Word‑processor som helst kan öppna.

```csharp
// Step 5: Save the document with the hidden shape
doc.Save(@"C:\Temp\HiddenEllipse.docx");
```

Den sparade filen, `HiddenEllipse.docx`, är ett **skapat tomt Word-dokument** som innehåller en dold ellips. När den öppnas i Microsoft Word visas en tom sida, men formen finns fortfarande kvar i Open XML‑strukturen.

## Fullständigt fungerande exempel

Nedan finns det kompletta, självständiga programmet som du kan kopiera, klistra in och köra.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();

            // 2️⃣ Initialise DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse shape (width: 100pt, height: 50pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the shape so it does not affect layout
            ellipse.Hidden = true;

            // 5️⃣ Save the result
            string outputPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Förväntat resultat**

* En fil med namnet `HiddenEllipse.docx` visas i `C:\Temp`.
* När filen öppnas i Microsoft Word visas en helt tom sida.
* Om du granskar dokumentet med Open XML SDK eller en zip‑visare hittar du `<w:shape>`‑elementet med `<w:hidden/>` i dokumentdelen.

## Vanliga frågor och edge‑cases

### Vad händer om formen fortfarande visas?

* Säkerställ att du använder Aspose.Words 23.9 eller senare – äldre versioner hade en bugg där `Hidden` ignorerades för vissa formtyper.
* Verifiera att du inte tillämpar någon extra formatering (t.ex. `WrapType`) som tvingar formen att ta upp layoututrymme.

### Kan jag dölja andra formtyper?

Ja. Samma `Hidden`‑egenskap fungerar för `ShapeType.Rectangle`, `ShapeType.Picture` osv. Byt bara ut `ShapeType.Ellipse` mot den önskade typen.

### Hur listar man dolda former senare?

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.Hidden)
        Console.WriteLine($"Hidden shape: {shape.ShapeType}");
}
```

Detta kodsnutt itererar över alla former och skriver ut de som är dolda, vilket är användbart för **skapa dolda former**‑arbetsflöden där du senare behöver bearbeta eller avdölja dem.

## Slutsats

Du vet nu hur du **skapar ett tomt Word-dokument**, **infogar ellips** och **döljer en form i Word** för att producera en **skapa dold form** som förblir osynlig för läsaren. Denna teknik är praktisk för att lagra metadata, bokmärken eller anpassad XML i ett dokument utan att ändra dess visuella utseende.

### Nästa steg

* Utforska **hur man döljer en form** villkorligt baserat på dokumentinnehåll.
* Lär dig **hur man avdöljer en form** när du genererar en slutgiltig version av dokumentet.
* Kombinera dolda former med **anpassade dokumentegenskaper** för att bädda in maskinläsbar data.

Känn dig fri att experimentera med olika formtyper, storlekar och dolda‑tillståndslogik för att passa ditt automationsscenario. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}