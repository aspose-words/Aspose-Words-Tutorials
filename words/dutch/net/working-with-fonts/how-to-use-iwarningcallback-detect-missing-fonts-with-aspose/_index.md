---
category: general
date: 2026-06-24
description: Hoe IWarningCallback te gebruiken om ontbrekende lettertypen in Aspose.Words‑documenten
  te detecteren. Leer een volledig, uitvoerbaar voorbeeld en best practices.
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: nl
og_description: Hoe IWarningCallback te gebruiken om ontbrekende lettertypen in Aspose.Words
  te detecteren. Volg de stapsgewijze handleiding voor een volledige, productieklare
  oplossing.
og_title: Hoe IWarningCallback te gebruiken – Detecteer ontbrekende lettertypen
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: Hoe IWarningCallback te gebruiken – Detecteer ontbrekende lettertypen met Aspose.Words
url: /nl/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe IWarningCallback te gebruiken – Ontbrekende lettertypen detecteren met Aspose.Words

Het gebruik van **IWarningCallback** is essentieel wanneer je werkt met Aspose.Words en **ontbrekende lettertypen** in een DOCX‑bestand moet **detecteren**. In deze gids lopen we een volledig, copy‑and‑paste‑voorbeeld door dat precies laat zien hoe je IWarningCallback gebruikt om waarschuwingen voor lettertype‑substitutie op te vangen, waarom dit belangrijk is, en wat je moet doen zodra je ze hebt vastgelegd.

Als je ooit een document hebt geopend en onleesbare tekst zag omdat een aangepast lettertype niet geïnstalleerd was, ken je die frustratie. Aan het einde van deze tutorial heb je een betrouwbare manier om die problemen programmeerbaar te detecteren, te loggen, of zelfs automatisch een fallback‑lettertype toe te passen.

## Wat je zult leren

- Het doel van **IWarningCallback** en wanneer je het moet gebruiken.  
- Hoe je een aangepaste waarschuwing‑collector implementeert die **detect missing fonts**‑gebeurtenissen isoleert.  
- De collector koppelen aan **LoadOptions** zodat elke document‑load wordt gemonitord.  
- De output verifiëren en randgevallen afhandelen (meerdere ontbrekende lettertypen, stille waarschuwingen, enz.).  

### Vereisten

- .NET 6.0 of later (de code werkt ook op .NET Framework 4.6+).  
- Aspose.Words for .NET geïnstalleerd via NuGet (`Install-Package Aspose.Words`).  
- Een DOCX‑bestand dat een lettertype verwijst dat niet aanwezig is op de machine (bijv. `DocumentWithMissingFont.docx`).  

Er zijn geen extra bibliotheken nodig—alles zit binnen Aspose.Words.

---

## Hoe IWarningCallback te gebruiken om ontbrekende lettertypen te detecteren in Aspose.Words

Hieronder staat het **volledige, uitvoerbare programma**. Kopieer het naar een nieuw console‑project, pas het bestandspad aan, en voer het uit. Je ziet console‑output voor elke ontbrekende‑lettertype‑waarschuwing.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Verwachte uitvoer

Als `DocumentWithMissingFont.docx` een lettertype met de naam *“MyFancyFont”* verwijst dat niet geïnstalleerd is, zie je iets als:

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

Elke regel die begint met **[Missing Font]** wordt gegenereerd door onze **IWarningCallback**‑implementatie, wat bewijst dat we succesvol **detect missing fonts**.

---

## Stap 1: Implementeer de IWarningCallback‑interface

Waarom hebben we een aangepaste klasse nodig? Aspose.Words geeft **waarschuwingen** om verschillende redenen—bestandsformaatproblemen, verouderde functies, en, het belangrijkste voor ons, lettertype‑substitutie. Door `IWarningCallback` te implementeren, krijgen we een hook die elke waarschuwing ontvangt zodra deze optreedt. Filteren op `WarningType.FontSubstitution` isoleert het specifieke scenario waarin een lettertype ontbreekt.

**Pro tip:** Als je *alle* waarschuwingen voor diagnostiek wilt vastleggen, verwijder dan simpelweg de `if`‑check en log elke `info.Type`.

