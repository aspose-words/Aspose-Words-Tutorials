---
category: general
date: 2026-09-24
description: Voeg een taartdiagram in een DOCX in met Aspose.Words voor Java. Leer
  de gatgrootte instellen, een part van de taart laten exploderen, een taartdiagramdeel
  markeren en moeiteloos een docx-diagram maken.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: nl
lastmod: 2026-09-24
og_description: Voeg een taartdiagram toe aan een DOCX met Aspose.Words voor Java.
  Beheers het instellen van de gatgrootte, het exploderen van een taartpunt, het markeren
  van een taartdiagramsegment en maak binnen enkele minuten een DOCX-diagram.
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: Voeg taartdiagram‑woord in Java in – stap‑voor‑stap handleiding
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: Voeg taartdiagram‑woord in Java toe – volledige gids
url: /nl/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Invoegen pie chart word in Java – volledige gids

Als je **insert pie chart word** in een DOCX‑bestand moet invoegen, laat deze tutorial je precies zien hoe je dat doet met Aspose.Words for Java. Je ziet de volledige workflow, van het maken van het document tot het aanpassen van de grafiek zodat het segment wordt geëxplodeerd, de gatgrootte op nul wordt gezet en het segment wordt gemarkeerd.

Werken met grafieken in Word‑documenten voelt vaak als een apart onderwerp ten opzichte van reguliere tekstverwerking, maar Aspose.Words verenigt beide. In de onderstaande stappen leer je ook hoe je **create docx chart**‑bestanden maakt die klaar zijn om te openen in Microsoft Word, Google Docs of een andere DOCX‑compatibele viewer.

## Wat je gaat bereiken

* **Insert pie chart word** in een leeg document invoegen  
* **Set hole size** om de grafiek om te zetten in een volledige cirkel (geen donut)  
* **Explode pie slice** om de aandacht te vestigen op een specifiek segment  
* **Highlight pie chart slice** met aangepaste opmaak  
* **Create docx chart** die kan worden gedeeld of verder bewerkt  

### Vereisten

* Java 17 of later (de code compileert ook met Java 8)  
* Aspose.Words for Java‑bibliotheek (versie 23.9 of nieuwer)  
* Een IDE of build‑tool (Maven/Gradle) die de Aspose.Words‑dependency kan oplossen  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## Hoe pie chart word in een DOCX in te voegen met Aspose.Words

De eerste stap is een nieuw leeg document aan te maken en een `DocumentBuilder` te verkrijgen. De builder geeft je directe toegang tot de content‑stream van het document, waardoor het triviaal wordt om **insert pie chart word** uit te voeren.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### Waarom dit belangrijk is
`Document` vertegenwoordigt het volledige Word‑bestand, terwijl `DocumentBuilder` de high‑level API is die je in staat stelt alinea's, tabellen en grafieken in te voegen zonder met low‑level XML te werken. Beginnen met een leeg document zorgt ervoor dat de grafiek die je toevoegt de enige inhoud is, wat perfect is voor leren of voor het genereren van op sjablonen gebaseerde rapporten.

## Stel hole size in om een volledige cirkel te maken

Standaard maakt Aspose.Words een donut‑grafiek wanneer je een pie chart aanvraagt. Om van de grafiek een echte cirkel te maken, moet je **set hole size** op `0` zetten. Dit verwijdert het binnenste gat en geeft een klassieke cirkel‑uiterlijk.

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### Praktische tip
Als je later besluit over te schakelen naar een donut‑grafiek, wijzig je eenvoudig de `holeSize`‑waarde naar een percentage (bijv. `30`). dezelfde API werkt voor beide grafiektype.

## Explode pie slice om een segment te markeren

Het exploderen van een segment laat het visueel opvallen. De **explode pie slice**‑operatie verplaatst het gekozen segment naar buiten toe met een percentage van de grafiek‑radius.

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### Waarom exploderen?
Een geëxplodeerd segment trekt de aandacht van de lezer naar het belangrijkste datapunt—perfect voor dashboards of managementsamenvattingen. De waarde `20` betekent 20 % van de radius; je kunt deze aanpassen tussen `0` (geen explosie) en `100` (volledig losgemaakt).

## Highlight pie chart slice met aangepaste opmaak

Naast het exploderen wil je misschien **highlight pie chart slice** door de vulkleur of rand te wijzigen. Terwijl de demo‑code zich richt op explosie, kun je deze als volgt uitbreiden:

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### Expertopmerking
Het wijzigen van de vulkleur van een specifiek segment vereist toegang tot het `DataPoint`‑object. Als je meerdere series hebt, doorloop je `series.getDataPoints()` en pas je stijlen conditioneel toe.

## Sla de gemaakte docx chart op en controleer

Tot slot **create docx chart** je door het `Document` op te slaan. Het resulterende bestand kan worden geopend in Microsoft Word om de opgemaakte cirkeldiagram te zien.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### Verwachte output
Het openen van `PieChartFormatted.docx` toont één cirkeldiagram:

* De grafiek beslaat een gebied van 400 × 300 pt.  
* De hole size is `0`, dus de grafiek is een volledige cirkel.  
* Het eerste segment is geëxplodeerd met 20 % en rood gekleurd (als je de optionele opmaak hebt toegevoegd).  

Je hebt nu een **create docx chart** die kan worden verspreid, ingesloten in e‑mails, of programmatisch verder bewerkt.

---

## Veelvoorkomende variaties en randgevallen

| Scenario | How to adapt the code |
|----------|----------------------|
| **Multiple series** | Loop over `pieChart.getChart().getSeries()` en stel `Explosion` of `FillColor` per serie in. |
| **Dynamic data** | Vul de series met waarden uit een database of CSV voordat je `setExplosion` aanroept. |
| **Different chart size** | Verander de breedte/hoogte‑argumenten in `insertChart(ChartType.PIE, width, height)`. |
| **Export to PDF** | Na het opslaan van de DOCX, roep `doc.save("output.pdf")` aan om een PDF‑versie van dezelfde grafiek te maken. |
| **Localization** | Gebruik `DocumentBuilder.insertChart` met een locale‑specifiek getalformaat voor labels. |

### Pro‑tip
Roep altijd `setHoleSize(0)` **na** `insertChart` aan. Als je het vóór het invoegen instelt, zal Aspose.Words terugkeren naar de standaard donut‑grootte zodra de grafiek is gemaakt.

---

## Samenvatting

Je weet nu hoe je **insert pie chart word** in een Word‑document kunt invoegen met Java, hoe je **set hole size** instelt voor een volledige cirkel, hoe je **explode pie slice** gebruikt om aandacht te trekken, en hoe je **highlight pie chart slice** met aangepaste kleuren kunt markeren. Het volledige voorbeeld laat ook zien hoe je **create docx chart**‑bestanden maakt die klaar zijn voor distributie.

---

## Volgende stappen

* Verken andere grafiektype (`BAR`, `LINE`, `SCATTER`) met `ChartType`.  
* Combineer grafiekgeneratie met mail‑merge om gepersonaliseerde rapporten te maken.  
* Integreer de gegenereerde DOCX in een webservice die het bestand op aanvraag retourneert.  

Als je tegen problemen aanloopt, controleer dan of je een compatibele versie van Aspose.Words gebruikt en of de uitvoermap bestaat en beschrijfbaar is.

Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe een kolomgrafiek te maken met Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Word Chart API gebruiken](/words/english/net/programming-with-charts/)
- [Een bubbelgrafiek invoegen in Word met Aspose.Words voor .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}