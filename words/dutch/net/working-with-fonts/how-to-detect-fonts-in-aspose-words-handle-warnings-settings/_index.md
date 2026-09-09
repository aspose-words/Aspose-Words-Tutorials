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

## Vereisten

- .NET6+ (van .NET Framework 4.6+).
- Aspose.Words voor .NET defect via NuGet (`Install-Package Aspose.Words`).
- Een Word‑bestand dat gekozen is voor een ontbrekend lettertype (bijv. *DocumentWithMissingFonts.docx*).

Als je dit allemaal hebt, geweldig – laten we beginnen.

![screenshot van lettertypen detecteren](https://example.com/detect-fonts.png "voorbeelduitvoer van lettertypen detecteren")

## Lettertypen detecteren met Aspose.Words

De eerste stap is Aspose.Words laten weten dat je geïnteresseerd bent in lettertype‑substitutie‑gebeurtenissen. Dit doe je door een aangepaste waarschuwing‑callback te leveren via **Aspose lettertype‑instellingen**. De callback ontvangt een `WarningInfo`‑object voor elke vervanging, waardoor je **lettertypen** tijdens runtime **detecteren** kunt.

### Stap 1: Maak een waarschuwings-callback-klasse

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

### Stap 2: Configureer LoadOptions met Aspose-lettertype-instellingen

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

### Stap 3: Laad het document en activeer de callback

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

### Stap 4: (Optioneel) Verzamel waarschuwingen voor later gebruik

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

### Stap 5: Controleer het resultaat programmatisch

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

## Veelgestelde vragen (en randgevallen)

**Wat moet ik doen als ik bepaalde vervangingen moet negeren?**
Je kunt conditionele logica toevoegen binnen `Waarschuwing` en herhaaldelijk terugkerend zonder te loggen voor lettertypen die je acceptabel vindt.

**Kan ik alle waarschuwingen onderdrukken en alleen een Booleaans resultaat krijgen?**
Ja—stel `loadOptions.WarningCallback = null` en inspecteer daarna `doc.FontInfo` na het laden (hoewel je dan de gedetailleerde log verliest).

**Werkt dit met PDF-conversie?**
Absoluut. Hetzelfde waarschuwingsmechanisme wordt geactiveerd wanneer je `doc.Save("out.pdf")` aanroept. De callback vangt alle lettertype-wisselingen tijdens de conversiestap op.

**Is er een prestatiehit?**
De overhead is minimaal – slechts een paar extra method‑calls per ontbrekend lettertype. Voor grote batches kun je de resultaten overwegen om te cachen.

## Afronding: wat we hebben besproken

- **Hoe je lettertype detecteert** door een aangepaste `IWarningCallback` te implementeren.
- **Hoe je waarschuwingen afhandelt** via `LoadOptions.WarningCallback`.
- Het aanpassen van **Aspose lettertype‑instellingen** (toevoegen van aangepaste lettertype‑kaarten, in‑/uitschakelen van waarschuwingen).
- **Hoe je waarschuwingen configureert** voor zowel directe console-uitvoer als latere analyse.

Met deze onderdelen kun je met vertrouwen Word-documenten verwerken, waardoor ontbrekende lettertypen gemarkeerd worden, en je output consistent behouden over verschillende omgevingen.

## Volgende stappen

- Verken `FontSettings.SubstitutionSettings` voor meer gedetailleerde controle (bijv. specifieke ontbrekende lettertypen mappen naar gekozen substituten).
- Combineer deze aanpak met Aspose.PDF om PDF’s te genereren die exact dezelfde typografie behouden.
- Automatiseer de waarschuwing-check in een CI/CD-pipeline om releases te elimineren die lettertype-problemen bevatten – perfect voor teams die **waarschuwingen afhandelen** als onderdeel van kwaliteitspoorten.

Heb je meer vragen over **stel lettertype-instellingen** of heb je hulp nodig bij het gevolg hiervan in een grotere service? Laat een reactie achter hieronder, en veel codeerplezier!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}