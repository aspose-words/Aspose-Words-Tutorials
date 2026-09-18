---
category: general
date: 2026-09-18
description: Tanulja meg, hogyan hozhat létre radiális diagramot egy Word-dokumentumban
  Java használatával, hogyan adhat hozzá diagram adatcímkéket, és hogyan illeszthet
  be sorozat adatokat egy teljes kódrészlettel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: hu
lastmod: 2026-09-18
og_description: Készíts radiális diagramot egy Word dokumentumban Java használatával,
  adj hozzá diagram adatcímkéket, és egyetlen útmutatóban illeszd be a sorozat adatait.
og_image_alt: Radial chart displayed inside a generated Word document
og_title: Radial diagram készítése Wordben Java-val – lépésről lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: Hogyan hozhatunk létre radiális diagramot egy Word dokumentumban Java segítségével
url: /hu/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan készítsünk radiális diagramot Word dokumentumban Java-val

Ha Word dokumentumban kell radiális diagramot létrehoznod, ez az útmutató pontos lépéseket mutat. Emellett megtanulod, hogyan adj hozzá diagram adatcímkéket és hogyan szúrj be sorozat adatokat, hogy a diagram készen álljon a bemutatásra.

A diagram programozott generálása megszünteti a kézi formázási munkát, és biztosítja a konzisztenciát a jelentések között. A tutorial feltételezi, hogy rendelkezel alapvető Java ismeretekkel, és telepítve van az Aspose.Words for Java legújabb verziója.

## Amire szükséged lesz

* Java 17 vagy újabb  
* Aspose.Words for Java (23.12 vagy újabb verzió)  
* Egy IDE vagy build eszköz, amely képes feloldani a Maven/Gradle függőségeket  

Ezeknek a előfeltételeknek a telepítése lehetővé teszi, hogy a példát további konfiguráció nélkül futtasd.

## Hogyan készítsünk radiális diagramot Word dokumentumban

Az első lépés egy üres Word fájl létrehozása, amely a diagramot fogja tartalmazni. Egy üres dokumentum tiszta vászonként szolgál, és elkerüli a nem kívánt stílusok alkalmazását.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

A `Document` a teljes .docx fájlt képviseli, míg a `DocumentBuilder` olyan metódusokat biztosít, amelyekkel beilleszthetsz elemeket, például bekezdéseket, táblázatokat és diagramokat.

## Hogyan szúrjuk be a diagramot

Ezután beillesztjük magát a diagramot. Az `insertChart` metódus létrehozza a diagram objektumot, és a builder aktuális kurzorpozíciójába helyezi.

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

A polárdiagram a központi tengely körül jeleníti meg az adatpontokat, ami ideális ciklikus információk ábrázolásához. A méretek pontban (pt) vannak megadva (1 pt ≈ 1/72 inch).

## Sorozat adatainak hozzáadása a diagramhoz

Egy diagram sorozatadatok nélkül üres. Sorozatot manuálisan is hozzáadhatsz, vagy adatforráshoz kötheted. Az alábbi példa egyetlen sorozatot ad hozzá három adatponttal.

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

Az `add` egy sorozat nevet, egy kategória címkék listáját és a hozzájuk tartozó numerikus értékek listáját kapja. Ezt a blokkot ismételheted további sorozatok (`addSeriesData`) hozzáadásához.

## Diagram adatcímkék hozzáadása az első sorozathoz

Az adatcímkék olvashatóvá teszik a diagramot anélkül, hogy az egérrel kellene föléjük menni. A következő sor bekapcsolja az értékcímkéket az első sorozathoz.

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

A `showValue` `true` értékre állítása közvetlenül a diagramon jeleníti meg minden pont értékét. Ugyanazon `DataLabelFormat` objektumon keresztül engedélyezheted a kategórianév, százalék vagy vezetővonal megjelenítését is.

## Word fájl mentése

Miután a diagram be van állítva, írd a dokumentumot a lemezre. Válassz egy olyan helyet, amelyhez az alkalmazásod hozzáfér.

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

A `RadialChart.docx` fájl most már egy teljesen működő radiális diagramot tartalmaz adatcímkékkel.

## Teljes működő példa

Az alábbi önálló programot másolhatod, lefordíthatod és futtathatod. Bemutatja a teljes munkafolyamatot az üres Word dokumentum létrehozásától a radiális diagram adatcímkékkel való mentéséig.

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**Várható eredmény**

Amikor megnyitod a `output/RadialChart.docx` fájlt a Microsoft Wordben, egy *Quarterly Sales* címmel ellátott radiális diagramot látsz. Minden pont a numerikus értékét (pl. „15000”) a jelölő mellett jeleníti meg.

## Gyakori variációk és szélhelyzetek

| Helyzet | Javasolt módosítás |
|-----------|--------------------|
| Másik diagramtípusra van szükség | Cseréld le a `ChartType.POLAR`-t bármely más `ChartType` enum értékre (pl. `ChartType.COLUMN`). |
| A diagramnak külső Excel tartományt kell használnia | Használd a `chart.setDataRange("Sheet1!A1:B5")` metódust a diagram létrehozása és a munkafüzet betöltése után. |
| El szeretnéd rejteni a jelmagyarázatot | `chart.getLegend().setVisible(false);` |
| A dokumentumot PDF‑ként kell menteni | Hívd meg a `doc.save("RadialChart.pdf");` metódust – az Aspose.Words automatikusan konvertálja a diagramot. |

Ezek a módosítások megőrzik a fő logikát, miközben a kimenetet a specifikus igényekhez igazítják.

## Pro tippek

* **A builder újrahasználata** – Több diagramot is beilleszthetsz ugyanabba a dokumentumba, ha többször meghívod a `builder.insertChart` metódust.  
* **Teljesítmény** – Sok diagram generálásakor hozz létre egyetlen `DocumentBuilder` példányt, és használd újra, hogy csökkentsd az objektum‑allokáció terhelését.  
* **Stílus** – A diagram megjelenését (színek, vonalvastagság) a `Chart` objektum `getSeries().get(i).getFormat()` metódusai vezérlik. Kísérletezz ezekkel a beállításokkal, hogy a vállalati arculathoz igazodjon.

## Következtetés

Most már tudod, hogyan kell radiális diagramot létrehozni Word dokumentumban Java-val, hogyan adj hozzá sorozat adatokat, és hogyan helyezz el diagram adatcímkéket a fájl mentése előtt. A teljes példát tovább bővítheted további sorozatokkal, egyedi stílusokkal vagy alternatív kimeneti formátumokkal.

Fedezd fel a kapcsolódó témákat, például **hogyan szúrj be diagramot** külső adatforrásokból, **üres Word dokumentum létrehozása** előre definiált sablonokkal, és **sorozat adatainak dinamikus hozzáadása** adatbázisokból. Kísérletezz különböző diagramtípusokkal, hogy megtaláld a legmegfelelőbb vizualizációt az adataidhoz.

## Mit érdemes legközelebb megtanulni?

- [Hogyan készítsünk oszlopdiagramot Aspose.Words for Java használatával](/words/english/java/document-conversion-and-export/using-charts/)
- [Word dokumentum létrehozása Java‑val – Téglalap alakzat hozzáadása árnyékhatással](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Alapértelmezett beállítások megadása adatcímkékhez egy diagramon](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}