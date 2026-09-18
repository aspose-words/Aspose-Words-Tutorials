---
category: general
date: 2026-09-18
description: Tanulja meg, hogyan hozhat létre Word-dokumentumot és illesszen be kördiagramot
  az Aspose.Words for Java használatával. Tartalmazza a kördiagram forgatását és a
  Word-fájl generálásának lépéseit.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: hu
lastmod: 2026-09-18
og_description: Hozzon létre egy Word-dokumentumot, és szúrjon be egy kördiagramot
  Java segítségével. Kövesse ezt az útmutatót a kördiagram forgatásához, a szeletek
  szétrobbanásához és a Word-fájl generálásához.
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: Word-dokumentum létrehozása kördiagrammal – lépésről lépésre Java útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Hogyan hozzunk létre Word-dokumentumot kördiagrammal Java-ban
url: /hu/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre Word-dokumentumot kördiagrammal Java-ban

Ha **Word-dokumentumot** szeretnél létrehozni, amely adatokat jelenít meg, ez az útmutató megmutatja, hogyan teheted meg az Aspose.Words for Java segítségével. Megtanulod, hogyan illessz be egy kördiagramot, hogyan „robbantsd ki” egy szeletet, hogyan forgasd el a diagramot, és végül **generálj egy Word-fájlt**, amelyet megnyithatsz a Microsoft Wordben.

Jelentések készítése, amelyek szöveget és diagramokat kombinálnak, nem igényel külön grafikai eszközt. A tutorial végére egy teljes, futtatható programod lesz, amely .docx fájlt hoz létre, benne egy teljesen konfigurált kördiagrammal.

## Előfeltételek

- Java 17 vagy újabb (a kód Java 8+ verzióval is lefordítható)
- Maven vagy Gradle a függőségkezeléshez
- Aspose.Words for Java licenc (az ingyenes próba verzió elegendő ehhez a példához)
- Alapvető ismeretek a Java szintaxisról

## 1. lépés: Maven projekt beállítása

Hozz létre egy új Maven projektet, és add hozzá az Aspose.Words függőséget a `pom.xml`-hez:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **Pro tipp:** Tartsd naprakészen a verziószámot; az újabb kiadások diagram‑típus fejlesztéseket és hibajavításokat tartalmaznak.

## 2. lépés: Új Word-dokumentum létrehozása

Az első művelet, amikor **Word-dokumentumot** hozol létre programból, egy `Document` objektum példányosítása. Ez az objektum a teljes .docx fájlt képviseli a memóriában.

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

A `Document` osztály a belépési pont minden Word‑feldolgozó funkcióhoz. Ebben a pillanatban még nem íródik fájl a lemezre; minden RAM‑ban történik, amíg a `save` metódust nem hívod meg.

## 3. lépés: Kördiagram beillesztése

A `DocumentBuilder` segítségével tartalmat adhatsz a dokumentumhoz. Az `insertChart` segítségével **kördiagramot** illeszthetsz be közvetlenül.

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

A `ChartType.PIE` azt mondja az Aspose.Words‑nek, hogy kördiagramot hozzon létre. A méretek pontban vannak megadva (1 pt ≈ 1/72 in). Ez a hívás után a diagram egy új bekezdésben jelenik meg.

## 4. lépés: Diagram adatainak feltöltése

A kördiagramnak egy értékcsaládra van szüksége. Itt három kategóriát adunk hozzá: „Alma”, „Banán” és „Cseresznye”.

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

Az `add` metódus felépíti a sorozatot, és automatikusan létrehozza a jelmagyarázat bejegyzéseit. Ezt a mintát bármely numerikus adathalmazra újra felhasználhatod.

## 5. lépés: Az első szelet kiemelése

Egy szelet „robbantása” felhívja a figyelmet egy adott értékre. Az első szelet (index 0) 20 ponttal van kifújva.

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

Az `explode` beállítása a sorozaton az egész diagramra hat, így csak az első adatpont kerül eltolásra.

## 6. lépés: Kördiagram forgatása

A diagram forgatása javítja a vizuális egyensúlyt, különösen akkor, ha a legnagyobb szelet nem a tetején van. A `setRotationAngle` metódus fokban várja az értéket.

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

Az 45°-os forgatás az induló szöget az óramutató járásával megegyező irányba mozgatja, ami sok elrendezésben olvashatóbbá teszi a diagramot.

## 7. lépés: Dokumentum mentése és Word-fájl generálása

Végül írd a dokumentumot a lemezre. Ez a lépés **generál egy Word-fájlt**, amely megnyitható a Microsoft Word, a LibreOffice vagy bármely kompatibilis megjelenítő programmal.

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

A `save` metódus automatikusan felismeri a .docx kiterjesztést, és Word‑kompatibilis csomagot ír ki. A `output` mappának léteznie kell, vagy programból létrehozhatod.

### Várt eredmény

A program futtatása után nyisd meg a `output/PieChart.docx` fájlt. A következőket kell látnod:

- Egyetlen oldal, amelyen egy 400 × 300 pt méretű kördiagram található.
- A „Alma” szelet 20 pt‑val kifújva.
- Az egész diagram 45°‑kal óramutató járásával megegyező irányban elforgatva.
- Egy jelmagyarázat, amely a három gyümölcs kategóriát tükrözi.

## Gyakori variációk és szélhelyzetek

### Több diagram beillesztése

Ha egynél több diagramra van szükséged, hívd meg újra a `builder.insertChart`‑t a kurzor áthelyezése után:

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### Diagram színeinek módosítása

A szeletek színeit a sorozat `getPoints()` gyűjteményén keresztül testreszabhatod:

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### Nagy adathalmazok kezelése

Tíz vagy több szelet esetén fontold meg a gyűrűdiagram (`ChartType.DOUGHNUT`) használatát, hogy a megjelenés átlátható maradjon.

## Összegzés

Most már tudod, hogyan **hozz létre Word-dokumentumot**, **illessz be kördiagramot**, **forgasd el a kördiagramot**, és **generálj Word-fájlt** az Aspose.Words for Java segítségével. A teljes megoldás bemutatja a teljes munkafolyamatot a dokumentum inicializálásától a végső fájl kimenetig, lefedve mind a „hogyan”, mind a „miért” aspektusát minden lépésnek.

Ezután fedezd fel a kapcsolódó témákat, például **hogyan hozhatsz létre kördiagram adatokat adatbázisból**, adatcímkék hozzáadását, vagy a diagram képként való exportálását. Kísérletezz különböző diagramtípusokkal (oszlop, vonal, gyűrű) a Word‑automatizálási eszköztárad bővítéséhez.


## Mit érdemes még megtanulni?


Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}