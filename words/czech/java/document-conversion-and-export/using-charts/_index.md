---
title: Použití grafů v Aspose.Words pro Javu
linktitle: Použití grafů
second_title: Aspose.Words Java Document Processing API
description: Naučte se vytvářet a přizpůsobovat grafy v Aspose.Words pro Java. Prozkoumejte typy grafů, formátování a vlastnosti os pro vizualizaci dat.
weight: 12
url: /cs/java/document-conversion-and-export/using-charts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Použití grafů v Aspose.Words pro Javu


## Úvod do používání grafů v Aspose.Words pro Javu

tomto tutoriálu prozkoumáme, jak pracovat s grafy pomocí Aspose.Words for Java. Dozvíte se, jak vytvářet různé typy grafů, přizpůsobovat vlastnosti os, formátovat štítky dat a další. Pojďme se ponořit!

## Vytvoření spojnicového grafu

Chcete-li vytvořit spojnicový graf, použijte následující kód:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Smazat výchozí vygenerované série.
chart.getSeries().clear();

// Přidání řady s daty a datovými štítky.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Nebo propojte kód formátu se zdrojovou buňkou.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## Vytváření jiných typů grafů

Pomocí podobných technik můžete vytvářet různé typy grafů, jako jsou sloupcové, plošné, bublinové, bodové a další. Zde je příklad vložení jednoduchého sloupcového grafu:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Smazat výchozí vygenerované série.
chart.getSeries().clear();

// Vytváření kategorií a přidávání dat.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## Přizpůsobení vlastností osy

Můžete přizpůsobit vlastnosti osy, jako je změna typu osy, nastavení značek, formátování štítků a další. Zde je příklad definování vlastností osy XY:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Vymažte výchozí řadu a přidejte svá data.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Změňte osu X na kategorii namísto data.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); //Měřeno v zobrazovacích jednotkách osy Y (stovky).
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

## Formátování datových štítků

Datové štítky můžete formátovat s různými formáty čísel. Zde je příklad:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Vymažte výchozí řadu a přidejte svá data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Další přizpůsobení grafu

Své grafy můžete dále přizpůsobit úpravou hranic, jednotek intervalu mezi štítky, skrytím os grafu a dalšími. Prozkoumejte poskytnuté fragmenty kódu a zjistěte více o těchto možnostech.

## Závěr

V tomto tutoriálu jsme prozkoumali, jak pracovat s grafy pomocí Aspose.Words for Java. Naučili jste se vytvářet různé typy grafů, přizpůsobovat vlastnosti os, formátovat popisky dat a další. Aspose.Words for Java poskytuje výkonné nástroje pro přidávání vizuálních reprezentací dat do vašich dokumentů, čímž zlepšuje způsob, jakým prezentujete informace.

## FAQ

### Jak mohu do grafu přidat více řad?

 Do grafu můžete přidat více řad pomocí`chart.getSeries().add()` metoda. Nezapomeňte zadat název série, kategorie a hodnoty dat.

### Jak mohu formátovat datové štítky pomocí vlastních číselných formátů?

Datové štítky můžete formátovat přístupem k`DataLabels` vlastnosti řady a pomocí nastavení požadovaného formátu kódu`getNumberFormat().setFormatCode()`.

### Jak přizpůsobím vlastnosti os v grafu?

 Vlastnosti os, jako je typ, značky, štítky a další, můžete přizpůsobit pomocí přístupu k`ChartAxis` vlastnosti jako`setCategoryType()`, `setCrosses()` a`setMajorTickMark()`.

### Jak mohu vytvořit jiné typy grafů, jako jsou bodové nebo plošné grafy?

 Můžete vytvořit různé typy grafů zadáním příslušných`ChartType` při vkládání grafu pomocí`builder.insertChart(ChartType.TYPE, width, height)`.

### Jak mohu skrýt osu grafu?

 Osu grafu můžete skrýt nastavením`setHidden(true)` vlastnost osy.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
