---
category: general
date: 2026-10-10
description: Leer hoe je een diagram in een Word‑bestand draait en het diagram in
  Word aanpast om de grootte van een donutdiagram te wijzigen, met een volledig Java‑voorbeeld.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: nl
lastmod: 2026-10-10
og_description: Hoe een grafiek in een Word‑bestand te roteren en de grafiek in Word
  aan te passen om de grootte van een donutgrafiek te wijzigen met Aspose.Words voor
  Java.
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: Hoe een grafiek in een Word‑document te roteren – stapsgewijze Java‑gids
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Hoe een grafiek te roteren in een Word‑document met Aspose.Words
url: /nl/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een grafiek te roteren in een Word-document met Aspose.Words

Als je **grafiek roteren** binnen een Microsoft Word‑bestand moet uitvoeren, laat deze gids je de exacte stappen zien. Je leert ook hoe je **grafiek bewerken in Word** kunt **de grootte van een donutgrafiek wijzigen** zonder je Java‑code te verlaten.

Word‑automatisering voelt vaak aan als een reeks losstaande API‑aanroepen, maar met Aspose.Words kun je een grafiek behandelen als elk ander documentknooppunt. Aan het einde van deze tutorial heb je een uitvoerbaar programma dat een bestaande `.docx` laadt, een donutgrafiek met 45° roteert, het gat verkleint tot 50 % van de straal, en het resultaat opslaat als een nieuw bestand.

## Vereisten

* Java 17 of nieuwer geïnstalleerd.
* Maven (of Gradle) om afhankelijkheden te beheren.
* Een invoer‑Word‑document (`input.docx`) dat al een donutgrafiek bevat.
* Een geldige Aspose.Words for Java‑licentie (of gebruik de evaluatiemodus).

## Stap 1: Het Maven‑project opzetten

