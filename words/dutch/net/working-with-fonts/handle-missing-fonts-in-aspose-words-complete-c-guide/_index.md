---
category: general
date: 2026-03-14
description: Verwerk ontbrekende lettertypen snel met Aspose.Words. Leer hoe u waarschuwingen
  voor lettertypevervanging kunt vastleggen, LoadOptions kunt configureren en weergaveproblemen
  kunt voorkomen.
draft: false
keywords:
- handle missing fonts
- Aspose.Words
- font substitution
- LoadOptions
- DocumentWarnings
- C# document loading
language: nl
og_description: Omgaan met ontbrekende lettertypen in Aspose.Words met behulp van
  een waarschuwingenverzamelaar. Deze tutorial laat stap‑voor‑stap zien hoe je lettertypevervangingen
  kunt detecteren en loggen.
og_title: Ontbrekende lettertypen in Aspose.Words behandelen – Complete C#-gids
tags:
- Aspose
- C#
- Fonts
- DocumentProcessing
title: Omgaan met ontbrekende lettertypen in Aspose.Words – Complete C#‑gids
url: /nl/net/working-with-fonts/handle-missing-fonts-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ontbrekende lettertypen verwerken in Aspose.Words – Complete C#-gids

Heb je ooit **ontbrekende lettertypen** moeten verwerken bij het laden van een Word‑document en je afgevraagd waarom je PDF‑ of afbeeldingoutput er niet goed uitziet? Je bent niet de enige. Ontbrekende lettertypebestanden zijn een stille boosdoener die een perfect ontworpen rapport in een rommelige puinhoop kan veranderen.  

Het goede nieuws? Aspose.Words biedt een nette manier om die font‑substitutie‑gebeurtenissen op te vangen, te loggen en zelfs een fallback‑lettertype te gebruiken als je dat wilt. In deze tutorial lopen we stap voor stap door een compleet, kant‑klaar voorbeeld dat precies laat zien hoe je een waarschuwingenverzamelaar instelt, deze koppelt aan `LoadOptions` en een document laadt dat mogelijk ontbrekende lettertypen bevat.

Aan het einde van deze gids kun je:

* Elke font‑substitutie detecteren die tijdens het laden van een document plaatsvindt.  
* Een vriendelijke console‑melding (of een logger) weergeven voor elk ontbrekend lettertype.  
* De oplossing uitbreiden om lettertypen te vervangen, indien nodig.  

**Prerequisites** – je hebt nodig:

* .NET 6.0 of later (de code werkt ook met .NET Core en .NET Framework).  
* Het Aspose.Words for .NET NuGet‑pakket (huidige versie 23.11).  
* Een Word‑bestand dat opzettelijk een lettertype aanroept dat niet op je machine geïnstalleerd is – we noemen het `doc-with-missing-font.docx`.  

Als je al vertrouwd bent met C# en een project hebt opgezet, kun je direct naar de code springen. Anders, lees verder; we behandelen eerst de kleine setup‑stappen.

---

## Waarom het verwerken van ontbrekende lettertypen belangrijk is

Wanneer Aspose.Words een document laadt, probeert het elke glyph te koppelen aan een lettertype dat op de machine is geïnstalleerd. Als het exacte lettertype niet gevonden wordt, vervangt het stilletjes de dichtstbijzijnde match. Die vervanging kan regelhoogtes, kerning en zelfs het verdwijnen van tekens beïnvloeden. Door het `WarningType.FontSubstitution`‑event vast te leggen, krijg je een helder beeld van **wat** er is vervangen en **waarom**, wat essentieel is voor:

* Het behouden van merkconsistentie (je corporate lettertype moet precies zo verschijnen als ontworpen).  
* Het debuggen van PDF‑conversieproblemen – vaak is een ontbrekend lettertype de boosdoener.  
* Het bouwen van geautomatiseerde document‑pipelines waarbij je problematische bestanden moet markeren voor handmatige controle.

Nu het “waarom” duidelijk is, duiken we in het **hoe**.

---

## Stap 1 – Stel de waarschuwingenverzamelaar in

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a collector that will receive warning events.
DocumentWarnings fontWarnings = new DocumentWarnings();

// Subscribe to the Warning event.
fontWarnings.Warning += (sender, e) =>
{
    // We only care about font substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Log the original font name that was missing.
        Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
    }
};
```

**Wat gebeurt er?**  
* `DocumentWarnings` is een dunne wrapper rond de callback‑interface.  
* De lambda controleert `e.WarningType` zodat we irrelevante waarschuwingen (zoals verouderde functies) negeren.  
* `e.WarningInfo` bevat de naam van het ontbrekende lettertype, die we naar de console schrijven.  

*Pro tip*: Vervang `Console.WriteLine` door een gestructureerde logger (Serilog, NLog) in productie – zo krijg je automatisch tijdstempels en log‑niveaus.

---

## Stap 2 – Koppel de verzamelaar aan LoadOptions

```csharp
// Configure load options to use our warning callback.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = fontWarnings
};
```

**Waarom LoadOptions gebruiken?**  
Naast waarschuwingen laat `LoadOptions` je wachtwoordafhandeling, codering en zelfs aangepaste resource‑loading regelen. Hier focussen we op het waarschuwingsgedeelte, maar hetzelfde patroon werkt voor andere callbacks.

---

## Stap 3 – Laad het document met de geconfigureerde opties

```csharp
// Path to the document that may reference missing fonts.
string docPath = Path.Combine(
    Environment.CurrentDirectory,
    "doc-with-missing-font.docx");

