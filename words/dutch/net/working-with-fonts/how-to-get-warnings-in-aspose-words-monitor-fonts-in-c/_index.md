---
category: general
date: 2026-01-06
description: Leer hoe u waarschuwingen kunt ontvangen bij het laden van documenten
  en hoe u lettertypen kunt monitoren met Aspose.Words. Deze gids behandelt waarschuwing‑callbacks
  en het bijhouden van lettertype‑substitutie.
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: nl
og_description: Hoe krijg je waarschuwingen in Aspose.Words? Volg deze stapsgewijze
  tutorial om lettertypen te monitoren en substitutie‑berichten vast te leggen tijdens
  het laden van documenten.
og_title: Hoe waarschuwingen te krijgen in Aspose.Words – Lettertypen monitoren
tags:
- Aspose.Words
- C#
- Font Monitoring
title: Hoe waarschuwingen ontvangen in Aspose.Words – Lettertypen monitoren in C#
url: /nl/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe waarschuwingen te krijgen in Aspose.Words – Lettertypen monitoren in C#

Heb je je ooit afgevraagd **hoe je waarschuwingen kunt krijgen** wanneer een Word‑document lettertypen bevat die je niet geïnstalleerd hebt? Het is een veelvoorkomend probleem—je app verwisselt stilletjes ontbrekende lettertypen, en je weet nooit wat er veranderd is. Het goede nieuws is dat je kunt inhaken op het waarschuwingssysteem van Aspose.Words en **lettertypen kunt monitoren** in realtime.

In deze tutorial laten we je precies zien hoe je die lettertype‑substitutie‑waarschuwingen kunt vastleggen, waarom het belangrijk is, en wat je met die informatie kunt doen zodra je die hebt. Geen externe documentatie, alleen een volledig, uitvoerbaar voorbeeld dat je nu meteen in Visual Studio kunt plakken.

> **Pro tip:** Als je een document‑conversiepijplijn bouwt, bespaart het vroegtijdig loggen van ontbrekende lettertypen je van vervelende lay‑out verrassingen later.

---

## Wat je nodig hebt

