---
category: general
date: 2026-04-10
description: hur man ställer in dpi när du konverterar Word till PNG. Lär dig hur
  du exporterar Word till PNG med en anpassad rutnätslayout och hög upplösning.
draft: false
keywords:
- how to set dpi
- convert word to png
- how to export word
- export word to png
- create png grid
language: sv
og_description: hur man ställer in dpi när man exporterar ett Word‑dokument. Den här
  handledningen visar hur man konverterar Word till PNG, exporterar Word till PNG
  och skapar ett PNG‑rutnät med C#.
og_title: hur man ställer in dpi – Komplett guide för att exportera Word till PNG
tags:
- C#
- Aspose.Words
- ImageExport
title: hur man ställer in DPI – Exportera Word till PNG‑rutnät i C#
url: /sv/net/programming-with-imagesaveoptions/how-to-set-dpi-export-word-to-png-grid-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hur man ställer in dpi – Exportera Word till PNG‑rutnät i C#

Har du någonsin funderat **hur man ställer in dpi** för en Word‑till‑PNG‑konvertering utan att dra i håret? Du är inte ensam. I många projekt—tänk automatiska rapportgeneratorer eller miniatyr‑pipelines—behöver du en skarp PNG som respekterar ett specifikt DPI, och ofta vill du också ha flera sidor packade i en enda rutnätsbild. I den här guiden går vi igenom en komplett, färdig‑att‑köra‑lösning som **konverterar Word till PNG**, låter dig **exportera Word till PNG** med en 300 DPI‑inställning, och till och med **skapar ett PNG‑rutnät** i ett svep.

> **Quick win:** Vid slutet av den här artikeln har du en enda rad C# som tar `input.docx` och spottar ut `output.png` med 300 DPI, arrangerad i ett 2 × 2‑rutnät. Inga extra verktyg, ingen manuell bildredigering.

## Vad du kommer att lära dig

- Hur man **ställer in DPI** med Aspose.Words `ImageSaveOptions`.
- De exakta stegen för att **exportera Word till PNG** med en anpassad sidlayout.
- Hur man **skapar ett PNG‑rutnät** (fyra sidor per rad/kolumn) i en enda fil.
- Vanliga fallgropar vid konvertering av stora dokument och hur man undviker dem.
- Ett antal variationer: exportera enskilda sidor, ändra rutnätsstorlek och byta PNG mot JPEG.

### Förutsättningar

| Krav | Varför det är viktigt |
|------|-----------------------|
| **Aspose.Words for .NET** (v23.12 eller nyare) | Tillhandahåller klasserna `Document` och `ImageSaveOptions` som vi förlitar oss på. |
| **.NET 6+** (eller .NET Framework 4.7.2) | Säkerställer kompatibilitet med det senaste API‑ytan. |
| **Grundläggande C#‑kunskaper** | Du behöver förstå namnrymder och filsökvägar. |
| **En Word‑fil** (`input.docx`) | Källdokumentet som vi ska konvertera. |

Om du ännu inte har installerat Aspose.Words, kör:

```bash
dotnet add package Aspose.Words
```

Nu när scenen är satt, låt oss dyka ner i koden.

## Steg 1 – Ladda källdokumentet (how to export word)

Det allra första du gör är att läsa in Word‑filen i minnet. Här börjar **how to export word**.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source .docx
Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

> **Pro tip:** Använd en absolut sökväg eller `Path.Combine` för att undvika överraskningar på olika OS.

## Steg 2 – Konfigurera Image Save Options (how to set dpi & create png grid)

Här är hjärtat i handledningen. Vi talar om för Aspose.Words exakt hur vi vill att PNG‑filen ska se ut: 300 DPI, PNG‑format, och en **grid‑layout** som packar fyra sidor i en enda bild.

```csharp
// Create PNG save options with a grid layout
ImageSaveOptions imgOptions = new ImageSaveOptions(SaveFormat.Png)
{
    // Arrange pages in a grid (2 columns × 2 rows = 4 pages)
    PageLayout = ImageSaveOptions.PageLayoutType.Grid,
    
    // Number of columns in the grid – 2 columns => 2 rows for 4 pages
    PageCount = 4,
    
    // Set the DPI – this is where we *how to set dpi*
    HorizontalResolution = 300,
    VerticalResolution = 300
};
```

### Varför dessa inställningar är viktiga

- **`PageLayout = Grid`** – Utan detta skulle varje sida sparas som en separat PNG. Rutnätsalternativet slår ihop dem, vilket sparar dig ett efterbearbetningssteg.
- **`PageCount = 4`** – Styr hur många sidor rutnätet ska innehålla. Om ditt dokument har fler än fyra sidor skapar Aspose automatiskt ytterligare rader.
- DPI‑inställningar – `HorizontalResolution` och `VerticalResolution` är reglagen som svarar på frågan **hur man ställer in dpi**. En 300 DPI‑bild är utskriftsklar och ser skarp ut på retina‑skärmar.

## Steg 3 – Spara dokumentet som en enda PNG (export word to png)

Nu kör vi sparoperationen. Denna enda rad gör det tunga arbetet.

```csharp
// Save the document pages as one PNG image
doc.Save(@"YOUR_DIRECTORY\output.png", imgOptions);
```

Efter att den här raden har körts hittar du `output.png` i den angivna mappen. Öppna den, så bör du se ett 2 × 2‑rutnät av de fyra första sidorna, var och en renderad med 300 DPI.

