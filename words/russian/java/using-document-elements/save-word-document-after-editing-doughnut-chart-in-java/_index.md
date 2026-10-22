---
category: general
date: 2026-09-11
description: Сохраните документ Word после редактирования кольцевой диаграммы с помощью
  Aspose.Words for Java. Узнайте, как изменить размер отверстия кольца, повернуть
  кольцевую диаграмму и изменить свойства кольцевой диаграммы.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: ru
lastmod: 2026-09-11
og_description: Сохраните документ Word после редактирования кольцевой диаграммы с
  помощью Aspose.Words для Java. В этом руководстве показано, как изменить размер
  отверстия кольца, повернуть кольцевую диаграмму и настроить внешний вид диаграммы.
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: Сохранить документ Word после редактирования кольцевой диаграммы — руководство
  по Java
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: Сохранить документ Word после редактирования кольцевой диаграммы в Java
url: /ru/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Сохранить документ Word после редактирования кольцевой диаграммы в Java

Если вам нужно **save Word document**, содержащий настроенную кольцевую диаграмму, это руководство покажет вам, как это сделать. Всего в несколько строк Java вы можете изменить отверстие кольца, повернуть кольцевую диаграмму и затем записать результат обратно на диск.

Вы увидите полностью готовый, исполняемый пример, использующий Aspose.Words for Java, а также советы по работе с несколькими диаграммами, проверке типов узлов и избежанию распространённых ошибок. Внешние ссылки не требуются — всё необходимое включено.

## Предварительные требования

- Java 17 или новее установлен
- Maven или Gradle для управления зависимостями
- Aspose.Words for Java (версия 23.9 или новее) добавлен в ваш проект  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- Файл Word (`input.docx`), содержащий одну кольцевую диаграмму

## Шаг 1: Загрузка документа Word

Первый шаг — открыть исходный файл. Этот шаг необходим, потому что все последующие операции работают с объектом `Document` в памяти.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Почему?** Загрузка документа создаёт DOM‑представление, позволяющее обходить формы, таблицы и диаграммы. Если файл не может быть открыт, Aspose.Words бросает исключение, поэтому вы сразу узнаёте, что путь неверен.

## Шаг 2: Поиск формы с кольцевой диаграммой

Диаграмма хранится внутри узла `Shape`. Мы получаем первую форму, содержащую диаграмму, и приводим её рендерер к типу `Chart`.

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **Почему?** Проверка `isChart()` предотвращает `ClassCastException`, когда документ содержит изображения или другие формы перед диаграммой. Это делает код надёжным для документов со смешанным содержимым.

## Шаг 3: Изменение размера отверстия кольца  

Теперь мы редактируем отверстие кольца. Метод `setHoleSize` ожидает процент от радиуса диаграммы (10 – 90).

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **Почему?** Изменение отверстия кольца (`change doughnut hole` / `change chart hole size`) позволяет подчеркнуть или уменьшить центральную область. Значения вне диапазона 10‑90 % игнорируются API.

## Шаг 4: Поворот кольцевой диаграммы  

Чтобы контролировать, где начинается первый сектор, задайте угол первого сектора. Это фактически **rotate doughnut chart**.

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **Почему?** Поворот диаграммы полезен, когда нужно, чтобы определённый сектор оказался вверху или соответствовал требованиям дизайна.

## Шаг 5: Сохранение обновлённого документа  

Наконец, запишите изменения в новый файл. Это момент, когда вы **save Word document** с отредактированной диаграммой.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Ожидаемый результат:** `output.docx` содержит оригинальное содержимое, но кольцевая диаграмма теперь имеет отверстие 30 % и её первый сектор начинается под углом 45 °. Открытие файла в Microsoft Word покажет преобразованную диаграмму.

## Полный рабочий пример

Ниже представлен полный код программы, который вы можете скопировать и вставить в свою IDE. Он включает все импорты и обработку ошибок, необходимые для безопасного **edit doughnut chart** и **save Word document**.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Ожидаемый вывод

Когда вы откроете `output.docx`:

- Отверстие в центре кольцевой диаграммы занимает примерно одну треть радиуса диаграммы.  
- Первый сектор начинается под углом 45°, сдвигая всю диаграмму по часовой стрелке.  

Оба визуальных изменения сразу отображаются в Word.

## Распространённые варианты и граничные случаи

| Ситуация | Как решить |
|-----------|----------------|
| **Multiple charts** | Iterate through `doc.getChildNodes(NodeType.SHAPE, true)` and filter `shape.isChart()`; apply `setHoleSize` / `setFirstSliceAngle` to each `Chart`. |
| **Chart is not a doughnut** | Check `chart.getType()`; only call `setHoleSize` when `chart.getType() == ChartType.DOUGHNUT`. |
| **Need to change hole size dynamically** | Compute the desired percentage based on data values, then call `setHoleSize(computedValue)`. |
| **Saving to a stream** | Use

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, которые опираются на техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Как создать столбчатую диаграмму с помощью Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Как сохранить документ в PDF с помощью Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Сохранить Word с паролем, используя Aspose.Words for Java](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}