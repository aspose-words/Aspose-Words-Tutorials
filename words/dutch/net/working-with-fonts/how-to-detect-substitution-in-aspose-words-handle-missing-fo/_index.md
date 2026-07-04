---
category: general
date: 2026-04-24
description: Hoe detecteer je vervanging van ontbrekende lettertypen in Aspose.Words
  met C#. Deze gids laat zien hoe je ontbrekende lettertypen betrouwbaar kunt afhandelen
  met FontSettings‑waarschuwingen.
draft: false
keywords:
- how to detect substitution
- handle missing fonts
- Aspose.Words font warnings
- C# missing font detection
- FontSettings event handling
language: nl
og_description: Hoe detecteer je het substitueren van ontbrekende lettertypen in Aspose.Words
  met C#. Leer hoe je ontbrekende lettertypen kunt afhandelen met FontSettings‑waarschuwingen.
og_title: Hoe Substitutie in Aspose.Words Detecteren – Complete Gids
tags:
- Aspose.Words
- C#
- Fonts
- .NET
title: Hoe substitutie detecteren in Aspose.Words – Ontbrekende lettertypen afhandelen
url: /nl/net/working-with-fonts/how-to-detect-substitution-in-aspose-words-handle-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe Substitutie Detecteren in Aspose.Words – Ontbrekende Lettertypen Afhandelen

Heb je je ooit afgevraagd **hoe je substitutie kunt detecteren** wanneer een document een lettertype probeert te gebruiken dat niet op je server is geïnstalleerd? Het is een veelvoorkomend pijnpunt, vooral wanneer je PDF‑ of Word‑bestanden genereert in een geautomatiseerde pipeline. Het goede nieuws is dat Aspose.Words een ingebouwde hook biedt om precies die situatie te signaleren, en je kunt ook **ontbrekende lettertypen** op een nette manier **afhandelen**.

In deze tutorial lopen we een real‑world voorbeeld door dat laat zien **hoe je substitutie kunt detecteren** via het `FontSettings.Warning`‑event, en we leggen uit hoe je **ontbrekende lettertypen** kunt **afhandelen** zonder je verwerkingsstroom te breken. Aan het einde heb je een kant‑klaar fragment, een duidelijk begrip van waarom elke regel belangrijk is, en een paar tips om de typische valkuilen te vermijden.

## Voorvereisten

- .NET 6.0 of later (de code werkt ook op .NET Framework)  
- Aspose.Words for .NET (NuGet‑pakket `Aspose.Words`) – versie 23.11 of nieuwer  
- Een voorbeeld‑document dat een lettertype referereert dat je niet geïnstalleerd hebt (bijv. `MissingFont.docx`)  
- Visual Studio, VS Code, of een andere C#‑IDE naar keuze  

Er is geen extra configuratie nodig naast het toevoegen van het NuGet‑pakket.

---

## Hoe Substitutie Detecteren met FontSettings

De kern van **hoe substitutie te detecteren** ligt in het `FontSettings.Warning`‑event. Wanneer Aspose.Words een aangevraagd lettertype niet kan vinden, wordt er een `WarningType.FontSubstitution`‑waarschuwing gegenereerd. Door je op dit event te abonneren krijg je een realtime‑melding, inclusief de oorspronkelijke lettertype‑naam en het lettertype dat als fallback is gebruikt.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable a custom FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Step 2: Hook into the FontSettings warning event – this is where we detect substitution.
loadOptions.FontSettings.Warning += (sender, e) =>
{
    // We only care about font‑substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Output the warning to the console – you could log it or collect it in a list.
        Console.WriteLine($"⚠️ Font substituted: {e.Message}");
    }
};

// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Waarom dit werkt:**  
- `LoadOptions.FontSettings` vertelt Aspose.Words om het `FontSettings`‑object te gebruiken dat je zojuist hebt aangemaakt.  
- Abonneren op `Warning` geeft je één centrale plek om *alle* lettertype‑gerelateerde problemen te monitoren, niet alleen ontbrekende lettertypen.  
- Het filter `WarningType.FontSubstitution` zorgt ervoor dat je alleen reageert op het exacte scenario waarin je geïnteresseerd bent – de essentie van **hoe substitutie te detecteren**.

