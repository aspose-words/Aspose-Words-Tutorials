---
category: general
date: 2026-09-24
description: Infoga ett cirkeldiagram i ett DOCX med Aspose.Words för Java. Lär dig
  att ställa in hålstorlek, explodera en cirkelskiva, markera en cirkeldiagramsskiva
  och skapa DOCX-diagram utan ansträngning.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: sv
lastmod: 2026-09-24
og_description: Infoga ett cirkeldiagram i ett DOCX med Aspose.Words för Java. Ställ
  in hålets storlek i master, explodera en diagramdel, markera en diagramdel och skapa
  DOCX-diagram på några minuter.
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: Infoga pajdiagram i Java – steg‑för‑steg‑handledning
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
title: Infoga cirkeldiagramord i Java – komplett guide
url: /sv/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga cirkeldiagram ord i Java – komplett guide

Om du behöver **infoga cirkeldiagram ord** i en DOCX‑fil, visar den här handledningen exakt hur du gör det med Aspose.Words för Java. Du får se hela arbetsflödet från att skapa dokumentet till att anpassa diagrammet så att segmentet exploderas, hålstorleken sätts till noll och segmentet markeras.

Att arbeta med diagram i Word‑dokument känns ofta som en separat sak jämfört med vanlig textbehandling, men Aspose.Words förenar båda. I stegen nedan lär du dig också hur du **skapar docx‑diagram**‑filer som är redo att öppnas i Microsoft Word, Google Docs eller någon annan DOCX‑kompatibel visare.

## Vad du kommer att uppnå

* **Infoga cirkeldiagram ord** i ett tomt dokument  
* **Sätt hålstorlek** för att göra diagrammet till en hel cirkel (ingen donut)  
* **Explodera cirkelsegment** för att rikta uppmärksamhet mot ett specifikt segment  
* **Markera cirkeldiagramsegment** med anpassad formatering  
* **Skapa docx‑diagram** som kan delas eller redigeras vidare  

### Förutsättningar

* Java 17 eller senare (koden kompileras även med Java 8)  
* Aspose.Words för Java‑bibliotek (version 23.9 eller nyare)  
* En IDE eller ett byggverktyg (Maven/Gradle) som kan lösa Aspose.Words‑beroendet  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## Hur du infogar cirkeldiagram ord i ett DOCX med Aspose.Words

Det första steget är att skapa ett nytt tomt dokument och hämta en `DocumentBuilder`. Buildern ger dig direkt åtkomst till dokumentets innehållsström, vilket gör det enkelt att **infoga cirkeldiagram ord**.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### Varför detta är viktigt
`Document` representerar hela Word‑filen, medan `DocumentBuilder` är det hög‑nivå‑API som låter dig infoga stycken, tabeller och diagram utan att behöva hantera låg‑nivå‑XML. Att börja med ett rent dokument säkerställer att diagrammet du lägger till är det enda innehållet, vilket är perfekt för lärande eller för att generera mall‑baserade rapporter.

## Sätt hålstorlek för att skapa en hel cirkel

Som standard skapar Aspose.Words ett donut‑diagram när du begär ett cirkeldiagram. För att göra diagrammet till en sann cirkel måste du **sätta hålstorlek** till `0`. Detta tar bort det inre hålet och ger ett klassiskt cirkeldiagram.

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### Praktisk tip
Om du senare bestämmer dig för att byta till ett donut‑diagram, ändra bara `holeSize`‑värdet till en procentandel (t.ex. `30`). Samma API fungerar för båda diagramtyperna.

## Explodera cirkelsegment för att markera ett segment

Att explodera ett segment får det att sticka ut visuellt. **Explodera cirkelsegment**‑operationen flyttar det valda segmentet utåt med en procentandel av diagramradien.

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### Varför explodera?
Ett exploderat segment drar läsarens blick till den viktigaste datapunkten – perfekt för instrumentpaneler eller ledningssammanfattningar. Värdet `20` betyder 20 % av radien; du kan justera det mellan `0` (ingen explosion) och `100` (fullt fristående).

## Markera cirkeldiagramsegment med anpassad formatering

Utöver att explodera kan du vilja **markera cirkeldiagramsegment** genom att ändra fyllningsfärgen eller kanten. Medan demo‑koden fokuserar på explosion kan du utöka den så här:

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### Expertanteckning
Att ändra fyllningsfärgen för ett specifikt segment kräver åtkomst till `DataPoint`‑objektet. Om du har flera serier, iterera genom `series.getDataPoints()` och applicera stilar villkorligt.

## Spara och verifiera det skapade docx‑diagrammet

Till sist **skapar du docx‑diagram** genom att spara `Document`. Den resulterande filen kan öppnas i Microsoft Word för att se det formaterade cirkeldiagrammet.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### Förväntat resultat
När du öppnar `PieChartFormatted.docx` visas ett enda cirkeldiagram:

* Diagrammet upptar ett område på 400 × 300 pt.  
* Hålstorleken är `0`, så diagrammet är en hel cirkel.  
* Det första segmentet är exploderat med 20 % och färgat rött (om du har lagt till den valfria formateringen).  

Du har nu ett **skapa docx‑diagram** som kan distribueras, bäddas in i e‑post eller redigeras vidare programmässigt.

---

## Vanliga variationer och kantfall

| Scenario | Hur du anpassar koden |
|----------|----------------------|
| **Flera serier** | Loopa över `pieChart.getChart().getSeries()` och sätt `Explosion` eller `FillColor` per serie. |
| **Dynamisk data** | Fyll serierna med värden från en databas eller CSV innan du anropar `setExplosion`. |
| **Olika diagramstorlek** | Ändra bredd‑/höjdarargumenten i `insertChart(ChartType.PIE, width, height)`. |
| **Export till PDF** | Efter att ha sparat DOCX, anropa `doc.save("output.pdf")` för att producera en PDF‑version av samma diagram. |
| **Lokalisering** | Använd `DocumentBuilder.insertChart` med ett lokalanpassat talformat för etiketter. |

### Pro‑tips
Anropa alltid `setHoleSize(0)` **efter** `insertChart`. Om du sätter den innan insättningen återgår Aspose.Words till standard‑donut‑storleken när diagrammet skapas.

---

## Sammanfattning

Du vet nu hur du **infogar cirkeldiagram ord** i ett Word‑dokument med Java, hur du **sätter hålstorlek** för ett hel‑cirkeldiagram, hur du **exploderar cirkelsegment** för att dra uppmärksamhet, och hur du **markerar cirkeldiagramsegment** med anpassade färger. Det kompletta exemplet visar också hur du **skapar docx‑diagram**‑filer som är redo för distribution.

---

## Nästa steg

* Utforska andra diagramtyper (`BAR`, `LINE`, `SCATTER`) med `ChartType`.  
* Kombinera diagramgenerering med mail‑merge för att producera personliga rapporter.  
* Integrera det genererade DOCX‑dokumentet i en webbtjänst som returnerar filen på begäran.  

Om du stöter på problem, kontrollera att du använder en kompatibel version av Aspose.Words och att mål‑katalogen finns och är skrivbar.

Lycka till med kodandet!


## Vad bör du lära dig härnäst?


Följande handledningar täcker närliggande ämnen som bygger vidare på teknikerna i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Using Word Chart API](/words/english/net/programming-with-charts/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}