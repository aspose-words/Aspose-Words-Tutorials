---
category: general
date: 2025-12-19
description: markdown med latex‑ekvationer guide – lär dig hur du konverterar docx
  till markdown, exporterar ekvationer till latex och sparar bilder i en mapp med
  unika namn med Aspose.Words i C#.
draft: false
keywords:
- markdown with latex equations
- convert docx to markdown
- save images to folder
- export equations to latex
- generate unique image names
language: sv
og_description: Markdown med LaTeX‑ekvationer‑handledning visar hur man konverterar
  docx till markdown, exporterar ekvationer till LaTeX och genererar unika bildnamn
  för sparade bilder.
og_title: markdown med latex‑ekvationer – fullständig C#‑konverteringsguide
tags:
- Aspose.Words
- C#
- Markdown
- LaTeX
title: 'markdown med latex‑ekvationer: konvertera DOCX till Markdown och exportera
  bilder'
url: /sv/net/programming-with-markdownsaveoptions/markdown-with-latex-equations-convert-docx-to-markdown-and-e/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# markdown med latex‑ekvationer: Konvertera DOCX till Markdown och exportera bilder

Behövt du **markdown med latex‑ekvationer** men var osäker på hur du får dem ur en Word‑fil? Du är inte ensam – många utvecklare stöter på detta när de flyttar dokumentation från Office till statiska webbplatsgeneratorer.  

I den här handledningen går vi igenom en komplett, end‑to‑end‑lösning som **konverterar docx till markdown**, **exporterar ekvationer till latex** och **sparar bilder i en mapp** med logik för **generera unika bildnamn**, allt med Aspose.Words för .NET.  

När du är klar har du ett färdigt C#‑program som producerar rena Markdown‑filer, LaTeX‑klar matematik och en prydlig bildkatalog – utan manuellt copy‑pasta.

## Vad du behöver

- .NET 6 (eller någon nyare .NET‑runtime)  
- Aspose.Words för .NET 23.10 eller senare (NuGet‑paket `Aspose.Words`)  
- En exempel‑`input.docx` som innehåller vanlig text, Office Math‑objekt och några bilder  
- En IDE du föredrar (Visual Studio, Rider eller VS Code)  

Det är allt. Inga extra bibliotek, inga krångliga kommandoradsverktyg – bara ren C#.

## Steg 1: Ladda dokumentet säkert (återställningsläge)

När du hanterar filer som kan ha redigerats av många händer är korruption en verklig risk. Aspose.Words låter dig aktivera *RecoveryMode* så att laddaren försöker reparera trasiga delar istället för att kasta ett undantag.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // Load the document with recovery mode – this handles possible corruption.
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx", loadOptions);
```

**Varför detta är viktigt:**  
Om källfilen innehåller felaktiga XML‑noder eller en trasig bildström, kommer återställningsläget fortfarande ge dig ett användbart `Document`‑objekt. Att hoppa över detta steg kan leda till en hård krasch, särskilt i CI‑pipelines där du inte kontrollerar varje uppladdning.

> **Pro‑tips:** När du bearbetar batchar, omslut laddningen i ett `try/catch` och logga eventuella `DocumentCorruptedException` för senare granskning.

## Steg 2: Konvertera DOCX till Markdown med LaTeX‑ekvationer

Nu kommer hjärtat i handledningen: vi vill ha **markdown med latex‑ekvationer**. Aspose.Words `MarkdownSaveOptions` låter dig ange `OfficeMathExportMode.LaTeX`, vilket konverterar varje Office Math‑objekt till en LaTeX‑sträng omsluten av `$…$` eller `$$…$$`.

```csharp
        // Export Office Math equations to LaTeX while saving as Markdown.
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        doc.Save(@"YOUR_DIRECTORY/output_math.md", markdownMathOptions);
```

Den resulterande `output_math.md` kommer att se ut ungefär så här:

```markdown
Here is an inline equation $E = mc^2$ inside a sentence.

And a displayed equation:

$$
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
$$
```

**Varför du vill ha detta:**  
De flesta statiska webbplatsgeneratorer (Hugo, Jekyll, MkDocs) förstår redan LaTeX‑avgränsare när du aktiverar ett MathJax‑ eller KaTeX‑plugin. Genom att exportera direkt till LaTeX undviker du ett efterbearbetningssteg som annars skulle kräva regex‑hackar.

### Kantfall

- **Komplexa ekvationer:** Mycket djupa nästlade strukturer renderas fortfarande korrekt, men du kan behöva öka `MathRenderer`‑minnesgränsen om du får `OutOfMemoryException`.  
- **Blandat innehåll:** Om ett stycke blandar vanlig text och en ekvation, delar Aspose.Words automatiskt upp dem och bevarar den omgivande markdownen.

## Steg 3: Spara bilder i mapp med unika namn

Om ditt Word‑dokument innehåller bilder vill du förmodligen ha dem som separata bildfiler som markdownen kan referera till. `ResourceSavingCallback` på `MarkdownSaveOptions` ger dig full kontroll över hur varje bild skrivs.

```csharp
        // Customize image handling during Markdown export.
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (resource, stream) =>
            {
                // Generate a unique file name for each image.
                string imageFileName = $"img_{Guid.NewGuid()}.png";
                string imagePath = Path.Combine(@"YOUR_DIRECTORY/Images", imageFileName);

                // Ensure the Images folder exists.
                Directory.CreateDirectory(Path.GetDirectoryName(imagePath)!);

                // Save the image to the file system.
                using var imageFile = File.Create(imagePath);
                resource.Save(imageFile);
            }
        };
        doc.Save(@"YOUR_DIRECTORY/output_images.md", markdownImageOptions);
