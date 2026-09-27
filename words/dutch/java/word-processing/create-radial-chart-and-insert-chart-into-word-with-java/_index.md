---
category: general
date: 2026-09-27
description: Maak een radiale grafiek in Java en voeg de grafiek in Word in. Leer
  hoe je de grafiekgrootte instelt, gegevensreeksen toevoegt en een leeg Word‑document
  genereert.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: nl
lastmod: 2026-09-27
og_description: Maak een radiale grafiek in Java en voeg deze vervolgens in Word in.
  Deze gids laat zien hoe je de grafiekgrootte instelt, gegevensreeksen toevoegt en
  een leeg Word‑document maakt.
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: Maak een radiale grafiek en voeg de grafiek in Word in met Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: Maak een radiale grafiek en voeg de grafiek in Word in met Java
url: /nl/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een radiale grafiek en voeg de grafiek in Word in met Java

Als je een **radiale grafiek** in een Word‑bestand wilt maken met Java, laat deze tutorial je precies zien hoe. Je ziet hoe je **een grafiek in Word invoegt**, de afmetingen van de grafiek instelt, en een **leeg Word‑document** vanaf nul bouwt.

We doorlopen elke benodigde stap, van het initialiseren van het document tot het toevoegen van een gegevensreeks en het opslaan van de uiteindelijke `.docx`. Aan het einde heb je een volledig functioneel Word‑bestand met een radiale grafiek, en begrijp je **hoe je de grafiekgrootte instelt** en **een gegevensreeks aan de grafiek toevoegt** voor toekomstige aanpassingen.

## Vereisten

* Java 17 of later (de code compileert met elke moderne JDK)
* Aspose.Words for Java 24.9 of nieuwer – de `setShowGraduations`‑methode is alleen beschikbaar vanaf deze versie
* Een IDE of build‑tool (Maven/Gradle) die de Aspose.Words‑JAR kan opnemen
* Basiskennis van Java‑syntaxis en Maven/Gradle‑dependency‑beheer

> **Pro tip:** Als je Maven gebruikt, voeg dan het volgende toe aan je `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Stap 1: Maak een leeg Word‑document

Een leeg document is het canvas waarop de grafiek wordt geplaatst. De `Document`‑klasse vertegenwoordigt het volledige `.docx`‑bestand.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

Het maken van een leeg document zorgt ervoor dat geen vooraf bestaande inhoud de lay‑out van de grafiek verstoort.

## Stap 2: Initialise een DocumentBuilder

`DocumentBuilder` biedt handige methoden om objecten, tekst en andere elementen in het document in te voegen.

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

De builder zal later worden gebruikt om **een grafiek in Word in te voegen**.

## Stap 3: Bouw de radiale grafiek

Aspose.Words ondersteunt veel grafiektype­s; `ChartType.RADIAL` maakt een radiale (polaire) grafiek.

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

Op dit moment bestaat de grafiek, maar heeft geen gegevens, grootte of visuele opties.

## Stap 4: Voeg een gegevensreeks toe aan de grafiek

Een grafiek zonder gegevensreeks is leeg. De `add`‑methode neemt een serienaam en een array met waarden.

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

Je kunt meerdere reeksen toevoegen door `add` herhaaldelijk aan te roepen. Dit voldoet aan de **add data series chart**‑vereiste.

## Stap 5: Schakel graduaties in (optioneel)

Graduaties zijn de radiale rasterlijnen die de leesbaarheid verbeteren. Ze zijn alleen beschikbaar vanaf versie 24.9.

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

Als je een oudere Aspose.Words‑versie gebruikt, zal deze regel een uitzondering veroorzaken—controleer dus eerst je bibliotheekversie.

## Stap 6: Stel de afmetingen van de grafiek in

Het regelen van de grafiekgrootte stelt je in staat deze netjes binnen de paginamarges te plaatsen. Dit beantwoordt **how to set chart size**.

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

Je kunt de breedte‑ en hoogte‑waarden aanpassen aan je lay‑outbehoeften. Onthoud dat 1 point ≈ 1/72 inch.

## Stap 7: Voeg de grafiek in het Word‑document in

Nu is de grafiek klaar om geplaatst te worden. De `insertChart`‑methode van `DocumentBuilder` verzorgt de invoeging.

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

Dit is de kern van de **insert chart into word**‑operatie.

## Stap 8: Sla het document op

Tot slot schrijf je het document naar schijf. Het bestand zal de radiale grafiek bevatten die je zojuist hebt gemaakt.

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Het uitvoeren van het programma genereert `RadialChart.docx` in de werkmap van het project. Het openen van het bestand in Microsoft Word toont een radiale grafiek met drie gegevenspunten en zichtbare graduaties.

### Verwachte output

* Een Word‑bestand met de naam `RadialChart.docx`
* In het bestand bevindt zich één pagina met een radiale grafiek van 400 × 300 points
* De grafiek toont één reeks met de titel **Series 1** en waarden **10, 20, 30**
* Graduaties (radiale rasterlijnen) zijn zichtbaar rondom de grafiek

## Veelvoorkomende variaties en randgevallen

| Situatie | Wat te wijzigen | Reden |
|----------|----------------|-------|
| **Meerdere reeksen** | Roep `chart.getSeries().add(...)` aan voor elke reeks | Stelt vergelijkende gegevensvisualisatie mogelijk |
| **Ander grafiektype** | Vervang `ChartType.RADIAL` door `ChartType.COLUMN` (of een ander) | Gebruik het grafiektype dat het beste bij je gegevens past |
| **Aangepaste kleuren** | Toegang tot `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` | Verbeterde visuele branding |
| **Oudere Aspose.Words‑versie** | Laat de regel `setShowGraduations` weg of upgrade de bibliotheek | Voorkomt `NoSuchMethodError` |
| **Opslaan in een ander formaat** | Gebruik `doc.save("RadialChart.pdf", SaveFormat.PDF)` | Genereert een PDF in plaats van een DOCX |

## Volledig uitvoerbaar voorbeeld

Hieronder staat het volledige, zelfstandige Java‑programma. Kopieer het naar een bestand met de naam `RadialChartExample.java`, voeg de Aspose.Words‑dependency toe en voer het uit.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## Conclusie

Je weet nu hoe je programmatically **een radiale grafiek maakt**, **een gegevensreeks aan de grafiek toevoegt**, **hoe je de grafiekgrootte instelt** regelt, en **een grafiek in Word invoegt**, terwijl je begint met een **leeg Word‑document**. Het voorbeeld maakt gebruik van Aspose.Words for Java 24.9, maar dezelfde concepten gelden voor andere grafiekbibliotheken die een vergelijkbare API bieden.

### Volgende stappen

* Verken andere grafiektype­s (`ChartType.PIE`, `ChartType.LINE`, enz.) – dit sluit aan bij het secundaire trefwoord **insert chart into word**.
* Pas as‑labels, legenda's en kleuren aan om aan je merkrichtlijnen te voldoen.
* Genereer grafieken dynamisch vanuit database‑query's of CSV‑bestanden.
* Converteer de resulterende `.docx` naar PDF voor distributie (`doc.save("output.pdf", SaveFormat.PDF)`).

Voel je vrij om te experimenteren met de afmetingen, reeksen en stijlopties om de exacte visualisatie te creëren die je nodig hebt. Veel plezier met coderen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe maak je een kolomgrafiek met Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Word‑document maken met Java – Rechthoekvorm toevoegen met schaduweffect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Area‑grafiek invoegen in een Word‑document](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}