---
category: general
date: 2026-10-07
description: Узнайте, как создать круговую диаграмму в Word, добавить серии данных
  и сохранить её в формате PNG с помощью Java. Следуйте пошаговому руководству для
  быстрого результата.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: ru
lastmod: 2026-10-07
og_description: 'Быстро создайте круговую диаграмму в Word: в этом руководстве показано,
  как добавить серии данных, сгенерировать диаграмму и сохранить её в Word как изображение
  (PNG). Следуйте полному примеру кода.'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: Создайте круговую диаграмму в Word и экспортируйте её в PNG – руководство
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: Как создать круговую диаграмму в Word и сохранить её в формате PNG
url: /ru/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать круговую диаграмму в Word и сохранить её как PNG

Если вам нужно **создать круговую диаграмму** внутри файла Microsoft Word, это руководство покажет, как сделать это с помощью Java. Вы также узнаете, как **добавить серии данных** к диаграмме и **сохранить диаграмму как PNG**, чтобы визуализацию можно было использовать за пределами Word.

Создание диаграммы непосредственно в документе избавляет вас от необходимости экспортировать данные в отдельный графический инструмент. К концу этого руководства у вас будет полностью функционирующий файл Word, содержащий круговую диаграмму и соответствующее PNG‑изображение на диске.

## Требования

* Java 17 или более поздняя версия установленa.
* Библиотека **GroupDocs.Viewer for Java** (или совместимая библиотека, предоставляющая классы `Document`, `Chart`, `ChartType` и `ImageSaveOptions`).
* Проект Maven или Gradle, в который можно добавить зависимость библиотеки.
* Входной документ Word (`input.docx`), расположенный в папке, к которой можно обратиться из кода.

Если вы используете Maven, добавьте зависимость (замените `VERSION` на последнюю версию):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## Как создать круговую диаграмму в Word

Суть решения состоит из трёх действий:

1. Загрузить исходный файл `.docx`.
2. **Добавить серии данных** в новый объект `Chart` типа `PIE`.
3. **Сохранить диаграмму как PNG**, чтобы получить файл изображения рядом с документом Word.

Ниже каждый шаг подробно объясняется, после чего следует точный Java‑код, который вам нужен.

### Шаг 1: Загрузить исходный документ

Необходимо открыть файл Word, в котором будет размещена диаграмма. Класс `Document` считывает содержимое `.docx` в память.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Почему это важно*: Загрузка документа создаёт изменяемую модель. Все последующие операции с диаграммой изменяют это представление в памяти, которое затем сохраняется обратно на диск.

### Шаг 2: Добавить серии данных в диаграмму

Создание **круговой диаграммы** начинается с экземпляра `Chart`. Конструктор принимает родительский `Document` и тип диаграммы (`ChartType.PIE`). После создания объекта диаграммы вы заполняете его числовыми значениями и необязательными метками.

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*Почему это важно*: Метод `add` **добавляет серии данных** в диаграмму. Каждая запись в `values` становится сектором круговой диаграммы, а `categories` предоставляют подписи легенды. Вы можете задать любое количество точек; библиотека автоматически вычислит углы секторов.

### Шаг 3: Сохранить диаграмму как PNG

После того как диаграмма стала частью документа, вы можете экспортировать её визуальное представление. Метод `save` у базового объекта диаграммы записывает PNG‑файл в файловую систему.

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*Почему это важно*: Сохранение диаграммы как PNG даёт растровое изображение, которое можно встраивать в веб‑страницы, электронные письма или отчёты без необходимости иметь оригинальный файл Word. Объект `ImageSaveOptions` позволяет управлять форматом, разрешением и другими параметрами экспорта.

## Создание круговой диаграммы в Word – настройка внешнего вида

Помимо базовых шагов, вы можете захотеть настроить цвета, заголовки или подписи данных. Большинство библиотек предоставляют объект `ChartOptions` или аналогичный. Ниже приведён быстрый пример, который добавляет заголовок и меняет цвета секторов:

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

Эти настройки необязательны, но демонстрируют, как можно **создать круговую диаграмму в Word**, соответствующую вашему бренду.

## Сохранить диаграмму Word как изображение – альтернативные подходы

Если вам нужен только образ и не требуется диаграмма внутри документа, вы можете пропустить вставку формы диаграммы в файл Word и сразу вызвать метод `save` после создания диаграммы. Код остаётся тем же; просто опустите шаги, добавляющие диаграмму в тело документа.

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

Эта техника полезна, когда вы генерируете множество диаграмм в пакетном процессе и вам важен только PNG‑вывод.

## Полный исполняемый пример

Скопируйте следующий класс в ваш проект, скорректируйте пути к файлам и запустите его. Программа выполнит:

1. Загрузит `input.docx`.
2. **Создаст круговую диаграмму**, **добавит серии данных** и внедрит её в документ.
3. **Сохранит диаграмму как PNG** (`radial.png`).
4. Сохранит изменённый файл Word как `output.docx`.



## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, основанные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и изучить альтернативные подходы к реализации в ваших проектах.

- [Как создать столбчатую диаграмму с помощью Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Создать точечную диаграмму Word с помощью Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Вставить столбчатую диаграмму в Word с помощью Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}