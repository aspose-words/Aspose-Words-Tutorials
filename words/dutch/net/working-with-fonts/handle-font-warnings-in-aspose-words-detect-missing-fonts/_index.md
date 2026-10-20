---
category: general
date: 2026-02-28
description: Leer hoe u fontwaarschuwingen kunt afhandelen en ontbrekende lettertypen
  kunt detecteren in Aspose.Words met C#. Complete stap‑voor‑stap gids met volledige
  code.
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: nl
og_description: Behandel lettertypewaarschuwingen in Aspose.Words en detecteer ontbrekende
  lettertypen met een kant‑en‑klare C#‑voorbeeld. Volg de stappen en bekijk de uitvoer.
og_title: Lettertypewaarschuwingen in Aspose.Words behandelen – Complete gids
tags:
- Aspose.Words
- C#
- Document Loading
title: Lettertypewaarschuwingen afhandelen in Aspose.Words – Ontbrekende lettertypen
  detecteren
url: /nl/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lettertypewaarschuwingen afhandelen in Aspose.Words – Ontbrekende lettertypen detecteren

Heb je ooit **lettertypewaarschuwingen** moeten afhandelen bij het laden van een Word‑document en je afgevraagd waarom sommige tekst er vreemd uitziet? Je bent niet de enige. Ontbrekende lettertypen veroorzaken substitutiewaarschuwingen die stilletjes de visuele lay-out kunnen corrumperen, en als je geen **ontbrekende lettertypen detecteert** zul je nooit weten wat er mis is gegaan.

In deze tutorial laten we je een praktische manier zien om **lettertypewaarschuwingen** af te handelen met behulp van Aspose.Words’ `IWarningCallback`. Aan het einde van de gids kun je elk lettertype‑substitutie‑event spotten, loggen en zelfs beslissen of je het laden wilt afbreken. Geen externe documentatie, alleen een enkel, copy‑paste‑klaar voorbeeld.

## Wat je zult leren

- Stel een aangepaste waarschuwingshandler in die alleen reageert op waarschuwingen voor lettertype‑substitutie.  
- Koppel de handler aan `LoadOptions` zodat elke documentlading erdoorheen gaat.  
- Controleer de output in de console en begrijp wat elke waarschuwing betekent.  

**Voorvereisten**

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.6+).  
- Aspose.Words for .NET geïnstalleerd via NuGet (`Install-Package Aspose.Words`).  
- Een Word‑bestand dat een lettertype gebruikt dat niet op je machine is geïnstalleerd (bijv. een aangepast bedrijfslettertype).  

Als je een van deze mist, haal ze dan nu binnen—anders, laten we beginnen.

## Hoe lettertypewaarschuwingen af te handelen in Aspose.Words

Hieronder staat het volledige, uitvoerbare programma. Het bevat alles van de `using`‑statements tot de `Main`‑methode, zodat je het in een console‑app kunt plakken en **F5** kunt indrukken.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **Verwachte console‑output** (ervan uitgaande dat het document een lettertype gebruikt dat je niet geïnstalleerd hebt):
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

Als het document **geen ontbrekende lettertypen** bevat, verschijnt de waarschuwingsregel nooit—dus je hebt effectief **ontbrekende lettertypen** alleen gedetecteerd wanneer dat nodig was.

### Waarom dit werkt

Aspose.Words gooit een `WarningInfo` voor elk niet‑kritisch probleem dat het tegenkomt tijdens het parseren van een bestand. Door `IWarningCallback` te implementeren krijg je een haak in die pijplijn. De `WarningType.FontSubstitution`‑vlag vertelt je precies wanneer de bibliotheek een aangevraagd lettertype moest vervangen door een fallback. Dit is de meest betrouwbare manier om **lettertypewaarschuwingen** af te handelen, omdat het *tijdens* het laden gebeurt, voordat je het document‑objectmodel aanraakt.

## Ontbrekende lettertypen detecteren zonder je app te breken

Soms wil je een ontbrekend lettertype behandelen als een fatale fout—misschien staan je merkrichtlijnen elke substitutie niet toe. Je kunt de handler aanpassen zodat deze een uitzondering gooit in plaats van alleen te loggen:

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

Nu zal het `try…catch`‑blok rond `new Document(...)` het probleem opvangen, zodat je kunt beslissen of je wilt afbreken, terugvallen of de gebruiker wilt vragen.

## Bonus: Waarschuwingen visualiseren in een UI‑applicatie

Als je een WinForms‑ of WPF‑app bouwt, vervang dan `Console.WriteLine` door een UI‑vriendelijke aanroep:

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

Zo zien eindgebruikers de waarschuwing meteen, en je blijft **lettertypewaarschuwingen** consistent afhandelen op alle platformen.

## Veelvoorkomende valkuilen & pro‑tips

- **Valkuil:** Vergeten `WarningCallback` in te stellen. Het standaardgedrag is om lettertypewaarschuwingen te negeren, dus je ziet ze nooit.  
  **Pro‑tip:** Maak altijd een `LoadOptions`‑instantie aan, zelfs als je alleen de waarschuwingshandler nodig hebt. Het is goedkoop en expliciet.  

- **Valkuil:** De verkeerde pad‑scheidingsteken gebruiken op een niet‑Windows‑OS.  
  **Pro‑tip:** Gebruik `Path.Combine` of een raw string literal (`@"C:\Docs\MissingFont.docx"` werkt op Windows; op Linux gebruik `"/home/user/docs/MissingFont.docx"`).  

- **Valkuil:** Aannemen dat de waarschuwing wordt getriggerd voor ingebedde lettertypen.  
  **Pro‑tip:** Ingebedde lettertypen worden beschouwd als aanwezig, dus er verschijnt geen substitutiewaarschuwing. Test met echt *ontbrekende* lettertypen om de handler in actie te zien.  

- **Valkuil:** Elke waarschuwingstype over‑loggen.  
  **Pro‑tip:** Filter op `WarningType.FontSubstitution` zoals getoond—dit houdt de console schoon en richt zich op het **detect missing fonts**‑scenario.

## Volledig werkend voorbeeld samenvatting

Hier is het volledige programma nogmaals, deze keer zonder commentaar voor wie een schone weergave prefereert:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

Kopieer, plak, voer uit—je console zal nu **lettertypewaarschuwingen** en **ontbrekende lettertypen** automatisch **afhandelen**.

## Volgende stappen

- **Log naar een bestand:** Vervang `Console.WriteLine` door een logger (bijv. NLog) voor productie‑grade tracing.  
- **Batchverwerking:** Loop door een map met documenten en verzamel alle lettertype‑substitutie‑gebeurtenissen in een CSV‑rapport.  
- **Automatische lettertype‑installatie:** Koppel de waarschuwingshandler om ontbrekende lettertypen van een bedrijfsrepository te downloaden voordat het laden doorgaat.  

Elk van deze uitbreidingen bouwt voort op het kernidee van **lettertypewaarschuwingen** afhandelen op een schone, herbruikbare manier.

---

*Happy coding! Als je tegen vreemde problemen aanloopt tijdens het **detect missing fonts**, laat dan een reactie achter. Ik help je graag met het oplossen.*  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}