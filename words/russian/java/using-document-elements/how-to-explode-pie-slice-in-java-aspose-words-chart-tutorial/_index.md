---
category: general
date: 2026-08-07
description: Как отделить срез круговой диаграммы в Java с помощью Aspose.Words. Узнайте,
  как добавить линии‑указатели к круговой диаграмме, создать диаграмму Word и настроить
  срезы круговой диаграммы.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: ru
lastmod: 2026-08-07
og_description: Как выделить часть круговой диаграммы в Java с помощью Aspose.Words.
  Это руководство показывает, как добавить выноски к круговой диаграмме, создавать
  диаграммы Word и настраивать сегменты круговой диаграммы для ясного визуального
  эффекта.
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: Как выделить сектор круговой диаграммы в Java – руководство Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: Как выделить часть круговой диаграммы в Java — учебник по диаграммам Aspose.Words
url: /ru/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как выделить сектор круговой диаграммы в Java – руководство по диаграммам Aspose.Words

Если вам нужно знать **как выделить сектор круговой диаграммы** в документе Word с помощью Java, этот учебник вам поможет. Мы также покажем, **как добавить линии‑соединения к круговым** диаграммам, **java create word chart** объекты, и **как настроить сектора круговой диаграммы** для получения аккуратного результата. К концу этого руководства у вас будет полностью готовый, исполняемый пример, который можно добавить в любой проект Java.

![Как выделить сектор круговой диаграммы в Java – диаграмма Aspose.Words](/images/pie-chart-exploded.png)

## Требования

* Java Development Kit (JDK) 8 или выше.
* Maven или Gradle для управления зависимостями.
* Лицензия Aspose.Words for Java (бесплатная оценочная версия подходит для обучения).
* Базовое знакомство с синтаксисом Java и объектно‑ориентированными концепциями.

> **Совет:** Несмотря на то, что Aspose.Words предлагает бесплатную пробную версию, покупка лицензии удаляет водяной знак оценки из сгенерированных документов.

## Что покрывает данный учебник

* Создание нового документа Word с нуля.  
* Вставка **pie chart** с помощью `DocumentBuilder`.  
* **Выделение сектора круговой диаграммы** для акцентирования точки данных.  
* **Добавление линий‑соединения к круговой диаграмме** для более четкой подписи.  
* Настройка внешнего вида сектора, например цветов и границ.  
* Сохранение документа на диск и проверка результата.

---

## Как выделить сектор круговой диаграммы с помощью Aspose.Words в Java

Первый шаг — настроить объект диаграммы и выделить нужный сектор. Aspose.Words предоставляет диаграмму через класс `Shape`, а каждый сектор представляет собой `ChartPoint`. Устанавливая свойство `Explosion`, вы контролируете, насколько далеко сектор будет смещён наружу.

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**Почему это работает:**  
`setExplosion(20)` сообщает движку диаграммы сместить сектор на 20 пунктов от центра диаграммы. Значение относительное; большие числа создают более драматичный эффект. Вы можете выделить любой сектор, изменив индекс (`get(1)`, `get(2)`, …).

## Добавление линий‑соединения к круговой диаграмме для более четких подписей

Линии‑соединения соединяют подпись сектора с его краем, что особенно полезно, когда сектора выделены или когда диаграмма содержит много небольших частей. Вызов `setLeaderLines(true)` включает эту функцию для всей серии.

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**Зачем нужны линии‑соединения:**  
Когда сектор выделен, подпись по умолчанию может перекрываться с другими элементами. Линии‑соединения делают подпись читаемой, рисуя короткую линию от сектора к текстовому полю.

## Java create Word chart – вставка серии данных

Диаграмма без данных не очень полезна. Необходимо заполнить серию категориями и значениями. Ниже мы добавляем три категории, представляющие долю рынка.

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**Объяснение:**  
`ChartSeries` содержит как категории (имена секторов), так и числовые значения. Включение `ShowCategoryName` и `ShowPercentage` делает диаграмму самодостаточной, что хорошо сочетается с ранее добавленными линиями‑соединения.

## Настройка секторов круговой диаграммы помимо выделения

Помимо выделения сектора, часто требуется настроить цвета, границы или даже полностью скрыть сектор. Ниже приведён фрагмент, демонстрирующий три распространённых настройки:

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**Зачем настраивать сектора:**  
Пользовательские цвета позволяют диаграмме соответствовать фирменному стилю, а границы повышают читаемость на печатных страницах. Скрытие сектора полезно, когда нужно сохранить модель данных, но временно исключить категорию из визуального вывода.

## Сохранение документа и проверка результата

Наконец, запишите документ на диск. Сгенерированный файл `.docx` можно открыть в Microsoft Word, LibreOffice или любом просмотрщике, поддерживающем этот формат.

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**Ожидаемый результат:**  
Когда вы откроете `PieChartDemo.docx`, вы увидите круговую диаграмму, где первый сектор (Product A) выделен наружу, линии‑соединения указывают от каждого сектора к его подписи, а сектора отображаются в пользовательских зелёном, синем и оранжевом цветах. Скрытый сектор (Product C) будет невидим, но проценты всё равно суммируются до 100 %, поскольку данные остаются в серии диаграммы.

## Полный, исполняемый пример

Ниже представлен полный код программы, который вы можете скопировать, вставить и запустить после добавления зависимости Aspose.Words в ваш проект.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**Зависимость (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

## Что следует изучить дальше?

Следующие учебники охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Как создать столбчатую диаграмму с помощью Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Как загрузить документы Word с помощью Aspose.Words Java: Полное руководство](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Как создать поля формы и добавить содержимое с помощью DocumentBuilder в Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}