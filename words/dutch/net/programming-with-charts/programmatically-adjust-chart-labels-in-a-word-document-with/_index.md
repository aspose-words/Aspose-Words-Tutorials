---
category: general
date: 2026-10-13
description: Leer hoe je programmatisch grafieklabels in een Word‑document kunt aanpassen
  met C#. Deze gids behandelt Aspose.Words‑grafiekmanipulatie en labeluitlijning.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: nl
lastmod: 2026-10-13
og_description: Programmeermatig diagramlabels in een Word‑document aanpassen met
  C#. Volg deze volledige tutorial om de plaatsing, uitlijning en meer van labels
  te wijzigen.
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: Programmatig grafiektitels aanpassen in Word – C# stap‑voor‑stap gids
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: Programmatig grafieklabels aanpassen in een Word‑document met C#
url: /nl/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Grafiektitels programmatically aanpassen in een Word-document met C#

Als je **grafiektitels programmatically wilt aanpassen** in een Word-document, laat deze gids je precies zien hoe je dat doet met C#. Of je nu rapporten genereert, dashboards automatiseert of sjablonen aanpast, je ziet een volledig, uitvoerbaar voorbeeld dat de plaatsing en uitlijning van een grafiektitel in een .docx‑bestand wijzigt.

Je leert ook hoe je **Aspose.Words chart manipulation**‑technieken gebruikt, meerdere series verwerkt en veelvoorkomende valkuilen vermijdt bij het werken met **C# chart data label**‑objecten.

## Vereisten

* .NET 6.0 (of later) geïnstalleerd  
* Visual Studio 2022 (of een andere C#‑IDE)  
* Het **Aspose.Words for .NET** NuGet‑pakket (`Install-Package Aspose.Words`)  
* Een Word‑document (`input.docx`) dat minstens één grafiek bevat  

Deze items zijn vereist voor het **Word document chart example** dat we gaan aanpassen.

## Stap 1: Het project opzetten en namespaces importeren

Maak een nieuw console‑project aan en voeg de benodigde `using`‑directieven toe. Dit bereidt de omgeving voor op **grafiektitels programmatically aanpassen**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*Waarom deze stap?*  
Het laden van het document geeft je toegang tot de interne **Word document chart example**‑boom, waarin grafieken worden opgeslagen als shape‑nodes.

## Stap 2: Het eerste grafiek‑shape vinden

Grafieken worden opgeslagen als `Shape`‑nodes. De onderstaande code haalt de eerste grafiek uit het document op, die het doelwit is voor onze label‑aanpassingen.

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*Waarom deze stap?*  
De `GetChild`‑methode zoekt recursief (`true`) en retourneert de eerste node van het type `Shape`. Casten naar `Chart` stelt ons in staat om met de grafiek‑specifieke API te werken.

## Stap 3: Toegang krijgen tot het datalabel dat je wilt wijzigen

Elke serie in een grafiek heeft een collectie datalabels. Voor een eenvoudige grafiek is het eerste label vaak voldoende. De code hieronder laat zien hoe je het bereikt.

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*Waarom deze stap?*  
`ChartSeries` vertegenwoordigt een reeks punten. `DataLabelCollection` bevat de labels voor die serie, waardoor je precieze controle hebt over plaatsing en uitlijning.

## Stap 4: Plaatsing en uitlijning van het label wijzigen

Nu **grafiektitels programmatically aanpassen** door de positie, horizontale uitlijning en verticale uitlijning in te stellen. Deze eigenschappen komen overeen met de opties die je in de Word‑UI ziet.

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*Waarom deze instellingen?*  

* `OutsideEnd` plaatst het label net buiten het einde van elke staaf of kolom, waardoor de leesbaarheid verbetert.  
* `HorizontalAlignment.Center` houdt de tekst gecentreerd boven het punt, terwijl `VerticalAlignment.Top` de bovenrand van het label uitlijnt met het datapunt, waardoor overlapping met andere elementen wordt voorkomen.

### Pro tip
Als een grafiek meerdere series heeft, loop dan door `chart.Series` en pas dezelfde instellingen toe op elke `DataLabelCollection`. Dit zorgt voor een consistente uitstraling over de hele grafiek.

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## Stap 5: Het gewijzigde document opslaan

Na het aanpassen van de labels, sla je de wijzigingen op in een nieuw bestand. Hiermee is het **modify chart label position**‑proces voltooid.

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Wanneer je `output.docx` opent, zie je dat elk grafieklabel is verplaatst naar het buitenste einde van zijn datapunt, horizontaal gecentreerd en verticaal uitgelijnd aan de bovenkant.

## Randgevallen en variaties

| Situatie | Waar op te letten | Aanbevolen aanpak |
|-----------|-------------------|----------------------|
| **Meerdere grafieken** in hetzelfde document | `GetChild` retourneert alleen de eerste grafiek. | Gebruik `doc.GetChildNodes(NodeType.Shape, true)` om over alle grafiek‑shapes te itereren. |
| **Series zonder datalabels** | `DataLabelCollection` kan leeg zijn. | Controleer `series.HasDataLabels` voordat je de collectie benadert. |
| **Verschillende grafiektype** (taart, lijn, spreiding) | Niet alle `DataLabelPosition`‑waarden zijn geldig. | Gebruik `DataLabelPosition.Auto` voor grafieken die automatisch de beste plaatsing bepalen. |
| **Lokalisatie** | Uitlijningsconstanten zijn taalonafhankelijk, maar de gerenderde tekst kan recht‑naar‑links‑ondersteuning nodig hebben. | Stel `dataLabel.TextDirection` in als je RTL‑talen nodig hebt. |

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren, plakken en uitvoeren. Vervang `YOUR_DIRECTORY` door een daadwerkelijk mappad.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Verwacht resultaat:** Het openen van `output.docx` toont elk grafieklabel buiten het datapunt geplaatst, horizontaal gecentreerd en verticaal uitgelijnd aan de bovenkant — precies het effect van **grafiektitels programmatically aanpassen** dat je hebt gescript.

## Conclusie

Je weet nu hoe je **grafiektitels programmatically aanpassen** in een Word‑document met C#. De tutorial behandelde:

* Het laden van een document met **Aspose.Words chart manipulation**  
* Toegang tot een **C# chart data label**  
* Het wijzigen van de **modify chart label position** en uitlijning  
* Het opslaan van het bestand en het afhandelen van veelvoorkomende randgevallen  

Vanaf hier kun je meer geavanceerde scenario's verkennen, zoals het aanpassen van label‑lettertypen, het toevoegen van voorwaardelijke opmaak, of het bijwerken van meerdere grafieken in een batch‑proces. Experimenteer met de verschillende `DataLabelPosition`‑opties om de stijl te vinden die het beste bij je rapporten past.

---

*Klaar om je geautomatiseerde rapportage‑pipeline te verbeteren? Probeer aangepaste getalformaten toe te voegen aan de labels of exporteer de grafiek als afbeelding voor gebruik in PDF‑bestanden.*

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Uniforme datalabels instellen in een kolomgrafiek met Aspose.Words voor .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Standaardopties instellen voor datalabels in een grafiek](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Grafiekserie‑gegevens bijwerken in een Word‑document met Aspose.Words voor .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}