### Verwachte Output

Het uitvoeren van de bovenstaande code met een document dat een niet‑bestaand lettertype referereert, geeft iets als volgt weer:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Als het document alleen geïnstalleerde lettertypen gebruikt, blijft de console stil – een duidelijk signaal dat **hoe substitutie te detecteren** geslaagd is zonder valse alarmen.

---

## Ontbrekende Lettertypen Gracieus Afhandelen

Het detecteren van een substitutie is slechts de helft van de strijd; je hebt ook een strategie nodig om **ontbrekende lettertypen** af te handelen zodat de uiteindelijke output er zoals bedoeld uitziet. Hieronder staan drie praktische benaderingen die je kunt combineren.

### 1. Een Fallback‑Lettertype‑Map Opgeven

Aspose.Words kan extra mappen doorzoeken op lettertypen. Door het te wijzen op een map die de meest voorkomende lettertypen bevat die je verwacht, verklein je de kans op substitutie volledig.

```csharp
// Assume you have a folder "FallbackFonts" with Arial, Times New Roman, etc.
loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

**Waarom:** Wanneer het oorspronkelijke lettertype ontbreekt, heeft Aspose.Words nu een bekende set alternatieven, wat vaak resulteert in een voorspelbaarder visueel resultaat.

### 2. Ontbrekende Lettertypen Programma­matig Vervangen

Als je volledige controle wilt, kun je het ontbrekende lettertype na detectie vervangen door een specifiek lettertype.

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("Comic Sans MS", new[] { "Arial", "Helvetica" });
```

**Waarom:** Dit vertelt de engine precies welke lettertypen geprobeerd moeten worden, zodat je bedrijfsbranding of toegankelijkheidsnormen kunt afdwingen.

### 3. Loggen en Afbreken (Wanneer Substitutie Onacceptabel Is)

Soms betekent een ontbrekend lettertype dat het document ongeldig is voor jouw use‑case (bijv. juridische formulieren). In dat scenario kun je een uitzondering gooien zodra een substitutie optreedt.

```csharp
loadOptions.FontSettings.Warning += (sender, e) =>
{
    if (e.WarningType == WarningType.FontSubstitution)
        throw new InvalidOperationException($"Critical font missing: {e.Message}");
};
```

**Waarom:** Direct falen voorkomt downstream‑fouten, zoals scheefstaande tabellen of gebroken handtekeningen.

---

## Volledig Werkend Voorbeeld – Alle Stappen Gecombineerd

Hieronder vind je een enkel, kant‑klaar programma dat **hoe substitutie te detecteren** *en* verschillende manieren om **ontbrekende lettertypen** af te handelen demonstreert. Voel je vrij om de secties die je niet nodig hebt uit te commentariëren.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Set up LoadOptions with a fresh FontSettings.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // 2️⃣ OPTIONAL: Add a fallback folder with extra fonts.
        // -------------------------------------------------
        // loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", true);

        // -------------------------------------------------
        // 3️⃣ OPTIONAL: Define explicit substitution rules.
        // -------------------------------------------------
        // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
        //     "Comic Sans MS", new[] { "Arial", "Helvetica" });

        // -------------------------------------------------
        // 4️⃣ Subscribe to the warning event – the heart of how to detect substitution.
        // -------------------------------------------------
        loadOptions.FontSettings.Warning += (sender, e) =>
        {
            if (e.WarningType == WarningType.FontSubstitution)
            {
                // Log the warning – you could also collect it in a list for later analysis.
                Console.WriteLine($"⚠️ Font substituted: {e.Message}");

                // Uncomment to abort on any substitution.
                // throw new InvalidOperationException($"Missing font detected: {e.Message}");
            }
        };

        // -------------------------------------------------
        // 5️⃣ Load the document; the warning handler fires automatically.
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // 6️⃣ Save the result – you’ll see the substituted font in the output file.
        // -------------------------------------------------
        string outPath = @"YOUR_DIRECTORY/Processed.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Wat je kunt verwachten:**  
