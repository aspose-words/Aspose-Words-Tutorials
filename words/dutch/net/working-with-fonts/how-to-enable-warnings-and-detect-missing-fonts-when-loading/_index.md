---
category: general
date: 2026-02-21
description: Leer hoe je waarschuwingen inschakelt, ontbrekende lettertypen detecteert
  en hoe je docx veilig laadt met Aspose.Words in C#. Volg de stapsgewijze gids.
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: nl
og_description: Hoe waarschuwingen in te schakelen, ontbrekende lettertypen te detecteren
  en docx‑bestanden correct te laden met Aspose.Words. Volledig codevoorbeeld inbegrepen.
og_title: Hoe waarschuwingen in te schakelen en ontbrekende lettertypen te detecteren
  bij het laden van DOCX
tags:
- C#
- Aspose.Words
- Document processing
title: Hoe waarschuwingen in te schakelen en ontbrekende lettertypen te detecteren
  bij het laden van DOCX‑bestanden
url: /nl/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe waarschuwingen in te schakelen en ontbrekende lettertypen te detecteren bij het laden van DOCX‑bestanden

Heb je je ooit afgevraagd **hoe je waarschuwingen** voor ontbrekende lettertypen kunt inschakelen voordat ze stilletjes je documentweergave verpesten? Je bent niet de enige—de meeste ontwikkelaars gaan ervan uit dat de bibliotheek gewoon “het juiste doet”, alleen om later te ontdekken dat een lettertype is vervangen zonder enige aanwijzing.  

In deze tutorial laten we je precies zien **hoe je waarschuwingen inschakelt**, hoe je **ontbrekende lettertypen detecteert**, en de juiste manier **hoe je docx laadt** met Aspose.Words voor .NET. Aan het einde heb je een kant‑klaar voorbeeld dat elke lettertype‑vervangingswaarschuwing naar de console print, zodat je nooit meer hoeft te raden wat er in het bestand is gebeurd.

## Prerequisites

- .NET 6.0 of later (de code werkt ook op .NET Framework 4.7+)  
- Visual Studio 2022 of een andere C#‑IDE naar keuze  
- Het **Aspose.Words** NuGet‑pakket (`Install-Package Aspose.Words`)  
- Een DOCX‑bestand dat mogelijk lettertypen bevat die niet op je machine geïnstalleerd zijn (we noemen het `input.docx`)

> **Pro tip:** Als je geen testbestand hebt, open dan gewoon een Word‑document dat een aangepast bedrijfslettertype gebruikt en sla het op als `input.docx`. Dat zal de waarschuwing activeren die we willen vastleggen.

## Overview of the solution

1. **Maak** een `LoadOptions`‑object aan met `FontSubstitutionWarnings` ingeschakeld.  
2. **Laad** het DOCX‑bestand met die opties.  
3. **Inspecteer** de `WarningCallback`‑collectie op eventuele `FontSubstitution`‑items.  
4. **Reageer** – je kunt loggen, weergeven, of zelfs het ontbrekende lettertype programmatisch vervangen.

Hieronder splitsen we elke stap uit, leggen *waarom* het belangrijk is, en geven we je een volledige, uitvoerbare code‑snippet.

---

## Stap 1: Installeer Aspose.Words en zet het project op

Voordat we **hoe je waarschuwingen inschakelt** kunnen, hebben we de bibliotheek nodig die ze daadwerkelijk ondersteunt.

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

Of, in de Visual Studio Package Manager Console:

```powershell
Install-Package Aspose.Words
```

> **Waarom deze stap?**  
> Zonder het pakket bestaan de `LoadOptions`, `Document` en de waarschuwingsinfrastructuur simpelweg niet. Het toevoegen van de NuGet‑referentie zorgt ervoor dat je de nieuwste stabiele versie ophaalt (op het moment van schrijven, 24.5).

## Stap 2: Maak laadopties die waarschuwingen voor lettertype‑substitutie inschakelen

Het hart van **hoe je waarschuwingen inschakelt** bevindt zich in de `LoadOptions`‑klasse. Het instellen van `FontSubstitutionWarnings` op `true` vertelt de engine om elke keer dat een ontbrekend lettertype moet worden vervangen, te registreren.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **Waarom deze vlag inschakelen?**  
> Standaard vervangt Aspose.Words stilletjes ontbrekende lettertypen door een fallback (meestal Arial). Dat kan leiden tot lay‑outverschuivingen, onzichtbare tekens of merkinbreuken. Het inschakelen van de vlag geeft je volledige zichtbaarheid.

