---
category: general
date: 2026-06-02
description: Toon de grafieklegenda in een Word‑document met C#. Leer hoe je een legenda
  toevoegt, een vooraf ingestelde grafiekstijl toepast en de weergave van Word‑grafieken
  in enkele minuten aanpast.
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: nl
og_description: Toon de grafieklegenda direct in een Word‑document. Deze gids leidt
  je stap voor stap door het toevoegen van een legenda, het toepassen van een vooraf
  ingestelde grafiekstijl en het omgaan met randgevallen.
og_title: Grafieklegenda weergeven in Word – Volledige C#‑handleiding
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: Grafieklegenda weergeven in Word met C# – Complete stapsgewijze handleiding
url: /nl/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Toon grafieklegenda in Word met C# – Complete stapsgewijze handleiding

Heb je je ooit afgevraagd **hoe je een legenda** aan een grafiek toevoegt die zich in een Word‑document bevindt? Je bent niet de enige. In veel rapporten maakt een ontbrekende legenda de gegevens cryptisch, en het oplossen ervan zou geen hoofdpijn moeten zijn.  

In deze tutorial laten we **grafieklegenda weergeven** in een Word‑bestand met behulp van Aspose.Words voor .NET, passen we een vooraf ingestelde grafiekstijl toe, en zorgen we ervoor dat de legenda precies verschijnt waar je het nodig hebt. Aan het einde heb je een kant‑klaar voorbeeld dat je in elk C#‑project kunt gebruiken.

## Wat deze gids behandelt

We lopen de volledige workflow door:

1. Laad een bestaand *.docx* dat al een grafiek bevat.  
2. Haal de eerste grafiek op (of een willekeurige grafiek die je target).  
3. **Pas een vooraf ingestelde grafiekstijl toe** om het uiterlijk een professionele uitstraling te geven.  
4. **Toon grafieklegenda**, positioneer deze rechts, en behandel speciale gevallen zoals Waterfall‑grafieken.  
5. Sla het gewijzigde document op.

Geen externe tools, geen handmatig geknoei met de UI—alleen pure code. De enige voorwaarde is een referentie naar het Aspose.Words NuGet‑pakket (versie 23.10 of later) en een basisbegrip van C#.

---

## Vereisten

- .NET 6.0 of later (het voorbeeld werkt ook met .NET Framework 4.7.2).  
- Aspose.Words for .NET‑bibliotheek geïnstalleerd (`Install-Package Aspose.Words`).  
- Een Word‑bestand (`input.docx`) dat al minstens één grafiek bevat.  
- Visual Studio, Rider, of een IDE naar keuze.

---

## Stap 1: Het project opzetten en het document laden

Maak eerst een console‑app (of integreer de code in een bestaand project). Voeg de `using`‑directieven toe en laad het `.docx`‑bestand.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **Waarom dit belangrijk is:** Het laden van het document is de basis. Zonder een `Document`‑instantie kun je de grafiekobjecten die Aspose.Words exposeert niet bereiken.

---

## Stap 2: Haal de doelgrafiek op

Grafieken worden opgeslagen als knooppunten in de documentboom. De `GetChild`‑methode voert een diepe zoekopdracht uit, waardoor we de eerste grafiek kunnen ophalen, ongeacht waar deze zich bevindt (koptekst, hoofdtekst, voettekst, enz.).

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **Tip:** Als je meerdere grafieken hebt, wijzig dan de index `0` naar `1`, `2`, … of itereren via `doc.GetChildNodes(NodeType.Chart, true)`.

---

## Stap 3: Pas een vooraf ingestelde visuele stijl toe

Een goed uitziende grafiek begint vaak met een stijl. Aspose.Words wordt geleverd met tientallen ingebouwde stijlen; `ChartStyle.Style12` is een nette, moderne optie.

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **Hoe het werkt:** De `Style`‑eigenschap verwijst naar de ingebouwde Word‑grafiekstijlen die je in de UI ziet. Het kiezen van een preset bespaart je het handmatig instellen van kleuren, lettertypen en markeringen.

---

## Stap 4: Schakel de legenda in en positioneer deze

Nu de ster van de show—**grafieklegenda weergeven**. We schakelen de legenda in en verankeren deze aan de rechterkant van de grafiek.

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **Waarom rechts?** Het plaatsen van de legenda aan de rechterkant houdt het gegevensgebied breed, wat vooral handig is voor staaf‑ of kolomgrafieken.

