---
category: general
date: 2025-12-31
description: Leg lettertypewaarschuwingen vast in Aspose.Words om ontbrekende lettertypen
  te detecteren en lijst ontbrekende lettertypen op in uw .NET‑app. Leer een stapsgewijze
  C#‑oplossing.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: nl
og_description: Vang fontwaarschuwingen in Aspose.Words op om ontbrekende lettertypen
  te detecteren en een lijst met ontbrekende lettertypen te tonen. Complete C#‑gids
  met code en tips.
og_title: Lettertypewaarschuwingen vastleggen – Detecteer en lijst ontbrekende lettertypen
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: Lettertypewaarschuwingen vastleggen – Detecteer en lijst ontbrekende lettertypen
url: /nl/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Fontwaarschuwingen vastleggen – Ontdek & lijst ontbrekende lettertypen

Heb je ooit **fontwaarschuwingen moeten vastleggen** bij het laden van een Word‑document, maar wist je niet hoe je de details van ontbrekende lettertypen kon tonen? Je bent niet de enige. In veel praktijkprojecten veroorzaken ontbrekende lettertypen lay‑outproblemen, en zonder juiste waarschuwingen achtervolg je spook‑bugs.  

In deze tutorial laten we je zien hoe je **ontbrekende lettertypen kunt detecteren** en **ontbrekende lettertypen kunt lijst​en** met Aspose.Words voor .NET. Aan het einde heb je een kant‑klaar C#‑fragment dat elke substitutiewaarschuwing afdrukt, zodat je kunt loggen, alarmeren of zelfs lettertypen automatisch kunt vervangen.

---

## Waarom het vastleggen van fontwaarschuwingen belangrijk is

Wanneer Aspose.Words een DOCX opent die verwijst naar een lettertype dat niet op de server is geïnstalleerd, vervangt het stilletjes door een fallback. Het document ziet er goed uit, maar de visuele getrouwheid is aangetast – denk aan een bedrijfslogo dat in het verkeerde lettertype wordt weergegeven.  

Het vastleggen van die waarschuwingen stelt je in staat om:

* **Merkconsistentie te behouden** – je weet precies welke lettertypen ontbreken.
* **Remediatie te automatiseren** – ontbrekende lettertypen programmatically vervangen.
* **Naleving te auditen** – rapporten genereren voor juridische of design‑reviews.

Kortom, **fontwaarschuwingen vastleggen** is de eerste verdedigingslinie tegen stille lettertype‑substitutie.

---

## LoadOptions instellen om ontbrekende lettertypen te detecteren

De sleutel tot het tonen van waarschuwingen is de eigenschap `LoadOptions.FontSubstitutionWarning`. Standaard staat deze op `None`, waardoor Aspose.Words de berichten opslokt. Door deze op `All` te zetten, vertelt je de bibliotheek elk substitutie‑event te registreren.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **Pro tip:** Als je al een aangepaste lettertype‑map hebt, wijs die dan toe aan `FontSettings.SetFontsFolder("path")` voordat je het document laadt. Zo kun je **ontbrekende lettertypen detecteren** die niet in de systeemdirectory staan.

---

## Het document laden en ontbrekende lettertypen lijst​en

Nu de `LoadOptions` klaar zijn, is de volgende stap het Word‑bestand te laden. De constructor accepteert het opties‑object, en elke substitutie wordt vastgelegd in de `WarningInfoCollection` van het document.

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

Als het bestand verwijst naar lettertypen die niet beschikbaar zijn, genereert elk ontbrekend lettertype een `WarningInfo`‑item. Je kunt **ontbrekende lettertypen lijst​en** door over die collectie te itereren.

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

Typische uitvoer ziet er als volgt uit:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Elke regel vertelt je precies welk lettertype ontbrak, waardoor aan de **list missing fonts**‑vereiste wordt voldaan.

---

## De WarningInfoCollection lezen en interpreteren

De `WarningInfoCollection` kan verschillende waarschuwings‑types bevatten (bijv. `DocumentStructure`, `ImageLoading`). Om je alleen op lettertype‑problemen richten, filter je op `WarningType.FontSubstitution`.

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

