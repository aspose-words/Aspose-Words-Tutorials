---
category: general
date: 2026-03-28
description: Hoe waarschuwingen vast te leggen bij het laden van een DOCX met Aspose.Words
  en waarschuwingsberichten voor ontbrekende lettertypen te krijgen. Leer hoe je ontbrekende
  lettertypen efficiënt kunt afhandelen.
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: nl
og_description: Hoe waarschuwingen vast te leggen bij het laden van een DOCX met Aspose.Words,
  waarschuwingsteksten te verkrijgen en ontbrekende lettertypen af te handelen met
  praktische codevoorbeelden.
og_title: Hoe waarschuwingen vast te leggen in Aspose.Words – Complete C#-gids
tags:
- Aspose.Words
- C#
- Document Processing
title: Hoe waarschuwingen vast te leggen in Aspose.Words – Complete C#-gids
url: /nl/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe waarschuwingen vast te leggen in Aspose.Words – Complete C# Gids

Heb je je ooit afgevraagd **hoe je waarschuwingen** kunt vastleggen die verschijnen wanneer je een Word‑document laadt met Aspose.Words? Misschien zie je vreemde lettertype‑wijzigingen en moet je precies weten waarom. Kortom, je kunt je aansluiten op het waarschuwingssysteem van de bibliotheek, **waarschuwingsberichten ophalen**, en zelfs **ontbrekende lettertypen afhandelen** voordat ze je lay‑out verpesten.  

In deze tutorial lopen we een real‑world scenario door: een DOCX laden, elke waarschuwing die de engine uitzendt verzamelen, en details afdrukken over eventuele lettertype‑substitutie die plaatsvindt. Aan het einde heb je een kant‑klaar code‑voorbeeld, begrijp je het “waarom” achter elke stap, en weet je hoe je de aanpak kunt uitbreiden voor je eigen projecten.

## Wat je zult leren

- Hoe je `LoadOptions` configureert zodat waarschuwingen automatisch worden vastgelegd.  
- De exacte manier om **waarschuwingsberichten** op te halen uit de `WarningInfoCollection`.  
- Hoe je **ontbrekende lettertypen** kunt identificeren en erop reageren via de `WarningType.FontSubstitution`‑vlag.  
- Tips voor het oplossen van randgevallen, zoals documenten met ingesloten lettertypen of aangepaste lettertype‑mappen.  

Geen externe referenties nodig – alles wat je nodig hebt staat hier.

---

## Voorvereisten

- .NET 6.0 of later (de code werkt ook op .NET Framework 4.7+).  
- Aspose.Words for .NET NuGet‑pakket (`Install-Package Aspose.Words`).  
- Een voorbeeld‑DOCX (`input.docx`) die ofwel enkele lettertypen mist of lettertypen gebruikt die niet op je machine geïnstalleerd zijn.  

Dat is alles. Als je al vertrouwd bent met C# en Visual Studio, kun je de code direct kopiëren‑plakken en uitvoeren.

---

## Stap 1: Load‑opties en een Waarschuwings‑callback voorbereiden

Het eerste wat Aspose.Words doet wanneer je `new Document(path, loadOptions)` aanroept, is het bestand parseren. Tijdens het parseren kan het ontbrekende lettertypen, niet‑ondersteunde functies of verouderde markup tegenkomen. Om die gebeurtenissen op te vangen, heb je een **waarschuwings‑callback**‑object nodig.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**Waarom dit belangrijk is:** Zonder een callback logt Aspose.Words waarschuwingen stilletjes naar de console (of negeert ze), waardoor je blind bent voor lettertype‑substituties die de lay‑out kunnen beïnvloeden. Door een dedicated `WarningInfoCollection` te leveren, krijg je volledige zichtbaarheid.

> **Pro tip:** Als je alleen om font‑gerelateerde waarschuwingen geeft, kun je later filteren – maar het verzamelen van *alle* waarschuwingen geeft je een vangnet voor toekomstige problemen.

---

## Stap 2: Het document laden met de geconfigureerde opties

Nu de callback klaar is, laad je het bestand. De `Document`‑constructor zal automatisch de callback aanroepen voor elk probleem dat het tegenkomt.

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**Wat er onder de motorkap gebeurt:** Aspose.Words parseert de Open XML, lost stijlen op en probeert elke lettertype‑referentie te koppelen aan een systeem‑geïnstalleerd lettertype. Als er geen overeenkomst wordt gevonden, maakt het een `WarningInfo`‑item van het type `FontSubstitution`.

---

## Stap 3: De verzamelde waarschuwingen ophalen en inspecteren

Na het laden bevat je `warningCollector` nu elke waarschuwing die is opgetreden. Laten we ze eruit halen en ons richten op berichten over lettertype‑substitutie.

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**Voorbeeldoutput** (je console kan iets als het volgende tonen):

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Als je *alle* waarschuwingen wilt, verwijder dan simpelweg de `if`‑check of log `warning.Type` voor elk item.

---

## Stap 4: Ontbrekende lettertypen afhandelen – meer dan alleen loggen

