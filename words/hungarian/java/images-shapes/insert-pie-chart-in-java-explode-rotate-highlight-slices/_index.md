---
category: general
date: 2026-07-20
description: Kördiagram beszúrása Java-ban lépésről‑lépésre útmutatóval. Tanulja meg,
  hogyan lehet szétrepeszteni egy szeletet, hogyan lehet elforgatni a kördiagramot,
  kiemelni egy szeletet és testreszabni a kördiagram szeletét.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: hu
lastmod: 2026-07-20
og_description: Illessze be a kördiagramot Java-ban, és sajátítsa el, hogyan lehet
  kibontani egy szeletet, hogyan lehet elforgatni a kördiagramot, kiemelni a kördiagram
  szeletét, és testre szabni a kördiagram szeletét a kifinomult vizuális jelentésekhez.
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: Kördiagram beillesztése Java-ban – Szétszórás, Forgatás és Kiemelés
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: Kördiagram beszúrása Java-ban – szeletek szétrobbanása, forgatása és kiemelése
url: /hu/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kördiagram beszúrása Java-ban – szelet kiemelése, forgatása és kiemelése

Valaha is szükséged volt **kördiagram beszúrására** egy Java jelentésbe, de nem tudtad, hogyan lehet egyetlen szeletet kiemelni? Nem vagy egyedül. Legyen szó irányítópult építéséről, számla generálásáról vagy egyszerűen csak felmérési eredmények megjelenítéséről, egy jól megformázott kördiagram a nyers számokat azonnal érthető betekintéssé alakíthatja.

Ebben az útmutatóban egy teljes, azonnal futtatható példát láthatsz, amely megmutatja, hogyan kell **kördiagramot beszúrni**, **hogyan kell szeletet kiemelni**, **hogyan kell kördiagramot forgatni**, és még **hogyan kell kördiagram szeletet kiemelni** egyedi színekkel. A végére egy újrahasználható kódrészletet kapsz, amelyet bármely Java projektbe beilleszthetsz, amely a népszerű *JFreeChart* könyvtárat (vagy bármely hasonló API-t) használ.

## Előfeltételek

- Java 17 vagy újabb (a kód régebbi verziókkal is lefordítható, de a tömörség kedvéért a modern `var` szintaxist használjuk).  
- Maven vagy Gradle a `org.jfree:jfreechart` függőség beillesztéséhez.  
- Alapvető Java osztályok és a diagramépítő koncepciójának ismerete.  

Ha még soha nem adtál hozzá könyvtárat egy Maven projekthez, egyszerűen illeszd be ezt a `pom.xml`-be:

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

Ennyi—nincs szükség további beállításra.

## 1. lépés: Kördiagram beszúrása – A Builder és a Chart objektum létrehozása

Először is szükségünk van egy *builderre* (gondolj rá, mint egy gyárra), amely tudja, hogyan kell diagramokat előállítani. A JFreeChart-ben a `ChartFactory` végzi a nehéz munkát.

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

Miért kezdünk az adatkészlettel? Mert maga a diagram csak egy vizuális burkolat a számok körül. Itt **kördiagramot beszúrva** már rendelkezünk egy 400 × 300-as vászonnal (a méret később kerül alkalmazásra, amikor képként rendereljük).

## 2. lépés: Hogyan kell szeletet kiemelni – Az első szegmens hangsúlyozása

Most, hogy a diagram létezik, tegyük kiemelkedővé az első szeletet. Egy szelet kiemelése azt jelenti, hogy azt kissé eltoljuk a kör középpontjától, így a szem könnyebben ráirányul.

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

Figyeld meg, hogy a **hogyan kell szeletet kiemelni** kifejezést használjuk a metódus nevében; ez kristálytisztán jelzi a szándékot. A `setExplodePercent` metódus egy kulcsot (a szelet címkéjét) és egy százalékot vár, így a „kijön” távolságot igény szerint állíthatod.

## 3. lépés: Hogyan kell kördiagramot forgatni – Kiinduló szög módosítása

Az alapértelmezett kördiagram a 12 óra pozícióból indul. Néha szeretnéd, ha az első szelet máshol kezdődne – talán egy tervezési makettnek megfelelően vagy egy másik diagrammal összhangban.

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

A `rotateChart(chart, 45)` hívás az egész kört elforgatja, így az „Apples” szelet 45 fokos szögnél kezdődik, pontosan ahogy a **hogyan kell kördiagramot forgatni** követelmény megkívánja.

## 4. lépés: Kördiagram szelet kiemelése – Egyedi színek és címkék

A kiemelés mellett előfordulhat, hogy egy szeletnek egyedi színt vagy félkövér címkét szeretnél adni, hogy valóban **kördiagram szeletet kiemelj**.

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

Itt **testre szabjuk a kördiagram szeletet** a festék és a címkestílus módosításával. Nyugodtan cseréld ki a színt vagy a betűtípust, hogy illeszkedjen a márka palettádhoz.

## 5. lépés: Diagram renderelése képfájlba (opcionális, de hasznos)

A legtöbb valós alkalmazásnak PNG, JPEG vagy akár PDF formátumban kell a diagramot megkapnia. Az alábbi gyors módon írhatod a diagramot egy fájlba.

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

A teljes folyamat futtatása egy 400 × 300-as PNG-t hoz létre, amely valahogy így néz ki:

![Kördiagram példa](image.png){: alt="Kördiagram példa, amely kiemelt és elforgatott szeletet mutat"}

## Teljes működő példa

Összegezve, itt egy `main` metódus, amelyet egyszerűen bemásolhatsz egy új Java osztályba és futtathatsz:

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### Várható kimenet

A program futtatása létrehoz egy **fruit-pie.png** nevű fájlt. Nyisd meg, és a következőket fogod látni:

- Egy 400 × 300-as kördiagram „Fruit Distribution” címmel.  
- Az „Apples” szelet 15 %-kal kiemelve kifelé.  
- Az egész diagram elforgatva, így az „Apples” a 45‑fokos pozícióban kezdődik.  
- A kiemelt

## Mi legyen a következő tanulnivaló?

Az alábbi útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan készíts oszlopdiagramot az Aspose.Words for Java segítségével](/words/english/java/document-conversion-and-export/using-charts/)
- [Szórt diagram beszúrása](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [Területdiagram beszúrása](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}