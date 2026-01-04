---
category: general
date: 2026-01-03
description: Hoe lettertypen te detecteren in Aspose.Words en waarschuwingen te verwerken
  met Aspose-lettertype‑instellingen – een stapsgewijze handleiding voor ontwikkelaars.
draft: false
keywords:
- how to detect fonts
- how to handle warnings
- aspose font settings
- how to configure warnings
language: nl
og_description: Hoe lettertypen te detecteren in Aspose.Words en waarschuwingen te
  configureren met de Aspose-lettertype‑instellingen. Leer de volledige workflow in
  enkele minuten.
og_title: Hoe lettertypen detecteren in Aspose.Words – Waarschuwingen afhandelen
tags:
- Aspose.Words
- C#
- Document Processing
title: Hoe lettertypen detecteren in Aspose.Words – Waarschuwingen en instellingen
  afhandelen
url: /nl/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe lettertypen detecteren in Aspose.Words – Waarschuwingen en instellingen afhandelen

Heb je je ooit afgevraagd **hoe je lettertypen** in een Word‑document kunt detecteren voordat het in productie gaat? Je bent niet de enige. Ontbrekende lettertypen kunnen nachtmerries veroorzaken in de lay‑out, en zonder juiste waarschuwingen kun je een defecte PDF of DOCX leveren zonder het te merken.  

In deze tutorial lopen we stap voor stap door **hoe je lettertypen** kunt detecteren met Aspose.Words, laten we **hoe je waarschuwingen afhandelt** zien, en passen we **Aspose lettertype‑instellingen** aan zodat je **waarschuwingen** precies kunt configureren zoals jij dat nodig hebt. Aan het einde heb je een kant‑klaar fragment dat elke substitutie die Aspose uitvoert afdrukt, en weet je hoe je het kunt aanpassen voor je eigen projecten.

## Prerequisites

- .NET 6+ (of .NET Framework 4.6+).  
- Aspose.Words for .NET geïnstalleerd via NuGet (`Install-Package Aspose.Words`).  
- Een Word‑bestand dat opzettelijk naar een ontbrekend lettertype verwijst (bijv. *DocumentWithMissingFonts.docx*).  

Als je dit al hebt, geweldig—laten we beginnen.

![how to detect fonts screenshot](https://example.com/detect-fonts.png "how to detect fonts example output")

## How to Detect Fonts with Aspose.Words

De eerste stap is Aspose.Words laten weten dat je geïnteresseerd bent in lettertype‑substitutie‑gebeurtenissen. Dit doe je door een aangepaste waarschuwing‑callback te leveren via **Aspose lettertype‑instellingen**. De callback ontvangt een `WarningInfo`‑object voor elke substitutie, waardoor je **lettertypen** tijdens runtime kunt **detecteren**.

### Step 1: Create a Warning Callback Class

Implementeer de `IWarningCallback`‑interface. Binnen de `Warning`‑methode filter je op `WarningType.FontSubstitution` en log je de details.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Receives warnings from Aspose.Words during document loading.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only act on font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **detect fonts** that were missing.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

> **Pro tip:** De `info.Description`‑string bevat zowel de naam van het ontbrekende lettertype als het vervangende lettertype dat Aspose heeft gekozen. Je kunt deze parseren als je een gestructureerd rapport nodig hebt.

### Step 2: Configure LoadOptions with Aspose Font Settings

Maak een `LoadOptions`‑instantie, koppel een nieuw `FontSettings`‑object, en wijs de `WarningCallback` toe aan de handler die we zojuist hebben gebouwd. Dit vertelt Aspose **hoe je waarschuwingen configureert**.

```csharp
// Prepare load options – this is where we **configure warnings**.
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings can be further customized (e.g., add a custom folder).
    FontSettings = new FontSettings(),
    WarningCallback = new FontSubstitutionWarningHandler()
};
```

Als je een eigen lettertype‑map hebt, kun je die als volgt toevoegen:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

Die regel laat een andere kant van **aspose font settings** zien — je bepaalt precies waar Aspose naar lettertypen zoekt voordat het besluit te substitueren.

### Step 3: Load the Document and Trigger the Callback

Laad nu het doel‑document met de `loadOptions`. Terwijl Aspose het bestand parseert, activeert elke ontbrekende lettertype‑waarschuwing de callback, waardoor **lettertypen** on‑the‑fly worden **gedetecteerd**.

```csharp
// The document contains missing fonts, which will fire our warning handler.
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);
```

Wanneer je het programma uitvoert, zie je een output vergelijkbaar met:

```
Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font substituted: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

### Step 4: (Optional) Collect Warnings for Later Use

Als je de substitutie‑gegevens wilt opslaan voor een rapport, wijzig je de handler zodat deze berichten in een lijst verzamelt.

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public List<string> Substitutions { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Substitutions.Add(info.Description);
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Later kun je `handler.Substitutions` naar een JSON‑bestand schrijven, naar een log‑service sturen, of weergeven in een UI.

### Step 5: Verify the Result Programmatically

Soms wil je bevestigen dat er *geen* substitutie heeft plaatsgevonden (bijv. in een CI‑build). Hier is een snelle controle:

```csharp
var handler = new FontSubstitutionWarningHandler();
loadOptions.WarningCallback = handler;

Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);