- **Aspose.Words for .NET** (nieuwste versie; de API is niet veranderd sinds v23.10)
- Een .NET‑ontwikkelomgeving (Visual Studio, Rider, of VS Code met de C#‑extensie)
- Een voorbeeld‑`.docx` dat een lettertype verwijst dat je niet geïnstalleerd hebt (bijv. **“NonExistentFont”**)

Dat is alles—geen extra NuGet‑pakketten naast Aspose.Words.

## Stap 1 – Een waarschuwingverzamelaar instellen (Primary Keyword in Header)

Het eerste wat je nodig hebt, is een plek om waarschuwingen op te slaan terwijl ze optreden. Aspose.Words biedt de `WarningCallback`‑eigenschap op `LoadOptions` precies voor dit doel.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**Waarom dit belangrijk is:**  
Wanneer de bibliotheek een ontbrekend lettertype tegenkomt, gooit hij geen uitzondering; hij geeft een `WarningInfo`‑object af. Door een verzamelaar aan te sluiten, krijg je volledige zichtbaarheid op elk substitutie‑evenement, waardoor je **lettertypen kunt monitoren** zonder je console te vervuilen met irrelevante berichten.

## Stap 2 – Het document laden met de waarschuwing‑geactiveerde opties

Nu lezen we daadwerkelijk het bestand. De `LoadOptions` die we in de vorige stap hebben voorbereid, zorgen ervoor dat alle lettertype‑gerelateerde waarschuwingen worden vastgelegd.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**Wat er onder de motorkap gebeurt:**  
Aspose.Words parseert het Word‑bestand, lost lettertypen op, en wanneer het een aangevraagd lettertype niet kan vinden, valt het terug op een substituut (meestal Arial). Het terugvallen veroorzaakt een `WarningType.FontSubstitution`‑waarschuwing, die terechtkomt in `warningCollector`.

## Stap 3 – De verzamelde waarschuwingen inspecteren (Primary Keyword Appears Again)

Nadat het document is geladen, itereren we eenvoudig over de `warningCollector` en printen we eventuele lettertype‑substitutie‑berichten.

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**Verwachte output** (ervan uitgaande dat het ontbrekende lettertype *“FancyScript”* is):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

Als het document meerdere onbekende lettertypen bevat, zie je één regel per substitutie—perfect voor logging of alerts.

## Stap 4 – Optioneel: De waarschuwingsinformatie loggen of opslaan

In productie wil je waarschijnlijk meer dan een `Console.WriteLine`. Hier is een snel voorbeeld dat de waarschuwingen naar een JSON‑bestand schrijft voor latere analyse.

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

Nu heb je een permanent record dat je kunt invoeren in een monitoring‑dashboard, of zelfs een geautomatiseerd verzoek kunt triggeren voor de ontbrekende lettertype‑bestanden.

## Stap 5 – Het resultaat verifiëren en opruimen

Voer het programma uit. Als je de substitutie‑berichten ziet, heb je succesvol **waarschuwingen gekregen** en ben je nu actief **lettertypen aan het monitoren**. Als er niets verschijnt, controleer dan dubbel of het testdocument werkelijk een lettertype verwijst dat niet op de machine is geïnstalleerd.

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

Een telling van nul betekent meestal één van de volgende zaken:

1. Alle lettertypen zijn gevonden (misschien is het lettertype *wel* lokaal geïnstalleerd), of
2. Het document bevatte geen lettertype‑verwijzingen die substitutie nodig hadden.

## Veelvoorkomende valkuilen & hoe ze te vermijden

| Valkuil | Waarom het gebeurt | Oplossing |
|---------|--------------------|-----------|
| **Geen waarschuwingen verschijnen** | Het lettertype bestaat daadwerkelijk op het systeem, of het document gebruikt alleen ingebouwde lettertypen. | Hernoem het lettertype in het bronbestand naar iets onmogelijks (bijv. `XYZ123`) en probeer het opnieuw. |
| **Te veel waarschuwingen (ruis)** | Je laadt veel documenten in een lus zonder de verzamelaar te wissen. | Instantieer `WarningInfoCollection` opnieuw voor elk document, of roep `warningCollector.Clear()` aan na verwerking. |
| **Prestatie‑impact** | Overmatig loggen naar schijf kan batchverwerking vertragen. | Buffer waarschuwingen in het geheugen en schrijf ze in bulk, of gebruik asynchrone bestands‑I/O. |
| **Ontbrekende `using Aspose.Words.Loading;`** | De `LoadOptions`‑klasse bevindt zich in deze namespace. | Voeg de ontbrekende `using`‑directive toe, zoals getoond in Stap 1. |

## De oplossing uitbreiden – Andere waarschuwings‑typen monitoren

Hoewel lettertype‑substitutie het meest zichtbaar is, kan Aspose.Words waarschuwingen geven voor:

- **Verouderde functies** (`WarningType.Deprecated`),
- **Potentieel gegevensverlies** (`WarningType.DataLoss`),
- **Niet‑ondersteunde bestandsformaten** (`WarningType.UnsupportedFileFormat`).

Je kunt het filter in Stap 3 uitbreiden om deze ook vast te leggen:

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

Op die manier monitor je niet alleen **hoe je lettertypen kunt monitoren**, maar ook **hoe je waarschuwingen kunt krijgen** voor elk scenario dat je applicatie kan tegenkomen.

## Volledig werkend voorbeeld (Klaar om te kopiëren‑plakken)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**Voer uit:** Bouw het project, voer het uit, en je zult de waarschuwingen zien afgedrukt en opgeslagen. Dat is het volledige antwoord op **hoe je waarschuwingen krijgt** en **hoe je lettertypen kunt monitoren** met Aspose.Words.

## Conclusie

Je weet nu **hoe je waarschuwingen krijgt** van Aspose.Words, specifiek voor lettertype‑substitutie‑scenario's, en je hebt geleerd **hoe je lettertypen kunt monitoren** gedurende het document‑laadproces. Door een `WarningCallback` te koppelen, de verzamelde `WarningInfo`‑objecten te itereren, en optioneel de gegevens op te slaan, krijg je volledige transparantie over ontbrekende‑lettertype‑gebeurtenissen—een essentiële mogelijkheid voor elke document‑verwerkings‑pijplijn.

Volgende stappen? Probeer het waarschuwingsfilter uit te breiden om gegevensverlies‑ of verouderde‑functie‑waarschuwingen te dekken, of integreer het JSON‑log in een monitoring‑dashboard zoals Grafana. Hetzelfde patroon werkt voor alle waarschuwings‑typen, zodat je goed uitgerust bent om elk probleem dat Aspose.Words je geeft in de gaten te houden.

Veel programmeerplezier, en moge je documenten altijd precies renderen zoals je verwacht!

<img src="font-warnings.png" alt="hoe waarschuwingen krijgen in Aspose.Words" style="max-width:100%;">

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}