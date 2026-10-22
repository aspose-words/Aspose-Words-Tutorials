---
category: general
date: 2026-08-07
description: Hogyan bontsuk szét a kördiagram szeletet Java-ban az Aspose.Words használatával.
  Tanulja meg, hogyan adjon vezetővonalakat a kördiagramhoz, hogyan hozzon létre Word-diagramot,
  és hogyan testreszabja a kördiagram szeleteit.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: hu
lastmod: 2026-08-07
og_description: Hogyan robbantsuk szét a kördiagram szeletét Java-ban az Aspose.Words
  segítségével. Ez az útmutató megmutatja, hogyan adhatunk vezetővonalakat a kördiagramhoz,
  hogyan hozhatunk létre Word-diagramokat, és hogyan testreszabhatjuk a kördiagram
  szeleteit a tiszta vizuális hatás érdekében.
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: Hogyan bontsuk ki a tortaszeletet Java-ban – Aspose.Words útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: Hogyan bontsuk ki a kördiagram szeletét Java-ban – Aspose.Words diagram útmutató
url: /hu/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan robbantsuk szét a kördiagram szeletet Java‑ban – Aspose.Words diagram útmutató

Ha szeretnéd megtudni, **hogyan robbantsuk szét a kördiagram szeletet** egy Word dokumentumban Java‑val, ez a tutorial mindent lefed. Megmutatjuk, **hogyan adhatunk vezetővonalakat a kördiagramokhoz**, **java create word chart** objektumok létrehozását, és **hogyan testreszabhatók a kördiagram szeletek** egy kifinomult eredményért. A útmutató végére egy teljes, futtatható példát kapsz, amelyet bármely Java projektbe beilleszthetsz.

![Hogyan robbantsuk szét a kördiagram szeletet Java‑ban – Aspose.Words diagram](/images/pie-chart-exploded.png)

## Előfeltételek

Mielőtt elkezdenéd, győződj meg róla, hogy rendelkezel:

* Java Development Kit (JDK) 8 vagy újabb verzióval.
* Maven vagy Gradle függőségkezelővel.
* Aspose.Words for Java licenccel (az ingyenes értékelő verzió tanulási célokra megfelelő).
* Alapvető ismeretekkel a Java szintaxisról és az objektum‑orientált koncepciókról.

> **Pro tipp:** Bár az Aspose.Words ingyenes próbaverziót kínál, a licenc megvásárlása eltávolítja a generált dokumentumok értékelő vízjelét.

## Mit fed le ez a tutorial

* Új Word dokumentum létrehozása a semmiből.  
* **Kördiagram** beszúrása a `DocumentBuilder` segítségével.  
* **Kördiagram szelet robbantása** egy adatpont kiemeléséhez.  
* **Vezetővonalak hozzáadása a kördiagramhoz** a tisztább címkézés érdekében.  
* A szeletek megjelenésének testreszabása, például színek és szegélyek.  
* A dokumentum mentése lemezre és az eredmény ellenőrzése.

---

## Hogyan robbantsuk szét a kördiagram szeletet az Aspose.Words segítségével Java‑ban

Az első lépés a diagramobjektum beállítása és a kívánt szelet robbantása. Az Aspose.Words a diagramot a `Shape` osztályon keresztül teszi elérhetővé, és minden szelet egy `ChartPoint`. Az `Explosion` tulajdonság beállításával szabályozhatod, hogy a szelet milyen messzire mozduljon ki a középpontból.

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**Miért működik:**  
A `setExplosion(20)` azt mondja a diagrammotornak, hogy a szeletet 20 ponttal tolja el a diagram középpontjától. Az érték relatív; nagyobb számok drámaibb hatást keltenek. Bármely szeletet robbantani tudsz az index módosításával (`get(1)`, `get(2)`, …).

## Vezetővonalak hozzáadása a kördiagramhoz a tisztább címkékért

A vezetővonalak a szelet címkéjét a szélhez kapcsolják, ami különösen hasznos, ha a szeletek robbantva vannak vagy a diagram sok kis szekciót tartalmaz. A `setLeaderLines(true)` hívás engedélyezi ezt a funkciót az egész sorozatra.

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**Miért van szükség vezetővonalakra:**  
Amikor egy szelet robbant, az alapértelmezett címke átfedhet más elemekkel. A vezetővonalak olvashatóvá teszik a címkét, egy rövid vonalat húzva a szelettől a szövegdobozig.

## Java create Word chart – adat sorozatok beszúrása

Egy diagram adat nélkül nem túl hasznos. Fel kell tölteni a sorozatot kategóriákkal és értékekkel. Az alábbiakban három kategóriát adunk hozzá, amelyek a piaci részesedést képviselik.

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**Magyarázat:**  
A `ChartSeries` tartalmazza mind a kategóriákat (a szelet neveket), mind a numerikus értékeket. A `ShowCategoryName` és a `ShowPercentage` engedélyezése önmagát magyarázó diagramot eredményez, ami jól illik a korábban hozzáadott vezetővonalakhoz.

## A kördiagram szeletek testreszabása a robbantás mellett

A szelet robbantása mellett gyakran szeretnénk színeket, szegélyeket módosítani, vagy akár teljesen elrejteni egy szeletet. Az alábbi kódrészlet három gyakori testreszabást mutat be:

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**Miért testreszabjuk a szeleteket:**  
Az egyedi színek segítenek, hogy a diagram illeszkedjen a vállalati arculathoz, míg a szegélyek javítják a nyomtatott oldalak olvashatóságát. Egy szelet elrejtése akkor hasznos, ha a adatmodellt érintetlenül szeretnéd tartani, de ideiglenesen ki szeretnél hagyni egy kategóriát a vizuális megjelenítésből.

## Dokumentum mentése és az eredmény ellenőrzése

Végül írjuk a dokumentumot a lemezre. A generált `.docx` fájlt megnyithatod a Microsoft Word, a LibreOffice vagy bármely, a formátumot támogató megjelenítő programmal.

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**Várható kimenet:**  
Amikor megnyitod a `PieChartDemo.docx` fájlt, egy kördiagramot látsz, ahol az első szelet (Product A) kifelé robbant, a vezetővonalak minden szeletből a címkéjéhez mutatnak, és a szeletek a testreszabott zöld, kék és narancssárga színekben jelennek meg. A rejtett szelet (Product C) nem lesz látható, de a százalékok továbbra is 100 %-ot adnak össze, mivel az adatok a diagram sorozatában megmaradnak.

---

## Teljes, futtatható példa

Az alábbiakban a teljes programot találod, amelyet másolhatsz, beilleszthetsz és futtathatsz, miután hozzáadtad az Aspose.Words függőséget a projektedhez.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**Függőség (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

## Mit érdemes még megtanulni?

A következő tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan hozzunk létre oszlopdiagramot az Aspose.Words for Java segítségével](/words/english/java/document-conversion-and-export/using-charts/)
- [Hogyan töltsünk be Word dokumentumokat az Aspose.Words Java-val: Átfogó útmutató](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Hogyan hozzunk létre űrlapmezőket és adjunk tartalmat a DocumentBuilderrel az Aspose.Words for Java-ban](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}