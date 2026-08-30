---
category: general
date: 2026-07-20
description: hur man infogar ett cirkeldiagram i Word med Aspose.Words. Lär dig att
  lägga till datapunktetikettprocent och visa procentandelar i diagrammet för professionella
  dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: sv
lastmod: 2026-07-20
og_description: hur du infogar ett cirkeldiagram i Word med Aspose.Words. Den här
  guiden visar hur du lägger till procent för datamärkning och visar procentsatser
  i diagrammet med bara några rader.
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: hur man infogar ett cirkeldiagram i Word – snabbguide
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: hur man infogar ett cirkeldiagram i Word – lägg till datamärkesprocent
url: /sv/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hur man infogar cirkeldiagram i Word – lägg till dataetikettprocent

Har du någonsin undrat **hur man infogar cirkeldiagram** i ett Word-dokument utan att kämpa med användargränssnittet? Du är inte ensam. I många rapporteringsscenarier behöver du *lägga till cirkeldiagram i Word* och, ännu viktigare, **visa procent på cirkeldiagram** så att läsarna omedelbart förstår datafördelningen.

I den här handledningen går vi igenom hela processen med Aspose.Words för Java. I slutet kommer du att veta exakt hur man **lägger till dataetikettprocent**, **visar procentandelar på diagrammet**, och får ett polerat cirkeldiagram som ser rätt ut redan första gången. Inga extra tillägg, inga manuella justeringar – bara ren kod som du kan släppa in i vilket projekt som helst.

---

## Förutsättningar

- Java 17 (eller senare) – den nuvarande LTS‑versionen som Aspose.Words stödjer.
- Aspose.Words för Java 24.x (den senaste vid skrivande, juli 2026).
- En grundläggande Maven‑ eller Gradle‑konfiguration för att hämta biblioteket.
- En IDE du föredrar (IntelliJ IDEA, Eclipse, VS Code… vilken som helst fungerar).

Om du redan har detta, bra—låt oss dyka ner.

---

## Steg 1: Ställ in projektet och importera biblioteket

Först, lägg till Aspose.Words‑beroendet i din `pom.xml` (Maven) eller `build.gradle` (Gradle). Detta ger dig åtkomst till `Document`, `DocumentBuilder` och diagramklasserna.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Proffstips:** Håll versionsnumret uppdaterat; nyare versioner lägger ofta till diagramrelaterade korrigeringar som gör **visning av procentandelar på diagram** mer pålitlig.

---

## Steg 2: Skapa ett nytt Word‑dokument och en builder

Buildern är ditt schweiziska armékniv för att infoga innehåll. Här skapar vi ett nytt dokument och fäster en `DocumentBuilder` till det.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Varför behöver vi en builder? Den abstraherar de lågnivå‑OpenXML‑strukturerna, så att vi kan fokusera på *vad* vi vill—som **lägga till cirkeldiagram i word**—istället för *hur* XML‑en ser ut.

---

## Steg 3: Infoga cirkeldiagrammet

Nu kommer kärnan i **hur man infogar cirkeldiagram**. Vi ber buildern att placera ett cirkeldiagram i en specifik storlek. Dimensionerna är i punkter (1 pt ≈ 1/72 tum).

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

Vid detta tillfälle är diagrammet tomt, men platshållaren finns redan i dokumentet. Du har precis **lagt till cirkeldiagram i word** programatiskt.

---

## Steg 4: Fyll diagrammet med data

Ett cirkeldiagram behöver minst en serie med värden. Låt oss mata det med några exempeldata som representerar marknadsandelar.

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

Om du någonsin behöver flera serier (staplade pajer, munkdiagram osv.) kan du anropa `pieChart.getSeries().add()` och upprepa stegen. Samma logik gäller när du vill **visa procentandelar på diagram** för varje segment.

---

## Steg 5: **lägga till dataetikettprocent** – visa procentandelarna på segmenten

Detta är den del som de flesta utvecklare glömmer: att konfigurera dataetiketterna så att de visar procentandelar. Utan detta visar diagrammet bara råa siffror, vilket kan vara tvetydigt.

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

`setShowPercent(true)`‑anropet instruerar Aspose.Words att rendera etiketten som “30 %”, “45 %” osv. Det är exakt så du **visar procent på cirkeldiagram** utan extra formateringsarbete.

---

## Steg 6: Spara dokumentet

