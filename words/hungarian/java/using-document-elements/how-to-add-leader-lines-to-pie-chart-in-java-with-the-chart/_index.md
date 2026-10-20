---
category: general
date: 2026-08-20
description: Adj vezetővonalakat a kördiagramhoz Java-ban gyorsan. Tanuld meg, hogyan
  illessz be, szétbontj, újraszínezz és címkézz szeleteket a Chart API-val.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: hu
lastmod: 2026-08-20
og_description: Adj vezetővonalakat a kördiagramhoz Java-ban egy tömör példával. Kövesd
  ezt az útmutatót a szeletek beszúrásához, szétszórásához, újraszínezéséhez és címkézéséhez
  a Chart API használatával.
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: Vezetővonalak hozzáadása kördiagramhoz Java-ban – lépésről lépésre Chart
  API útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: Hogyan adhatunk hozzá vezetővonalakat a kördiagramhoz Java-ban a Chart API-val
url: /hu/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan adjunk vezető vonalakat kördiagramhoz Java-ban a Chart API-val

Ha Java-ban **vezető vonalakat a kördiagramhoz adni** kell, ez az útmutató végigvezet a teljes folyamaton. Megmutatjuk, hogyan szúrj be egy kördiagramot, hogyan robbants ki egy szeletet a hangsúlyozáshoz, hogyan változtasd meg a színét, és végül hogyan engedélyezd a vezető vonalakat, amelyek feliratozzák a kirobbanó szegmenst.

A példa a szabványos Chart API-t használja, amely számos Java jelentéskészítő könyvtárban megtalálható. Külső eszközök nem szükségesek, és a kód bármely JDK 8+ környezetben fut.

## Mit fogsz elérni

* Hozz létre egy `Chart`-ot `ChartType.PIE` típusúval egy egyedi mérettel.  
* Robbants ki az első szeletet a figyelem felkeltéséhez.  
* Állítsd be a kirobbanó szelet szektor színét kékre.  
* **Vezető vonalakat adj a kördiagramhoz**, hogy a szelet címkéje egyértelműen kapcsolódjon.

Már kell, hogy legyen egy Java projekted a Chart könyvtárral a classpath-on. Ha Maven-t használsz, add hozzá a függőséget, amelyet az előkövetelmények szakaszban láthatsz.

## Előkövetelmények

* JDK 8 vagy újabb telepítve.  
* A Chart könyvtár (pl. `com.example.chart:chart-api:2.5.0`).  
* Alapvető ismeretek a Java osztályok és metódushívások terén.

---

## Hogyan adjunk vezető vonalakat a kördiagramhoz

Az alábbiakban egy teljes, futtatható program látható, amely minden lépést bemutat. A kód szándékosan önálló, így másolhatod, beillesztheted és futtathatod módosítások nélkül.

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### Az egyes lépések magyarázata

| Lépés | Mit csinál a kód | Miért fontos |
|------|-------------------|----------------|
| **1️⃣ Kördiagram beszúrása** | `builder.insertChart(ChartType.PIE, 400, 300)` egy 400 × 300 pixel kördiagramot hoz létre. | Létrehozza a diagram konténert és meghatározza annak méreteit, amelyek befolyásolják a címkék elhelyezését és a vezető vonalak hosszát. |
| **2️⃣ Az első szelet kirobbanása** | `setExplosion(20)` a szeletet a sugár 20 %-ával eltolja. | A kirobbanó szelet felkelti a néző figyelmét és láthatóvá teszi a vezető vonalat. |
| **3️⃣ Szektor szín beállítása** | `setSectorColor(Color.BLUE)` a szelet kitöltését kékre változtatja. | A színkontraszt javítja az olvashatóságot, különösen ha a szelet ki van emelve. |
| **4️⃣ Vezető vonalak engedélyezése** | `setLeaderLines(true)` bekapcsolja az összekötő vonalakat, amelyek a szeletet a címkéjéhez kapcsolják. | A vezető vonalak biztosítják, hogy a címke olvasható maradjon még akkor is, ha a szelet kifelé van mozgatva. |

