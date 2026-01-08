---
category: general
date: 2025-12-29
description: Lär dig hur du ställer in DPI när du konverterar Word till PNG med Aspose.Words.
  Denna steg‑för‑steg‑handledning täcker också export av högupplöst PNG och bildupplösningsinställningar.
draft: false
keywords:
- how to set dpi
- convert word to png
- save word as png
- high resolution png export
- set image resolution png
language: sv
og_description: Hur man ställer in DPI när man konverterar Word till PNG med Aspose.Words.
  Följ den här guiden för högupplöst PNG‑export och kontroll av bildupplösning.
og_title: Hur man ställer in DPI vid konvertering av Word till PNG – Komplett C#‑guide
tags:
- Aspose.Words
- C#
- Image Export
title: Hur man ställer in DPI vid konvertering av Word till PNG – Komplett C#-guide
url: /sv/net/programming-with-imagesaveoptions/how-to-set-dpi-when-converting-word-to-png-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så ställer du in DPI när du konverterar Word till PNG – Komplett C#-guide

Har du någonsin undrat **hur man ställer in DPI** när du konverterar ett Word‑dokument till PNG? Kanske behöver du skarpa skärmdumpar för en presentation, eller så genererar du utskrivbara tillgångar som måste se skarpa ut vid 300 dpi. Oavsett är du på rätt plats. I den här handledningen går vi igenom hur du konverterar en flersidig `.docx` till högupplösta PNG‑bilder med Aspose.Words, och vi visar exakt hur du ställer in bildens upplösning så att resultatet inte blir suddigt.

Vi kommer också att strö in tips om **convert word to png**, **save word as png**, och uppnå en **high resolution png export** utan ansträngning. Inga externa dokument, bara ett självständigt, körbart exempel som du kan kopiera‑klistra in i Visual Studio.

---

## Vad du behöver

- **Aspose.Words for .NET** (latest version, e.g., 24.9).  
- .NET 6+ (eller .NET Framework 4.7.2+) – någon nyare runtime fungerar.  
- En Word‑fil (`MultiPage.docx`) som du vill omvandla till PNG‑filer.  
- En utvecklingsmiljö – Visual Studio, Rider eller VS Code räcker.

Det är allt. Inga extra NuGet‑paket förutom Aspose.Words.

## Steg 1: Läs in Word‑dokumentet

Först och främst: vi behöver en in‑memory‑representation av Word‑filen. Klassen `Document` gör det åt oss.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the multi‑page document from disk
Document multiPageDoc = new Document("YOUR_DIRECTORY/MultiPage.docx");
```

> **Varför detta är viktigt:** Att läsa in dokumentet ger oss tillgång till dess `PageCount`, vilket vi senare behöver när vi instruerar Aspose att exportera **alla sidor** som PNG.

## Steg 2: Konfigurera ImageSaveOptions med DPI‑inställningar

Nu säger vi åt Aspose att vi vill ha PNG‑utdata *och* vi specificerar DPI. Egenskaperna `ImageHorizontalResolution` och `ImageVerticalResolution` är där magin sker.

```csharp
// Create PNG save options and set the DPI to 300
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    // Export every page (0‑based index to PageCount‑1)
    PageSet = new PageSet(0, multiPageDoc.PageCount - 1),

    // Set image resolution – this is the “how to set dpi” part
    ImageHorizontalResolution = 300, // 300 DPI horizontally
    ImageVerticalResolution   = 300, // 300 DPI vertically

    // Give each page a friendly file name
    PageSavingCallback = (sender, args) =>
    {
        args.ImageFileName = $"Page_{args.PageIndex + 1}.png";
    }
};
```

> **Proffstips:** 300 dpi är de‑facto‑standard för utskriftsklara grafik. Om du bara behöver skärmvisningskvalitet räcker 96 dpi och minskar filstorleken avsevärt.

## Steg 3: Spara alla sidor som en enda sammansatt PNG (eller separata filer)

Aspose låter dig antingen samla varje sida i en enda massiv sammansatt PNG **eller** skriva varje sida till en egen fil. Exemplet nedan visar *single tiled*-metoden, men `PageSavingCallback` som vi lade till säkerställer redan att separata filer skapas om du byter flaggan `ExportImagesAsSeparateFiles`.

```csharp
// Save the whole document as a tiled PNG file
multiPageDoc.Save("YOUR_DIRECTORY/Pages.png", imageSaveOptions);
```

Om du föredrar en fil per sida, sätt bara:

```csharp
imageSaveOptions.ExportImagesAsSeparateFiles = true;
```

och callback‑funktionen tar hand om att namnge varje `Page_#.png`.

## Steg 4: Verifiera resultatet

Efter att ha kört koden, öppna `Pages.png` (eller de genererade `Page_#.png`‑filerna) i en bildvisare. Du bör se skarpa, högupplösta bilder som matchar layouten i de ursprungliga Word‑sidorna.

- **Upplösningskontroll:** Högerklicka → Egenskaper → Detaljer → Horizontal DPI / Vertical DPI → bör visa **300**.  
- **Storlekskontroll:** Vid 300 dpi blir en vanlig A4‑sida (8,27 tum × 11,69 tum) ungefär 2481 × 3508 pixlar – perfekt för utskrift.

