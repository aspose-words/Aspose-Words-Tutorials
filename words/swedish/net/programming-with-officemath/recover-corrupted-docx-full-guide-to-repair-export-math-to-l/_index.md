---
category: general
date: 2025-12-23
description: Lär dig hur du återställer korrupta docx‑filer, använder återställningsläge,
  exporterar ekvationer till LaTeX och genererar unika bildnamn i C#. Steg‑för‑steg‑kod
  med förklaringar.
draft: false
keywords:
- recover corrupted docx
- how to use recovery mode
- export equations to latex
- generate unique image names
language: sv
og_description: Återställ korrupta docx-filer, använd återställningsläge, exportera
  ekvationer till LaTeX och generera unika bildnamn med Aspose.Words i C#.
og_title: återställ korrupt docx – Komplett C#‑handledning
tags:
- Aspose.Words
- C#
- Document Recovery
title: återställ korrupt docx – Fullständig guide för reparation, exportera matematik
  till LaTeX och generera unika bildnamn
url: /sv/net/programming-with-officemath/recover-corrupted-docx-full-guide-to-repair-export-math-to-l/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# återställ korrupt docx – Fullständig guide för reparation, export av matematik till LaTeX & generering av unika bildnamn

Har du någonsin öppnat en **.docx** som vägrar att laddas eftersom den är korrupt? Du är inte ensam. I många verkliga projekt kan en trasig Word‑fil stoppa ett helt arbetsflöde, men den goda nyheten är att du kan **återställa korrupta docx**‑filer programmässigt.  

I den här handledningen går vi igenom de exakta stegen för att **återställa korrupta docx**, visar **hur du använder återställningsläge**, demonstrerar **export av ekvationer till LaTeX**, och slutligen **genererar unika bildnamn** när du sparar till Markdown. När du är klar har du ett enda, körbart C#‑program som hanterar alla dessa uppgifter utan problem.

## Förutsättningar

- .NET 6 eller senare (koden fungerar också med .NET Framework 4.6+).  
- Aspose.Words for .NET (gratis provversion eller licensierad version). Installera via NuGet:

```bash
dotnet add package Aspose.Words
```

- Grundläggande kunskap om C# och fil‑I/O.  
- En korrupt `corrupt.docx`‑fil att testa mot (du kan simulera korruption genom att trunkera en giltig fil).

> **Proffstips:** Behåll en backup av originalfilen innan du börjar – återställning är destruktiv endast om du skriver över källan.

## Steg 1 – Återställ den korrupta DOCX‑filen med återställningsläge

Det första vi måste göra är att tala om för Aspose.Words att behandla den inkommande filen som potentiellt skadad. Här kommer **hur du använder återställningsläge** in.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load a possibly corrupted document using recovery mode
        // -----------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded successfully – recovery mode applied.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
            return;
        }

        // ---------------------------------------------------------------
        // Subsequent steps go here...
        // ---------------------------------------------------------------
    }
}
```

**Varför detta är viktigt:**  
När `RecoveryMode.Recover` är aktiverat försöker Aspose.Words bygga om det interna dokumentträdet, hoppar över oläsliga delar samtidigt som så mycket innehåll som möjligt bevaras. Utan detta skulle `Document`‑konstruktorn kasta ett undantag och du skulle förlora alla chanser att rädda filen.

> **Vad händer om filen är bortom reparation?**  
> Biblioteket kommer fortfarande att returnera ett `Document`‑objekt, men vissa noder kan saknas. Du kan inspektera `doc.GetChildNodes(NodeType.Any, true).Count` för att se hur många som överlevde.

## Steg 2 – Exportera Office Math‑ekvationer till LaTeX när du sparar som Markdown

Många tekniska dokument innehåller ekvationer skrivna med Office Math. Om du behöver dessa ekvationer i LaTeX – till exempel för att publicera på en vetenskaplig blogg – kan du låta Aspose.Words utföra konverteringen åt dig.

```csharp
        // -----------------------------------------------------------------
        // Step 2: Export Office Math equations to LaTeX in a Markdown file
        // -----------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        string markdownPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(markdownPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown with LaTeX equations saved to: {markdownPath}");
```

**Hur det fungerar:**  
`OfficeMathExportMode.LaTeX` talar om för spararen att ersätta varje `OfficeMath`‑nod med dess LaTeX‑representation omsluten av `$…$` (inline) eller `$$…$$` (display). Den resulterande Markdown‑filen kan matas direkt till statiska webbplatsgeneratorer som Hugo eller Jekyll.

> **Edge case:** Om originaldokumentet innehåller komplexa ekvationsobjekt (t.ex. matriser) kan LaTeX‑konverteringen generera flerradig output. Granska den genererade `.md`‑filen för att säkerställa att den uppfyller dina formateringsförväntningar.

## Steg 3 – Spara dokumentet som PDF samtidigt som du styr taggning av flytande former

Ibland behöver du en PDF‑version av samma dokument, men du bryr dig också om hur flytande former (bilder, textrutor) taggas för tillgänglighet. Flaggan `ExportFloatingShapesAsInlineTag` ger dig den kontrollen.

```csharp
        // -----------------------------------------------------------------
        // Step 3: Save as PDF with custom floating‑shape tagging
        // -----------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true // true → <Figure>, false → <Div>
        };

        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved with inline tags to: {pdfPath}");
