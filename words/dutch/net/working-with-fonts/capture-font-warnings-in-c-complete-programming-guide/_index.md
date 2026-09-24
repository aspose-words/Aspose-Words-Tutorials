---
category: general
date: 2026-02-18
description: Leer hoe u lettertypewaarschuwingen kunt vastleggen en ontbrekende lettertypen
  kunt detecteren in C# met Aspose.Words. Volg deze stapsgewijze gids om ontbrekende
  lettertypen efficiënt te verwerken.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: nl
og_description: Leg fontwaarschuwingen vast in C# en leer hoe je ontbrekende lettertypen
  kunt detecteren, afhandelen en opsommen, met een volledig codevoorbeeld.
og_title: Lettertypewaarschuwingen vastleggen in C# – Complete gids
tags:
- Aspose.Words
- C#
- Font Management
title: Lettertypewaarschuwingen vastleggen in C# – Complete programmeergids
url: /nl/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lettertypewaarschuwingen vastleggen in C# – Complete programmeergids

Heb je je ooit afgevraagd hoe je **lettertypewaarschuwingen kunt vastleggen** wanneer een document een lettertype aanroept dat niet op de server is geïnstalleerd? Je bent niet de enige. In veel bedrijfsapplicaties veroorzaken ontbrekende lettertypen lay‑outproblemen, en de enige betrouwbare manier om ze te ontdekken is door te luisteren naar de waarschuwingen die de bibliotheek genereert.  

In deze tutorial laten we je een kant‑en‑klaar werkende oplossing zien die niet alleen **lettertypewaarschuwingen vastlegt**, maar ook **ontbrekende lettertypen detecteert**, **ontbrekende lettertypen afhandelt**, en zelfs **ontbrekende lettertypen opsomt**, zodat je kunt beslissen of je wilt substitueren, insluiten of de gebruiker waarschuwen. Geen externe documentatie nodig—gewoon kopiëren, plakken en uitvoeren.

## Wat je zult leren

- Hoe je `LoadOptions` configureert om waarschuwingen voor lettertype‑substitutie in te schakelen.  
- De exacte code die je nodig hebt om een DOCX te laden en elke waarschuwing op te halen.  
- Waarom elke stap belangrijk is, inclusief prestatie‑overwegingen.  
- Afhandeling van randgevallen, zoals documenten met gemengde‑script lettertypen of aangepaste lettertype‑mappen.  

**Prerequisites**: .NET 6+ (of .NET Framework 4.6+), een referentie naar het **Aspose.Words** NuGet‑pakket, en een basisbegrip van C#. Als je Aspose.Words nog nooit hebt gebruikt, geen zorgen—deze gids leidt je door elke nuance.

![Diagram van het vastleggen van lettertypewaarschuwingen](image.png){alt="diagram van lettertypewaarschuwingen vastleggen"}

## Lettertypewaarschuwingen vastleggen – Waarom het belangrijk is

Wanneer Aspose.Words een document laadt, vervangt het stilzwijgend elk niet‑beschikbaar lettertype door een fallback. Die fallback houdt de laadoperatie in stand, maar het visuele resultaat kan volledig uit balans zijn. Door de **SubstitutionWarningLevel.All**‑vlag in te schakelen, voegt de bibliotheek een `WarningInfo`‑item toe voor elk ontbrekend lettertype, waardoor je **ontbrekende lettertypen kunt detecteren** voordat het document wordt gerenderd of opgeslagen.

> **Pro tip:** Als je honderden bestanden verwerkt in een batch‑taak, kan het loggen van deze waarschuwingen naar een centrale opslag je later uren handmatige QA besparen.

## Stap 1: Stel je project in

1. Open je favoriete IDE (Visual Studio, Rider, VS Code).  
2. Maak een nieuw console‑project aan:

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. Voeg het Aspose.Words‑pakket toe:

```bash
dotnet add package Aspose.Words
```

Dat is alles—geen extra DLL's, geen COM‑interop. De bibliotheek levert alles wat je nodig hebt om **ontbrekende lettertypen af te handelen**.

