---
title: Diagramok használata az Aspose.Words for Java programban
linktitle: Diagramok használata
second_title: Aspose.Words Java Document Processing API
description: Ismerje meg, hogyan hozhat létre és testreszabhat diagramokat az Aspose.Words for Java programban. Fedezze fel a diagramtípusokat, a formázást és a tengelytulajdonságokat az adatok megjelenítéséhez.
weight: 12
url: /hu/java/document-conversion-and-export/using-charts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Diagramok használata az Aspose.Words for Java programban


## Bevezetés a diagramok használatába az Aspose.Words for Java programban

Ebben az oktatóanyagban megvizsgáljuk, hogyan dolgozhatunk diagramokkal az Aspose.Words for Java használatával. Megtanulja, hogyan hozhat létre különféle típusú diagramokat, hogyan testreszabhatja a tengely tulajdonságait, formázhatja az adatcímkéket stb. Merüljünk el!

## Vonaldiagram készítése

Vonaldiagram létrehozásához használja a következő kódot:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Alapértelmezett generált sorozat törlése.
chart.getSeries().clear();

// Sorozat hozzáadása adatokkal és adatcímkékkel.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Vagy csatolja a formátumkódot egy forráscellához.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## Más típusú diagramok készítése

Hasonló technikákkal különféle típusú diagramokat hozhat létre, például oszlop-, terület-, buborék-, szórvány- és egyéb diagramokat. Íme egy példa egy egyszerű oszlopdiagram beszúrására:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Alapértelmezett generált sorozat törlése.
chart.getSeries().clear();

// Kategóriák létrehozása és adatok hozzáadása.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## Tengelytulajdonságok testreszabása

Testreszabhatja a tengely tulajdonságait, például módosíthatja a tengely típusát, beállíthatja a pipajeleket, formázhatja a címkéket stb. Íme egy példa az XY tengely tulajdonságainak meghatározására:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Törölje az alapértelmezett sorozatokat, és adja hozzá adatait.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Módosítsa az X tengelyt kategóriára a dátum helyett.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); //Az Y tengely kijelzési egységeiben mérve (száz).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## Adatcímkék formázása

Az adatcímkéket különböző számformátumokkal formázhatja. Íme egy példa:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Törölje az alapértelmezett sorozatokat, és adja hozzá adatait.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## További diagram testreszabások

Tovább testreszabhatja diagramjait a határok, a címkék közötti intervallum egységek beállításával, a diagram tengelyeinek elrejtésével stb. Fedezze fel a megadott kódrészleteket, hogy többet megtudjon ezekről a lehetőségekről.

## Következtetés

Ebben az oktatóanyagban megvizsgáltuk, hogyan dolgozhatunk diagramokkal az Aspose.Words for Java használatával. Megtanulta különféle típusú diagramok létrehozását, a tengelytulajdonságok testreszabását, az adatcímkék formázását stb. Az Aspose.Words for Java hatékony eszközöket biztosít az adatok vizuális megjelenítésének hozzáadásához a dokumentumokhoz, javítva ezzel az információk megjelenítésének módját.

## GYIK

### Hogyan adhatok több sorozatot egy diagramhoz?

 Több sorozatot is hozzáadhat egy diagramhoz a segítségével`chart.getSeries().add()` módszer. Ügyeljen arra, hogy adja meg a sorozat nevét, kategóriáit és adatértékeit.

### Hogyan formázhatom az adatcímkéket egyéni számformátumokkal?

Az adatcímkéket a`DataLabels` egy sorozat tulajdonságait, és állítsa be a kívánt formátumkódot`getNumberFormat().setFormatCode()`.

### Hogyan szabhatom testre a tengely tulajdonságait egy diagramban?

 Testreszabhatja a tengely tulajdonságait, például a típust, a pipajeleket, a címkéket és egyebeket, ha eléri a`ChartAxis` tulajdonságok, mint`setCategoryType()`, `setCrosses()` , és`setMajorTickMark()`.

### Hogyan hozhatok létre más típusú diagramokat, például szóró- vagy területdiagramokat?

 Különféle diagramtípusokat hozhat létre a megfelelő megadásával`ChartType` segítségével a diagram beillesztésekor`builder.insertChart(ChartType.TYPE, width, height)`.

### Hogyan rejthetek el egy diagramtengelyt?

 A diagram tengelyét a beállításával elrejtheti`setHidden(true)` a tengely tulajdonsága.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
