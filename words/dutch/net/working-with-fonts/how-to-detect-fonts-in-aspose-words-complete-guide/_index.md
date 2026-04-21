---
category: general
date: 2026-04-21
description: Leer hoe u lettertypen detecteert, waarschuwingen vastlegt, een callback
  configureert en waarschuwingen opsomt met Aspose.Words in C#. Stapsgewijze gids
  voor betrouwbare lettertypeafhandeling.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: nl
og_description: Hoe detecteer je lettertypen in Aspose.Words? Deze tutorial laat zien
  hoe je waarschuwingen kunt vastleggen, een callback kunt configureren en waarschuwingen
  kunt enumereren in C#.
og_title: Hoe lettertypen detecteren in Aspose.Words – Complete gids
tags:
- Aspose.Words
- C#
- Document Processing
title: Hoe lettertypen detecteren in Aspose.Words – Complete gids
url: /nl/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe lettertypen te detecteren in Aspose.Words – Complete gids

Heb je je ooit afgevraagd **hoe je lettertypen** kunt detecteren die ontbreken wanneer je een Word‑document laadt? Het is een scenario dat vaker voorkomt dan je zou willen, vooral bij het werken met legacy‑bestanden of cross‑platform implementaties. In deze tutorial lopen we een compleet, uitvoerbaar voorbeeld door dat **waarschuwingen vastlegt**, **een callback configureert**, en **waarschuwingen opsomt** zodat je altijd weet welke lettertypen zijn vervangen.

We gebruiken Aspose.Words for .NET (v24.9 op het moment van schrijven) en gewone C#. Geen externe services, geen magie—alleen de API en een paar regels code. Aan het einde kun je elke lettertype‑vervanging opsporen, loggen, en zelfs beslissen of je het laden moet afbreken als een cruciaal lettertype ontbreekt.  

### Wat je nodig hebt
- **Aspose.Words for .NET** (install via NuGet: `Install-Package Aspose.Words`)
- .NET 6.0 of later (de code werkt ook op .NET Framework)
- Een voorbeeld‑DOCX die een lettertype verwijst dat niet op de machine aanwezig is (bijv. “MyCustomFont.ttf”)
- Visual Studio, Rider, of een C#‑editor naar keuze

> **Pro tip:** Als je geen document met ontbrekende lettertypen hebt, hernoem dan eenvoudig een lettertype‑bestand op je systeem of bewerk de DOCX‑XML om te verwijzen naar een niet‑bestaande lettertype‑familie.

---

## Hoe lettertypen te detecteren met Aspose.Words

Het kernidee is om in te haken op het waarschuwingssysteem van Aspose.Words. Wanneer de bibliotheek een aangevraagd lettertype niet kan vinden, geeft het een `WarningType.FontSubstitution`‑waarschuwing af. Door een aangepaste `IWarningCallback`‑implementatie te leveren, kun je **lettertypen detecteren** die tijdens het laadproces zijn vervangen.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **Waarom dit werkt:** Aspose.Words roept de `Warning`‑methode aan voor elk niet‑kritisch probleem. Door de `WarningInfo`‑objecten op te slaan krijg je volledige toegang tot het type, bericht en context, wat precies is wat je nodig hebt om **lettertypen te detecteren** die zijn vervangen.

---

## Hoe waarschuwingen vast te leggen bij het laden van een document

Nu we een collector hebben, moeten we de `LoadOptions` vertellen deze te gebruiken. Dit is het **hoe je waarschuwingen vastlegt** deel van de puzzel.

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **Randgeval:** Als je een document laadt vanuit een stream (`new Document(stream, loadOptions)`), werkt dezelfde callback—geef gewoon de stream door in plaats van een bestandspad.

Op dit punt is het document volledig geladen, maar eventuele lettertype‑vervangingswaarschuwingen zijn veilig opgeslagen in `warningCollector.Warnings`.

---

## Hoe waarschuwingen te enumereren en lettertype‑vervangingen te rapporteren

Tot slot filteren we de verzamelde waarschuwingen en **enumereren we waarschuwingen** die specifiek over lettertype‑vervanging gaan. Deze stap zet ruwe data om in een leesbaar rapport.

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**Verwachte output** (voorbeeld):

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

Als het document geen ontbrekende lettertypen bevat, produceert de lus simpelweg geen output—niets om je zorgen over te maken.

---

## Volledig werkend voorbeeld (Alle stappen in één bestand)

Hieronder staat het volledige programma dat je kunt kopiëren‑plakken in een console‑project. Het verbindt **hoe je lettertypen detecteert**, **hoe je waarschuwingen vastlegt**, **hoe je een callback configureert**, en **hoe je waarschuwingen enumerateert** in één samenhangende stroom.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**Het uitvoeren van dit programma** zal elk lettertype afdrukken dat Aspose.Words moest vervangen. Je kunt de output omleiden naar een logbestand, een waarschuwing genereren, of zelfs het laden afbreken als een cruciaal lettertype ontbreekt.

---

## Veelgestelde vragen & valkuilen

### Wat als ik moet stoppen met laden wanneer een vereist lettertype ontbreekt?
Je kunt de `WarningInfo`‑objecten in de callback inspecteren en een uitzondering gooien wanneer een bepaalde lettertype‑naam verschijnt. De uitzondering zal het laden afbreken, waardoor je volledige controle hebt.

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### Werkt dit met PDF’s of andere formaten?
Ja. Aspose.Words gebruikt dezelfde waarschuwingsinfrastructuur voor PDF’s, RTF en HTML. Vervang gewoon de bestandsextensie en de rest van de code blijft identiek.

### Hoe kan ik waarschuwingen loggen naar een bestand in plaats van de console?
Vervang `Console.WriteLine` door elk logframework dat je prefereert (`Serilog`, `NLog`, etc.). De `WarningInfo`‑klasse biedt `Message`, `Source` en `Exception` voor gedetailleerde logs.

### Heeft dit invloed op de prestaties?
De overhead is verwaarloosbaar—Aspose.Words genereert de waarschuwingen al intern. Het toevoegen van een callback slaat ze simpelweg op in een lijst, wat O(n) is in het aantal waarschuwingen. Voor typische documenten is de impact ver onder de 1 % van de totale laadtijd.

## Visuele samenvatting

![Hoe lettertypen te detecteren in Aspose.Words – waarschuwingsstroom diagram](https://example.com/images/font-detection-diagram.png "hoe lettertypen te detecteren")

*Alt‑tekst:* **hoe lettertypen te detecteren** – diagram dat de waarschuwings‑callback, collectie en enumeratie‑stappen toont.

## Samenvatting

We hebben **hoe je lettertypen kunt detecteren** in Aspose.Words behandeld door **waarschuwingen vast te leggen**, **een callback te configureren**, en **waarschuwingen te enumereren**. Het volledige code‑voorbeeld toont een productie‑klaar patroon dat je in elke .NET‑applicatie kunt gebruiken.  

Vervolgens kun je misschien verkennen:

- **Hoe je waarschuwingen vastlegt** voor andere problemen (bijv. problemen met afbeeldingconversie)
- **Hoe je een callback configureert** voor aangepaste logframeworks
- **Hoe je waarschuwingen enumerateert** over meerdere documenten in een batch‑taak
- Het gebruik van **Aspose.Words.Fonts.FontSettings** om fallback‑lettertype‑mappen te bieden, wat het aantal vervangingen in eerste instantie kan verminderen.

Probeer het, pas de collector aan om bij je logstijl te passen, en je zult nooit meer verrast worden door een onverwachte lettertype‑vervanging. Als je tegen vreemde dingen aanloopt, laat dan een reactie achter—happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}