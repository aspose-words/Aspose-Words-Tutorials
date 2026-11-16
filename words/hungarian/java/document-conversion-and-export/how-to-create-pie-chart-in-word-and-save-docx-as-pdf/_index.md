---
category: general
date: 2026-11-15
description: Tanulja meg, hogyan hozhat létre kördiagramot egy Word-dokumentumban,
  és hogyan mentheti a docx-et PDF-ként Java használatával. Ez az útmutató a Word
  PDF-re konvertálását és a diagram hozzáadását is bemutatja.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: hu
lastmod: 2026-11-15
og_description: Készíts kördiagramot egy Word‑fájlban, és mentsd el a docx‑et PDF‑ként
  Java‑val. Kövesd ezt a lépésről‑lépésre útmutatót a Word PDF‑re konvertálásához
  és a diagramok hozzáadásához.
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: Kördiagram létrehozása Wordben és a docx mentése PDF-ként – Java útmutató
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: Hogyan készítsünk kördiagramot a Wordben, és mentsük a docx fájlt PDF‑ként
url: /hu/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan készítsünk kördiagramot Word-ben és mentsük a docx-et PDF-ként

Ha **kördiagramot** kell létrehoznod egy Word dokumentumban, majd **docx-et PDF-ként menteni**, ez a bemutató pontosan megmutatja, hogyan. Egy teljes, futtatható példát láthatsz, amely egy .docx fájlt PDF-re konvertál, miközben beágyaz egy kördiagramot, így a “hogyan adjunk hozzá diagramot” kérdésre válaszolhatsz anélkül, hogy szétszórt kódrészleteket kellene keresned.

Ebben az útmutatóban megtanulod:

* Egy meglévő *.docx* betöltése (vagy teljesen új létrehozása)  
* Az Aspose.Words for Java használata **kördiagramot létrehozni** és adatokat feltölteni  
* **docx mentése PDF-ként** a diagram helyes megjelenítésével  
* A **Word PDF-re konvertálása** finomságainak megértése diagramok esetén  

A lépések az Aspose.Words 2024‑x.x és a Java 17 verzióval működnek, de a koncepciók bármely, Word diagramkezelést támogató könyvtárra alkalmazhatók.

## Előfeltételek

Mielőtt elkezdenéd, győződj meg róla, hogy rendelkezel:

| Követelmény | Miért fontos |
|-------------|----------------|
| Java 17 (vagy újabb) | A legújabb Aspose.Words JAR által megkövetelt |
| Maven vagy Gradle build eszköz | Egyszerűsíti a függőségkezelést |
| Aspose.Words for Java (legújabb verzió) | Provides `Document`, `Chart`, and `ChartType` classes |
| Egy bemeneti **.docx** fájl (vagy egy üres dokumentum) | A diagram ebbe a fájlba lesz beillesztve |

Add the Aspose.Words dependency to your `pom.xml` (Maven) or `build.gradle` (Gradle). Example for Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## 1. lépés: Word dokumentum betöltése (vagy új létrehozása)

Az első művelet egy `Document` példány beszerzése. Ha már van sablonod, add meg az útvonalát; egyébként hozz létre egy üres dokumentumot.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*Miért ez a lépés?* A `Document` objektum a Word tartalom minden elemének tárolója, beleértve a diagramokat is. Egy meglévő fájl betöltése lehetővé teszi a környező szöveg és stílusok megőrzését, miközben új vizuális elemet adsz hozzá.

## 2. lépés: **Kördiagram létrehozása** – a “hogyan készítsünk diagramot” lényege

Most egy `Chart` objektumot hozunk létre a `ChartType.PIE` segítségével. Ez automatikusan létrehoz egy kördiagram helyőrzőt, amelyet később adatokal tölthetsz fel.

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*Magyarázat*: `ChartType.PIE` azt mondja az Aspose.Words-nek, hogy egy kördiagram sablont használjon. A diagram a dokumentum törzséhez kerül hozzáadásra, így ott jelenik meg, ahol szükséged van rá. Ez egyetlen hívással kielégíti a “hogyan adjunk hozzá diagramot” követelményt.

## 3. lépés: Diagram feltöltése – a “hogyan adjunk hozzá diagramot” kérdés megválaszolása adatokkal

Egy kördiagram értelmetlen sorozatadatok nélkül. Használd a `Series` gyűjteményt kategóriák és értékek hozzáadásához.

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*Miért fontos*: Minden `add` hívás egy szeletet hoz létre a körben. Az első argumentum a címke, a második a numerikus érték. Ezeket helyettesítheted dinamikus adatokkal egy adatbázisból vagy CSV fájlból.

