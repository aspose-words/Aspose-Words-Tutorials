---
category: general
date: 2026-01-11
description: Aktivera varningar för teckensnittssubstitution för att upptäcka saknade
  teckensnitt i dina .NET‑dokument. Lär dig hur du får namn på saknade teckensnitt
  och listar saknade teckensnitt med Aspose.Words.
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: sv
og_description: Aktivera varningar för teckensnittssubstitution i Aspose.Words för
  att upptäcka saknade teckensnitt, få namn på saknade teckensnitt och lista saknade
  teckensnitt i dina dokument.
og_title: Aktivera varningar för teckensnittssubstitution – Steg‑för‑steg C#‑handledning
tags:
- Aspose.Words
- C#
- Document Processing
title: Aktivera varningar för teckensnittssubstitution i Aspose.Words – Komplett guide
url: /sv/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aktivera varningar för teckensnittssubstitution – Komplett guide

Har du någonsin undrat varför ett Word-dokument ser lite felaktigt ut efter att du laddat upp det på en server? Sannolikt är ett teckensnitt som den ursprungliga författaren använde inte tillgängligt på din maskin, och Aspose.Words bytte tyst ut det mot det närmaste matchande. **Aktivera varningar för teckensnittssubstitution** och du får omedelbart veta vilka teckensnitt som saknas, vad de ersattes med och hur du ska agera på den informationen.

I den här handledningen går vi igenom ett praktiskt, end‑to‑end‑exempel som visar hur du **upptäcker saknade teckensnitt**, hämtar **get missing font name**, och till och med **list missing fonts** för rapportering. Inga onödiga detaljer, bara en tydlig lösning som du kan lägga in i vilket .NET‑projekt som helst idag.

---

## Vad du kommer att lära dig

- Hur du konfigurerar `LoadOptions` så att Aspose.Words avger detaljerade varningar.
- Den exakta koden som behövs för att ladda ett dokument och enumerera teckensnitt‑relaterade varningar.
- Sätt att extrahera det saknade teckensnittets namn och dess substitution, och sedan skriva ut en snygg rapport.
- Tips för att hantera kantfall, såsom dokument med dussintals saknade teckensnitt eller anpassade teckensnittsmappar.

### Förutsättningar

- .NET 6+ (koden fungerar också med .NET Framework 4.7+)
- Aspose.Words för .NET 23.10 eller nyare (du kan hämta det från NuGet)
- Ett exempel‑DOCX som refererar till ett teckensnitt du inte har installerat (vi kallar det `MissingFont.docx`)

Om du har dessa grunder, låt oss dyka ner.

---

## Steg 1: Ställ in LoadOptions för att aktivera varningar för teckensnittssubstitution  

Det första du måste göra är att tala om för Aspose.Words att du bryr dig om saknade teckensnitt. Som standard loggar biblioteket bara varningar internt. Att sätta `SubstitutionWarningLevel` till `Typical` (eller `All` för den mest utförliga utskriften) slår på funktionen.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**Varför detta är viktigt:**  
När `SubstitutionWarningLevel` är satt, lägger Aspose.Words varje gång det inte kan hitta ett refererat teckensnitt till dokumentets `Warnings`‑samling ett `FontSubstitutionWarning`. Den samlingen är det enda pålitliga sättet att **upptäcka saknade teckensnitt** utan att manuellt parsa dokumentet.

> **Pro tip:** Om du hanterar en batch av dokument och vill vara helt säker på att du fångar varje substitution, använd `FontSubstitutionWarningLevel.All`. Det är lite bullrigt men garanterar att ingen varning går förbi.

---

## Steg 2: Ladda dokumentet med de konfigurerade alternativen  

Nu när varningssystemet är förberett, ladda ditt DOCX med de `LoadOptions` vi just förberedde. Sökvägen kan vara absolut eller relativ; se bara till att filen finns.

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**Vad händer under huven?**  
Aspose.Words parsar dokumentets XML, löser upp varje `<w:font>`‑element och kontrollerar systemets teckensnittskatalog (plus eventuella anpassade mappar du kan ha lagt till i `FontSettings`). När det inte kan hitta ett teckensnitt, registrerar det en varning – exakt vad vi behöver för att **list missing fonts** senare.

