---
category: general
date: 2026-11-25
description: Tanulja meg, hogyan készítsen kördiagramot Java-ban, hogyan illessze
  be a kördiagramot egy Word-dokumentumba, hogyan robbantsa szét a diagram szeletét,
  és hogyan változtassa meg a diagram orientációját, világos kódrészletekkel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: hu
lastmod: 2026-11-25
og_description: Készítsen kördiagramot Java-ban, illessze be a kördiagramot egy dokumentumba,
  kibontsa a diagram szeletét, és lépésről‑lépésre kóddal változtassa meg a diagram
  orientációját.
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: Kördiagram készítése Java-ban – beszúrás, szelet szétrobbantása és forgatás
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: Hogyan hozhatunk létre kördiagramot, illesszük be, és testre szabjuk a tájolását
  Java-ban
url: /hu/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre kördiagramot, szúrjuk be, és testre szabjuk a tájolást Java-ban

Ha **kördiagramot** kell létrehoznia egy Word-dokumentumban, ez az útmutató pontosan megmutatja, hogyan teheti meg. Megtanulja, hogyan **szúrjon be kördiagramot**, hogyan emelje ki egy szeletet a hangsúlyozás érdekében, és hogyan **változtassa meg a diagram tájolását** egy egyszerű forgatással.

A tutorial mindent lefed, amire szüksége van – a Aspose.Words for Java könyvtár beállításától egy végleges `.docx` fájl előállításáig, amely egy elforgatott, kiemelt kördiagramot jelenít meg. Nem szükséges külső dokumentáció; csak kövesse a lépéseket és futtassa a kódot.

## Prerequisites

Mielőtt elkezdené, győződjön meg róla, hogy rendelkezik:

* Java 17 vagy újabb verzióval.
* Maven vagy Gradle a függőségek kezeléséhez.
* Érvényes Aspose.Words for Java licenccel (vagy használja az ingyenes értékelő módot).

Adja hozzá az Aspose.Words függőséget a `pom.xml` (Maven) vagy `build.gradle` (Gradle) fájlhoz. Példa Mavenra:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **Pro tip:** Tartsa naprakészen a könyvtár verzióját; a legújabb kiadás (24.10 a cikk írásakor) hibajavításokat tartalmaz a diagrammegjelenítéshez.

## Step 1: Create pie chart and insert it into the document

Az első lépés a **kördiagram** objektumok létrehozása és beágyazása egy Word-fájlba. Az alábbi kód egy egyszerű dokumentumot épít, hozzáad egy diagramhelyőrzőt, és egy 400 × 300 pixel méretű kördiagramot szúr be.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**Miért fontos:** A `builder.insertChart` egy diagramhelyőrzőt hoz létre, amelyet az Aspose.Words automatikusan OOXML diagrammá konvertál a dokumentum mentésekor. A `ChartType.PIE` argumentum azt mondja a könyvtárnak, hogy kördiagramot jelenítsen meg, ezzel teljesítve a **insert pie chart** követelményt.

## Step 2: Explode pie slice to highlight a segment

Egy szelet kiemelése felhívja a figyelmet egy adott adatpontra. Az alábbi sor a első szeletet (index 0) 10 ponttal emeli ki:

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

A szelet indexét megváltoztathatja egy másik szelet célzásához, vagy módosíthatja a kiemelés távolságát egy finomabb hatás érdekében. A szelet kiemelése a **explode pie slice** szabványos módja az Aspose.Words-ben.

## Step 3: Change chart orientation by rotating it

A diagram forgatása friss vizuális perspektívát ad. Használja a `setRotationAngle` metódust a teljes diagram óramutató járásával megegyező irányú forgatásához (a szög fokban van megadva).

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

A fenti hívás teljesíti a **rotate pie chart** és **change chart orientation** követelményeket. Bármely 0 és 360 fok közötti szög elfogadott.

## Full runnable example

Mindent egy helyen, itt egy komplett, önálló program, amely kördiagramot hoz létre, kiemel egy szeletet, és elforgatja a diagramot. Futtassa az IDE-jéből vagy a parancssorból a `java -cp <classpath> PieChartDemo` paranccsal.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### Expected output

* Egy **CreatePieChartDemo.docx** nevű fájl jelenik meg a munkakönyvtárban.
* A fájl megnyitása a Microsoft Wordben egy 400 × 300 pixel méretű kördiagramot mutat.
* Az első szelet (Q1) 10 ponttal ki van tolva, így **explode pie slice** hatást kelt.
* A teljes diagram 45 fokkal van elforgatva, bemutatva a **change chart orientation** és **rotate pie chart** funkciókat.

## Common variations and edge cases

| Helyzet | Hogyan kell módosítani a kódot |
|-----------|-----------------------|
| **Eltérő diagramméret** | Módosítsa a `400, 300` argumentumokat a `insertChart` hívásban. |
| **Több sorozat** | Adjon hozzá további `ChartSeries` objektumokat a `chart.getSeries()`-hez. |
| **Másik szelet kiemelése** | Használja a `setExplode(sliceIndex, distance)` metódust a kívánt `sliceIndex` értékkel. |
| **Nincs forgatás szükséges** | Hagyja ki a `setRotationAngle` hívást, vagy állítsa a szöget `0`-ra. |
| **Exportálás PDF-be a DOCX helyett** | A dokumentum építése után hívja a `doc.save("output.pdf")` metódust PDF formátummal. |

> **Figyeljen:** Negatív kiemelési távolság használata `IllegalArgumentException`-t dob. Mindig adjon meg nem negatív értéket.

## Performance tip

Ha sok diagramot generál egy ciklusban, használjon egyetlen `DocumentBuilder` példányt, és csak a `insertChart` metódust hívja meg minden iterációban. Ez csökkenti a memóriaigényt és felgyorsítja a feldolgozást.

## Conclusion

Most már tudja, hogyan **create pie chart**, **insert pie chart**, **explode pie slice**, és **rotate pie chart** használatával az Aspose.Words for Java könyvtárat. A teljes példakód bemutatja a teljes munkafolyamatot – a dokumentum inicializálásától a fájl mentéséig, amely egy elforgatott, kiemelt kördiagramot jelenít meg.

A következő lépésként tovább **change chart orientation**-t vizsgálhat 3‑D hatások alkalmazásával, vagy kísérletezhet más diagramtípusokkal, például **Bar** vagy **Line**. Ugyanazok az API minták érvényesek, így a tutorial bővítése egyszerű.

Nyugodtan módosítsa az adatokat, a szelet indexét vagy a forgatási szöget, hogy megfeleljen saját jelentési igényeinek, és ossza meg eredményeit a közösséggel!

## What Should You Learn Next?

A következő tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}