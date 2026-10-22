---
category: general
date: 2026-03-25
description: Maak een PDF-document in C# en leer hoe je een rechthoekvorm toevoegt,
  de vulkleur instelt, de vormgrootte aanpast en de transparantie van de vorm instelt
  in slechts een paar stappen.
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: nl
og_description: Maak een PDF-document in C# en zie hoe je een rechthoek toevoegt,
  de vulkleur, grootte en transparantie instelt voor een gepolijste PDF-uitvoer.
og_title: PDF-document maken met een rechthoekvorm – C#‑tutorial
tags:
- C#
- PDF
- Aspose.Words
title: PDF-document maken met een rechthoekvorm – volledige C#-gids
url: /nl/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# PDF‑document maken met een rechthoekige vorm – Volledige C#‑gids

Heb je ooit een **PDF‑document** moeten **maken** dat een op maat gestylede vorm bevat, maar wist je niet waar je moest beginnen? Je bent niet de enige. Of je nu een rapportgenerator of een marketingflyer bouwt, een rechthoek programmatisch tekenen, de vulkleur instellen, de grootte aanpassen en zelfs de transparantie regelen kan je PDF’s er veel professioneler uit laten zien.

In deze tutorial lopen we een volledig, kant‑klaar C#‑voorbeeld door dat **een PDF‑document maakt**, **een rechthoekige vorm toevoegt**, **de vulkleur instelt**, **de vormgrootte definieert**, en **de vormtransparantie instelt** voor een subtiele buitenste schaduw. Aan het einde heb je één PDF‑bestand (`shadow.pdf`) dat je kunt openen om het resultaat te zien.

> **Pro tip:** dezelfde aanpak werkt met andere vormtypen (ellipse, lijn, enz.) — vervang gewoon `ShapeType.RECTANGLE` door het type dat je nodig hebt.

---

## Wat je nodig hebt

| Voorwaarde | Waarom het belangrijk is |
|------------|--------------------------|
| **.NET 6+** (of .NET Framework 4.6+) | De Aspose.Words‑bibliotheek richt zich op moderne runtimes. |
| **Aspose.Words for .NET** NuGet‑pakket | Biedt `Document`, `Shape`, `ShadowEffect` en gerelateerde klassen. |
| **Een C#‑IDE** (Visual Studio, Rider, VS Code) | Maakt debuggen en uitvoeren van het voorbeeld moeiteloos. |
| **Basiskennis van C#** | Je begrijpt de syntaxis zonder een diepe duik. |

Je kunt de bibliotheek via de commandoregel installeren:

```bash
dotnet add package Aspose.Words
```

Dat is alles — geen extra DLL’s, geen native afhankelijkheden. Zodra het pakket aanwezig is, compileert en draait de onderstaande code.

---

## Stapsgewijze implementatie

Hieronder splitsen we het proces in vijf logische stappen. Elke stap heeft een duidelijke kop (zodat AI‑modellen het kunnen indexeren) en een kort code‑blok dat je direct kunt kopiëren‑plakken.

### ## 1. PDF‑document maken en het canvas voorbereiden

Het allereerste wat we doen is een `Document` instantieren. Beschouw het als een leeg canvas dat uiteindelijk je PDF‑bestand wordt.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **Waarom?** `Document` bevat alle secties, alinea’s en vormen. Beginnen met een schoon object garandeert dat er geen verborgen artefacten van eerdere runs aanwezig zijn.

### ## 2. Rechthoekige vorm toevoegen – vulkleur en vormgrootte instellen

Nu maken we een rechthoek, geven we hem een heldere gele vulkleur en definiëren we zijn afmetingen. Dit dekt zowel **add rectangle shape** als **set fill color** en **set shape size**.

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **Opmerking:** Breedte/hoogte worden gemeten in points (1 point = 1/72 inch). Pas deze getallen aan om ze op je lay‑out af te stemmen.

