---
category: general
date: 2026-07-29
description: Voeg een cirkeldiagram in met Aspose.Words voor Java en leer hoe je een
  donutdiagram genereert, een cirkeldiagram formatteert, een diagram in Word formatteert
  en de grootte van het diagram aanpast.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: nl
lastmod: 2026-07-29
og_description: Voeg een cirkeldiagram in met Aspose.Words for Java en leer snel hoe
  je een donutdiagram maakt, een cirkeldiagram opmaakt, een diagram in Word formatteert
  en de diagramgrootte aanpast voor professionele documenten.
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: Cirkeldiagram invoegen in Java – Complete Aspose.Words‑handleiding
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: Cirkeldiagram invoegen in Java met Aspose.Words – Volledige gids
url: /nl/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Taartdiagram invoegen in Java met Aspose.Words – Complete gids

Heb je je ooit afgevraagd hoe je **een taartdiagram** in een Word‑document kunt **invoegen** vanuit Java‑code? Je bent niet de enige—veel ontwikkelaars lopen tegen dit obstakel aan wanneer ze snel en programmatic data willen visualiseren. Het goede nieuws? Met Aspose.Words for Java kun je dit doen in slechts een handvol regels, en terwijl je bezig bent kun je ook **een donut‑diagram genereren**, **taartdiagram opmaken**, **diagram Word opmaken**, en **de grootte van het diagram aanpassen** aan je huisstijl.

In deze tutorial lopen we een real‑world voorbeeld door dat begint met het maken van een leeg document, een taartdiagram toevoegt, een paar visuele eigenschappen aanpast, en uiteindelijk het bestand opslaat. Aan het einde heb je een herbruikbare code‑snippet die je in elk Java‑project kunt plakken dat diagramautomatisering nodig heeft. Geen extra libraries, geen handmatig gedoe met Office‑interop—gewoon nette, gecompileerde Java.

## Wat je nodig hebt

- **Java 17** (of een recente JDK; de API is achterwaarts compatibel)
- **Aspose.Words for Java** 22.12 of nieuwer – je kunt het Maven‑artifact of de .jar van de Aspose‑site halen.
- Een bescheiden IDE (IntelliJ IDEA, Eclipse, VS Code…) – alles wat je een `main`‑methode laat uitvoeren.
- Optioneel: een licentiebestand als je het evaluatiewatermerk niet wilt.

Als je dit hebt, kunnen we direct naar de code springen.

## Stap 1: Taartdiagram invoegen met Aspose.Words

Het eerste wat we doen is **een taartdiagram invoegen** in een nieuw document. Deze stap vormt de basis voor alles wat volgt, omdat het diagramobject ons toegang geeft tot series, datapunten en visuele aanpassingen.

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Waarom dit belangrijk is:** `DocumentBuilder.insertChart` maakt niet alleen het diagram, maar retourneert ook een `Chart`‑object dat we kunnen manipuleren. De breedte‑ en hoogte‑argumenten laten je **de grootte van het diagram aanpassen** direct bij het aanmaken, zodat je later niet meer hoeft te schalen.

## Stap 2: Donut‑diagram genereren (optioneel)

Als je ontwerp een gat in het midden vereist—denk aan een klassiek donut‑diagram—maakt Aspose er een één‑regel oplossing van. Dezelfde `Chart`‑instantie kan van een gewone taart naar een donut worden omgezet door de gatgrootte aan te passen.

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Tip:** De gatgrootte heeft alleen effect voor `ChartType.DONUT`. Als je het type `PIE` behoudt, wordt de aanroep genegeerd, dus experimenteer gerust.

## Stap 3: Taartdiagramsegmenten opmaken

Een goede visual benadrukt vaak een specifiek segment. Hier **vormen we het taartdiagram** door het eerste segment 20 punten naar buiten te “exploderen”. Dit trekt de aandacht van de lezer naar het belangrijkste datapunt.

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Pro‑tip:** Je kunt door `pieChart.getSeries()` loopen als je meerdere series hebt en individuele kleuren, randen of datalabels instellen. Zo **formatteer je diagram Word**‑documenten met rijke styling.

## Stap 4: Gegevens aan het diagram toevoegen