if (handler.Substitutions.Count == 0)
{
    Console.WriteLine("All fonts were found – no substitutions.");
}
else
{
    Console.WriteLine($"Detected {handler.Substitutions.Count} missing fonts.");
}
```

Dat fragment demonstreert **hoe je waarschuwingen afhandelt** op een deterministische manier, waardoor je volledige controle hebt over de build‑pipeline.

## Frequently Asked Questions (and Edge Cases)

**What if I need to ignore certain substitutions?**  
Je kunt conditionele logica toevoegen binnen `Warning` en simpelweg terugkeren zonder te loggen voor lettertypen die je acceptabel vindt.

**Can I suppress all warnings and just get a boolean result?**  
Ja—stel `loadOptions.WarningCallback = null` en inspecteer daarna `doc.FontInfo` na het laden (hoewel je dan de gedetailleerde log verliest).

**Does this work with PDF conversion?**  
Absoluut. Hetzelfde waarschuwingsmechanisme wordt geactiveerd wanneer je `doc.Save("out.pdf")` aanroept. De callback vangt alle lettertype‑wisselingen tijdens de conversiestap.

**Is there a performance hit?**  
De overhead is minimaal—slechts een paar extra method‑calls per ontbrekend lettertype. Voor grote batches kun je overwegen de resultaten te cachen.

## Wrap‑Up: What We Covered

- **Hoe je lettertypen detecteert** door een aangepaste `IWarningCallback` te implementeren.  
- **Hoe je waarschuwingen afhandelt** via `LoadOptions.WarningCallback`.  
- Het afstemmen van **Aspose lettertype‑instellingen** (toevoegen van aangepaste lettertype‑mappen, in‑/uitschakelen van waarschuwingen).  
- **Hoe je waarschuwingen configureert** voor zowel directe console‑output als latere analyse.  

Met deze onderdelen kun je met vertrouwen Word‑documenten verwerken, garanderen dat ontbrekende lettertypen worden gemarkeerd, en je output consistent houden over verschillende omgevingen.

## Next Steps

- Verken `FontSettings.SubstitutionSettings` voor meer gedetailleerde controle (bijv. specifieke ontbrekende lettertypen mappen naar gekozen substituten).  
- Combineer deze aanpak met Aspose.PDF om PDF’s te genereren die exact dezelfde typografie behouden.  
- Automatiseer de waarschuwing‑check in een CI/CD‑pipeline om releases te blokkeren die lettertype‑problemen bevatten—perfect voor teams die **waarschuwingen afhandelen** als onderdeel van kwaliteits‑gates.

Heb je meer vragen over **aspose font settings** of heb je hulp nodig bij het integreren hiervan in een grotere service? Laat een reactie achter hieronder, en happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}