Maak een nieuw Maven‑project aan of voeg de volgende afhankelijkheid toe aan je bestaande `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

Het uitvoeren van `mvn clean install` downloadt de bibliotheek en maakt de klassen beschikbaar op je classpath.

## Stap 2: Het Word‑document laden dat een grafiek bevat

De eerste handeling is het openen van het bestaande document. De `Document`‑klasse vertegenwoordigt het volledige bestand.

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Het laden van het bestand **wijzigt** het niet; het maakt simpelweg een in‑memory‑representatie aan die je kunt opvragen en bewerken.

## Stap 3: Een DocumentBuilder maken voor navigatie

`DocumentBuilder` biedt een cursor‑achtige API om door de documentboom te lopen. We zullen het gebruiken om de eerste grafiek‑shape te vinden.

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

De builder start aan het begin van het document, maar je kunt hem later naar elk knooppunt verplaatsen indien nodig.

## Stap 4: Het eerste grafiek‑shape ophalen

Grafieken worden opgeslagen als `Shape`‑knooppunten. Door kind‑knooppunten van het type `NodeType.SHAPE` te filteren, kunnen we het grafiekobject extraheren.

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

Als het document meerdere grafieken bevat, kun je itereren over `getChildNodes` en elk `Shape` controleren op `hasChart()` voordat je cast.

## Stap 5: De grafiek roteren (grafiek roteren)

Een donutgrafiek is in wezen een taartgrafiek met een gat. Het roteren verandert de starthoek van het eerste segment.

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

De `setStartAngle`‑methode verwacht een double die graden weergeeft. Positieve waarden roteren met de klok mee, negatieve waarden roteren tegen de klok in.

## Stap 6: De grootte van het donutgat wijzigen (grootte van donutgrafiek wijzigen)

De gatgrootte wordt uitgedrukt als een fractie van de grafiekstraal. Een waarde van `0.5` betekent dat het gat 50 % van de totale straal inneemt.

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**Tip:** Het geldige bereik is `0.0` (geen gat, d.w.z. een gewone taart) tot `0.9` (zeer dunne ring). Waarden buiten dit bereik zullen een `IllegalArgumentException` veroorzaken.

## Stap 7: Het gewijzigde document opslaan

Schrijf tenslotte de wijzigingen terug naar de schijf.

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

Wanneer je `DoughnutFormatted.docx` opent in Microsoft Word, zie je dat de donutgrafiek 45° is geroteerd en het gat is verkleind tot de helft van de oorspronkelijke grootte.

## Volledig, uitvoerbaar voorbeeld

Door alle onderdelen samen te voegen, hier is het volledige programma dat je kunt kopiëren‑plakken in je IDE:

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### Verwachte output

Het uitvoeren van het programma geeft het volgende weer:

```
Chart rotated and doughnut size changed successfully.
```

Het openen van `DoughnutFormatted.docx` toont een donutgrafiek waarvan het eerste segment start op de 45°‑positie en waarvan de binnenstraal de helft van de buitenstraal beslaat.

## Veelvoorkomende variaties en randgevallen

| Situatie | Wat aan te passen | Waarom het belangrijk is |
|-----------|-------------------|--------------------------|
| **Meerdere grafieken** | Loop door `getChildNodes(NodeType.SHAPE, true)` en controleer `shape.hasChart()` voor elk | Garandeert dat je de beoogde grafiek wijzigt in plaats van de eerste |
| **Staaf‑ of lijngrafiek** | `setStartAngle` is niet van toepassing; gebruik `chart.getSeries().get(0).setFillFormat(...)` voor andere visuele aanpassingen | Niet alle grafiektype­s ondersteunen rotatie; donut‑/taartgrafieken zijn de enige met een starthoek |
| **Grafiek zonder donutgat** | Sla `setDoughnutHoleSize` over of converteer eerst het grafiektype naar donut via `chart.setChartType(ChartType.DONUT)` | Het wijzigen van de gatgrootte op een niet‑donutgrafiek veroorzaakt een uitzondering |
| **Grote documenten** | Gebruik `DocumentBuilder.moveToDocumentStart()` en `builder.moveToNode(chartShape)` voor gerichte navigatie | Verbeterde prestaties door het vermijden van volledige doorloop van niet‑relevante knooppunten |

## Pro‑tips voor betrouwbare grafiekmanipulatie

* **Cache de grafiek‑referentie** – Als je van plan bent meerdere eigenschappen te wijzigen, bewaar dan een lokale `Chart`‑variabele in plaats van herhaaldelijk `chartShape.getChart()` aan te roepen.
* **Valideer invoerwaarden** – Controleer vóór het aanroepen van `setStartAngle` of `setDoughnutHoleSize` het bereik om runtime‑fouten te voorkomen.
* **Gebruik een licentie** – De evaluatiemodus voegt een watermerk toe op de eerste pagina. Het toepassen van een licentie (`License license = new License(); license.setLicense("Aspose.Words.lic");`) verwijdert dit.

## Volgende stappen

Nu je weet hoe je een **grafiek rotert** en de **grootte van een donutgrafiek wijzigt**, kun je andere **grafiek bewerken in Word** scenario's verkennen:

* Verander de segmentkleuren met `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())`.
* Voeg gegevenslabels toe door `chart.getSeries().get(0).setHasDataLabel(true)` aan te roepen.
* Exporteer de grafiek als afbeelding met `chart.toImage(300, 300, ImageType.PNG)`.

Elk van deze uitbreidingen volgt hetzelfde patroon: verkrijg het `Chart`‑object, roep de juiste setter aan, en sla het document op.

---

**Je hebt zojuist geleerd hoe je donutgrafieken in Word met Java kunt roteren en van grootte kunt veranderen.** Voel je vrij om de code aan te passen voor andere grafiektype­s, te integreren in een grotere document‑generatie‑pipeline, of te combineren met Aspose.Slides voor PowerPoint‑automatisering. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe een kolomgrafiek maken met Aspose.Words voor Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Grafiekas verbergen in een Word‑document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Bubbelgrafiek invoegen in Word‑document](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}