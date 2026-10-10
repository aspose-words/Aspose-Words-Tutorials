---
category: general
date: 2026-10-10
description: Tanulja meg, hogyan lehet elforgatni egy diagramot egy Word-fájlban,
  és módosítani a diagramot Wordben a gyűrűdiagram méretének megváltoztatásához egy
  teljes Java példával.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: hu
lastmod: 2026-10-10
og_description: Hogyan lehet elforgatni egy diagramot egy Word-fájlban, és módosítani
  a diagramot Wordben a fánkdiagram méretének megváltoztatásához az Aspose.Words for
  Java használatával.
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: Hogyan forgassuk el a diagramot egy Word-dokumentumban – lépésről lépésre
  Java útmutató
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Hogyan forgassuk el a diagramot egy Word-dokumentumban az Aspose.Words segítségével
url: /hu/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan forgassunk diagramot egy Word dokumentumban az Aspose.Words segítségével

Ha **how to rotate chart**-ra van szükséged egy Microsoft Word fájlban, ez az útmutató pontos lépéseket mutat. Emellett megtanulod, hogyan **modify chart in Word**-t **change doughnut chart size**-ra anélkül, hogy elhagynád a Java kódodat.

A Word automatizálás gyakran úgy érződik, mintha egymástól független API hívások sorozata lenne, de az Aspose.Words segítségével a diagramot bármely más dokumentumcsomópontként kezelheted. A tutorial végére egy futtatható programod lesz, amely betölti a meglévő `.docx` fájlt, 45°‑kal elforgat egy fánkdiagramot, a lyukat a sugár 50 %-ára csökkenti, és az eredményt új fájlként menti.

## Prerequisites

Mielőtt elkezdenéd, győződj meg róla, hogy rendelkezel:

* Java 17 vagy újabb telepítve.
* Maven (vagy Gradle) a függőségek kezeléséhez.
* Egy bemeneti Word dokumentum (`input.docx`), amely már tartalmaz egy fánkdiagramot.
* Érvényes Aspose.Words for Java licenc (vagy használja a kiértékelési módot).

## Step 1: Set up the Maven project

Hozz létre egy új Maven projektet, vagy add hozzá a következő függőséget a meglévő `pom.xml`-hez:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

A `mvn clean install` futtatása letölti a könyvtárat, és a osztályokat elérhetővé teszi az osztályúton.

## Step 2: Load the Word document that contains a chart

Az első művelet a meglévő dokumentum megnyitása. A `Document` osztály képviseli az egész fájlt.

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

A fájl betöltése **nem** módosítja azt; egyszerűen egy memóriában lévő reprezentációt hoz létre, amelyet lekérdezhetsz és szerkeszthetsz.

## Step 3: Create a DocumentBuilder for navigation

A `DocumentBuilder` egy kurzor‑szerű API-t biztosít a dokumentumfa bejárásához. Ezt fogjuk használni az első diagram alakzat megtalálásához.

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

A builder a dokumentum elején kezd, de később szükség esetén bármely csomópontra áthelyezhető.

## Step 4: Retrieve the first chart shape

A diagramok `Shape` csomópontokként tárolódnak. A `NodeType.SHAPE` típusú gyermekcsomópontok szűrésével kinyerhetjük a diagram objektumot.

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

Ha a dokumentum több diagramot tartalmaz, iterálhatsz a `getChildNodes`-on, és minden `Shape` esetén ellenőrizheted a `hasChart()`-t, mielőtt átkonvertálnád.

## Step 5: Rotate the chart (how to rotate chart)

A fánkdiagram lényegében egy lyukú kördiagram. Forgatása megváltoztatja az első szelet kezdőszögét.

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

A `setStartAngle` metódus egy fokokat jelző double értéket vár. A pozitív értékek óramutató járásával megegyező irányba forgatnak, a negatívak pedig ellentétes irányba.

## Step 6: Change the doughnut hole size (change doughnut chart size)

A lyuk mérete a diagram sugárának tört részeként van kifejezve. A `0.5` érték azt jelenti, hogy a lyuk a teljes sugár 50 %-át foglalja el.

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**Tip:** Az érvényes tartomány `0.0` (nincs lyuk, azaz normál kör) és `0.9` (nagyon vékony gyűrű) között van. A tartományon kívüli értékek `IllegalArgumentException`-t dobnak.

