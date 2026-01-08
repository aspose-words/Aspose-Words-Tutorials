---
date: 2025-12-13
description: Ismerje meg, hogyan hozhat létre oszlopdiagramot és formázhatja a diagram
  adatcímkéit az Aspose.Words for Java segítségével. Fedezze fel több sorozat hozzáadását,
  a tengely típusának módosítását és a diagramtengely elrejtését.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Hogyan készítsünk oszlopdiagramot az Aspose.Words for Java használatával
url: /hu/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan hozzunk létre oszlopdiagramot az Aspose.Words for Java segítségével

Ebben az útmutatóban **oszlopdiagramot** fogsz létrehozni közvetlenül a Word‑dokumentumokban az Aspose.Words for Java használatával. Bemutatjuk, hogyan hozhatsz létre különböző diagramtípusokat, hogyan adhatod hozzá több sorozatot, hogyan formázhatod a diagram adatcímkéket, hogyan változtathatod meg a tengely típusát, és akár hogyan rejtheted el a diagram tengelyét, ha letisztultabb megjelenést szeretnél. A végére egy stabil, termelés‑kész megközelítést kapsz a gazdag diagramok beágyazásához a dokumentumaidba.

## Gyors válaszok
- **Mi a fő osztály egy diagram felépítéséhez?** `DocumentBuilder` a `insertChart` metódussal.
- **Melyik metódus ad hozzá új sorozatot?** `chart.getSeries().add(...)`.
- **Hogyan formázhatom a diagram adatcímkéket?** Használd a `getDataLabels().get(...).getNumberFormat().setFormatCode(...)` hívást.
- **Elrejthetek egy tengelyt?** Igen, hívd meg a `setHidden(true)` metódust a tengely objektumon.
- **Szükség van licencre az Aspose.Words‑hez?** Licenc szükséges a termelési környezetben; ingyenes próba elérhető.

## Mi az az oszlopdiagram, és miért használjuk?

Az oszlopdiagram a kategóriákat függőleges sávokként jeleníti meg, így ideális az értékek csoportok közötti összehasonlításához (pl. értékesítés régiónként, havi kiadások stb.). Java‑alkalmazásokban az Aspose.Words segítségével generált oszlopdiagram közvetlenül beágyazható a Word / DOCX fájlokba anélkül, hogy Excelre vagy külső eszközökre lenne szükség.

## Hogyan hozzunk létre oszlopdiagramot

Az alábbi egyszerű példa egy alap oszlopdiagramot hoz létre. A kód megegyezik az eredeti snippet‑kel – csak magyarázó megjegyzéseket adtunk hozzá, hogy könnyebben követhető legyen.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Delete default generated series.
chart.getSeries().clear();

// Creating categories and adding data.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

### Több sorozat hozzáadása

**Több sorozatot** adhatsz hozzá egy oszlopdiagramhoz a `chart.getSeries().add(...)` ismételt meghívásával, ahogyan a fenti példában látható. Minden sorozat saját kategória‑ és értékkészlettel rendelkezhet, lehetővé téve több adathalmaz oldal‑oldali összehasonlítását.

## Hogyan hozzunk létre vonaldiagramot egyedi adatcímkékkel

Ha vonaldiagramra van szükséged az oszlopdiagram helyett, ugyanaz a minta alkalmazható. Ez a példa bemutatja, hogyan **formázhatod a diagram adatcímkéket** különböző számformátumokkal.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Delete default generated series.
chart.getSeries().clear();

// Adding a series with data and data labels.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Or link format code to a source cell.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

### Adatcímkék hozzáadása

A `series1.hasDataLabels(true)` **adatcímkéket ad** a sorozathoz, míg a `setShowValue(true)` megjeleníti a tényleges értékeket a diagramon.

## Hogyan változtassuk meg a tengely típusát és testre szabjuk a tengely tulajdonságait

A tengely típusának módosítása (pl. dátumtól kategóriáig) lehetővé teszi, hogy szabályozd, hogyan kerülnek ábrázolásra az adatpontok. Ez a snippet azt is mutatja, hogyan **rejtsd el a diagram tengelyét**, ha minimalista megjelenést szeretnél.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Change the X axis to be a category instead of date.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Measured in display units of the Y axis (hundreds).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

// Example of hiding the Y axis.
yAxis.setHidden(true);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### Tengely típusának módosítása

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **módosítja a tengely típusát** egy dátumalapú tengelyről kategóriálisra, így teljes kontrollt kapsz a címkék elhelyezése felett.

## Hogyan formázzuk a diagram adatcímkéket (számformátumok)

A számformátumok közvetlenül a tengelyre vagy az adatcímkékre alkalmazhatók. Ez a példa az Y‑tengely számait ezres elválasztóval formázza.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## További diagram testreszabások

Az alapok mellett beállíthatod a határokat, meghatározhatod a címkék közötti intervallum egységeket, elrejtheted a specifikus tengelyeket, és még sok mást. Tekintsd meg az Aspose.Words for Java API dokumentációját a teljes tulajdonságlistáért.

## Gyakran ismételt kérdések

**K: Hogyan adhatok hozzá több sorozatot egy diagramhoz?**  
V: Használd a `chart.getSeries().add()` metódust minden egyes sorozathoz, amelyet meg szeretnél jeleníteni. Minden hívás megadhat egyedi nevet, kategória‑tömböt és érték‑tömböt.

**K: Hogyan formázhatom a diagram adatcímkéket egyedi számformátumokkal?**  
V: Szerezz hozzá egy sorozat `DataLabels` objektumához, majd hívd meg a `getNumberFormat().setFormatCode("your format")` metódust. A formátumot összekapcsolhatod egy forráscellával a `isLinkedToSource(true)` segítségével is.

**K: Hogyan rejthetem el egy diagram tengelyét?**  
V: Hívd meg a `setHidden(true)` metódust a kívánt `ChartAxis` objektumon (pl. `chart.getAxisY().setHidden(true)`).

**K: Mi a legjobb módja a tengely típusának módosítására?**  
V: Használd a `setCategoryType(AxisCategoryType.CATEGORY)`-t a kategóriális tengelyekhez, vagy az `AxisCategoryType.DATE`-t a dátumtengelyekhez.

**K: Hogyan adhatok adatcímkéket egy sorozathoz?**  
V: Engedélyezd őket a `series.hasDataLabels(true)` hívással, majd állítsd be a láthatóságot a `series.getDataLabels().setShowValue(true)` metódussal.

## Összegzés

Mindezt lefedtük, ami ahhoz szükséges, hogy **oszlopdiagramot** hozz létre az Aspose.Words for Java‑val – az alap diagramok beszúrásától a több sorozatos ábrákon át a diagram adatcímkék formázásáig, a tengely típusának módosításáig és a tengelyek elrejtéséig egy tiszta megjelenés érdekében. Alkalmazd ezeket a technikákat jelentés‑ vagy dokumentum‑generálási folyamataidban, hogy professzionális, adat‑vezérelt Word‑dokumentumokat szállíts.

---

**Utoljára frissítve:** 2025-12-13  
**Tesztelve a következővel:** Aspose.Words for Java 24.12 (legújabb)  
**Szerző:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}