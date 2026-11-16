---
category: general
date: 2026-11-15
description: Узнайте, как добавить круговую диаграмму в документ Word с помощью Aspose.Words
  for Java. Включает преобразование в кольцевую диаграмму, взрывной срез и полный
  пример кода.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: ru
lastmod: 2026-11-15
og_description: Добавьте круговую диаграмму в документ Word с помощью Aspose.Words
  for Java. Этот учебник показывает, как отделить срез и превратить диаграмму в кольцевую.
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: Добавьте круговую диаграмму в документ Word с помощью Java – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Как добавить круговую диаграмму в документ Word с помощью Java
url: /ru/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Добавить круговую диаграмму в документ Word – полное руководство на Java

Если вам нужно **добавить круговую диаграмму в документ Word** программно, этот учебник покажет, как сделать это с помощью Aspose.Words for Java. Вы увидите полный процесс: загрузку DOCX, создание круговой диаграммы, «взрыв» первого сектора и преобразование диаграммы в пончик, задав размер отверстия.

Руководство также охватывает распространённые варианты — такие как добавление нескольких серий, настройка цветов и работа с документами, уже содержащими диаграммы — чтобы вы могли адаптировать код к реальным проектам, например автоматизированным отчетам или динамическим презентациям.

## Требования

* Java 17 или новее (код также компилируется с JDK 11+)
* Maven 3.6+ или Gradle для управления зависимостями
* Лицензия Aspose.Words for Java (бесплатная пробная версия подходит для тестирования)
* Базовое понимание синтаксиса Java и структуры Maven‑проекта

## Шаг 1: Настройте Maven‑проект и импортируйте Aspose.Words

Создайте новый Maven‑проект (или добавьте в существующий) и включите зависимость Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **Совет:** Если вы используете Gradle, эквивалентная запись выглядит так `implementation 'com.aspose:aspose-words:24.9'`.

Зависимость добавит классы `Document`, `Chart` и `ChartType`, которые потребуются для работы с диаграммами.

## Шаг 2: Загрузите целевой документ

Вы можете начать с существующего файла `.docx` или создать новый пустой документ. Пример ниже загружает шаблон `input.docx`, расположенный в папке `src/main/resources`.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

Если файл не существует, Aspose.Words автоматически создаст новый пустой документ при вызове `new Document()` без указания имени файла.

## Шаг 3: Создайте круговую диаграмму и вставьте её в документ

Aspose.Words рассматривает диаграмму как форму, которую можно разместить в любом месте, где может находиться абзац. Следующий код создаёт **круговую диаграмму**, добавляет одну серию данных и вставляет диаграмму после первого абзаца.

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**Почему этот шаг важен:**  
* `ChartType.PIE` указывает Aspose.Words отрисовать традиционную круговую диаграмму.  
* Добавление серии с метками категорий и числовыми значениями автоматически заполняет сектора.  
* Вставка диаграммы как дочернего элемента `Paragraph` сохраняет поток документа.

## Шаг 4: Взрыв первого сектора для выделения

*Взрывной сектор* привлекает внимание к определённому пункту данных. API предоставляет метод `setExplode(boolean)` у объекта `ChartSeries`. Установка его для первой серии (индекс 0) делает первый сектор выпадающим.

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **Распространённый вопрос:** *Что если у меня несколько серий?*  
> Вы можете обратиться к конкретной серии по её индексу, например `pieChart.getSeries().get(1).setExplode(true)` для второй серии.

## Шаг 5: Преобразуйте круговую диаграмму в пончик, задав размер отверстия

Пончик‑диаграмма — это по сути круговая диаграмма с полой серединой. Aspose.Words позволяет задать размер отверстия в процентах от радиуса диаграммы.

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

Метод `setHoleSize` принимает значения от **0** (обычная круговая диаграмма) до **100** (полностью пустая). Значение около **30‑40** даёт визуально сбалансированный пончик.

## Шаг 6: Сохраните и проверьте результат

После всех изменений сохраните документ. Следующая строка записывает файл в папку `output`.

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### Ожидаемый результат

Откройте `final-pie-doughnut.docx` в Microsoft Word:

* Пончик‑диаграмма появляется там, где был первый абзац.  
* Сектор «Apples» взорван (слегка отделён от остальных).  
* Диаграмма показывает четыре сектора с метками *Apples*, *Bananas*, *Cherries*, *Dates* и процентами, которые вы задали.

Если вам нужен вывод в PDF, измените `SaveFormat` на `SaveFormat.PDF`.

## Обработка граничных случаев и вариантов

### Добавление нескольких серий

Если требуется несколько серий (например, сложенный пончик), добавляйте их последовательно:

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### Пользовательские цвета

Можно задать цвет каждому сектору через `ChartDataPoint.setFillFormat().setSolidFillColor()`:

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### Работа с существующей диаграммой

Если документ уже содержит диаграмму и вы хотите лишь изменить её, найдите форму диаграммы:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### Обработка лицензии

Aspose.Words требует лицензии для использования в продакшене. Поместите файл `Aspose.Words.lic` в classpath и загрузите его при старте приложения:

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

Отсутствие лицензии добавит водяной знак в сгенерированный документ.

## Полный, исполняемый пример

Ниже приведён полностью готовый Java‑класс, включающий каждый описанный шаг. Скопируйте его в `src/main/java/com/example/AddPieChart.java` и запустите `mvn compile exec:java`.

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

Запуск программы создаёт описанный ранее пончик‑диаграмму. При необходимости измените `categories`, `values` или `holeSize` под свои данные.

## Заключение

Теперь вы знаете, как **добавить круговую диаграмму в документ Word** с помощью Java и Aspose.Words. В руководстве рассмотрены загрузка документа, создание круговой диаграммы, взрыв сектора, преобразование диаграммы в пончик и обработка распространённых вариантов, таких как несколько серий, пользовательские цвета и существующие диаграммы. На этой основе вы можете создавать инструменты автоматической генерации отчетов, динамические презентации или внедрять богатые визуализации непосредственно в файлы Word.

### Что изучать дальше

* **add bar chart to Word document** – аналогичные шаги, но используйте `ChartType.BAR`.  
* **customize chart legends and titles** – используйте `pieChart.getTitle().setText("...")` и `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`.  
* **export the Word document as PDF** – измените `SaveFormat` на `PDF` для готовых к распространению файлов.  
* **populate chart data from a database** – замените статические массивы результатами JDBC‑запросов.

Не стесняйтесь экспериментировать с различными типами диаграмм, источниками данных и параметрами оформления. Приятного кодинга!

## Что вам следует изучить дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}