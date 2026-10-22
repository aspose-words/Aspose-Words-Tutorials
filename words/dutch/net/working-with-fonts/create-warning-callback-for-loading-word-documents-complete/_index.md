---
category: general
date: 2026-03-25
description: Maak een waarschuwingscallback om een Word‑document te laden en ontbrekende
  lettertypen te detecteren. Leer hoe u lettertype‑instellingen configureert in Aspose.Words
  voor .NET.
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: nl
og_description: Maak een waarschuwingscallback om een Word‑document te laden terwijl
  ontbrekende lettertypen worden gedetecteerd. Deze gids laat zien hoe u lettertype‑instellingen
  configureert in Aspose.Words.
og_title: Maak waarschuwingscallback – Laad Word‑document & detecteer ontbrekende
  lettertypen
tags:
- Aspose.Words
- C#
- Font handling
title: Maak een waarschuwingscallback voor het laden van Word‑documenten – Complete
  gids
url: /nl/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Waarschuwingscallback maken – Word-document laden & ontbrekende lettertypen detecteren

Heb je ooit een **create warning callback** moeten maken bij het laden van een Word-document en je afgevraagd waarom sommige lettertypen gewoon verdwijnen? Je bent niet de enige. In veel bedrijfsapplicaties veroorzaken ontbrekende lettertypen catastrofale lay‑outproblemen, en zonder een juiste callback merk je het probleem misschien nooit.

Het goede nieuws? Met Aspose.Words voor .NET kun je **load Word document**, **detect missing fonts** en **configure font settings** allemaal in een paar nette code‑regels. In deze tutorial lopen we een volledig, uitvoerbaar voorbeeld door, leggen we uit waarom elk onderdeel belangrijk is, en laten we je zien hoe je kunt verifiëren dat de waarschuwingscallback zijn werk doet.

> **Wat je mee krijgt**  
> * Een volledig C#‑programma dat een DOCX laadt, eventuele lettertype‑substituties rapporteert, en je in staat stelt de zoekpaden voor lettertypen aan te passen.  
> * Begrip van de `FontSettings`, `LoadOptions` en `IWarningCallback` klassen.  
> * Tips voor het omgaan met randgevallen zoals ingebedde lettertypen of systeem‑brede lettertype‑mappen.

---

## Vereisten

- .NET 6+ (of .NET Framework 4.7.2+) met een C#‑compiler.  
- Aspose.Words for .NET NuGet‑pakket (`Install-Package Aspose.Words`).  
- Een voorbeeld‑Word‑bestand (`input.docx`) dat minstens één lettertype gebruikt dat niet op de machine geïnstalleerd is (bijv. *Calibri Light* in een minimale Windows‑container).  
- Basiskennis van C#‑console‑apps.

Er zijn geen extra bibliotheken nodig; alles zit binnen Aspose.Words.

---

## Stap 1: Maak waarschuwingscallback om ontbrekende lettertypen te detecteren

Het **primary** onderdeel van deze puzzel is een klasse die `IWarningCallback` implementeert. Aspose.Words roept deze callback aan telkens wanneer het een situatie tegenkomt die een waarschuwing rechtvaardigt – lettertype‑substitutie is het meest voorkomende.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Why this matters** – Zonder een callback zou je achteraf door de logs moeten zoeken. Door waarschuwingen in realtime af te handelen kun je beslissen of je het laden wilt afbreken, het ontbrekende lettertype wilt vervangen door een alternatief, of het probleem simpelweg wilt loggen voor later onderzoek.

## Stap 2: FontSettings configureren voor aangepaste lettertype‑afhandeling

Voordat we het document daadwerkelijk laden, willen we Aspose.Words laten weten waar het moet zoeken naar lettertypen die niet op het systeem aanwezig zijn. Daar komt `FontSettings` om de hoek kijken.

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**Why this matters** – Door Aspose.Words te wijzen naar een map die de ontbrekende lettertypen bevat, kun je vaak substitutie volledig voorkomen. Wanneer dat niet mogelijk is, zorgt een verstandige standaard (zoals *Arial*) ervoor dat het document leesbaar blijft.

## Stap 3: Word-document laden met de geconfigureerde waarschuwingscallback

