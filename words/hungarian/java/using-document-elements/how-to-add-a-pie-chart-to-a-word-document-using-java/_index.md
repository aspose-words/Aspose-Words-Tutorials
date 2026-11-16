---
category: general
date: 2026-11-15
description: Tanulja meg, hogyan adhat hozzá kördiagramot egy Word-dokumentumhoz az
  Aspose.Words for Java segítségével. Tartalmazza a gyűrűdiagram átalakítást, a szétrepedt
  szeletet és a teljes kódmintát.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: hu
lastmod: 2026-11-15
og_description: Adjon hozzá egy kördiagramot egy Word-dokumentumhoz az Aspose.Words
  for Java használatával. Ez az útmutató bemutatja, hogyan lehet egy szeletet szétválasztani
  és a diagramot gyűrűdiagrammá alakítani.
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: Kördiagram hozzáadása egy Word-dokumentumhoz Java-val – lépésről‑lépésre
  útmutató
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Hogyan lehet kördiagramot hozzáadni egy Word-dokumentumhoz Java segítségével
url: /hu/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kördiagram (pie chart) hozzáadása Word dokumentumhoz – teljes Java útmutató

Ha **programozottan szeretnél kördiagramot hozzáadni egy Word dokumentumhoz**, ez a tutorial pontosan megmutatja, hogyan teheted meg az Aspose.Words for Java segítségével. Láthatod a teljes munkafolyamatot: DOCX betöltése, kördiagram létrehozása, az első szelet „kibontása”, és a diagram torta‑formából fánk‑formává alakítása a lyukméret beállításával.

Az útmutató a gyakori variációkat is bemutatja – például több sorozat hozzáadását, színek testreszabását, valamint a már diagramot tartalmazó dokumentumok kezelését – így a kódot könnyen alkalmazhatod valós projektekben, mint az automatizált jelentéskészítés vagy dinamikus prezentációk.

## Előfeltételek

Mielőtt elkezdenéd, győződj meg róla, hogy a következőkkel rendelkezel:

* Java 17 vagy újabb (a kód JDK 11+‑tel is lefordítható)
* Maven 3.6+ vagy Gradle a függőségkezeléshez
* Aspose.Words for Java licenc (a ingyenes próbaverzió teszteléshez elegendő)
* Alapvető Java szintaxis és Maven projektstruktúra ismerete

## 1. lépés: Maven projekt beállítása és az Aspose.Words importálása

Hozz létre egy új Maven projektet (vagy adj hozzá egy meglévőhöz) és add hozzá az Aspose.Words függőséget:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tipp:** Ha Gradlet használsz, az ekvivalens bejegyzés: `implementation 'com.aspose:aspose-words:24.9'`.

A függőség tartalmazza a `Document`, `Chart` és `ChartType` osztályokat, amelyekre a diagramok manipulálásához szükséged lesz.

## 2. lépés: A cél dokumentum betöltése

Kezdhetsz egy meglévő `.docx` fájlból, vagy létrehozhatsz egy új üres dokumentumot. Az alábbi példa egy `input.docx` nevű sablont tölt be, amely a `src/main/resources` mappában található.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

Ha a fájl nem létezik, az Aspose.Words automatikusan egy új üres dokumentumot hoz létre, amikor a `new Document()`‑t fájlnév nélkül hívod.

## 3. lépés: Kördiagram létrehozása és beszúrása a dokumentumba

Az Aspose.Words a diagramot alakzatként kezeli, amely bárhol elhelyezhető, ahol bekezdés megjelenhet. Az alábbi kód **kördiagramot** hoz létre, egyetlen adat sorozatot ad hozzá, és a diagramot az első bekezdés után szúrja be.

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**Miért fontos ez a lépés:**  
* `ChartType.PIE` azt mondja az Aspose.Words‑nek, hogy hagyományos kördiagramot rendereljen.  
* Egy sorozat hozzáadása, amely tartalmazza a kategória címkéket és a numerikus értékeket, automatikusan feltölti a szeleteket.  
* A diagram `Paragraph` gyermekeként való beszúrása megőrzi a dokumentum folyamatosságát.

## 4. lépés: Az első szelet „kibontása” a kiemeléshez

Egy *kibontott szelet* felhívja a figyelmet egy adott adatpontra. Az API a `ChartSeries` objektumon keresztül biztosítja a `setExplode(boolean)` metódust. Az első sorozaton (index 0) való beállításával az első szelet kiugrik.

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **Gyakori kérdés:** *Mi van, ha több sorozatom van?*  
> Egy adott sorozatot az indexe alapján célozhatsz meg, például `pieChart.getSeries().get(1).setExplode(true)` a második sorozathoz.

