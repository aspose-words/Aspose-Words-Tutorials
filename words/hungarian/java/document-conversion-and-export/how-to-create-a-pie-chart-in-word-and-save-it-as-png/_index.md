---
category: general
date: 2026-10-07
description: Tanulja meg, hogyan készítsen kördiagramot a Wordben, adjon hozzá adatcsoportokat,
  és mentse a diagramot PNG formátumban Java segítségével. Kövesse a lépésről‑lépésre
  útmutatót a gyors eredményekért.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: hu
lastmod: 2026-10-07
og_description: 'Készítsen gyorsan kördiagramot Wordben: ez a tutorial bemutatja,
  hogyan adjon hozzá adat sorozatokat, hozza létre a diagramot, és mentse a Word-diagramot
  képként (PNG). Kövesse a teljes kódrészletet.'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: Kördiagram létrehozása Wordben és exportálása PNG formátumba – útmutató
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: Hogyan készítsünk kördiagramot a Wordben, és mentsük PNG formátumban
url: /hu/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan készítsünk kördiagramot a Wordben, és mentsük PNG-ként

Ha **kördiagram** objektumokat kell létrehoznod egy Microsoft Word fájlban, ez az útmutató pontosan megmutatja, hogyan teheted ezt Java-val. Emellett megtanulod, hogyan **adj hozzá adat sorozatokat** a diagramhoz és **mentsd a diagramot PNG-ként**, hogy a vizuális elemet a Wordön kívül is felhasználhasd.

Diagram közvetlenül a dokumentumban történő generálása megkímél attól, hogy adatokat exportálj egy külön grafikai eszközbe. A tutorial végére egy teljesen működő Word fájlod lesz, amely tartalmaz egy kördiagramot és egy hozzá illő PNG képet a lemezen.

## Előfeltételek

* Java 17 vagy újabb telepítve.
* A **GroupDocs.Viewer for Java** (vagy egy kompatibilis könyvtár, amely biztosítja a `Document`, `Chart`, `ChartType` és `ImageSaveOptions` osztályokat).
* Egy Maven vagy Gradle projekt, ahol hozzáadhatod a könyvtár függőségét.
* Egy bemeneti Word dokumentum (`input.docx`), amely egy olyan mappában található, amelyre a kódból hivatkozhatsz.

Ha Maven-t használsz, add hozzá a függőséget (cseréld le a `VERSION`-t a legújabb kiadásra):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## Hogyan készítsünk kördiagramot a Wordben

A megoldás központja három művelet köré épül:

1. Töltsd be a forrás `.docx` fájlt.
2. **Adj hozzá adat sorozatot** egy új `Chart` objektumhoz, amelynek típusa `PIE`.
3. **Mentsd a diagramot PNG-ként**, hogy a Word dokumentum mellett egy képfájlt kapj.

Az egyes lépéseket részletesen magyarázzuk, majd a szükséges pontos Java kódot is megadjuk.

### 1. lépés: A forrás dokumentum betöltése

Meg kell nyitnod a Word fájlt, amely a diagramot fogja tartalmazni. A `Document` osztály beolvassa a `.docx` tartalmat a memóriába.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Miért fontos*: A dokumentum betöltése egy módosítható modellt hoz létre. Az összes későbbi diagramművelet ezt a memóriában lévő reprezentációt módosítja, amelyet később visszaírhatsz a lemezre.

### 2. lépés: Adat sorozat hozzáadása a diagramhoz

Egy **kördiagram** létrehozása egy `Chart` példánnyal kezdődik. A konstruktor megkapja a szülő `Document`-et és a diagram típusát (`ChartType.PIE`). Miután a diagram objektum létezik, numerikus értékekkel és opcionális címkékkel töltheted fel.

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*Miért fontos*: Az `add` metódus **adat sorozatot ad hozzá** a diagramhoz. A `values` minden eleme egy szeletet jelent a körben, míg a `categories` a jelmagyarázat címkéit biztosítja. Tetszőleges számú pontot megadhatsz; a könyvtár automatikusan kiszámítja a szeletek szögeit.

### 3. lépés: Diagram mentése PNG-ként

Miután a diagram a dokumentum része, exportálhatod a vizuális ábrát. A diagram alapobjektum `save` metódusa egy PNG fájlt ír a fájlrendszerre.

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*Miért fontos*: A diagram PNG-ként való mentése egy raszteres képet ad, amely beágyazható weboldalakba, e‑mail üzenetekbe vagy jelentésekbe anélkül, hogy az eredeti Word fájlra szükség lenne. Az `ImageSaveOptions` objektum lehetővé teszi a formátum, felbontás és egyéb export beállítások szabályozását.

## Kördiagram generálása a Wordben – a megjelenés testreszabása

Az alaplépések mellett előfordulhat, hogy testre szeretnéd szabni a színeket, címeket vagy adatcímkéket. A legtöbb könyvtár egy `ChartOptions` vagy hasonló objektumot biztosít. Íme egy gyors példa, amely címet ad hozzá és megváltoztatja a szeletek színeit:

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

Ezek a testreszabások opcionálisak, de bemutatják, hogyan **generálhatsz kördiagramot a Wordben**, amely megfelel a márkádnak.

## Word diagram mentése képként – alternatív megközelítések

Ha csak a képre van szükséged, a diagramot a dokumentumban nem kell elhelyezned, és a diagram létrehozása után közvetlenül meghívhatod a `save` metódust. A kód változatlan marad; egyszerűen kihagyod azokat a lépéseket, amelyek a diagramot a dokumentum törzsébe illesztik.

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

Ez a technika akkor hasznos, ha sok diagramot generálsz egy kötegelt folyamatban, és csak a PNG kimenet érdekel.

## Teljes futtatható példa

Másold a következő osztályt a projektedbe, állítsd be a fájl útvonalakat, és futtasd. A program a következőket fogja:

1. Betölti az `input.docx`-t.
2. **Létrehoz egy kördiagramot**, **adat sorozatot ad hozzá**, és beágyazza a dokumentumba.
3. **Mentse a diagramot PNG-ként** (`radial.png`).
4. A módosított Word fájlt elmenti `output.docx` néven.



## Mit érdemes legközelebb megtanulni?

A következő tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy elsajátíthasd a további API funkciókat és alternatív megvalósítási módokat a saját projektjeidben.

- [Hogyan készítsünk oszlopdiagramot az Aspose.Words for Java használatával](/words/english/java/document-conversion-and-export/using-charts/)
- [Word szórásdiagram létrehozása az Aspose.Words for .NET használatával](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Oszlopdiagram beszúrása Wordbe az Aspose.Words for .NET használatával](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}