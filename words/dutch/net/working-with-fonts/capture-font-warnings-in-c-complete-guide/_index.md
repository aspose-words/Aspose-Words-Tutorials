---
category: general
date: 2026-03-06
description: Leg fontwaarschuwingen vast tijdens het laden van een Word‑document in
  C#. Leer ontbrekende lettertypen detecteren, de lettertypen van het document controleren
  en ontbrekende lettertypen efficiënt afhandelen.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- load word document
- check document fonts
- handle missing fonts
language: nl
og_description: Leg fontwaarschuwingen vast tijdens het laden van een Word‑document
  in C#. Deze tutorial laat zien hoe je ontbrekende lettertypen kunt detecteren, de
  lettertypen van het document kunt controleren en ontbrekende lettertypen kunt afhandelen.
og_title: Lettertypewaarschuwingen vastleggen in C# – Volledige gids
tags:
- Aspose.Words
- C#
- Font Management
title: Lettertypewaarschuwingen vastleggen in C# – Complete gids
url: /nl/net/working-with-fonts/capture-font-warnings-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lettertypewaarschuwingen vastleggen in C# – Complete Gids

Heb je ooit **lettertypewaarschuwingen moeten vastleggen** bij het verwerken van een Word‑document? Het vastleggen van lettertypewaarschuwingen is essentieel om **ontbrekende lettertypen te detecteren** en ervoor te zorgen dat de uiteindelijke output er precies uitziet zoals je bedoeld had.  

In deze tutorial lopen we een praktisch, end‑to‑end voorbeeld door dat een `.docx`‑bestand laadt, het laadproces bewaakt en eventuele lettertype‑substituties rapporteert. Aan het einde weet je hoe je **load word document** veilig **laadt**, **documentlettertypen controleert**, en **ontbrekende lettertypen afhandelt** zonder onverwachte runtime‑fouten.

## Wat je zult leren

- Hoe je een waarschuwingcollector aan een Aspose.Words `Document` koppelt.
- Welke waarschuwingstypen een ontbrekend of vervangen lettertype aangeven.
- Manieren om die waarschuwingen te loggen of erop te reageren in een productie‑applicatie.
- Tips voor het configureren van aangepaste lettertype‑bronnen als je **ontbrekende lettertypen** op een elegante manier wilt **afhandelen**.

> **Voorvereiste:** Je hebt een geldige Aspose.Words for .NET‑licentie (of je gebruikt de gratis proefversie) en een .NET‑ontwikkelomgeving (Visual Studio, Rider, of VS Code). Er zijn geen andere bibliotheken vereist.

---

## Lettertypewaarschuwingen vastleggen – Stap‑voor‑stap

Hieronder staat de volledige, uitvoerbare code. Elke sectie is opgesplitst in een eigen stap zodat je kunt copy‑pasten, experimenteren en de logica kunt uitbreiden.

![Lettertypewaarschuwingen diagram](image.png "Diagram met waarschuwingverzameling"){: alt="lettertypewaarschuwingen diagram"}

### Stap 1: Laad het Word‑document