---

## Stap 5: Waterfall‑grafieken afhandelen (speciaal geval)

Waterfall‑grafieken gedragen zich iets anders; de legenda kan standaard verborgen zijn. De volgende guard‑clausule zorgt ervoor dat de legenda zichtbaar is wanneer het grafiektype Waterfall is.

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **Opmerking over randgeval:** Sommige oudere Word‑versies negeren `HasLegend` voor Waterfall‑grafieken, dus het expliciet instellen van `Legend.Show` garandeert zichtbaarheid.

---

## Stap 6: Sla het gewijzigde document op

Schrijf tenslotte de wijzigingen terug naar de schijf. Je kunt het originele bestand overschrijven of een nieuw bestand aanmaken.

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

Het uitvoeren van het programma genereert `output.docx` met een zichtbare legenda aan de rechterkant, gestyled met `Style12`. Open het bestand in Word om het resultaat te verifiëren.

---

## Volledig werkend voorbeeld (Alle stappen gecombineerd)

Hieronder staat de volledige, kant‑klaar code. Kopieer‑en‑plak deze in `Program.cs` (of een ander C#‑bestand) en pas de bestands‑paden aan.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**Verwacht resultaat:** Het openen van `output.docx` toont de oorspronkelijke grafiek met een rechts uitgelijnde legenda, gestyled met de moderne `Style12`. Alle gegevensreeksen zijn duidelijk gelabeld, waardoor de grafiek direct begrijpelijk is.

---

## Veelgestelde vragen (FAQ)

### Hoe voeg je een legenda toe aan een specifieke grafiek (niet de eerste)?

Vervang de `0`‑index in `GetChild(NodeType.Chart, 0, true)` door de nul‑gebaseerde positie van je doelgrafiek, of loop door alle grafiek‑knooppunten:

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### Kan ik de legenda onderaan plaatsen in plaats van rechts?

Zeker. Verander gewoon de `LegendPosition`‑enum:

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### Wat als de grafiek al een legenda heeft maar ik wil deze verbergen?

Stel `HasLegend` in op `false`:

```csharp
chart.HasLegend = false;
```

### Werkt dit met Word 2010, 2016 en later?

Ja. Aspose.Words abstraheert de onderliggende Word‑versie, zodat dezelfde code werkt met alle moderne .docx‑bestanden.

---

## Pro‑tips & veelvoorkomende valkuilen

- **Pro tip:** Na het toepassen van een stijl kun je nog steeds individuele elementen (kleuren, gegevenslabels) aanpassen via de `Chart.Series`‑collectie. De stijl biedt een solide basis.
- **Let op:** Als de grafiek zich in een tabelcel bevindt, kan de legenda krap staan. Overweeg de grafiekgrootte (`chart.Width`, `chart.Height`) te vergroten voordat je de legenda positioneert.
- **Prestatienota:** Het laden van grote documenten (honderden MB) kan veel geheugen verbruiken. Gebruik `LoadOptions` met `LoadFormat.Docx` om de overhead te verminderen als je alleen grafiekmanipulatie nodig hebt.

---

## Volgende stappen

Nu je weet **hoe je een legenda toevoegt** en **een vooraf ingestelde grafiekstijl toepast** in Word, kun je het volgende verkennen:

- **Aangepaste grafiekkleuren** (`chart.Series[i].Format.Fill.ForeColor`).  
- **Gegevenslabel‑opmaak** (`chart.Series[i].HasDataLabel = true`).  
- **Exporteren van de grafiek als afbeelding** (`chart.ToImage()`), handig voor inbedding elders.  

Elk van deze onderwerpen bouwt voort op hetzelfde objectmodel, dus de leercurve zal zacht zijn.

---

## Conclusie

We hebben zojuist een nette, end‑to‑end‑oplossing getoond voor **grafieklegenda weergeven** in een Word‑document met C#. Door het document te laden, de grafiek op te halen, een vooraf ingestelde stijl toe te passen, de legenda in te schakelen en Waterfall‑eigenaardigheden af te handelen, krijg je een gepolijste grafiek die klaar is voor elk bedrijfsrapport.

Voel je vrij om te experimenteren met andere `ChartStyle`‑waarden of legendarposities—je datavisualisaties verdienen de beste presentatie. Als je ergens tegenaan loopt, laat dan een reactie achter; happy coding!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Using Word Chart API](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}