Waarschuwingen vastleggen is nuttig, maar vaak moet je **ontbrekende lettertypen** programmatisch **afhandelen**. Hier zijn twee veelvoorkomende strategieën:

### 4.1 Ontbrekende lettertypen vervangen door een specifieke fallback

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

Nu wordt elk ontbrekend lettertype vervangen door *Calibri* in plaats van de standaard fallback van de bibliotheek.

### 4.2 Dynamisch een vervangend lettertype insluiten

Als je een aangepast lettertype‑bestand hebt (bijv. `MyFallback.ttf`), kun je dit tijdens runtime registreren:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

Deze aanpak is handig wanneer je een specifiek bedrijfslettertype meegeeft met je applicatie.

> **Randgeval:** Documenten die het benodigde lettertype al insluiten, negeren de systeem‑substitutieregels. In dat scenario blijft de warning‑collectie leeg voor dat lettertype, wat precies is wat je wilt.

---

## Stap 5: Volledig werkend voorbeeld (Kopie‑Plak klaar)

Hieronder staat een zelf‑containend programma dat alles van begin tot eind demonstreert. Vervang gewoon `YOUR_DIRECTORY/input.docx` door het pad naar je testbestand.

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Wat je kunt verwachten**

- De console print elke font‑substitutie‑waarschuwing, voorafgegaan door een waarschuwings‑emoji voor zichtbaarheid.  
- Het output‑DOCX (`output.docx`) gebruikt *Calibri* waar een ontbrekend lettertype werd gedetecteerd.  
- Geen ongehandelde uitzonderingen – het waarschuwingssysteem handelt onbekende lettertypen elegant af.

---

## Veelgestelde vragen & antwoorden

**Q: Werkt dit ook met PDF’s die uit Word zijn gegenereerd?**  
A: Ja. Aspose.Words behandelt PDF’s als een ander output‑formaat. Het vastleggen van waarschuwingen gebeurt tijdens de *load*‑fase, dus het is onafhankelijk van de uiteindelijke export.

**Q: Wat als ik waarschuwingen wil vastleggen voor **alle** documentbewerkingen (opslaan, converteren, enz.)?**  
A: Je kunt dezelfde `WarningInfoCollection` hergebruiken door deze toe te wijzen aan `Document.WarningCallback` nadat het document is geïnstantieerd. Elke volgende bewerking voegt nieuwe items toe aan dezelfde collectie.

**Q: Heeft de waarschuwings‑callback invloed op de prestaties?**  
A: Verwaarloosbaar. De collectie slaat simpelweg objecten op; tenzij je duizenden waarschuwingen in een strakke loop verwerkt, merk je geen vertraging.

**Q: Hoe onderdruk ik waarschuwingen die me niet interesseren?**  
A: Implementeer een aangepaste klasse die `IWarningCallback` erft en filter binnen de `Warning`‑methode. De ingebouwde `WarningInfoCollection` slaat alleen op, ze filtert niet.

---

## Pro tips & valkuilen

- **Pro tip:** Inspecteer altijd de `Warning.Description` – deze bevat de exacte naam van het ontbrekende lettertype. Dit kan je helpen beslissen of je het lettertype met je app moet leveren.  
- **Let op ingesloten lettertypen:** Als het bron‑DOCX het benodigde lettertype al insluit, zal Aspose.Words geen substitutie‑waarschuwing geven, zelfs als het lettertype lokaal niet geïnstalleerd is.  
- **Thread‑veiligheid:** `WarningInfoCollection` is niet thread‑safe. Als je meerdere documenten gelijktijdig laadt, geef elke thread zijn eigen collectie.  
- **Versiecontrole:** De waarschuwings‑API is stabiel sinds Aspose.Words 20.8. Zorg dat je een recente versie gebruikt om geen nieuwere waarschuwings‑types te missen.

---

## Conclusie

We hebben behandeld **hoe je waarschuwingen** van Aspose.Words kunt vastleggen, laten zien hoe je **waarschuwingsberichten** kunt ophalen, en praktische manieren getoond om **ontbrekende lettertypen** af te handelen via fallback‑lettertypen of aangepaste lettertype‑mappen. Het volledige voorbeeld staat klaar om in elk .NET‑project te worden geplakt, en de concepten schalen naar grotere automatiserings‑pipelines.

Vervolgens kun je verkennen:

- `Document.WarningCallback` gebruiken om waarschuwingen tijdens **opslaan**‑bewerkingen vast te leggen.  
- Waarschuwingen loggen naar een bestand of telemetriesysteem voor productie‑monitoring.  
- De callback uitbreiden om automatisch ontbrekende lettertypen te vervangen door merk‑specifieke typografie.

Voel je vrij om te experimenteren — verwissel het fallback‑lettertype, voeg meer documenten toe aan de batch, of integreer de warning‑collector in een CI‑pipeline die font‑gerelateerde regressies markeert. Veel programmeerplezier, en moge je documenten altijd exact renderen zoals je verwacht!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}