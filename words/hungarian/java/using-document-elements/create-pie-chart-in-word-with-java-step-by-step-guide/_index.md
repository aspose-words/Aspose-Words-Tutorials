---
category: general
date: 2026-08-14
description: Készíts kördiagramot Wordben Java-val az Aspose.Words segítségével. Tanulja
  meg, hogyan adjon hozzá sorozat adatokat a diagramhoz, és hogyan forgassa el a kördiagram
  szeletét néhány sorban.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: hu
lastmod: 2026-08-14
og_description: Készítsen kördiagramot Wordben Java-val az Aspose.Words használatával.
  Ez az útmutató bemutatja, hogyan adhat hozzá sorozat adatokat a diagramhoz, és hogyan
  forgathatja gyorsan a kördiagram szeletét.
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: Kördiagram készítése Wordben Java-val – teljes kódolási útmutató
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Kördiagram létrehozása Wordben Java-val – lépésről lépésre útmutató
url: /hu/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kördiagram létrehozása Word-ben Java-val – lépésről‑lépésre útmutató

Ha programozott módon **kördiagramot kell létrehozni Word-ben**, ez az útmutató pontosan megmutatja, hogyan teheted meg Java és Aspose.Words segítségével. Megtanulod a teljes munkafolyamatot, a diagram beszúrásától az adatpontok hozzáadásáig és az első szelet elforgatásáig.

A diagram közvetlenül egy `.docx` fájlban történő generálása eltávolítja a manuális másolás‑beillesztés lépését, és lehetővé teszi jelentések, számlák vagy műszerfalak automatizálását. Útközben bemutatjuk, hogyan **adjunk sorozat adatokat a diagramhoz** és hogyan **forgassuk el a kördiagram szeletet** a jobb vizuális hangsúly érdekében.

## Kördiagram létrehozása Word-ben – áttekintés

Az Aspose.Words for Java egy folyékony `DocumentBuilder` API-t biztosít, amely képes diagram objektumot beszúrni egy Word dokumentumba. A választott diagramtípus határozza meg az alapértelmezett elrendezést, és testreszabhatod a sorozatot, színeket, szögeket, sőt egyetlen metódushívással átválthatsz gyűrű alakú diagramra is.

### Miért használjuk az Aspose.Words-ot?

* **No Microsoft Office required** – a könyvtár bármely szerveren vagy CI környezetben működik.  
* **Full .docx fidelity** – a generált diagram pontosan olyan, mint egy manuálisan Word-ben létrehozott.  
* **Single‑file dependency** – csak add hozzá a JAR-t, és már használhatod.

## Hogyan adjunk sorozat adatokat a diagramhoz

Egy diagram adat nélkül csak egy helykitöltő. A `Chart` objektum egy `Series` gyűjteményt tesz elérhetővé; minden sorozat egy numerikus értéklistát tartalmaz, amely a szeletekre (kördiagram esetén) vagy pontokra (vonaldiagram esetén) vonatkozik. Az adatok hozzáadása egyszerű:

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**What the code does:**  
* `chart.getSeries()` returns a `List<ChartSeries>`.  
* `get(0)` selects the first series because a pie chart contains only one series by definition.  
* `add(double)` appends a data point. The values are automatically converted to percentages that sum to 100 % when the chart renders.

> **Pro tip:** Ha az adatforrásod háromnál több kategóriát tartalmaz, folytasd az értékek ugyanúgy történő hozzáadását. Az Aspose.Words automatikusan további szeleteket hoz létre.

## Kördiagram szelet elforgatása

Néha egy adott szeletet egy meghatározott szögben szeretnénk elindítani, hogy a legfontosabb rész a néző felé nézzen. A `setFirstSliceAngle(double)` metódus elforgatja a teljes diagramot, ezzel a első szelet kiindulási pontját módosítva:

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

A szöget fokban mérik az óramutató járásával megegyező irányban a függőleges tengelytől. Ha `0`-ra (az alapértelmezett) állítod, az első szelet a tetején jelenik meg. Állítsd a értéket a szelet kiemeléséhez vagy egy tervezési irányelvnek megfelelően.

> **Common question:** *Does rotating affect the data order?*  
> Nem. Az adat sorrendje változatlan marad; csak a vizuális kiindulási pozíció változik.

## Teljes Java példa

