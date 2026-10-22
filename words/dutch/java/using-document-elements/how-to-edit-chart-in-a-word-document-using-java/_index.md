---
category: general
date: 2026-09-11
description: Hoe een grafiek in een Word‑document te bewerken met Java – leer grafiekinstellingen
  bijwerken, rasterlijnen inschakelen, grafiekopties wijzigen en het bijgewerkte document
  opslaan.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- update chart settings
- save updated document
- change chart options
- enable chart gridlines
language: nl
lastmod: 2026-09-11
og_description: Hoe een grafiek in een Word‑document te bewerken met Java. Volg deze
  gids om grafiekinstellingen bij te werken, rasterlijnen in te schakelen, grafiekopties
  te wijzigen en het bijgewerkte document op te slaan.
og_image_alt: Screenshot of a Word document showing a chart with gridlines enabled
og_title: Hoe bewerk je een grafiek in een Word‑document met Java – volledige gids
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  headline: How to edit chart in a Word document using Java
  type: TechArticle
- description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  name: How to edit chart in a Word document using Java
  steps:
  - name: Expected result
    text: 'When you open `output.docx`:'
  - name: What if the document has no chart?
    text: 'Attempting to cast a non‑chart shape will throw a `ClassCastException`.
      Guard against this by checking the shape type:'
  - name: How to edit a specific chart instead of the first one?
    text: 'Iterate through `shapes` and match a known title or an alternative identifier:'
  - name: Can I disable gridlines again later?
    text: 'Yes, simply set the property to `false`:'
  - name: Does this work with `.doc` (binary) files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. However, some newer chart features (like graduations) are only
      stored in the OOXML format, so you’ll see the effect only when saving as `.docx`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Hoe een grafiek in een Word‑document te bewerken met Java
url: /nl/java/using-document-elements/how-to-edit-chart-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een chart te bewerken in een Word-document met Java

Als je een **chart bewerken** in een Word‑bestand, laat deze gids je de exacte stappen zien. Je leert hoe je chart‑instellingen bijwerkt, chart‑gridlines inschakelt, chart‑opties wijzigt, en uiteindelijk **het bijgewerkte document opslaat** zonder enige opmaak te verliezen.

Werken met charts programmatically voelt vaak als een black‑box operatie, vooral wanneer je visuele details zoals graduaties of gridlines wilt aanpassen. Deze tutorial behandelt alles wat je moet weten, van het laden van het document tot het opslaan van de wijzigingen. Er zijn geen externe tools nodig—alleen de Aspose.Words for Java‑bibliotheek (versie 24.9 of later).

By the end of this article you will be able to:

* Een `.docx`‑bestand laden dat een chart bevat.
* De chart‑shape vinden en de eigenschappen ervan wijzigen.
* Chart‑gridlines (graduaties) inschakelen en andere opties aanpassen.
* **Het bijgewerkte document** opslaan naar een nieuw bestand.

## Vereisten

* Java 17 of later geïnstalleerd op je machine.  
* Maven of Gradle om afhankelijkheden te beheren.  
* Aspose.Words for Java 24.9+ (de versie die `setShowGraduations` introduceerde).  
* Een Word‑document (`input.docx`) dat al minstens één chart bevat.

Als je niet bekend bent met Aspose.Words, beschouw het als een volledig uitgeruste API die je in staat stelt Word‑documenten programmatically te lezen, te wijzigen en te schrijven—vergelijkbaar met hoe je een DOM in een webbrowser zou manipuleren.

## Stap 1: Het project opzetten en de bibliotheek importeren

Maak een nieuw Maven‑project aan of voeg de afhankelijkheid toe aan een bestaand project:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **Pro tip:** Gebruik de nieuwste stabiele release om er zeker van te zijn dat je de `setShowGraduations`‑methode hebt. Oudere versies zullen niet compileren.

## Stap 2: Het Word-document laden dat een chart bevat

De eerste actie in elke **chart bewerken**‑workflow is het laden van het bronbestand. Aspose.Words vertegenwoordigt het volledige document met de `Document`‑klasse.

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // Replace with the actual path to your input file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document into memory
        Document doc = new Document(inputPath);
```

Het `Document`‑object geeft je toegang tot elke node in het bestand, inclusief shapes, tabellen en alinea's.  

## Stap 3: De eerste chart‑shape in het document vinden

Charts worden opgeslagen als `Shape`‑nodes waarvan de renderer een `Chart` is. Om een chart te bewerken moet je eerst die node ophalen.

```java
        // Find all shape nodes (including charts)
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);

        // Assume the first shape is a chart; adjust the index if needed
        Shape chartShape = (Shape) shapes.get(0);

        // Cast the shape renderer to Chart
        Chart chart = (Chart) chartShape.getChart();
```

Als het document meerdere charts bevat, iterate over `shapes` en controleer `chartShape.getChart() != null` voordat je cast. Dit voorkomt `ClassCastException` en zorgt ervoor dat je **chart‑opties wijzigt** alleen op geldige chart‑objecten.

## Stap 4: Chart‑gridlines (graduaties) inschakelen – een nieuwe eigenschap in versie 24.9

De eigenschap `setShowGraduations` schakelt de zichtbaarheid van kleine gridlines op de waardenas in of uit. Het inschakelen ervan verbetert vaak de leesbaarheid bij dichte datasets.

```java
        // Turn on gridlines (graduations) for the value axis
        chart.setShowGraduations(true);
