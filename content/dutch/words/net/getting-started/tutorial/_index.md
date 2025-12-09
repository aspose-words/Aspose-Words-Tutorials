---
language: nl
url: /dutch/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# Ontdek Ontbrekende Lettertypen in Aspose.Words Documenten – Complete C# Gids

Heb je je ooit afgevraagd hoe je **ontbrekende lettertypen** kunt **detecteren** wanneer je een Word‑bestand laadt met Aspose.Words? In mijn dagelijkse werk ben ik een paar PDF's tegengekomen die er niet goed uitzagen omdat het oorspronkelijke document een lettertype gebruikte dat ik niet geïnstalleerd had. Het goede nieuws? Aspose.Words kan je precies vertellen wanneer het een lettertype vervangt, en je kunt die informatie vastleggen met een eenvoudige warning‑callback.  

In deze tutorial lopen we een **volledig, uitvoerbaar voorbeeld** door dat laat zien hoe je elke lettertype‑vervanging logt, waarom de callback belangrijk is, en een paar extra trucjes voor robuuste detectie van ontbrekende lettertypen. Geen poespas, alleen de code en de redenering die je nodig hebt om het vandaag werkend te krijgen.

---

## Wat je zult leren

- Hoe je een **Aspose.Words warning callback** implementeert om font‑substitutie‑gebeurtenissen op te vangen.  
- Hoe je **LoadOptions C#** configureert zodat de callback wordt aangeroepen tijdens het laden van een document.  
- Hoe je verifieert dat de detectie van ontbrekende lettertypen echt werkt, en hoe de console‑output eruitziet.  
- Optionele aanpassingen voor grote batches of headless omgevingen.  

**Prerequisites** – Je hebt een recente versie van Aspose.Words voor .NET nodig (de code is getest met 23.12), .NET 6 of later, en een basisbegrip van C#. Als je die hebt, kun je van start.

---

## Detecteer Ontbrekende Lettertypen met een Warning Callback

Het hart van de oplossing is een implementatie van `IWarningCallback`. Aspose.Words genereert een `WarningInfo`‑object voor veel situaties, maar we zijn alleen geïnteresseerd in `WarningType.FontSubstitution`. Laten we zien hoe we hierop kunnen inhaken.

### Stap 1: Maak een Font‑Warning Collector

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*Waarom dit belangrijk is*: Door te filteren op `WarningType.FontSubstitution` vermijden we rommel van niet‑gerelateerde waarschuwingen (zoals verouderde functies). De `info.Description` bevat al de oorspronkelijke lettertype‑naam en de gebruikte fallback, waardoor je een duidelijk audit‑pad hebt.

---

## Configureer LoadOptions om de Callback te Gebruiken

Nu vertellen we Aspose.Words om onze collector te gebruiken wanneer het een bestand laadt.

### Stap 2: Stel LoadOptions In

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*Waarom dit belangrijk is*: `LoadOptions` is de enige plek waar je de callback, encryptiewachtwoorden en andere laad‑gedragingen kunt aansluiten. Het gescheiden houden van de `Document`‑constructor maakt de code herbruikbaar voor vele bestanden.

---

## Laad het Document en Leg Ontbrekende Lettertypen Vast

Met de callback aangesloten is de volgende stap simpelweg het document laden.

### Stap 3: Laad je DOCX (of elk ondersteund formaat)

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

Wanneer de `Document`‑constructor het bestand parseert, triggert elk ontbrekend lettertype onze `FontWarningCollector`. De console toont regels zoals:

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

Die regel is het concrete bewijs dat **ontbrekende lettertypen detecteren** heeft gewerkt.

---

## Verifieer de Output – Wat te Verwachten

Voer het programma uit vanuit een terminal of Visual Studio. Als het bron‑document een lettertype bevat dat je niet geïnstalleerd hebt, zie je minstens één regel “Font substituted”. Als het document alleen geïnstalleerde lettertypen gebruikt, blijft de callback stil en krijg je alleen het bericht “Document loaded successfully.”.

**Tip**: Om dubbel te controleren, open het Word‑bestand in Microsoft Word en bekijk de lettertype‑lijst. Elk lettertype dat verschijnt in *Replace Fonts* onder de *Home → Font*‑groep is een kandidaat voor substitutie.

---

## Geavanceerd: Detecteer Ontbrekende Lettertypen in Bulk

Vaak moet je tientallen bestanden scannen. Hetzelfde patroon schaalt mooi:

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

Omdat de `FontWarningCollector` elke keer dat hij wordt aangeroepen naar de console schrijft, krijg je een per‑bestand rapport zonder extra infrastructuur. Voor productiescenario's wil je misschien naar een bestand of een database loggen – vervang simpelweg `Console.WriteLine` door je voorkeurslogger.

---

## Veelvoorkomende Valkuilen & Pro‑Tips

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **Geen waarschuwingen verschijnen** | Het document bevat in feite alleen geïnstalleerde lettertypen. | Controleer door het bestand in Word te openen of door opzettelijk een lettertype van je systeem te verwijderen. |
| **Callback niet aangeroepen** | `LoadOptions.WarningCallback` was nooit toegewezen of er later een nieuw `LoadOptions`‑object werd gebruikt. | Bewaar één `LoadOptions`‑object en hergebruik het voor elke load. |
| **Te veel niet‑gerelateerde waarschuwingen** | Je filterde niet op `WarningType.FontSubstitution`. | Voeg de `if (info.Type == WarningType.FontSubstitution)`‑guard toe zoals getoond. |
| **Prestatie‑vertraging bij enorme bestanden** | De callback wordt uitgevoerd bij elke waarschuwing, wat er veel kan zijn voor grote documenten. | Schakel andere waarschuwingstypen uit via `LoadOptions.WarningCallback` of stel `LoadOptions.LoadFormat` in op een specifiek type als je dat weet. |

---

## Volledig Werkend Voorbeeld (Klaar om te Kopiëren‑Plakken)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Verwachte console‑output** (wanneer een ontbrekend lettertype wordt aangetroffen):

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

Als er geen substitutie plaatsvindt, zie je alleen de succesregel.

---

## Conclusie

Je hebt nu een **volledige, productie‑klare manier om ontbrekende lettertypen te detecteren** in elk document dat door Aspose.Words wordt verwerkt. Door gebruik te maken van de **Aspose.Words warning callback** en het configureren van **LoadOptions C#**, kun je elke lettertype‑substitutie loggen, lay‑outproblemen oplossen en ervoor zorgen dat je PDF's de beoogde uitstraling behouden.  

Van één enkel bestand tot een enorme batch, het patroon blijft hetzelfde—implementeer `IWarningCallback`, sluit het aan op `LoadOptions`, en laat Aspose.Words het zware werk doen.  

Klaar voor de volgende stap? Probeer dit te combineren met **font embedding** of **fallback font families** om het probleem automatisch op te lossen, of verken de **DocumentVisitor**‑API voor diepere inhoudsanalyse. Veel plezier met coderen, en moge al je lettertypen blijven waar je ze verwacht!  

---

![Detect missing fonts in Aspose.Words – console output screenshot](https://example.com/images/detect-missing-fonts.png "detect missing fonts console output")

{{< layout-end >}}

{{< layout-end >}}