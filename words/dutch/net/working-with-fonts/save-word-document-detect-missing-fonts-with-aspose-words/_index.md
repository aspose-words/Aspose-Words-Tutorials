---
category: general
date: 2026-03-22
description: Sla Word-document op en detecteer ontbrekende lettertypen met Aspose.Words.
  Leer hoe je ontbrekende lettertypen kunt bijhouden en lettertypefouten kunt vastleggen
  in C#.
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: nl
og_description: Opslaan van Word-document en detecteren van ontbrekende lettertypen
  in C#. Deze gids laat zien hoe je ontbrekende lettertypen kunt bijhouden en lettertypefouten
  kunt vastleggen met een waarschuwingscallback.
og_title: Word-document opslaan – Ontdek ontbrekende lettertypen met Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Word-document opslaan – Ontdek ontbrekende lettertypen met Aspose.Words
url: /nl/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-document opslaan – Ontbrekende lettertypen detecteren met Aspose.Words

Heb je ooit **word document opslaan** moeten, maar wist je niet zeker of sommige lettertypen erin de round‑trip zouden overleven? Het gebeurt vaker dan je denkt, vooral wanneer documenten tussen computers met verschillende lettertypebibliotheken reizen. Het goede nieuws? Aspose.Words biedt een ingebouwde manier om **ontbrekende lettertypen te detecteren** terwijl je **word document opslaat**, zodat je ze kunt loggen, waarschuwen of zelfs vervangen voordat het bestand op het scherm van een gebruiker verschijnt.

In deze tutorial lopen we een compleet, kant‑klaar voorbeeld door dat niet alleen een Word-document opslaat, maar ook **ontbrekende lettertypen bijhoudt** en **lettertype‑fouten vastlegt** met behulp van een aangepaste waarschuwingshandler. Aan het einde weet je precies waarom de waarschuwings‑callback belangrijk is, hoe je deze koppelt, en hoe de console‑output eruitziet wanneer een substitutie plaatsvindt. Geen extra poespas—alleen de code die je nu in een .NET‑project kunt plaatsen.

> **Vereisten**  
> • .NET 6 (of een recente .NET Framework) geïnstalleerd  
> • Visual Studio 2022 of je favoriete IDE  
> • Een gelicentieerde kopie van **Aspose.Words for .NET** (de gratis proefversie werkt voor testen)  

Als je die hebt, laten we beginnen.

---

## Word-document opslaan en ontbrekende lettertypen detecteren

Het kernidee is simpel: voordat je `Document.Save` aanroept, wijs je een object toe dat `IWarningCallback` implementeert aan `Document.WarningCallback`. Aspose.Words zal dit object aanroepen voor elke waarschuwing die het tegenkomt, inclusief **font substitution** waarschuwingen die optreden wanneer het bron‑document een lettertype verwijst dat je systeem niet kan vinden.

```csharp
using Aspose.Words;
using Aspose.Words.Warning;

// Step 1: Create a warning handler that prints font substitution messages
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only react to font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// Step 2: Load a document that may contain missing fonts
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Step 3: Register the warning handler with the document
document.WarningCallback = new FontWarningHandler();

// Step 4: Save the document; any font substitution warnings will be output to the console
document.Save("YOUR_DIRECTORY/output.docx");
```

**Wat je zult zien:**  
Als `input.docx` een lettertype verwijst dat niet geïnstalleerd is, print de console iets als:

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

Die regel vertelt je precies welk lettertype ontbrak en wat Aspose.Words in plaats daarvan gebruikte—perfect voor **capturing font errors** voordat je het bestand verzendt.

---

## Ontbrekende lettertypen bijhouden met een waarschuwings‑callback (Stap‑voor‑stap)

### 1️⃣ Installeer Aspose.Words

Open de NuGet‑console van je project en voer uit:

```bash
dotnet add package Aspose.Words
```

Dit haalt de nieuwste stabiele versie op (momenteel 24.10). Het up‑to‑date houden van de bibliotheek zorgt ervoor dat je de nieuwste **detect missing fonts** mogelijkheden en bugfixes krijgt.

### 2️⃣ Definieer de waarschuwings‑handler

