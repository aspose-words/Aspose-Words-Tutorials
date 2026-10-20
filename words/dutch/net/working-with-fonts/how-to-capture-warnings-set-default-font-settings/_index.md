---
category: general
date: 2026-03-19
description: Leer hoe u waarschuwingen kunt vastleggen in Aspose.Words, standaardlettertype‑instellingen
  kunt instellen en ontbrekende lettertypen kunt detecteren bij het laden van een
  Word‑document.
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: nl
og_description: Hoe waarschuwingen vast te leggen in Aspose.Words, standaardlettertype-instellingen
  in te stellen en ontbrekende lettertypen te detecteren bij het laden van een Word‑document.
og_title: Hoe waarschuwingen vast te leggen – Standaard lettertype‑instellingen instellen
tags:
- Aspose.Words
- C#
- Document Processing
title: Hoe waarschuwingen vastleggen – Standaardlettertype‑instellingen instellen
url: /nl/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe Waarschuwingen Vast te Leggen – Standaard Lettertype‑Instellingen Instellen

**Hoe waarschuwingen vast te leggen** is een veelvoorkomende behoefte wanneer je met Aspose.Words werkt, vooral als je documenten afhankelijk zijn van specifieke lettertypen die mogelijk niet op de doelsysteem aanwezig zijn. Heb je ooit een DOCX geopend en je afgevraagd waarom de lay‑out er vreemd uitzag? Het antwoord zit vaak verborgen in een waarschuwing over een ontbrekend lettertype.  

In deze gids lopen we stap voor stap door **hoe waarschuwingen vast te leggen** terwijl je een **Word‑document laadt**, **standaard lettertype‑instellingen instelt**, en uiteindelijk **ontbrekende lettertypen detecteert** zodat je programmatic kunt reageren. Geen poespas—alleen een volledig, uitvoerbaar voorbeeld en de reden achter elke regel.

> *Pro tip:* Het vroegtijdig vastleggen van waarschuwingen bespaart je later het debuggen van mysterieuze lay‑out‑fouten.

---

## Wat Je Nodig Hebt

- **Aspose.Words for .NET** (nieuwste versie per 2026).  
- Een .NET‑ontwikkelomgeving (Visual Studio, Rider of VS Code).  
- Een voorbeeld‑DOCX dat verwijst naar een lettertype dat je *niet* geïnstalleerd hebt (bijv. *Comic Sans MS* op een Linux‑machine).  

Dat is alles. Er zijn geen extra NuGet‑pakketten nodig naast Aspose.Words.

---

## Stap 1 – Begrijpen Waarom Je Waarschuwingen Moet Vastleggen

Wanneer Aspose.Words een document parseert, kan het lettertypen tegenkomen die niet beschikbaar zijn op de host. Standaard vervangt de bibliotheek stilletjes een fallback‑lettertype, wat kan leiden tot gewijzigde regeleinden, spatiëring en zelfs verdwijning van tekst.  

Het gebruik van de **WarningCallback** in combinatie met een **FontSettings**‑object geeft je twee dingen:

1. **Zichtbaarheid** – je krijgt een `WarningInfo`‑item voor elke substitutie.  
2. **Controle** – je kunt vooraf een standaardlettertype configureren om visuele verrassingen te minimaliseren.

Beschouw het als het installeren van een “watchdog” die elke keer schreeuwt wanneer de motor een onderdeel onder de motorkap verwisselt.

---

## Stap 2 – Standaard Lettertype‑Instellingen Instellen

Het eerste secundaire trefwoord, **standaard lettertype‑instellingen instellen**, verschijnt hier. Je maakt een `FontSettings`‑instantie aan en wijst eventueel een map aan die jouw fallback‑lettertypen bevat.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **Waarom?**  
> Als je geen fallback opgeeft, kiest Aspose.Words het eerste systeemlettertype dat bij de stijl past, wat sterk kan afwijken. Door een bekend standaardlettertype in te stellen, garandeer je consistente weergave op verschillende machines.

---

## Stap 3 – Een Waarschuwing‑Callback Voorbereiden om Waarschuwingen Vast te Leggen

Nu laten we **hoe waarschuwingen vast te leggen** zien door een `WarningInfoCollection` aan de laadopties te koppelen. Deze collectie slaat elke waarschuwing op die tijdens het laadproces wordt gegenereerd.

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

De `WarningInfoCollection` implementeert `IWarningCallback`, zodat Aspose.Words automatisch elke waarschuwing in `warningInfos` plaatst. Polling is niet nodig.

---

## Stap 4 – Word‑Document Laden met de Geconfigureerde Opties

Hier komt het tweede secundaire trefwoord, **Word‑document laden**, in actie. We geven zowel de `FontSettings` als de `WarningCallback` door aan een `LoadOptions`‑instantie.

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Als het document verwijst naar een lettertype dat niet geïnstalleerd is, zal de waarschuwing‑callback een `WarningType.FontSubstitution`‑item vastleggen.

---

## Stap 5 – Ontbrekende Lettertypen Detecteren uit de Verzamelde Waarschuwingen

Tot slot beantwoorden we het derde secundaire trefwoord, **ontbrekende lettertypen detecteren**, door over de verzamelde waarschuwingen te itereren.

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

Typische uitvoer ziet er als volgt uit:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Die regel vertelt je precies welk lettertype ontbreekt en welke fallback is gebruikt—informatie die je kunt loggen, aan de gebruiker kunt tonen, of zelfs kunt gebruiken om een aangepaste lettertype‑installatieroutine te activeren.

---

## Volledig Uitvoerbaar Voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren‑plakken in een console‑applicatie. Het demonstreert **hoe waarschuwingen vast te leggen**, **standaard lettertype‑instellingen in te stellen**, **Word‑document te laden**, en **ontbrekende lettertypen te detecteren** in één doorlopend proces.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**Verwacht resultaat:** Wanneer het opgegeven DOCX een lettertype refereert dat niet geïnstalleerd is, print de console een waarschuwing voor elke substitutie. Als alle lettertypen aanwezig zijn, produceert de lus geen output.

---

## Veelvoorkomende Valkuilen & Randgevallen

| Situatie | Waarom het gebeurt | Hoe je het oplost |
|----------|--------------------|-------------------|
| **Geen waarschuwingen verschijnen** hoewel de lay‑out er verkeerd uitziet | Het document gebruikt *embedded* lettertypen, die Aspose.Words rendert zonder substitutie. | Controleer `Document.HasEmbeddedFonts` en overweeg de ingebedde lettertypen te extraheren als je ze op een andere machine nodig hebt. |
| **Meerdere waarschuwingen voor de |  |  |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}