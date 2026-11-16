---
category: general
date: 2026-11-15
description: Leer hoe je een cirkeldiagram maakt in een Word‑document en een docx
  opslaat als PDF met Java. Deze gids behandelt ook het converteren van Word naar
  PDF en hoe je een diagram toevoegt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: nl
lastmod: 2026-11-15
og_description: Maak een cirkeldiagram in een Word‑bestand en sla het docx op als
  PDF met Java. Volg deze stapsgewijze tutorial om Word naar PDF te converteren en
  diagrammen toe te voegen.
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: Maak een cirkeldiagram in Word en sla docx op als PDF – Java-gids
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: Hoe maak je een cirkeldiagram in Word en sla je een docx op als PDF
url: /nl/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe maak je een pie chart in Word en sla je docx op als PDF

Als je een **create pie chart** wilt maken binnen een Word‑document en vervolgens **save docx as PDF**, laat deze tutorial je precies zien hoe. Je ziet een volledig, uitvoerbaar voorbeeld dat een .docx‑bestand converteert naar een PDF terwijl een pie chart wordt ingebed, zodat je kunt antwoorden op “how to add chart” zonder te zoeken naar verspreide fragmenten.

In deze gids leer je:

* Laad een bestaande *.docx* (of begin vanaf nul)  
* Gebruik Aspose.Words for Java om **create pie chart** te maken en gegevens te vullen  
* **Save docx as PDF** met het diagram correct gerenderd  
* Begrijp de nuances van **convert word to pdf** wanneer diagrammen betrokken zijn  

De stappen werken met Aspose.Words 2024‑x.x en Java 17, maar de concepten zijn toepasbaar op elke bibliotheek die Word‑diagrammanipulatie ondersteunt.

## Vereisten

Voordat je begint, zorg ervoor dat je het volgende hebt:

| Vereiste | Waarom het belangrijk is |
|----------|--------------------------|
| Java 17 (or later) | Vereist door de nieuwste Aspose.Words JAR |
| Maven or Gradle build tool | Vereenvoudigt het beheer van afhankelijkheden |
| Aspose.Words for Java (latest version) | Biedt de klassen `Document`, `Chart`, en `ChartType` |
| An input **.docx** file (or a blank document) | Het diagram wordt in dit bestand ingevoegd |

Voeg de Aspose.Words‑afhankelijkheid toe aan je `pom.xml` (Maven) of `build.gradle` (Gradle). Voorbeeld voor Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Stap 1: Laad het Word‑document (of maak een nieuw document)

De eerste stap is het verkrijgen van een `Document`‑instantie. Als je al een sjabloon hebt, geef dan het pad door; anders maak je een leeg document.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*Waarom deze stap?* Het `Document`‑object is de container voor alle Word‑inhoud, inclusief diagrammen. Het laden van een bestaand bestand laat je de omringende tekst en stijlen behouden terwijl je een nieuw visueel element toevoegt.

## Stap 2: **Create pie chart** – de kern van “how to create chart”

Nu maken we een `Chart`‑object aan met `ChartType.PIE`. Dit creëert automatisch een placeholder voor een pie chart die je later kunt vullen met gegevens.

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*Uitleg*: `ChartType.PIE` vertelt Aspose.Words om een pie‑chart‑template te gebruiken. Het diagram wordt toegevoegd aan de body van het document, zodat het verschijnt waar je het nodig hebt. Dit voldoet aan de “how to add chart”‑vereiste in één enkele oproep.

## Stap 3: Vul het diagram – beantwoord “how to add chart” met gegevens

Een pie chart is betekenisloos zonder seriedata. Gebruik de `Series`‑collectie om categorieën en waarden toe te voegen.

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*Waarom dit belangrijk is*: Elke oproep van `add` maakt een segment van de cirkel. Het eerste argument is het label, het tweede is de numerieke waarde. Je kunt deze vervangen door dynamische gegevens uit een database of CSV‑bestand.

