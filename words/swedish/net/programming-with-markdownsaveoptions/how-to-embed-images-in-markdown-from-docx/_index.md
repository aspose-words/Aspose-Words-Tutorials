---
category: general
date: 2026-02-10
description: Lär dig hur du bäddar in bilder när du konverterar DOCX till Markdown,
  samt tips för ekvationer och högupplöst utdata.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- export word to markdown
- how to convert equations
- save word as markdown
language: sv
og_description: Hur man bäddar in bilder vid konvertering av en DOCX‑fil till Markdown,
  med högupplösta bilder och LaTeX‑ekvationsexport.
og_title: Hur man bäddar in bilder i Markdown från DOCX – Fullständig guide
tags:
- Aspose.Words
- C#
- Document conversion
title: Hur man bäddar in bilder i Markdown från DOCX
url: /sv/net/programming-with-markdownsaveoptions/how-to-embed-images-in-markdown-from-docx/
---

.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man bäddar in bilder i Markdown från DOCX

Har du någonsin undrat **hur man bäddar in bilder** när du omvandlar en Word‑fil till ett rent Markdown‑dokument? Du är inte ensam—utvecklare stöter ständigt på problem när bilder försvinner eller blir suddiga efter konvertering. Den goda nyheten? Med några rader C# kan du behålla varje bild skarp, exportera matematik som LaTeX och få en färdig‑att‑publicera `.md`‑fil.

I den här handledningen kommer vi också att beröra **convert docx to markdown**, **export word to markdown**, och till och med den knepigare **how to convert equations** så att du kan **save word as markdown** utan att kompromissa med kvaliteten. I slutet har du ett självständigt, körbart exempel som du kan klistra in direkt i ditt projekt.

---

## Vad du behöver

