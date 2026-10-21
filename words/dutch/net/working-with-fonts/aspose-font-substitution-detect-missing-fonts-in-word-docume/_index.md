---
category: general
date: 2026-04-05
description: Aspose gids voor lettertypevervanging om ontbrekende lettertypen te detecteren
  bij het laden van een Word‑document. Leer hoe u lettertype‑instellingen configureert
  en ontbrekende lettertypen efficiënt afhandelt.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- configure font settings
- handle missing fonts
language: nl
og_description: Aspose gids voor lettertypevervanging om ontbrekende lettertypen te
  detecteren bij het laden van een Word‑document. Leer hoe u lettertype‑instellingen
  configureert en ontbrekende lettertypen efficiënt afhandelt.
og_title: Aspose Lettertypevervanging – Detecteer ontbrekende lettertypen in Word-documenten
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose Lettertypevervanging – Detecteer ontbrekende lettertypen in Word-documenten
url: /nl/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docume/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Ontdek Ontbrekende Lettertypen in Word-documenten

Kom je ooit een Word‑bestand tegen dat er perfect uitziet op één computer maar vreemde lettertype‑wijzigingen vertoont op een andere? Dat is het klassieke **aspose font substitution**‑probleem, en het betekent meestal dat er lettertypen ontbreken op het doelsysteem. In deze tutorial laten we je, stap‑voor‑stap, zien hoe je **ontbrekende lettertypen** kunt **detecteren** wanneer je een **Word‑document laadt**, hoe je **lettertype‑instellingen** kunt **configureren**, en wat je moet doen om **ontbrekende lettertypen** op een nette manier af te handelen.

We lopen een volledig, uitvoerbaar C#‑voorbeeld door, leggen uit waarom elke regel belangrijk is, en laten je zelfs de console‑output zien die je kunt verwachten. Aan het einde kun je lettertype‑substituties direct zien zodra een document wordt geladen—geen giswerk nodig.

## Wat je zult leren

- Hoe je de diagnostische collector van Aspose.Words inschakelt voor lettertype‑waarschuwingen.  
- De exacte code die nodig is om een **Word‑document te laden** met aangepaste **lettertype‑instellingen**.  
- Hoe je over `WarningInfo`‑objecten itereren om elk vervangen lettertype te vermelden.  
- Tips om ongewenste waarschuwingen te onderdrukken of fallback‑lettertypen te bieden.  
- Een kant‑klaar voorbeeld dat je kunt kopiëren‑plakken in Visual Studio.

### Vereisten

- .NET 6.0 of later (de API werkt hetzelfde op .NET Framework).  
- Aspose.Words for .NET (NuGet‑pakket `Aspose.Words`).  
- Een Word‑bestand dat een lettertype verwijst dat je niet geïnstalleerd hebt (bijv. `MissingFont.docx`).  

Als je die hebt, laten we erin duiken.

## Stap 1 – Schakel de diagnostische collector in (Configureer lettertype‑instellingen)

Allereerst: Aspose.Words registreert alleen waarschuwingen voor lettertype‑substitutie als je het vertelt. Dat doe je door een `FontSettings`‑object te maken en dit toe te wijzen aan een `LoadOptions`‑instantie. Beschouw dit als het inschakelen van de “debug‑lampjes” voor lettertype‑afhandeling.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options with a fresh FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    // The FontSettings object is the hub for all font‑related configuration.
    FontSettings = new FontSettings()
};
```

**Waarom?**  
Zonder een `FontSettings`‑object blijft de waarschuwing‑collector stil, en zul je nooit weten welke lettertypen zijn vervangen. Door het leeg te initialiseren laten we Aspose de standaard systeemlettertypen gebruiken *en* houden we elke substitutie bij.

> **Pro tip:** Als je weet dat een specifieke map bedrijfslettertypen bevat, wijs `FontSettings` daar naartoe met `SetFontsFolder("path")`. Dat kan het aantal ontbrekende‑lettertype‑waarschuwingen verminderen.

## Stap 2 – Laad het document met de geconfigureerde opties (Laad Word‑document)

Nu de collector actief is, laad je je `.docx`‑bestand met dezelfde `LoadOptions`. Dit is het moment waarop Aspose het document scant, elke lettertype‑referentie zoekt, en beslist of een substitutie nodig is.

```csharp
// Step 2: Load the Word file while applying the previously defined load options.
Document document = new Document(@"C:\Docs\MissingFont.docx", loadOptions);
```

**Waarom is dit belangrijk?**  
Als je simpelweg `new Document("MissingFont.docx")` zou aanroepen, zouden de standaardinstellingen worden toegepast *en* zou de waarschuwingslijst leeg blijven. Het doorgeven van `loadOptions` garandeert dat de diagnostische collector is gekoppeld aan de laad‑pipeline.

## Stap 3 – Haal lettertype‑substitutie‑waarschuwingen op en toon ze (Detecteer ontbrekende lettertypen)

Nadat het document in het geheugen staat, slaat Aspose eventuele waarschuwingen op in `document.WarningCallback.Warnings`. Loop door die collectie, filter op `WarningType.FontSubstitution`, en print de beschrijving. Elke beschrijving vertelt je welk lettertype ontbrak en welk lettertype in plaats daarvan werd gebruikt.

```csharp
// Step 3: Examine the warning list for any font substitution entries.
foreach (WarningInfo warningInfo in document.WarningCallback.Warnings)
{
    if (warningInfo.Type == WarningType.FontSubstitution)
    {
        // The Description contains a human‑readable message, e.g.,
        // "Font 'Comic Sans MS' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warningInfo.Description}");
    }
}
```

**Verwachte console‑output**

```
Substituted font: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Substituted font: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

