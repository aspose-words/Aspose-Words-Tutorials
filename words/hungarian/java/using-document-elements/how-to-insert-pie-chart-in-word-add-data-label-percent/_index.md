---
category: general
date: 2026-07-20
description: Hogyan illesszünk be kördiagramot a Wordbe az Aspose.Words segítségével.
  Tanulja meg, hogyan adjon hozzá adatcímke százalékot, és jelenítse meg a százalékokat
  a diagramon professzionális dokumentumokhoz.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: hu
lastmod: 2026-07-20
og_description: Hogyan szúrjunk be kördiagramot a Word dokumentumba az Aspose.Words
  segítségével. Ez az útmutató megmutatja, hogyan adhatunk hozzá adatcímke százalékot,
  és hogyan jeleníthetünk meg százalékokat a diagramon néhány sorban.
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: hogyan illessz be kördiagramot a Wordben – gyors útmutató
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: Hogyan szúrjunk be kördiagramot a Wordben – adatcímke százalék hozzáadása
url: /hu/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hogyan szúrjunk be kördiagramot Word-be – adatcímke százalék hozzáadása

Gondoltad már valaha, **hogyan szúrjunk be kördiagramot** egy Word dokumentumba anélkül, hogy a felhasználói felülettel küzdenél? Nem vagy egyedül. Sok jelentéskészítési helyzetben szükség van a *kördiagram Word-be való hozzáadására*, és ami még fontosabb, **a százalék megjelenítésére a kördiagramon**, hogy az olvasók azonnal megértsék az adatmegoszlást.

Ebben az útmutatóban végigvezetünk a teljes folyamaton az Aspose.Words for Java használatával. A végére pontosan tudni fogod, hogyan **adjunk hozzá adatcímke százalékot**, **jelenítsünk meg százalékokat a diagramon**, és hogyan kapjunk egy kifinomult kördiagramot, ami már az első alkalommal helyes. Nincs szükség extra pluginekre, manuális beállításokra – csak tiszta kód, amelyet bármely projektbe beilleszthetsz.

---

## Előfeltételek

- Java 17 (vagy újabb) – a jelenlegi LTS verzió, amelyet az Aspose.Words támogat.
- Aspose.Words for Java 24.x (a legújabb a írás időpontjában, 2026. július).
- Alap Maven vagy Gradle beállítás a könyvtár lehívásához.
- Kedvenc IDE-d (IntelliJ IDEA, Eclipse, VS Code… bármelyik megfelel).

Ha már mindezek megvannak, nagyszerű – merüljünk el.

## 1. lépés: A projekt beállítása és a könyvtár importálása

Először add hozzá az Aspose.Words függőséget a `pom.xml` (Maven) vagy `build.gradle` (Gradle) fájlodhoz. Ez hozzáférést biztosít a `Document`, `DocumentBuilder` és a diagram osztályokhoz.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tipp:** Tartsd naprakészen a verziószámot; az újabb kiadások gyakran hoznak diagramokkal kapcsolatos javításokat, amelyek megbízhatóbbá teszik a **százalékok megjelenítését a diagramon**.

## 2. lépés: Új Word dokumentum és builder létrehozása

A builder a svájci bicskád a tartalom beszúrásához. Itt létrehozunk egy új dokumentumot, és csatolunk hozzá egy `DocumentBuilder`‑t.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Miért van szükségünk egy builderre? Absztrahálja az alacsony szintű OpenXML struktúrákat, így a *mi* szeretnénk—például **kördiagram hozzáadása Word-hez**—helyett a *hogyan* néz ki az XML.

## 3. lépés: A kördiagram beszúrása

Most jön a **hogyan szúrjunk be kördiagramot** lényege. A buildert arra kérjük, hogy egy adott méretű kördiagramot helyezzen el. A méretek pontban vannak megadva (1 pt ≈ 1/72 in).

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

Ebben a pontban a diagram üres, de a helyfoglaló már a dokumentumban van. Így **programozottan hozzáadtad a kördiagramot Word-hez**.

## 4. lépés: A diagram feltöltése adatokkal

A kördiagramnak legalább egy értékcsaládra van szüksége. Töltsük fel néhány mintaadatával, amely a piaci részesedést mutatja.

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

Ha több sorozatra van szükséged (halmozott körök, gyűrűdiagramok stb.), meghívhatod a `pieChart.getSeries().add()`‑t, és ismételheted a lépéseket. Ugyanez a logika érvényes, amikor **százalékokat szeretnél megjeleníteni a diagramon** minden szelethez.

## 5. lépés: **adatcímke százalék hozzáadása** – a százalékok megjelenítése a szeleteken

Ez a rész, amit a legtöbb fejlesztő elfelejt: a adatcímkék konfigurálása a százalékok megjelenítéséhez. Enélkül a diagram csak nyers számokat mutat, ami félreérthető lehet.

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

A `setShowPercent(true)` hívás azt mondja az Aspose.Words‑nek, hogy a címkét „30 %”, „45 %” stb. formában jelenítse meg. Pontosan így **mutathatod a százalékot a kördiagramon** extra formázás nélkül.

## 6. lépés: Dokumentum mentése

