---
category: general
date: 2026-06-20
description: Schakel waarschuwingen voor lettertypevervanging in C# in met Aspose.Words.
  Leer hoe je LoadOptions configureert, waarschuwingen vastlegt en ontbrekende lettertypen
  efficiënt afhandelt.
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: nl
og_description: Schakel waarschuwingen voor lettertypevervanging in C# met Aspose.Words.
  Deze gids laat zien hoe je LoadOptions instelt, WarningInfo leest en berichten over
  ontbrekende lettertypen weergeeft.
og_title: Lettertypevervangingswaarschuwingen inschakelen in C# – Complete gids
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: Waarschuwingen voor lettertypevervanging inschakelen in C# met Aspose.Words
url: /nl/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Font substitution warnings inschakelen in C# met Aspose.Words

Heb je je ooit afgevraagd hoe je **font substitution warnings inschakelen** kunt wanneer een Word‑document verwijst naar een lettertype dat niet op de server is geïnstalleerd? Je bent niet de enige. Ontbrekende lettertypen kunnen stilletjes de lay‑out van gegenereerde PDF‑s of afbeeldingen corrumperen, en de enige manier om dat vroegtijdig te detecteren is door naar de waarschuwingen te luisteren die Aspose.Words uitzendt.

In deze tutorial lopen we een hands‑on voorbeeld door dat je precies laat zien hoe je die waarschuwingen inschakelt, ze uit de `WarningInfo`‑collectie haalt en betekenisvolle berichten naar de console print. Aan het einde weet je hoe je **Aspose.Words LoadOptions** configureert, **C# font substitution warnings** afhandelt, en je document‑verwerkings‑pipeline robuust houdt.

We behandelen ook een paar randgevallen—wat er gebeurt als je waarschuwingen onderdrukt, of als je ze moet loggen in plaats van af te drukken—en geven je een compleet, copy‑and‑paste‑klaar code‑voorbeeld dat werkt met de nieuwste Aspose.Words voor .NET (vanaf versie 24.10).

## Wat je nodig hebt

- .NET 6.0 of later (de code werkt ook op .NET Framework 4.7+)
- Een NuGet‑referentie naar `Aspose.Words` (installeren via `dotnet add package Aspose.Words`)
- Een Word‑bestand dat verwijst naar een lettertype dat je **niet** geïnstalleerd hebt (bijv. `DocumentWithMissingFont.docx`)
- Een degelijke IDE (Visual Studio, Rider, of VS Code)

Dat is alles—geen extra services, geen propriëtaire tools. Klaar? Laten we beginnen.

## Stap 1: Font substitution warnings inschakelen

Het eerste wat je moet doen is Aspose.Words vertellen dat je een melding wilt ontvangen wanneer het een ontbrekend lettertype vervangt. Dit gebeurt via de `FontSettings`‑eigenschap van een `LoadOptions`‑object. Standaard zijn waarschuwingen **uitgeschakeld** om de API stil te houden, dus we moeten de schakelaar zelf omzetten.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **Waarom dit werkt:** Wanneer `FontSettings` niet `null` is, vult de bibliotheek automatisch `Document.WarningInfo` met alle `WarningType.FontSubstitution`‑items die het tegenkomt tijdens het laden van een document. Beschouw het als het inschakelen van een “debug‑mode” voor lettertypen.

## Stap 2: Het document laden met geconfigureerde opties

Nu de waarschuwingscollectie actief is, laad je document met de `LoadOptions` die we zojuist hebben voorbereid. Als het document een ontbrekend lettertype bevat, zal Aspose.Words een fallback gebruiken en een waarschuwing toevoegen aan de `WarningInfo`‑lijst.

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **Pro tip:** Als je veel bestanden in een lus verwerkt, hergebruik dan dezelfde `LoadOptions`‑instantie—eenmalig aanmaken bespaart enkele milliseconden per iteratie.

## Stap 3: Doorloop WarningInfo en toon font substitution‑berichten

