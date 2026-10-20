---
category: general
date: 2026-09-18
description: Научитесь создавать документ Word и вставлять круговую диаграмму с помощью
  Aspose.Words для Java. Включает шаги по повороту круговой диаграммы и генерации
  файла Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: ru
lastmod: 2026-09-18
og_description: Создайте документ Word и вставьте круговую диаграмму с помощью Java.
  Следуйте этому руководству, чтобы вращать диаграмму, вырывать сектора и генерировать
  файл Word.
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: Создайте документ Word с круговой диаграммой — пошаговое руководство на
  Java
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Как создать документ Word с круговой диаграммой в Java
url: /ru/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать документ Word с круговой диаграммой на Java

Если вам нужно **создать документ Word**, визуализирующий данные, это руководство покажет, как сделать это с помощью Aspose.Words for Java. Вы узнаете, как вставить круговую диаграмму, «взрыв» сектора, повернуть диаграмму и, наконец, **сгенерировать файл Word**, который можно открыть в Microsoft Word.

Создание отчетов, комбинирующих текст и диаграммы, не требует отдельного графического инструмента. К концу этого урока у вас будет полностью готовая, исполняемая программа, создающая файл .docx с полностью настроенной круговой диаграммой.

## Предварительные требования

- Java 17 или новее (код также компилируется с Java 8+)
- Maven или Gradle для управления зависимостями
- Лицензия Aspose.Words for Java (бесплатная пробная версия подходит для этого примера)
- Базовые знания синтаксиса Java

## Шаг 1: Настройка проекта Maven

Создайте новый проект Maven и добавьте зависимость Aspose.Words в `pom.xml`:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **Совет:** Следите за актуальностью номера версии; новые релизы добавляют улучшения типов диаграмм и исправления ошибок.

## Шаг 2: Создание нового документа Word

Первая операция при **создании документа Word** программно — это создание объекта `Document`. Этот объект представляет весь файл .docx в памяти.

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

Класс `Document` является точкой входа для всех функций обработки Word. На данном этапе файл еще не записан на диск; всё происходит в ОЗУ до вызова `save`.

## Шаг 3: Как вставить круговую диаграмму

`DocumentBuilder` позволяет добавлять содержимое в документ. С помощью `insertChart` можно **вставить круговую диаграмму** напрямую.

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` указывает Aspose.Words создать круговую диаграмму. Размеры задаются в пунктах (1 pt ≈ 1/72 in). После этого вызова диаграмма появляется в новом абзаце.

## Шаг 4: Заполнение диаграммы данными

Круговая диаграмма требует набор значений. Здесь мы добавляем три категории: «Apples», «Bananas» и «Cherries».

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

Метод `add` формирует серию и автоматически создает элементы легенды. Этот шаблон можно использовать для любого числового набора данных.

## Шаг 5: Выделение первого сектора

«Взрыв» сектора привлекает внимание к определенному значению. Первый сектор (индекс 0) «взрывается» на 20 пунктов.

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

Установка `explode` для серии влияет на всю диаграмму, поэтому только первая точка данных смещается.

## Шаг 6: Как повернуть круговую диаграмму

Поворот диаграммы улучшает визуальный баланс, особенно когда самый большой сектор не находится вверху. Метод `setRotationAngle` принимает значение в градусах.

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

Поворот на 45° смещает начальный угол по часовой стрелке, делая диаграмму более удобочитаемой в большинстве макетов.

## Шаг 7: Сохранение документа и генерация файла Word

Наконец, запишите документ на диск. Этот шаг **генерирует файл Word**, который можно открыть в Microsoft Word, LibreOffice или любом совместимом просмотрщике.

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Метод `save` автоматически определяет расширение .docx и записывает пакет, совместимый с Word. Папка `output` должна существовать, либо её можно создать программно.

### Ожидаемый результат

После запуска программы откройте `output/PieChart.docx`. Вы должны увидеть:

- Одну страницу с круговой диаграммой размером 400 × 300 pt.
- Сектор «Apples», «взрыв» которого составляет 20 pt наружу.
- Весь график повернут на 45° по часовой стрелке.
- Легенду, соответствующую трем категориям фруктов.

## Распространённые варианты и граничные случаи

### Вставка нескольких диаграмм

Если требуется более одной диаграммы, вызовите `builder.insertChart` ещё раз после перемещения курсора:

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### Изменение цветов диаграммы

Цвета секторов можно настроить через коллекцию `getPoints()` серии:

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### Работа с большими наборами данных

Для наборов данных более 10 секторов рекомендуется использовать кольцевую диаграмму (`ChartType.DOUGHNUT`), чтобы визуализация оставалась чистой.

## Заключение

Теперь вы знаете, как **создать документ Word**, **вставить круговую диаграмму**, **повернуть круговую диаграмму** и **сгенерировать файл Word** с помощью Aspose.Words for Java. Полное решение демонстрирует весь рабочий процесс от инициализации документа до окончательного вывода файла, охватывая как «как», так и «почему» каждого шага.

Далее изучайте связанные темы, такие как **как создать данные для круговой диаграммы** из базы данных, добавление подписей к данным или экспорт диаграммы в изображение. Экспериментируйте с различными типами диаграмм (столбчатая, линейная, кольцевая), чтобы расширить свой набор средств автоматизации Word.

## Что вам стоит изучить дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}