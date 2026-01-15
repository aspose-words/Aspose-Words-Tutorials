---
category: general
date: 2026-01-14
description: Log waarschuwingen voor lettertypevervanging tijdens het laden van Word‑documenten
  met Aspose.Words. Leer hoe je ontbrekende lettertypen kunt detecteren en hoe je
  ontbrekende lettertypen kunt vastleggen in C#.
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: nl
og_description: Log waarschuwingen voor lettertypevervanging tijdens het laden van
  Word‑documenten met Aspose.Words. Ontdek hoe je ontbrekende lettertypen kunt detecteren
  en vastleggen in C#.
og_title: Log waarschuwingen voor lettertypevervanging – Complete Aspose.Words-gids
tags:
- Aspose.Words
- C#
- Document Processing
title: Log waarschuwingen voor lettertypevervanging – Complete Aspose.Words-gids
url: /nl/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Log Font Substitutie Waarschuwingen – Complete Aspose.Words Gids

Het loggen van font‑substitutie‑waarschuwingen is essentieel wanneer je moet garanderen dat een Word‑document er precies hetzelfde uitziet nadat het is geladen door Aspose.Words. Als je je ooit hebt afgevraagd hoe je **ontbrekende lettertypen kunt detecteren** of wilt weten **hoe je ontbrekende lettertypen kunt vastleggen**, ben je hier op de juiste plek.  

In deze tutorial lopen we een real‑world scenario door, laten we de volledige C#‑code zien, en leggen we uit waarom elke regel belangrijk is. Aan het einde kun je elke font‑substitutie‑gebeurtenis loggen en erop reageren — geen mysterieuze waarschuwingen meer.

![Voorbeeld van loggen van font‑substitutie‑waarschuwingen](/images/font-warnings.png "Schermafbeelding die console‑output van loggen van font‑substitutie‑waarschuwingen toont")

## Wat je zult leren

- Hoe je `LoadOptions` configureert zodat Aspose.Words getypeerde waarschuwingen voor font‑substitutie genereert.  
- De exacte stappen om **ontbrekende lettertypen te detecteren** tijdens het laden van een document.  
- Een nette manier om **ontbrekende lettertypen vast te leggen** en ze naar je eigen log‑ of monitoringsysteem te schrijven.  
- Edge‑case handling (bijv. wanneer een document een lettertype bevat dat niet op de server is geïnstalleerd).  

### Vereisten

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.6+).  
- Een geldige Aspose.Words for .NET‑licentie (of de gratis proefversie).  
- Basiskennis van C# en console‑applicaties.  

Als je dat al hebt, laten we erin duiken.

## Stap 1 – LoadOptions instellen om getypeerde waarschuwingen te genereren

Het hart van de oplossing ligt in `LoadOptions.FontSubstitutionWarning`. Door dit te wijzigen naar `RaiseTypedWarnings` vertel je Aspose.Words een gebeurtenis **elke keer** te activeren wanneer het exacte lettertype dat je vraagt niet kan vinden.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **Waarom dit belangrijk is:**  
> Het standaardgedrag vervangt stilzwijgend een ontbrekend lettertype door de dichtstbijzijnde match, wat kan leiden tot lay‑out‑glitches die je nooit ziet aankomen. Het genereren van getypeerde waarschuwingen geeft je volledige zichtbaarheid.

## Stap 2 – Abonneren op het Waarschuwings‑Evenement

Nu koppelen we ons aan `loadOptions.FontSubstitutionWarning`. De lambda ontvangt een `e`‑object dat ons precies vertelt welk lettertype ontbrak en welk lettertype in plaats daarvan werd gebruikt.

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **Pro tip:** Als je dit op een webserver draait, vervang `Console.WriteLine` door een gestructureerde logger (Serilog, NLog, etc.) zodat je later de gegevens kunt opvragen.

## Stap 3 – Het Document Laden met de Geconfigureerde Opties

Met het waarschuwingsmechanisme actief, laad je het document gewoon zoals je normaal zou doen. Het evenement wordt automatisch geactiveerd voor elk ontbrekend lettertype.

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### Verwachte console‑output

