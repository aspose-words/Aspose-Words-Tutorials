---
date: 2026-02-16
description: Узнайте, как добавить несколько серий в диаграммы в Aspose.Words для
  Java, изменить деления осей, применить пользовательский числовой формат и создавать
  документы Word с линейными и столбчатыми диаграммами.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Добавить несколько серий в диаграммы в Aspose.Words для Java
url: /ru/java/document-conversion-and-export/using-charts/
weight: 12
---

 Cases" => "Общие сценарии использования"

"Financial dashboards" => "Финансовые панели мониторинга"

"Sales reports" => "Отчёты о продажах"

"Project tracking" => "Отслеживание проектов"

"Additional Chart Customizations" => "Дополнительные настройки диаграмм"

"Conclusion" => "Заключение"

"Frequently Asked Questions" => "Часто задаваемые вопросы"

Then Q&A.

"Last Updated:" keep date.

"Tested With:" etc.

Now produce final content with same markdown.

Make sure to keep code block placeholders as separate lines.

Also there are block shortcodes at top and bottom.

Let's craft final output.{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Добавление нескольких рядов в диаграммы в Aspose.Words для Java

## Введение в использование диаграмм в Aspose.Words для Java

В этом руководстве вы узнаете **как добавить несколько рядов** в диаграмму с помощью Aspose.Words для Java, почему важно настраивать метки делений осей и применять пользовательский числовой формат, а также как создать документ Word, насыщенный диаграммами. Независимо от того, нужен ли вам линейный график для финансовых данных или столбчатая диаграмма для продаж, приведённые ниже шаги помогут вам программно создавать, стилизовать и тонко настраивать диаграммы.

## Быстрые ответы
- **Как добавить несколько рядов?** Используйте `chart.getSeries().add(...)` для каждого ряда, который вы хотите отобразить.  
- **Можно ли изменить метки делений осей?** Да — используйте `setMajorTickMark()` и `setMinorTickMark()` у объектов осей.  
- **Какой формат можно применить к подписьм данных?** Любой совместимый с Excel числовой формат, например `"$"#,##0.00` или `0.00%`.  
- **Какие типы диаграмм поддерживаются?** Линейные, столбчатые, областные, пузырьковые, точечные и многие другие через `ChartType`.  
- **Нужна ли лицензия для продакшн?** Для полной функциональности требуется действующая лицензия Aspose.Words для Java.

## Что означает «добавление нескольких рядов» в диаграмме?
Добавление нескольких рядов подразумевает вставку более одного набора данных в одну область диаграммы, что позволяет сравнивать разные категории или периоды времени бок‑о‑бок. Каждый ряд отображается своей линией, столбцом или набором маркеров, предоставляя читателям более насыщенную визуальную историю.

## Зачем использовать Aspose.Words для Java для генерации Word‑документов с диаграммами?
- **Полный контроль** над типом диаграммы, макетом и стилем без необходимости открывать Word вручную.  
- **Программная генерация** удобно вписывается в автоматизированные конвейеры отчётности.  
- **Кросс‑платформенность** — работает в любой среде, совместимой с Java.  
- **Богатый API** для настройки осей, подписей данных и числовых форматов.

## Требования
- Java Development Kit (JDK) 8 или выше.  
- Библиотека Aspose.Words для Java, добавленная в ваш проект (Maven/Gradle или JAR).  
- Действующая лицензия Aspose для продакшн (необязательно для оценки).

## Пошаговое руководство

### Шаг 1: Создать линейную диаграмму и **добавить несколько рядов**
Ниже приведён основной код, который создаёт линейную диаграмму, очищает ряд по умолчанию и затем добавляет три отдельных ряда с пользовательскими подписями данных.

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

> **Совет:** Вызывайте `chart.getSeries().add(...)` столько раз, сколько необходимо, чтобы **добавить несколько рядов** — каждый вызов создаёт новую линию (или столбец и т.д.) на той же диаграмме.

### Шаг 2: **Создать столбчатую диаграмму** (create column chart java)
Следующий фрагмент показывает, как вставить простую столбчатую диаграмму, полезную для сравнения категорий бок‑о‑бок.

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

### Шаг 3: **Изменить метки делений осей** (change axis tick marks)
Настройка осей X и Y повышает читаемость. Ниже код, демонстрирующий изменение меток делений, обратный порядок и установку пользовательских точек пересечения.

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

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### Шаг 4: **Применить пользовательский числовой формат** (apply custom number format)
Вы можете форматировать числа осей или подписи данных любым шаблоном, поддерживаемым Excel. Пример ниже задаёт для оси Y формат с разделителем тысяч.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### Шаг 5: Сгенерировать окончательный Word‑документ (generate chart word document)
После настройки рядов, осей и подписей просто вызовите `doc.save(...)`, как показано в фрагментах выше. Полученный файл `.docx` содержит полностью функциональные диаграммы, которые можно открыть и отредактировать в Microsoft Word.

## Общие сценарии использования
- **Финансовые панели мониторинга** — линейные диаграммы с несколькими рядами для доходов, расходов и прибыли.  
- **Отчёты о продажах** — столбчатые диаграммы, сравнивающие квартальные продажи по регионам.  
- **Отслеживание проектов** — областные или точечные диаграммы, визуализирующие прогресс во времени.  

## Дополнительные настройки диаграмм
Помимо базовых возможностей, вы можете регулировать границы, скрывать оси (`axis.setHidden(true)`), менять цвета, добавлять легенды и многое другое. Обратитесь к справочнику API Aspose.Words для Java для полного списка параметров.

## Заключение
В этом руководстве мы рассмотрели, как **добавлять несколько рядов** в диаграммы, создавать как линейные, так и столбчатые диаграммы, **изменять метки делений осей**, **применять пользовательские числовые форматы** и, наконец, **генерировать документ Word, насыщенный диаграммами**. С Aspose.Words для Java вы получаете мощный, ориентированный на код способ встраивать профессиональные визуализации данных непосредственно в свои документы.

## Часто задаваемые вопросы

**В: Как добавить несколько рядов в диаграмму?**  
О: Вызовите `chart.getSeries().add()` для каждого ряда, который вы хотите отобразить. Каждый вызов создаёт новый набор данных, отображаемый как отдельная линия, столбец или группа маркеров.

**В: Как отформатировать подписи данных с помощью пользовательского числового формата?**  
О: Получите объект `DataLabels` у ряда и используйте `getNumberFormat().setFormatCode("ваш шаблон")`. Также можно привязать формат к исходной ячейке с помощью `isLinkedToSource(true)`.

**В: Как изменить метки делений осей?**  
О: Используйте `setMajorTickMark()` и `setMinorTickMark()` у `ChartAxis`. Доступные варианты: `CROSS`, `INSIDE`, `OUTSIDE` и `NONE`.

**В: Могу ли я создавать другие типы диаграмм, например точечные или областные?**  
О: Да — укажите нужный `ChartType` (например, `ChartType.SCATTER`, `ChartType.AREA`) при вызове `builder.insertChart(...)`.

**В: Как скрыть ось, которая не нужна?**  
О: Вызовите `axis.setHidden(true)` у нужного `ChartAxis`.

---

**Последнее обновление:** 2026-02-16  
**Тестировано с:** Aspose.Words для Java 24.11  
**Автор:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}