## Stap 3: Laad het DOCX‑bestand met de geconfigureerde opties

Nu we weten **hoe je docx laadt** met ingeschakelde waarschuwingen, voeren we de lading daadwerkelijk uit.

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **Wat gebeurt er onder de motorkap?**  
> Tijdens het parseren van de DOCX controleert Aspose.Words elk `<w:rFonts>`‑element. Als het opgegeven lettertype niet geïnstalleerd is, registreert het een `FontSubstitution`‑waarschuwing en valt terug op een standaardlettertype. Omdat we waarschuwingen hebben ingeschakeld, komen die items terecht in `document.WarningCallback.Warnings`.

## Stap 4: Haal lettertype‑substitutie‑waarschuwingen op en toon ze

De eigenschap `WarningCallback` bevat een `WarningInfoCollection`. Loop erdoorheen, filter op `WarningType.FontSubstitution`, en geef de berichten weer.

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**Verwachte output** (voorbeeld):

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **Wat te doen met deze berichten?**  
> Je kunt ze loggen naar een bestand, weergeven in een UI, of zelfs een aangepaste fallback‑routine voor lettertypen activeren. Het belangrijkste is dat je nu *ontbrekende lettertypen detecteert* in plaats van later te moeten raden.

## Stap 5: (Optioneel) Vervang ontbrekende lettertypen door een specifieke fallback

Als je een bedrijfslettertype hebt dat je wilt afdwingen, kun je de waarschuwingen afhandelen en ze direct vervangen.

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **Waarom dit overwegen?**  
> Het garandeert visuele consistentie over alle gegenereerde documenten, wat cruciaal is voor merknaleving.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat één C#‑bestand dat je kunt kopiëren‑en‑plakken in een console‑applicatie. Het behandelt alles—van het installeren van het pakket tot het afdrukken van waarschuwingen.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Voer uit**: `dotnet run` vanuit de projectmap. Als er lettertypen ontbreken, zie je de waarschuwingen afgedrukt, en wordt de optionele vervanging toegepast voordat het bestand wordt opgeslagen.

## Veelgestelde vragen

### Werkt dit ook met PDF‑conversie?

Ja. Nadat je de waarschuwingen hebt afgehandeld, kun je `doc.Save("output.pdf")` aanroepen en verschijnen de vervangen lettertypen in de PDF zoals ze in de DOCX staan.

### Wat als ik waarschuwingen voor een specifiek lettertype wil onderdrukken?

Je kunt ze filteren in de lus—sla simpelweg de `WarningInfo` over waarvan de `Message` de naam van het lettertype bevat dat je wilt negeren.

### Is `FontSubstitutionWarnings` beschikbaar in oudere Aspose.Words‑versies?

Het werd geïntroduceerd in versie 20.5. Als je vastzit op een oudere release, upgrade dan via NuGet; de API‑wijziging is achterwaarts compatibel.

## Conclusie

We hebben stap voor stap **hoe je waarschuwingen inschakelt** doorlopen, je laten **ontbrekende lettertypen detecteren**, en de juiste manier **hoe je docx laadt** met Aspose.Words gedemonstreerd, terwijl je volledige zichtbaarheid op lettertype‑substituties behoudt. Door `document.WarningCallback.Warnings` te inspecteren krijg je een betrouwbaar audit‑logboek—geen stille vervangingen meer.

Volgende stappen? Probeer de waarschuwingslogica te koppelen aan een logging‑framework zoals Serilog, of bouw een UI die ontbrekende lettertypen markeert voordat je het document naar gebruikers verzendt. Je kunt ook de `FontSettings`‑klasse verkennen voor meer gedetailleerde controle over lettertype‑substitutie‑beleid.

Veel programmeerplezier, en moge je documenten altijd precies renderen zoals je bedoeld hebt! 

![Diagram die de stroom van het laden van een DOCX‑bestand tot het vastleggen van lettertype‑substitutie‑waarschuwingen weergeeft – hoe je waarschuwingen inschakelt in Aspose.Words](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}