## Stap 2: Verbind de callback met LoadOptions

`LoadOptions` is de poort die Aspose.Words vertelt hoe het binnenkomende document moet behandelen. Door `WarningCallback` in te stellen op een instantie van onze collector, is de callback actief voor de volledige laadoperatie. Je kunt hetzelfde `LoadOptions`‑object hergebruiken voor meerdere documenten, wat handig is in batch‑verwerkings‑pipelines.

**Veelgestelde vraag:** *Wat gebeurt er als ik een document laad zonder LoadOptions op te geven?*  
Antwoord: Aspose.Words zal nog steeds intern waarschuwingen genereren, maar zonder een callback worden ze stilletjes weggegooid, en verlies je de kans om **detect missing fonts**.

## Stap 3: Laad een document en vang ontbrekende lettertype‑waarschuwingen op

De `Document`‑constructor die een bestandspad en `LoadOptions` accepteert, doet het zware werk. Terwijl het bestand wordt geparseerd, activeert elk ontbrekend lettertype onze `FontWarningCollector.Warning`‑methode. De console‑output bewijst dat het mechanisme werkt.

**Randgeval:** Een enkel document kan meerdere afwezige lettertypen refereren. De callback wordt één keer per ontbrekend lettertype geactiveerd, dus je ziet meerdere regels—perfect voor het opbouwen van een uitgebreide rapportage.

## Waarom IWarningCallback gebruiken in plaats van handmatige lettertype‑controles?

Je zou handmatig de `Run.Font`‑eigenschappen van het document kunnen doorzoeken na het laden, maar dat vereist dat het document eerst succesvol wordt geladen—iets dat mislukt als het lettertype volledig onbeschikbaar is. Het waarschuwingssysteem werkt **voordat** enige substitutie plaatsvindt, waardoor je een echt beeld krijgt van wat er ontbreekt.

Bovendien wordt de callback uitgevoerd **als onderdeel van de laad‑pipeline**, wat betekent dat je vroegtijdig kunt afbreken, lettertypen on‑the‑fly kunt vervangen, of gedetailleerde diagnostiek kunt loggen zonder extra passes over de documentboom.

## Meerdere ontbrekende lettertypen elegant afhandelen

Als je veel ontbrekende lettertypen verwacht, overweeg dan om ze te verzamelen in een collectie:

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

Na het laden kun je over `MissingFonts` itereren en ze bijvoorbeeld naar een CSV‑bestand schrijven voor het ontwerpteam.

## Bonus: Waarschuwingen loggen naar een bestand

Console‑output is prima voor demo’s, maar productcode logt meestal naar een persistente opslag. Vervang de `Console.WriteLine`‑aanroep door iets als:

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

Nu heb je een audit‑trail die later kan worden bekeken, wat voldoet aan compliance‑vereisten.

## Conclusie

We hebben behandeld **hoe IWarningCallback te gebruiken** om **ontbrekende lettertypen** in Aspose.Words te **detecteren**, van het implementeren van de callback tot het koppelen ervan aan `LoadOptions` en het afhandelen van de resulterende waarschuwingen. Deze aanpak geeft je realtime inzicht in lettertype‑gerelateerde problemen, zodat je kunt loggen, vervangen of gebruikers kunt waarschuwen voordat het document wordt gerenderd.

Volgende stappen die je kunt verkennen:

- **Fallback fonts:** programmeerbaar een standaardlettertype toewijzen wanneer een substitutie plaatsvindt.  
- **Batch processing:** een map met documenten doorlopen, waarbij dezelfde `AggregatingFontCollector` wordt hergebruikt.  
- **User feedback:** ontbrekende‑lettertype‑waarschuwingen in een UI tonen in plaats van in de console.

Probeer het in je eigen project—geen mysterieuze onleesbare tekst meer, alleen duidelijke, bruikbare diagnostiek. Happy coding!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe DOCX te laden en ontbrekende lettertypen te detecteren – Complete C#‑gids](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [Hoe lettertypen te detecteren in Aspose.Words – Waarschuwingen & instellingen afhandelen](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Hoe LoadOptions te gebruiken in Aspose.Words – Complete gids](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}