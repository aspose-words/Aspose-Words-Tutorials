---
category: general
date: 2026-09-24
description: Helyezzen be kördiagramot egy DOCX-be az Aspose.Words for Java használatával.
  Tanulja meg beállítani a lyuk méretét, szétrobbantani a kördiagram szeletet, kiemelni
  a kördiagram szeletet, és könnyedén létrehozni a DOCX diagramot.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: hu
lastmod: 2026-09-24
og_description: Helyezzen be kördiagramot egy DOCX-be az Aspose.Words for Java segítségével.
  Mesteri módon állítsa be a lyuk méretét, szétrobbanó szeletet, emelje ki a kördiagram
  szeletét, és percek alatt készítsen docx diagramot.
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: Kördiagram beillesztése Java-ban – lépésről lépésre útmutató
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
title: Pie chart szó beszúrása Java-ban – teljes útmutató
url: /hu/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kördiagram szó beszúrása Java-ban – teljes útmutató

If you need to **insert pie chart word** in a DOCX file, this tutorial shows you exactly how to do it with Aspose.Words for Java. You’ll see the full workflow from creating the document to customizing the chart so that the slice is exploded, the hole size is set to zero, and the slice is highlighted.

Working with charts in Word documents often feels like a separate concern from regular text processing, but Aspose.Words unifies both. In the steps below you’ll also learn how to **create docx chart** files that are ready to be opened in Microsoft Word, Google Docs, or any other DOCX‑compatible viewer.

## Amit el fogsz érni

* **Insert pie chart word** egy üres dokumentumba  
* **Set hole size** a diagram teljes körre (donut nélkül) alakításához  
* **Explode pie slice** egy adott szegmens kiemeléséhez  
* **Highlight pie chart slice** egyedi formázással  
* **Create docx chart**, amely megosztható vagy tovább szerkeszthető  

### Előfeltételek

* Java 17 vagy újabb (a kód Java 8‑kal is lefordítható)  
* Aspose.Words for Java könyvtár (23.9 vagy újabb verzió)  
* IDE vagy build eszköz (Maven/Gradle), amely fel tudja oldani az Aspose.Words függőséget  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## Hogyan szúrjunk be pie chart word-t egy DOCX-be az Aspose.Words segítségével

The first step is to create a new blank document and obtain a `DocumentBuilder`. The builder gives you direct access to the document’s content stream, making it trivial to **insert pie chart word**.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### Miért fontos ez

`Document` a teljes Word fájlt képviseli, míg a `DocumentBuilder` egy magas szintű API, amely lehetővé teszi bekezdések, táblázatok és diagramok beszúrását anélkül, hogy alacsony szintű XML‑kel kellene foglalkozni. Egy tiszta dokumentummal kezdve biztosítod, hogy a hozzáadott diagram az egyetlen tartalom legyen, ami tökéletes a tanuláshoz vagy sablon‑alapú jelentések generálásához.

## Lyukméret beállítása a teljes kör létrehozásához

By default, Aspose.Words creates a doughnut chart when you request a pie chart. To make the chart a true circle, you must **set hole size** to `0`. This removes the inner hole and yields a classic pie appearance.

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### Praktikus tipp

If you later decide to switch to a doughnut chart, simply change the `holeSize` value to a percentage (e.g., `30`). The same API works for both chart types.

## Szelet robbantása a szegmens kiemeléséhez

Exploding a slice makes it stand out visually. The **explode pie slice** operation moves the chosen slice outward by a percentage of the chart radius.

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### Miért robbantás?

An exploded slice draws the reader’s eye to the most important data point—perfect for dashboards or executive summaries. The value `20` means 20 % of the radius; you can adjust it between `0` (no explosion) and `100` (fully detached).

## Kördiagram szelet kiemelése egyedi formázással

Beyond exploding, you might want to **highlight pie chart slice** by changing its fill color or border. While the demo code focuses on explosion, you can extend it as follows:

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### Szakértői megjegyzés

Changing the fill color of a specific slice requires accessing the `DataPoint` object. If you have multiple series, iterate through `series.getDataPoints()` and apply styles conditionally.

## A létrehozott docx diagram mentése és ellenőrzése

Finally, you **create docx chart** by saving the `Document`. The resulting file can be opened in Microsoft Word to see the formatted pie chart.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### Várt kimenet
Opening `PieChartFormatted.docx` shows a single pie chart:

* The chart occupies a 400 × 300 pt area.  
* The hole size is `0`, so the chart is a full pie.  
* The first slice is exploded by 20 % and colored red (if you added the optional formatting).  

You now have a **create docx chart** that can be distributed, embedded in emails, or further edited programmatically.

---

## Gyakori változatok és szélhelyzetek

| Forgatókönyv | Hogyan kell módosítani a kódot |
|----------|----------------------|
| **Multiple series** | `pieChart.getChart().getSeries()` ciklusával iterálj, és állítsd be a `Explosion` vagy `FillColor` értéket sorozatonként. |
| **Dynamic data** | Töltsd fel a sorozatot adatbázisból vagy CSV‑ből származó értékekkel, mielőtt meghívod a `setExplosion`‑t. |
| **Different chart size** | Módosítsd a szélesség/magasság argumentumokat az `insertChart(ChartType.PIE, width, height)`‑ben. |
| **Export to PDF** | A DOCX mentése után hívd meg a `doc.save("output.pdf")`‑t, hogy PDF‑verziót készíts ugyanarról a diagramról. |
| **Localization** | Használd a `DocumentBuilder.insertChart`‑t helyspecifikus számformátummal a címkékhez. |

### Pro tipp
Mindig hívd meg a `setHoleSize(0)` **az** `insertChart` **után**. Ha a beszúrás előtt állítod be, az Aspose.Words visszaáll az alapértelmezett donut méretre, miután a diagram létrejön.

---

## Összefoglalás

You now know how to **insert pie chart word** into a Word document using Java, how to **set hole size** for a full‑pie look, how to **explode pie slice** to draw attention, and how to **highlight pie chart slice** with custom colors. The complete example also demonstrates how to **create docx chart** files that are ready for distribution.

---

## Következő lépések

* Fedezd fel a többi diagramtípust (`BAR`, `LINE`, `SCATTER`) a `ChartType`‑al.  
* Kombináld a diagramgenerálást a levélösszefűzéssel személyre szabott jelentések készítéséhez.  
* Integráld a generált DOCX‑et egy webszolgáltatásba, amely kérésre visszaadja a fájlt.  

If you run into issues, remember to verify that you’re using a compatible version of Aspose.Words and that the output directory exists and is writable.

Boldog kódolást!

## Mit kellene legközelebb megtanulnod?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Hogyan hozzunk létre oszlopdiagramot az Aspose.Words for Java használatával](/words/english/java/document-conversion-and-export/using-charts/)
- [Word Chart API használata](/words/english/net/programming-with-charts/)
- [Buborékdiagram beszúrása Word-be az Aspose.Words for .NET használatával](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}