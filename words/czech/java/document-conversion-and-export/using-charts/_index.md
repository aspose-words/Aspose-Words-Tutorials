---
"description": "Naučte se, jak vytvářet a upravovat grafy v Aspose.Words pro Javu. Prozkoumejte typy grafů, formátování a vlastnosti os pro vizualizaci dat."
"linktitle": "Používání grafů"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Používání grafů v Aspose.Words pro Javu"
"url": "/cs/java/document-conversion-and-export/using-charts/"
"weight": 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Používání grafů v Aspose.Words pro Javu


## Úvod do používání grafů v Aspose.Words pro Javu

V tomto tutoriálu se podíváme na práci s grafy pomocí Aspose.Words pro Javu. Naučíte se, jak vytvářet různé typy grafů, upravovat vlastnosti os, formátovat popisky dat a další. Pojďme se na to pustit!

## Vytvoření spojnicového grafu

Chcete-li vytvořit spojnicový graf, použijte následující kód:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Smazat výchozí generovanou sérii.
chart.getSeries().clear();

// Přidání řady s daty a popisky dat.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Nebo propojte formátovací kód se zdrojovou buňkou.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## Vytváření dalších typů grafů

Pomocí podobných technik můžete vytvářet různé typy grafů, jako jsou sloupcové, plošné, bublinové, bodové a další. Zde je příklad vložení jednoduchého sloupcového grafu:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Smazat výchozí generovanou sérii.
chart.getSeries().clear();

// Vytváření kategorií a přidávání dat.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## Úpravy vlastností os

Vlastnosti os můžete přizpůsobit, například změnit typ osy, nastavit značky zaškrtnutí, formátovat popisky a další. Zde je příklad definování vlastností osy XY:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Vymažte výchozí sérii a přidejte svá data.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Změňte osu X tak, aby zobrazovala kategorii místo data.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Měřeno v jednotkách zobrazení osy Y (stovky).
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

## Formátování popisků dat

Popisky dat můžete formátovat pomocí různých číselných formátů. Zde je příklad:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Vymažte výchozí sérii a přidejte svá data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Další úpravy grafů

Grafy si můžete dále přizpůsobit úpravou hranic, intervalových jednotek mezi popisky, skrytím os grafu a dalšími funkcemi. Prohlédněte si poskytnuté úryvky kódu a dozvíte se o těchto možnostech více.

## Závěr

tomto tutoriálu jsme prozkoumali, jak pracovat s grafy pomocí Aspose.Words pro Javu. Naučili jste se, jak vytvářet různé typy grafů, upravovat vlastnosti os, formátovat popisky dat a další. Aspose.Words pro Javu poskytuje výkonné nástroje pro přidávání vizuálních reprezentací dat do vašich dokumentů a vylepšování způsobu prezentace informací.

## Často kladené otázky

### Jak mohu do grafu přidat více řad?

Do grafu můžete přidat více řad pomocí `chart.getSeries().add()` metoda. Nezapomeňte zadat název řady, kategorie a datové hodnoty.

### Jak mohu formátovat popisky dat s vlastními číselnými formáty?

Štítky dat můžete formátovat přístupem k `DataLabels` vlastnosti řady a nastavení požadovaného formátovacího kódu pomocí `getNumberFormat().setFormatCode()`.

### Jak mohu přizpůsobit vlastnosti osy v grafu?

Vlastnosti osy, jako je typ, značky zaškrtnutí, popisky a další, můžete přizpůsobit přístupem k `ChartAxis` vlastnosti jako `setCategoryType()`, `setCrosses()`a `setMajorTickMark()`.

### Jak mohu vytvořit jiné typy grafů, jako například bodové nebo plošné grafy?

Můžete vytvořit různé typy grafů zadáním příslušných `ChartType` při vkládání grafu pomocí `builder.insertChart(ChartType.TYPE, width, height)`.

### Jak mohu skrýt osu grafu?

Osu grafu můžete skrýt nastavením `setHidden(true)` vlastnost osy.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}