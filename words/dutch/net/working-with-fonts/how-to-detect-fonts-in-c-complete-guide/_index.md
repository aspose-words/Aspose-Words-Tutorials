---
category: general
date: 2026-04-02
description: Hoe lettertypen te detecteren in C#‑documenten met Aspose.Words. Leer
  hoe u lettertype‑instellingen configureert en ontbrekende lettertypen efficiënt
  afhandelt.
draft: false
keywords:
- how to detect fonts
- configure font settings
- handle missing fonts
- font substitution warning
- Aspose.Words font handling
language: nl
og_description: Hoe lettertypen te detecteren in C#-documenten met Aspose.Words. Deze
  gids laat zien hoe u lettertype‑instellingen configureert en ontbrekende lettertypen
  afhandelt.
og_title: Hoe lettertypen detecteren in C# – Complete gids
tags:
- C#
- Aspose.Words
- Document Processing
title: Hoe lettertypen in C# te detecteren – Complete gids
url: /nl/net/working-with-fonts/how-to-detect-fonts-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe lettertypen detecteren in C# – Complete gids

Heb je je ooit afgevraagd **hoe je lettertypen** kunt detecteren die ontbreken of worden vervangen wanneer je een Word‑document laadt in .NET? Je bent niet de enige—ontwikkelaars lopen constant tegen het probleem aan dat een document een lettertype aanroept dat niet op de server is geïnstalleerd. Het goede nieuws is dat Aspose.Words je een nette, programmeerbare manier biedt om die hiaten te ontdekken.

In deze tutorial lopen we een hands‑on voorbeeld door dat niet alleen **hoe je lettertypen detecteert** laat zien, maar ook demonstreert hoe je **lettertype‑instellingen configureert** en **ontbrekende lettertypen** elegant afhandelt. Aan het einde heb je een kant‑klaar fragment dat elke waarschuwing over lettertype‑vervanging afdrukt, zodat je kunt loggen, waarschuwen of lettertypen kunt vervangen wanneer dat nodig is.

---

## Wat je nodig hebt

- **Aspose.Words for .NET** (de nieuwste versie werkt het beste; de code hieronder richt zich op .NET 6+)
- Een .NET‑ontwikkelomgeving (Visual Studio, Rider of VS Code)
- Een voorbeeld‑`.docx` dat een lettertype aanroept dat je niet geïnstalleerd hebt (ideaal voor testen)

Er zijn geen extra NuGet‑pakketten nodig naast Aspose.Words, en de oplossing werkt op Windows, Linux en macOS.

---

## Stap 1: Installeer en referentieer Aspose.Words

Voeg eerst de bibliotheek toe aan je project. Het NuGet‑commando is eenvoudig:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Als je op een CI‑server werkt, pin dan de pakketversie om onverwachte breaking changes te vermijden.

---

## Stap 2: Configureer lettertype‑instellingen (en bereid Load‑opties voor)

Voordat je een document opent, kun je Aspose.Words vertellen waar fallback‑lettertypen te vinden zijn. Dit is het **configureer lettertype‑instellingen**‑deel dat voorkomt dat de engine stilletjes lettertypen verwisselt die je misschien niet wilt.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 2: Create a FontSettings object and point it to a folder with fallback fonts
var fontSettings = new FontSettings();

// Example: add a custom folder that contains common Windows fonts
fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);

// You can also embed a default font to use when nothing matches
fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

