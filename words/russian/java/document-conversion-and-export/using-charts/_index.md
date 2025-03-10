---
title: Использование диаграмм в Aspose.Words для Java
linktitle: Использование диаграмм
second_title: API обработки документов Java Aspose.Words
description: Узнайте, как создавать и настраивать диаграммы в Aspose.Words для Java. Изучите типы диаграмм, форматирование и свойства осей для визуализации данных.
weight: 12
url: /ru/java/document-conversion-and-export/using-charts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Использование диаграмм в Aspose.Words для Java


## Введение в использование диаграмм в Aspose.Words для Java

В этом уроке мы рассмотрим, как работать с диаграммами с помощью Aspose.Words для Java. Вы узнаете, как создавать различные типы диаграмм, настраивать свойства осей, форматировать метки данных и многое другое. Давайте погрузимся!

## Создание линейной диаграммы

Для создания линейной диаграммы используйте следующий код:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Удалить созданную по умолчанию серию.
chart.getSeries().clear();

// Добавление серии с данными и метками данных.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Или свяжите код формата с исходной ячейкой.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## Создание других типов диаграмм

Вы можете создавать различные типы диаграмм, такие как столбчатые, площадные, пузырьковые, точечные и другие, используя похожие методы. Вот пример вставки простой столбчатой диаграммы:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Удалить созданную по умолчанию серию.
chart.getSeries().clear();

// Создание категорий и добавление данных.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## Настройка свойств оси

Вы можете настроить свойства оси, например, изменить тип оси, установить деления, форматировать метки и т. д. Вот пример определения свойств оси XY:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Очистите серию по умолчанию и добавьте свои данные.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Измените ось X так, чтобы вместо даты отображалась категория.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); //Измеряется в единицах отображения оси Y (сотни).
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

## Форматирование меток данных

Вы можете форматировать метки данных с помощью различных числовых форматов. Вот пример:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Очистите серию по умолчанию и добавьте свои данные.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Дополнительные настройки диаграммы

Вы можете дополнительно настроить свои диаграммы, настроив границы, интервалы между метками, скрыв оси диаграммы и т. д. Изучите предоставленные фрагменты кода, чтобы узнать больше об этих параметрах.

## Заключение

В этом уроке мы изучили, как работать с диаграммами с помощью Aspose.Words для Java. Вы узнали, как создавать различные типы диаграмм, настраивать свойства осей, форматировать метки данных и многое другое. Aspose.Words для Java предоставляет мощные инструменты для добавления визуальных представлений данных в ваши документы, улучшая способ представления информации.

## Часто задаваемые вопросы

### Как добавить несколько рядов в диаграмму?

 Вы можете добавить несколько рядов в диаграмму с помощью`chart.getSeries().add()` метод. Обязательно укажите название серии, категории и значения данных.

### Как отформатировать метки данных с помощью пользовательских числовых форматов?

Вы можете форматировать метки данных, перейдя к`DataLabels` свойства серии и установка нужного формата кода с помощью`getNumberFormat().setFormatCode()`.

### Как настроить свойства осей на диаграмме?

 Вы можете настроить свойства осей, такие как тип, деления, метки и многое другое, перейдя к`ChartAxis` свойства, такие как`setCategoryType()`, `setCrosses()` , и`setMajorTickMark()`.

### Как создать другие типы диаграмм, например, точечные или площадные диаграммы?

 Вы можете создавать различные типы диаграмм, указав соответствующие`ChartType` при вставке диаграммы с помощью`builder.insertChart(ChartType.TYPE, width, height)`.

### Как скрыть ось диаграммы?

 Вы можете скрыть ось диаграммы, установив`setHidden(true)` свойство оси.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
