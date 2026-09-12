---
category: general
date: 2026-09-11
description: Mentse a Word dokumentumot a gyűrűdiagram szerkesztése után az Aspose.Words
  for Java segítségével. Tanulja meg, hogyan változtathatja meg a gyűrűlyuk méretét,
  forgathatja a gyűrűdiagramot, és szerkesztheti a gyűrűdiagram tulajdonságait.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: hu
lastmod: 2026-09-11
og_description: Mentse a Word dokumentumot a fánkdiagram szerkesztése után az Aspose.Words
  for Java használatával. Ez az útmutató bemutatja, hogyan változtatható a fánk lyukmérete,
  hogyan forgatható el a fánkdiagram, és hogyan testreszabható a diagram megjelenése.
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: Word dokumentum mentése a gyűrűdiagram szerkesztése után – Java útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: Word-dokumentum mentése Java-ban a gyűrűdiagram szerkesztése után
url: /hu/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word dokumentum mentése a fánkdiagram szerkesztése után Java-ban

Ha **Word dokumentumot** kell mentened, amely testreszabott fánkdiagramot tartalmaz, ez az útmutató pontosan megmutatja, hogyan. Néhány Java sorral megváltoztathatod a fánk lyukát, elforgathatod a fánkdiagramot, majd visszaírhatod az eredményt a lemezre.

Látni fogsz egy teljes, futtatható példát, amely az Aspose.Words for Java-t használja, valamint tippeket a több diagram kezelésére, a csomóponttípusok ellenőrzésére és a gyakori hibák elkerülésére. Külső hivatkozásokra nincs szükség – minden, amire szükséged van, benne van.

## Előfeltételek

- Java 17 vagy újabb telepítve
- Maven vagy Gradle a függőségek kezeléséhez
- Aspose.Words for Java (23.9 vagy újabb verzió) hozzáadva a projekthez  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- Egy Word fájl (`input.docx`), amely egyetlen fánkdiagramot tartalmaz

## 1. lépés: Word dokumentum betöltése

Az első lépés a forrásfájl megnyitása. Ez a lépés elengedhetetlen, mert minden további művelet a memóriában lévő `Document` objektumon dolgozik.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Miért?** A dokumentum betöltése DOM reprezentációt hoz létre, amely lehetővé teszi alakzatok, táblázatok és diagramok bejárását. Ha a fájlt nem lehet megnyitni, az Aspose.Words kivételt dob, így azonnal tudod, hogy az útvonal hibás.

## 2. lépés: A fánkdiagram alakzatának megtalálása

A diagram egy `Shape` csomópontban tárolódik. Lekérjük az első alakzatot, amely diagramot tartalmaz, és a renderelőt `Chart` típusra castoljuk.

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **Miért?** Az `isChart()` ellenőrzése megakadályozza a `ClassCastException`-t, ha a dokumentumban a diagram előtt képek vagy más alakzatok vannak. Ez a kódot robusztusabbá teszi kevert tartalmú dokumentumok esetén.

## 3. lépés: A fánk lyuk méretének módosítása  

Most szerkesztjük a fánk lyukát. A `setHoleSize` metódus a diagram sugárának százalékát várja (10 – 90).

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **Miért?** A fánk lyukának módosítása (`change doughnut hole` / `change chart hole size`) lehetővé teszi a központi terület hangsúlyozását vagy elnyomását. A 10‑90 % tartományon kívüli értékeket az API figyelmen kívül hagyja.

## 4. lépés: A fánkdiagram forgatása  

Az első szelet kezdőpontjának szabályozásához állítsd be az első szelet szögét. Ez hatékonyan **elforgatja a fánkdiagramot**.

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **Miért?** A diagram forgatása hasznos, ha egy adott szeletet a tetején szeretnéd megjeleníteni, vagy hogy megfeleljen egy tervezési specifikációnak.

## 5. lépés: A módosított dokumentum mentése  

Végül írd vissza a változtatásokat egy új fájlba. Ez az a pillanat, amikor **Word dokumentumot** mentesz a szerkesztett diagrammal.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Várható eredmény:** `output.docx` tartalmazza az eredeti tartalmat, de a fánkdiagram most 30 % lyukkal rendelkezik, és az első szelet 45 °‑nél kezdődik. A fájl megnyitása a Microsoft Wordben a módosított diagramot mutatja.

## Teljes működő példa

Az alábbiakban a teljes program látható, amelyet beilleszthetsz a fejlesztői környezetedbe. Tartalmazza az összes importot és a hibakezelést, amely a **fánkdiagram szerkesztéséhez** és a **Word dokumentum biztonságos mentéséhez** szükséges.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Várható kimenet

Amikor megnyitod a `output.docx` fájlt:

- A fánkdiagram központi lyuka körülbelül a diagram sugárának egyharmadát foglalja el.  
- Az első szelet a 45‑fokos pozícióban kezdődik, a teljes diagramot óramutató járásával megegyező irányba eltolva.  

Mindkét vizuális változás azonnal megjelenik Wordben.

## Gyakori variációk és szélsőséges esetek

| Situation | How to handle |
|-----------|----------------|
| **Több diagram** | Iterálj a `doc.getChildNodes(NodeType.SHAPE, true)`-en, és szűrd a `shape.isChart()`-et; alkalmazd a `setHoleSize` / `setFirstSliceAngle` metódusokat minden `Chart`-ra. |
| **A diagram nem fánk** | Ellenőrizd a `chart.getType()`-t; csak akkor hívd meg a `setHoleSize`-t, ha `chart.getType() == ChartType.DOUGHNUT`. |
| **Dinamikusan kell módosítani a lyuk méretét** | Számítsd ki a kívánt százalékot az adatértékek alapján, majd hívd meg a `setHoleSize(computedValue)`-t. |
| **Mentés stream-be** | Használd |

## Mit érdemes legközelebb megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan hozzunk létre oszlopdiagramot az Aspose.Words for Java használatával](/words/english/java/document-conversion-and-export/using-charts/)
- [Hogyan mentsünk dokumentumot PDF-ként az Aspose.Words for Java-val](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Word mentése jelszóval az Aspose.Words for Java használatával](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}