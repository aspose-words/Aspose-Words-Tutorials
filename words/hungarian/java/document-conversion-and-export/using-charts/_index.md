---
"description": "Ismerd meg, hogyan hozhatsz létre és szabhatsz testre diagramokat az Aspose.Words for Java programban. Ismerd meg a diagramtípusokat, a formázást és a tengelytulajdonságokat az adatvizualizációhoz."
"linktitle": "Diagramok használata"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Diagramok használata az Aspose.Words Java-ban"
"url": "/hu/java/document-conversion-and-export/using-charts/"
"weight": 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Diagramok használata az Aspose.Words Java-ban


## Bevezetés a diagramok használatába az Aspose.Words Java-ban

Ebben az oktatóanyagban azt vizsgáljuk meg, hogyan dolgozhatunk diagramokkal az Aspose.Words for Java használatával. Megtanulod, hogyan hozhatsz létre különféle típusú diagramokat, hogyan szabhatod testre a tengelyek tulajdonságait, hogyan formázhatod az adatfeliratokat és még sok mást. Vágjunk bele!

## Vonaldiagram létrehozása

Vonaldiagram létrehozásához használja a következő kódot:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Alapértelmezetten generált sorozat törlése.
chart.getSeries().clear();

// Adatsorok hozzáadása adatokkal és adatcímkékkel.
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

## Más típusú diagramok létrehozása

Különböző típusú diagramokat hozhat létre, például oszlop-, terület-, buborék-, szórt- és egyéb diagramokat hasonló technikákkal. Íme egy példa egy egyszerű oszlopdiagram beszúrására:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Alapértelmezetten generált sorozat törlése.
chart.getSeries().clear();

// Kategóriák létrehozása és adatok hozzáadása.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## Tengelytulajdonságok testreszabása

Testreszabhatja a tengelyek tulajdonságait, például módosíthatja a tengely típusát, beállíthat osztásjeleket, formázhatja a feliratokat és egyebeket. Íme egy példa az XY tengely tulajdonságainak definiálására:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Töröld az alapértelmezett sorozatokat, és add hozzá az adataidat.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Módosítsa az X tengelyt úgy, hogy dátum helyett kategória legyen.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Az Y tengely megjelenítési egységeiben mérve (százas).
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

Az adatfeliratokat különböző számformátumokkal formázhatja. Íme egy példa:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Töröld az alapértelmezett sorozatokat, és add hozzá az adataidat.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## További diagram-testreszabási lehetőségek

A diagramokat tovább testreszabhatja a határok, a címkék közötti intervallumegységek módosításával, a diagramtengelyek elrejtésével és egyebekkel. A mellékelt kódrészletekből többet is megtudhat ezekről a lehetőségekről.

## Következtetés

Ebben az oktatóanyagban azt vizsgáltuk meg, hogyan dolgozhatunk diagramokkal az Aspose.Words for Java segítségével. Megtanultuk, hogyan hozhatunk létre különféle típusú diagramokat, hogyan szabhatjuk testre a tengelytulajdonságokat, hogyan formázhatjuk az adatfeliratokat és egyebeket. Az Aspose.Words for Java hatékony eszközöket biztosít az adatok vizuális ábrázolásainak hozzáadásához a dokumentumokhoz, javítva az információk bemutatásának módját.

## GYIK

### Hogyan adhatok hozzá több adatsort egy diagramhoz?

Több adatsort is hozzáadhat egy diagramhoz a `chart.getSeries().add()` metódus. Feltétlenül adja meg a sorozat nevét, a kategóriákat és az adatértékeket.

### Hogyan formázhatom az adatfeliratokat egyéni számformátumokkal?

Az adatcímkéket a következővel formázhatja: `DataLabels` egy sorozat tulajdonságai és a kívánt formátumkód beállítása a `getNumberFormat().setFormatCode()`.

### Hogyan szabhatom testre a tengelytulajdonságokat egy diagramban?

A tengelyek tulajdonságait, például a típust, az osztásjeleket, a feliratokat és egyebeket testreszabhatja a `ChartAxis` olyan tulajdonságok, mint `setCategoryType()`, `setCrosses()`, és `setMajorTickMark()`.

### Hogyan hozhatok létre más típusú diagramokat, például szóródási vagy területdiagramokat?

Különböző diagramtípusokat hozhat létre a megfelelő megadásával `ChartType` diagram beillesztésekor a következő használatával: `builder.insertChart(ChartType.TYPE, width, height)`.

### Hogyan rejthetek el egy diagramtengelyt?

A diagramtengely elrejtéséhez állítsa be a `setHidden(true)` a tengely tulajdonsága.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}