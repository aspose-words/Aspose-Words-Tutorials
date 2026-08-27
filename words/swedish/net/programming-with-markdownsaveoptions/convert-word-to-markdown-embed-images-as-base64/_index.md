---
category: general
date: 2026-01-03
description: Konvertera Word till Markdown och bädda in bilder som base64 på en gång.
  Lär dig hur du sparar Word som markdown, genererar markdown från Word och använder
  base64‑bild‑data‑uri.
draft: false
keywords:
- convert word to markdown
- embed images as base64
- save word as markdown
- base64 image data uri
- generate markdown from word
language: sv
og_description: Konvertera Word till Markdown och bädda in bilder som base64‑data‑URI:er.
  Denna steg‑för‑steg‑handledning visar hur du sparar Word som markdown och genererar
  markdown från Word.
og_title: Konvertera Word till Markdown – Guide för Base64‑bildinbäddning
tags:
- Aspose.Words
- C#
- Markdown
title: Konvertera Word till Markdown – Bädda in bilder som Base64
url: /sv/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Konvertera Word till Markdown – Bädda in bilder som Base64

Har du någonsin behövt **konvertera Word till markdown** men stött på problem med bilderna? Du är inte ensam. Word gillar att lagra bilder som separata filer, medan markdown föredrar de där små `data:image/...;base64,`‑strängarna som håller allt prydligt i en enda fil.  

I den här handledningen går vi igenom en komplett, färdig‑att‑köra‑lösning som **sparar Word som markdown**, **bäddar in bilder som base64**, och dessutom visar hur du **genererar markdown från Word** med Aspose.Words för .NET. När du är klar har du en enda `.md`‑fil som renderas exakt som originaldokumentet—inga externa bildmappar behövs.

## Vad du behöver

- **.NET 6.0 eller senare** (allt som kan referera ett NuGet‑paket)
- **Aspose.Words for .NET** (gratis provversion fungerar bra för testning)
- En enkel `.docx`‑fil med några bilder (vi kallar den `input.docx`)
- Din favorit‑IDE (Visual Studio, Rider, VS Code—välj vad du föredrar)

Om du redan har dem, toppen—låt oss sätta igång. Om inte, installeras NuGet‑paketet med en enda rad:

```bash
dotnet add package Aspose.Words
```

## Steg 1: Ladda Word‑dokumentet — utgångspunkten för **konvertera Word till markdown**

Först måste vi läsa in `.docx`‑filen i minnet. Här börjar konverteringsmagin.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file that contains the images.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **Varför detta är viktigt:**  
> Att ladda dokumentet ger Aspose full åtkomst till texten, stilarna och alla inbäddade resurser. Utan detta steg finns det inget att konvertera.

## Steg 2: Ställ in MarkdownSaveOptions med en Resource‑Saving‑Callback

Aspose låter dig avlyssna varje resurs (som bilder) som normalt skulle skrivas till disk. Genom att tillhandahålla en anpassad `IResourceSavingCallback` kan vi ersätta den standardfil‑baserade sparningen med en **base64‑bild‑data‑uri**.

```csharp
// Configure Markdown save options so that images become Base64 URIs.
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceHandler()
};
```

### Den anpassade hanteraren – omvandla bilder till Base64

Nedan är den fullständiga implementationen. Lägg märke till hur vi kontrollerar `args.ResourceType == ResourceType.Image` och sedan:

1. Skriv bilden till en `MemoryStream`.
2. Konvertera byte‑arrayen till en Base64‑sträng.
3. Bygg en `data:image/jpeg;base64,`‑URI och tilld den till `args.Uri`.

```csharp
// Custom handler that converts each image resource to a Base64 data URI.
class MyResourceHandler : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only process images – leave other resources untouched.
        if (args.ResourceType == ResourceType.Image)
        {
            // Prepare an in‑memory stream for the image.
            using (MemoryStream ms = new MemoryStream())
            {
                // Save the image using default JPEG options.
                args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                // Build the Base64 data URI.
                string base64 = Convert.ToBase64String(ms.ToArray());
                args.Uri = $"data:image/jpeg;base64,{base64}";
                // No need to keep the stream open after we set the URI.
                args.KeepResourceStreamOpen = false;
            }
        }
    }
}
```

> **Proffstips:** Om ditt käll‑Word använder PNG‑filer, byt `ImageSaveOptions.DefaultJpeg` mot `ImageSaveOptions.DefaultPng` och ändra MIME‑typen därefter (`image/png`).

## Steg 3: Spara dokumentet som Markdown – det sista **save word as markdown**‑steget

Nu när callback‑en är klar är den faktiska sparningen en en‑radig kod.

```csharp
// Save the document to a Markdown file. Images are already embedded.
document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
```

När du öppnar `output.md` i någon markdown‑visare (VS Code‑förhandsgranskning, GitHub, osv.) ser du texten exakt som i original‑Word‑filen, och bilderna visas inline utan separata bildfiler.

## Förväntad utdata

```markdown
# Sample Title

Here’s a paragraph that originally lived in Word.

![Embedded Image](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxISEhU...
```