## Step 7: Save the modified document

Végül írd vissza a változtatásokat a lemezre.

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

Amikor megnyitod a `DoughnutFormatted.docx`-et a Microsoft Wordben, láthatod, hogy a fánkdiagram 45°‑kal el van forgatva, és a lyuk a eredeti méret felére csökkent.

## Full, runnable example

Az összes részt összegezve, itt a teljes program, amelyet egyszerűen beilleszthetsz a fejlesztői környezetedbe:

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### Expected output

A program futtatása a következőt írja ki:

```
Chart rotated and doughnut size changed successfully.
```

A `DoughnutFormatted.docx` megnyitása egy olyan fánkdiagramot mutat, amelynek első szelete a 45°‑os pozícióból indul, és a belső sugár a külső sugár felét foglalja el.

## Common variations and edge cases

| Helyzet | Mit kell módosítani | Miért fontos |
|-----------|----------------|----------------|
| **Több diagram** | `getChildNodes(NodeType.SHAPE, true)`-t iterálva, és minden `shape` esetén ellenőrizve a `hasChart()`-t | Biztosítja, hogy a kívánt diagramot módosítsd, ne az elsőt |
| **Oszlop vagy vonaldiagram** | `setStartAngle` nem alkalmazható; használja a `chart.getSeries().get(0).setFillFormat(...)`-t egyéb vizuális finomításokhoz | Nem minden diagramtípus támogatja a forgatást; csak a fánk/kördiagramok rendelkeznek kezdőszöggel |
| **Lyuk nélküli diagram** | `setDoughnutHoleSize` kihagyása vagy először a diagram típusának fánkká konvertálása a `chart.setChartType(ChartType.DONUT)` segítségével | Lyukméret módosítása nem fánk diagramon kivételt dob |
| **Nagy dokumentumok** | `DocumentBuilder.moveToDocumentStart()` és `builder.moveToNode(chartShape)` használata a célzott navigációhoz | Javítja a teljesítményt azáltal, hogy elkerüli a nem releváns csomópontok teljes bejárását |

## Pro tips for reliable chart manipulation

* **Cache the chart reference** – Ha több tulajdonságot szeretnél módosítani, tarts egy helyi `Chart` változót a `chartShape.getChart()` ismételt hívása helyett.
* **Validate input values** – A `setStartAngle` vagy `setDoughnutHoleSize` hívása előtt ellenőrizd a tartományt a futásidejű hibák elkerülése érdekében.
* **Use a license** – A kiértékelési mód vízjelet helyez az első oldalra. Licenc alkalmazása (`License license = new License(); license.setLicense("Aspose.Words.lic");`) eltávolítja azt.

## Next steps

Most, hogy már tudod, **how to rotate chart** és **change doughnut chart size**, felfedezheted a további **modify chart in Word** szcenáriókat:

* Módosítsd a szelet színeit a `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())` használatával.
* Adj hozzá adatcímkéket a `chart.getSeries().get(0).setHasDataLabel(true)` hívásával.
* Exportáld a diagramot képként a `chart.toImage(300, 300, ImageType.PNG)` használatával.

Ezek a kiterjesztések ugyanazt a mintát követik: szerezzük meg a `Chart` objektumot, hívjuk meg a megfelelő setter‑t, és mentsük a dokumentumot.

---

**Épp most sajátítottad el a fánkdiagramok forgatását és átméretezését Wordben Java használatával.** Nyugodtan adaptáld a kódot más diagramtípusokhoz, integráld egy nagyobb dokumentum‑generálási folyamatba, vagy kombináld az Aspose.Slides‑szel PowerPoint automatizáláshoz. Boldog kódolást!

## Mit érdemes legközelebb megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan hozzunk létre oszlopdiagramot az Aspose.Words for Java segítségével](/words/english/java/document-conversion-and-export/using-charts/)
- [Diagram tengely elrejtése egy Word dokumentumban](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Buborékdiagram beszúrása Word dokumentumba](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}