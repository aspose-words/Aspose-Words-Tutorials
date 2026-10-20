---
category: general
date: 2026-01-14
description: Logga varningar för teckensnittssubstitution när du laddar Word‑dokument
  med Aspose.Words. Lär dig att upptäcka saknade teckensnitt och hur du fångar upp
  saknade teckensnitt i C#.
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: sv
og_description: Logga varningar om teckensnittssubstitution när du laddar Word-dokument
  med Aspose.Words. Upptäck hur du kan upptäcka saknade teckensnitt och fånga upp
  saknade teckensnitt i C#.
og_title: Logga varningar för teckensnittssubstitution – Fullständig Aspose.Words-guide
tags:
- Aspose.Words
- C#
- Document Processing
title: Logga varningar för teckensnittssubstitution – Komplett Aspose.Words-guide
url: /sv/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Logga varningar för teckensnittssubstitution – Komplett Aspose.Words-guide

Att logga varningar för teckensnittssubstitution är viktigt när du måste garantera att ett Word‑dokument ser exakt likadant ut efter att det har lästs in av Aspose.Words. Om du någonsin har undrat hur man **detect missing fonts** eller vill veta **how to capture missing fonts**, är du på rätt plats.  

I den här handledningen går vi igenom ett verkligt scenario, visar den kompletta C#‑koden och förklarar varför varje rad är viktig. När du är klar kommer du kunna logga varje teckensnittssubstitutions‑händelse och agera på den—inga mystiska varningar kvar.

![Exempel på loggning av teckensnittssubstitution](/images/font-warnings.png "Skärmbild som visar konsolutdata för loggning av teckensnittssubstitution")

## Vad du kommer att lära dig

- Hur du konfigurerar `LoadOptions` så att Aspose.Words höjer typade varningar för teckensnittssubstitution.  
- De exakta stegen för att **detect missing fonts** under dokumentladdning.  
- Ett rent sätt att **capture missing fonts** och skriva dem till din egen logg eller övervakningssystem.  
- Edge‑case‑hantering (t.ex. när ett dokument innehåller ett teckensnitt som inte är installerat på servern).  

### Förutsättningar

- .NET 6.0 eller senare (koden fungerar även med .NET Framework 4.6+).  
- En giltig Aspose.Words‑licens för .NET (eller en gratis provversion).  
- Grundläggande kunskap om C# och konsolapplikationer.  

Om du redan har detta, låt oss dyka ner.

## Steg 1 – Ställ in LoadOptions för att använda RaiseTypedWarnings

Kärnan i lösningen ligger i `LoadOptions.FontSubstitutionWarning`. Genom att byta den till `RaiseTypedWarnings` talar du om för Aspose.Words att avfyra en händelse **varje gång** den inte kan hitta exakt det teckensnitt du begärde.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **Why this matters:**  
> Standardbeteendet byter tyst ut ett saknat teckensnitt mot det närmaste matchande, vilket kan leda till layout‑glitchar du aldrig ser komma. Att höja typade varningar ger dig full insyn.

## Steg 2 – Prenumerera på varningshändelsen

Nu kopplar vi in oss på `loadOptions.FontSubstitutionWarning`. Lambdan får ett `e`‑objekt som exakt talar om vilket teckensnitt som saknades och vilket som användes istället.

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **Pro tip:** Om du kör detta på en webbserver, ersätt `Console.WriteLine` med en strukturerad logger (Serilog, NLog, osv.) så att du kan fråga efter data senare.

## Steg 3 – Ladda dokumentet med de konfigurerade alternativen

Med varningsmekanismen på plats laddar du helt enkelt dokumentet som du brukar. Händelsen avfyras automatiskt för varje saknat teckensnitt.

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### Förväntad konsolutdata

Om `input.docx` refererar till ett teckensnitt som heter *MyFancyFont* som inte är installerat, kommer du att se:

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

Varje rad motsvarar en **detect missing fonts**‑händelse och ger dig en komplett revisionsspårning.

## Steg 4 – Hantera edge‑case‑scenarier och avancerade situationer

### 4.1 När ingen substitution sker

Ibland använder ett dokument bara systemteckensnitt som redan finns. I så fall avfyras varningshändelsen aldrig, och du får en ren konsol utan någon utdata. Det är ett gott tecken—din miljö har redan alla nödvändiga teckensnitt.

### 4.2 Fånga varningar för senare analys

Om du behöver lagra varningarna för en nattlig rapport, samla dem i en lista:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

Efter laddning kan du serialisera `missingFonts` till JSON, skriva till en databas eller e‑mailla en sammanfattning.

### 4.3 Arbeta med PDF‑filer eller andra format

Samma `LoadOptions`‑metod fungerar för `Load`‑anrop på PDF, RTF och även HTML‑filer. Skicka bara samma options‑instans, så kommer Aspose.Words att höja varningar för varje teckensnitt den inte kan matcha.

## Steg 5 – Verifiera resultatet programatiskt

Om du föredrar ett automatiserat test istället för att titta på konsolen, påstå att listan innehåller förväntade poster:

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

Detta kodsnutt demonstrerar **how to capture missing fonts** i kod, inte bara i loggar.

## Vanliga fallgropar & hur man undviker dem

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| Forgetting to set `RaiseTypedWarnings` | The default is `DoNotRaise`, so no events fire. | Explicitly set `FontSubstitutionWarning` as shown in Step 1. |
| Using `Console.WriteLine` in a web app | Console output disappears in IIS/ASP.NET Core. | Switch to a persistent logger (e.g., Serilog). |
| Loading a document with a relative path | The working directory may differ at runtime. | Use absolute paths or `Path.Combine(AppContext.BaseDirectory, "input.docx")`. |
| Ignoring the `SubstitutedFontName` | You lose insight into which fallback was chosen. | Always log both `FontName` and `SubstitutedFontName`. |

## Bonus: Automatisera teckensnittsinstallation

Om du kontrollerar distributionsmiljön kan du förinstallera de saknade teckensnitten med ett PowerShell‑skript:

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

Att köra detta innan din applikation startar eliminerar de flesta **detect missing fonts**‑varningarna helt och hållet.

## Slutsats

Vi har gått igenom allt du behöver för att **log font substitution warnings** när du laddar Word‑dokument med Aspose.Words. Genom att konfigurera `LoadOptions`, prenumerera på varningshändelsen och eventuellt persistera resultaten kan du på ett pålitligt sätt **detect missing fonts** och förstå **how to capture missing fonts** för vilket .NET‑projekt som helst.

Ta koden, anpassa loggern efter din stack, så blir du aldrig överraskad av en tyst teckensnittssubstitution igen. Nästa steg kan inkludera:

- Integrera varningslistan med din CI/CD‑pipeline för att misslyckas byggen när kritiska teckensnitt saknas.  
- Utöka metoden för att övervaka teckensnittsanvändning över en flotta av dokument.  
- Utforska Aspose.Words `FontSettings`‑API för att tillhandahålla egna fallback‑teckensnitt.

Har du frågor eller ett knepigt scenario? Lämna en kommentar så felsöker vi tillsammans. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}