Een diagram zonder gegevens is slechts een decoratieve vorm. Laten we het een eenvoudige dataset geven—bijvoorbeeld kwartaal‑verkoopcijfers.

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Waarom we dit doen:** Door expliciet `ChartPoint`‑objecten toe te voegen, garanderen we dat het diagram onze bedrijfslogica weerspiegelt. De aanroepen `setShowCategoryName` en `setShowValue` maken deel uit van **het opmaken van het taartdiagram** zodat zowel labels als cijfers worden weergegeven.

## Stap 5: Uiterlijk fijn afstellen (grootte & stijl van diagram aanpassen)

Naast de initiële afmetingen wil je misschien de legenda, titel of zelfs het lettertype van de datalabels aanpassen. Al deze zaken vallen onder **grootte van het diagram aanpassen** en algemene opmaak.

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Randgeval:** Als je later besluit het document naar PDF te exporteren, blijft de vector‑data van het diagram scherp omdat de grootte in punten, niet in pixels, is gedefinieerd. Dat is een winst voor **diagram Word opmaken** en downstream‑formaten.

## Stap 6: Document opslaan en bekijken

De laatste stap is zo simpel als `doc.save` aanroepen. Dit schrijft een `.docx`‑bestand dat je kunt openen in Microsoft Word, LibreOffice, of elke viewer die het OpenXML‑formaat ondersteunt.

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Resultaat:** Open `PieChart.docx` en je ziet een netjes geschaald taart‑ (of donut‑)diagram met een geëxplodeerd segment, een titel en een legenda—alles gegenereerd zonder ooit de UI aan te raken.

### Verwachte output

| Element | Wat je zult zien |
|---------|------------------|
| Diagramtype | Taartdiagram (of donut als `holeSize` > 0) |
| Segmentexplosie | Eerste segment verschoven met 20 pt |
| Legenda | Geplaatst aan de rechterkant |
| Titel | “Quarterly Sales Distribution” in vet 14 pt |
| Datalabels | Categorie‑naam en waarde getoond op elk segment |
| Document | Een standaard Word `.docx`‑bestand klaar om te delen |

## Veelgestelde vragen & valkuilen

- **Heb ik een licentie nodig?**  
  De evaluatieversie werkt prima voor testen, maar voegt een watermerk toe. Plaats je `aspose.words.lic`‑bestand in de classpath voor een schone output.

- **Kan ik dit met Maven gebruiken?**  
  Zeker. Voeg de volgende afhankelijkheid toe aan je `pom.xml`:

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **Wat als ik meer dan één serie heb?**  
  Loop over `pieChart.getSeries()` en pas `setExplosion`, `setFillColor` of andere opmaak per serie toe. Zo **formatteer je taartdiagram** voor multidimensionale data.

- **Is het diagram bewerkbaar in Word na generatie?**  
  Ja—eenmaal opgeslagen kun je het document openen en handmatig kleuren, lettertypen aanpassen, of zelfs de taart omzetten naar een staafdiagram als dat nodig is.

## Samenvatting

We hebben net **een taartdiagram ingevoegd** in een Word‑document met Aspose.Words for Java, laten zien hoe je **een donut‑diagram genereert**, meerdere manieren **het taartdiagram opmaakt**, **diagram Word opmaakt** best practices behandeld, en geleerd hoe je **de grootte van het diagram aanpast** voor een gepolijste uitstraling. Het complete, uitvoerbare voorbeeld hierboven kun je in elk Java‑project plaatsen, waardoor je direct diagramautomatisering krijgt zonder de overhead van COM‑interop of Office‑installaties.

Wat nu? Probeer de gegevensbron te vervangen door een live database, voeg conditionele kleuren toe op basis van drempels, of exporteer hetzelfde document naar PDF voor een print‑klare rapportage. Elk van die stappen bouwt voort op de basis die we hebben gelegd, dus de overgang zal soepel verlopen.

Als je tegen problemen aanloopt of ideeën hebt voor verdere verbeteringen—misschien een gestapelde staaf of een lijndiagram—laat dan een reactie achter. Veel plezier met diagrammen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe een kolomdiagram maken met Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Getal opmaken van datalabel in een diagram](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Getalopmaak voor as in een diagram](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}