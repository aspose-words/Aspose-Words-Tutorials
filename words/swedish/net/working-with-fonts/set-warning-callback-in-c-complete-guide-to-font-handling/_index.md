---
category: general
date: 2026-02-10
description: Ställ in varningsåteruppringning för att övervaka teckensnittsändringar
  medan du konfigurerar standardteckensnitt och anger standardimportteckensnitt i
  Aspose.Words. Lär dig den fullständiga steg‑för‑steg‑lösningen.
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: sv
og_description: Ställ in varningscallback för att övervaka teckensnittsändringar när
  du konfigurerar standardteckensnitt och anger standardimportteckensnitt. Följ hela
  handledningen för Aspose.Words.
og_title: Ställ in varningsåteranrop i C# – Komplett guide
tags:
- Aspose.Words
- C#
- Document Import
title: Ställ in varningscallback i C# – Komplett guide till hantering av teckensnitt
url: /sv/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ställ in varningsåteranrop i C# – Komplett guide till teckenhantering

Har du någonsin behövt **set warning callback** när du laddar ett Word‑dokument och undrat hur du *configure default font* samtidigt? Du är inte ensam. I många verkliga projekt—som automatiserade rapportgeneratorer eller dokumentkonverteringspipeline—kan saknade teckensnitt tyst förstöra layouten, och det enda sättet att fånga dessa problem är att **monitor font changes** via ett varningsåteranrop.

I den här handledningen går vi igenom ett praktiskt exempel som visar hur du **set warning callback**, **configure default font** och till och med **set default import font** med Aspose.Words för .NET. I slutet har du ett färdigt kodexempel, förstår varför varje del är viktig och vet hur du anpassar det för kantfall som anpassade teckensnittsmappar eller tysta ersättningar.

---

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar även på .NET Framework 4.6+)  
- Aspose.Words for .NET NuGet‑paket (`Install-Package Aspose.Words`)  
- En mapp som innehåller fallback‑teckensnittet du vill använda (t.ex. `fonts/Arial.ttf`)  
- Grundläggande kunskap om C#‑konsolappar  

Inga ytterligare bibliotek krävs.

---

## Steg 1: Skapa LoadOptions och **configure default font**

Det första du gör när du vill kontrollera teckenhantering är att skapa en `LoadOptions`‑instans. Detta objekt talar om för Aspose.Words hur saknade teckensnitt ska hanteras vid import.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**Varför detta är viktigt:**  
Om källdokumentet refererar till ett teckensnitt som inte är installerat på servern, kommer Aspose.Words att titta i den mapp du angav. Detta är kärnan i **set default import font**—du talar explicit till biblioteket var en ersättning kan hittas innan några varningar ens har genererats.

---

## Steg 2: **Set warning callback** för att **monitor font changes**

Aspose.Words avger en `WarningInfoCollection` när den måste ersätta ett teckensnitt, bland annat. Genom att fästa en hanterare kan du logga eller reagera på varje ersättning.

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**Varför detta är viktigt:**  
Att bara **configure default font** räcker inte om du behöver granska vilka teckensnitt som faktiskt byttes. Återanropet ger dig en realtidslogg, uppfyller kravet **monitor font changes** och hjälper dig att fånga oväntade ersättningar tidigt i en CI‑pipeline.

---

## Steg 3: Ladda dokumentet med de förberedda alternativen

Nu när laddningsalternativen är helt förberedda kan du säkert ladda vilken `.docx`‑fil som helst. Återanropet triggas automatiskt om en ersättning sker.

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**Vad du kommer att se:**  
Om källan använder ett teckensnitt som inte finns, kommer konsolen att skriva ut något liknande:

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

Den utskriften bekräftar att du framgångsrikt har **set warning callback** och att **default import font** trätt i kraft.

---

## Steg 4: (Valfritt) Finjustera teckensnittsersättningsbeteende

Ibland kan du vilja ersätta *alla* saknade teckensnitt med en enda familj, oavsett den ursprungliga begäran. Aspose.Words låter dig ange ett *fallback‑teckensnitt* globalt.

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**När du ska använda detta:**  
Om du genererar PDF‑filer för ett varumärke som bara tillåter ett begränsat urval av teckensnitt, säkerställer detta konsistens i alla dokument, även om källan försöker använda något exotiskt.

---

## Steg 5: Spara eller vidarebehandla dokumentet

Efter laddning kan du fortsätta med vilken bearbetning du behöver—redigering, konvertering till PDF, extrahering av text osv. Här är ett snabbt exempel på att spara dokumentet som en PDF samtidigt som de ersatta teckensnitten bevaras.

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

Den resulterande PDF‑filen kommer att visa fallback‑teckensnittet där en ersättning skedde, vilket ger dig en visuell bekräftelse på att **set warning callback** fungerade som förväntat.

---

## Vanliga fallgropar & pro‑tips

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| **Callback never fires** | `LoadOptions.WarningCallback` var inte tilldelad *före* att dokumentet laddades. | Se till att alltid fästa återanropet **före** anropet `new Document(...)`. |
| **Wrong font folder** | Felaktig sökväg eller saknade läsrättigheter. | Verifiera att mappen finns och att appen har `Read`‑behörighet. Använd absoluta sökvägar för pålitlighet. |
| **Multiple substitutions, noisy output** | Stora dokument med många saknade teckensnitt. | Filtrera varningar efter `WarningType.FontSubstitution` (som visat) eller skriv dem till en loggfil istället för konsolen. |
| **Fallback font not applied** | Fallback‑teckensnittet är inte installerat på maskinen. | Placera `.ttf`/`.otf`‑filen i den mapp du skickade till `SetFontsFolder`. Aspose.Words laddar den direkt, ingen OS‑installation behövs. |

**Pro‑tips:** När du kör detta i en CI/CD‑pipeline, omdirigera konsolutdata till ett byggartefakt. På så sätt har du en revisionsspårning av varje teckensnittsersättning som skedde under bygget.

---

## Fullt fungerande exempel (klar att kopiera och klistra in)

Nedan är det kompletta programmet som du kan klistra in i ett nytt Console‑App‑projekt. Det innehåller alla steg, using‑satser och kommentarer du behöver.

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**Förväntad konsolutdata** (förutsatt att `Times New Roman` saknades):

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

Kör programmet, öppna `output.pdf`, och du kommer att se dokumentet renderat med fallback‑teckensnittet där det behövs.

---

## Slutsats

Du har nu ett robust, produktionsklart mönster för hur du **set warning callback** i C#, **configure default font**, **monitor font changes** och **set default import font** när du arbetar med Aspose.Words. Genom att fästa en varningssamling innan laddning, peka `FontSettings` på en pålitlig teckensnittsmapp och eventuellt tvinga en global fallback, får du full insyn och kontroll över teckensnittsersättningar—precis vad någon robust dokument‑bearbetningspipeline behöver.

Redo för nästa nivå? Prova att kombinera detta tillvägagångssätt med:

- **Dynamisk teckensnittsladdning** från en databas (använd `FontSettings.SetFontsFolder` vid körning).  
- **Anpassade varningshanterare** som skriver till en strukturerad logg (JSON eller CSV) för analys.  
- **Parallell dokumentbearbetning** där varje tråd får sina egna `LoadOptions` för att undvika korsprat.

Känn dig fri att experimentera, anpassa koden till din egen arkitektur och dela eventuella upptäckter i kommentarerna. Lycka till med kodandet!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}