```

> **Waarom dit belangrijk is:** Gridlines geven kijkers een visuele referentie voor elk datapunt, waardoor trends makkelijker te herkennen zijn. De standaardwaarde is `false`, dus je moet ze expliciet inschakelen wanneer nodig.

Je kunt ook andere aspecten aanpassen, zoals de hoofd‑gridlines, as‑titels, of de plaatsing van de legenda. Hieronder staat een voorbeeld van het wijzigen van de chart‑titel en de positie van de legenda—beide onderdeel van **chart‑opties wijzigen**.

```java
        // Change the chart title
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);

        // Move the legend to the bottom
        chart.getLegend().setPosition(LegendPosition.BOTTOM);
```

## Stap 5: Het document opslaan met de bijgewerkte chart‑instellingen

Na het aanpassen van de chart, sla je de wijzigingen op. Deze stap voltooit de **bijgewerkte document opslaan** fase.

```java
        // Replace with the desired output path
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // Save the modified document
        doc.save(outputPath);
        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

Het uitvoeren van het programma zal `output.docx` genereren waarin de chart nu gridlines, een nieuwe titel en een verplaatste legenda weergeeft. Open het bestand in Microsoft Word om de visuele wijzigingen te verifiëren.

## Volledige broncode (uitvoerbaar)

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document that contains a chart
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Locate the first chart shape in the document
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
        Shape chartShape = (Shape) shapes.get(0);
        Chart chart = (Chart) chartShape.getChart();

        // 3️⃣ Enable chart gridlines (graduations)
        chart.setShowGraduations(true);

        // 4️⃣ Change chart options (title and legend)
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);
        chart.getLegend().setPosition(LegendPosition.BOTTOM);

        // 5️⃣ Save the document with the updated chart settings
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

### Verwacht resultaat

Wanneer je `output.docx` opent:

* De chart toont kleine gridlines op de waardenas.  
* De titel luidt **“Sales Overview 2026”**.  
* De legenda verschijnt onderaan de chart.

Als de oorspronkelijke chart al gridlines had, blijft het visuele uiterlijk ongewijzigd, wat bevestigt dat de code **idempotent** is.

## Veelgestelde vragen en edge‑case handling

### Wat als het document geen chart bevat?

Proberen een non‑chart shape te casten zal een `ClassCastException` veroorzaken. Bescherm hiertegen door het shape‑type te controleren:

```java
if (chartShape.getShapeType() == ShapeType.CHART) {
    Chart chart = (Chart) chartShape.getChart();
    // proceed with modifications
}
```

### Hoe bewerk je een specifieke chart in plaats van de eerste?

Itereer door `shapes` en match een bekende titel of een alternatieve identifier:

```java
for (Node node : shapes) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart c = (Chart) shape.getChart();
        if ("Revenue Q1".equals(c.getTitle().getText())) {
            // modify this chart
        }
    }
}
```

### Kan ik gridlines later weer uitschakelen?

Ja, stel simpelweg de eigenschap in op `false`:

```java
chart.setShowGraduations(false);
```

### Werkt dit met `.doc` (binaire) bestanden?

Aspose.Words abstraheert het bestandsformaat, dus dezelfde code werkt voor `.doc` en `.docx`. Sommige nieuwere chart‑functies (zoals graduaties) worden echter alleen opgeslagen in het OOXML‑formaat, dus je ziet het effect alleen bij het opslaan als `.docx`.

## Tips voor productie‑klare code

* **Validate input paths** – gebruik `Files.exists(Paths.get(inputPath))` vóór het laden.  
* **Wrap API calls** in try‑catch‑blokken om `Exception`‑details zichtbaar te maken, vooral bij corrupte documenten.  
* **Dispose resources** – hoewel Aspose.Words het geheugen beheert, kan het aanroepen van `doc.close()` (of het gebruik van try‑with‑resources indien beschikbaar) native handles eerder vrijgeven.  
* **Version check** – zorg ervoor dat de runtime‑bibliotheekversie ≥ 24.9 is vóór het aanroepen van `setShowGraduations`. Je kunt `License.getVersion()` opvragen als je een programmatic guard nodig hebt.

## Conclusie

Je weet nu **hoe je een chart** kunt bewerken in een Word‑document met Java. Het proces—het document laden, de chart vinden, chart‑gridlines inschakelen, chart‑opties wijzigen, en **het bijgewerkte document opslaan**—dekt de meest voorkomende scenario's voor programmatic chart‑manipulatie.  

Vanaf hier kun je extra aanpassingen verkennen, zoals het wijzigen van kleuren van dataseries, het toepassen van chart‑stijlen, of het exporteren van de chart als afbeelding. Elk van deze taken volgt hetzelfde patroon: haal de `Chart`‑instantie op, pas de eigenschappen aan, en **sla het bijgewerkte document op**.

Veel plezier met coderen, en voel je vrij om met andere chart‑instellingen te experimenteren om aan je rapportagebehoeften te voldoen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe een kolomgrafiek maken met Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hoe een document opslaan als pdf met Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Standaardopties instellen voor gegevenslabels in een chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}