### ## 3. Een buitenste schaduw toepassen en vormtransparantie instellen

Schaduwen geven diepte, en het regelen van hun opacity is de kern van **set shape transparency**. Hieronder configureren we een grijze buitenste schaduw met 30 % transparantie.

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **Waarom transparantie instellen?** Een 30 % transparante schaduw ziet er subtiel uit, waardoor de rechthoek niet “plat” op de pagina lijkt.

### ## 4. De vorm in de document‑body invoegen

We plaatsen nu de rechthoek in de eerste alinea van de eerste sectie van het document. Deze stap brengt alles samen.

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **Randgeval:** Als je de vorm op een nieuwe pagina wilt, voeg dan `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;` toe vóór het toevoegen van de vorm.

### ## 5. Het document opslaan als PDF‑bestand

Tot slot schrijven we de in‑memory structuur naar een fysiek PDF‑bestand. Het bestand wordt weggeschreven naar de map die je opgeeft.

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

Wanneer je het programma uitvoert, verschijnt er een bestand met de naam `shadow.pdf`. Het openen ervan toont een gele rechthoek met een zachte grijze schaduw die 4 points is verschoven — precies wat onze code beschrijft.

> **Verwacht resultaat:** Een één‑pagina PDF waarin de rechthoek zich dicht bij de linkerbovenhoek van de pagina bevindt, gevuld met geel, 200 × 100 points groot, en met een half‑transparante buitenste schaduw.

---

## Volledig werkend voorbeeld (Klaar om te kopiëren‑plakken)

Hieronder staat het volledige bronbestand, klaar om in een nieuw console‑project te plaatsen.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **Tip:** Vervang `YOUR_DIRECTORY` door een absoluut pad zoals `C:\Temp` of een relatief pad zoals `.\output`. Het programma maakt de map aan als deze nog niet bestaat.

---

## Veelgestelde vragen (FAQ)

**Q: Kan ik de positie van de rechthoek op de pagina wijzigen?**  
A: Zeker. Stel `rectangle.Left` en `rectangle.Top` in (beide gemeten in points) voordat je de vorm aan de alinea toevoegt.

**Q: Wat als ik een transparante vulkleur wil in plaats van een transparante schaduw?**  
A: Gebruik `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` — het eerste argument is het alfacanal (0‑255), waarbij 128 ongeveer 50 % transparantie oplevert.

**Q: Werkt dit met .NET Core?**  
A: Ja. Aspose.Words ondersteunt .NET Standard 2.0+, dus je kunt dezelfde code draaien op .NET 6, .NET 7, of .NET Framework 4.6+.

**Q: Hoe kan ik meerdere vormen toevoegen?**  
A: Herhaal simpelweg stappen 2‑4 voor elke vorm, eventueel door ze in verschillende alinea’s of secties te plaatsen.

---

## Conclusie

We hebben zojuist **een PDF‑document** vanaf nul **gemaakt**, **een rechthoekige vorm toegevoegd**, **de vulkleur ingesteld**, **de grootte gedefinieerd**, en **de vormtransparantie aangepast** om een gepolijste schaduweffect te bereiken. De voorbeeldcode is zelfstandig, draait in minder dan een minuut, en laat de kernconcepten zien die je nodig hebt voor complexere PDF‑lay‑outs.

Klaar voor de volgende uitdaging? Probeer de rechthoek te vervangen door een vorm met afgeronde hoeken, embed een afbeelding in de vorm, of genereer automatisch een inhoudsopgave. Dezelfde API laat je tekst, afbeeldingen en vectoren stapelen — de mogelijkheden zijn eindeloos.

Als je deze gids nuttig vond, geef hem dan een ster op GitHub, deel hem met een collega, of laat een reactie achter met jouw eigen variaties. Veel programmeerplezier!

---

![create pdf document with rectangle shape example](/images/rectangle-shadow.png "Screenshot showing the created PDF with a yellow rectangle and gray outer shadow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}