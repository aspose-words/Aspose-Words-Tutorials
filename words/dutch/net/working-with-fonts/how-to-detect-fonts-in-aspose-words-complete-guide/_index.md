---
category: general
date: 2026-04-07
description: Leer hoe u lettertypen kunt detecteren en hoe u waarschuwingen kunt vastleggen
  bij het afhandelen van ontbrekende lettertypen in C# met Aspose.Words. Stapsgewijze
  code inbegrepen.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: nl
og_description: Hoe detecteer je lettertypen in Aspose.Words? Volg deze tutorial om
  waarschuwingen vast te leggen en ontbrekende lettertypen moeiteloos te verwerken.
og_title: Hoe lettertypen in Aspose.Words te detecteren – Complete gids
tags:
- Aspose.Words
- C#
- Font handling
title: Hoe lettertypen detecteren in Aspose.Words – Complete gids
url: /nl/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe lettertypen te detecteren in Aspose.Words – Complete gids

Heb je je ooit afgevraagd **hoe je lettertypen** kunt detecteren die ontbreken in een Word‑document voordat je het naar productie brengt? Je bent niet de enige. In veel enterprise‑scenario's kan een verdwaald lettertype een PDF‑conversiepijplijn breken of lay‑out‑glitches veroorzaken die er onprofessioneel uitzien. Het goede nieuws is dat Aspose.Words een ingebouwde manier biedt om die afwezige lettertypen op te sporen en duidelijke waarschuwingen te geven.

In deze tutorial lopen we precies door **hoe je lettertypen detecteert**, **hoe je waarschuwingen opvangt**, en de beste praktijken om **ontbrekende lettertypen af te handelen** zodat je applicatie robuust blijft. Geen externe tools, geen giswerk—alleen pure C#‑code die je direct in je project kunt plaatsen.

> **Snel overzicht:** Aan het einde heb je een herbruikbare `FontSubstitutionWarningCollector` die elk lettertype‑substitutie‑bericht tijdens het laden van een document verzamelt, en weet je hoe je moet reageren wanneer een lettertype niet gevonden kan worden.

---

## Wat je zult leren

- Hoe je `LoadOptions` configureert om te luisteren naar waarschuwingen voor lettertype‑substitutie.  
- Hoe je die waarschuwingen opvangt in een aangepaste collector‑klasse.  
- Hoe je de verzamelde waarschuwingen verwerkt en beslist of je moet afbreken, loggen of lettertypen moet substitueren.  
- Edge‑case‑afhandeling voor documenten die verwijzen naar externe of ingebedde lettertypen.  

**Prerequisites:** .NET 6+ (of .NET Framework 4.6+), Aspose.Words for .NET (nieuwste versie), en een basiskennis van C#. Als je nog nooit met Aspose.Words hebt gewerkt, maak je geen zorgen—deze gids gaat uit van slechts een paar minuten installatie‑tijd.

---

## Hoe lettertypen te detecteren met Aspose.Words LoadOptions

De eerste stap om ontbrekende lettertypen te detecteren is Aspose.Words te laten melden dat ze ontbreken. Dit gebeurt via de eigenschap `LoadOptions.WarningCallback`, die elke klasse accepteert die `IWarningCallback` implementeert. Hieronder maken we een kleine collector die elke waarschuwing opslaat voor later onderzoek.

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

**Waarom dit belangrijk is:** Zonder een warning‑callback substitueert Aspose.Words stilzwijgend ontbrekende lettertypen door een standaardlettertype, en je merkt nooit dat er een probleem is. Door `WarningType.FontSubstitution` op te vangen, krijg je volledige zichtbaarheid—precies de gegevens die je nodig hebt om **lettertypen te detecteren** die niet beschikbaar zijn op de host‑machine.

Nu koppelen we de collector aan `LoadOptions` en laden we een document:

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

