---
category: general
date: 2026-11-22
description: Создайте круговую диаграмму в Java и узнайте, как задать размер диаграммы,
  добавить подписи данных, отобразить проценты и повернуть первый сектор для ясного
  визуального эффекта.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: ru
lastmod: 2026-11-22
og_description: Создайте круговую диаграмму на Java, затем задайте размер диаграммы,
  отобразите проценты в подписи данных и поверните первый сектор — всё в одном исполняемом
  примере.
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: Создайте круговую диаграмму с пользовательским размером, метками и вращением
  в Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: Создать круговую диаграмму с пользовательским размером, метками данных и вращением
  в Java
url: /ru/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание круговой диаграммы с пользовательским размером, метками данных и вращением в Java

Если вам нужно **create pie chart** в Java, это руководство проведёт вас через весь процесс. Вы узнаете, как **set chart size**, включить **show percentages pie chart**, добавить **data labels pie chart** и **rotate pie chart slice**, чтобы первый сегмент начинался под углом 45 градусов.

В примере используется **Aspose.Slides for Java**, широко используемая библиотека для работы с файлами PowerPoint. Те же концепции применимы к другим библиотекам построения диаграмм; просто замените вызовы API на эквиваленты в вашем наборе инструментов.

## Требования

* Java 17 или новее установлен
* Maven 3.8+ (или Gradle) для управления зависимостями
* Базовое понимание синтаксиса Java
* Доступ к бинарному файлу Aspose.Slides for Java (вы можете получить бесплатную trial‑версию на официальном сайте)

Добавьте зависимость в ваш `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## Создание круговой диаграммы — полный пример

Следующая программа создаёт слайд PowerPoint, содержащий круговую диаграмму с пользовательским размером, процентными метками данных и вращённым первым сегментом.

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### Почему каждый шаг важен

| Шаг | Назначение | Как связано с ключевыми словами |
|------|------------|--------------------------------|
| **Insert chart** | **Create pie chart** – основной объект, который будет отображать визуализацию. | Непосредственно удовлетворяет требование *create pie chart*. |
| **Set dimensions** | Вызов `addChart(..., 400, 300)` демонстрирует **set chart size**. | Управляет шириной (400 px) и высотой (300 px). |
| **Show percentages** | `setShowPercentage(true)` заставляет диаграмму **show percentages pie chart** на каждом сегменте. | Пользователи часто нуждаются в процентах вместо сырых значений. |
| **Add data labels** | Конфигурация `DataLabelFormat` добавляет **data labels pie chart** с нужной видимостью. | Метки повышают читаемость и могут быть настроены. |
| **Rotate slice** | `setFirstSliceAngle(45)` вращает диаграмму так, что первый сегмент начинается под углом 45°, удовлетворяя **rotate pie chart slice**. | Улучшает визуальное выделение конкретного сегмента. |

## Пошаговый разбор

### 1. Вставка круговой диаграммы и установка её размера

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*Метод `addChart` создаёт диаграмму и одновременно **set chart size** до 400 × 300 пунктов.* Если нужен другой размер, измените два последних аргумента.

### 2. Заполнение диаграммы данными

Демонстрация добавляет три категории и одну серию. При необходимости замените жёстко закодированные числа данными из базы данных, CSV‑файла или ввода пользователя.

### 3. Показ процентов на каждом сегменте

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*Включение `setShowPercentage(true)` гарантирует, что диаграмма **show percentages pie chart** автоматически вычисляет долю каждого сегмента от общего количества.*

### 4. Добавление подробных меток данных

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

Вы можете переключать другие параметры меток (`setShowValue`, `setShowSeriesName` и т.д.), чтобы настроить опыт **add data labels pie chart**.

### 5. Вращение первого сегмента

```java
chart.setFirstSliceAngle(45);
```

*Вызов `setFirstSliceAngle(45)` **rotate pie chart slice**, так что первый сегмент начинается под углом 45°, выделяя его.*

### 6. Сохранение и просмотр результата

Запуск программы создаёт `output/PieChartDemo.pptx`. Откройте его в PowerPoint или любом совместимом просмотрщике, чтобы увидеть окончательную круговую диаграмму:

![Create pie chart example](images/pie_chart_example.png){.align-center alt="Снимок экрана созданной круговой диаграммы с пользовательским размером, процентными метками и вращённым первым сегментом"}

Изображение выше демонстрирует результат **create pie chart**, подтверждая, что размер, метки, проценты и вращение применены корректно.

## Распространённые варианты и граничные случаи

| Ситуация | Корректировка |
|-----------|----------------|
| Другие размеры диаграммы | Измените параметры ширины/высоты в `addChart`. |
| Несколько серий | Добавьте дополнительные объекты `IChartSeries`; у каждой серии могут быть свои настройки меток. |
| Пользовательский формат меток | Используйте `series.getDataLabelFormat().setNumberFormat("0.0%")` для управления количеством знаков после запятой. |
| Вращение на другой угол | Передайте любое целое число (0‑360) в `setFirstSliceAngle`. |
| Экспорт в изображение | После сохранения вызовите `chart.writeAsSvg(outPath)` или `chart.writeAsPng(outPath)` для растровой версии. |

> **Pro tip:** Если вы планируете генерировать множество диаграмм в цикле, переиспользуйте один объект `Presentation` и заменяйте только данные диаграммы. Это уменьшает нагрузку на память и ускоряет обработку.

## Заключение

Теперь вы знаете, как **create pie chart** в Java, **set chart size**, включить **show percentages pie chart**, **add data labels pie chart** и **rotate pie chart slice** для лучшего визуального акцента. Полный, исполняемый пример демонстрирует каждый шаг от инициализации до сохранения конечного файла PowerPoint.

### Что дальше?

* Исследуйте другие типы диаграмм (Bar, Line, Area), используя тот же enum `ChartType`.  
* Объединяйте несколько диаграмм на одном слайде для панелей мониторинга.  
* Экспортируйте диаграммы в PNG или SVG для использования в веб‑приложениях.  

Не стесняйтесь экспериментировать с цветами, легендами и анимационными эффектами — ваши визуализации ограничены лишь воображением. Приятного построения диаграмм!

## Что вам следует изучить дальше?

Следующие учебные материалы охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [как вставить круговую диаграмму в Word – добавить процент метки данных](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [Как разорвать сегмент круговой диаграммы в Java – учебник по Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Вставка круговой диаграммы в Java – разрыв, вращение и выделение сегментов](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}