Slutligen skriver du dokumentet till disk. Du kan välja `.docx`, `.pdf` eller till och med `.html`. För den här guiden håller vi oss till det moderna `.docx`‑formatet.

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

Kör programmet, öppna `PieChartDemo.docx`, och du kommer att se ett snyggt renderat cirkeldiagram med procentetiketter på varje segment.

---

## Förväntat resultat

Nedan är en skärmdump av den genererade Word‑filen. Lägg märke till hur varje segment visar sin andel som en procentandel—precis vad vi ville ha när vi satte **lägga till dataetikettprocent**.

![Skärmdump av ett Word-dokument som innehåller ett cirkeldiagram med procentetiketter](/images/pie-chart-percent.png){.center width=600px alt="Skärmdump som visar hur man infogar cirkeldiagram i Word med procentetiketter"}

*Alt‑texten innehåller huvudnyckelordet, vilket uppfyller både SEO och tillgänglighet.*

---

## Vanliga frågor & hantering av kantfall

| Question | Answer |
|----------|--------|
| **Kan jag ändra teckensnittet för procentetiketterna?** | Ja. Efter att ha aktiverat `setShowPercent(true)`, hämta `DataLabel`‑objektet och justera dess `Font`‑egenskap (`dataLabel.getFont().setSize(10);`). |
| **Vad händer om jag behöver ett munkdiagram istället för ett cirkeldiagram?** | Byt ut `ChartType.PIE` mot `ChartType.DOUGHNUT` i `insertChart`‑anropet. Samma **lägga till dataetikettprocent**‑logik fungerar. |
| **Visar äldre Word‑versioner (2007‑2010) procentandelarna korrekt?** | Aspose.Words skriver den underliggande XML‑en på ett versionsoberoende sätt, så procentandelarna visas i alla Word‑versioner som stödjer diagram (2007+). |
| **Hur lägger man till en titel på diagrammet?** | Använd `pieChart.getTitle().setText("Market Share");` innan du sparar. |
| **Kan jag infoga diagrammet i ett specifikt stycke eller en tabellcell?** | Absolut. Flytta `DocumentBuilder` till önskad plats (`builder.moveToParagraph(index, true);` eller `builder.moveToCell(table, row, column, true);`) innan du anropar `insertChart`. |

---

## Tips och tricks från fältet

- **Proffstips:** Om du planerar att generera många diagram i en loop, återanvänd en enda `DocumentBuilder`‑instans; det minskar minnesanvändning.
- **Se upp för:** Mycket små segment (< 2 %). Aspose.Words kan utelämna etiketten för att undvika rörighet; du kan tvinga den med `dataLabel.setShowLabel(true);`.
- **Prestanda‑notering:** Diagramrendering är CPU‑intensiv. Vid massrapportgenerering, överväg multitrådning men se till att varje tråd arbetar på sin egen `Document`‑instans.
- **Versionskontroll:** Metoden `setShowPercent` introducerades i Aspose.Words 22.8. Om du använder en äldre version, uppgradera eller beräkna procentandelarna manuellt och sätt dem som anpassade etiketter.

---

## Sammanfattning

Vi har gått igenom **hur man infogar cirkeldiagram** i ett Word‑dokument med Aspose.Words, visat hur man **lägger till dataetikettprocent**, och demonstrerat det enklaste sättet att **visa procentandelar på diagram**. Med bara några rader Java kan du **lägga till cirkeldiagram i word** och **visa procent på cirkeldiagram**, vilket omvandlar råa siffror till omedelbart läsbara visualiseringar.

---

## Vad blir nästa steg?

- Experimentera med andra diagramtyper (`BAR`, `LINE`, `AREA`) och se hur samma **lägga till dataetikettprocent**‑logik tillämpas.
- Kombinera diagram med tabeller för rikare rapporter—Aspose.Words gör det enkelt att placera ett diagram bredvid en datatabell.
- Utforska att exportera samma dokument till PDF eller HTML för att se hur procentandelarna renderas i olika format.

Känn dig fri att justera dimensioner, färger eller datakälla (t.ex. en databasfråga) och se dina Word‑rapporter bli levande. Om du stöter på problem, lämna en kommentar nedan—lycklig diagramgenerering!

---

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Infoga stapeldiagram i Word med Aspose.Words för .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Infoga områdesdiagram i Word‑dokument \| Aspose.Words för .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Infoga ett bubbeldiagram i Word med Aspose.Words för .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}