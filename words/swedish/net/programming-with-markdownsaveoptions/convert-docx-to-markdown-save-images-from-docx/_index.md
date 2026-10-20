---
category: general
date: 2026-06-27
description: Konvertera docx till markdown och spara bilder från docx med Aspose.Words.
  Lär dig hur du extraherar bilder från Word‑filen och exporterar Word‑dokumentet
  som markdown.
draft: false
keywords:
- convert docx to markdown
- save images from docx
- extract images from word file
- export word document as markdown
language: sv
og_description: Konvertera docx till markdown och spara bilder från docx. Den här
  guiden visar hur du extraherar bilder från en Word‑fil och exporterar Word‑dokumentet
  som markdown.
og_title: Konvertera docx till markdown & spara bilder från docx
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  headline: Convert docx to markdown & save images from docx
  type: TechArticle
- description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  name: Convert docx to markdown & save images from docx
  steps:
  - name: How the code works
    text: '- **Loading the document** (`new Document(inputPath)`) gives us an in‑memory
      representation of the Word file, complete with all its parts—paragraphs, tables,
      and **images**. - **`MarkdownSaveOptions`** is where the magic happens. By attaching
      a `ResourceSavingCallback`, we gain full control over eve'
  - name: Quick sanity check
    text: '- Does the Markdown file open without errors in VS Code’s preview pane?
      ✅ - Are all pictures displayed when you view the file on GitHub? ✅ - Did the
      `Images` directory contain one file per picture from the original `.docx`? ✅'
  - name: What’s next?
    text: '- **Style the Markdown** – add a front‑matter block for Jekyll or Hugo.
      - **Automate the pipeline** – embed this code in an Azure DevOps or GitHub Action
      step. - **Handle tables and footnotes** – explore other `MarkdownSaveOptions`
      flags like `ExportTableBorderStyles`.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Markdown
- Word
title: Konvertera docx till markdown och spara bilder från docx
url: /sv/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-save-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Konvertera docx till markdown & spara bilder från docx

Har du någonsin undrat hur man **convert docx to markdown** utan att förlora bilderna som är inbäddade i din Word‑fil? Du är inte ensam—utvecklare behöver ofta en ren Markdown‑version av en rapport samtidigt som varje diagram, logotyp eller skärmdump behålls intakt.

I den här handledningen går vi igenom ett komplett, färdigt att köra exempel som **converts a .docx to Markdown**, **saves images from docx** till en mapp du väljer, och visar dig hur du **extract images from Word file** med det kraftfulla Aspose.Words‑biblioteket. I slutet kommer du också att veta hur du **export Word document as markdown** i en enda kodrad.

## Vad du behöver

- .NET 6+ (eller .NET Framework 4.7.2+) installerat på din maskin  
- En NuGet‑referens till `Aspose.Words` (gratis provversion fungerar bra)  
- Ett exempel `input.docx` som innehåller minst en bild  
- En IDE du gillar—Visual Studio, Rider eller till och med VS Code räcker  

Inga extra tredjepartsverktyg, ingen krånglig kommandoradsakrobatik. Bara ren C#‑kod.

## Konvertera docx till markdown – Översikt

Kärnidén är enkel:

1. Läs in källdokumentet i Word.  
2. Berätta för Aspose.Words hur du vill att externa resurser (som bilder) ska hanteras.  
3. Spara dokumentet som Markdown och låt biblioteket göra det tunga arbetet.

Nedan är det **fulla, körbara programmet**. Kopiera‑klistra gärna in det i ett nytt konsolprojekt och tryck `Ctrl+F5`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load the source document that contains images
        // -----------------------------------------------------------------
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        Document doc = new Document(inputPath);

        // -----------------------------------------------------------------
        // Step 2: Configure Markdown save options with a custom callback
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This callback runs for each external resource (images, CSS, etc.)
            ResourceSavingCallback = (sender, args) =>
            {
                // ---------------------------------------------------------
                // Step 3a: Save images to a custom folder using a unique name
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.Image)
                {
                    string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
                    Directory.CreateDirectory(imageFolder); // ensures folder exists

                    // Use a GUID so we never clash with existing files
                    string uniqueName = Guid.NewGuid().ToString() + args.Extension;
                    args.SavePath = Path.Combine(imageFolder, uniqueName);
                }

                // ---------------------------------------------------------
                // Step 3b: Skip CSS files – they aren't needed for plain Markdown
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.CssStyleSheet)
                    args.Cancel = true;
            }
        };

        // -----------------------------------------------------------------
        // Step 4: Export the document to Markdown, applying the options
        // -----------------------------------------------------------------
        string outputPath = Path.Combine("YOUR_DIRECTORY", "output.md");
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("Conversion complete! Markdown saved to " + outputPath);
        Console.WriteLine("Images extracted to " + Path.Combine("YOUR_DIRECTORY", "Images"));
    }
}
```

### Så fungerar koden

- **Loading the document** (`new Document(inputPath)`) ger oss en minnesrepresentation av Word‑filen, komplett med alla dess delar—paragrafer, tabeller och **images**.  
- **`MarkdownSaveOptions`** är där magin sker. Genom att fästa en `ResourceSavingCallback` får vi full kontroll över varje extern resurs som Aspose.Words försöker skriva ut.  
- Inuti callbacken **extract images from Word file** genom att kontrollera `args.ResourceType == ResourceType.Image`. Callbacken får bildens byte‑data, dess ursprungliga filändelse och en `SavePath`‑egenskap som vi sätter till en mapp vi skapar i farten. Genom att använda `Guid.NewGuid()` garanteras ett unikt filnamn, så du av misstag inte skriver över tidigare körningar.  
- Vi **skip CSS** (`ResourceType.CssStyleSheet`) eftersom ren Markdown inte behöver en stilmall. Detta håller utdata prydlig.  
- Till sist skriver `doc.Save(outputPath, mdOptions)` Markdown‑filen, och ersätter Word‑konstruktioner med motsvarande Markdown (rubriker blir `#`, tabeller blir rader separerade med pipe‑tecken, osv.).

