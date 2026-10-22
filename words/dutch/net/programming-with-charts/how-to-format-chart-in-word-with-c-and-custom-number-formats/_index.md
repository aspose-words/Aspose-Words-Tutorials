---
category: general
date: 2026-10-13
description: Hoe een grafiek in Word te formatteren met C# door een aangepast getalformaat,
  zoals valuta, toe te passen op de assen van de grafiek. Stap‑voor‑stap codevoorbeeld
  inbegrepen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: nl
lastmod: 2026-10-13
og_description: Hoe je een grafiek in Word formatteert met C# laat je een aangepast
  getalformaat toepassen op de assen van de grafiek, zodat waarden verschijnen als
  valuta, percentages of elk gewenst patroon. Volg de stapsgewijze handleiding.
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: Hoe een grafiek in Word te formatteren met C# – aangepaste getalformaten
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: Hoe een grafiek in Word opmaken met C# en aangepaste getalformaten
url: /nl/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe grafiek opmaken in Word met C# en aangepaste getalnotaties

Het opmaken van een grafiek in Word met C# is een veelvoorkomende vereiste wanneer u gegevens professioneel wilt presenteren. Deze gids laat zien hoe u een aangepaste getalnotatie toepast op de as van een grafiek met behulp van **Aspose.Words for .NET**, zodat de waarden precies verschijnen zoals u verwacht.

U leert hoe u een DOCX‑bestand laadt, de eerste grafiek vindt, het huidige formaat leest en vervolgens een nieuw patroon instelt, bijvoorbeeld valuta met twee decimalen. De tutorial behandelt ook hoe u het as‑formaat van een grafiek voor extra reeksen wijzigt en hoe u het formaat indien nodig terugzet.

## Vereisten

* .NET 6.0 of later geïnstalleerd  
* Een Visual Studio 2022 (of een andere IDE die .NET ondersteunt) project  
* Het **Aspose.Words for .NET** NuGet‑pakket (`Aspose.Words`)  
* Een Word‑document (`input.docx`) dat minstens één grafiek bevat

U kunt het pakket toevoegen met de volgende opdracht:

```bash
dotnet add package Aspose.Words
```

## Hoe grafiek opmaken in Word met Aspose.Words

Het onderstaande volledige programma demonstreert elke stap die nodig is om **grafiek**‑aswaarden op te maken. Sla het bestand op als `Program.cs` en voer het uit vanaf de opdrachtregel of vanuit uw IDE.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### Uitleg van elke stap

| Stap | Waarom het belangrijk is | Belangrijke code |
|------|--------------------------|------------------|
| **Document laden** | U heeft een `Document`‑object nodig om met het Word‑bestand te werken. | `new Document("input.docx")` |
| **Grafiek ophalen** | `Chart`‑objecten worden opgeslagen als `Shape`‑knooppunten; casten stelt u in staat om grafiek‑specifieke API's te gebruiken. | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **X‑waarden benaderen** | Asopmaak wordt toegepast op de waardencollectie van een gegevensreeks. | `chart.ChartData.Series[0].XValues` |
| **Huidig formaat lezen** | Kennis van de bestaande `FormatCode` helpt u te bepalen of u deze moet vervangen of uitbreiden. | `xValues.FormatCode` |
| **Aangepast formaat instellen** | De eigenschap `FormatCode` accepteert elk Excel‑compatibel patroon, waardoor valuta, percentages, datums, enz. mogelijk zijn. | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **Document opslaan** | Het behouden van wijzigingen schrijft het nieuwe as‑formaat terug naar het DOCX‑bestand. | `doc.Save("output_formatted.docx")` |

Het uitvoeren van het programma levert `output_formatted.docx` op. Open het in Word en u ziet de X‑as‑waarden van de grafiek weergegeven als **$1,234.00**, **$2,345.00**, … in plaats van platte getallen.

## Aangepaste getalnotatie toepassen op grafiekas