Waarom filteren? Omdat een groot document ook waarschuwingen kan genereren over corrupte afbeeldingen of niet‑ondersteunde functies. Door de collectie te beperken, vermijd je ruis en houd je de **capture font warnings**‑output overzichtelijk.

---

## Volledig werkend voorbeeld – Fontwaarschuwingen in actie

Hieronder vind je het complete, zelfstandige programma dat je in elk .NET‑console‑project kunt plaatsen. Het demonstreert elke stap, van het configureren van `LoadOptions` tot het afdrukken van een nette lijst met ontbrekende lettertypen.

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**Verwachte console‑output**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Als het document geen ontbrekende lettertypen bevat, zie je:

```
All referenced fonts are available – no warnings captured.
```

---

## Veelvoorkomende randgevallen & hoe ze op te lossen

| Situatie | Waarom het gebeurt | Aanbevolen oplossing |
|-----------|----------------|-----------------|
| **Document gebruikt een ingebed OpenType‑lettertype** | Aspose.Words kan ingebedde lettertypen lezen, maar alleen als het bestand niet corrupt is. | Controleer het DOCX eerst in Word; embed het lettertype opnieuw indien nodig. |
| **Grote hoeveelheid waarschuwingen** (bijv. 200+ ontbrekende lettertypen) | Bulk‑importen uit legacy‑systemen verwijzen vaak naar een breed scala aan lettertypen. | Verwerk de waarschuwingen in batches: sla ze op in een database en voer daarna een lettertype‑installatiescript uit. |
| **WarningInfoCollection is leeg** | Ofwel heeft het document alle lettertypen, of `FontSubstitutionWarning` bleef op `None`. | Controleer je `LoadOptions`‑configuratie en zorg dat je het juiste bestandspad laadt. |
| **Aangepaste lettertypen staan op een netwerkschijf** | Netwerk‑latentie kan time‑outs veroorzaken tijdens het zoeken naar lettertypen. | Laad de lettertypen vooraf in `FontSettings` met `SetFontsFolder` en zet `CacheFontData = true`. |

Deze tips helpen je **ontbrekende lettertypen betrouwbaar te detecteren**, zelfs in complexe omgevingen.

---

## Illustratie

![capture font warnings example](https://example.com/images/capture-font-warnings.png "capture font warnings example")

*De screenshot toont een console‑run waarbij twee ontbrekende lettertypen worden gerapporteerd.*

---

## Volgende stappen – Verder gaan dan eenvoudige rapportage

Nu je **fontwaarschuwingen kunt vastleggen**, overweeg je automatisering van remediatie:

1. **Automatische lettertype‑substitutie** – Vervang ontbrekende lettertypen door een bedrijfs‑goedgekeurde fallback via `FontSettings.SubstitutionSettings`.
2. **Loggen naar een bewakings‑systeem** – Stuur de waarschuwingsberichten naar Serilog, ELK of Azure Application Insights.
3. **Gebruikers‑rapporten** – Genereer een HTML‑ of PDF‑samenvatting voor designers om te bekijken welke lettertypen geïnstalleerd moeten worden.

Al deze uitbreidingen bouwen voort op dezelfde basis die we hebben behandeld: `LoadOptions` configureren, het document laden en `WarningInfoCollection` lezen.

---

## Conclusie

Je hebt zojuist geleerd hoe je **fontwaarschuwingen kunt vastleggen** in Aspose.Words, **ontbrekende lettertypen kunt detecteren**, en **ontbrekende lettertypen kunt lijst​en** met een nette, console‑vriendelijke output. De aanpak is eenvoudig, vereist slechts een paar regels C#, en werkt met elke .NET‑versie die Aspose.Words 23.x of hoger ondersteunt.  

Probeer het op een voorbeeld‑DOCX dat verwijst naar een lettertype dat je bewust hebt verwijderd – je ziet de waarschuwingen onmiddellijk verschijnen. Daarna kun je beslissen of je de ontbrekende lettertypen wilt installeren, programmatically vervangen, of simpelweg loggen voor later gebruik.

Happy coding, en moge je documenten altijd met de juiste lettertypen worden weergegeven!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}