- Als `MissingFont.docx` een lettertype referereert dat niet op de machine staat, print de console de substitutie‑waarschuwing.  
- Het opgeslagen `Processed.docx` gebruikt het fallback‑lettertype dat je hebt geconfigureerd (of de standaard van de bibliotheek).  
- Er verschijnen geen ongevangen uitzonderingen, tenzij je bewust afbreekt bij substitutie.

---

## Veelgestelde Vragen & Randgevallen

| Vraag | Antwoord |
|----------|--------|
| *Wat als het document veel ontbrekende lettertypen bevat?* | Het waarschuwings‑event wordt getriggerd voor **elke** substitutie, dus je ziet meerdere regels. Je kunt ze aggregeren in een lijst voor een samenvattend rapport. |
| *Werkt dit ook bij PDF‑conversie?* | Absoluut. Dezelfde `FontSettings` worden gerespecteerd wanneer je `doc.Save("out.pdf")` aanroept. De substitutie‑waarschuwing wordt nog steeds gegenereerd, zodat je de visuele getrouwheid van de PDF kunt verifiëren. |
| *Kan ik substitutie detecteren nadat het document al geladen is?* | Niet direct. De waarschuwing wordt gegenereerd **tijdens** het laden of opslaan. Als je een post‑load analyse nodig hebt, vang dan de waarschuwingen op in een collectie tijdens de laadfase. |
| *Wat als er aangepaste lettertypen in de DOCX zijn ingebed?* | Ingebedde lettertypen worden beschouwd als aanwezig, dus er treedt geen substitutie op. Als het ingebedde lettertype corrupt is, genereert Aspose.Words nog steeds een waarschuwing, die je op dezelfde manier kunt opvangen. |
| *Is er een prestatie‑impact?* | Minimalistisch. De waarschuwingscontrole is lichtgewicht; de echte kosten liggen bij het laden van het document zelf. Het toevoegen van een lettertype‑map kan de zoektijd iets verhogen, maar alleen bij de eerste load. |

---

## Pro‑Tips & Valkuilen om te Vermijden

- **Pro tip:** Zet altijd `recursive: true` wanneer je naar een map met veel lettertypen wijst; anders worden sub‑mappen genegeerd.  
- **Let op:** Hoofdlettergevoeligheid op Linux. Lettertype‑namen zijn hoofdletter‑onafhankelijk op Windows, maar niet op Linux, dus gebruik de exacte naam of voeg beide varianten toe.  
- **Onthoud:** Als je in een container‑omgeving draait, zorg er dan voor dat de lettertype‑map onderdeel is van de image of tijdens runtime wordt gemount.  
- **Tip:** Sla waarschuwingen op in een `List<string>` als je een samenvatting aan eindgebruikers wilt tonen of wilt loggen naar een monitoring‑systeem.  

---

## Conclusie

We hebben behandeld **hoe substitutie van ontbrekende lettertypen** in Aspose.Words te detecteren, je verschillende manieren laten zien om **ontbrekende lettertypen** af te handelen, en een compleet, uitvoerbaar voorbeeld geleverd dat je in elk .NET‑project kunt plakken. Door gebruik te maken van het `FontSettings.Warning`‑event krijg je realtime inzicht in lettertype‑problemen, en met fallback‑mappen of expliciete substitutieregels houd je je output er precies uitzien zoals je verwacht.

Klaar voor de volgende stap? Probeer de oplossing uit te breiden zodat het fallback‑lettertype automatisch wordt ingebed in de gegenereerde PDF, of koppel de waarschuwingshandler aan een gecentraliseerde logging‑service voor grootschalige document‑pipelines. De patronen die we vandaag hebben besproken — event‑gedreven detectie, gracieuze fallback, en expliciete foutafhandeling — zijn toepasbaar op vele andere Aspose‑API’s, zodat je nu uitgerust bent om lettertype‑gerelateerde uitdagingen overal aan te pakken.

Heb je meer vragen over lettertype‑afhandeling, PDF‑conversie, of Aspose.Words‑trucs? Laat een reactie achter hieronder, en happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}