---
category: general
date: 2026-02-10
description: Stel een waarschuwingscallback in om lettertypewijzigingen te monitoren
  terwijl u het standaardlettertype configureert en het standaard importlettertype
  instelt in Aspose.Words. Leer de volledige stap‑voor‑stapoplossing.
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: nl
og_description: Stel een waarschuwingscallback in om lettertypewijzigingen te monitoren
  tijdens het configureren van het standaardlettertype en het instellen van het standaard
  importlettertype. Volg de volledige tutorial voor Aspose.Words.
og_title: Waarschuwingscallback instellen in C# – Complete gids
tags:
- Aspose.Words
- C#
- Document Import
title: Stel waarschuwingscallback in C# – Complete gids voor lettertypebeheer
url: /nl/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

. | Always attach the callback **before** calling `new Document(...)`. |

Translate each.

Now final sections.

Make sure to keep code block placeholders.

Now produce final output.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Waarschuwingscallback instellen in C# – Complete gids voor lettertypebeheer

Heb je ooit moeten **set warning callback** bij het laden van een Word‑document en je afgevraagd hoe je tegelijk *configure default font* kunt instellen? Je bent niet de enige. In veel real‑world projecten—zoals geautomatiseerde rapportgeneratoren of documentconversiepijplijnen—kunnen ontbrekende lettertypen stilletjes de lay‑out breken, en de enige manier om die problemen te detecteren is door **monitor font changes** via een waarschuwingscallback.

In deze tutorial lopen we stap voor stap door een praktisch voorbeeld dat laat zien hoe je **set warning callback**, **configure default font** en zelfs **set default import font** kunt gebruiken met Aspose.Words for .NET. Aan het einde heb je een kant‑klaar code‑fragment, begrijp je waarom elk onderdeel belangrijk is, en weet je hoe je het kunt aanpassen voor randgevallen zoals aangepaste lettertype‑mappen of stille substituties.

---

## Prerequisites

- .NET 6.0 of later (de code werkt ook op .NET Framework 4.6+)  
- Aspose.Words for .NET NuGet‑package (`Install-Package Aspose.Words`)  
- Een map die het fallback‑lettertype bevat dat je wilt gebruiken (bijv. `fonts/Arial.ttf`)  
- Basiskennis van C# console‑apps  

Er zijn geen extra libraries nodig.

---

## Stap 1: Maak LoadOptions en **configure default font**

Het eerste wat je doet wanneer je de lettertype‑afhandeling wilt beheersen, is een `LoadOptions`‑instantie aanmaken. Dit object vertelt Aspose.Words hoe om te gaan met ontbrekende lettertypen tijdens het importeren.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**Waarom dit belangrijk is:**  
Als het bron‑document een lettertype aanroept dat niet op de server is geïnstalleerd, kijkt Aspose.Words in de map die jij hebt opgegeven. Dit is de kern van **set default import font**—je vertelt de bibliotheek expliciet waar een vervanging te vinden is voordat er waarschuwingen worden gegenereerd.

---

## Stap 2: **Set warning callback** om **monitor font changes**

Aspose.Words geeft een `WarningInfoCollection` af telkens wanneer het een lettertype moet substitueren, naast andere zaken. Door een handler te koppelen kun je elke substitutie loggen of erop reageren.

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**Waarom dit belangrijk is:**  
Alleen **configure default font** is niet genoeg als je wilt auditen welke lettertypen daadwerkelijk zijn vervangen. De callback levert een realtime‑log, voldoet aan de **monitor font changes**‑eis en helpt onverwachte fallback‑situaties vroegtijdig in een CI‑pipeline te detecteren.

---

## Stap 3: Laad het document met de voorbereide opties

Nu de load‑options volledig zijn geconfigureerd, kun je veilig elk `.docx`‑bestand laden. De callback wordt automatisch geactiveerd als er een substitutie plaatsvindt.

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**Wat je zult zien:**  
Als de bron een lettertype gebruikt dat niet aanwezig is, zal de console iets als het volgende afdrukken:

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

Die output bevestigt dat je succesvol **set warning callback** hebt ingesteld en dat de **default import font** effect heeft gehad.

