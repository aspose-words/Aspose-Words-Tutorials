---
category: general
date: 2026-10-26
description: Maak een donutgrafiek en voeg een taartgrafiek in Java toe met stapsgewijze
  code. Leer de volledige workflow voor flexibele grafiekvisualisaties.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: nl
lastmod: 2026-10-26
og_description: Maak een donutgrafiek in Java met deze gids, die ook laat zien hoe
  je een cirkeldiagram kunt invoegen voor flexibele visualisaties.
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: Maak een donutgrafiek en voeg een taartgrafiek in – Java-gids
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: Hoe maak je een donutgrafiek en voeg je een cirkeldiagram in
url: /nl/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe maak je een doughnut chart en voeg je een pie chart in

Als je een **doughnut chart maken** in Java moet, leidt deze tutorial je stap voor stap door het proces. We laten ook zien hoe je een **pie chart invoegen** met dezelfde builder‑API, zodat je moeiteloos tussen visuele stijlen kunt schakelen. Aan het einde van de gids heb je een compleet, uitvoerbaar programma dat beide diagramtypen produceert en veelvoorkomende aanpassingen demonstreert.

De tutorial behandelt:

* Initialiseren van de chart builder die door de gekozen bibliotheek wordt geleverd.  
* Een doughnut chart maken en de gatgrootte configureren.  
* Een pie chart invoegen en een partitie laten exploderen voor nadruk.  
* Tips voor het omgaan met randgevallen zoals ontbrekende series of niet‑ondersteunde diagramtypen.

Je hebt alleen een recente JDK (8 of hoger) en de chart‑bibliotheek‑JAR op je classpath nodig. Er zijn geen externe services vereist.

---

## Vereisten

| Item | Reden |
|------|--------|
| Java Development Kit (JDK) 8+ | Vereist om het voorbeeld te compileren en uit te voeren. |
| Chart library (e.g., **Aspose.Cells for Java** or **JFreeChart**) | Biedt `ChartBuilder`, `ChartType` en methoden voor seriesmanipulatie die in de code worden gebruikt. |
| An IDE or a text editor | Om het Java‑bronbestand te schrijven en uit te voeren. |

Zorg ervoor dat de bibliotheek‑JAR aan het build‑pad van je project wordt toegevoegd. Als je Maven gebruikt, voeg dan de juiste dependency toe; anders plaats je de JAR in de `libs`‑map en verwijs je er tijdens het compileren naar.

---

## Stap 1: De chart builder instellen

De eerste stap is het aanmaken van een `ChartBuilder` (of equivalent) instantie die de diagramobjecten genereert. Dit object fungeert als een fabriek en bevat het werkblad of canvas waarop het diagram wordt geplaatst.

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**Waarom dit belangrijk is:**  
De builder koppelt het diagram aan een specifiek werkblad, waardoor alle daaropvolgende diagramobjecten hetzelfde tekenoppervlak delen. Als je deze stap overslaat, heb je geen doellocatie voor de visuele elementen.

---

## Stap 2: **Doughnut chart maken**

Nu genereren we een doughnut chart met een gedefinieerde grootte. De gatgrootte bepaalt hoeveel van het centrum van het diagram leeg is, waardoor een gewone taart een doughnut wordt.

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**Uitleg:**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` maakt het diagramobject aan en reserveert ruimte op het werkblad.  
* `setHoleSize(30)` zet de taart om in een doughnut met een 30 % leeg centrum.  
* `add("{10, 20, 30, 40}", true)` levert vier datapunten; de `true`‑vlag vertelt de bibliotheek de waarden als één enkele serie te behandelen.  

**Randgeval:** Als het geselecteerde diagramtype geen gat ondersteunt (bijv. een staafdiagram), veroorzaakt het aanroepen van `getDoughnutChart()` een uitzondering. Controleer altijd het diagramtype voordat je de gatgrootte aanpast.

---

## Stap 3: **Pie chart invoegen**

Nadat de doughnut klaar is, laten we zien hoe je een **pie chart** kunt **invoegen** met dezelfde builder. Deze stap benadrukt de overeenkomst tussen de twee diagramtypen en toont hoe je een partitie kunt accentueren.

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**Uitleg:**  

- `ChartType.PIE` geeft de builder de opdracht een klassiek taartdiagram te maken.  
- `setExplode(10)` verschuift de eerste partitie met 10 % van de radius, een veelgebruikte techniek om een belangrijk datapunt te accentueren.  

**Tip:** De `setExplode`‑methode werkt alleen op de eerste serie van een pie chart. Als je meerdere series hebt, moet je de juiste index targeten.

---

## Stap 4: Werkmap opslaan

Schrijf tenslotte de werkmap naar een bestand zodat je de diagrammen kunt bekijken in Excel of een andere compatibele viewer.

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**Waarom nu opslaan:** Het opslaan van de werkmap voltooit alle tekenbewerkingen. Proberen het bestand te bekijken voordat het is opgeslagen resulteert in een leeg of onvolledig document.

**Resultaat:** Het openen van *DoughnutAndPieChart.xlsx* toont een doughnut‑diagram met een 30 % gat aan de linkerkant en een pie chart met een geëxplodeerde eerste partitie aan de rechterkant.

---

## Stap 5: Veelvoorkomende variaties en probleemoplossing

| Situatie | Aanpassing |
|-----------|------------|
| **Verschillende diagramafmetingen** | Wijzig de breedte- en hoogte‑argumenten in `insertChart`. |
| **Meerdere dataseries** | Roep `add` meerdere keren aan of geef een 2‑D‑array‑string door. |
| **Dynamische gatgrootte** | Bereken de gatgrootte op basis van het gegevensbereik en roep vervolgens `setHoleSize` aan. |
| **Meerdere partities exploderen** | Loop door `chart.getSeries().get(i).setExplode(percent)` voor elke partitie die je wilt verschuiven. |
| **Bibliotheek ondersteunt geen doughnut** | Gebruik een pie chart en teken handmatig een witte cirkel eroverheen, hoewel dit minder nauwkeurig is. |

**Pro tip:** Roep altijd `builder.flush()` (indien beschikbaar) aan na het invoegen van diagrammen bij het werken met grote werkmappen. Dit geeft interne buffers vrij en voorkomt geheugenlekken.

![Java‑code die een doughnut chart maakt en een pie chart invoegt](https://example.com/images/doughnut-pie-java.png "voorbeeld van doughnut chart maken in Java")

*De afbeelding toont de uiteindelijke werkmapindeling met beide diagrammen naast elkaar.*

---

## Conclusie

Je weet nu hoe je een **doughnut chart** kunt **maken** en een **pie chart** kunt **invoegen** in Java met behulp van een vloeiende builder‑API. Het volledige voorbeeld behandelt initialisatie, grootte‑configuratie, gatgrootte, partitie‑explosie en bestandsoutput. Vanaf hier kun je extra aanpassingen verkennen, zoals kleuren, legenda's en gegevenslabels, om aan je rapportage‑eisen te voldoen.

**Volgende stappen**

* Experimenteer met **chart customization Java**‑functies zoals gradient‑vullingen en gegevenslabels.  
* Integreer de diagramgeneratie in een webservice die de werkmap op aanvraag retourneert.  
* Vergelijk de builder‑aanpak met andere bibliotheken (bijv. JFreeChart) om de beste keuze voor je project te bepalen.

Veel plezier met diagrammen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe maak je een doughnut chart in een Word‑document met Java](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [Word‑document opslaan na het bewerken van een doughnut chart in Java](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [Pie chart invoegen in Java – Exploderen, roteren & partities accentueren](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}