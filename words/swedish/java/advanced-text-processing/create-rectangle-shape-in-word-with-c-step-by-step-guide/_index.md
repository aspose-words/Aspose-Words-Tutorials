---
category: general
date: 2026-03-04
description: Lär dig hur du skapar en rektangel, lägger till skugga på formen och
  applicerar skuggeffekt i ett Word‑dokument, och sedan sparar Word‑dokumentet automatiskt.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- save word document
- create blank document
language: sv
og_description: Skapa en rektangel, lägg till skugga på formen och tillämpa skuggeffekten
  i ett Word‑dokument med C#. Följ den här guiden för att enkelt spara Word‑dokumentet.
og_title: Skapa rektangel i Word – Komplett C#‑handledning
tags:
- C#
- Aspose.Words
- Document Automation
title: Skapa rektangelform i Word med C# – Steg‑för‑steg‑guide
url: /sv/java/advanced-text-processing/create-rectangle-shape-in-word-with-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangelform i Word med C# – Komplett programmeringshandledning

Har du någonsin behövt **create rectangle shape** i en Word‑fil men varit osäker på var du ska börja? Du är inte ensam—många utvecklare stöter på den muren när de först dyker in i programmatisk dokumentgenerering. Den goda nyheten är att med några rader C# kan du infoga en rektangel, **add shadow to shape**, och **apply shadow effect** utan att någonsin öppna Word själv. I den här guiden går vi igenom hela processen, från en ny **create blank document** till att spara den slutliga **save word document** på disk.

Vi kommer att täcka allt du behöver: det nödvändiga NuGet‑paketet, de exakta API:erna, varför varje egenskap är viktig, och ett antal tips för att undvika de vanligaste fallgroparna. I slutet har du ett fullt körbart exempel som du kan släppa in i vilket .NET‑projekt som helst.

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar även med .NET Framework 4.7+)
- Visual Studio 2022 eller någon IDE du föredrar
- **Aspose.Words for .NET** installerat via NuGet (`Install-Package Aspose.Words`)
- Grundläggande kunskap om C#‑syntax

Inga ytterligare Word‑interop‑bibliotek behövs—Aspose.Words hanterar allt i minnet.

## Steg 1 – Skapa ett tomt dokument

Det första vi gör är **create blank document**. Tänk på det som en tom duk som vi senare kommer att **create rectangle shape** på.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a new blank document
Document doc = new Document();   // This gives us a fresh Word file
```

> **Why this matters:** Att börja med ett rent `Document`‑objekt garanterar att inga dolda stilar eller sektioner stör rektangelns placering senare.

## Steg 2 – Infoga en rektangelform i dokumentet

Nu **create rectangle shape** faktiskt. Vi kommer att sätta dess storlek, positionering och tala om för Word att inte flöda text runt den.

```csharp
// Step 2: Add a rectangle shape
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 200;          // Width in points (1 point = 1/72 inch)
rectangle.Height = 100;         // Height in points
rectangle.WrapType = WrapType.None; // No text wrapping
```

> **Pro tip:** Om du behöver att rektangeln ska ligga i en tabellcell, ändra `WrapType` till `WrapType.Inline`. För de flesta rapporter håller `None` formen flytande ovanför texten.

## Steg 3 – Lägg till skugga på formen och konfigurera dess utseende

Här händer magin: vi **add shadow to shape** och **apply shadow effect**. Skuggan får rektangeln att sticka ut på sidan, särskilt när den skrivs ut.

```csharp
// Step 3: Enable shadow and set its properties
rectangle.ShadowFormat.Visible = true;          // Turn on the shadow
rectangle.ShadowFormat.BlurRadius = 5.0;        // Softness of the shadow edge
rectangle.ShadowFormat.Transparency = 0.3;      // 30 % transparent
rectangle.ShadowFormat.OffsetX = 8;             // Horizontal shift
rectangle.ShadowFormat.OffsetY = 8;             // Vertical shift
rectangle.ShadowFormat.Color = Color.Blue;     // Shadow colour
```

> **Why these values?**  
> - **BlurRadius** styr hur suddiga kanterna blir; ett värde runt `5` ger ett subtilt, professionellt utseende.  
> - **Transparency** låter den underliggande texten förbli läsbar.  
> - **OffsetX/Y** flyttar skuggan bort från formen, vilket skapar djup.  
> - Att använda en **blue** nyans är bara ett exempel—vilken `System.Drawing.Color` som helst fungerar.

## Steg 4 – Lägg till den konfigurerade formen i dokumentkroppen

Med rektangeln fullt stylad, **add rectangle shape** vi nu till dokumentets första sektion. Detta steg placerar faktiskt formen i filen.

```csharp
// Step 4: Append the shape to the first section's body
doc.FirstSection.Body.AppendChild(rectangle);
```

> **Edge case:** Om ditt dokument redan innehåller sektioner kan du vilja rikta in dig på en specifik (`doc.Sections[2]` till exempel). Koden ovan fungerar för ett dokument med en enda sektion, vilket är vanligt för snabba rapporter.

## Steg 5 – Spara Word‑dokumentet

Till sist **save word document** vi till disk. Filen kommer att innehålla rektangeln med sin skugga, redo att öppnas i Microsoft Word.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\shadowed_rectangle.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Tip:** Använd `doc.Save(outputPath, SaveFormat.Docx)` om du behöver vara explicit angående formatet. `Save`‑metoden upptäcker automatiskt filändelsen, men att vara explicit kan undvika förvirring när sökvägen genereras programatiskt.

## Fullt, körbart exempel

Nedan är det kompletta programmet som du kan kopiera‑och‑klistra in i en konsolapplikation. Det inkluderar alla `using`‑satser och `Main`‑metoden, så du kan köra det direkt.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document
            Document doc = new Document();

            // 2️⃣ Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 200;
            rectangle.Height = 100;
            rectangle.WrapType = WrapType.None;

            // 3️⃣ Apply shadow effect
            rectangle.ShadowFormat.Visible = true;
            rectangle.ShadowFormat.BlurRadius = 5.0;
            rectangle.ShadowFormat.Transparency = 0.3;
            rectangle.ShadowFormat.OffsetX = 8;
            rectangle.ShadowFormat.OffsetY = 8;
            rectangle.ShadowFormat.Color = Color.Blue;

            // 4️⃣ Insert the shape into the document body
            doc.FirstSection.Body.AppendChild(rectangle);

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\shadowed_rectangle.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document saved at {outputPath}");
        }
    }
}
```

