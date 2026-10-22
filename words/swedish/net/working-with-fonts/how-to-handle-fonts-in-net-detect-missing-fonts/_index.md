---
category: general
date: 2026-06-02
description: hur man hanterar typsnitt i .NET – upptäck saknade typsnitt och spåra
  typsnittsändringar med LoadOptions och FontSettings. Lär dig en komplett, körbar
  lösning.
draft: false
keywords:
- how to handle fonts
- detect missing fonts
- track font changes
language: sv
og_description: hur man hanterar typsnitt i .NET – upptäck saknade typsnitt och spåra
  typsnittsändringar. Följ den här steg‑för‑steg‑guiden för en komplett, färdig‑att‑köra‑lösning.
og_title: hur man hanterar typsnitt i .NET – upptäck saknade typsnitt
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: how to handle fonts in .NET – detect missing fonts and track font changes
    using LoadOptions and FontSettings. Learn a complete, runnable solution.
  headline: how to handle fonts in .NET – detect missing fonts
  type: TechArticle
tags:
- .NET
- Aspose.Words
- FontSettings
title: så här hanterar du teckensnitt i .NET – upptäck saknade teckensnitt
url: /sv/net/working-with-fonts/how-to-handle-fonts-in-net-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hur man hanterar typsnitt i .NET – upptäcka saknade typsnitt

Har du någonsin funderat **hur man hanterar typsnitt** när ett Word‑dokument refererar till ett teckensnitt som inte är installerat på maskinen? Du är inte ensam. Saknade typsnitt kan förvandla en polerad rapport till ett rörigt kaos, och utan rätt varningar kanske du aldrig får reda på vad som byttes ut.  

I den här handledningen visar vi dig exakt **hur man hanterar typsnitt** genom att upptäcka saknade typsnitt **och** spåra typsnittsändringar i realtid. I slutet har du en självständig konsolapp som loggar varje ersättning, så du aldrig blir förvånad över en mystisk Helvetica som dyker upp där Times New Roman borde vara.

> **Vad du får:** ett komplett, kopiera‑och‑klistra‑klart kodexempel, en förklaring av varje rad, tips för verkliga projekt och en snabb titt på edge‑cases du kan stöta på.

## Förutsättningar

- .NET 6.0 eller senare (exemplet använder en top‑level `Program.cs` för korthet)  
- Aspose.Words for .NET 23.9 eller nyare – du kan hämta det från NuGet med `dotnet add package Aspose.Words`  
- Ett Word‑dokument som medvetet refererar till ett typsnitt du inte har (t.ex. `MissingFont.docx`)  

Inga andra bibliotek krävs.

![Diagram showing how the LoadOptions flow into FontSettings and the substitution warning event – how to handle fonts in .NET example](https://example.com/images/font‑handling‑flow.png "how to handle fonts in .NET example")

## Steg 1: Ställ in LoadOptions med FontSettings  

Det första vi behöver är ett `LoadOptions`‑objekt som talar om för Aspose.Words att hålla utkik efter typsnittproblem.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

// Create LoadOptions and attach a fresh FontSettings instance.
var loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

**Varför detta är viktigt:** `LoadOptions` är grindvakten när ett dokument läses från disk. Genom att tillhandahålla en anpassad `FontSettings` får vi en krok in i den interna typsnittslösningsmotorn, vilket är det enda sättet att **upptäcka saknade typsnitt** innan dokumentet renderas.

## Steg 2: Prenumerera på SubstitutionWarning‑händelsen  

Aspose.Words utlöser en `SubstitutionWarning`‑händelse varje gång den inte kan hitta exakt det typsnitt du begärde. Vi kommer att logga detaljerna så att du kan se vilka typsnitt som begärdes och vilka som faktiskt användes.

```csharp
// Hook into the warning event – this is where we “track font changes”.
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.RequestedFontName – the name the document asked for.
    // e.SubstitutedFontName – the name Aspose.Words fell back to.
    // e.WarningType – tells you why the substitution happened.
    Console.WriteLine(
        $"[Font Substitution] Requested: {e.RequestedFontName}, " +
        $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
};
```

**Varför vi lyssnar:** Utan denna lyssnare skulle du aldrig få veta att en ersättning skedde. Händelsen ger dig en fullständig revisionsspårning, vilket uppfyller kravet att “spåra typsnittsändringar”.

## Steg 3: Läs in dokumentet med våra konfigurerade alternativ  

Nu läser vi faktiskt filen. Eftersom vi har skickat med `loadOptions` kommer Aspose.Words att utlösa varningshändelsen för varje saknat typsnitt den stöter på.

```csharp
// Replace the path with the location of your test document.
string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

Document doc = new Document(docPath, loadOptions);
```

Det är allt – dokumentet är nu inläst, och eventuella typsnittsproblem har redan skrivits ut till konsolen.

## Steg 4: (Valfritt) Verifiera de ersatta typsnitten i dokumentet  

Om du vill dubbelkolla vilka typsnitt som hamnade i den slutgiltiga PDF‑ eller DOCX‑filen, kan du gå igenom dokumentets typsnittssamling:

```csharp
Console.WriteLine("\n--- Fonts actually used in the document ---");
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
}
```

Att köra detta efter inläsningen listar varje typsnitt som motorn bestämde sig för att bädda in eller referera. Praktiskt när du behöver generera en rapport för QA‑team.

## Fullt fungerande exempel  

Kopiera blocket nedan till ett nytt konsolprojekt (`dotnet new console`) och kör det. Programmet kommer att skriva ut varje ersättning och sedan lista de typsnitt som överlevde inläsningen.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions with FontSettings.
        // -------------------------------------------------
        var loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Step 2: Hook the substitution warning event.
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"[Font Substitution] Requested: {e.RequestedFontName}, " +
                $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
        };

        // -------------------------------------------------
        // Step 3: Load the document (this triggers warnings).
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // Step 4 (optional): List fonts actually used.
        // -------------------------------------------------
        Console.WriteLine("\n--- Fonts actually used in the document ---");
        foreach (FontInfo fontInfo in doc.FontInfos)
        {
            Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
        }

        Console.WriteLine("\nDone. Press any key to exit.");
        Console.ReadKey();
    }
}
```

### Förväntad utskrift  

Om `MissingFont.docx` begär *“Comic Sans MS”* (som inte är installerat) kommer du att se något liknande:

```
[Font Substitution] Requested: Comic Sans MS, Used: Arial, Reason: FontNotFound
[Font Substitution] Requested: Times New Roman, Used: Times New Roman, Reason: None

