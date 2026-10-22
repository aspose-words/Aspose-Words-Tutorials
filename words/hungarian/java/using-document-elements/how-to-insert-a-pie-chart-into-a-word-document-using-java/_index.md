---
category: general
date: 2026-09-27
description: Tanulja meg, hogyan szúrjon be kördiagramot egy Word dokumentumba Java-val,
  hogyan készítsen kördiagramot Word-ben, és hogyan jelenítse meg a százalékokat a
  kördiagramon a tiszta adatáttekintés érdekében.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: hu
lastmod: 2026-09-27
og_description: Hogyan illesszünk be kördiagramot egy Word-dokumentumba Java-val.
  Ez az útmutató megmutatja, hogyan készítsünk kördiagramot Wordben, hogyan jelenítsük
  meg a százalékokat a kördiagramon, és hogyan adjunk hozzá vezetővonalakat.
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: Hogyan illesszünk be egy kördiagramot egy Word dokumentumba Java használatával
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: Hogyan szúrjunk be egy kördiagramot egy Word-dokumentumba Java használatával
url: /hu/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan illesszünk be egy kördiagramot egy Word dokumentumba Java segítségével

Ha **how to insert pie chart** egy Word fájlba, ez az útmutató végigvezeti a teljes folyamaton. Megmutatjuk, hogyan **create pie chart in Word**, hogyan jelenítsünk meg százalékokat minden szeletnél, és hogyan adjunk hozzá vezetővonalakat a kifinomult megjelenésért.

A Word automatizálás gyakran nehézkesnek tűnik, de az Aspose.Words for Java segítségével programozottan generálhat teljesen formázott dokumentumokat. A tutorial végére egy futtatható Java kódrészletet kap, amely egy stílusos kördiagramot tartalmazó Word dokumentumot hoz létre.

## Előfeltételek

- Java 17 vagy újabb telepítve
- Maven vagy Gradle a függőségek kezeléséhez
- Aspose.Words for Java (23.11 vagy újabb verzió) hozzáadva a projekthez
- Alapvető ismeretek a Java szintaxisról

Nem szükséges előzetes tapasztalat a diagram API-kkal kapcsolatban; az alábbi lépések mindent lefednek a projekt beállításától a végső kimenetig.

## 1. lépés: Maven függőség beállítása

Add the Aspose.Words library to your `pom.xml`. Ez az egyetlen függőség hozzáférést biztosít a `Document`, `DocumentBuilder` és diagram osztályokhoz.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

Ha Gradlet használsz, az ekvivalens a következő:

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **Pro tip:** Használd a legújabb stabil verziót a hibajavítások és az új diagram funkciók kihasználásához.

## 2. lépés: Új dokumentum és builder létrehozása

`Document` objektum a Word fájlt képviseli, míg a `DocumentBuilder` lehetővé teszi a tartalom beszúrását. Ez a **add chart to word document** alapja.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

A builder most már készen áll objektumok elhelyezésére a dokumentum bármely részén.

## 3. lépés: Kördiagram beszúrása

Az Aspose.Words több diagramtípust támogat; mi a `ChartType.PIE`-t választjuk. A méret pontokban van megadva (1 pont = 1/72 hüvelyk).

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

Ebben a szakaszban a diagram egy alapértelmezett adat sorozatot tartalmaz helyőrző értékekkel. Szükség esetén később lecserélheted ezeket az értékeket.

## 4. lépés: A diagram sorozatának elérése

A kördiagram egyetlen sorozattal rendelkezik, amely a szeletek értékeit tartalmazza. Szerezd meg, hogy formázást alkalmazhass.

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## 5. lépés: Az első szelet kiemelése (exploding)

Egy szelet kiemelése (exploding) a figyelmet egy adott adatpontra irányítja. Ez gyakori vizuális jelzés, ha egy kulcsfontosságú mérőszámot szeretnél hangsúlyozni.

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## 6. lépés: Százalékok megjelenítése minden szeleten

A százalékok közvetlen megjelenítése a diagramon javítja az adatértelmezést. Ez megfelel a **show percentages on pie chart** követelménynek.

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## 7. lépés: Vezetővonalak hozzáadása a tisztább címkékhez

A vezetővonalak összekötik a szeletcímkéket a megfelelő szekciókkal, ezzel elkerülve a kétértelműséget. Ez teljesíti a **how to add leader lines**.

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## 8. lépés: Dokumentum mentése

Végül írd a dokumentumot a lemezre. Bármely mappát választhatod, amelyhez írási jogosultságod van.

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

A program futtatása létrehozza a `output/PieFormatted.docx` fájlt. Nyisd meg a fájlt a Microsoft Wordben, és egy kördiagramot látsz, ahol:

- Az első szelet ki van emelve.
- Minden szelet megjeleníti a százalékos értékét.
- A vezetővonalak a százalékoktól a megfelelő szeletekre mutatnak.

### Várható kimenet

![Formázott kördiagram a Wordben](/images/pie-formatted.png){: .center-image alt="Formázott kördiagram beillesztve egy Word dokumentumba"}

A képernyőfotó (az alt szöveg a fő kulcsszót használja) szemlélteti a végső megjelenést: egy tiszta, adat‑vezérelt kördiagram, amely készen áll jelentések, javaslatok vagy műszerfalak számára.

## Gyakori variációk és szélsőséges esetek

### Szeletértékek módosítása

Ha egyedi adatokat szeretnél, cseréld le az alapértelmezett sorozat értékeket:

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### Több sorozat (donut diagram)

Míg egy egyszerű kördiagram egy sorozattal rendelkezik, az Aspose.Words több sorozatos donut diagramokat is támogat. Cseréld a `ChartType.PIE`-t `ChartType.DONUT`-ra, és ismételd meg a sorozat‑konfiguráció lépéseit.

### Exportálás PDF‑be

Ha az utólagos munkafolyamat PDF‑et igényel, hívd meg a `doc.save("output/PieFormatted.pdf");` metódust a diagram felépítése után. A vizuális elrendezés változatlan marad.

## Teljes forráskód

Az alábbiakban a teljes, önálló Java fájl található, amelyet beilleszthetsz az IDE‑dbe.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

Fordítsd le és futtasd a programot a `mvn compile exec:java -Dexec.mainClass=PieChartExample` paranccsal (vagy az ekvivalens Gradle parancssal). A generált Word fájl a teljesen formázott kördiagramot fogja tartalmazni.

## Következtetés

Most már tudod, hogyan **how to insert pie chart** egy Word dokumentumba Java segítségével, hogyan **create pie chart in Word**, hogyan **show percentages on pie chart**, és hogyan **add chart to word document** vezetővonalakkal. A teljes példa bemutatja az egyes lépéseket, elmagyarázza, miért íródott így a kód, és tippeket ad a testreszabáshoz.

Ezután érdemes lehet felfedezni:

- [Hogyan hozzunk létre oszlopdiagramot az Aspose.Words for Java használatával](/words/english/java/document-conversion-and-export/using-charts/)
- [Diagram tengely elrejtése egy Word dokumentumban](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Vonaldiagram létrehozása Wordben az Aspose.Words for .NET használatával](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}