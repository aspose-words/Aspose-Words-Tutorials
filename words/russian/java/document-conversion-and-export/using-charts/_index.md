---
date: 2025-12-13
description: Изучите, как создавать столбчатую диаграмму и форматировать подписи данных
  диаграммы с помощью Aspose.Words для Java. Узнайте, как добавлять несколько рядов,
  менять тип оси и скрывать ось диаграммы.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Как создать столбчатую диаграмму с помощью Aspose.Words для Java
url: /ru/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Как создать столбчатую диаграмму с помощью Aspose.Words для Java

В этом руководстве вы **создадите столбчатую диаграмму** непосредственно в документах Word, используя Aspose.Words для Java. Мы пройдемся по созданию разных типов диаграмм, добавлению нескольких рядов, форматированию подписей данных, изменению типа оси и даже скрытию оси диаграммы, когда нужен более чистый вид. К концу вы получите надёжный, готовый к продакшну подход для встраивания богатых диаграмм в ваши документы.

## Быстрые ответы
- **Какой основной класс для построения диаграммы?** `DocumentBuilder` с методом `insertChart`.
- **Какой метод добавляет новый ряд?** `chart.getSeries().add(...)`.
- **Как отформатировать подписи данных диаграммы?** Используйте `getDataLabels().get(...).getNumberFormat().setFormatCode(...)`.
- **Можно ли скрыть ось?** Да, вызовите `setHidden(true)` у объекта оси.
- **Нужна ли лицензия для Aspose.Words?** Лицензия требуется для продакшн‑использования; доступна бесплатная trial‑версия.

## Что такое столбчатая диаграмма и зачем её использовать?

Столбчатая диаграмма отображает категориальные данные в виде вертикальных столбцов, что делает её идеальной для сравнения значений между группами (продажи по регионам, ежемесячные расходы и т.д.). В Java‑приложениях генерация столбчатой диаграммы с помощью Aspose.Words позволяет встраивать эти визуалы напрямую в файлы Word / DOCX без необходимости использовать Excel или сторонние инструменты.

## Как создать столбчатую диаграмму

Ниже приведён простой пример, создающий базовую столбчатую диаграмму. Код полностью идентичен оригинальному фрагменту – мы лишь добавили поясняющие комментарии, чтобы было легче понять.

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

### Добавление нескольких рядов

Вы можете **добавлять несколько рядов** в столбчатую диаграмму, вызывая `chart.getSeries().add(...)` последовательно, как показано выше. Каждый ряд может иметь собственный набор категорий и значений, позволяя сравнивать несколько наборов данных бок‑о‑бок.

## Как создать линейную диаграмму с пользовательскими подписями данных

Если нужна линейная диаграмма вместо столбчатой, применяется тот же шаблон. Этот пример также демонстрирует **форматирование подписей данных** с различными числовыми форматами.

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

### Добавление подписей данных

Вызов `series1.hasDataLabels(true)` **добавляет подписи данных** к ряду, а `setShowValue(true)` делает сами значения видимыми на диаграмме.

## Как изменить тип оси и настроить свойства оси

Изменение типа оси (например, с даты на категорию) позволяет контролировать, как отображаются точки данных. Этот фрагмент также показывает, как **скрыть ось диаграммы**, если вы предпочитаете минималистичный дизайн.

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

### Изменение типа оси

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **изменяет тип оси** с оси, основанной на датах, на категориальную, давая вам полный контроль над размещением меток.

## Как форматировать подписи данных диаграммы (числовые форматы)

Вы можете применять числовое форматирование непосредственно к оси или подписям данных. В этом примере числа оси Y форматируются с разделителем тысяч.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Дополнительные настройки диаграммы

Помимо базовых возможностей, вы можете регулировать границы, задавать интервалы между метками, скрывать отдельные оси и многое другое. Обратитесь к документации Aspose.Words for Java API для полного списка свойств.

## Часто задаваемые вопросы

**В: Как добавить несколько рядов к диаграмме?**  
О: Используйте `chart.getSeries().add()` для каждого ряда, который хотите отобразить. Каждый вызов может принимать уникальное имя, массив категорий и массив значений.

**В: Как отформатировать подписи данных диаграммы с пользовательскими числовыми форматами?**  
О: Получите объект `DataLabels` у ряда и вызовите `getNumberFormat().setFormatCode("ваш формат")`. Также можно привязать формат к исходной ячейке с помощью `isLinkedToSource(true)`.

**В: Как скрыть ось диаграммы?**  
О: Вызовите `setHidden(true)` у нужного `ChartAxis` (например, `chart.getAxisY().setHidden(true)`).

**В: Как лучше изменить тип оси?**  
О: Используйте `setCategoryType(AxisCategoryType.CATEGORY)` для категориальных осей или `AxisCategoryType.DATE` для датированных осей.

**В: Как добавить подписи данных к ряду?**  
О: Включите их с помощью `series.hasDataLabels(true)`, а затем настройте отображение через `series.getDataLabels().setShowValue(true)`.

## Заключение

Мы рассмотрели всё, что нужно для **создания столбчатой диаграммы** с помощью Aspose.Words для Java — от вставки базовых диаграмм и добавления нескольких рядов до форматирования подписей данных, изменения типа оси и скрытия осей для чистого вида. Внедрите эти техники в свои отчёты или конвейеры генерации документов, чтобы предоставлять профессиональные, основанные на данных документы Word.

---

**Последнее обновление:** 2025-12-13  
**Тестировано с:** Aspose.Words for Java 24.12 (latest)  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}