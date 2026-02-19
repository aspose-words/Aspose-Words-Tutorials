---
category: general
date: 2026-02-18
description: Lär dig hur du fångar teckensnittsvarningar och upptäcker saknade teckensnitt
  i C# med Aspose.Words. Följ den här steg‑för‑steg‑guiden för att hantera saknade
  teckensnitt effektivt.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: sv
og_description: Fånga fontvarningar i C# och lär dig att upptäcka saknade typsnitt,
  hantera saknade typsnitt och lista saknade typsnitt med ett komplett kodexempel.
og_title: Fånga teckensnittsvarningar i C# – Komplett guide
tags:
- Aspose.Words
- C#
- Font Management
title: Fånga teckensnittsvarningar i C# – Fullständig programmeringsguide
url: /sv/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

kan integreras i vilken befintlig pipeline som helst—oavsett om du"

The sentence seems cut off; keep as is.

Then closing shortcodes unchanged.

Now produce final content with all translations and unchanged placeholders.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Fånga teckensnittsvarningar i C# – Komplett programmeringsguide

Har du någonsin undrat hur man **fångar teckensnittsvarningar** när ett dokument refererar till ett teckensnitt som inte är installerat på servern? Du är inte ensam. I många företagsapplikationer orsakar saknade teckensnitt layoutproblem, och det enda pålitliga sättet att upptäcka dem är att lyssna på de varningar som biblioteket ger.  

I den här handledningen visar vi dig en färdig‑till‑körning‑lösning som inte bara **fångar teckensnittsvarningar** utan också **upptäcker saknade teckensnitt**, **hanterar saknade teckensnitt**, och till och med **listar saknade teckensnitt** så att du kan besluta om du ska ersätta, bädda in eller varna användaren. Ingen extern dokumentation behövs—bara kopiera, klistra in och kör.

## Vad du kommer att lära dig

- Hur du konfigurerar `LoadOptions` för att aktivera varningar för teckensnittsbyte.  
- Den exakta koden du behöver för att läsa in en DOCX och hämta varje varning.  
- Varför varje steg är viktigt, inklusive prestandaöverväganden.  
- Hantering av kantfall såsom dokument med blandade skriptteckensnitt eller anpassade teckensnittsmappar.  

**Förutsättningar**: .NET 6+ (eller .NET Framework 4.6+), en referens till **Aspose.Words** NuGet‑paketet, och en grundläggande förståelse för C#. Om du aldrig har använt Aspose.Words tidigare, oroa dig inte—den här guiden går igenom varje nyans.

![Diagram som visar flödet för att fånga teckensnittsvarningar](image.png){alt="Diagram som visar flödet för att fånga teckensnittsvarningar"}

## Fånga teckensnittsvarningar – Varför det är viktigt

När Aspose.Words läser in ett dokument byter det tyst ut alla otillgängliga teckensnitt mot ett reservteckensnitt. Det reservteckensnittet håller laddningsoperationen igång, men det visuella resultatet kan bli helt felplacerat. Genom att aktivera flaggan **SubstitutionWarningLevel.All** lägger biblioteket till en `WarningInfo`‑post för varje saknat teckensnitt, vilket gör att du kan **upptäcka saknade teckensnitt** innan dokumentet renderas eller sparas.

> **Proffstips:** Om du bearbetar hundratals filer i ett batchjobb, kan loggning av dessa varningar till en central lagring spara dig timmar av manuell QA senare.

## Steg 1: Ställ in ditt projekt

1. Öppna din favorit‑IDE (Visual Studio, Rider, VS Code).  
2. Skapa ett nytt konsolprojekt:

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. Lägg till Aspose.Words‑paketet:

```bash
dotnet add package Aspose.Words
```

Det är allt—inga extra DLL‑filer, ingen COM‑interop. Biblioteket levererar allt du behöver för att **hantera saknade teckensnitt**.

## Steg 2: Förbered LoadOptions för att fånga alla varningar om teckensnittsbyte

För att få motorn att **fånga teckensnittsvarningar** måste du instruera den att registrera varje byte. Följande kodsnutt skapar en `LoadOptions`‑instans, aktiverar varningsnivån och (valfritt) pekar motorn mot en mapp som innehåller anpassade teckensnitt du eventuellt vill använda.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**Varför detta är viktigt:**  
- `SubstitutionWarningLevel.All` säkerställer att **varje** saknat‑teckensnitt‑händelse registreras, inte bara den första.  
- Utan denna flagga ersätter Aspose.Words tyst teckensnittet och du får aldrig veta att ett problem finns.

## Steg 3: Läs in dokumentet med de konfigurerade alternativen

Nu öppnar vi faktiskt filen. Ersätt `DocumentWithMissingFonts.docx` med sökvägen till ditt testdokument.

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

Om filen innehåller några referenser till teckensnitt som inte finns på maskinen (eller i den valfria mappen du lade till), kommer `document.WarningInfoCollection` att fyllas.

## Steg 4: Hitta och visa eventuella varningar om teckensnittsbyte

Här är hjärtat i handledningen: iterera över `WarningInfoCollection` för att **lista saknade teckensnitt**. Vi filtrerar på `WarningType.FontSubstitution` och skriver ut ett vänligt meddelande.

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Förväntad utdata

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

Om dokumentet endast använder installerade teckensnitt kommer du att se raden “✅ No missing fonts detected”.

## Steg 5: Avancerat – Hur du **hanterar saknade teckensnitt** programatiskt

Att bara skriva ut en lista kan räcka för ett diagnostikverktyg, men många produktionssystem behöver **hantera saknade teckensnitt** automatiskt. Nedan följer två vanliga strategier:

### 5.1 Ersätt med ett känt reservteckensnitt

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 Bädda in ett anpassat teckensnitt i farten

Om du har en företagsfontfil (`MyBrand.ttf`) kan du bädda in den när ett saknat teckensnitt upptäcks:

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **Obs:** Att bädda in teckensnitt kan öka filens storlek, så överväg avvägningen mellan kvalitet och bandbredd.

## Vanliga fallgropar och hur du undviker dem

| Symptom | Trolig orsak | Åtgärd |
|---------|--------------|--------|
| Inga varningar visas även om dokumentet ser felaktigt ut | `SubstitutionWarningLevel` inte satt till `All` | Se till att steg 2 sätter flaggan exakt som visas |
| Varningar listar samma teckensnitt flera gånger | Dokumentet innehåller teckensnittet i flera stilar | Deduplikera om du bara behöver en unik lista: `fontWarnings.Select(w => w.Description).Distinct()` |
| Applikationen kraschar på stora DOCX‑filer | Laddning med standardminnesinställningar | Använd `LoadOptions.LoadFormat` eller strömma filen för att minska minnesbelastningen |

## Fullt fungerande exempel (Klar‑för‑kopiering)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

Kör programmet med `dotnet run`. Du bör se listan över saknade teckensnitt skriven till konsolen, vilket bekräftar att du framgångsrikt har **fångat teckensnittsvarningar**.

## Slutsats

Du har nu ett komplett, produktionsklart mönster för att **fånga teckensnittsvarningar**, **upptäcka saknade teckensnitt**, **hantera saknade teckensnitt**, och **lista saknade teckensnitt** med Aspose.Words i C#. Metoden är lättviktig, kräver bara några rader kod, och kan integreras i vilken befintlig pipeline som helst—oavsett om du

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}