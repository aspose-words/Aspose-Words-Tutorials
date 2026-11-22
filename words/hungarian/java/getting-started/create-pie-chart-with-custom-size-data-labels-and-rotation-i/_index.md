---
category: general
date: 2026-11-22
description: Készíts kördiagramot Java-ban, és tanuld meg, hogyan állítsd be a diagram
  méretét, adj hozzá adatcímkéket, jelenítsd meg a százalékokat, valamint forgasd
  el az első szeletet a tiszta vizuális hatás érdekében.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: hu
lastmod: 2026-11-22
og_description: Készíts kördiagramot Java-ban, majd állítsd be a diagram méretét,
  jelenítsd meg a százalékokat az adatcímkéken, és forgasd el az első szeletet – mindezt
  egyetlen, futtatható példában.
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: Készíts kördiagramot egyedi mérettel, címkékkel és forgatással Java-ban
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: Kördiagram létrehozása egyedi mérettel, adatcímkékkel és forgatással Java-ban
url: /hu/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Készíts kördiagramot egyedi mérettel, adatcímkékkel és forgatással Java-ban

Ha Java-ban **create pie chart**-t szeretnél készíteni, ez az útmutató végigvezet a teljes folyamaton. Megtanulod, hogyan **set chart size**, engedélyezd a **show percentages pie chart**-ot, adj hozzá **data labels pie chart**-ot, és **rotate pie chart slice**-t, hogy az első szelet 45‑fokos szögben kezdődjön.

A példa a **Aspose.Slides for Java**-t használja, egy széles körben használt könyvtárat PowerPoint fájlok manipulálásához. Ugyanazok a koncepciók más diagramkönyvtárakra is alkalmazhatók; csak cseréld ki az API hívásokat a saját eszköztárad megfelelőinek.

## Előfeltételek

* Java 17 vagy újabb telepítve  
* Maven 3.8+ (vagy Gradle) a függőségek kezeléséhez  
* Alapvető ismeretek a Java szintaxisáról  
* Hozzáférés az Aspose.Slides for Java binárishoz (ingyenes próbaverziót a hivatalos weboldalon szerezhetsz)

Add the dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## Készíts kördiagramot – teljes példa

A következő program egy PowerPoint diát hoz létre, amely egy egyedi méretű kördiagramot, százalékos adatcímkéket és egy elforgatott első szeletet tartalmaz.

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### Miért fontos minden lépés

| Lépés | Cél | Hogyan kapcsolódik a kulcsszavakhoz |
|------|-----|-------------------------------------|
| **Insert chart** | **Create pie chart** – a vizuál megjelenítéséért felelős fő objektum. | Közvetlenül teljesíti a *create pie chart* követelményt. |
| **Set dimensions** | Az `addChart(..., 400, 300)` hívás bemutatja a **set chart size**-t. | A szélességet (400 px) és a magasságot (300 px) szabályozza. |
| **Show percentages** | `setShowPercentage(true)` biztosítja, hogy a diagram **show percentages pie chart**-ot jelenítse meg minden szeletnél. | A felhasználók gyakran a százalékokat részesítik előnyben a nyers értékek helyett. |
| **Add data labels** | A `DataLabelFormat` konfiguráció hozzáadja a **data labels pie chart**-ot a kívánt láthatósággal. | A címkék javítják az olvashatóságot és testreszabhatók. |
| **Rotate slice** | `setFirstSliceAngle(45)` elforgatja a diagramot, így az első szelet 45‑fokos szögben kezdődik, teljesítve a **rotate pie chart slice**-t. | Javítja egy adott szelet vizuális hangsúlyát. |

## Lépésről‑lépésre bontás

### 1. Insert a pie chart and set chart size

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*Az `addChart` metódus létrehozza a diagramot és egyben **set chart size**-t állít 400 × 300 pontban.*  
Ha más méretre van szükséged, módosítsd az utolsó két argumentumot.

