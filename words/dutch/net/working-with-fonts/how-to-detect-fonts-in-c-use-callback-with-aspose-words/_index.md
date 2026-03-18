---
category: general
date: 2026-03-17
description: Hoe lettertypen te detecteren in C# met Aspose.Words en een waarschuwingscallback.
  Leer hoe je de callback kunt gebruiken om missende lettertypevervangingen vast te
  leggen tijdens het laden van documenten.
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: nl
og_description: Hoe lettertypen te detecteren in C# met Aspose.Words. Deze gids laat
  zien hoe je een callback gebruikt om waarschuwingen voor ontbrekende lettertypen
  vast te leggen tijdens het laden van een document.
og_title: Hoe lettertypen detecteren in C# – Gebruik een callback met Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Hoe lettertypen detecteren in C# – Gebruik een callback met Aspose.Words
url: /nl/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

and title.

Proceed.

Let's produce final content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe lettertypen detecteren in C# – Gebruik een callback met Aspose.Words

Heb je ooit **hoe lettertypen te detecteren** in een Word‑document programmatically nodig gehad en je afgevraagd waarom sommige tekens er vreemd uitzien na conversie? Je bent niet de enige. In veel real‑world projecten—factuurgeneratoren, rapport‑exporteurs of batch‑verwerkings‑pipelines—veroorzaken ontbrekende lettertypen stille lay‑out‑glitches die moeilijk te debuggen zijn.  

Het goede nieuws? Aspose.Words biedt een nette manier om die problemen zichtbaar te maken met een waarschuwing‑callback. In deze tutorial zie je **hoe je een callback gebruikt** om elke lettertype‑substitutie die Aspose uitvoert tijdens het laden van een document vast te leggen, en je krijgt een kant‑klaar voorbeeld dat een duidelijk rapport van ontbrekende lettertypen afdrukt.

We behandelen:

* De minimale vereisten (een .NET‑project en het Aspose.Words NuGet‑pakket).  
* Hoe je `IWarningCallback` implementeert om te luisteren naar `WarningType.FontSubstitution`.  
* Hoe je de callback koppelt aan `LoadOptions` en een document laadt.  
* Hoe de output eruitziet, plus een paar praktische tips voor productiecodel.

Aan het einde kun je automatisch **lettertypen detecteren** in elk DOCX, DOC of RTF‑bestand en actie ondernemen op basis van ontbrekende‑lettertype‑informatie—of dat nu betekent loggen, een gebruiker waarschuwen, of een fallback‑lettertype gebruiken.

---

