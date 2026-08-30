---
category: general
date: 2026-07-16
description: Maak een taartdiagram in Java met Aspose.Words. Leer hoe je leidende
  lijnen toevoegt, de legende van het diagram weergeeft en een segment uit elkaar
  trekt in één tutorial.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: nl
lastmod: 2026-07-16
og_description: Maak een taartdiagram in Java met Aspose.Words. Deze handleiding laat
  zien hoe je leidingslijnen toevoegt, de legende van het diagram weergeeft en een
  partje explodeert, waardoor je binnen enkele minuten een gepolijste visual krijgt.
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: Maak een taartdiagram met Aspose.Words Java – Volledige opmaak tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: Maak een cirkeldiagram met Aspose.Words Java – Volledige stapsgewijze handleiding
url: /nl/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een taartdiagram met Aspose.Words Java – Volledige stapsgewijze handleiding

Heb je je ooit afgevraagd hoe je **een taartdiagram** programmatically in Java kunt maken zonder te worstelen met low‑level teken‑API’s? Je bent niet de enige. Veel ontwikkelaars hebben snel een visual nodig voor rapporten, dashboards of geautomatiseerde documenten, en ze grijpen naar Aspose.Words omdat het het zware werk uit handen neemt.  

In deze tutorial lopen we een compleet, kant‑en‑klaar voorbeeld door dat niet alleen **een taartdiagram maakt**, maar je ook laat zien hoe je **leidende lijnen** toevoegt, **de diagramlegenda** weergeeft en zelfs **een partitie explodeert** voor nadruk. Aan het einde heb je een `.docx`‑bestand dat er zo gepolijst uitziet dat het een klant kan imponeren.

> **Snelle winst:** Het code‑fragment hieronder werkt direct met Aspose.Words for Java 23.9 (of elke nieuwere versie). Geen extra afhankelijkheden, alleen de JAR.

## Wat je zult leren

- Een leeg Word‑document opzetten met `DocumentBuilder`.
- Een **taartdiagram** van aangepaste grootte invoegen.
- De **explode‑partitie**‑functie gebruiken om een datapunt te benadrukken.
- **Leidende lijnen** inschakelen zodat de geëxplodeerde partitie verbonden blijft met het label.
- De **diagramlegenda** activeren zodat lezers direct elke partitie kunnen identificeren.
- Het resultaat opslaan naar een `.docx`‑bestand dat je kunt openen in Microsoft Word of LibreOffice.

**Voorwaarden** – Je hebt nodig:

1. Java 17 (of later) geïnstalleerd.
2. Aspose.Words for Java JAR op je classpath.
3. Een eenvoudige IDE of teksteditor – IntelliJ IDEA, Eclipse, VS Code, wat je maar prefereert.

Laten we nu beginnen.

## Stap 1: Initialiseert het document en de builder – Voorbereiden om **taartdiagram te maken**

Eerst hebben we een schoon documentcanvas nodig. `Document` vertegenwoordigt het volledige Word‑bestand, terwijl `DocumentBuilder` de helper is die ons inhoud laat toevoegen.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **Waarom dit belangrijk is:** Beginnen met een verse `Document` garandeert dat er geen verborgen stijlen of achtergebleven objecten zijn die de weergave van het diagram kunnen verstoren.

## Stap 2: Het **taartdiagram** invoegen – Grootte doet ertoe

Aspose.Words maakt diagraminvoeging een één‑regel‑actie. Hier vragen we om een taartdiagram van 400 × 300 punten – ongeveer 5,5 × 4,2 inch op een typisch scherm.

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **Pro tip:** Als je een andere grootte nodig hebt, wijzig dan simpelweg de twee numerieke argumenten. De API werkt in punten, waarbij 72 punten = 1 inch.

## Stap 3: **Hoe een partitie te exploderen** – Een belangrijk datapunt benadrukken

Een partitie exploderen haalt deze uit de rest van de taart, waardoor de aandacht van de lezer wordt getrokken. De methode `setExplosion` neemt een integer die de afstand in punten aangeeft.

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **Wat als je meerdere series hebt?** Je kunt `setExplosion` aanroepen op elke series‑index (`get(1)`, `get(2)`, …) om verschillende partities te exploderen.

## Stap 4: **Leidende lijnen toevoegen** en **diagramlegenda weergeven** – De puntjes op de i zetten