--- Fonts actually used in the document ---
Arial – Regular
Times New Roman – Regular
```

Den första raden bevisar att vi **upptäcker saknade typsnitt** och **spårar typsnittsändringar**. Den andra raden visar en ersättning som inte behövde ske (ingen varning, eftersom typsnittet fanns).

## Vanliga fallgropar & pro‑tips  

| Fallgropar | Vad händer | Hur man fixar / undviker |
|------------|------------|--------------------------|
| **Inga varningshändelser utlöses** | Du kan tro att API:et är trasigt. | Se till att *tilldela* `FontSettings` till `LoadOptions` **innan** du läser in dokumentet. Händelsekroken måste fästas **innan** anropet `new Document(...)`. |
| **Ersatta typsnitt ser fortfarande felaktiga ut** | Aspose.Words faller tillbaka på ett generiskt typsnitt som inte matchar stilen. | Ange en anpassad typsnittsmapp via `fontSettings.SetFontsFolder(@"C:\MyFonts", true)`. Detta ger motorn fler alternativ innan den faller tillbaka på ett generiskt typsnitt. |
| **Prestandapåverkan på stora dokument** | Genomsökning av varje typsnitt kan lägga till några millisekunder. | Cacha `FontSettings`‑objektet om du laddar många dokument i följd. Återanvändning av samma instans undviker att läsa om systemets typsnittstabeller. |
| **Konsolutdata försvinner i GUI‑appar** | Du ser inte varningarna. | Omdirigera händelsen till en logger (t.ex. `Serilog`) eller skriv till en fil: `File.AppendAllText("font-warnings.log", …)`. |

## Utöka lösningen  

- **Exportera till PDF med inbäddade typsnitt** – efter inläsning, anropa `doc.Save("output.pdf", SaveOptions.CreateSaveOptions(SaveFormat.Pdf));` och se till att sätta `PdfSaveOptions.FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll;`.  
- **Batch‑behandling** – omslut inläsningslogiken i en `foreach` över en mapp med DOCX‑filer. Logga varje fils varningar till en CSV för revisionsändamål.  
- **Användarvänligt UI** – exponera samma logik bakom en knapp i en WinForms/WPF‑app, och visa varningarna i en `ListBox`.

## Slutsats  

Vi har gått igenom **hur man hanterar typsnitt** i .NET genom att konfigurera `LoadOptions`, prenumerera på `SubstitutionWarning`‑händelsen och slutligen läsa in dokumentet. Exemplet **upptäcker saknade typsnitt** men också **spårar typsnittsändringar** så att du kan granska varje ersättning.  

Prova det med dina egna dokument, justera sökvägen till typsnittsmappen, så blir du aldrig överraskad av ett oväntat typsnittsswap igen. Om du fann den här guiden användbar, överväg att utforska relaterade ämnen som *“bädda in anpassade typsnitt i PDF med Aspose.Words”* eller *“skapa en typsnittsfallback‑strategi för cross‑platform .NET‑appar.”*  

Lycka till med kodningen, och må dina dokument alltid renderas exakt som du tänkt!

## Vad bör du lära dig härnäst?


Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man laddar DOCX och upptäcker saknade typsnitt – komplett C#‑guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [Hur man upptäcker typsnitt i Aspose.Words – hantera varningar & inställningar](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Hur man använder LoadOptions i Aspose.Words – komplett guide](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}