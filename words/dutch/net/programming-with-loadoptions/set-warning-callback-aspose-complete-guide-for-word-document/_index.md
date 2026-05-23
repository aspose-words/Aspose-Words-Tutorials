---
category: general
date: 2026-05-23
description: Stel de waarschuwingscallback van Aspose in om waarschuwingen voor lettertypevervanging
  vast te leggen in Aspose.Words. Leer over LoadOptions, FontSettings en de implementatie
  van IWarningCallback.
draft: false
keywords:
- set warning callback aspose
- aspose words loadoptions
- aspose fonts substitution
- iwarningcallback implementation
- aspose document loading
language: nl
og_description: Stel een waarschuwing‑callback in Aspose in om lettertypevervanging
  in Aspose.Words te monitoren. Deze tutorial toont LoadOptions, FontSettings en de
  implementatie van de waarschuwing‑handler.
og_title: Waarschuwing-callback instellen Aspose – Stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  headline: set warning callback aspose – Complete Guide for Word Document Loading
  type: TechArticle
- description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  name: set warning callback aspose – Complete Guide for Word Document Loading
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well). -
      A valid Aspose.Words for .NET license or a trial key. - Visual Studio, Rider,
      or any C# editor you prefer. - A sample DOCX (`fontTest.docx`) that references
      a missing font (optional but helpful).'
  - name: Expected console output
    text: 'If `fontTest.docx` references a font that isn’t installed, you’ll see something
      like:'
  - name: When to use a custom LoadOptions
    text: '- **Batch processing** of many files where you want a uniform logging strategy.
      - **Cloud services** that need to report missing fonts back to the caller. -
      **Testing pipelines** that verify documents adhere to a corporate font policy.'
  type: HowTo
tags:
- Aspose.Words
- C#
- FontSettings
title: Waarschuwingscallback instellen in Aspose – Complete gids voor het laden van
  Word‑documenten
url: /nl/net/programming-with-loadoptions/set-warning-callback-aspose-complete-guide-for-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set warning callback aspose – Complete gids voor het laden van Word-documenten

Heb je je ooit afgevraagd hoe je **set warning callback aspose** kunt instellen zodat je nooit meer een waarschuwing voor lettertype‑substitutie mist? Je bent niet de enige. Wanneer een DOCX een lettertype verwijst dat niet geïnstalleerd is, vervangt Aspose.Words het stilletjes, en zonder een juiste callback kun je nooit weten dat er iets is veranderd.

In deze tutorial lopen we stap voor stap door een volledig, uitvoerbaar voorbeeld dat precies laat zien hoe je die waarschuwingen kunt opvangen. Aan het einde begrijp je **Aspose.Words LoadOptions**, hoe je **FontSettings** configureert, en waarom het implementeren van **IWarningCallback** de schoonste manier is om op de hoogte te blijven. Geen poespas—alleen de code die je vandaag in een .NET‑project kunt gebruiken.

## Wat je zult leren

- Hoe je **set warning callback aspose** op een `LoadOptions`‑instantie instelt.  
- De rol van **Aspose.Words LoadOptions** bij het openen van een document.  
- Het configureren van **Aspose fonts substitution**‑afhandeling met `FontSettings`.  
- Het schrijven van een aangepaste **IWarningCallback‑implementatie** om lettertype‑problemen te loggen.  
- Een document veilig laden met de beste praktijken voor **Aspose document loading**.

### Vereisten

- .NET 6.0 of later (de code werkt ook op .NET Framework 4.5+).  
- Een geldige Aspose.Words for .NET‑licentie of een trial‑sleutel.  
- Visual Studio, Rider of een andere C#‑editor naar keuze.  
- Een voorbeeld‑DOCX (`fontTest.docx`) die een ontbrekend lettertype referereert (optioneel maar handig).

> **Pro tip:** Als je geen DOCX met een ontbrekend lettertype hebt, hernoem dan een lettertype in de stijl van het document en zie de waarschuwing afgaan.