// Load the document using the previously configured LoadOptions.
Document document = new Document(docPath, loadOptions);
```

Als je dit fragment uitvoert met een document dat bijvoorbeeld *Calibri Light* aanroept terwijl je testmachine alleen *Calibri* heeft, krijg je een output die er ongeveer zo uitziet:

```
Font 'Calibri Light' was substituted.
```

Dat is de volledige detectielus – simpel, maar krachtig.

---

## Stap 4 – (Optioneel) Vervang ontbrekende lettertypen door een bekende vervanger

```csharp
// Create FontSettings and map any missing font to Arial.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "*", // wildcard – applies to any missing font
    new[] { "Arial" } // fallback font(s)
);

// Apply the FontSettings to the document.
document.FontSettings = fontSettings;

// Now re-save the document; all missing fonts will render as Arial.
document.Save("output-with-fallback.pdf");
Console.WriteLine("Document saved with fallback font applied.");
```

**Uitleg**  
* Het wildcard `"*"` vertelt Aspose.Words om *elk* ontbrekend lettertype op dezelfde manier te behandelen.  
* Je kunt ook specifieke lettertypen individueel mappen als je fijnmazige controle nodig hebt.  
* Na het instellen van `document.FontSettings` respecteert elke daaropvolgende rendering (PDF, afbeelding, HTML) de substitutie.

---

## Volledig werkend voorbeeld

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        try
        {
            // -------------------------------------------------
            // Step 1: Create a warnings collector.
            // -------------------------------------------------
            DocumentWarnings fontWarnings = new DocumentWarnings();
            fontWarnings.Warning += (sender, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
                }
            };

            // -------------------------------------------------
            // Step 2: Attach the collector to LoadOptions.
            // -------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = fontWarnings
            };

            // -------------------------------------------------
            // Step 3: Load the document (may contain missing fonts).
            // -------------------------------------------------
            string docPath = Path.Combine(
                Environment.CurrentDirectory,
                "doc-with-missing-font.docx");

            Document doc = new Document(docPath, loadOptions);

            // -------------------------------------------------
            // Step 4 (optional): Apply a fallback font.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
                "*", new[] { "Arial" });

            doc.FontSettings = fontSettings;

            // Save the result to verify the substitution.
            string outPath = Path.Combine(
                Environment.CurrentDirectory,
                "output-with-fallback.pdf");

            doc.Save(outPath);
            Console.WriteLine($"Document saved to '{outPath}'.");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

**Verwachte output** (wanneer een ontbrekend lettertype wordt gedetecteerd):

```
Font 'Times New Roman PS' was substituted.
Document saved to 'C:\MyProject\output-with-fallback.pdf'.
```

Als het bron‑document al alle benodigde lettertypen bevat, verschijnt de waarschuwingsregel simpelweg niet – niets om je zorgen over te maken.

---

## Veelgestelde vragen & randgevallen

| Vraag | Antwoord |
|-------|----------|
| **Wat als ik alleen wil loggen en niet lettertypen wil vervangen?** | Sla het `FontSettings`‑blok volledig over; de waarschuwingenverzamelaar alleen is voldoende. |
| **Kan ik waarschuwingen naar een bestand omleiden?** | Ja – vervang `Console.WriteLine` door `File.AppendAllText("font-warnings.log", …)`. |
| **Werkt dit voor DOC, DOCX en ODT?** | Absoluut. `LoadOptions` geldt voor alle formaten die door Aspose.Words worden ondersteund. |
| **Wat gebeurt er met aangepaste lettertypen die in het document zijn ingebed?** | Ingebedde lettertypen omzeilen het substitutiemechanisme; ze worden gebruikt zoals ze zijn. |
| **Is er een prestatie‑impact?** | De overhead is minimaal – slechts één callback per ontbrekend lettertype. Bij grote batches kun je overwegen om waarschuwingen te aggregeren in plaats van per gebeurtenis te schrijven. |

---

## Conclusie

We hebben laten zien **hoe je ontbrekende lettertypen** in Aspose.Words kunt afhandelen door een `DocumentWarnings`‑verzamelaar te koppelen aan `LoadOptions`, eventueel een fallback‑lettertype in te stellen en het resultaat op te slaan. Dit patroon geeft volledige inzage in font‑substitutie‑events, waardoor je de visuele consistentie behoudt bij PDF‑, afbeelding‑ of HTML‑conversies.

Mogelijke vervolgstappen:

* Integreer de waarschuwingenverzamelaar met een gecentraliseerd logging‑framework.  
* Bouw een UI‑dashboard dat documenten met ontbrekende lettertypen lijst voor batchverwerking.  
* Combineer deze aanpak met Aspose.PDF om te verifiëren dat de gegenereerde PDF‑bestanden daadwerkelijk het fallback‑lettertype gebruiken.  

Voel je vrij om te experimenteren – verwissel `"Arial"` voor `"Tahoma"` of laad een andere documentenset. Het kernidee blijft hetzelfde: vang de waarschuwing, handel ernaar, en zorg dat je documenten er precies uitzien zoals bedoeld.

Veel plezier met coderen! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}