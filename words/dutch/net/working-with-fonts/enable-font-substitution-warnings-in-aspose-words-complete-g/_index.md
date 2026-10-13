---
category: general
date: 2026-01-11
description: Schakel waarschuwingen voor lettertypevervanging in om ontbrekende lettertypen
  in uw .NET‑documenten te detecteren. Leer hoe u de naam van een ontbrekend lettertype
  kunt ophalen en een lijst met ontbrekende lettertypen kunt weergeven met Aspose.Words.
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: nl
og_description: Schakel waarschuwingen voor lettertypevervanging in Aspose.Words in
  om ontbrekende lettertypen te detecteren, de naam van het ontbrekende lettertype
  te verkrijgen en ontbrekende lettertypen in uw documenten weer te geven.
og_title: Lettertypevervangingswaarschuwingen inschakelen – Stapsgewijze C#‑tutorial
tags:
- Aspose.Words
- C#
- Document Processing
title: Waarschuwingen voor lettertypevervanging inschakelen in Aspose.Words – Complete
  gids
url: /nl/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lettertypevervangingswaarschuwingen inschakelen – Complete gids

Heb je je ooit afgevraagd waarom een Word‑document er een beetje anders uitziet nadat je het op een server hebt geladen? Het is waarschijnlijk dat een lettertype dat de oorspronkelijke auteur gebruikte niet beschikbaar is op jouw machine, en Aspose.Words heeft het stilletjes vervangen door het dichtstbijzijnde alternatief. **Schakel lettertypevervangingswaarschuwingen in** en je weet meteen welke lettertypen ontbreken, waarmee ze zijn vervangen en hoe je op die informatie kunt reageren.

In deze tutorial lopen we een praktisch, end‑to‑end voorbeeld door dat laat zien hoe je **ontbrekende lettertypen kunt detecteren**, de **get missing font name** kunt ophalen, en zelfs **ontbrekende lettertypen kunt opsommen** voor rapportage. Geen poespas, alleen een duidelijke oplossing die je vandaag nog in elk .NET‑project kunt gebruiken.

---

## Wat je zult leren

- Hoe je `LoadOptions` configureert zodat Aspose.Words gedetailleerde waarschuwingen genereert.
- De exacte code die nodig is om een document te laden en lettertype‑gerelateerde waarschuwingen te enumereren.
- Manieren om de ontbrekende lettertype‑naam en de vervanging te extraheren en vervolgens een net rapport te genereren.
- Tips voor het omgaan met randgevallen, zoals documenten met tientallen ontbrekende lettertypen of aangepaste lettertype‑mappen.

### Vereisten

- .NET 6+ (de code werkt ook met .NET Framework 4.7+)
- Aspose.Words for .NET 23.10 of nieuwer (je kunt het ophalen via NuGet)
- Een voorbeeld‑DOCX die verwijst naar een lettertype dat je niet geïnstalleerd hebt (we noemen het `MissingFont.docx`)

Als je deze basis hebt, laten we erin duiken.

---

## Stap 1: LoadOptions configureren om lettertypevervangingswaarschuwingen in te schakelen  

Het eerste dat je moet doen is Aspose.Words laten weten dat je belang hecht aan ontbrekende lettertypen. Standaard logt de bibliotheek waarschuwingen alleen intern. Door `SubstitutionWarningLevel` in te stellen op `Typical` (of `All` voor de meest uitgebreide output) schakel je dit in.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**Waarom dit belangrijk is:**  
Wanneer `SubstitutionWarningLevel` is ingesteld, voegt Aspose.Words elke keer dat het een verwijst lettertype niet kan vinden een `FontSubstitutionWarning` toe aan de `Warnings`‑collectie van het document. Die collectie is de enige betrouwbare manier om **ontbrekende lettertypen te detecteren** zonder het document handmatig te parseren.

> **Pro tip:** Als je met een batch documenten werkt en er absoluut zeker van wilt zijn dat je elke substitutie opvangt, gebruik dan `FontSubstitutionWarningLevel.All`. Het is iets rumoeriger, maar garandeert dat er geen waarschuwing doorheen glipt.

## Stap 2: Het document laden met de geconfigureerde opties  

Nu het waarschuwingssysteem is ingesteld, laad je DOCX met de `LoadOptions` die we zojuist hebben voorbereid. Het pad kan absoluut of relatief zijn; zorg er gewoon voor dat het bestand bestaat.

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**Wat gebeurt er achter de schermen?**  
Aspose.Words parseert de XML van het document, lost elk `<w:font>`‑element op en controleert de systeem‑lettertypecatalogus (plus eventuele aangepaste mappen die je aan `FontSettings` hebt toegevoegd). Wanneer het een lettertype niet kan vinden, registreert het een waarschuwing — precies wat we later nodig hebben om **ontbrekende lettertypen op te sommen**.