---

## Steg 3: Iterera över varningar och extrahera detaljer om saknade teckensnitt  

Med dokumentet i minnet innehåller `Warnings`‑samlingen varje `FontSubstitutionWarning`. Vi kommer att loopa igenom den, filtrera efter rätt typ, och skriva ut en vänlig rapport.

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**Förväntad utskrift** (förutsatt att källdokumentet refererar till `MyCustomFont` som inte är installerat):

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

Observera hur varje post ger dig både **get missing font name** (`MyCustomFont`) och reservteckensnittet (`Arial`). Det är exakt den information du behöver för att besluta om du ska bädda in originalteckensnittet, be författaren om en ersättning, eller helt enkelt acceptera substitutionen.

---

## Steg 4: Valfritt – Samla data i en lista för vidare bearbetning  

Om du behöver exportera rapporten till CSV, skicka den via ett API, eller bara behålla den i minnet för senare, kan du lagra varningarna i en starkt‑typad lista.

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

Nu har du **list missing fonts** i ett format som vilket downstream‑system som helst kan konsumera. Oavsett om du matar ett dashboard eller genererar en audit‑logg, är data redo.

---

## Steg 5: Hantera kantfall och vanliga fallgropar  

### Flera saknade teckensnitt i ett enda körning  

Stora företagsmallar refererar ofta till dussintals anpassade teckensnitt. Varningssamlingen kan bli omfattande, men itereringsmönstret ovan skalar linjärt, så prestanda är ingen oro. Kom bara ihåg att hålla utskriften läsbar – gruppering efter sida eller stil kan vara hjälpsamt om du behöver djupare analys.

### Anpassade teckensnittsmappar  

Om du lagrar teckensnitt i en icke‑standard katalog (t.ex. en delad nätverksresurs), tala om för Aspose.Words var den ska leta:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

Att sätta detta *innan* du laddar dokumentet ger biblioteket en chans att hitta teckensnitten, vilket kan eliminera vissa varningar helt.

### Undertrycka specifika varningar  

Ibland vet du att en viss substitution är acceptabel (t.ex. ett dekorativt teckensnitt som du inte har något emot att ersätta). Du kan filtrera bort dem i efterhand:

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### Versionskompatibilitet  

`FontSubstitutionWarningLevel`‑enum har varit stabil sedan Aspose.Words 20.12. Om du använder en äldre version kan du behöva uppgradera för att få tillgång till varningsnivå‑funktionen.

---

## Fullt fungerande exempel  

Nedan är det kompletta, färdiga programmet som inkluderar alla stegen ovan. Klistra in det i ett nytt konsolprojekt, lägg till Aspose.Words‑NuGet‑paketet, och peka `docPath` på ett dokument som refererar till ett saknat teckensnitt.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

Att köra detta program kommer att **enable font substitution warnings**, **detect missing fonts**, **get missing font name**, och **list missing fonts** både i konsolen och i en CSV‑fil.

---

## Slutsats  

Vi har precis gått igenom allt du behöver för att **enable font substitution warnings** i Aspose.Words, från den initiala konfigurationen till att extrahera en ren lista över saknade teckensnitt. Genom att följa stegen ovan kan du granska dina dokument, säkerställa visuell integritet, och undvika obehagliga överraskningar när du renderar på en server.

Nästa steg kan du vilja utforska:

- "**Embedding missing fonts** direkt i den genererade PDF‑ eller DOCX‑filen (använd `FontSettings.EmbeddedFonts`)."
- "**Automating font installation** på byggagenter baserat på den genererade rapporten."
- "**Integrating with CI pipelines** för att misslyckas med byggen när kritiska teckensnitt saknas."

Prova dem, så förvandlar du ett enkelt varningssystem till ett fullskaligt teckensnittshanteringsflöde.

Lycklig kodning, och må alla dina teckensnitt bli funna!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}