## Spara bilder från docx – Anpassad mappstrategi

Varför bry sig om en anpassad mapp? Föreställ dig att du genererar dokumentation för en CI‑pipeline. Du vill att Markdown‑filen och dess resurser ska ligga sida‑vid‑sida i en ren, reproducerbar layout.

```csharp
string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
Directory.CreateDirectory(imageFolder);
```

Ett par **pro‑tips**:

- **Keep the folder path relative** till ditt projekts rot. På så sätt kan Markdown‑filen referera till bilder med en relativ länk (`![Alt text](Images/abc123.png)`), vilket fungerar på GitHub, GitLab eller någon statisk webbplatsgenerator.  
- **If you need deterministic names** (t.ex. att samma bild alltid ska få samma filnamn), ersätt GUID‑en med en hash av bildens byte‑data: `MD5.Create().ComputeHash(args.Data)`. Det är en liten justering men kan vara praktisk för cachning.

## Extrahera bilder från Word‑fil – Edge cases

1. **Multiple image formats** – Aspose.Words stödjer PNG, JPEG, GIF, BMP och till och med SVG. `args.Extension`‑egenskapen innehåller redan rätt filändelse, så du behöver inte gissa.  
2. **Very large images** – Om ditt källdokument innehåller högupplösta foton kan de genererade filerna bli stora. Överväg att lägga till ett komprimeringssteg efter callbacken, med `System.Drawing` eller `ImageSharp`.  
3. **Hidden images** – Word kan lagra bilder i sidhuvuden/sidfötter eller till och med i textrutor. Callbacken ser dem alla, så du extraherar **varje** bild, inte bara de synliga. Om du bara vill ha bilder i brödtexten, lägg till ett filter på `args.ImageIndex` eller inspektera `args.ImageType`.

## Export Word document as markdown – Verifiera resultatet

Efter att ha kört programmet, öppna `output.md` i någon Markdown‑visare. Du bör se något liknande:

```markdown
# My Report

Here is an introductory paragraph.

![Image1](Images/3f9c2d1e-7a5b-4c9e-9f6a-2b4e5d6f7a8b.png)

More text follows...
```

Lägg märke till hur bildlänken pekar på **Images**‑mappen vi skapade. Det är kännetecknet för en lyckad **export Word document as markdown**‑operation.

### Snabb kontroll

- Öppnas Markdown‑filen utan fel i VS Code‑förhandsgranskningen? ✅  
- Visas alla bilder när du tittar på filen på GitHub? ✅  
- Innehöll `Images`‑katalogen en fil per bild från den ursprungliga `.docx`? ✅  

Om någon av dessa kontroller misslyckas, dubbelkolla `ResourceSavingCallback`‑logiken och se till att platshållaren `YOUR_DIRECTORY` pekar på en skrivbar plats.

## Vanliga fallgropar och hur du undviker dem

| Fallgrop | Varför det händer | Lösning |
|----------|-------------------|--------|
| **Bilder visas inte** | Callbacken avfyras aldrig eftersom `ResourceSavingCallback` inte tilldelades. | Tilldela callbacken **innan** du anropar `doc.Save`. |
| **Tom bildmapp** | `args.Cancel = true` sattes av misstag för alla resurser. | Avbryt endast CSS (`ResourceType.CssStyleSheet`), låt bilder vara orörda. |
| **Filväg för lång på Windows** | Att använda djupt nästlade mappar plus GUID‑er kan överstiga 260 tecken. | Håll mappen grundläggande, eller aktivera stöd för långa sökvägar i Windows 10+. |
| **Dubbletta bildnamn** | Att använda `DateTime.Now.Ticks` istället för GUID kan leda till kollisioner i snabba loopar. | Håll dig till `Guid.NewGuid()` för unikhet. |

## Sammanfattning

Vi har just **converted docx to markdown**, **saved images from docx**, och demonstrerat hur man **extract images from Word file** samtidigt som vi **export Word document as markdown** på ett rent, repeterbart sätt. Hela processen bygger på Aspose.Words’ `ResourceSavingCallback`, som ger dig fin kontroll över varje extern resurs.

### Vad blir nästa?

- **Style the Markdown** – lägg till ett front‑matter‑block för Jekyll eller Hugo.  
- **Automate the pipeline** – bädda in denna kod i ett Azure DevOps‑ eller GitHub Action‑steg.  
- **Handle tables and footnotes** – utforska andra `MarkdownSaveOptions`‑flaggor som `ExportTableBorderStyles`.  

Känn dig fri att justera mappstrukturen, lägga till bildkomprimering, eller till och med byta utdataformat till HTML genom att byta `MarkdownSaveOptions` mot `HtmlSaveOptions`. Himlen är gränsen när du har en solid bas för **convert docx to markdown**.

Lycka till med kodandet, och må din dokumentation alltid vara både vacker **och** maskinläsbar!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Spara Word‑bilder – Konvertera Word till Markdown med Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Konvertera Word till Markdown – Bädda in bilder som Base64](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)
- [Hur man byter namn på bilder vid konvertering av DOCX till Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}