- **Aspose.Words for .NET** (v23.9 eller nyare). Det är ett kommersiellt bibliotek, men du kan hämta en gratis 30‑dagars provversion från Aspose‑webbplatsen.  
- En .NET‑utvecklingsmiljö (Visual Studio, Rider eller VS Code med C#‑tillägget).  
- Ett inmatnings‑Word‑dokument (`input.docx`) som innehåller minst en bild och ett par ekvationer.  

Det är allt—inga extra NuGet‑paket, inga externa konverterare. Biblioteket sköter allt tungt arbete.

---

## Steg‑för‑steg konvertering

Nedan delar vi upp processen i små steg. Varje rubrik innehåller ett nyckelord för att hålla både sökmotorer och AI‑assistenter nöjda.

### ## Hur man bäddar in bilder under DOCX till Markdown‑konvertering

Det första du måste göra är att tala om för Aspose.Words var källfilen finns.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Step 1: Load the source document
Document doc = new Document(@"C:\Docs\input.docx");
```

*Varför detta är viktigt*: Att ladda dokumentet skapar en minnesrepresentation av varje stycke, bild och ekvation. Om du hoppar över detta steg finns det inget att konvertera, och därmed inga bilder att bädda in.

> **Proffstips**: Använd en absolut sökväg under testning, byt sedan till en relativ (t.ex. `Path.Combine(AppDomain.CurrentDomain.BaseDirectory, "input.docx")`) för produktion.

### ## Konvertera docx till markdown med högupplösta bilder

Nu konfigurerar vi `MarkdownSaveOptions`. Här styr du bild‑DPI och matematik‑exportläge.

```csharp
// Step 2: Configure Markdown save options
MarkdownSaveOptions mdSave = new MarkdownSaveOptions
{
    // 300 DPI gives you print‑ready quality while still keeping file size reasonable
    ImageResolution = 300,

    // Export equations as LaTeX so they render nicely on GitHub, GitLab, or static site generators
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Uncomment the line below if you prefer Base64‑embedded images (makes the .md file self‑contained)
    // ExportImagesAsBase64 = true,
};
```

*Varför detta är viktigt*: `ImageResolution` bestämmer hur rasteriserade bilder sparas. Standardvärdet (96 DPI) ser ofta suddigt ut på Retina‑skärmar. Att sätta det till **300 DPI** bevarar detaljer utan att filstorleken blir för stor. `OfficeMathExportMode.LaTeX` säkerställer att varje Word‑ekvation omvandlas till ren LaTeX‑kod, vilket de flesta Markdown‑renderare förstår.

### ## Exportera word till markdown och verifiera resultatet

Till sist skriver vi Markdown‑filen till disk.

```csharp
// Step 3: Save the document as Markdown
string outputPath = @"C:\Docs\HighRes.md";
doc.Save(outputPath, mdSave);
Console.WriteLine($"✅ Document saved to {outputPath}");
```

*Varför detta är viktigt*: Metoden `Save` tillämpar alla alternativ vi satte tidigare. Efter detta anrop hittar du en `.md`‑fil där varje bild‑tagg ser ut så här:

```markdown
![Image 1](HighRes.md_files/Image_0.png)
```

Om du aktiverade `ExportImagesAsBase64` skulle taggen istället innehålla en lång `data:image/png;base64,…`‑sträng, vilket gör Markdown‑filen portabel.

---

## Hur man konverterar ekvationer utan att förlora kvalitet

Ekvationer är ofta den svåraste delen av ett Word‑till‑Markdown‑flöde. Aspose.Words erbjuder två exportlägen:

| Mode | Result | When to use |
|------|--------|-------------|
| **LaTeX** (`OfficeMathExportMode.LaTeX`) | Ren LaTeX‑syntax (`\frac{a}{b}`) | Du renderar Markdown på plattformar som stödjer MathJax eller KaTeX. |
| **Image** (`OfficeMathExportMode.Image`) | PNG‑bild inbäddad som vilken annan bild som helst | Målrendreraren har ingen matematikstöd (t.ex. enkel GitHub‑README). |

Om du behöver **båda**—LaTeX för moderna visare *och* en reservbild för äldre verktyg—kan du köra konverteringen två gånger, varje gång med ett annat `OfficeMathExportMode`, och sedan slå ihop resultaten manuellt. Det är lite extra arbete, men det garanterar maximal kompatibilitet.

---

## Spara word som markdown – hantera kantfall

### Stora bilder

När en bild överstiger 5 MB kan standard‑`ImageResolution` fortfarande producera en enorm PNG. För att hålla filstorleken i schack kan du ner‑skala selektivt:

```csharp
if (new FileInfo(@"C:\Docs\input.docx").Length > 10_000_000) // >10 MB DOCX
{
    mdSave.ImageResolution = 150; // half the DPI for huge docs
}
```

### Saknade teckensnitt

Om ditt Word‑dokument använder ett anpassat teckensnitt som inte är installerat på servern kan den rasteriserade bilden se felaktig ut. Den säkraste lösningen är att **bädda in teckensnittet** i DOCX innan konvertering (File → Options → Save → Embed fonts) eller att förinstallera teckensnittet på maskinen som kör koden.

### Base64 vs. externa filer

Att bädda in bilder som Base64 gör Markdown‑filen till ett enda, delbart artefakt—perfekt för e‑post eller snabba demo‑exempel. Dock kan filstorleken skjuta i höjden (en 200 KB PNG blir ~270 KB i Base64). Om du planerar att checka in Markdown i ett Git‑arkiv, håll dig till externa bildfiler för renare diffar.

---

## Fullt, körbart exempel

Nedan är det kompletta programmet som du kan kopiera‑klistra in i en konsolapp. Det inkluderar alla de valfria kontrollerna som diskuterats ovan.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // ---- Configuration -------------------------------------------------
        string inputPath  = @"C:\Docs\input.docx";
        string outputPath = @"C:\Docs\HighRes.md";

        // Verify the source file exists
        if (!File.Exists(inputPath))
        {
            Console.Error.WriteLine($"❌ Input file not found: {inputPath}");
            return;
        }

        // Load the Word document
        Document doc = new Document(inputPath);

        // Set up save options
        MarkdownSaveOptions mdSave = new MarkdownSaveOptions
        {
            ImageResolution = 300,
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            // ExportImagesAsBase64 = true, // uncomment for a single‑file .md
        };

        // Adjust DPI for very large source files
        if (new FileInfo(inputPath).Length > 10_000_000) // >10 MB
        {
            mdSave.ImageResolution = 150;
            Console.WriteLine("🔧 Large DOCX detected – reducing image DPI to 150.");
        }

        // Perform the conversion
        doc.Save(outputPath, mdSave);
        Console.WriteLine($"✅ Markdown saved to: {outputPath}");

        // Quick verification: list generated images
        string imageFolder = Path.Combine(Path.GetDirectoryName(outputPath) ?? "", Path.GetFileNameWithoutExtension(outputPath) + "_files");
        if (Directory.Exists(imageFolder))
        {
            Console.WriteLine("🖼️ Images generated:");
            foreach (var img in Directory.GetFiles(imageFolder))
                Console.WriteLine($"   - {Path.GetFileName(img)}");
        }
    }
}
```

**Förväntat resultat**: Efter att ha kört programmet ser du `HighRes.md` tillsammans med en mapp `HighRes_files` som innehåller varje bild som en PNG‑fil (eller en enda Base64‑kodad sträng om du togglade det alternativet). Alla ekvationer visas som LaTeX‑block som:

```markdown
$$
\int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
$$
```

Öppna `.md`‑filen i VS Code, GitHub‑förhandsgranskning eller någon Markdown‑visare som stödjer MathJax så ser du en trogen kopia av det ursprungliga Word‑dokumentet.

---

## Slutsats

Vi har just gått igenom **hur man bäddar in bilder** när du **konverterar docx till markdown**, och täckt allt från DPI‑inställningar till LaTeX‑ekvationsexport. Det korta programmet ovan låter dig **exportera word till markdown** i ett enda steg, samtidigt som du får full kontroll över bildkvalitet och ekvationsformat.  

Om du är redo att gå vidare, överväg:

- **Spara Word som Markdown** med anpassad CSS för styling.  
- Automatisera processen för batch‑filer med `Directory.GetFiles`.  
- Lägg till ett CLI‑argument för att växla Base64‑inbäddning i farten.  

Prova det, justera alternativen, och låt dina Markdown‑dokument se lika polerade ut som de ursprungliga Word‑filerna. Har du frågor eller ett udda kantfall? Lämna en kommentar—lycklig kodning!  

![how to embed images example](placeholder-image.png)   <!-- alt text includes primary keyword -->

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}