---

## Stap 4: (Optioneel) Fijn afstellen van lettertype‑substitutiegedrag

Soms wil je alle ontbrekende lettertypen vervangen door één enkele familie, ongeacht de oorspronkelijke aanvraag. Aspose.Words laat je een *fallback‑lettertype* globaal instellen.

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**Wanneer dit te gebruiken:**  
Als je PDF’s genereert voor een merk dat slechts een beperkt aantal lettertypen toestaat, zorgt dit voor consistentie in elk document, zelfs als de bron iets exotisch probeert te gebruiken.

---

## Stap 5: Opslaan of verder verwerken van het document

Na het laden kun je doorgaan met elke gewenste verwerking—bewerken, converteren naar PDF, tekst extraheren, enz. Hier is een kort voorbeeld van het opslaan van het document als PDF terwijl de vervangen lettertypen behouden blijven.

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

De resulterende PDF toont het fallback‑lettertype op elke plaats waar een substitutie heeft plaatsgevonden, waardoor je visueel kunt bevestigen dat de **set warning callback** naar behoren werkte.

---

## Veelvoorkomende valkuilen & Pro‑tips

| Probleem | Waarom het gebeurt | Oplossing |
|----------|-------------------|----------|
| **Callback never fires** | `LoadOptions.WarningCallback` was niet toegewezen *voordat* het document werd geladen. | Koppel de callback **altijd vóór** het aanroepen van `new Document(...)`. |
| **Wrong font folder** | Typfout in pad of ontbrekende leesrechten. | Controleer of de map bestaat en de app lees‑toegang heeft. Gebruik absolute paden voor betrouwbaarheid. |
| **Multiple substitutions, noisy output** | Grote documenten met veel ontbrekende lettertypen. | Filter waarschuwingen op `WarningType.FontSubstitution` (zoals getoond) of schrijf ze naar een log‑bestand in plaats van naar de console. |
| **Fallback font not applied** | Het fallback‑lettertype is niet geïnstalleerd op de machine. | Plaats het `.ttf`/`.otf`‑bestand in de map die je hebt doorgegeven aan `SetFontsFolder`. Aspose.Words laadt het direct, zonder OS‑installatie. |

**Pro‑tip:** Wanneer je dit in een CI/CD‑pipeline draait, leid de console‑output om naar een build‑artifact. Zo heb je een audit‑trail van elke lettertype‑substitutie die tijdens de build heeft plaatsgevonden.

---

## Volledig werkend voorbeeld (Kopie‑en‑plak klaar)

Hieronder vind je het complete programma dat je in een nieuw Console‑App‑project kunt plakken. Het bevat alle stappen, using‑statements en commentaren die je nodig hebt.

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**Verwachte console‑output** (ervan uitgaande dat `Times New Roman` ontbrak):

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

Voer het programma uit, open `output.pdf`, en je ziet dat het document is gerenderd met het fallback‑lettertype waar nodig.

---

## Conclusie

Je beschikt nu over een solide, productie‑klaar patroon om **set warning callback** in C# te gebruiken, **configure default font**, **monitor font changes**, en **set default import font** bij het werken met Aspose.Words. Door een waarschuwingscollector vóór het laden te koppelen, `FontSettings` naar een betrouwbare lettertype‑map te wijzen, en eventueel een globale fallback af te dwingen, krijg je volledige zichtbaarheid en controle over lettertype‑substitutie—precies wat elke robuuste document‑verwerkingspipeline nodig heeft.

Klaar voor de volgende stap? Probeer deze aanpak te combineren met:

- **Dynamic font loading** vanuit een database (gebruik `FontSettings.SetFontsFolder` tijdens runtime).  
- **Custom warning handlers** die naar een gestructureerd log (JSON of CSV) schrijven voor analytics.  
- **Parallel document processing** waarbij elke thread zijn eigen `LoadOptions` krijgt om kruis‑talk te voorkomen.

Voel je vrij om te experimenteren, de code aan je eigen architectuur aan te passen, en eventuele ontdekkingen te delen in de reacties. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}