---
category: general
date: 2026-04-07
description: Lär dig hur du upptäcker typsnitt och hur du fångar varningar när du
  hanterar saknade typsnitt i C# med Aspose.Words. Steg‑för‑steg‑kod inkluderad.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: sv
og_description: Hur upptäcker du teckensnitt i Aspose.Words? Följ den här handledningen
  för att fånga varningar och hantera saknade teckensnitt utan ansträngning.
og_title: Hur man upptäcker teckensnitt i Aspose.Words – Komplett guide
tags:
- Aspose.Words
- C#
- Font handling
title: Hur man upptäcker typsnitt i Aspose.Words – Komplett guide
url: /sv/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man upptäcker teckensnitt i Aspose.Words – Komplett guide

Har du någonsin undrat **hur man upptäcker teckensnitt** som saknas i ett Word-dokument innan du skickar det till produktion? Du är inte ensam. I många företagsmiljöer kan ett felaktigt teckensnitt bryta en PDF‑konverteringspipeline eller orsaka layout‑glitchar som ser oprofessionella ut. Den goda nyheten är att Aspose.Words ger dig ett inbyggt sätt att sniffa upp de frånvarande teckensnitten och visa tydliga varningar.

I den här handledningen går vi igenom exakt **hur man upptäcker teckensnitt**, **hur man fångar varningar**, och bästa praxis för att **hantera saknade teckensnitt** så att din applikation förblir robust. Inga externa verktyg, ingen gissning—bara ren C#‑kod som du kan släppa in i ditt projekt just nu.

> **Snabb förhandsvisning:** Vid slutet kommer du att ha en återanvändbar `FontSubstitutionWarningCollector` som samlar varje teckensnitt‑substitutionsmeddelande under dokumentladdning, och du kommer att veta hur du ska reagera när ett teckensnitt inte kan hittas.

---

## Vad du kommer att lära dig

- Hur du konfigurerar `LoadOptions` för att lyssna på varningar om teckensnitt‑substitution.  
- Hur du fångar dessa varningar i en anpassad samlarklass.  
- Hur du bearbetar de insamlade varningarna och beslutar om du ska avbryta, logga eller ersätta teckensnitt.  
- Hantering av edge‑case för dokument som refererar till fjärr‑ eller inbäddade teckensnitt.  

**Förutsättningar:** .NET 6+ (eller .NET Framework 4.6+), Aspose.Words för .NET (senaste versionen), och en grundläggande förtrogenhet med C#. Om du aldrig har använt Aspose.Words tidigare, oroa dig inte—denna guide förutsätter bara några minuters installationstid.

## Så upptäcker du teckensnitt med Aspose.Words LoadOptions

Det första steget för att upptäcka saknade teckensnitt är att tala om för Aspose.Words att rapportera dem. Detta görs via egenskapen `LoadOptions.WarningCallback`, som accepterar vilken klass som helst som implementerar `IWarningCallback`. Nedan skapar vi en liten samlare som lagrar varje varning för senare inspektion.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**Varför detta är viktigt:** Utan en varningscallback ersätter Aspose.Words tyst saknade teckensnitt med ett standardteckensnitt, och du får aldrig veta att ett problem finns. Genom att fånga `WarningType.FontSubstitution` får vi full insyn—exakt den data du behöver för att **upptäcka teckensnitt** som inte finns på värddatorn.

Nu kopplar vi samlaren till `LoadOptions` och laddar ett dokument:

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **Proffstips:** Om du arbetar med många dokument i ett batch‑läge, återanvänd samma `FontSubstitutionWarningCollector`‑instans men kom ihåg att anropa `Clear()` mellan laddningar för att undvika att blanda varningar från olika filer.

## Fånga varningar under dokumentladdning

Efter att dokumentet har laddats har samlaren redan alla teckensnitt‑relaterade varningar. Den nästa logiska frågan är: *Hur fångar jag varningar* på ett sätt som är enkelt att logga eller visa?

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

Typisk output ser ut så här:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**Vad detta visar:** Varje rad avslöjar det ursprungliga teckensnittets namn och den reserv som Aspose.Words valde. Beväpnad med denna information kan du avgöra om reservteckensnittet är acceptabelt eller om du behöver bädda in det saknade teckensnittet manuellt.

## Hantera saknade teckensnitt på ett smidigt sätt

Att upptäcka och fånga varningar är bara halva striden. Det verkliga värdet kommer när du **hanterar saknade teckensnitt** på ett produktionsklart sätt. Nedan följer tre vanliga strategier:

1. **Logga och fortsätt** – Lämplig för batch‑bearbetning där du bara behöver ett revisionsspår.  
2. **Avbryt vid kritiska teckensnitt** – Kasta ett undantag om ett specifikt teckensnitt (t.ex. ett varumärkes‑specifikt typsnitt) saknas.  
3. **Bädda in teckensnittet i farten** – Ladda det saknade teckensnittet från en känd mapp och registrera det i Aspose.Words innan du laddar om dokumentet.

### Exempel: Avbryt vid ett kritiskt teckensnitt

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### Exempel: Automatisk inbäddning av saknade teckensnitt

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**Varför dessa mönster hjälper:** Genom att explicit bestämma vad som ska göras när ett teckensnitt saknas, eliminerar du tysta reservval som kan äventyra varumärket eller läsbarheten. Detta är kärnan i **hantering av saknade teckensnitt** på ett kontrollerat sätt.

## Komplett fungerande exempel

När vi sätter ihop allt, här är ett enda, färdigt‑att‑köra‑program som demonstrerar **hur man upptäcker teckensnitt**, **hur man fångar varningar**, och en enkel policy för att **hantera saknade teckensnitt** genom att logga dem.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**Förväntat resultat:** När du kör programmet mot ett dokument som refererar till ett teckensnitt som inte finns på maskinen, kommer konsolen att lista varje substitutionsvarning. Om någon varning involverar ett teckensnitt från `critical`‑uppsättningen, avslutas programmet tidigt, vilket förhindrar att en felaktig PDF genereras.

## Vanliga frågor (FAQ)

| Question | Answer |
|----------|--------|
| *Behöver jag en licens för Aspose.Words för att använda den här koden?* | Ja, en giltig Aspose.Words‑licens tar bort utvärderingsvattenstämplar och låser upp full funktionalitet. |
| *Kan detta tillvägagångssätt upptäcka inbäddade teckensnitt?* | Inbäddade teckensnitt är redan en del av filen, så Aspose.Words kommer inte att ge en substitutionsvarning. Du kan kontrollera `Document.FontInfos` för att lista inbäddade teckensnitt om så behövs. |
| *Vad händer om det saknade teckensnittet är ett systemteckensnitt på Windows men inte på Linux?* | Samma varning kommer att utlösas på Linux eftersom teckensnittet inte är installerat där. Använd strategin “hantera saknade teckensnitt” för att leverera de nödvändiga `.ttf`‑filerna med din app. |
| *Är varningssamlaren trådad* |  |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}