Végül írd a dokumentumot a lemezre. Választhatsz `.docx`, `.pdf` vagy akár `.html` formátumot. Ebben az útmutatóban a modern `.docx` formátumot használjuk.

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

Futtasd a programot, nyisd meg a `PieChartDemo.docx` fájlt, és egy szép renderelt kördiagramot látsz, amelynek minden szeletén százalékcímkék vannak.

## Várható kimenet

Az alábbi képernyőkép a generált Word fájlt mutatja. Figyeld meg, hogy minden szelet a részesedését százalékban jeleníti meg – pontosan azt, amit a **adatcímke százalék hozzáadása** beállításakor szerettünk volna.

![Képernyőkép egy Word dokumentumról, amely kördiagramot százalékcímkékkel tartalmaz](/images/pie-chart-percent.png){.center width=600px alt="Képernyőkép, amely bemutatja, hogyan szúrjunk be kördiagramot Word-be százalékcímkékkel"}

*Az alt szöveg tartalmazza az elsődleges kulcsszót, ezzel kielégítve mind az SEO‑t, mind a hozzáférhetőséget.*

## Gyakori kérdések és szél‑eset kezelése

| Question | Answer |
|----------|--------|
| **Meg tudom változtatni a százalékcímkék betűtípusát?** | Igen. A `setShowPercent(true)` engedélyezése után szerezd meg a `DataLabel` objektumot, és állítsd be a `Font` tulajdonságát (`dataLabel.getFont().setSize(10);`). |
| **Mi van, ha gyűrűdiagramra van szükségem a kördiagram helyett?** | Cseréld le a `ChartType.PIE`-t `ChartType.DOUGHNUT`-ra az `insertChart` hívásban. Az ugyanaz a **adatcímke százalék hozzáadása** logika működik. |
| **Megjelennek-e a százalékok helyesen a régebbi Word verziókban (2007‑2010)?** | Az Aspose.Words a háttér‑XML‑t verziófüggetlen módon írja, így a százalékok megjelennek minden olyan Wordben, amely támogatja a diagramokat (2007+). |
| **Hogyan adhatok címet a diagramhoz?** | Használd a `pieChart.getTitle().setText("Market Share");` kódot a mentés előtt. |
| **Beszúrhatom a diagramot egy adott bekezdésbe vagy táblázatcellába?** | Természetesen. Mozgasd a `DocumentBuilder`‑t a kívánt helyre (`builder.moveToParagraph(index, true);` vagy `builder.moveToCell(table, row, column, true);`) az `insertChart` hívása előtt. |

## Tippek és trükkök a gyakorlatból

- **Pro tipp:** Ha sok diagramot szeretnél egy ciklusban generálni, használd újra ugyanazt a `DocumentBuilder` példányt; ez csökkenti a memóriahasználatot.
- **Figyelj:** Nagyon kis szeletek (< 2 %). Az Aspose.Words kihagyhatja a címkét a zsúfoltság elkerülése érdekében; kényszerítheted a `dataLabel.setShowLabel(true);` használatával.
- **Teljesítményjegyzet:** A diagram renderelése CPU‑igényes. Tömeges jelentéskészítés esetén fontold meg a több szálas feldolgozást, de győződj meg róla, hogy minden szál a saját `Document` példányán dolgozik.
- **Verzióellenőrzés:** A `setShowPercent` metódus az Aspose.Words 22.8‑ban került bevezetésre. Ha régebbi verziót használsz, frissíts, vagy számold ki manuálisan a százalékokat, és állítsd be egyéni címkeként.

## Összefoglalás

Áttekintettük, **hogyan szúrjunk be kördiagramot** egy Word dokumentumba az Aspose.Words segítségével, megmutattuk, hogyan **adjunk hozzá adatcímke százalékot**, és bemutattuk a legegyszerűbb módot a **százalékok megjelenítésére a diagramon**. Néhány Java sorral **kördiagramot adhatunk hozzá Word-hez** és **százalékot jeleníthetünk meg a kördiagramon**, így a nyers számok azonnal olvasható vizuálissá válnak.

## Mi a következő lépés?

- Kísérletezz más diagramtípusokkal (`BAR`, `LINE`, `AREA`), és nézd meg, hogyan alkalmazható ugyanaz a **adatcímke százalék hozzáadása** logika.
- Kombináld a diagramokat táblázatokkal a gazdagabb jelentésekért – az Aspose.Words egyszerűvé teszi a diagram elhelyezését egy adat táblázat mellett.
- Fedezd fel a dokumentum PDF‑ vagy HTML‑formátumba való exportálását, hogy lásd, hogyan jelennek meg a százalékok a különböző formátumokban.

Nyugodtan módosítsd a méreteket, színeket vagy az adatforrást (pl. adatbázis lekérdezés), és nézd, ahogy a Word jelentéseid életre kelnek. Ha elakadsz, hagyj megjegyzést alább – jó diagramkészítést!

## Mit érdemes legközelebb megtanulni?

A következő útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljes, működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Oszlopdiagram beszúrása Word-be az Aspose.Words for .NET használatával](/words/english/net/working-with-charts/insert-column-chart/)
- [Területdiagram beszúrása Word dokumentumba | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Buborékdiagram beszúrása Word-be az Aspose.Words for .NET használatával](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}