```

**Hur markdownen ser ut nu:**

```markdown
![Image description](Images/img_3f9c2a1e-7b5d-4c8f-9d6e-2b5c7a9e1f0a.png)
```

**Varför generera unika namn?**  
Om samma bild förekommer flera gånger skulle originalnamnet leda till överskrivningar. GUID‑baserade namn garanterar att varje fil är unik, vilket är särskilt praktiskt när du kör konverteringen i parallella jobb.

### Tips & Fallgropar

- **Prestanda:** Att skapa ett GUID för varje bild ger försumbar overhead, men om du bearbetar tusentals bilder kan du byta till en deterministisk hash (t.ex. SHA‑256 av bild‑bytena).  
- **Filformat:** `resource.Save` skriver bilden i sitt ursprungliga format. Om du behöver alla PNG‑filer, ersätt `resource.Save(imageFile);` med `resource.Save(imageFile, ImageSaveOptions.CreateSaveOptions(SaveFormat.Png));`.

## Steg 4: Exportera PDF med inline‑former (valfritt)

Ibland behöver du fortfarande en PDF‑version av samma dokument, kanske för juridisk granskning. Att sätta `ExportFloatingShapesAsInlineTag` behåller flytande objekt (som textrutor) i PDF‑filen som inline‑taggar, vilket bevarar layoutens noggrannhet.

```csharp
        // Save the document as PDF, exporting floating shapes as inline tags.
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save(@"YOUR_DIRECTORY/output_shapes.pdf", pdfOptions);
    }
}
```

Du kan hoppa över detta steg om PDF‑utmatning inte ingår i ditt arbetsflöde – inget går sönder om du utelämnar det.

## Fullt fungerande exempel (alla steg kombinerade)

Nedan är det kompletta programmet som du kan kopiera‑klistra in i en konsolapp. Glöm inte att ersätta `YOUR_DIRECTORY` med en faktisk absolut eller relativ sökväg.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // 1️⃣ Load with recovery mode.
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx", loadOptions);

        // 2️⃣ Export markdown with LaTeX equations.
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        doc.Save(@"YOUR_DIRECTORY/output_math.md", markdownMathOptions);

        // 3️⃣ Save images to a folder, using unique GUID names.
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (resource, stream) =>
            {
                string imageFileName = $"img_{Guid.NewGuid()}.png";
                string imagePath = Path.Combine(@"YOUR_DIRECTORY/Images", imageFileName);
                Directory.CreateDirectory(Path.GetDirectoryName(imagePath)!);
                using var imageFile = File.Create(imagePath);
                resource.Save(imageFile);
            }
        };
        doc.Save(@"YOUR_DIRECTORY/output_images.md", markdownImageOptions);

        // 4️⃣ (Optional) Export PDF with inline shape tags.
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save(@"YOUR_DIRECTORY/output_shapes.pdf", pdfOptions);
    }
}
```

När du kör programmet skapas tre filer:

| Fil | Syfte |
|------|---------|
| `output_math.md` | Markdown som innehåller LaTeX‑klara ekvationer |
| `output_images.md` | Markdown med bildlänkar som pekar på unikt namngivna PNG‑filer |
| `output_shapes.pdf` | PDF‑version som bevarar flytande former som inline‑taggar (valfritt) |

## Slutsats

Du har nu en **markdown med latex‑ekvationer**‑pipeline som **konverterar docx till markdown**, **exporterar ekvationer till latex** och **sparar bilder i mapp** samtidigt som den **genererar unika bildnamn** för varje bild. Metoden är helt självbärande, fungerar med alla moderna .NET‑projekt och kräver bara Aspose.Words‑NuGet‑paketet.

Vad blir nästa steg? Prova att mata in den genererade markdownen i en statisk webbplatsgenerator som Hugo, aktivera MathJax och se hur din dokumentation förvandlas från ett slutet Office‑format till en vacker, webb‑klar sida. Behöver du tabeller? Aspose.Words stödjer också `MarkdownSaveOptions.ExportTableAsHtml`, så du kan behålla komplexa layouter intakta.

If

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}