Wanneer een partitie wordt geëxplodeerd, kan het label wegdrijven. Leidende lijnen houden het label vast, waardoor de leesbaarheid behouden blijft. Tegelijkertijd biedt een legenda een snelle sleutel voor alle partities.

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **Waarom leidende lijnen inschakelen?** Zonder deze kan het label zweven, waardoor gebruikers niet weten bij welke partitie het hoort.  
> **Een aangepaste legendarpositie nodig?** Gebruik `chart.getLegend().setPosition(LegendPosition.TOP)` of een andere enum‑waarde.

## Stap 5: Het document opslaan – De laatste **taartdiagram‑maak** stap

Tot slot slaan we het document op schijf op. Pas het pad aan naar een map waar je schrijfrechten voor hebt.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

Voer het programma uit, open het gegenereerde `PieChartDemo.docx`, en je zou een mooi opgemaakt taartdiagram moeten zien met een geëxplodeerde eerste partitie, leidende lijnen en een zichtbare legenda.

![Pie chart example showing exploded slice and legend](pie-chart-example.png){: .center-image alt="Create pie chart example with exploded slice, leader lines, and legend"}

### Verwachte output

Wanneer je het Word‑bestand opent, ziet het diagram er ongeveer zo uit:

- Een taartdiagram van 400 × 300 pt.
- De eerste partitie is verschoven met 10 pt.
- Een dunne leidende lijn verbindt de geëxplodeerde partitie met zijn label.
- Een legenda onder het diagram geeft elke seriesnaam weer.

Zie je de leidende lijn niet, controleer dan of `setLeaderLines(true)` *na* de explosie‑instelling wordt aangeroepen — de volgorde is belangrijk.

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Probleem | Waarom het gebeurt | Oplossing |
|----------|--------------------|-----------|
| **Geen legenda zichtbaar** | `setShowLegend(true)` ontbrak of werd aangeroepen op het verkeerde diagramobject. | Zorg ervoor dat je `chart.setShowLegend(true)` **na** het ophalen van de `Chart` van de shape aanroept. |
| **Leidende lijn ontbreekt** | De partitie was niet geëxplodeerd, of het diagramtype ondersteunt geen leidende lijnen. | Alleen `ChartType.PIE` (of `PIE_3D`) ondersteunt leidende lijnen. Roep eerst `setExplosion` aan, daarna `setLeaderLines(true)`. |
| **Partitie beweegt niet** | Explosiewaarde te laag (0‑2 pt). | Verhoog de integer, bv. `setExplosion(10)` of hoger voor een dramatischer effect. |
| **Diagram ziet er vervormd uit** | Een niet‑vierkante grootte (breedte ≠ hoogte) kan de taart samendrukken. | Houd breedte en hoogte gelijk of dichtbij; 400 × 300 werkt, maar 400 × 400 geeft een perfecte cirkel. |

## Geavanceerde aanpassingen (optioneel)

Wil je verder gaan dan de basis, overweeg dan:

- **Aangepaste kleuren**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **Datalabels**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **3‑D‑effect**: Vervang `ChartType.PIE` door `ChartType.PIE_3D`.

Met deze opties kun je het uiterlijk afstemmen op de huisstijlrichtlijnen van je organisatie.

## Samenvatting – Wat we hebben bereikt

We begonnen met een leeg Word‑document, **een taartdiagram gemaakt**, **de eerste partitie geëxplodeerd**, **leidende lijnen toegevoegd**, en **de diagramlegenda weergegeven**. De volledige workflow past in een beknopte `main`‑methode, waardoor hij eenvoudig in grotere rapportage‑pipelines kan worden geïntegreerd.

## Volgende stappen

- **Meer series toevoegen**: Vul het diagram met echte gegevens uit een database of CSV‑bestand.
- **Exporteren naar PDF**: Gebruik `doc.save("output.pdf", SaveFormat.PDF);` om een PDF‑versie te genereren.
- **Combineren met andere vormen**: Voeg tabellen, afbeeldingen of extra diagrammen toe voor een volledig rapport.

Ben je benieuwd naar andere diagramtypen — kolom, balk, lijn — vervang dan simpelweg `ChartType.PIE` door de gewenste enum en volg dezelfde opmaakstappen.

---

*Veel plezier met diagrammen!* Laat gerust een reactie achter als iets niet werkte zoals verwacht, of deel hoe jij de legendarpositie hebt aangepast. Jouw feedback helpt ons allemaal betere geautomatiseerde documenten te bouwen.


## Wat moet je hierna leren?


De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)
- [How to Add Watermark to Documents Using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}