## Stap 3: Door de waarschuwingen itereren en ontbrekende lettertype‑details extraheren  

Met het document in het geheugen bevat de `Warnings`‑collectie elke `FontSubstitutionWarning`. We zullen er doorheen lopen, filteren op het juiste type en een vriendelijk rapport afdrukken.

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**Verwachte output** (ervan uitgaande dat het bron‑document `MyCustomFont` verwijst, dat niet geïnstalleerd is):

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

Let op hoe elke regel je zowel de **get missing font name** (`MyCustomFont`) als de fallback (`Arial`) geeft. Dat is precies de informatie die je nodig hebt om te beslissen of je het originele lettertype wilt insluiten, de auteur om een vervanging wilt vragen, of de substitutie simpelweg accepteert.

## Stap 4: Optioneel – De gegevens verzamelen in een lijst voor verdere verwerking  

Als je het rapport moet exporteren naar CSV, via een API moet verzenden, of gewoon in het geheugen wilt bewaren voor later, kun je de waarschuwingen opslaan in een sterk getypeerde lijst.

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

Nu heb je **ontbrekende lettertypen opgesomd** in een formaat dat elk downstream‑systeem kan gebruiken. Of je nu een dashboard voedt of een audit‑log genereert, de gegevens zijn klaar.

## Stap 5: Randgevallen en veelvoorkomende valkuilen afhandelen  

### Meerdere ontbrekende lettertypen in één run  

Grote bedrijfs‑templates verwijzen vaak naar tientallen aangepaste lettertypen. De waarschuwingencollectie kan omvangrijk worden, maar het iteratiepatroon hierboven schaalt lineair, dus prestaties zijn geen zorg. Zorg er alleen voor dat de output leesbaar blijft — groeperen per pagina of stijl kan nuttig zijn als je een diepere analyse nodig hebt.

### Aangepaste lettertype‑mappen  

Als je lettertypen opslaat in een niet‑standaard map (bijv. een gedeelde netwerkschijf), geef dan Aspose.Words aan waar te zoeken:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

Door dit *vóór* het laden van het document in te stellen, krijgt de bibliotheek de kans om de lettertypen te vinden, waardoor sommige waarschuwingen volledig kunnen verdwijnen.

### Specifieke waarschuwingen onderdrukken  

Soms weet je dat een specifieke substitutie acceptabel is (bijv. een decoratief lettertype dat je zonder problemen wilt vervangen). Je kunt die achteraf filteren:

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### Versie‑compatibiliteit  

De `FontSubstitutionWarningLevel`‑enum is stabiel sinds Aspose.Words 20.12. Als je een oudere versie gebruikt, moet je mogelijk upgraden om de waarschuwing‑niveau‑functie te kunnen gebruiken.

## Volledig werkend voorbeeld  

Hieronder staat het volledige, kant‑klaar programma dat alle bovenstaande stappen bevat. Plak het in een nieuw console‑project, voeg het Aspose.Words‑NuGet‑pakket toe, en laat `docPath` wijzen naar een document dat een ontbrekend lettertype verwijst.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

Het uitvoeren van dit programma zal **lettertypevervangingswaarschuwingen inschakelen**, **ontbrekende lettertypen detecteren**, **get missing font name** ophalen, en **ontbrekende lettertypen opsommen** zowel in de console als in een CSV‑bestand.

## Conclusie  

We hebben zojuist alles behandeld wat je nodig hebt om **lettertypevervangingswaarschuwingen in te schakelen** in Aspose.Words, van de eerste configuratie tot het extraheren van een nette lijst met ontbrekende lettertypen. Door de bovenstaande stappen te volgen kun je je documenten auditen, visuele getrouwheid waarborgen en onaangename verrassingen bij het renderen op een server voorkomen.

Vervolgens kun je de volgende zaken verkennen:

- **Ontbrekende lettertypen insluiten** direct in de output‑PDF of DOCX (gebruik `FontSettings.EmbeddedFonts`).
- **Automatiseren van lettertype‑installatie** op build‑agents op basis van het gegenereerde rapport.
- **Integreren met CI‑pipelines** om builds te laten falen wanneer kritieke lettertypen ontbreken.

Probeer ze uit, en je verandert een eenvoudig waarschuwingssysteem in een volledige lettertype‑beheersworkflow.

Veel programmeerplezier, en moge al je lettertypen gevonden worden!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}