## 5. lépés: A kördiagram fánkká alakítása a lyukméret beállításával

A fánkdiagram lényegében egy lyukas középpontú kördiagram. Az Aspose.Words lehetővé teszi a lyukméret százalékos megadását a diagram sugárához képest.

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

A `setHoleSize` metódus **0** (normál kör) és **100** (teljesen üres) közötti értékeket fogad el. A **30‑40** körüli érték vizuálisan kiegyensúlyozott fánkot eredményez.

## 6. lépés: Mentés és az eredmény ellenőrzése

Az összes módosítás után mentsd el a dokumentumot. Az alábbi sor a fájlt az `output` mappába írja.

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### Várt kimenet

Nyisd meg a `final-pie-doughnut.docx` fájlt a Microsoft Word‑ben:

* Egy fánkdiagram jelenik meg ott, ahol az első bekezdés állt.  
* Az „Alma” szelet kibontva (könnyen elkülönül a többitől).  
* A diagram négy szeletet mutat, feliratozva *Alma*, *Banán*, *Cseresznye*, *Datolya* címkékkel és a megadott százalékokkal.

Ha PDF kimenetet szeretnél, változtasd meg a `SaveFormat`‑ot `SaveFormat.PDF`‑ra.

## Szélső esetek és variációk kezelése

### Több sorozat hozzáadása

Ha több sorozatra van szükséged (például rétegezett fánk), add hozzá őket egymás után:

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### Egyedi színek

Minden szelethez színt rendelhetsz a `ChartDataPoint.setFillFormat().setSolidFillColor()` segítségével:

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### Létező diagram módosítása

Ha a dokumentum már tartalmaz diagramot, és csak azt szeretnéd módosítani, keresd meg a diagram alakzatát:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### Licenckezelés

Az Aspose.Words licencet igényel a termelésben való használathoz. Helyezd a `Aspose.Words.lic` fájlt a classpath‑ba, és töltsd be az alkalmazás indításakor:

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

A licenc hiánya vízjelet helyez a generált dokumentumra.

## Teljes, futtatható példa

Az alábbiakban a teljes Java osztály látható, amely az összes korábban tárgyalt lépést tartalmazza. Másold be a `src/main/java/com/example/AddPieChart.java` fájlba, majd futtasd a `mvn compile exec:java` parancsot.

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

A program futtatása a leírt fánkdiagramot hozza létre. Igazítsd a `categories`, `values` vagy `holeSize` értékeket az adataidhoz.

## Összegzés

Most már tudod, hogyan **adj hozzá kördiagramot egy Word dokumentumhoz** Java és Aspose.Words segítségével. A tutorial bemutatta a dokumentum betöltését, kördiagram létrehozását, egy szelet kibontását, a diagram fánkká alakítását, valamint a gyakori variációk kezelését, mint a több sorozat, egyedi színek és meglévő diagramok módosítása. Ezzel az alapokkal automatizált jelentéskészítő eszközöket építhetsz, dinamikus prezentációkat generálhatsz, vagy gazdag vizualizációkat ágyazhatsz közvetlenül Word fájlokba.

### Mit érdemes még felfedezni

* **oszlopdiagram hozzáadása Word dokumentumhoz** – hasonló lépések, csak a `ChartType.BAR`‑t használod.  
* **diagram jelmagyarázat és cím testreszabása** – használd a `pieChart.getTitle().setText("...")` és a `pieChart.getLegend().setPosition(LegendPosition.RIGHT)` metódusokat.  
* **Word dokumentum exportálása PDF‑be** – a `SaveFormat`‑ot `PDF`‑re állítva készíthetsz terjeszthető fájlokat.  
* **diagram adatok feltöltése adatbázisból** – cseréld le a statikus tömböket JDBC lekérdezés eredményeire.

Kísérletezz különböző diagramtípusokkal, adatforrásokkal és stílusbeállításokkal. Boldog kódolást!

## Mit tanulj meg legközelebb?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket és lépésről‑lépésre magyarázatokat tartalmaz, hogy könnyedén elsajátíthasd az API további funkcióit és alternatív megvalósítási módokat saját projektjeidben.

- [Hogyan bonts ki egy kördiagram szeletet Java‑ban – Aspose.Words diagram tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Kördiagram létrehozása Aspose.Words Java‑val – Teljes lépés‑ről‑lépésre útmutató](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}