## Hoe set warning callback aspose in te stellen voor documentladen

Hieronder staat het volledige, zelfstandige programma. Sla het op als `Program.cs`, herstel de NuGet‑pakketten en voer het uit. De console zal elke lettertype‑substitutie‑waarschuwing die Aspose.Words genereert tijdens het laden van het bestand afdrukken.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// ------------------------------------------------------------
// Step 1: Create a warning handler that implements IWarningCallback
// ------------------------------------------------------------
class FontSubstitutionWarningHandler : IWarningCallback
{
    // This method is called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property tells you which font was substituted.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// ------------------------------------------------------------
// Step 2: Prepare FontSettings (default works for most cases)
// ------------------------------------------------------------
FontSettings fontSettings = new FontSettings();
// You could add custom font folders here if you want to avoid substitution:
// fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// ------------------------------------------------------------
// Step 3: Build LoadOptions and attach our warning callback
// ------------------------------------------------------------
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontSubstitutionWarningHandler()
};

// ------------------------------------------------------------
// Step 4: Load the document using the configured LoadOptions
// ------------------------------------------------------------
try
{
    // Replace the path with the location of your test document.
    Document doc = new Document("YOUR_DIRECTORY/fontTest.docx", loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

### Verwachte console‑uitvoer

Als `fontTest.docx` een lettertype referereert dat niet geïnstalleerd is, zie je iets als:

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Document loaded successfully.
```

Als elk lettertype aanwezig is, wordt alleen de regel *Document loaded successfully* afgedrukt—geen waarschuwingen, geen ruis.

![set warning callback aspose example](image.png "set warning callback aspose example")

## Begrijpen van LoadOptions in Aspose.Words

`LoadOptions` is de toegangspoort tot elke aanpassing die je kunt doen bij **aspose document loading**. Het stelt je in staat om:

1. **Een aangepast `FontSettings` op te geven** – handig wanneer je applicatie eigen lettertypen meelevert.  
2. **Een waarschuwing‑callback toe te voegen** – precies wat we deden om lettertype‑substituties te vangen.  
3. Documentformaatdetectie, wachtwoordafhandeling en meer te regelen.

Omdat `LoadOptions` wordt doorgegeven aan de `Document`‑constructor, worden de instellingen **eenmalig** toegepast, precies op het moment dat het bestand wordt geparseerd. Daarom kunnen we garanderen dat onze waarschuwing‑handler elke substitutie ziet voordat het document in het geheugen wordt opgebouwd.

### Wanneer een aangepaste LoadOptions te gebruiken

- **Batchverwerking** van veel bestanden waarbij je een uniforme logstrategie wilt.  
- **Cloud‑services** die ontbrekende lettertypen moeten rapporteren aan de aanroeper.  
- **Test‑pipelines** die verifiëren of documenten voldoen aan een bedrijfs‑lettertypebeleid.

## Configureren van FontSettings voor Aspose lettertype‑substitutie

Het `FontSettings`‑object bepaalt hoe Aspose.Words lettertypen oplost. Standaard zoekt het in de systeem‑lettermappen en valt vervolgens terug op ingebouwde substituten. Je kunt dit gedrag fijn afstellen:

```csharp
FontSettings fontSettings = new FontSettings();

// Add a folder that contains your corporate fonts.
fontSettings.SetFontsFolder(@"C:\Corporate\Fonts", recursive: true);

// Optionally, map a missing font to a specific substitute.
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "MissingFont", new[] { "Arial", "Times New Roman" });
```

Deze regels zijn optioneel voor het basis‑scenario “set warning callback aspose”, maar ze laten zien hoe je het aantal substitutie‑waarschuwingen kunt **verminderen** door de juiste lettertypen vooraf beschikbaar te stellen.

## Implementeren van IWarningCallback voor waarschuwingen over lettertype‑substitutie

De `IWarningCallback`‑interface is klein—slechts één `Warning`‑methode. Toch geeft het je **volledige controle** over hoe waarschuwingen worden afgehandeld:

- **Log naar een bestand** in plaats van naar de console.  
- **Verzamel waarschuwingen** in een lijst voor latere analyse.  
- **Gooi uitzonderingen** voor kritieke waarschuwingen (bijv. wanneer een vereist lettertype ontbreekt).

Hier is een snel voorbeeld dat waarschuwingen opslaat in een `List<string>`:

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Je kunt vervolgens `handler.Messages` inspecteren na het laden van het document om te bepalen of je de verwerking moet afbreken.

## Een document laden met aangepaste waarschuwingafhandeling (volledige workflow)

Alles samenvoegend ziet het uiteindelijke patroon dat je waarschijnlijk opnieuw zult gebruiken er als volgt uit:

```csharp
// 1️⃣ Create the warning handler.
CollectingWarningHandler handler = new CollectingWarningHandler();

// 2️⃣ Set up FontSettings (add custom fonts if needed).
FontSettings fs = new FontSettings();
fs.SetFontsFolder(@"C:\MyApp\Fonts", true);

// 3️⃣ Build LoadOptions with both FontSettings and the handler.
LoadOptions opts = new LoadOptions
{
    FontSettings = fs,
    WarningCallback = handler
};

// 4️⃣ Load the document.
Document doc = new Document("input.docx", opts);

// 5️⃣ React to any font‑substitution warnings.
if (handler.Messages.Any())
{
    Console.WriteLine("The following fonts were substituted:");
    foreach (var msg in handler.Messages)
        Console.WriteLine("- " + msg);
}
else
{
    Console.WriteLine("No font issues detected.");
}
```

Dit fragment demonstreert de **aspose document loading**‑stroom die je in productie zult gebruiken: configureren, laden, dan reageren. Het patroon schaalt goed, of je nu één bestand verwerkt of door duizenden heen loopt.

## Veelgestelde vragen & randgevallen

**Wat als het document met een wachtwoord beveiligd is?**  
Voeg `Password = "secret"` toe aan de `LoadOptions`‑initializer. De waarschuwing‑callback blijft werken zodra het bestand is ontsleuteld.

**Zal de callback afgaan voor andere waarschuwingssoorten?**  
Ja—`WarningInfo.Type` kan `DocumentStructure`, `UnsupportedFileFormat`, enz. in ons voorbeeld filteren we op `FontSubstitution`, maar je kunt alles loggen door de `if`‑controle te verwijderen.

**Heeft dit invloed op de prestaties?**  
Negentig. De callback wordt alleen aangeroepen wanneer er een waarschuwing optreedt, wat veel minder vaak is dan de normale parse‑stappen.

**Kan ik lettertype‑substitutie volledig uitschakelen?**  
Je kunt `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` instellen, maar dan zal Aspose.Words een uitzondering gooien voor ontbrekende lettertypen in plaats van ze te vervangen.

## Conclusie

Je weet nu precies hoe je **set warning callback aspose** kunt gebruiken om lettertype‑substitutie‑gebeurtenissen te monitoren tijdens de verwerking met **Aspose.Words LoadOptions**. Door `FontSettings` te configureren, een lichte `IWarningCallback` te implementeren en het document met die opties te laden, krijg je volledige zichtbaarheid op alle lettertype‑wijzigingen die Aspose achter de schermen maakt.  

Vanaf hier kun je:

- De waarschuwing‑handler uitbreiden om naar een centrale logging‑service te schrijven.  
- De callback combineren met een aangepaste fallback‑strategie voor lettertypen.  
- Het patroon gebruiken bij het bouwen van een cloud‑API die door de klant geüploade documenten valideert.

Probeer het met je eigen DOCX‑bestanden, pas de `FontSettings` aan, en zie hoe de console je precies vertelt welke lettertypen zijn vervangen. Veel programmeerplezier, en moge je documenten altijd correct worden weergegeven!

## Gerelateerde tutorials

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}