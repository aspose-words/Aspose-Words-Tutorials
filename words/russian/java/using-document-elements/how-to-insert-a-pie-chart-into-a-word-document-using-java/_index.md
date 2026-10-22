---
category: general
date: 2026-09-27
description: Узнайте, как вставить круговую диаграмму в документ Word с помощью Java,
  создать её в Word и отобразить проценты на диаграмме для ясного понимания данных.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: ru
lastmod: 2026-09-27
og_description: Как вставить круговую диаграмму в документ Word с помощью Java. Это
  руководство покажет, как создать круговую диаграмму в Word, отобразить проценты
  на диаграмме и добавить линии‑выноски.
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: Как вставить круговую диаграмму в документ Word с помощью Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: Как вставить круговую диаграмму в документ Word с помощью Java
url: /ru/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как вставить круговую диаграмму в документ Word с помощью Java

Если вам нужно **how to insert pie chart** в файл Word, это руководство проведёт вас через весь процесс. Вы увидите, как **create pie chart in Word**, отобразить проценты на каждом сегменте и добавить линии‑выноски для аккуратного вида.

Автоматизация Word часто кажется тяжёлой, но с Aspose.Words for Java вы можете программно генерировать полностью отформатированные документы. К концу этого руководства у вас будет исполняемый фрагмент Java, который создаёт документ Word, содержащий стилизованную круговую диаграмму.

## Предварительные требования

- Java 17 или новее установлен
- Maven или Gradle для управления зависимостями
- Aspose.Words for Java (версия 23.11 или новее), добавленная в ваш проект
- Базовое знакомство с синтаксисом Java

Вам не требуется предварительный опыт работы с API диаграмм; нижеописанные шаги охватывают всё от настройки проекта до конечного результата.

## Шаг 1: Настройка зависимости Maven

Добавьте библиотеку Aspose.Words в ваш `pom.xml`. Эта единственная зависимость предоставляет доступ к `Document`, `DocumentBuilder` и классам диаграмм.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

Если вы используете Gradle, эквивалент выглядит так:

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **Pro tip:** Используйте последнюю стабильную версию, чтобы получать исправления ошибок и новые возможности диаграмм.

## Шаг 2: Создание нового документа и билдера

`Document` представляет файл Word, а `DocumentBuilder` позволяет вставлять содержимое. Это основа для **add chart to word document**.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Теперь билдер готов размещать объекты в любой части документа.

## Шаг 3: Вставка круговой диаграммы

Aspose.Words поддерживает несколько типов диаграмм; мы выбираем `ChartType.PIE`. Размер задаётся в пунктах (1 пункт = 1/72 дюйма).

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

На данном этапе диаграмма содержит серию данных по умолчанию с заполнителями. При необходимости вы можете позже заменить эти значения.

## Шаг 4: Доступ к серии диаграммы

Круговая диаграмма имеет одну серию, содержащую значения секторов. Получите её, чтобы применить форматирование.

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## Шаг 5: Выделить (взрыв) первый сектор

Взрыв сектора привлекает внимание к определённой точке данных. Это распространённый визуальный приём, когда нужно выделить ключевой показатель.

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## Шаг 6: Показать проценты на каждом секторе

Отображение процентов непосредственно на диаграмме улучшает восприятие данных. Это удовлетворяет требование **show percentages on pie chart**.

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## Шаг 7: Добавить линии‑выноски для более чётких подписей

Линии‑выноски соединяют подписи секторов с их соответствующими частями, устраняя неоднозначность. Это реализует **how to add leader lines**.

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## Шаг 8: Сохранить документ

Наконец, запишите документ на диск. Вы можете выбрать любую папку, в которую у вас есть права записи.

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

Запуск программы создаёт `output/PieFormatted.docx`. Откройте файл в Microsoft Word, и вы увидите круговую диаграмму, где:

- Первый сектор взорван.
- Каждый сектор отображает своё процентное значение.
- Линии‑выноски указывают от процентов к соответствующим секторам.

### Ожидаемый результат

![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image alt="Отформатированная круговая диаграмма, вставленная в документ Word"}

Скриншот (alt‑текст использует основной ключевой запрос) иллюстрирует конечный вид: чистая, основанная на данных круговая диаграмма, готовая для отчётов, предложений или панелей мониторинга.

## Общие варианты и граничные случаи

### Изменение значений секторов

Если вам нужны пользовательские данные, замените значения серии по умолчанию:

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### Несколько серий (кольцевая диаграмма)

Хотя простая круговая диаграмма имеет одну серию, Aspose.Words также поддерживает кольцевые диаграммы с несколькими сериями. Замените `ChartType.PIE` на `ChartType.DONUT` и повторите шаги настройки серии.

### Экспорт в PDF

Если ваш последующий процесс требует PDF, вызовите `doc.save("output/PieFormatted.pdf");` после построения диаграммы. Визуальное оформление останется идентичным.

## Полный исходный код

Ниже приведён полный, автономный Java‑файл, который вы можете скопировать и вставить в свою IDE.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

Скомпилируйте и запустите программу с помощью `mvn compile exec:java -Dexec.mainClass=PieChartExample` (или эквивалентной команды Gradle). Сгенерированный файл Word будет содержать полностью отформатированную круговую диаграмму.

## Заключение

Теперь вы знаете **how to insert pie chart** в документ Word с помощью Java, как **create pie chart in Word**, как **show percentages on pie chart**, и как **add chart to word document** с линиями‑выносками. Полный пример демонстрирует каждый шаг, объясняет, почему код написан именно так, и даёт советы по настройке.

Далее вы можете изучить:

- Добавление подписей данных с пользовательскими шрифтами (вариации **show percentages on pie chart**)
- Комбинирование нескольких диаграмм в одном документе (случай использования **add chart to word document**)
- Автоматизацию генерации отчётов с таблицами и диаграммами вместе

Не стесняйтесь экспериментировать с цветами, порядком секторов или экспортом в PDF. Приятного кодинга!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, которые опираются на техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Как создать столбчатую диаграмму с помощью Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Скрыть оси диаграммы в документе Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Создать линейную диаграмму в Word с помощью Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}