`![Embedded Image]`‑raden är en **base64‑bild‑data‑uri**—hela bilden är kodad där. Inga extra mappar, inga brutna länkar.

## Edge Cases & hur du hanterar dem

| Situation | Vad du ska göra |
|-----------|-----------------|
| **Stora bilder** – Base64 ökar storleken med ~33% | Överväg att ändra storlek innan konvertering: `args.ResourceData.Save(ms, new ImageSaveOptions { ImageResolution = 72 })`. |
| **Icke‑JPEG‑bilder** (PNG, GIF) | Detektera originalformatet via `args.ResourceData.ImageType` och sätt rätt MIME‑typ (`image/png`, `image/gif`). |
| **Mycket långa dokument** (hundratals bilder) | Håll koll på minnesanvändning; du kan strömma varje bild till disk tillfälligt om processen får slut på RAM. |
| **Behöver separata bildfiler** (t.ex. för en statisk webbplats) | Returnera `false` från callback‑en för bilder du vill behålla som filer, och låt Aspose skriva dem till en mapp. |

## Vanliga frågor (Svarade i förväg)

- **Fungerar detta med .doc‑filer?** Ja—Aspose.Words kan läsa in äldre `.doc`‑filer på samma sätt som du läser in `.docx`. Peka bara `new Document("myfile.doc")` på den.
- **Vad händer med tabeller och fotnoter?** De stöds fullt ut av Markdown‑exportören. Tabeller blir markdown‑tabeller; fotnoter blir inline‑referenser.
- **Kan jag ändra markdown‑varianten?** `MarkdownSaveOptions` har en egenskap `MarkdownVersion` (CommonMark, GitHub, osv.). Ställ in den innan du sparar om du behöver en specifik syntax.

## Fullt, färdigt‑att‑köra‑exempel

Nedan är det kompletta programmet som du kan kopiera‑och‑klistra in i en konsolapp. Det inkluderar alla using‑satser, handler‑klassen och felhantering.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                // 1️⃣ Load the source Word document.
                Document doc = new Document("YOUR_DIRECTORY/input.docx");

                // 2️⃣ Prepare Markdown options with our custom image handler.
                MarkdownSaveOptions options = new MarkdownSaveOptions
                {
                    ResourceSavingCallback = new MyResourceHandler()
                };

                // 3️⃣ Save as Markdown – images become Base64 URIs.
                string outputPath = "YOUR_DIRECTORY/output.md";
                doc.Save(outputPath, options);

                Console.WriteLine($"✅ Success! Markdown saved to {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Conversion failed: {ex.Message}");
            }
        }
    }

    // Custom callback that embeds images as Base64 data URIs.
    class MyResourceHandler : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType == ResourceType.Image)
            {
                using (MemoryStream ms = new MemoryStream())
                {
                    // Preserve original format if you prefer PNG/GIF.
                    args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                    string base64 = Convert.ToBase64String(ms.ToArray());
                    args.Uri = $"data:image/jpeg;base64,{base64}";
                    args.KeepResourceStreamOpen = false;
                }
            }
        }
    }
}
```

Kör programmet, öppna den genererade `output.md`, och du ser en perfekt markdown‑replik av din Word‑fil—**konvertera Word till markdown** har aldrig varit enklare.

## Sammanfattning

Vi började med problemet att **konvertera Word till markdown** samtidigt som bilderna hålls inline. Genom att ladda dokumentet, konfigurera en `MarkdownSaveOptions`‑callback och spara filen uppnådde vi en ren **save word as markdown**‑lösning som producerar **base64‑bild‑data‑uri**‑strängar. Du vet nu också hur du **bäddar in bilder som base64**, hanterar edge cases och finjusterar processen för olika bildtyper.

## Vad blir nästa?

- **Generera HTML istället för markdown** – byt `MarkdownSaveOptions` mot `HtmlSaveOptions` och återanvänd samma callback.
- **Batch‑konvertera flera filer** – omslut logiken i en `foreach`‑loop över en mapp.
- **Integrera i en CI‑pipeline** – automatisera dokumentationsgenerering för statiska webbplatser.

Känn dig fri att experimentera, justera bildkvaliteten, eller till och med lägga till din egen anpassade resurs‑hantering (t.ex. ladda upp bilder till en CDN och infoga URL‑en). Himlen är gränsen när du kombinerar Aspose.Words med lite C#‑genialitet.

Lycka till med kodandet, och må din markdown alltid renderas perfekt! 

![Diagram som visar konverteringsflöde Word till markdown – bädda in bilder som base64](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNjAwIiBoZWlnaHQ9IjQwMCIgdmlld0JveD0iMCAwIDYwMCA0MDAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PHJlY3Qgd2lkdGg9IjYwMCIgaGVpZ2h0PSI0MDAiIGZpbGw9IiNmZmYiIHN0cm9rZT0iI2NjYyIgLz48dGV4dCB4PSI1MCIgeT0iMjAwIiBmb250LXNpemU9IjM2IiBmaWxsPSIjMDAwIj5JbWFnZSBJbWFnZSBJbWFnZSBJbWFnZTwvdGV4dD48L3N2Zz4= "convert word to markdown flow diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}