![Hoe lettertypen detecteren in een Word‑document met Aspose.Words waarschuwing‑callback](https://example.com/images/detect-fonts.png "hoe lettertypen detecteren in een Word‑document")

## Wat je nodig hebt

* **.NET 6.0** of later (het voorbeeld compileert ook met .NET Framework 4.6+).  
* **Aspose.Words for .NET** – installeer via NuGet: `Install-Package Aspose.Words`.  
* Een voorbeeld‑Word‑bestand dat bewust een lettertype verwijst dat je niet geïnstalleerd hebt (bijv. `MissingFont.docx`).  

Er zijn geen extra bibliotheken nodig; alles zit binnen de Aspose‑namespace.

---

## Hoe lettertypen detecteren met een waarschuwing‑callback

### Stap 1: Maak een warning‑callback klasse

De callback implementeert `IWarningCallback`. Wanneer Aspose.Words een lettertype tegenkomt dat het niet kan vinden, genereert het een `WarningInfo` met `WarningType.FontSubstitution`. Onze klasse schrijft simpelweg een vriendelijke regel naar de console.

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**Waarom dit belangrijk is:** Door te filteren op `WarningType.FontSubstitution` vermijden we storende waarschuwingen (zoals verouderde functies) en houden we de log gefocust op het exacte probleem dat je wilt oplossen—**het detecteren van lettertypen** die niet op de machine aanwezig zijn.

---

### Stap 2: Koppel de callback aan `LoadOptions`

`LoadOptions` laat je aanpassen hoe een document wordt geparseerd. Door onze `FontWarningCollector` toe te wijzen aan de eigenschap `WarningCallback`, vertel je Aspose om deze aan te roepen telkens er een ontbrekend lettertype wordt aangetroffen.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Tip:** Je kunt hier ook `LoadOptions.FontSettings` instellen als je programmatisch een fallback‑lettertype wilt opgeven. Dat is een geavanceerd scenario dat we later kort noemen.

---

### Stap 3: Laad het document en bekijk de output

Nu laden we het bestand daadwerkelijk. Zodra Aspose het document parseert, triggert elk niet‑gevonden lettertype onze callback.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**Verwachte console‑output** (ervan uitgaande dat het document *Comic Sans MS* refereert, wat niet geïnstalleerd is):

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

Als het document meerdere ontbrekende lettertypen bevat, zie je één regel per lettertype—precies de **hoe lettertypen te detecteren**‑informatie die je nodig hebt.

---

## Hoe de callback gebruiken voor complexere scenario's

### Loggen naar een bestand in plaats van de console

In productie wil je waarschijnlijk een persistente log. Vervang `Console.WriteLine` door een `StreamWriter`:

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### Waarschuwingen verzamelen voor latere analyse

Soms heb je de lijst met ontbrekende lettertypen nodig nadat het document is geladen, bijvoorbeeld om een UI‑dialoog te tonen. Sla de waarschuwingen op in een `List<string>` en maak deze beschikbaar:

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### Een fallback‑lettertype programmatisch aanbieden

Als je een bedrijfslettertype wilt afdwingen, kun je dit toevoegen aan `FontSettings` vóór het laden:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

Nu vervangt Aspose ontbrekende lettertypen door *Arial Unicode MS* terwijl het nog steeds de substitutie rapporteert via de callback. Dit is een handige manier om **hoe een callback te gebruiken** voor zowel detectie als automatische remediering.

---

## Veelvoorkomende valkuilen en pro‑tips

| Valkuil | Waarom het gebeurt | Hoe te vermijden |
|--------|-------------------|------------------|
| **Vergeten `Aspose.Words.Warnings` te refereren** | De `IWarningCallback`‑interface zit daar. | Voeg `using Aspose.Words.Warnings;` toe bovenaan. |
| **Een document laden zonder `LoadOptions`** | De standaardloader vervangt stilletjes lettertypen zonder melding. | Maak altijd een `LoadOptions`‑instantie en wijs je callback toe. |
| **Uitvoeren op een server met beperkte rechten** | Schrijven naar een logbestand kan `UnauthorizedAccessException` veroorzaken. | Gebruik een schrijfbare map (bijv. de app‑data‑directory) of blijf bij in‑memory collecties. |
| **Meerdere threads delen dezelfde collector** | `FontWarningCollector` is standaard niet thread‑safe. | Maak per thread een aparte collector of bescherm de lijst met een lock. |
| **Aannemen dat de callback afgaat voor ingesloten lettertypen** | Ingesloten lettertypen zijn al aanwezig in het document; er wordt geen waarschuwing gegeven. | Als je de integriteit van ingesloten lettertypen wilt controleren, inspecteer `FontInfo` via `FontSettings`. |

---

## Volledig werkend voorbeeld (Kopieer‑en‑plak klaar)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Wat je zou moeten zien** (ervan uitgaande dat het bestand twee afwezige lettertypen refereert):

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

Als het bestand alleen geïnstalleerde lettertypen gebruikt, print de console simpelweg:

```
Document loaded successfully.

No missing fonts detected.
```

---

## Afronding

We hebben stap voor stap **hoe lettertypen te detecteren** in een Word‑document laten zien door een aangepaste waarschuwing‑callback te koppelen aan Aspose.Words. Deze aanpak is lichtgewicht, vereist

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}