Als `input.docx` een lettertype *MyFancyFont* aanroept dat niet geïnstalleerd is, zie je:

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

Elke regel komt overeen met een **ontbrekende lettertypen detecteren**‑gebeurtenis, waardoor je een volledige audit‑trail krijgt.

## Stap 4 – Edge‑Cases en Geavanceerde Scenario’s Afhandelen

### 4.1 Wanneer er geen substitutie plaatsvindt

Soms gebruikt een document alleen systeemlettertypen die al aanwezig zijn. In dat geval wordt het waarschuwings‑evenement nooit geactiveerd en krijg je een schone console zonder output. Dat is een goed teken — je omgeving heeft al alle benodigde lettertypen.

### 4.2 Waarschuwingen Vastleggen voor Later Analyse

Als je de waarschuwingen wilt opslaan voor een nachtelijk rapport, verzamel ze dan in een lijst:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

Na het laden kun je `missingFonts` serialiseren naar JSON, naar een database schrijven, of een samenvatting e‑mailen.

### 4.3 Werken met PDF’s of Andere Formaten

Dezelfde `LoadOptions`‑aanpak werkt voor `Load`‑aanroepen op PDF’s, RTF en zelfs HTML‑bestanden. Geef gewoon dezelfde opties‑instantie door, en Aspose.Words zal waarschuwingen genereren voor elk lettertype dat niet kan worden gematcht.

## Stap 5 – Het Resultaat Programma­tisch Verifiëren

Als je de voorkeur geeft aan een geautomatiseerde test in plaats van het console handmatig te bekijken, controleer dan of de lijst de verwachte items bevat:

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

Dit fragment toont **hoe je ontbrekende lettertypen kunt vastleggen** in code, niet alleen in logs.

## Veelvoorkomende Valkuilen & Hoe ze te Vermijden

| Valkuil | Waarom het gebeurt | Oplossing |
|---------|--------------------|-----------|
| Vergeten `RaiseTypedWarnings` in te stellen | De standaard is `DoNotRaise`, waardoor er geen gebeurtenissen worden getriggerd. | Stel `FontSubstitutionWarning` expliciet in zoals getoond in Stap 1. |
| `Console.WriteLine` gebruiken in een webapp | Console‑output verdwijnt in IIS/ASP.NET Core. | Schakel over naar een persistente logger (bijv. Serilog). |
| Een document laden met een relatief pad | De werkmap kan tijdens runtime verschillen. | Gebruik absolute paden of `Path.Combine(AppContext.BaseDirectory, "input.docx")`. |
| Het negeren van `SubstitutedFontName` | Je verliest inzicht in welke fallback is gekozen. | Log altijd zowel `FontName` als `SubstitutedFontName`. |

## Bonus: Font‑Installatie Automatiseren

Als je de implementatie‑omgeving beheert, kun je de ontbrekende lettertypen vooraf installeren met een PowerShell‑script:

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

Dit script uitvoeren vóórdat je applicatie start, elimineert de meeste **ontbrekende lettertypen detecteren**‑waarschuwingen.

## Conclusie

We hebben alles behandeld wat je nodig hebt om **font‑substitutie‑waarschuwingen te loggen** bij het laden van Word‑documenten met Aspose.Words. Door `LoadOptions` te configureren, je te abonneren op het waarschuwings‑evenement, en eventueel de resultaten te persisteren, kun je betrouwbaar **ontbrekende lettertypen detecteren** en begrijpen **hoe je ontbrekende lettertypen kunt vastleggen** voor elk .NET‑project.

Pak de code, pas de logger aan op jouw stack, en je zult nooit meer verrast worden door een stille font‑swap. Volgende stappen kunnen zijn:

- De waarschuwingslijst integreren met je CI/CD‑pipeline om builds te laten falen wanneer kritieke lettertypen ontbreken.  
- De aanpak uitbreiden om font‑gebruik te monitoren over een hele vloot documenten.  
- De `FontSettings`‑API van Aspose.Words verkennen om aangepaste fallback‑lettertypen te bieden.

Heb je vragen of een lastig scenario? Laat een reactie achter, en laten we samen het probleem oplossen. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}