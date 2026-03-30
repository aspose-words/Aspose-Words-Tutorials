---
category: general
date: 2026-03-30
description: Lär dig hur du ställer in skugga på en Word-form med C#. Den här guiden
  visar också hur du lägger till formskugga, justerar formens transparens och lägger
  till rektangelskugga.
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: sv
og_description: Hur ställer du in skugga på en Word-form i C#? Följ den här steg‑för‑steg‑guiden
  för att lägga till formskugga, justera formens transparens och lägga till rektangelskugga.
og_title: Hur man lägger till skugga på en Word-form – C#‑handledning
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Hur man sätter skugga på en Word-form – C#‑handledning
url: /sv/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så sätter du skugga på en Word-form – C#-handledning

Har du någonsin undrat **hur man sätter skugga** på en form i ett Word‑dokument utan att trixa med användargränssnittet? Du är inte ensam. I många rapporter eller marknadsföringspresentationer får en subtil drop‑shadow en rektangel att sticka ut, och att göra det programatiskt sparar timmar.

I den här guiden går vi igenom ett komplett, färdigt‑att‑köra exempel som inte bara visar **hur man sätter skugga**, utan också täcker **add shape shadow**, **adjust shape transparency** och till och med **add rectangle shadow** för de klassiska förklaringsrutorna. När du är klar har du en Word‑fil (`output.docx`) som ser polerad ut, och du förstår varför varje egenskap är viktig.

## Förutsättningar

- .NET 6+ (eller .NET Framework 4.7.2) med en C#‑kompilator  
- Aspose.Words för .NET NuGet‑paket (`Install-Package Aspose.Words`)  
- Grundläggande kunskap om C# och Word‑objektmodellen  

Inga ytterligare bibliotek krävs—allt finns i Aspose.Words.

---

## Så sätter du skugga på en Word-form i C#

Nedan är den kompletta källkoden. Spara den som `Program.cs` och kör den från din IDE eller `dotnet run`. Koden laddar en befintlig `.docx`, hittar den första formen (en rektangel som standard), slår på dess skugga, justerar några visuella parametrar och sparar resultatet.

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **Vad du kommer att se** – Rektangeln har nu en svart drop‑shadow som är 30 % transparent, förskjuten 5 pt åt höger och ner, med en mjuk oskärpa. Öppna `output.docx` i Word för att verifiera.

## Justera formens transparens – varför det är viktigt

Transparens är inte bara en estetisk reglage; den påverkar läsbarheten. Ett värde på 0,0 gör skuggan helt ogenomskinlig, medan 1,0 döljer den helt. I kodsnutten ovan använde vi `0.3` för att uppnå en subtil effekt som fungerar på både ljusa och mörka bakgrunder. Känn dig fri att experimentera:

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

Kom ihåg att **adjust shape transparency** också kan tillämpas på formens fyllnadsfärg om du behöver en halvtransparent rektangel.

## Lägg till formskugga på olika objekt

Koden vi använde riktar sig mot ett `Shape`‑objekt, men samma `ShadowFormat`‑egenskaper finns på **Image**, **Chart** och även **TextBox**‑objekt. Här är ett snabbt mönster du kan kopiera‑klistra in:

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

Så oavsett om du **add shape shadow** till en logotyp eller en dekorativ ikon, är tillvägagångssättet identiskt.

## Så lägger du till skugga på vilken form som helst – specialfall

1. **Form utan en omgivningsruta** – Vissa Word‑former (som fria klotter) stöder inte skuggor. Att försöka sätta `ShadowFormat.Visible` misslyckas tyst. Kontrollera `shape.IsShadowSupported` om du behöver säkerhet.  
2. **Äldre Word‑versioner** – Skuggegenskaperna motsvarar funktioner i Word 2007+. Om du måste stödja Word 2003 kommer skuggan att ignoreras när filen öppnas.  
3. **Flera skuggor** – Aspose.Words stödjer för närvarande en enda skugga per form. Om du behöver en dubbellager‑effekt, duplicera formen, förskjut den och tillämpa olika skuggeinställningar.

## Lägg till rektangelskugga – ett verkligt exempel

Föreställ dig att du genererar en kvartalsrapport och varje sektionsrubrik är en färgad rektangel. Att lägga till en **add rectangle shadow** ger sidan ett “kort‑likt” utseende. Stegen är identiska med grundexemplet; se bara till att formen du riktar in dig på faktiskt är en rektangel (`shape.ShapeType == ShapeType.Rectangle`). Om du behöver skapa rektangeln från grunden, se kodsnutten nedan:

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

Att köra hela programmet med detta tillägg ger dig en ny rektangel som redan har den önskade **add rectangle shadow**‑effekten.

---

![Word shape with shadow](placeholder-image.png){alt="hur man sätter skugga på en form i Word"}

*Figur: Rektangeln efter att skuggeinställningarna har tillämpats.*

## Snabb sammanfattning (Punktlista – fusklapp)

- **Läs in** dokumentet med `new Document(path)`.  
- **Hitta** formen via `doc.GetChild(NodeType.Shape, index, true)`.  
- **Aktivera** skugga: `shape.ShadowFormat.Visible = true;`.  
- **Ställ in färg** med vilken `System.Drawing.Color` som helst.  
- **Justera transparens** (`0.0–1.0`) för att kontrollera opaciteten.  
- **OffsetX / OffsetY** flyttar skuggan horisontellt/vertikalt (punkter).  
- **BlurRadius** mjukar upp kanten—högre värden = suddigare skugga.  
- **Spara** filen och öppna den i Word för att se resultatet.

## Vad du kan prova härnäst?

- **Dynamiska färger** – Hämta skuggfärgen från ett tema eller användarinmatning.  
- **Villkorliga skuggor** – Tillämpa en skugga endast när formens bredd överstiger ett tröskelvärde.  
- **Batch‑bearbetning** – Loopa igenom alla former i ett dokument och **add shape shadow** automatiskt.  

Om du har följt med, vet du nu **hur man sätter skugga**, hur man **justerar formens transparens**, och hur man **add rectangle shadow** för den professionella finishen. Känn dig fri att experimentera, bryta saker och sedan fixa dem—kodning är den bästa läraren.

---

*Lycklig kodning! Om den här handledningen hjälpte dig, lämna en kommentar eller dela dina egna skuggtrick. Ju mer vi lär oss av varandra, desto snyggare blir våra Word‑dokument.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}