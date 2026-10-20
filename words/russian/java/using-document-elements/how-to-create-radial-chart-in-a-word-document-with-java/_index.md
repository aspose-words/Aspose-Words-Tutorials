---
category: general
date: 2026-09-18
description: Узнайте, как создать радиальную диаграмму в документе Word с помощью
  Java, добавить подписи данных к диаграмме и вставить данные серии, используя полный
  пример кода.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: ru
lastmod: 2026-09-18
og_description: Создайте радиальную диаграмму в документе Word с помощью Java, добавьте
  подписи данных диаграммы и вставьте данные серии в одном руководстве.
og_image_alt: Radial chart displayed inside a generated Word document
og_title: Создайте радиальную диаграмму в Word с помощью Java — пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: Как создать радиальную диаграмму в документе Word с помощью Java
url: /ru/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать радиальную диаграмму в документе Word с помощью Java

Если вам нужно создать радиальную диаграмму в документе Word, это руководство покажет точные шаги. Вы также узнаете, как добавить подписи данных диаграммы и вставить данные серии, чтобы диаграмма была готова к презентации.

Программное создание диаграммы устраняет ручную работу по форматированию и гарантирует согласованность отчетов. В руководстве предполагается, что у вас есть базовые знания Java и установлена последняя версия библиотеки Aspose.Words for Java.

## Что вам понадобится

* Java 17 или новее  
* Aspose.Words for Java (версия 23.12 или новее)  
* IDE или система сборки, способная разрешать зависимости Maven/Gradle  

Наличие этих предварительных условий позволяет запустить пример без дополнительной настройки.

## Как создать радиальную диаграмму в документе Word

Первый шаг — создать пустой файл Word, который будет содержать диаграмму. Пустой документ предоставляет чистое полотно и избегает нежелательных стилей.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` представляет весь файл .docx, а `DocumentBuilder` предоставляет методы для вставки элементов, таких как абзацы, таблицы и диаграммы.

## Как вставить диаграмму

Далее вставляем саму диаграмму. Метод `insertChart` создает объект диаграммы и размещает его в текущей позиции курсора билдера.

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

Полярная (radial) диаграмма отображает точки данных вокруг центральной оси, что идеально подходит для представления циклической информации. Размеры задаются в пунктах (1 pt ≈ 1/72 дюйма).

## Добавить данные серии в диаграмму

Диаграмма без данных серии пуста. Вы можете добавить серию вручную или привязать её к источнику данных. Пример ниже добавляет одну серию с тремя точками данных.

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` принимает имя серии, список меток категорий и список соответствующих числовых значений. Вы можете повторять этот блок, чтобы добавить дополнительные серии (`addSeriesData`).

## Добавить подписи данных к первой серии

Подписи данных делают диаграмму читаемой без наведения курсора на точки. Следующая строка включает подписи значений для первой серии.

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

Установка `showValue` в `true` отображает значение каждой точки непосредственно на диаграмме. Вы также можете включить имена категорий, проценты или линии‑указатели через тот же объект `DataLabelFormat`.

## Сохранить файл Word

После настройки диаграммы запишите документ на диск. Выберите расположение, доступное вашему приложению.

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

Файл `RadialChart.docx` теперь содержит полностью функциональную радиальную диаграмму с подписями данных.

## Полный рабочий пример

Ниже приведена автономная программа, которую вы можете скопировать, скомпилировать и запустить. Она демонстрирует полный процесс от создания пустого документа Word до сохранения радиальной диаграммы с подписями данных.

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**Ожидаемый результат**

Когда вы откроете `output/RadialChart.docx` в Microsoft Word, вы увидите радиальную диаграмму с заголовком *Quarterly Sales*. Каждая точка отображает своё числовое значение (например, «15000») рядом с маркером.

## Распространённые варианты и граничные случаи

| Ситуация | Рекомендуемое изменение |
|-----------|--------------------|
| Требуется другой тип диаграммы | Замените `ChartType.POLAR` на любое другое значение перечисления `ChartType` (например, `ChartType.COLUMN`). |
| Диаграмма должна использовать внешний диапазон Excel | Используйте `chart.setDataRange("Sheet1!A1:B5")` после создания диаграммы и загрузки рабочей книги. |
| Нужно скрыть легенду | `chart.getLegend().setVisible(false);` |
| Документ необходимо сохранить как PDF | Вызовите `doc.save("RadialChart.pdf");` – Aspose.Words автоматически преобразует диаграмму. |

Эти корректировки сохраняют основную логику, адаптируя вывод под конкретные требования.

## Полезные советы

* **Повторное использование билдера** – Вы можете вставлять несколько диаграмм в один документ, вызывая `builder.insertChart` многократно.
* **Производительность** – При генерации большого количества диаграмм создавайте один экземпляр `DocumentBuilder` и переиспользуйте его, чтобы снизить накладные расходы на создание объектов.
* **Стилизация** – Внешний вид диаграммы (цвета, толщина линий) управляется методами объекта `Chart` через `getSeries().get(i).getFormat()`. Экспериментируйте с этими настройками, чтобы соответствовать фирменному стилю.

## Заключение

Теперь вы знаете, как создать радиальную диаграмму в документе Word с помощью Java, добавить данные серии и подписи данных перед сохранением файла. Полный пример можно расширить, добавив дополнительные серии, пользовательские стили или альтернативные форматы вывода.

Изучайте связанные темы, такие как **how to insert chart** из внешних источников данных, **create blank word** документы с предопределёнными шаблонами и **add series data** динамически из баз данных. Экспериментируйте с различными типами диаграмм, чтобы найти лучший способ визуализации ваших данных.

## Что следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}