Zodra het document is geladen, bevat de `WarningInfo`‑collectie elke waarschuwing die tijdens het laden is opgetreden. We zijn alleen geïnteresseerd in `WarningType.FontSubstitution`, dus filteren we dienovereenkomstig.

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

Het uitvoeren van de bovenstaande code tegen een document dat verwijst naar het ontbrekende lettertype “Papyrus” kan een output opleveren zoals:

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

Dat zijn de **font substitution messages** waar je naar op zoek was—duidelijk, bruikbaar, en klaar om gelogd te worden of naar een waarschuwingssysteem te sturen.

## Volledig werkend voorbeeld

Hieronder staat een zelfstandige console‑applicatie die alles samenbrengt. Kopieer‑en‑plak het in een nieuw `.csproj`‑bestand en druk op **Run**.

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### Verwachte output

Als het document verwijst naar lettertypen die niet geïnstalleerd zijn, zie je iets vergelijkbaars met:

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

Als elk lettertype aanwezig is op de machine, zal het programma simpelweg afdrukken:

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## Veelvoorkomende valkuilen & Pro‑tips

| Issue | Why It Happens | How to Fix / Avoid |
|-------|----------------|--------------------|
| **Waarschuwingen verdwijnen** | Je hebt `FontSettings` gewist of een `LoadOptions` zonder deze gebruikt. | Instantieer altijd `FontSettings`, zelfs als je geen eigenschappen wijzigt. |
| **Te veel waarschuwingen** | Het document gebruikt veel exotische lettertypen. | Overweeg een aangepaste lettertype‑map toe te voegen aan `FontSettings` via `SetFontsFolder` om substituties te verminderen. |
| **Prestatieverlies in een strakke lus** | Het opnieuw aanmaken van `LoadOptions` bij elke iteratie voegt overhead toe. | Hergebruik één enkele `LoadOptions`‑instantie voor alle documenten. |
| **Ontbrekende console‑output** | Uitvoeren binnen een GUI‑applicatie waar `Console.WriteLine` wordt genegeerd. | Redirect waarschuwingen naar een logger (`ILogger`) of schrijf ze naar een bestand. |

### Waarschuwingen afhandelen in een real‑world service

In een web‑API wil je waarschijnlijk niet naar de console schrijven. Pipe de waarschuwingen in plaats daarvan naar een gestructureerd logboek:

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

Zo behoud je **document warning handling** terwijl je service schoon blijft.

## Voorbeeld uitbreiden

- **Andere waarschuwings‑typen vastleggen** (bijv. `WarningType.UnknownFileFormat`) door de `if`‑filter te verwijderen.
- **Een rapport opslaan** van alle waarschuwingen naar JSON voor downstream‑analyse.
- **Een specifiek fallback‑lettertype forceren** door `FontSettings.SubstitutionSettings.DefaultFontName` in te stellen.

Al deze zijn natuurlijke uitbreidingen zodra je **font substitution warnings inschakelen** onder de knie hebt.

## Conclusie

We hebben je laten zien hoe je **font substitution warnings inschakelt** in C# met Aspose.Words, van het configureren van `LoadOptions` tot het itereren over `WarningInfo` en het afdrukken van vriendelijke berichten. Door de bovenstaande stappen te volgen kun je je document‑verwerkings‑pipelines beschermen tegen stille lay‑out‑wijzigingen veroorzaakt door ontbrekende lettertypen.

Probeer vervolgens een aangepaste lettertype‑map toe te voegen, de waarschuwingen naar een bestand te loggen, of ze zelfs naar een monitoring‑dashboard te sturen. Hetzelfde patroon werkt voor elk **document warning handling**‑scenario, of je nu converteert naar PDF, afbeeldingen rendert, of mail‑merge uitvoert.

Heb je vragen over **C# font substitution warnings** of wil je een slimme oplossing delen? Laat een reactie achter—veel plezier met coderen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Font substitution warnings inschakelen in Aspose.Words – Complete gids](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Hoe lettertypen detecteren in Aspose.Words – Waarschuwingen & instellingen afhandelen](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Font substitution warnings vastleggen in Java met Aspose.Words – Complete gids](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}