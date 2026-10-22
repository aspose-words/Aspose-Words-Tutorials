---
category: general
date: 2026-08-14
description: Maak een taartdiagram in Word met Java met behulp van Aspose.Words. Leer
  hoe je seriedata aan het diagram toevoegt en een taartsegment roteert in slechts
  een paar regels.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: nl
lastmod: 2026-08-14
og_description: Maak een taartdiagram in Word met Java met behulp van Aspose.Words.
  Deze tutorial laat zien hoe je seriedata aan het diagram toevoegt en een taartpunt
  snel draait.
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: Maak een taartdiagram in Word met Java – volledige codegids
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Maak een cirkeldiagram in Word met Java – stap‑voor‑stap gids
url: /nl/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een taartdiagram in Word met Java – stapsgewijze handleiding

Als je **een taartdiagram in Word** programmatisch wilt maken, laat deze gids je precies zien hoe je dat doet met Java en Aspose.Words. Je leert de volledige workflow, van het invoegen van het diagram tot het toevoegen van gegevenspunten en het roteren van de eerste part.

Een diagram direct in een `.docx`‑bestand genereren verwijdert de handmatige kopie‑plakstap en stelt je in staat rapporten, facturen of dashboards te automatiseren. Onderweg behandelen we ook **hoe je seriesgegevens aan een diagram toevoegt** en hoe je **een taartdiagram‑part rotert** voor betere visuele nadruk.

## Maak een taartdiagram in Word – overzicht

Aspose.Words for Java biedt een vloeiende `DocumentBuilder`‑API die een diagramobject in een Word‑document kan invoegen. Het type diagram dat je kiest bepaalt de standaardlay-out, en je kunt de series, kleuren, hoeken aanpassen, en zelfs overschakelen naar een donut‑vorm met één methode‑aanroep.

### Waarom Aspose.Words gebruiken?

* **Geen Microsoft Office vereist** – de bibliotheek werkt op elke server of CI‑omgeving.  
* **Volledige .docx‑getrouwheid** – het gegenereerde diagram ziet er identiek uit als een handmatig in Word gemaakt diagram.  
* **Enkele‑bestand afhankelijkheid** – voeg gewoon de JAR toe en je bent klaar om te gaan.

## Hoe seriesgegevens aan een diagram toevoegen

Een diagram zonder gegevens is slechts een tijdelijke aanduiding. Het `Chart`‑object biedt een `Series`‑collectie; elke serie bevat een lijst met numerieke waarden die overeenkomen met partjes (voor een taart) of punten (voor een lijn). Gegevens toevoegen is eenvoudig:

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**Wat de code doet:**  
* `chart.getSeries()` retourneert een `List<ChartSeries>`.  
* `get(0)` selecteert de eerste serie omdat een taartdiagram per definitie slechts één serie bevat.  
* `add(double)` voegt een gegevenspunt toe. De waarden worden automatisch omgezet naar percentages die optellen tot 100 % wanneer het diagram wordt gerenderd.

> **Pro tip:** Als je gegevensbron meer dan drie categorieën bevat, blijf dan waarden op dezelfde manier toevoegen. Aspose.Words maakt automatisch extra partjes aan.

## Een taartdiagram‑part roteren

Soms wil je dat een specifiek partje begint onder een bepaalde hoek zodat het belangrijkste segment naar de kijker wijst. De `setFirstSliceAngle(double)`‑methode roteert het hele diagram, waardoor de start van het eerste partje effectief wordt verplaatst:

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

De hoek wordt gemeten in graden met de klok mee vanaf de verticale as. Instellen op `0` (de standaard) plaatst het eerste partje bovenaan. Pas de waarde aan om een partje te accentueren of om te voldoen aan een ontwerprichtlijn.

> **Veelgestelde vraag:** *Heeft roteren invloed op de volgorde van de gegevens?*  
> Nee. De volgorde van de gegevens blijft hetzelfde; alleen de visuele startpositie verandert.

