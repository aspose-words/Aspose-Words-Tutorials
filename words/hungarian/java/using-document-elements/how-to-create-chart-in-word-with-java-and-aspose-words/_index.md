---
category: general
date: 2026-09-24
description: Tanulja meg, hogyan hozhat létre diagramot a Wordben Java használatával,
  hogyan illeszthet be radiális diagramot, és hogyan mentheti a dokumentumot docx
  formátumban az Aspose.Words segítségével.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create chart in word
- save document as docx
- add chart to word
- create word document java
- insert radial chart
language: hu
lastmod: 2026-09-24
og_description: Diagram létrehozása Wordben Java és Aspose.Words segítségével. Ez
  az útmutató megmutatja, hogyan adjon hozzá radiális diagramot, testreszabja az adatokat,
  és mentse a dokumentumot docx formátumban.
og_image_alt: Radial chart inserted in a Word document using Java code
og_title: Diagram készítése Wordben Java-val – lépésről lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  headline: How to create chart in Word with Java and Aspose.Words
  type: TechArticle
- description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  name: How to create chart in Word with Java and Aspose.Words
  steps:
  - name: You should see a single page with a centered radial chart.
    text: You should see a single page with a centered radial chart.
  - name: If you added series data, the chart displays four slices labeled Q1‑Q4.
    text: If you added series data, the chart displays four slices labeled Q1‑Q4.
  - name: Right‑click the chart → **Edit Data** to confirm the underlying data table.
    text: Right‑click the chart → **Edit Data** to confirm the underlying data table.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Chart
- DOCX
title: Hogyan készíts diagramot a Wordben Java és az Aspose.Words segítségével
url: /hu/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozhatunk létre diagramot Word-ben Java-val és az Aspose.Words segítségével

Ha **create chart in Word**-t kell létrehoznod Java alkalmazásból, ez az útmutató végigvezet a teljes folyamaton. Megmutatjuk, hogyan adhatunk hozzá egy radiális diagramot, opcionálisan tölthetjük fel a sorozatait, és végül **save document as docx**-et használva az Aspose.Words for Java könyvtárat.

A vizuális adatok generálása egy Word fájlban gyakori követelmény jelentések, számlázás vagy automatizált dokumentumgenerálás esetén. A tutorial végére képes leszel **create word document java** projekteket készíteni, amelyek **add chart to Word** fájlokat hoznak létre manuális szerkesztés nélkül.

## Előkövetelmények

* Java Development Kit (JDK) 8 vagy újabb.
* Maven vagy Gradle a függőségkezeléshez.
* IDE, például IntelliJ IDEA, Eclipse vagy VS Code.
* Érvényes Aspose.Words for Java licenc (az ingyenes próba a fejlesztéshez is működik).

Ezek az eszközök biztosítják az alapot a következő kódrészletekhez.

## 1. lépés: Maven projekt beállítása

Hozz létre egy új Maven projektet (vagy frissíts egy meglévőt), és add hozzá az Aspose.Words függőséget a `pom.xml`-hez:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word‑chart‑demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

A `mvn clean install` futtatása letölti a könyvtárat, és elérhetővé teszi a `Document`, `DocumentBuilder` és `ChartType` osztályokat az osztályútvonalon.

> **Pro tip:** Tartsd naprakészen a könyvtár verzióját. Az új kiadások új diagramtípusokat adnak hozzá és javítják a renderelési teljesítményt.

## 2. lépés: Új Word dokumentum létrehozása

Az első programozási lépés a **create chart in Word**-hez egy üres `Document` példányosítása. Ez az objektum képviseli a teljes `.docx` csomagot.

```java
import com.aspose.words.*;

public class RadialChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a blank Word document
        Document doc = new Document();

        // Step 2.2: Obtain a DocumentBuilder to insert content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` úgy működik, mint egy kurzor; ismeri a jelenlegi beszúrási pontot, és metódusokat biztosít szöveg, táblázatok és diagramok számára. Ekkor már **created word document java** stílusban rendelkezel – egy tiszta vászon, készen a tartalomra.

## 3. lépés: Radiális diagram beszúrása

Az Aspose.Words számos diagramtípust támogat. A **insert radial chart**-hez hívd meg az `insertChart`-ot a `ChartType.RADIAL` paraméterrel. A metódus továbbá a szélességet és magasságot pontban (1 point ≈ 1/72 inch) várja.

```java
        // Step 3: Insert a radial chart (400 × 300 points)
        Shape chart = builder.insertChart(ChartType.RADIAL, 400, 300);
```

A visszakapott `Shape` objektum tartalmazza a mögöttes diagram objektumot. A diagram automatikusan megjeleníti a 24,9°-os elrendezés fokozatait, ami a Wordben a radiális diagramok alapértelmezett beállítása.

### Miért használjunk radiális diagramot?

A radiális diagram olyan adatokat jelenít meg, amelyek körbe köröznek egy kört, így ideális ciklikus minták (pl. havi eladások, óra‑arc metrikák) ábrázolására. Ugyanaz az API képes oszlop-, kör- vagy vonaldiagramok beszúrására, de a radiális típus egyedi megjelenést kölcsönöz extra stíluskód nélkül.