## Vanliga fallgropar & hur du undviker dem

| Problem | Varför det händer | Lösning |
|---------|-------------------|--------|
| **Suddigt resultat** | DPI kvar på standard (96) | Ställ explicit in `ImageHorizontalResolution` **och** `ImageVerticalResolution`. |
| **Saknade sidor** | `PageSet` täcker bara en delmängd | Använd `new PageSet(0, multiPageDoc.PageCount - 1)` för att inkludera alla sidor. |
| **Filnamnskrockar** | Callback inte satt | Tillhandahåll en `PageSavingCallback` som genererar unika namn. |
| **Stor filstorlek** | 600 dpi eller högre utan behov | Välj den lägsta DPI som fortfarande uppfyller ditt kvalitetskrav. |
| **Out‑of‑memory‑fel** för stora dokument | Export av en massiv sammansatt PNG | Byt till `ExportImagesAsSeparateFiles = true` för att skriva varje sida individuellt. |

## Avancerat: Exportera till olika PNG‑varianter

Ibland behöver du en **transparent bakgrund** eller ett **annat färgdjup**. Aspose.Words stödjer dessa justeringar via `PngOptions` i `ImageSaveOptions`.

```csharp
imageSaveOptions.PngOptions = new PngOptions
{
    // Enable transparency
    Transparency = true,

    // 8‑bit color depth (smaller file) or 24‑bit for full color
    BitDepth = 24
};
```

Du kan också kombinera detta med DPI‑inställningarna ovan för att få en **high resolution png export** som är klar för både webben och utskrift.

## Fullt fungerande exempel

Nedan är det kompletta, kopiera‑och‑klistra‑klara programmet. Byt bara ut `YOUR_DIRECTORY` mot den faktiska sökvägen på din maskin.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/MultiPage.docx");

        // 2️⃣ Configure PNG export with 300 DPI
        ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Png)
        {
            PageSet = new PageSet(0, doc.PageCount - 1),
            ImageHorizontalResolution = 300,
            ImageVerticalResolution = 300,
            // Optional: separate files per page
            // ExportImagesAsSeparateFiles = true,

            // 3️⃣ Friendly file names for each page
            PageSavingCallback = (sender, args) =>
            {
                args.ImageFileName = $"Page_{args.PageIndex + 1}.png";
            },

            // 4️⃣ High‑resolution PNG tweaks (transparent background, 24‑bit)
            PngOptions = new PngOptions
            {
                Transparency = true,
                BitDepth = 24
            }
        };

        // 5️⃣ Save – either a tiled PNG or separate files
        doc.Save("YOUR_DIRECTORY/Pages.png", options);

        Console.WriteLine("Conversion complete! Check YOUR_DIRECTORY for the PNG files.");
    }
}
```

Kör programmet, så får du en **high resolution PNG export** av varje sida, var och en med exakt den DPI du angav.

## Vanliga frågor

**Q: Fungerar detta med äldre `.doc`‑filer?**  
A: Absolut. Aspose.Words abstraherar formatet, så samma kod hanterar `.doc`, `.docx`, `.rtf` och även `.odt`.

**Q: Kan jag exportera till JPEG istället för PNG?**  
A: Ja – byt bara `SaveFormat.Png` till `SaveFormat.Jpeg` och justera `JpegOptions` om det behövs.

**Q: Vad händer om jag behöver 600 dpi för en stor affisch?**  
A: Ställ in `ImageHorizontalResolution = 600` och `ImageVerticalResolution = 600`. Håll koll på minnesanvändning; stora DPI‑värden ökar pixelmåtten snabbt.

**Q: Finns det ett sätt att batch‑processa många Word‑filer?**  
A: Lägg in logiken i en `foreach (var file in Directory.GetFiles(folder, "*.docx"))`‑loop. Kom ihåg att avyttra varje `Document`‑instans eller återanvänd ett enda `ImageSaveOptions`‑objekt för effektivitet.

## Slutsats

Vi har gått igenom **hur man ställer in DPI** när du **konverterar Word till PNG** med Aspose.Words, behandlat nyanserna i **high resolution PNG export**, och gett dig ett färdigt kodexempel som **save word as png** med exakt kontroll över bildens upplösning. Genom att justera `ImageHorizontalResolution`, `ImageVerticalResolution` och eventuellt `PngOptions` kan du skapa utskriftsklara grafik eller lätta webbresurser med förtroende.

Nästa steg? Prova att experimentera med olika DPI‑värden, byt till export av separata filer, eller kombinera detta arbetsflöde med en PDF‑till‑PNG‑pipeline för ännu bredare dokumenthantering. Samma principer gäller när du **set image resolution png** för andra format, så du är nu rustad att hantera ett brett spektrum av bild‑export‑scenarier.

Lycka till med kodandet, och må dina PNG‑filer alltid vara knivskarpa! 

![How to set DPI when converting Word to PNG – example output](/images/how-to-set-dpi-word-to-png.png "how to set dpi")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}