## Volledig Java‑voorbeeld

Hieronder staat een compleet, kant‑klaar programma dat een Word‑document met een taartdiagram maakt, seriesgegevens toevoegt, het partje roteert en het bestand opslaat. Alle benodigde imports staan vermeld, zodat je de code in elke IDE kunt kopiëren.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Verwachte output

* Een bestand met de naam **PieChart.docx** verschijnt in de `output`‑map.  
* Het openen van het bestand in Microsoft Word toont een kleurrijk taartdiagram met drie partjes (40 %, 30 %, 30 %).  
* Het diagram is 45° met de klok mee geroteerd, zodat het eerste partje iets rechts van de verticale as begint.

## Veelvoorkomende valkuilen en best practices

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| **Diagram verschijnt leeg** | Het document werd opgeslagen voordat het diagram volledig was gerenderd. | Roep `doc.save()` **aan** na alle diagram‑aanpassingen. |
| **Partijwaarden tellen niet op tot 100 %** | Het toevoegen van ruwe getallen die geen percentages vertegenwoordigen kan leiden tot onverwachte schaalvergroting. | Geef waarden die logisch een deel van een geheel vertegenwoordigen, of laat Aspose.Words de percentages automatisch berekenen. |
| **Rotatie heeft geen effect** | Het gebruik van `ChartType.DOUGHNUT` zonder `holeSize` in te stellen kan het rotatie‑effect verbergen. | Behoud het diagram als `PIE` of pas `holeSize` aan na het instellen van de hoek. |
| **Bestandspad‑fouten** | Relatieve paden kunnen anders worden opgelost op Windows versus Linux. | Gebruik `Paths.get("output", "PieChart.docx").toString()` of een absoluut pad voor productcode. |

### Tips voor productiegebruik

* **Herbruik de `DocumentBuilder`** – je kunt meerdere diagrammen in hetzelfde document invoegen door herhaaldelijk `insertChart` aan te roepen.  
* **Styling** – gebruik `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);` om percentages direct op het diagram weer te geven.  
* **Performance** – genereer het diagram één keer en kloon het (`chart.deepClone()`) als je identieke diagrammen op meerdere plaatsen nodig hebt.

## Een taartdiagram‑part roteren – geavanceerde scenario's

* **Dynamische hoek** – bereken de hoek op basis van gegevens (bijv. laat het grootste partje bovenaan beginnen).  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **Meerdere series** – hoewel een taartdiagram normaal één serie heeft, laat Aspose.Words je er meer toevoegen voor gestapelde taarten. De rotatie geldt nog steeds alleen voor de eerste serie.

## Conclusie

Je weet nu hoe je **een taartdiagram in Word** maakt met Java, hoe je **seriesgegevens aan een diagram toevoegt**, en hoe je **een taartdiagram‑part roteert** voor visuele nadruk. Het volledige voorbeeld toont de hele workflow — van documentinitialisatie tot het opslaan van het uiteindelijke `.docx`‑bestand — zodat je diagramgeneratie kunt integreren in elke geautomatiseerde rapportage‑pipeline.

### Wat is het volgende?

* Verken andere diagramtypen (`ChartType.BAR`, `ChartType.LINE`) om je automatiseringstoolkit uit te breiden.  
* Combineer diagramgeneratie met **mail merge** om gepersonaliseerde rapporten voor elke ontvanger te maken.  
* Duik in de **Styling API** (`ChartFormat`, `DataLabel`, `ChartTitle`) om aan je bedrijfsbranding te voldoen.

Voel je vrij om te experimenteren met verschillende datasets, hoeken en diagramstijlen. Veel plezier met coderen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe een kolomdiagram te maken met Aspose.Words voor Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hoe formulier‑velden te maken en inhoud toe te voegen met DocumentBuilder in Aspose.Words voor Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Hoe Word naar PDF te converteren met Aspose.Words voor Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}