// Wrap the settings into LoadOptions so Aspose.Words uses them when loading
var loadOptions = new LoadOptions { FontSettings = fontSettings };
```

Waarom? Als het document *Comic Sans* aanroept maar je server alleen *Calibri* heeft, zal Aspose.Words *Calibri* substitueren en een waarschuwing geven. Door het zoekpad te configureren, verminder je ongewenste verrassingen.

---

## Stap 3: Laad het document met de voorbereide opties

Nu openen we daadwerkelijk het bestand. De `LoadOptions` die we in de vorige stap hebben opgebouwd, worden direct doorgegeven aan de `Document`‑constructor.

```csharp
// Step 3: Load the Word file using the configured FontSettings
var docPath = @"C:\Docs\input.docx";
var document = new Document(docPath, loadOptions);
```

Als het bestand niet gevonden kan worden of corrupt is, wordt er een uitzondering gegooid—dus je wilt dit in productcode wellicht in een try/catch wikkelen.

---

## Stap 4: Scan de document‑waarschuwingen op lettertype‑substituties

Aspose.Words verzamelt een lijst met waarschuwingen tijdens het parseren. Daaronder vertelt `FontSubstitutionWarning` je precies welk lettertype is vervangen.

```csharp
// Step 4: Iterate over warnings and look for FontSubstitutionWarning instances
foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fontWarning)
    {
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
}
```

De `Warnings`‑collectie kan ook andere items bevatten (bijv. `DocumentStructureWarning`). Filteren op `FontSubstitutionWarning` zorgt ervoor dat we alleen het **ontbrekende lettertype‑scenario** rapporteren dat ons interesseert.

---

## Stap 5: Zet alles bij elkaar – Een compleet, uitvoerbaar voorbeeld

Hieronder staat het volledige programma. Kopieer‑plak het in een nieuwe console‑app en voer het uit; je ziet elke ontbrekende lettertype‑waarschuwing in de console verschijnen.

```csharp
// Full example: Detect font substitutions in a Word document
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare font settings (configure font settings)
        var fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);
        fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

        // 2️⃣ Build load options with those settings
        var loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document (handle missing fonts gracefully)
        var docPath = @"C:\Docs\input.docx";
        Document document;
        try
        {
            document = new Document(docPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Scan warnings for font substitution events
        bool anySubstitutions = false;
        foreach (WarningInfo warning in document.Warnings)
        {
            if (warning is FontSubstitutionWarning fontWarning)
            {
                anySubstitutions = true;
                Console.WriteLine(
                    $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
            }
        }

        // 5️⃣ Inform the user if everything was fine
        if (!anySubstitutions)
        {
            Console.WriteLine("No font substitutions detected – all fonts were found.");
        }
    }
}
```

**Verwachte output** (voorbeeld):

```
Font 'Times New Roman' was substituted with 'Arial'.
Font 'Comic Sans MS' was substituted with 'Arial'.
```

Als het document alleen lettertypen gebruikt die op de machine bestaan, zie je in plaats daarvan de regel “No font substitutions detected”.

---

## Randgevallen & Veelgestelde vragen

### Wat als het document helemaal **geen waarschuwingen** bevat?

Dat betekent simpelweg dat elk aangevraagd lettertype werd gevonden in de door jou geconfigureerde zoekmappen. De `anySubstitutions`‑vlag in het voorbeeld dekt dit geval.

### Kan ik waarschuwingen **loggen** naar een bestand in plaats van de console?

Absoluut. Vervang de `Console.WriteLine`‑aanroepen door een logger naar keuze (Serilog, NLog, etc.). Het `WarningInfo`‑object biedt ook `WarningType` en `WarningMessage` als je meer details nodig hebt.

### Hoe kan ik bepaalde lettertypen **negeren**, zoals een bedrijfsmerklettertype dat nooit mag worden vervangen?

Je kunt een aangepaste substitutieregel toevoegen:

```csharp
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("MyBrandFont", new[] { "Arial", "Helvetica" });
```

Nu zal Aspose.Words alleen *MyBrandFont* vervangen door de opgegeven alternatieven, en ontvang je nog steeds een waarschuwing die je kunt afhandelen.

### Werkt dit op **Linux** containers?

Ja—zorg er alleen voor dat je een map met de benodigde `.ttf`/`.otf`‑bestanden mount en `SetFontsFolder` ernaar laat wijzen. Aspose.Words is niet afhankelijk van OS‑geïnstalleerde lettertypen.

---

## Visueel overzicht

![how to detect fonts flowchart](detect-fonts.png "Diagram showing the steps to detect fonts in a document")

*Afbeeldingsalt-tekst:* **how to detect fonts** flowchart die configuratie, laden en waarschuwinginspectie illustreert.

---

## Samenvatting – Wat we hebben geleerd

- **Hoe je lettertypen** detecteert die ontbreken of worden vervangen met behulp van Aspose.Words‑waarschuwingen.  
- Hoe je **lettertype‑instellingen configureert** om naar aangepaste lettertype‑mappen te wijzen en een standaard fallback in te stellen.  
- Strategieën om **ontbrekende lettertypen** af te handelen, van loggen tot aangepaste substitutieregels.

Dit alles past in een compacte, zelfstandige console‑app die je in elke .NET‑oplossing kunt dropen.

---

## Volgende stappen & gerelateerde onderwerpen

- **Lettertypen insluiten** direct in het output‑document om toekomstige substituties te vermijden (`SaveOptions` met `EmbedFullFonts`).  
- **Programmeerbare lettertype‑vervanging** – vervang ontbrekende lettertypen door een specifiek alternatief vóór het opslaan.  
- **Prestatie‑optimalisatie** – cache `FontSettings` bij het verwerken van veel documenten in een batch.  

Als je in deze onderwerpen geïnteresseerd bent, zoek dan naar *configure font settings* en *handle missing fonts*—die leiden je naar diepere duiken in lettertype‑beheer met Aspose.Words.

---

Veel plezier met coderen! Heb je een vreemd lettertype‑randgeval? Laat een reactie achter, en we lossen het samen op.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}