### 2. Populate the chart with data

A demó három kategóriát és egy sorozatot ad hozzá. A szükséges esetben cseréld ki a keménykódolt számokat adatbázisból, CSV‑ből vagy felhasználói bemenetből származó adatokra.

### 3. Show percentages on each slice

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*A `setShowPercentage(true)` engedélyezése biztosítja, hogy a diagram **show percentages pie chart** automatikusan kiszámolja minden szelet részesedését az összegből.*

### 4. Add detailed data labels

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

Más címkeopciókat (`setShowValue`, `setShowSeriesName`, stb.) is beállíthatsz, hogy testre szabhasd a **add data labels pie chart** élményt.

### 5. Rotate the first slice

```java
chart.setFirstSliceAngle(45);
```

*A `setFirstSliceAngle(45)` hívása **rotate pie chart slice**, így az első szegmens 45‑fokos szögben kezdődik, kiemelve azt.*

### 6. Save and view the result

A program futtatása létrehozza a `output/PieChartDemo.pptx` fájlt. Nyisd meg PowerPointban vagy bármely kompatibilis megjelenítőben a végleges kördiagram megtekintéséhez:

![Create pie chart example](images/pie_chart_example.png){.align-center alt="Képernyőkép egy létrehozott kördiagramról egyedi mérettel, százalékos címkékkel és egy elforgatott első szelettel"}

A fenti kép bemutatja a **create pie chart** eredményt, megerősítve, hogy a méret, a címkék, a százalékok és a forgatás helyesen alkalmazva vannak.

## Gyakori variációk és szélhelyzetek

| Helyzet | Módosítás |
|---------|-----------|
| **Different chart dimensions** | Módosítsd a szélesség/magasság paramétereket az `addChart`-ben. |
| **Multiple series** | Adj hozzá további `IChartSeries` objektumokat; minden sorozatnak saját címke beállításai lehetnek. |
| **Custom label format** | Használd a `series.getDataLabelFormat().setNumberFormat("0.0%")`-t a tizedesjegyek szabályozásához. |
| **Rotating to another angle** | Adj meg bármilyen egész számot (0‑360) a `setFirstSliceAngle`-nek. |
| **Export as image** | Mentés után hívd a `chart.writeAsSvg(outPath)` vagy `chart.writeAsPng(outPath)` metódust egy raszteres verzióhoz. |

> **Pro tip:** Ha sok diagramot szeretnél egy ciklusban generálni, használd újra ugyanazt a `Presentation` objektumot, és csak cseréld ki a diagram adatokat. Ez csökkenti a memóriahasználatot és felgyorsítja a feldolgozást.

## Következtetés

Most már tudod, hogyan **create pie chart**-t készíts Java-ban, **set chart size**-t állíts be, engedélyezd a **show percentages pie chart**-ot, **add data labels pie chart**-ot, és **rotate pie chart slice**-t a jobb vizuális hangsúly érdekében. A teljes, futtatható példa minden lépést bemutat a inicializálástól a végső PowerPoint fájl mentéséig.

### Mi a következő?

* Fedezz fel más diagramtípusokat (Bar, Line, Area) ugyanazzal a `ChartType` enum-mal.  
* Kombinálj több diagramot egy dián a műszerfalakhoz.  
* Exportáld a diagramokat PNG vagy SVG formátumba webalkalmazásokhoz.  

Nyugodtan kísérletezz színekkel, jelmagyarázatokkal és animációs hatásokkal – az adatvizualizációid csak a képzeleted által korlátozottak. Boldog diagramkészítést!

## Mit érdemes még megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [hogyan illessz be kördiagramot Word-be – adatcímke százalék hozzáadása](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [Hogyan robbants ki kördiagram szeletet Java-ban – Aspose.Words diagram oktató](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Kördiagram beillesztése Java-ban – Robbantás, forgatás és szeletek kiemelése](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}