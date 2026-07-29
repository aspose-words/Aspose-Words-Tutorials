---
category: general
date: 2026-07-29
description: Вставьте круговую диаграмму с помощью Aspose.Words для Java и узнайте,
  как создать кольцевую диаграмму, отформатировать круговую диаграмму, отформатировать
  диаграмму в Word и настроить её размер.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: ru
lastmod: 2026-07-29
og_description: Вставьте круговую диаграмму с помощью Aspose.Words для Java и быстро
  научитесь создавать кольцевую диаграмму, форматировать круговую диаграмму, форматировать
  диаграмму в Word и настраивать размер диаграммы для профессиональных документов.
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: Вставка круговой диаграммы в Java – Полный учебник по Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: Вставка круговой диаграммы в Java с Aspose.Words – Полное руководство
url: /ru/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Вставка круговой диаграммы в Java с Aspose.Words – Полное руководство

Когда‑нибудь задумывались, как **insert pie chart** в документ Word из кода Java? Вы не одиноки — многие разработчики сталкиваются с этой проблемой, когда им нужен быстрый программный способ визуализации данных. Хорошая новость? С Aspose.Words for Java вы можете сделать это всего за несколько строк, и при этом также **generate doughnut chart**, **format pie chart**, **format chart Word** и **customize chart size** в соответствии с вашим брендом.

В этом руководстве мы пройдем реальный пример, который начинается с создания пустого документа, вставки круговой диаграммы, настройки нескольких визуальных свойств и, наконец, сохранения файла. К концу вы получите переиспользуемый фрагмент кода, который можно вставить в любой Java‑проект, требующий автоматизации диаграмм. Без дополнительных библиотек, без ручного вмешательства в Office Interop — просто чистый, скомпилированный Java.

## Что понадобится

- **Java 17** (или любой современный JDK; API совместим с более старыми версиями)
- **Aspose.Words for Java** 22.12 или новее — можно взять Maven‑артефакт или .jar с сайта Aspose.
- Любая удобная IDE (IntelliJ IDEA, Eclipse, VS Code…) — всё, что позволяет запустить метод `main`.
- Необязательно: файл лицензии, если не хотите видеть водяной знак оценки.

Если всё это у вас есть, можно сразу переходить к коду.

## Шаг 1: Вставка круговой диаграммы с помощью Aspose.Words

Первое, что мы делаем, — **insert pie chart** в свежий документ. Этот шаг задаёт основу для всего остального, потому что объект диаграммы даёт доступ к сериям, точкам данных и визуальным настройкам.

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Why this matters:** `DocumentBuilder.insertChart` not only creates the chart but also returns a `Chart` object that we can manipulate. The width and height arguments let you **customize chart size** right at creation time, so you don’t need to resize later.

## Шаг 2: Создание кольцевой диаграммы (опционально)

Если ваш дизайн требует отверстия посередине — представьте классическую кольцевую диаграмму — Aspose делает это в одну строку. Тот же экземпляр `Chart` можно переключить с обычного круга на кольцо, изменив размер отверстия.

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Tip:** The hole size only takes effect for `ChartType.DONUT`. If you keep the type as `PIE`, the call is ignored, so feel free to experiment.

## Шаг 3: Форматирование секторов круговой диаграммы

Хорошая визуализация часто подчёркивает определённый сектор. Здесь мы **format pie chart**, «взрывая» первый сектор на 20 пунктов наружу. Это привлекает взгляд читателя к самому важному пункту данных.

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Pro tip:** You can loop through `pieChart.getSeries()` if you have multiple series and set individual colors, borders, or data labels. That’s the way to **format chart Word** documents with rich styling.

## Шаг 4: Добавление данных в диаграмму

Диаграмма без данных — просто декоративный элемент. Давайте заполним её простым набором данных — например, квартальными продажами.

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Why we do this:** By explicitly adding `ChartPoint` objects we guarantee the chart reflects our business logic. The `setShowCategoryName` and `setShowValue` calls are part of **formatting the pie chart** to show both labels and numbers.

## Шаг 5: Точная настройка внешнего вида (customize chart size & style)

Помимо начальных размеров, вы можете захотеть настроить легенду, заголовок или даже шрифт, используемый для подписей данных. Всё это относится к **customize chart size** и общей стилизации.

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Edge case:** If you later decide to export the document to PDF, the chart’s vector data stays crisp because the size is defined in points, not pixels. That’s a win for **format chart Word** and downstream formats.

## Шаг 6: Сохранение и просмотр документа

Последний шаг так же прост, как вызов `doc.save`. Это записывает файл `.docx`, который можно открыть в Microsoft Word, LibreOffice или любом просмотрщике, поддерживающем формат OpenXML.

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Result:** Open `PieChart.docx` and you’ll see a neatly sized pie (or doughnut) chart with an exploded slice, a title, and a legend—all generated without ever touching the UI.

### Ожидаемый результат

| Element | What you’ll see |
|---------|-----------------|
| Chart type | Pie chart (or doughnut if `holeSize` > 0) |
| Slice explosion | First slice offset by 20 pts |
| Legend | Positioned on the right |
| Title | “Quarterly Sales Distribution” in bold 14 pt |
| Data labels | Category name and value shown on each slice |
| Document | A standard Word `.docx` file ready for sharing |

## Часто задаваемые вопросы и подводные камни

- **Do I need a license?**  
  The evaluation version works fine for testing, but it adds a watermark. Drop your `aspose.words.lic` file in the classpath for a clean output.

- **Can I use this with Maven?**  
  Absolutely. Add the following dependency to your `pom.xml`:

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **What if I have more than one series?**  
  Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`, or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional data.

- **Is the chart editable in Word after generation?**  
  Yes—once saved, you can open the document and manually adjust colors, fonts, or even convert the pie to a bar chart if you need to.

## Итоги

We’ve just **inserted pie chart** into a Word document using Aspose.Words for Java, shown how to **generate doughnut chart**, demonstrated multiple ways to **format pie chart**, covered **format chart Word** best practices, and learned how to **customize chart size** for a polished look. The complete, runnable example above can be dropped into any Java project, giving you instant chart automation without the overhead of COM interop or Office installations.

What’s next? Try swapping the data source for a live database, add conditional colors based on thresholds, or export the same document to PDF for a print‑ready report. Each of those steps builds on the foundation we’ve laid out, so you’ll find the transition smooth.

If you hit any snags or have ideas for further enhancements—maybe a stacked bar or a line chart—drop a comment below. Happy charting!

## Что изучать дальше?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Number Format For Axis In A Chart](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}