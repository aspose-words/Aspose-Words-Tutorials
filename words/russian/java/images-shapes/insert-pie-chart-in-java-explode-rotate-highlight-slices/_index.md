---
category: general
date: 2026-07-20
description: Вставьте круговую диаграмму в Java с пошаговым руководством. Узнайте,
  как «взрывать» сектор, как вращать круговую диаграмму, как выделять сектор и как
  настраивать его.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: ru
lastmod: 2026-07-20
og_description: Вставьте круговую диаграмму в Java и освоите, как «взрывать» сектор,
  вращать диаграмму, выделять сектор и настраивать его для создания качественных визуальных
  отчётов.
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: Вставка круговой диаграммы в Java – взрыв, вращение и выделение
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: Вставка круговой диаграммы в Java — разрыв, вращение и выделение секторов
url: /ru/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Вставка круговой диаграммы в Java – Выделение, Поворот и Подсветка Секторов

Когда‑нибудь вам нужно было **insert pie chart** в Java‑отчете, но вы не знали, как сделать отдельный сектор выпадающим? Вы не одиноки. Независимо от того, создаёте ли вы панель мониторинга, генерируете счёт‑фактуру или просто визуализируете результаты опроса, хорошо оформленная круговая диаграмма может превратить сырые цифры в мгновенно понятные инсайты.

В этом руководстве вы увидите полностью готовый к запуску пример, который показывает, как вставить круговую диаграмму, **how to explode slice**, **how to rotate pie chart**, а также **highlight pie chart slice** с пользовательскими цветами. К концу у вас будет переиспользуемый фрагмент, который можно вставить в любой Java‑проект, использующий популярную библиотеку *JFreeChart* (или любой аналогичный API).

## Предварительные требования

- Java 17 или новее (код компилируется и в более старых версиях, но мы будем использовать современный синтаксис `var` для краткости).  
- Maven или Gradle для получения зависимости `org.jfree:jfreechart`.  
- Базовое понимание классов Java и концепции построителя диаграмм.  

Если вы никогда не добавляли библиотеку в проект Maven, просто вставьте это в ваш `pom.xml`:

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

Вот и всё — дополнительная настройка не требуется.

## Шаг 1: Вставка круговой диаграммы – Создание Builder и объекта Chart

Во-первых, нам нужен *builder* (подумайте о нём как о фабрике), который умеет создавать диаграммы. В JFreeChart за это отвечает `ChartFactory`.

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

Почему мы начинаем с набора данных? Потому что сама диаграмма — это лишь визуальная оболочка над числами. **inserting pie chart** здесь уже создаёт холст 400 × 300 (размер будет применён позже при рендеринге в изображение).

## Шаг 2: How to Explode Slice – Выделение первого сегмента

Теперь, когда диаграмма существует, давайте сделаем первый сектор более заметным. Взрыв (exploding) сектора отодвигает его немного от круга, привлекая внимание читателя.

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

Обратите внимание, что мы используем фразу **how to explode slice** в имени метода; это делает намерение кристально ясным. Метод `setExplodePercent` принимает ключ (метку сектора) и процент, поэтому вы можете регулировать расстояние «выстрела» по необходимости.

## Шаг 3: How to Rotate Pie Chart – Изменение начального угла

По умолчанию круговая диаграмма начинается с позиции 12 часов. Иногда требуется, чтобы первый сектор начинался в другом месте — возможно, чтобы соответствовать макету дизайна или другой диаграмме.

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

Вызов `rotateChart(chart, 45)` вращает всю диаграмму так, чтобы сектор «Apples» начинался под углом 45 градусов, точно как требует **how to rotate pie chart**.

## Шаг 4: Highlight Pie Chart Slice – Пользовательские цвета и подписи

Помимо взрыва, вы можете захотеть задать сектору уникальный цвет или жирную подпись, чтобы действительно **highlight pie chart slice**.

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

Здесь мы **customize pie chart slice** изменяя его заливку и стиль подписи. Не стесняйтесь менять цвет или шрифт, чтобы соответствовать палитре вашего бренда.

## Шаг 5: Render the Chart to an Image (Optional but Handy)

Большинству реальных приложений нужен график в виде PNG, JPEG или даже PDF. Ниже показан быстрый способ записать диаграмму в файл.

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

Запуск полного процесса создаст PNG размером 400 × 300, выглядящий примерно так:

![Insert pie chart example](image.png){: alt="Пример вставки круговой диаграммы, показывающий взорванный и повернутый сектор"}

## Полный рабочий пример

Объединив всё вместе, вот метод `main`, который вы можете скопировать‑вставить в новый Java‑класс и выполнить:

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### Ожидаемый результат

Запуск программы создаёт файл под названием **fruit-pie.png**. Откройте его, и вы увидите:

- Круговую диаграмму 400 × 300 с заголовком «Fruit Distribution».  
- Сектор «Apples», взорванный наружу на 15 %.  
- Вся диаграмма повернута, так что «Apples» начинается под углом 45 градусов.  
- Взорванный

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Как создать столбчатую диаграмму с помощью Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Вставка точечной диаграммы](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [Вставка областной диаграммы](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}