Az alábbiakban egy komplett, azonnal futtatható program látható, amely Word dokumentumot hoz létre egy kördiagrammal, hozzáadja a sorozat adatokat, elforgatja a szeletet, és elmenti a fájlt. Minden szükséges import felsorolásra került, így a kódot bármely IDE-be be tudod másolni.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Várható kimenet

* A **PieChart.docx** nevű fájl megjelenik az `output` mappában.  
* A fájl Microsoft Word-ben történő megnyitása egy színes kördiagramot mutat három szelettel (40 %, 30 %, 30 %).  
* A diagram 45°-kal az óramutató járásával megegyező irányban van elforgatva, így az első szelet kissé a függőleges tengely jobb oldalán kezdődik.

## Gyakori buktatók és legjobb gyakorlatok

| Probléma | Miért fordul elő | Megoldás |
|----------|-------------------|----------|
| **A diagram üresnek jelenik meg** | A dokumentumot a diagram teljes renderelése előtt mentették el. | Hívd meg a `doc.save()`-t **a** diagram módosításainak **összes** elvégzése után. |
| **A szelet értékek nem adódnak össze 100 %-ra** | Nyers számok hozzáadása, amelyek nem százalékot képviselnek, váratlan skálázáshoz vezethet. | Adj meg olyan értékeket, amelyek logikusan egy egész részeit jelentik, vagy hagyd, hogy az Aspose.Words automatikusan kiszámolja a százalékokat. |
| **A forgatás nem hat** | `ChartType.DOUGHNUT` használata `holeSize` beállítása nélkül elrejtheti a forgatás hatását. | Tartsd a diagramot `PIE` típusúként, vagy állítsd be a `holeSize`-t a szög beállítása után. |
| **Fájlútvonal hibák** | A relatív útvonalak Windows és Linux rendszerek között eltérően kerülhetnek feloldásra. | Használd a `Paths.get("output", "PieChart.docx").toString()`-t vagy egy abszolút útvonalat a produkciós kódban. |

### Tippek a produkciós használathoz

* **Használd újra a `DocumentBuilder`-t** – ugyanabban a dokumentumban több diagramot is beszúrhatsz az `insertChart` ismételt meghívásával.  
* **Stílus** – használd a `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`-t, hogy a százalékokat közvetlenül a diagramon jelenítsd meg.  
* **Teljesítmény** – generáld le a diagramot egyszer, és klónozd (`chart.deepClone()`) ha több helyen is azonos diagramra van szükséged.

## Kördiagram szelet elforgatása – fejlett forgatókönyvek

* **Dinamikus szög** – számold ki a szöget az adatok alapján (pl. a legnagyobb szeletet a tetején kezdődően).  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **Több sorozat** – bár egy kördiagram általában egy sorozattal rendelkezik, az Aspose.Words lehetővé teszi több sorozat hozzáadását a rétegezett kördiagramokhoz. A forgatás továbbra is csak az első sorozatra vonatkozik.

## Összegzés

Most már tudod, hogyan **kördiagramot kell létrehozni Word-ben** Java használatával, hogyan **adjunk sorozat adatokat a diagramhoz**, és hogyan **forgassuk el a kördiagram szeletet** a vizuális hangsúly érdekében. A teljes példa bemutatja a teljes munkafolyamatot – a dokumentum inicializálásától a végső `.docx` fájl mentéséig – így a diagramgenerálást bármely automatizált jelentéskészítő folyamatba beillesztheted.

### Mi a következő?

* Fedezd fel a többi diagramtípust (`ChartType.BAR`, `ChartType.LINE`), hogy bővítsd az automatizálási eszköztáradat.  
* Kombináld a diagramgenerálást **mail merge**-rel, hogy személyre szabott jelentéseket készíts minden címzettnek.  
* Merülj el a **Styling API**-ban (`ChartFormat`, `DataLabel`, `ChartTitle`), hogy a vállalati arculatodnak megfelelően formázd a diagramokat.

Nyugodtan kísérletezz különböző adatkészletekkel, szögekkel és diagramstílusokkal. Boldog kódolást!

## Mit legyen a következő tanulnivalód?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy elsajátíthasd a további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan hozzunk létre oszlopdiagramot az Aspose.Words for Java segítségével](/words/english/java/document-conversion-and-export/using-charts/)
- [Hogyan hozzunk létre űrlapmezőket és adjunk tartalmat a DocumentBuilder használatával az Aspose.Words for Java-ban](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Hogyan konvertáljuk a Word-et PDF-be az Aspose.Words for Java használatával](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}