### Opcionális: Megjelenés testreszabása (nem kötelező, de hasznos)

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

Ezek a finomhangolások bemutatják, hogyan készíthetsz **diagramot létrehozni** professzionális megjelenéssel, anélkül, hogy elhagynád a Java kódot.

## 4. lépés: **docx mentése PDF-ként** – a “Word PDF-re konvertálása” végső része

Miután a diagram beágyazásra került, exportáld a dokumentumot PDF-be. Az Aspose.Words a diagramot vektorgrafikaként rendereli, megőrizve a minőséget.

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*Fontos pont*: A `save` metódus automatikusan konvertálja a Word fájlt PDF-re, kezelve a diagram rasterizálását, betűtípus beágyazását és az oldalelrendezést. Ez teljesíti a **docx mentése pdf** célt, és megbízható módot mutat be a **Word PDF-re konvertálása** megvalósítására diagramok jelenléte esetén.

### Várható kimenet

A program futtatása `output.pdf`-t hoz létre, amely tartalmaz:

* Az `input.docx` eredeti tartalmát (ha van)  
* Egy teljesen renderelt kördiagramot a *Sales Distribution Q1* címmel  
* Pontos szelet százalékokat, amelyek egyeznek az adatokkal (40 %, 30 %, 30 %)

Nyisd meg a PDF-et bármely megjelenítőben, és egy tiszta kördiagramot kell látnod, amely azonos a Word fájlban láthatóval.

## Gyakori hibák és hogyan kerüld el őket

| Probléma | Oka | Megoldás |
|----------|-----|----------|
| A diagram üresen jelenik meg a PDF-ben | Hiányzó betűtípus vagy diagram renderelési beállítások | Győződj meg róla, hogy a legújabb Aspose.Words verziót használod; ez tartalmazza a szükséges renderelési könyvtárakat. |
| Az adatértékek helytelenül kerekítődnek | Egész számok használata nagy számok esetén | Használj `double` értékeket vagy skálázd a számokat, mielőtt a sorozathoz adnád őket. |
| A kimeneti PDF hatalmas | Képek beágyazása magas DPI-vel | Állítsd be a `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)`-t, ha képeket is beágyazol. |
| A “Word PDF-re konvertálása” `UnsupportedOperationException`-t dob | Régebbi Java verzió (< 11) használata | Frissíts Java 17-re vagy újabbra, amit az Aspose.Words 24.x megkövetel. |

## Profi tipp: A diagramkészítő logika újrahasználata

Ha több diagramot kell hozzáadnod ugyanahhoz a dokumentumhoz, vedd ki a diagramépítő kódot egy segédmetódusba:

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

Ezután meghívhatod a `doc.getFirstSection().getBody().appendChild(createPieChart(...));`-t minden adatkészlethez, így a kódod DRY (Don’t Repeat Yourself) marad.

## Összegzés

Most már tudod, hogyan **kördiagramot** készíts egy Word dokumentumban, töltsd fel adatokal, és **docx-et PDF-ként** ments Java segítségével. Ez az end‑to‑end példa lefedi a teljes **Word PDF-re konvertálása** munkafolyamatot, megválaszolja a **hogyan adjunk hozzá diagramot** kérdést, és bemutatja a **diagramot létrehozni** programozottan.  

Innen tovább felfedezheted:

* Oszlop- vagy vonaldiagramok hozzáadása (`ChartType.BAR`, `ChartType.LINE`) – egy másik **diagramot létrehozni** szcenárió.  
* Exportálás más formátumokba, például PNG vagy HTML (`SaveFormat.PNG`, `SaveFormat.HTML`).  
* Dinamikus bemeneti dokumentum generálása táblázatokkal vagy helyőrzőkkel a diagramok beszúrása előtt.

Nyugodtan kísérletezz különböző adatkészletekkel, stílusbeállításokkal, vagy akár több diagram egy oldalon való beágyazásával. Boldog kódolást!

## Mit érdemes legközelebb megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan illesszünk be kördiagramot egy Word dokumentumba Java használatával](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [Hogyan mentsünk Word dokumentumot PDF-ként és hozzunk létre hozzáférhető PDF-et Java-ban](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [Hogyan készítsünk diagramot Word-ben Java és Aspose.Words segítségével](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}