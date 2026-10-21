---
category: general
date: 2026-08-20
description: Voeg snel aanwijzingslijnen toe aan een taartdiagram in Java. Leer hoe
  je segmenten kunt invoegen, laten exploderen, opnieuw kleuren en labelen met de
  Chart API.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: nl
lastmod: 2026-08-20
og_description: Voeg leader lines toe aan een taartdiagram in Java met een beknopt
  voorbeeld. Volg deze gids om segmenten in te voegen, te exploderen, opnieuw te kleuren
  en te labelen met behulp van de Chart API.
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: Leidende lijnen toevoegen aan een taartdiagram in Java – stapsgewijze Chart
  API‑gids
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: Hoe leidende lijnen toevoegen aan een taartdiagram in Java met de Chart API
url: /nl/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe leiderlijnen toe te voegen aan een taartdiagram in Java met de Chart API

Als je **leiderlijnen wilt toevoegen aan een taartdiagram** in Java, leidt deze gids je door het volledige proces. Je ziet hoe je een taartdiagram invoegt, een partitie explodeert voor nadruk, de kleur wijzigt, en uiteindelijk leiderlijnen inschakelt die het geëxplodeerde segment labelen.

Het voorbeeld maakt gebruik van de standaard Chart API die in veel Java-rapportagelibrairies voorkomt. Er zijn geen externe tools nodig, en de code draait op elke JDK 8+ omgeving.

## Wat je zult bereiken

* Maak een `Chart` van type `ChartType.PIE` met een aangepaste grootte.  
* Explodeer de eerste partitie om aandacht te trekken.  
* Stel de sectorkleur van de geëxplodeerde partitie in op blauw.  
* **Leiderlijnen toevoegen aan een taartdiagram** zodat het partitieslabel duidelijk verbonden is.

Je zou al een Java-project moeten hebben met de Chart-bibliotheek op het classpath. Als je Maven gebruikt, voeg dan de afhankelijkheid toe die in de sectie vereisten wordt getoond.

## Vereisten

* JDK 8 of nieuwer geïnstalleerd.  
* De Chart-bibliotheek (bijv. `com.example.chart:chart-api:2.5.0`).  
* Basiskennis van Java-klassen en methode‑aanroepen.

---

## Hoe leiderlijnen toe te voegen aan een taartdiagram

Hieronder staat een volledig, uitvoerbaar programma dat elke stap demonstreert. De code is opzettelijk zelf‑voorzienend zodat je deze kunt kopiëren, plakken en uitvoeren zonder aanpassingen.

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### Uitleg van elke stap

| Stap | Wat de code doet | Waarom het belangrijk is |
|------|-------------------|--------------------------|
| **1️⃣ Invoegen van een taartdiagram** | `builder.insertChart(ChartType.PIE, 400, 300)` maakt een taartdiagram van 400 × 300 pixel. | Stelt de grafiekcontainer in en definieert de afmetingen, wat invloed heeft op de plaatsing van labels en de lengte van de leiderlijnen. |
| **2️⃣ Explodeer de eerste partitie** | `setExplosion(20)` verschuift de partitie met 20 % van de radius. | Een geëxplodeerde partitie trekt de aandacht van de kijker en maakt de leiderlijn zichtbaar. |
| **3️⃣ Stel sectorkleur in** | `setSectorColor(Color.BLUE)` verandert de vulling van de partitie naar blauw. | Kleurcontrast verbetert de leesbaarheid, vooral wanneer de partitie is gemarkeerd. |
| **4️⃣ Schakel leiderlijnen in** | `setLeaderLines(true)` zet de verbindingslijnen aan die de partitie met zijn label verbinden. | Leiderlijnen zorgen ervoor dat het label leesbaar blijft, zelfs wanneer de partitie naar buiten wordt verplaatst. |

De `saveAsPng`‑aanroep is optioneel maar handig om het visuele resultaat te verifiëren. Na het uitvoeren van het programma zou je een afbeelding moeten zien die lijkt op de onderstaande.

![Add leader lines to pie chart](https://example.com/assets/pie-leader-lines.png "Add leader lines to pie chart – exploded slice with blue color and leader lines")

*Figuur: Een taartdiagram waarbij de eerste partitie is geëxplodeerd, blauw gekleurd, en verbonden met zijn label door een leiderlijn.*

## Leiderslijnen aanpassen (geavanceerd)

De basisaanroep `setLeaderLines(true)` gebruikt de standaardstijl van de bibliotheek. Je kunt het uiterlijk verder aanpassen:

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

Deze opties zijn handig wanneer je de huisstijl van het bedrijf moet volgen of de toegankelijkheid wilt verbeteren.

### Meerdere series verwerken

Als je taartdiagram meer dan één serie bevat, wil je misschien alleen voor een specifieke partitie leiderlijnen. Gebruik de serie‑index om het juiste element te targeten:

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

Wanneer een partitie niet geëxplodeerd is, wordt de leiderlijn doorgaans automatisch verborgen, maar je kunt deze forceren met `setLeaderLineEnabled(true)`.

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Valkuil | Symptoom | Oplossing |
|--------|----------|-----------|
| **Leiderlijnen niet zichtbaar** | Grafiek wordt gerenderd zonder verbindingslijnen. | Zorg ervoor dat de partitie geëxplodeerd is (`setExplosion` > 0) of schakel de leiderlijnen expliciet in voor de partitie. |
| **Labels overlappen** | Labels botsen met elkaar. | Vergroot de grafiekgrootte of stel `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)` in. |
| **Kleur niet toegepast** | Partitie behoudt de standaardkleur. | Controleer of je de juiste serie‑index target (`getSeries().get(0)`). |
| **Afbeelding niet opgeslagen** | `saveAsPng` geeft een uitzondering. | Controleer de schrijfrechten voor de doelmap en of de bibliotheek PNG-export ondersteunt. |

## Volledige broncode

Voor het gemak staat hier opnieuw het volledige bronbestand, inclusief imports en commentaar:

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

Het uitvoeren van dit programma genereert `pie-with-leader-lines.png`, die een taartdiagram toont met een geëxplodeerde blauwe partitie en duidelijke leiderlijnen die naar het partitelabel wijzen.

## Conclusie

Je weet nu hoe je **leiderlijnen kunt toevoegen aan een taartdiagram** objecten in Java met de Chart API. Het proces bestaat uit het invoegen van een `ChartType.PIE`, het exploderen van de gewenste partitie, het aanpassen van de kleur, en het inschakelen van leiderlijnen. Met de optionele stijlopties kun je de lijnekleur, dikte en labelplaatsing fijn afstemmen om aan elke visuele eis te voldoen.

Vervolgens kun je gerelateerde onderwerpen verkennen zoals **pie chart explosion Java**, **set sector color Chart API**, en **builder.insertChart usage** om meer geavanceerde visualisaties te maken, zoals donut‑diagrammen, gestapelde taarten, of interactieve dashboards.

Voel je vrij om te experimenteren met verschillende partitie‑indexen, kleuren en leiderlijn‑stijlen—je diagrammen worden met elke aanpassing informatiever en visueel aantrekkelijker. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe een kolomdiagram te maken met Aspose.Words voor Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Datum‑tijdwaarden toevoegen aan as van een diagram](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [Kolomdiagram invoegen in Word met Aspose.Words voor .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}