Eerst moeten we **load word document** dat mogelijk lettertypen bevat die niet op de huidige machine geïnstalleerd zijn. De `Document`‑constructor doet het zware werk, maar we houden de aanroep geïsoleerd zodat je later een stream of een byte‑array kunt gebruiken indien nodig.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        // 👉 Replace the path with the location of your .docx file.
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Step 1: Load the Word document.
        Document doc = LoadDocument(inputPath);

        // Step 2 and 3 are performed inside LoadDocument – see below.
    }

    /// <summary>
    /// Loads a document while attaching a warning collector.
    /// Returns the Document instance ready for further processing.
    /// </summary>
    private static Document LoadDocument(string path)
    {
        // Create the warning collector before the load.
        var warningCollector = new WarningInfoCollector();

        // Attach the collector to the document’s warning callback.
        // This ensures that any font‑related warnings are captured.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // Load the file – this is where Aspose.Words may discover missing fonts.
        tempDoc = new Document(path);

        // After loading, iterate over warnings and report them.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }
```

**Waarom dit belangrijk is:** Een document laden zonder een waarschuwinghandler betekent dat elke lettertype‑substitutie stil wordt genegeerd. Door `WarningCallback` *voor* het laden in te stellen, garanderen we dat we elke `FontSubstitution`‑waarschuwing zien die optreedt.

### Stap 2: Koppel een waarschuwingcollector

De `WarningInfoCollector`‑klasse is een ingebouwde implementatie van `IWarningCallback`. Het slaat elke waarschuwing simpelweg op in een lijst die we later kunnen inspecteren.

```csharp
    /// <summary>
    /// Scans the collected warnings and prints information about missing fonts.
    /// </summary>
    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            // We’re only interested in font‑related warnings.
            if (warning.Type == WarningType.FontSubstitution)
            {
                // warning.Description contains the original font name.
                // warning.Subtype holds the name of the font that was actually used.
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Pro tip:** Als je **ontbrekende lettertypen** agressiever wilt **afhandelen** (bijv. het laden afbreken of vervangen door een specifieke fallback), kun je `Console.WriteLine` vervangen door aangepaste logica — een uitzondering gooien, naar een bestand loggen, of zelfs een aangepaste lettertype‑bron toevoegen.

### Stap 3: Verifieer de output

Voer het programma uit vanuit een console. Als je `input.docx` een lettertype gebruikt dat niet geïnstalleerd is, zie je regels zoals:

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
```

Als er geen output verschijnt, gebruikte het document alleen lettertypen die al beschikbaar zijn **of** Aspose.Words vond een passend lettertype in zijn ingebouwde fallback‑collectie. Hoe dan ook, je hebt met succes **documentlettertypen gecontroleerd**.

## Ontbrekende lettertypen detecteren zonder licentie (gratis proefversie)

Zelfs als je de 30‑daagse proefversie gebruikt, werkt het waarschuwingsmechanisme precies hetzelfde. Het enige verschil is dat de proefversie een watermerk toevoegt aan de gegenereerde output, wat **geen** invloed heeft op het verzamelen van waarschuwingen. Zo kun je veilig **ontbrekende lettertypen detecteren** voordat je besluit een volledige licentie aan te schaffen.

## Ontbrekende lettertypen afhandelen – Geavanceerde opties

Soms wil je je eigen lettertypebestanden leveren (bijv. bedrijfs‑brandlettertypen) zodat de substitutie nooit plaatsvindt. Aspose.Words laat je aangepaste lettertype‑mappen registreren:

```csharp
// Register a folder that contains all your custom .ttf/.otf files.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
doc.FontSettings = fontSettings;
```

Plaats de bovenstaande code **voor** je het document laadt als je wilt dat de loader die lettertypen meeneemt tijdens de eerste parse‑fase. Dit is de meest betrouwbare manier om **ontbrekende lettertypen** af te handelen zonder te vertrouwen op de standaard systeemlettertypen.

## Veelvoorkomende valkuilen & hoe ze te vermijden

| Valkuil | Waarom het gebeurt | Oplossing |
|---------|--------------------|-----------|
| **Waarschuwingcollector gekoppeld na het laden** | Het document is al geparseerd, dus er worden geen waarschuwingen geregistreerd. | Koppel `WarningCallback` **voor** het aanroepen van `new Document(path)`. |
| **Alleen algemene waarschuwingen verschijnen** | Je filterde op het verkeerde `WarningType`. | Gebruik `WarningType.FontSubstitution` om je op lettertype‑problemen te richten. |
| **Geen output ondanks ontbrekende lettertypen** | Aspose.Words vond een ingebouwde fallback (bijv. Arial). | Schakel ingebouwde fallbacks uit via `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` |
| **Prestatieverlies bij het scannen van grote documenten** | Het verzamelen van elke waarschuwing kan duur zijn. | Beperk de verzameling tot alleen `FontSubstitution`, of verwerk waarschuwingen in batches. |

## Volledig werkend voorbeeld (klaar om te copy‑pasten)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Load the document and capture any font warnings.
        Document doc = LoadDocument(inputPath);

        // At this point you can continue processing the document,
        // knowing that you’ve already reported any missing fonts.
        Console.WriteLine("Document loaded successfully.");
    }

    private static Document LoadDocument(string path)
    {
        var warningCollector = new WarningInfoCollector();

        // IMPORTANT: set the callback BEFORE the load.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // OPTIONAL: register custom font folder to reduce substitutions.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
        tempDoc.FontSettings = fontSettings;

        // Load the document – this triggers warning collection.
        tempDoc = new Document(path);

        // Report any font substitutions.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }

    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Verwachte console‑output** (ervan uitgaande dat er twee ontbrekende lettertypen zijn):

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
Document loaded successfully.
```

Als de console stil blijft behalve “Document loaded successfully,” heb je **documentlettertypen gecontroleerd** en geen ontbrekende gevonden.

## Conclusie

We hebben je laten zien hoe je **lettertypewaarschuwingen kunt vastleggen** in C# met Aspose.Words, een betrouwbare manier om **ontbrekende lettertypen te detecteren**, **load word document** veilig te **laden**, **documentlettertypen te controleren**, en **ontbrekende lettertypen** af te handelen via aangepaste lettertype‑bronnen.  

Met dit patroon kun je lettertype‑validatie integreren in elke automatiserings‑pipeline — of je nu PDF’s genereert, converteert naar HTML, of simpelweg Word‑bestanden archiveert.

### Wat is het volgende?

- Verken de **FontSettings.SubstitutionSettings**‑API om je eigen fallback‑regels te definiëren.
- Combineer het verzamelen van waarschuwingen met een logging‑framework (Serilog, NLog) voor productie‑monitoring.
- Gebruik dezelfde aanpak om andere waarschuwingstypen vast te leggen, zoals beeldresolutie of niet‑ondersteunde functies.

Heb je meer vragen over lettertype‑afhandeling of Aspose.Words in het algemeen? Laat een reactie achter of ga naar de Aspose‑communityforums. Veel plezier met coderen, en moge je documenten altijd weergeven met de lettertypen die je verwacht!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}