Die output vertelt je precies welke lettertypen ontbreken op de machine die de code uitvoert. Je kunt nu beslissen of je de ontbrekende lettertypen installeert, ze in het document embed, of de substitutie behoudt.

![Console‑output die aspose lettertype‑substitutie‑waarschuwingen toont](/images/aspose-font-substitution-console.png)

*Afbeeldings‑alt‑tekst:* aspose font substitution – console‑output met een lijst van vervangen lettertypen

## Stap 4 – Optioneel: Pas het substitutiegedrag aan (Ontbrekende lettertypen afhandelen)

Soms wil je niet alleen weten *dat* er een substitutie heeft plaatsgevonden—je wilt *hoe* het gebeurt controleren. Aspose.Words laat je een aangepaste `IFontSubstitutionRule` registreren. Hieronder staat een snel voorbeeld dat elk ontbrekend lettertype dwingt terug te vallen op `Tahoma`.

```csharp
// Optional Step 4 – Define a custom substitution rule.
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        // Always return Tahoma regardless of the missing font.
        return new FontInfo("Tahoma");
    }
}

// Apply the rule to the FontSettings we created earlier.
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(new TahomaFallbackRule());
```

**Wanneer zou je dit gebruiken?**  
Als je PDF’s genereert voor een webservice en je weet dat elke client `Tahoma` kan weergeven, dan garandeert het forceren van de fallback visuele consistentie zonder tientallen lettertype‑bestanden te hoeven leveren.

## Volledig werkend voorbeeld (Alle stappen gecombineerd)

Hier is het volledige programma dat je kunt plakken in een nieuw console‑project. Het compileert direct, ervan uitgaande dat je het Aspose.Words NuGet‑pakket hebt geïnstalleerd.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1 – Enable diagnostic collector (configure font settings)
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Optional: Force all missing fonts to Tahoma
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(
            new TahomaFallbackRule());

        // -------------------------------------------------
        // Step 2 – Load the document (load word document)
        // -------------------------------------------------
        Document doc = new Document(@"C:\Docs\MissingFont.docx", loadOptions);

        // -------------------------------------------------
        // Step 3 – List any font substitutions (detect missing fonts)
        // -------------------------------------------------
        foreach (WarningInfo warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"Substituted font: {warning.Description}");
        }
    }
}

// -------------------------------------------------
// Optional custom rule class (handle missing fonts)
// -------------------------------------------------
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        return new FontInfo("Tahoma");
    }
}
```

Voer het programma uit, bekijk de console, en je zult elk ontbrekend‑lettertype‑event zien afgedrukt. Vanaf daar kun je beslissen of je de ontbrekende lettertypen installeert, embed, of de fallback behoudt.

## Veelgestelde vragen

**V: Werkt dit met PDF‑conversie?**  
Ja. Wanneer je later `doc.Save("output.pdf")` aanroept, worden de lettertypen die tijdens het laden zijn vervangen, ingebed in de PDF. Het vroegtijdig opvangen van de waarschuwingen helpt je onverwachte lettertype‑wijzigingen in de uiteindelijke PDF te voorkomen.

**V: Wat als ik veel documenten moet verwerken?**  
Plaats de laadlogica in een try‑catch‑blok en hergebruik een enkele `FontSettings`‑instantie voor meerdere documenten. Dat vermindert overhead en houdt de waarschuwing‑collector actief voor elk bestand.

**V: Kan ik de waarschuwingen volledig onderdrukken?**  
Je kunt `loadOptions.WarningCallback = null;` instellen vóór het laden, maar je verliest dan de mogelijkheid om **ontbrekende lettertypen te detecteren**—wat meestal niet gewenst is.

## Conclusie

We hebben alles behandeld wat je nodig hebt om **aspose font substitution** onder de knie te krijgen: het inschakelen van de diagnostische collector, het laden van een Word‑bestand met aangepaste **lettertype‑instellingen**, het extraheren van de lijst met ontbrekende lettertypen, en zelfs het overschrijven van de standaard substitutieregel om **ontbrekende lettertypen** op jouw manier af te handelen. Met slechts een paar regels C# krijg je volledige zichtbaarheid op lettertype‑problemen die anders verborgen blijven achter subtiele lay‑out‑wijzigingen.

Volgende stappen? Probeer de originele lettertypen in het document te embedden met `FontSettings.SetFontsFolder` of verken `FontSourceBase` om lettertypen uit een database te laden. Je kunt ook experimenteren met de `Document.BuiltInStyle`‑collectie om te zien hoe stijl‑niveau lettertype‑wijzigingen zich verspreiden.

Heb je meer vragen over Aspose.Words of lettertype‑beheer? Laat een reactie achter, bekijk de officiële Aspose‑documentatie, of start een nieuw project en speel met de bovenstaande code. Veel plezier met coderen, en moge je documenten altijd precies renderen zoals bedoeld!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}