Nu koppelen we alles samen: we maken `LoadOptions`, voegen onze `FontSettings` en `FontWarningHandler` toe, en laden tenslotte het document.

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**Why this matters** – `LoadOptions` is de enige plek waar je configureert *hoe* een document wordt gelezen. Door zowel de lettertype‑configuratie als de waarschuwingscallback te leveren, zorgen we ervoor dat elk ontbrekend lettertype zowel op de juiste plaatsen wordt gezocht **en** onmiddellijk wordt gerapporteerd.

## Stap 4: Verifieer de output – wat zou je moeten zien?

Voer het programma uit vanuit een console. Als `input.docx` een lettertype gebruikt dat niet geïnstalleerd is en ook niet in `C:\SharedFonts` staat, zie je iets als:

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

Als alle lettertypen beschikbaar zijn, verschijnt de waarschuwingsregel simpelweg nooit. Deze directe feedbacklus is van onschatbare waarde tijdens geautomatiseerde documentverwerkings‑pipelines waar stille lettertype‑wisselingen de merkrichtlijnen kunnen breken.

## Stap 5: Veelvoorkomende valkuilen en best‑practice tips

| Valkuil | Hoe te vermijden |
|---------|-----------------|
| **Vergeten `Aspose.Words.Fonts` te refereren** | Zorg ervoor dat je bovenaan `using Aspose.Words.Fonts;` hebt staan; anders zal de compiler klagen over ontbrekende types. |
| **Pad naar lettertype‑map is onjuist** | Controleer het pad dubbel en stel `recursive: true` in als je sub‑mappen hebt. Gebruik `Path.GetFullPath` om te debuggen. |
| **Meerdere waarschuwingscallbacks** | Aspose.Words respecteert alleen de laatste `WarningCallback` die je toewijst. Houd één handler die delegeert als je complexere logica nodig hebt. |
| **Uitvoeren op een server zonder UI** | Console‑writes zijn prima, maar voor web‑apps wil je misschien loggen naar een bestand of monitoringsysteem in plaats van `Console.WriteLine`. |
| **Grote documenten veroorzaken prestatieverlies** | Herbruik een enkele `FontSettings`‑instantie over meerdere loads; deze telkens opnieuw aanmaken kan kostbaar zijn. |

**Pro tip:** Als je waarschuwingen wilt *verzamelen* voor latere analyse, sla ze dan op in een `List<string>` binnen de handler in plaats van direct af te drukken.

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Je kunt vervolgens `handler.Messages` inspecteren na het laden van het document.

## Stap 6: De oplossing uitbreiden – wat als ik een fallback‑lettertype moet insluiten?

Soms wil je dat het ontbrekende lettertype *ingesloten* wordt in de output‑PDF zodat downstream‑viewers de exacte weergave zien. Na het laden van het document kun je insluiten forceren:

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

Dit fragment toont hoe dezelfde **configure font settings** aanpak kan worden uitgebreid voorbij alleen het laden.

## Volledig uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren‑plakken in een nieuw Console‑App‑project. Het bevat alle hierboven besproken onderdelen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**Expected output** (wanneer een ontbrekend lettertype aanwezig is):

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

Als er geen substitutie plaatsvindt, verschijnen alleen de succesberichten.

## Conclusie

We hebben zojuist een **created warning callback** gemaakt die betrouwbaar **detects missing fonts** tijdens het **loading a Word document** met Aspose.Words, en we hebben laten zien hoe je **configure font settings** kunt gebruiken om te bepalen waar de bibliotheek naar lettertypen zoekt en welke fallback te gebruiken. Door `FontSettings` en `LoadOptions` te koppelen, krijg je volledige zichtbaarheid op lettertype‑gerelateerde problemen—geen stille lay‑out‑fouten meer.

Volgende stappen? Probeer de `FontWarningHandler` te vervangen door een logger die naar een database schrijft, of experimenteer met **font substitution rules** om specifieke ontbrekende lettertypen te koppelen aan merk‑goedgekeurde alternatieven. Je kunt ook **dynamic font loading** vanuit cloud‑opslag verkennen als je app in een gecontaineriseerde omgeving draait.

Heb je vragen over een specifiek randgeval—zoals het omgaan met OpenType‑features of versleutelde DOCX‑bestanden? Laat een reactie achter hieronder, en happy coding!  

---

![Create warning callback diagram](https://example.com/images/create-warning-callback.png "Create warning callback diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}