```

**Varför växla denna flagga?**  
- `true` → Flytande former blir `<Figure>`‑taggar, vilket många skärmläsare behandlar som separata bilder med bildtexter.  
- `false` → Former omsluts av generiska `<Div>`‑taggar, som kan ignoreras av hjälpmedelstekniker. Välj baserat på dina tillgänglighetskrav.

## Steg 4 – Exportera till Markdown med anpassad bildhantering (generera unika bildnamn)

När du sparar ett Word‑dokument till Markdown skrivs alla inbäddade bilder till disk. Som standard får de originalfilnamnet, vilket kan leda till kollisioner om du bearbetar många dokument i samma mapp. Låt oss haka in i sparprocessen och **automatiskt generera unika bildnamn**.

```csharp
        // -----------------------------------------------------------------
        // Step 4: Export to Markdown with custom image naming
        // -----------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                // Create a sub‑folder for markdown images if it doesn't exist
                string imageFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imageFolder);

                // Build a GUID‑based filename preserving the original extension
                string uniqueName = Guid.NewGuid().ToString() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imageFolder, uniqueName);
            }
        };

        string markdownPath2 = @"YOUR_DIRECTORY\out2.md";
        doc.Save(markdownPath2, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with uniquely named images saved to: {markdownPath2}");
```

**Vad händer under huven?**  
`ResourceSavingCallback` anropas för varje extern resurs (bilder, SVG‑filer osv.) under sparandet. Genom att returnera en fullständig sökväg bestämmer du var filen hamnar och vad den heter. GUID‑en säkerställer **generera unika bildnamn** utan någon manuell bokföring.

> **Tips:** Om du behöver ett deterministiskt namnschema (t.ex. baserat på bildens alt‑text) kan du ersätta `Guid.NewGuid()` med en hash av `resourceInfo.Name`.

## Fullt fungerande exempel

När allt sätts ihop får du hela programmet som du kan kopiera‑klistra in i en konsolapp:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -------------------------------------------------------------
        // Load the possibly corrupted document (Recovery Mode)
        // -------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded with recovery mode.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Unable to load document: {ex.Message}");
            return;
        }

        // -------------------------------------------------------------
        // Export equations to LaTeX in Markdown
        // -------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        string mdMathPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(mdMathPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown (LaTeX) saved: {mdMathPath}");

        // -------------------------------------------------------------
        // Save as PDF with inline floating‑shape tags
        // -------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved: {pdfPath}");

        // -------------------------------------------------------------
        // Export Markdown with unique image names
        // -------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                string imgFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imgFolder);
                string uniqueFile = Guid.NewGuid() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imgFolder, uniqueFile);
            }
        };
        string mdImgPath = @"YOUR_DIRECTORY\out2.md";
        doc.Save(mdImgPath, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with unique images saved: {mdImgPath}");
    }
}
```

### Förväntad output

Att köra programmet bör ge konsolmeddelanden liknande:

```
✅ Document loaded with recovery mode.
✅ Markdown (LaTeX) saved: YOUR_DIRECTORY\out.md
✅ PDF saved: YOUR_DIRECTORY\out.pdf
✅ Markdown with unique images saved: YOUR_DIRECTORY\out2.md
```

Du får tre filer:

| Fil | Syfte |
|------|---------|
| `out.md` | Markdown där varje Office Math‑ekvation visas som LaTeX (`$…$` eller `$$…$$`). |
| `out.pdf` | PDF‑version med flytande former taggade som `<Figure>` för bättre tillgänglighet. |
| `out2.md` + `md_images\*` | Markdown plus en mapp med unikt namngivna bildfiler (GUID‑baserade). |

## Vanliga frågor & edge cases

| Fråga | Svar |
|----------|--------|
| **Vad händer om den korrupta filen saknar återställbart innehåll?** | Aspose.Words kommer fortfarande att returnera ett `Document`‑objekt, men det kan vara tomt. Kontrollera `doc.GetChildNodes(NodeType.Paragraph, true).Count` innan du fortsätter. |
| **Kan jag ändra LaTeX‑avgränsaren?** | Ja – sätt `markdownMathOptions.MathDelimiter = "$$"` för att tvinga display‑stil avgränsare. |
| **Behöver jag disponera `Document`‑objektet?** | Klassen `Document` implementerar `IDisposable`. Wrappa den i ett `using`‑block om du bearbetar många filer för att frigöra inhemska resurser snabbt. |
| **Hur behåller jag de ursprungliga bildfilnamnen?** | Returnera `Path.Combine(imageFolder, resourceInfo.Name)` i callback‑metoden. Kom bara ihåg risken för namnkonflikter. |
| **Är GUID‑metoden säker för versionskontrollerade repos?** | GUID‑er är stabila över körningar, men de är inte mänskligt läsbara. Om du behöver reproducerbara namn, hash originalnamnet plus ett projekt‑brett salt. |

## Slutsats

Vi har visat dig hur du **återställer korrupta docx**‑filer, demonstrerat **hur du använder

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}