Waarom hebben we een aparte klasse nodig? Het implementeren van `IWarningCallback` stelt je in staat om alle waarschuwingslogica op één plek te centraliseren. Je kunt ook naar een bestand loggen, telemetrie verzenden, of een uitzondering gooien als een ontbrekend lettertype een harde fout is voor je workflow.

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only the warnings we care about
        if (info.Type == WarningType.FontSubstitution)
        {
            // Here we simply write to the console,
            // but you could replace this with any logging framework.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **Pro tip:** Als je **track missing fonts** over veel documenten moet bijhouden, sla de berichten dan op in een `List<string>` binnen de handler en maak ze later beschikbaar voor rapportage.

### 3️⃣ Laad je bron‑document

De `Document`‑constructor kan een bestandspad, een stream of zelfs ruwe bytes accepteren. In de meeste gevallen wijs je het naar een `.docx` die je van een gebruiker of een ander systeem hebt ontvangen.

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Als het bestand groot is, overweeg dan `LoadOptions` te gebruiken om lazy loading in te schakelen, wat het geheugenverbruik vermindert.

### 4️⃣ Koppel de callback

Wijs de instantie toe aan `doc.WarningCallback`. Vanaf dat moment zal elke waarschuwing (inclusief lettertype‑substituties) via jouw handler lopen.

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ Sla het document op

Nu kun je veilig `Save` aanroepen. De waarschuwings‑handler wordt **synchronously** uitgevoerd tijdens de opslaan‑operatie, zodat je de output meteen ziet.

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

Als je liever opslaat naar een ander formaat (PDF, HTML, enz.), werkt hetzelfde waarschuwingsmechanisme—Aspose.Words zal nog steeds ontbrekende lettertypen melden vóór de conversie.

---

## Lettertype‑fouten vastleggen – Veelvoorkomende randgevallen

Hoewel de basisstroom de meeste scenario's dekt, lopen real‑world projecten vaak tegen een paar hobbels aan. Hieronder staan enkele variaties die je kunt tegenkomen en hoe je ze afhandelt.

### Ontbrekend lettertype in een header/footer

Headers en footers zijn afzonderlijke knooppunten, maar het waarschuwingssysteem behandelt ze hetzelfde als de hoofdtekst. Geen extra code nodig; de callback wordt ook voor die lettertypen geactiveerd. Zorg er alleen voor dat je het volledige document laadt (het standaardgedrag doet dit).

### Meerdere substituties in één document

Als een document meerdere onbekende lettertypen gebruikt, wordt de handler één keer per substitutie aangeroepen. Om te voorkomen dat de console overspoeld wordt, kun je berichten dedupliceren:

```csharp
class FontWarningHandler : IWarningCallback
{
    private readonly HashSet<string> _seen = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution && _seen.Add(info.Description))
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

### Waarschuwingen omzetten in uitzonderingen

Soms is een ontbrekend lettertype een deal‑breaker. Gooi een uitzondering in de handler om het opslaan af te breken:

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

Onthoud dat je `doc.Save` moet omhullen met een `try/catch`‑blok om de uitzondering netjes af te handelen.

---

## Resultaat verifiëren – Wat te verwachten

Nadat het opslaan voltooid is, open je `output.docx` in Microsoft Word (of een andere compatibele viewer). Je zou dezelfde visuele lay-out als het origineel moeten zien, maar de vervangen lettertypen verschijnen als de fallback die je in de console zag. Om dubbel te controleren kun je:

1. Open **Bestand → Opties → Geavanceerd → Documentinhoud weergeven → Kwaliteit gebruiken (draft)** – dit dwingt Word om eventuele verborgen lettertype‑substituties te tonen.
2. Gebruik Word’s **Lettertypen vervangen** dialoog (`Ctrl+Shift+F`) om te zien welke lettertypen daadwerkelijk zijn ingesloten.

Als alles overeenkomt, heb je succesvol **saved word document** terwijl je **detecting missing fonts** en **capturing font errors** hebt uitgevoerd. 🎉

---

## Volledig werkend voorbeeld (Klaar om te kopiëren‑plakken)

Hieronder staat het volledige programma dat je in een nieuw Console‑App‑project kunt plaatsen. Vervang gewoon `YOUR_DIRECTORY` door een daadwerkelijk mappad op je machine.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warning;

namespace FontWarningDemo
{
    // Step 1: Create a warning handler that prints font substitution messages
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            // Only handle font‑substitution warnings
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Load a document that may contain missing fonts
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3: Register the warning handler with the document
            document.WarningCallback = new FontWarningHandler();

            // Step 4: Save the document; any font substitution warnings will be output to the console
            document.Save("YOUR_DIRECTORY/output.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Verwachte console‑output** (voorbeeld):

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

Dat is het hele verhaal—geen verborgen stappen, geen externe documenten die je moet zoeken.

---

## Conclusie

We hebben je net laten zien hoe je **save word document** kunt uitvoeren terwijl je actief **detect missing fonts**, **track missing fonts**, en **capture font errors** gebruikt via de waarschuwings‑callback van Aspose.Words. Door een kleine `IWarningCallback`‑implementatie te koppelen, krijg je volledige zichtbaarheid op lettertype‑substituties tijdens het opslaan, waardoor je de mogelijkheid hebt om te loggen, te vervangen of af te breken indien nodig.  

Klaar voor de volgende uitdaging? Probeer de handler uit te breiden zodat waarschuwingen naar een gestructureerd JSON‑log worden geschreven, of combineer het met Aspose.PDF om hetzelfde document te converteren terwijl je lettertype‑informatie behoudt. Je kunt ook onderzoeken om ontbrekende lettertypen direct in het uitvoerbestand in te sluiten—Aspose.Words ondersteunt lettertype‑inbedding via `LoadOptions.FontSettings`.  

Probeer het, pas de code aan voor jouw pipeline, en laat ons weten hoe het voor je werkt. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}