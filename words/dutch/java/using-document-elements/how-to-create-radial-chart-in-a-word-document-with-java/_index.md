---
category: general
date: 2026-09-18
description: Leer hoe je een radiaal diagram maakt in een Word‑document met Java,
  diagramgegevenslabels toevoegt en seriedata invoegt met een volledig codevoorbeeld.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: nl
lastmod: 2026-09-18
og_description: Maak een radiale grafiek in een Word‑document met Java, voeg gegevenslabels
  aan de grafiek toe en voeg seriedata in één tutorial in.
og_image_alt: Radial chart displayed inside a generated Word document
og_title: Maak een radiale grafiek in Word met Java – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: Hoe maak je een radiale grafiek in een Word‑document met Java
url: /nl/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe maak je een radiaal diagram in een Word‑document met Java

Als u een radiaal diagram in een Word‑document moet maken, laat deze gids u de exacte stappen zien. U leert ook hoe u diagramdatatags toevoegt en seriedata invoegt zodat het diagram klaar is voor presentatie.

Het programmatisch genereren van een diagram verwijdert handmatig opmaakwerk en garandeert consistentie tussen rapporten. Deze tutorial gaat ervan uit dat u basiskennis van Java heeft en een recente versie van de Aspose.Words for Java‑bibliotheek geïnstalleerd heeft.

## Wat u nodig heeft

* Java 17 of nieuwer  
* Aspose.Words for Java (versie 23.12 of later)  
* Een IDE of build‑tool die Maven/Gradle‑afhankelijkheden kan oplossen  

Het hebben van deze vereisten geïnstalleerd stelt u in staat het voorbeeld uit te voeren zonder extra configuratie.

## Hoe maak je een radiaal diagram in een Word‑document

De eerste stap is het maken van een leeg Word‑bestand dat het diagram zal bevatten. Een leeg document biedt een schoon canvas en voorkomt ongewenste stijlen.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` vertegenwoordigt het volledige .docx‑bestand, terwijl `DocumentBuilder` methoden levert voor het invoegen van elementen zoals alinea’s, tabellen en diagrammen.

## Hoe diagram in te voegen

Vervolgens voegt u het diagram zelf in. De `insertChart`‑methode maakt een diagramobject aan en plaatst het op de huidige cursorpositie van de builder.

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

Een polair diagram rendert gegevenspunten rond een centrale as, wat ideaal is voor het weergeven van cyclische informatie. De afmetingen worden uitgedrukt in points (1 pt ≈ 1/72 inch).

## Seriedata toevoegen aan het diagram

Een diagram zonder seriedata is leeg. U kunt handmatig een serie toevoegen of deze binden aan een gegevensbron. Het voorbeeld hieronder voegt één serie toe met drie gegevenspunten.

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` ontvangt een serienaam, een lijst met categorielabels en een lijst met bijbehorende numerieke waarden. U kunt dit blok herhalen om extra series toe te voegen (`addSeriesData`).

## Diagramdatatags toevoegen aan de eerste serie

Datatags maken het diagram leesbaar zonder over punten te zweven. De volgende regel schakelt waardelabels in voor de eerste serie.

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

Door `showValue` op `true` te zetten, wordt de waarde van elk punt direct op het diagram weergegeven. U kunt ook categorienamen, percentages of leidende lijnen inschakelen via hetzelfde `DataLabelFormat`‑object.

## Het Word‑bestand opslaan

Nadat het diagram is geconfigureerd, schrijft u het document naar schijf. Kies een locatie die uw applicatie kan benaderen.

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

Het bestand `RadialChart.docx` bevat nu een volledig functioneel radiaal diagram met datatags.

## Volledig werkend voorbeeld

Hieronder staat een zelfstandige toepassing die u kunt kopiëren, compileren en uitvoeren. Het demonstreert de volledige workflow van het maken van een leeg Word‑document tot het opslaan van een radiaal diagram met datatags.

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**Verwacht resultaat**

Wanneer u `output/RadialChart.docx` opent in Microsoft Word, ziet u een radiaal diagram met de titel *Quarterly Sales*. Elk punt toont zijn numerieke waarde (bijv. “15000”) naast de marker.

## Veelvoorkomende variaties en randgevallen

| Situatie | Aanbevolen wijziging |
|-----------|--------------------|
| U heeft een ander diagramtype nodig | Vervang `ChartType.POLAR` door een andere `ChartType` enum‑waarde (bijv. `ChartType.COLUMN`). |
| Het diagram moet een extern Excel‑bereik gebruiken | Gebruik `chart.setDataRange("Sheet1!A1:B5")` na het aanmaken van het diagram en het laden van de werkmap. |
| U wilt de legenda verbergen | `chart.getLegend().setVisible(false);` |
| Het document moet als PDF worden opgeslagen | Roep `doc.save("RadialChart.pdf");` aan – Aspose.Words converteert het diagram automatisch. |

## Pro‑tips

* **Herbruik de builder** – U kunt meerdere diagrammen in hetzelfde document invoegen door `builder.insertChart` herhaaldelijk aan te roepen.  
* **Performance** – Bij het genereren van veel diagrammen, maak één `DocumentBuilder`‑instantie aan en hergebruik deze om de overhead van objectallocatie te verminderen.  
* **Styling** – Het uiterlijk van het diagram (kleuren, lijndikte) wordt geregeld via de `Chart`‑objectmethoden `getSeries().get(i).getFormat()`. Experimenteer met deze instellingen om te voldoen aan de huisstijl van uw organisatie.

## Conclusie

U weet nu hoe u een radiaal diagram in een Word‑document met Java maakt, seriedata toevoegt en diagramdatatags toevoegt voordat u het bestand opslaat. Het volledige voorbeeld kan worden uitgebreid om extra series, aangepaste stijlen of alternatieve uitvoerformaten te ondersteunen.

Verken gerelateerde onderwerpen zoals **hoe diagram in te voegen** vanuit externe gegevensbronnen, **Word‑documenten maken** met vooraf gedefinieerde sjablonen, en **seriedata toevoegen** dynamisch vanuit databases. Experimenteer met verschillende diagramtypes om te ontdekken welk visueel uw gegevens het beste communiceert.

## Wat moet u hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om u te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in uw eigen projecten te verkennen.

- [Hoe maak je een kolomdiagram met Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Word‑document maken met Java – Rechthoekvorm toevoegen met schaduweffect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Standaardopties instellen voor datatags in een diagram](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}