![how to set dpi example](https://example.com/placeholder.png "hur man ställer in dpi när man exporterar Word till PNG")

*Bild‑alt‑text: hur man ställer in dpi när man exporterar Word till PNG – visar ett 2×2‑rutnät PNG.*

## Steg 4 – Verifiera resultatet (create png grid)

En snabb kontroll sparar huvudvärk senare. Du kan programatiskt bekräfta DPI och dimensioner:

```csharp
using System.Drawing;

// Load the generated PNG
using (Bitmap bmp = new Bitmap(@"YOUR_DIRECTORY\output.png"))
{
    Console.WriteLine($"Width: {bmp.Width}px, Height: {bmp.Height}px");
    Console.WriteLine($"Horizontal DPI: {bmp.HorizontalResolution}");
    Console.WriteLine($"Vertical DPI: {bmp.VerticalResolution}");
}
```

Om konsolen skriver ut `300` för båda DPI‑värdena har du lyckats **hur man ställer in dpi**. Bredden och höjden kommer att spegla den kombinerade storleken på fyra sidor.

## Avancerade variationer

### Konvertera Word till PNG – En fil per sida

Ibland behöver du separata PNG‑filer istället för ett rutnät. Byt bara `PageLayout` till `SinglePage` och loopa igenom sidorna:

```csharp
for (int i = 0; i < doc.PageCount; i++)
{
    imgOptions.PageIndex = i;               // Export only this page
    imgOptions.PageLayout = ImageSaveOptions.PageLayoutType.SinglePage;
    doc.Save($@"YOUR_DIRECTORY\page_{i + 1}.png", imgOptions);
}
```

Nu har du `page_1.png`, `page_2.png`, … – perfekt för miniatyrgallerier.

### Exportera Word till PNG med en annan rutnätsstorlek

Om du behöver ett 3 × 3‑rutnät (nio sidor), justera bara `PageCount`:

```csharp
imgOptions.PageCount = 9;          // 3 columns × 3 rows
imgOptions.PageLayout = ImageSaveOptions.PageLayoutType.Grid;
```

Aspose beräknar automatiskt antalet nödvändiga rader.

### Byt PNG mot JPEG (om filstorleken spelar roll)

Att byta format är lika enkelt som att ersätta `SaveFormat.Png` med `SaveFormat.Jpeg`. Du kan också styra JPEG‑kvaliteten:

```csharp
ImageSaveOptions jpegOptions = new ImageSaveOptions(SaveFormat.Jpeg)
{
    PageLayout = ImageSaveOptions.PageLayoutType.Grid,
    PageCount = 4,
    HorizontalResolution = 300,
    VerticalResolution = 300,
    JpegQuality = 90   // 0‑100, higher = better quality
};

doc.Save(@"YOUR_DIRECTORY\output.jpg", jpegOptions);
```

### Hantera stora dokument

När du arbetar med dokument över 100 sidor, överväg att streama utdata för att undvika minnespress:

```csharp
using (FileStream fs = new FileStream(@"YOUR_DIRECTORY\large_output.png", FileMode.Create))
{
    doc.Save(fs, imgOptions);
}
```

Streaming säkerställer att processen förblir lättviktig, även på modest server.

## Vanliga fallgropar & hur man undviker dem

| Symtom | Orsak | Lösning |
|--------|-------|---------|
| PNG ser suddig ut | DPI lämnades på standard 96 | **Ställ `HorizontalResolution` och `VerticalResolution` till 300** (eller högre). |
| Endast första sidan visas | `PageLayout` fortfarande satt till `SinglePage` | Byt till `ImageSaveOptions.PageLayoutType.Grid`. |
| Utdatafilen är enorm | PNG‑format med 300 DPI kan bli stort | Använd JPEG med `JpegQuality` < 90, eller minska DPI om utskriftskvalitet inte krävs. |
| Rutnätet kapar sidmarginaler | Standardhantering av marginaler | Justera `ImageSaveOptions.PageMargins` vid behov. |

## Sammanfattning – Vad vi gick igenom

- **hur man ställer in dpi** – genom att konfigurera `HorizontalResolution` och `VerticalResolution`.
- **konvertera word till png** – med `ImageSaveOptions` och `SaveFormat.Png`.
- **hur man exporterar word** – genom att ladda dokumentet med `Document` och anropa `Save`.
- **exportera word till png** – en enradare som producerar en högupplöst PNG.
- **skapa png‑rutnät** – genom att sätta `PageLayout = Grid` och `PageCount` för att styra layouten.

Allt detta får plats i ett kompakt, självständigt C#‑snutt som du kan klistra in i vilket .NET‑projekt som helst.

## Vad blir nästa steg?

- Experimentera med **olika DPI‑värden** (150, 600) för att se hur filstorleken förändras.
- Kombinera detta tillvägagångssätt med **Aspose.PDF** för att slå ihop PNG‑rutnätet till en PDF‑rapport.
- Utforska **färgrymdsomvandling** (RGB → CMYK) om du skickar PNG‑filen till ett professionellt tryckeri.
- Titta på **asynkron sparning** (`doc.SaveAsync`) för UI‑responsiva applikationer.

Har du frågor om kantfall—som att exportera krypterade DOCX‑filer eller hantera inbäddade teckensnitt? Lägg en kommentar så gräver jag gärna djupare.

*Glad kodning! Om den här handledningen hjälpte dig **hur man ställer in dpi** och exportera dina Word‑dokument till ett elegant PNG‑rutnät, ge den ett stjärnmärke eller dela den med en kollega som kämpar med samma problem.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}