### Optioneel: Aanpassen van het uiterlijk (niet vereist maar nuttig)

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

Deze aanpassingen laten zien hoe je **how to create chart** kunt realiseren met een professionele uitstraling, zonder de Java‑code te verlaten.

## Stap 4: **Save docx as PDF** – het laatste deel van “convert word to pdf”

Zodra het diagram is ingebed, exporteer je het document naar PDF. Aspose.Words rendert het diagram als een vectorafbeelding, waardoor de kwaliteit behouden blijft.

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*Belangrijk punt*: De `save`‑methode converteert automatisch het Word‑bestand naar PDF, waarbij diagramrasterisatie, lettertype‑inbedding en paginalay-out worden afgehandeld. Dit vervult het **save docx as pdf**‑doel en toont een betrouwbare manier om **convert word to pdf** uit te voeren wanneer diagrammen aanwezig zijn.

### Verwachte output

Het uitvoeren van het programma levert `output.pdf` op dat bevat:

* De originele inhoud van `input.docx` (indien aanwezig)  
* Een volledig gerenderd pie chart met de titel *Sales Distribution Q1*  
* Nauwkeurige segmentpercentages die overeenkomen met de gegevens (40 %, 30 %, 30 %)

Open de PDF in een willekeurige viewer en je zou een scherp pie chart moeten zien, identiek aan wat je in het Word‑bestand zou zien.

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Probleem | Oorzaak | Oplossing |
|----------|---------|-----------|
| Diagram verschijnt leeg in PDF | Lettertype- of diagramrenderingsinstellingen ontbreken | Zorg ervoor dat je de nieuwste Aspose.Words‑versie gebruikt; deze bevat de benodigde renderingsbibliotheken. |
| Gegevenswaarden worden onjuist afgerond | Gebruik van gehele getallen met grote waarden | Geef `double`‑waarden op of schaal de getallen voordat je ze aan de series toevoegt. |
| Uitvoer‑PDF is enorm | Afbeeldingen ingebed met hoge DPI | Stel `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)` in als je ook afbeeldingen embedt. |
| “convert word to pdf” geeft `UnsupportedOperationException` | Gebruik van een oudere Java‑versie (< 11) | Upgrade naar Java 17 of hoger, wat vereist is voor Aspose.Words 24.x. |

## Pro‑tip: Hergebruik de diagram‑creatie‑logica

Als je meerdere diagrammen aan hetzelfde document wilt toevoegen, haal dan de diagram‑bouwcode uit in een hulpfunctie:

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

Nu kun je `doc.getFirstSection().getBody().appendChild(createPieChart(...));` aanroepen voor elke dataset, waardoor je code DRY (Don’t Repeat Yourself) blijft.

## Conclusie

Je weet nu hoe je een **create pie chart** binnen een Word‑document kunt maken, deze kunt vullen met gegevens, en **save docx as PDF** kunt uitvoeren met Java. Dit end‑to‑end‑voorbeeld behandelt de volledige **convert word to pdf**‑workflow, beantwoordt **how to add chart**, en demonstreert **how to create chart** programmatisch.

Vanaf hier kun je het volgende verkennen:

* Het toevoegen van staaf‑ of lijndiagrammen (`ChartType.BAR`, `ChartType.LINE`) – een ander **how to create chart**‑scenario.  
* Exporteren naar andere formaten zoals PNG of HTML (`SaveFormat.PNG`, `SaveFormat.HTML`).  
* Dynamisch het invoerdocument genereren met tabellen of placeholders voordat je diagrammen invoegt.

Voel je vrij om te experimenteren met verschillende datasets, stijlopties, of zelfs het embedden van meerdere diagrammen per pagina. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe een pie chart in een Word‑document in te voegen met Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [Hoe Word op te slaan als PDF en een toegankelijke PDF te maken in Java](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [Hoe een diagram in Word te maken met Java en Aspose.Words](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}