## 4. lépés: (Opcionális) A diagram sorozat adatainak feltöltése

Ha azt szeretnéd, hogy a diagram valós értékeket mutasson, sorozatokat és pontokat kell hozzáadnod. A következő kódrészlet egy sorozatot ad hozzá három adatponttal:

```java
        // Optional: add data to the chart
        Chart chartObj = chart.getChart();
        chartObj.getSeries().clear(); // remove any default series

        // Create a new series
        ChartSeries series = chartObj.getSeries().add("Quarterly Revenue");

        // Add data points (value, category)
        series.getDataPoints().add(15000, "Q1");
        series.getDataPoints().add(21000, "Q2");
        series.getDataPoints().add(18000, "Q3");
        series.getDataPoints().add(24000, "Q4");
```

Az `add` hívásokat annyiszor megismételheted, ahány pont szükséges. Az Aspose.Words automatikusan frissíti a vizuális ábrázolást, így a radiális szeletek az új értékekhez igazodnak.

> **Common question:** *Mi a teendő, ha adatbázisból kell adatot kötni?*  
> Hozd be a sorokat, iterálj rajtuk, és a cikluson belül hívd meg a `series.getDataPoints().add(value, label)` metódust. Az API szálbiztos, és bármely általad biztosított `ResultSet`-tel működik.

## 5. lépés: Dokumentum mentése DOCX formátumban

Amikor a diagram készen áll, az utolsó lépés a **save document as docx**. A `save` metódus a fájl kiterjesztéséből határozza meg a kimeneti formátumot.

```java
        // Step 5: Persist the document
        String outputPath = "output/RadialChartDemo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Az előállított fájl egy teljesen működőképes radiális diagramot tartalmaz, amely megnyitható a Microsoft Word, a LibreOffice vagy bármely, a DOCX formátumot támogató megjelenítő programban. Mivel a `.docx` kiterjesztést használtuk, a Word az Open XML formátumban menti a fájlt, ami a modern szabvány a Word dokumentumok számára.

### Az eredmény ellenőrzése

Nyisd meg a `RadialChartDemo.docx` fájlt Wordben:

1. Egyetlen oldalt kell látnod, amelyen középre igazított radiális diagram szerepel.
2. Ha sorozat adatot adtál hozzá, a diagram négy szeletet mutat, Q1‑Q4 címkékkel.
3. Jobb‑kattints a diagramra → **Edit Data**, hogy ellenőrizd a mögöttes adat táblát.

Ha a diagram üresnek jelenik meg, ellenőrizd, hogy a sorozatok hozzáadása előtt hívtad-e a `chart.getChart()`-t, és győződj meg arról, hogy a dokumentumépítő kurzora a kívánt helyen van a diagram beszúrásához.

## 6. lépés: Haladó tippek diagramok használatához

| Tip | Why it matters |
|-----|----------------|
| **Set chart style** – `chart.getChart().setStyle(ChartStyle.STYLE_PRESET_5);` | Javítja a vizuális konzisztenciát anélkül, hogy manuálisan formáznád az egyes elemeket. |
| **Resize after insertion** – `chart.setWidth(500); chart.setHeight(350);` | Lehetővé teszi a diagram méretének finomhangolását az oldal elrendezése alapján. |
| **Add a title** – `chart.getChart().getTitle().setText("Revenue Overview");` | Kontextust ad az olvasóknak, akik a dokumentumot a környező szöveg nélkül nézik. |
| **Export to PDF** – `doc.save("RadialChartDemo.pdf");` | Hasznos, ha nem szerkeszthető verzióra van szükség a terjesztéshez. |
| **License handling** – `License lic = new License(); lic.setLicense("Aspose.Words.lic");` | Megakadályozza a kiértékelési vízjel megjelenését a termelési verziókban. |

Ezek a fejlesztések opcionálisak, de bemutatják, hogyan tudod tovább testre szabni a diagramot, miután megtanultad a **add chart to Word**-t.

## Következtetés

Most már egy teljes, önálló példával rendelkezel, amely megmutatja, hogyan **create chart in Word** Java-val, **insert radial chart**, opcionálisan töltsd fel adatokal, és **save document as docx**. Ugyanez a minta más diagramtípusokra is működik, így a tutorialt bővítheted oszlop-, vonal- vagy kördiagramokra is.

A következő lépésként érdemes felfedezni:

* **create word document java** projektek, amelyek táblázatokat, képeket és több diagramot kombinálnak.
* **save document as docx** használata **save document as pdf**-vel együtt a többformátumú jelentéshez.
* Dinamikus adatok hozzáadása REST API-król vagy adatbázisokból a diagramjaidhoz.

Nyugodtan kísérletezz a stílusbeállításokkal, a diagram méretekkel és az adatforrásokkal. Jó kódolást!

## Mit érdemes még megtanulni?

A következő tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan hozzunk létre oszlopdiagramot az Aspose.Words for Java használatával](/words/english/java/document-conversion-and-export/using-charts/)
- [Üres Word dokumentum létrehozása az Aspose.Words segítségével – Lépésről‑lépésre útmutató](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Word dokumentum Java – Téglalap alakzat hozzáadása árnyékhatással](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}