Als u een **aangepaste getalnotatie** op de Y‑as of op extra reeksen moet toepassen, is het proces identiek—richt u zich alleen op een andere collectie:

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **Pro tip:** Gebruik dubbele aanhalingstekens binnen de opmaak‑string om letterlijke tekens in te sluiten (bijv. `"$"` voor valuta). Escape de aanhalingstekens zoals hierboven getoond.

## Aangepaste getalnotatie – omgaan met de locale van Word

Word respecteert de locale van het document bij het interpreteren van getalnotaties. Als het document een niet‑US‑locale gebruikt, moet u mogelijk de opmaak‑string aanpassen:

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

Het testen van de notatie op een document met Duitse taalinstellingen bevestigt dat waarden verschijnen als **€ 1.234,00**.

## Hoe grafiekeigenschappen programmatically instellen

Naast as‑opmaak wilt u vaak **grafiek**‑titels, legenda’s of gegevenslabels instellen. Hier is een kort fragment dat laat zien hoe u een grafiektitel instelt nadat u de as hebt opgemaakt:

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

Door dit te combineren met de aangepaste getalnotatie krijgt u een volledig gepolijste grafiek die klaar is voor rapportage.

## Grafiekasformaat dynamisch wijzigen op basis van gebruikersinvoer

In real‑world‑toepassingen kunt u gebruikers een formaat laten kiezen tijdens runtime. De volgende methode kapselt de opmaaklogica in:

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

U kunt `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` aanroepen voor valuta of `SetAxisFormat(chart, 0, "0%")` voor percentages. Deze aanpak houdt uw hoofdcode overzichtelijk en ondersteunt toekomstige uitbreidingen.

## Randgevallen en veelvoorkomende valkuilen

| Situatie | Waar op te letten | Aanbevolen oplossing |
|----------|-------------------|----------------------|
| Document bevat **geen grafiek** | `GetChild` retourneert `null`, wat een cast‑exception veroorzaakt. | Controleer op `null` vóór het casten (zie voorbeeld). |
| Meerdere grafieken in hetzelfde document | De code pakt altijd de eerste grafiek (`index 0`). | Loop door `doc.GetChildNodes(NodeType.Shape, true)` en filter op `ShapeType.Chart`. |
| Reeks **zonder X‑waarden** (bijv. cirkeldiagrammen) | Toegang tot `XValues` kan een `ArgumentOutOfRangeException` veroorzaken. | Controleer of `Series[i].XValues` niet leeg is vóór het opmaken. |
| Locale‑mismatch | Valutasymbool kan onjuist verschijnen. | Stel `xValues.FormatCode` expliciet in met de juiste locale‑symbolen. |

## Verwachte output

Na het uitvoeren van het voorbeeldprogramma, open **output_formatted.docx**. De X‑as van de grafiek moet getallen weergeven in het gekozen aangepaste formaat. Voor het valuta‑voorbeeld zien de as‑labels er als volgt uit:

```
$1,000.00
$2,000.00
$3,000.00
```

Als u het percentage‑formaat op Y‑waarden hebt toegepast, verschijnen de Y‑as‑labels als:

```
10%
20%
30%
```

## Conclusie

Deze tutorial heeft u laten zien **hoe grafiek** in Word met C# op te maken door **een aangepaste getalnotatie** op aswaarden toe te passen. U beschikt nu over een herbruikbaar patroon voor het instellen van valuta, percentages of elke andere numerieke notatie, evenals richtlijnen voor het omgaan met locales, meerdere reeksen en dynamische gebruikersinvoer.

Vervolgens kunt u **hoe grafiek**‑titels, gegevenslabels of zelfs het exporteren van de grafiek als afbeelding met `ChartRenderer` verkennen. Deze onderwerpen bouwen direct voort op de hier behandelde concepten en helpen u volledig geautomatiseerde rapportage‑oplossingen te creëren.

---

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om u te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in uw eigen projecten te verkennen.

- [Getalnotatie voor as in een grafiek](/words/english/net/programming-with-charts/number-format-for-axis/)
- [Getal opmaken van gegevenslabel in een grafiek](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Secundaire X‑as opmaken en weergave‑eenheden instellen op duizenden in Word‑lijngrafieken met Aspose.Words for .NET](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}