### Förväntat resultat

När du öppnar *shadowed_rectangle.docx* i Microsoft Word kommer du att se en blå‑rammad rektangel som svävar nära toppen av första sidan, med en mjuk blå skugga förskjuten 8 pt åt höger och neråt. Ingen extra text omger den eftersom vi satte `WrapType.None`.

## Vanliga frågor & variationer

| Question | Answer |
|----------|--------|
| **Kan jag ändra formen till en ellips?** | Ja—byt ut `ShapeType.Rectangle` mot `ShapeType.Ellipse`. Alla skuggegenskaper förblir desamma. |
| **Vad händer om jag behöver flera former?** | Upprepa helt enkelt Steg 2‑4 för varje ny `Shape`‑instans, justera `OffsetX/Y` eller `Left/Top` för att undvika överlappning. |
| **Finns det ett sätt att få skuggfärgen att matcha formens fyllning?** | Absolut. Sätt `rectangle.FillColor` först, och tilldela sedan `rectangle.ShadowFormat.Color = rectangle.FillColor;`. |
| **Hur infogar jag formen i en tabellcell?** | Använd `cell.FirstParagraph.AppendChild(rectangle);` efter att ha lokaliserat önskat `Cell`‑objekt. |
| **Fungerar detta på .NET Core?** | Ja—Aspose.Words är plattformsoberoende. Se bara till att referera rätt NuGet‑paketversion för .NET Core/5/6. |

## Vanliga fallgropar & pro‑tips

- **Pitfall:** Glömmer att sätta `ShadowFormat.Visible = true`. Skugg‑egenskaperna kommer att ignoreras tyst.  
  **Fix:** Aktivera alltid synlighet innan du justerar andra skuggparametrar.

- **Pitfall:** Att använda ett mycket stort `BlurRadius` (t.ex. 20) kan få skuggan att se suddig och oprofessionell ut.  
  **Fix:** Håll dig till värden mellan `3` och `8` för de flesta affärsdokument.

- **Pro tip:** Om du behöver att formen ska kunna väljas senare (t.ex. för slutanvändarredigering), undvik att sätta `WrapType.Inline`. Flytande former (`WrapType.None`) är enklare att flytta programatiskt.

- **Pro tip:** När du genererar många dokument i en loop, återanvänd en enda `Document`‑instans och anropa `doc.Clone(true)` för varje iteration för att förbättra prestanda.

## Relaterade ämnen du kan utforska härnäst

- **Add text inside a rectangle shape** – lär dig hur du använder `Shape.TextPath` för etiketter.  
- **Create complex diagrams** – kombinera flera former, anslutningar och gruppering.  
- **Export to PDF** – konvertera samma dokument till PDF med ett enda `doc.Save("output.pdf")`.  
- **Apply different fill styles** – gradienter, texturer eller till och med bilder i former.

## Slutsats

Vi har just **create rectangle shape**, **add shadow to shape**, och **apply shadow effect** i en Word‑fil med C#. Genom att följa de fem kortfattade stegen har du nu ett återanvändbart mönster för alla dokument‑automatiseringsscenarier, och du vet hur du **save word document** på ett pålitligt sätt. Känn dig fri att justera dimensioner, färger eller till och med byta ut rektangeln mot en annan geometri—Aspose.Words gör allt enkelt.

Om du tyckte att den här handledningen var hjälpsam, ge den en stjärna på GitHub, eller dela dina egna variationer i kommentarerna. Lycka till med kodandet, och må dina dokument alltid se lika polerade ut som den här skuggade rektangeln!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}