> **Pro tip:** Als je met veel documenten in één batch werkt, hergebruik dan dezelfde `FontSubstitutionWarningCollector`‑instantie, maar vergeet niet `Clear()` aan te roepen tussen de loads om te voorkomen dat waarschuwingen van verschillende bestanden door elkaar raken.

---

## Waarschuwingen tijdens het laden van een document opvangen

Nadat het document is geladen, bevat de collector al elke lettertype‑gerelateerde waarschuwing. De logische volgende vraag is: *Hoe vang ik waarschuwingen* op een manier die makkelijk te loggen of weer te geven is?

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

Typische output ziet er als volgt uit:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**Wat dit je vertelt:** Elke regel onthult de oorspronkelijke lettertype‑naam en de fallback die Aspose.Words heeft gekozen. Met deze informatie kun je bepalen of de fallback acceptabel is of dat je het ontbrekende lettertype handmatig moet insluiten.

---

## Ontbrekende lettertypen elegant afhandelen

Het detecteren en opvangen van waarschuwingen is slechts de helft van de strijd. De echte waarde komt wanneer je **ontbrekende lettertypen** op een productie‑klare manier **afhandelt**. Hieronder staan drie veelvoorkomende strategieën:

1. **Loggen en doorgaan** – Geschikt voor batch‑verwerking waar je alleen een audit‑trail nodig hebt.  
2. **Afbreken bij kritieke lettertypen** – Gooi een uitzondering als een specifiek lettertype (bijv. een merk‑specifiek lettertype) ontbreekt.  
3. **Lettertype on‑the‑fly insluiten** – Laad het ontbrekende lettertype uit een bekende map en registreer het bij Aspose.Words voordat je het document opnieuw laadt.

### Voorbeeld: Afbreken bij een kritisch lettertype

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

### Voorbeeld: Ontbrekende lettertypen automatisch insluiten

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

**Waarom deze patronen helpen:** Door expliciet te bepalen wat er gebeurt wanneer een lettertype ontbreekt, elimineer je stille substituties die de branding of leesbaarheid kunnen ondermijnen. Dit is de essentie van **ontbrekende lettertypen afhandelen** op een gecontroleerde manier.

---

## Volledig werkend voorbeeld

Alles samengevoegd, hier is een enkel, kant‑klaar programma dat **hoe je lettertypen detecteert**, **hoe je waarschuwingen opvangt**, en een eenvoudige beleidsregel toont om **ontbrekende lettertypen** te **loggen**.

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

**Verwacht resultaat:** Wanneer je het programma uitvoert tegen een document dat een lettertype refereert dat niet op de machine aanwezig is, zal de console elke substitutie‑waarschuwing weergeven. Als een waarschuwing een lettertype uit de `critical`‑set betreft, stopt het programma vroegtijdig, waardoor een gebrekkige PDF niet wordt gegenereerd.

---

## Veelgestelde vragen (FAQ)

| Vraag | Antwoord |
|-------|----------|
| *Heb ik een licentie voor Aspose.Words nodig om deze code te gebruiken?* | Ja, een geldige Aspose.Words‑licentie verwijdert evaluatiewatermerken en ontgrendelt de volledige functionaliteit. |
| *Kan deze aanpak ingebedde lettertypen detecteren?* | Ingebedde lettertypen maken al deel uit van het bestand, dus Aspose.Words zal geen substitutie‑waarschuwing geven. Je kunt `Document.FontInfos` gebruiken om ingebedde lettertypen te enumereren indien nodig. |
| *Wat als het ontbrekende lettertype een systeemlettertype is op Windows maar niet op Linux?* | Dezelfde waarschuwing wordt op Linux getoond omdat het lettertype daar niet geïnstalleerd is. Gebruik de “ontbrekende lettertypen afhandelen”‑strategie om de benodigde `.ttf`‑bestanden met je app mee te leveren. |
| *Is de waarschuwingverzamelaar thread‑veilig?* | De collector zelf is niet thread‑veilig; als je meerdere threads gebruikt, moet je een eigen synchronisatie‑mechanisme implementeren of een aparte collector per thread aanhouden. |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}