## Stap 2: Bereid Load‑opties voor om alle lettertype‑substitutie‑waarschuwingen vast te leggen

Om de engine **lettertypewaarschuwingen vast te leggen**, moet je hem vertellen elke substitutie te registreren. Het volgende fragment maakt een `LoadOptions`‑instantie, schakelt het waarschuwingsniveau in, en (optioneel) wijst de engine op een map die aangepaste lettertypen bevat die je eventueel wilt gebruiken.

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

**Waarom dit belangrijk is:**  
- `SubstitutionWarningLevel.All` zorgt ervoor dat **elke** ontbrekende‑lettertype‑gebeurtenis wordt geregistreerd, niet alleen de eerste.  
- Zonder deze vlag vervangt Aspose.Words stilzwijgend het lettertype en weet je nooit dat er een probleem bestaat.

## Stap 3: Laad het document met de geconfigureerde opties

Nu openen we daadwerkelijk het bestand. Vervang `DocumentWithMissingFonts.docx` door het pad naar je testdocument.

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

Als het bestand verwijzingen bevat naar lettertypen die niet op de machine staan (of in de optionele map die je hebt toegevoegd), zal de `document.WarningInfoCollection` worden gevuld.

## Stap 4: Zoek en toon eventuele lettertype‑substitutie‑waarschuwingen

Hier is het hart van de tutorial: itereren over de `WarningInfoCollection` om **ontbrekende lettertypen op te sommen**. We filteren op `WarningType.FontSubstitution` en printen een vriendelijke boodschap.

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

### Verwachte uitvoer

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

Als het document alleen geïnstalleerde lettertypen gebruikt, zie je de regel “✅ No missing fonts detected”.

## Stap 5: Geavanceerd – Hoe je **ontbrekende lettertypen** programmatisch **afhandelt**

Alleen een lijst afdrukken kan voldoende zijn voor een diagnostisch hulpmiddel, maar veel productiesystemen moeten **ontbrekende lettertypen** automatisch **afhandelen**. Hieronder staan twee veelvoorkomende strategieën:

### 5.1 Substitueren met een bekende fallback

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 Een aangepast lettertype on‑the‑fly insluiten

Als je een bedrijfs‑lettertypebestand hebt (`MyBrand.ttf`), kun je het insluiten wanneer een ontbrekend lettertype wordt gedetecteerd:

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

> **Opmerking:** Het insluiten van lettertypen kan de bestandsgrootte van de output vergroten, dus weeg de afweging tussen getrouwe weergave en bandbreedte af.

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Symptoom | Waarschijnlijke oorzaak | Oplossing |
|----------|--------------------------|-----------|
| Er verschijnen geen waarschuwingen, hoewel het document er verkeerd uitziet | `SubstitutionWarningLevel` niet ingesteld op `All` | Zorg ervoor dat stap 2 de vlag exact zoals weergegeven instelt |
| Waarschuwingen vermelden hetzelfde lettertype meerdere keren | Document bevat het lettertype in verschillende stijlen | De‑duplicateer als je alleen een unieke lijst nodig hebt: `fontWarnings.Select(w => w.Description).Distinct()` |
| Applicatie crasht bij grote DOCX‑bestanden | Laden met standaard geheugeninstellingen | Gebruik `LoadOptions.LoadFormat` of stream het bestand om de geheugenbelasting te verminderen |

## Volledig werkend voorbeeld (Klaar om te kopiëren‑plakken)

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

Voer het programma uit met `dotnet run`. Je zou de lijst met ontbrekende lettertypen in de console moeten zien verschijnen, wat bevestigt dat je succesvol **lettertypewaarschuwingen hebt vastgelegd**.

## Conclusie

Je hebt nu een complete, productie‑klare patroon om **lettertypewaarschuwingen vast te leggen**, **ontbrekende lettertypen te detecteren**, **ontbrekende lettertypen af te handelen**, en **ontbrekende lettertypen op te sommen** met Aspose.Words in C#. De aanpak is lichtgewicht, vereist slechts een paar regels code, en kan in elke bestaande pipeline worden geïntegreerd—of je nu

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}