A `saveAsPng` hívás opcionális, de hasznos a vizuális eredmény ellenőrzéséhez. A program futtatása után egy az alábbihoz hasonló képet kell látnod.

![Vezető vonalak hozzáadása a kördiagramhoz](https://example.com/assets/pie-leader-lines.png "Vezető vonalak hozzáadása a kördiagramhoz – kirobbanó szelet kék színnel és vezető vonalakkal")

*Ábra: Egy kördiagram, ahol az első szelet kirobban, kék színű, és egy vezető vonallal van összekötve a címkéjével.*

## A vezető vonalak testreszabása (haladó)

Az alap `setLeaderLines(true)` hívás a könyvtár alapértelmezett stílusát használja. További beállításokkal szabályozhatod a megjelenést:

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

Ezek a beállítások hasznosak, ha a vállalati arculathoz kell igazítani, vagy a hozzáférhetőséget szeretnéd javítani.

### Több sorozat kezelése

Ha a kördiagramod több mint egy sorozatot tartalmaz, előfordulhat, hogy csak egy adott szelethez szeretnél vezető vonalakat. Használd a sorozat indexét a megfelelő elem célzásához:

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

Ha egy szelet nincs kirobbanva, a vezető vonal általában automatikusan rejtve van, de kényszerítheted a megjelenést a `setLeaderLineEnabled(true)` használatával.

## Gyakori buktatók és elkerülésük módjai

| Buktató | Tünet | Megoldás |
|--------|-------|----------|
| **A vezető vonalak nem láthatók** | A diagram csatlakozók nélkül jelenik meg. | Győződj meg arról, hogy a szelet ki van robbantva (`setExplosion` > 0), vagy kifejezetten engedélyezd a vezető vonalakat a szeleten. |
| **Címkék átfedése** | A címkék egymással ütköznek. | Növeld a diagram méretét, vagy állítsd be a `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)` értéket. |
| **A szín nem alkalmazott** | A szelet az alapértelmezett színen marad. | Ellenőrizd, hogy a megfelelő sorozat indexet célozod (`getSeries().get(0)`). |
| **A kép nem mentődött** | `saveAsPng` kivételt dob. | Ellenőrizd a kimeneti könyvtár írási jogosultságait, és hogy a könyvtár támogatja-e a PNG exportot. |

## Teljes forráskód listázása

Kényelmi okokból itt újra a teljes forrásfájl, beleértve az importokat és a megjegyzéseket:

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

A program futtatása létrehozza a `pie-with-leader-lines.png` fájlt, amely egy kirobbanó kék szelettel és egyértelmű vezető vonalakkal ellátott kördiagramot mutat, amelyek a szelet címkéjére mutatnak.

## Következtetés

Most már tudod, hogyan **adj vezető vonalakat a kördiagram objektumokhoz** Java-ban a Chart API használatával. A folyamat egy `ChartType.PIE` beszúrásából, a kívánt szelet kirobbanásából, a szín testreszabásából és a vezető vonalak engedélyezéséből áll. Az opcionális stílusbeállításokkal finomhangolhatod a vonal színét, vastagságát és a címke elhelyezését, hogy bármilyen vizuális követelménynek megfeleljen.

Ezután érdemes megvizsgálni a kapcsolódó témákat, például **pie chart explosion Java**, **set sector color Chart API**, és **builder.insertChart usage**, hogy összetettebb vizualizációkat hozz létre, mint a gyűrűdiagramok, rétegezett kördiagramok vagy interaktív műszerfalak.

Nyugodtan kísérletezz különböző szelet indexekkel, színekkel és vezető vonal stílusokkal—diagramjaid egyre informatívabbá és vizuálisan vonzóbbá válnak minden módosítással. Boldog kódolást!

## Mit érdemes legközelebb megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljesen működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Add Date Time Values To Axis Of A Chart](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}