---
category: general
date: 2026-09-11
description: Как редактировать график в документе Word с помощью Java — узнайте, как
  обновлять настройки графика, включать сетку графика, изменять параметры графика
  и сохранять обновлённый документ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- update chart settings
- save updated document
- change chart options
- enable chart gridlines
language: ru
lastmod: 2026-09-11
og_description: Как редактировать диаграмму в документе Word с помощью Java. Следуйте
  этому руководству, чтобы обновить настройки диаграммы, включить сетку диаграммы,
  изменить параметры диаграммы и сохранить обновлённый документ.
og_image_alt: Screenshot of a Word document showing a chart with gridlines enabled
og_title: Как редактировать диаграмму в документе Word с помощью Java – полное руководство
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  headline: How to edit chart in a Word document using Java
  type: TechArticle
- description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  name: How to edit chart in a Word document using Java
  steps:
  - name: Expected result
    text: 'When you open `output.docx`:'
  - name: What if the document has no chart?
    text: 'Attempting to cast a non‑chart shape will throw a `ClassCastException`.
      Guard against this by checking the shape type:'
  - name: How to edit a specific chart instead of the first one?
    text: 'Iterate through `shapes` and match a known title or an alternative identifier:'
  - name: Can I disable gridlines again later?
    text: 'Yes, simply set the property to `false`:'
  - name: Does this work with `.doc` (binary) files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. However, some newer chart features (like graduations) are only
      stored in the OOXML format, so you’ll see the effect only when saving as `.docx`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Как редактировать диаграмму в документе Word с помощью Java
url: /ru/java/using-document-elements/how-to-edit-chart-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как редактировать диаграмму в документе Word с помощью Java

Если вам нужно **как редактировать диаграмму** в файле Word, это руководство покажет точные шаги. Вы узнаете, как обновлять настройки диаграммы, включать сетку диаграммы, менять параметры диаграммы и, наконец, **сохранить обновлённый документ** без потери форматирования.

Работа с диаграммами программно часто ощущается как работа с чёрным ящиком, особенно когда требуется подправить визуальные детали, такие как деления или сетка. Этот учебник охватывает всё, что нужно знать, от загрузки документа до сохранения изменений. Внешние инструменты не требуются — только библиотека Aspose.Words for Java (версия 24.9 или новее).

К концу этой статьи вы сможете:

* Загрузить файл `.docx`, содержащий диаграмму.
* Найти форму диаграммы и изменить её свойства.
* Включить сетку диаграммы (деления) и настроить другие параметры.
* **Сохранить обновлённый документ** в новый файл.

## Предварительные требования

* Java 17 или новее, установленная на вашем компьютере.  
* Maven или Gradle для управления зависимостями.  
* Aspose.Words for Java 24.9+ (версия, в которой появился метод `setShowGraduations`).  
* Документ Word (`input.docx`), уже содержащий хотя бы одну диаграмму.

Если вы не знакомы с Aspose.Words, представьте её как полнофункциональное API, позволяющее программно читать, изменять и записывать документы Word — аналогично работе с DOM в веб‑браузере.

## Шаг 1: Настройте проект и импортируйте библиотеку

Создайте новый Maven‑проект или добавьте зависимость в существующий:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **Pro tip:** Используйте последнюю стабильную версию, чтобы иметь метод `setShowGraduations`. Более старые версии не скомпилируются.

## Шаг 2: Загрузите документ Word, содержащий диаграмму

Первое действие в любом **как редактировать диаграмму** процессе — загрузить исходный файл. Aspose.Words представляет весь документ классом `Document`.

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // Replace with the actual path to your input file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document into memory
        Document doc = new Document(inputPath);
```

Объект `Document` даёт доступ ко всем узлам внутри файла, включая формы, таблицы и абзацы.  

## Шаг 3: Найдите первую форму диаграммы в документе

Диаграммы хранятся как узлы `Shape`, чей рендерер — `Chart`. Чтобы отредактировать диаграмму, сначала получите этот узел.

```java
        // Find all shape nodes (including charts)
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);

        // Assume the first shape is a chart; adjust the index if needed
        Shape chartShape = (Shape) shapes.get(0);

        // Cast the shape renderer to Chart
        Chart chart = (Chart) chartShape.getChart();
```

Если в документе несколько диаграмм, пройдитесь по `shapes` и проверьте `chartShape.getChart() != null` перед приведением типа. Это предотвращает `ClassCastException` и гарантирует, что вы **изменяете параметры диаграммы** только у действительных объектов диаграмм.

## Шаг 4: Включите сетку диаграммы (деления) — новое свойство в версии 24.9

Свойство `setShowGraduations` переключает видимость мелкой сетки по оси значений. Включение её часто улучшает читаемость плотных наборов данных.

```java
        // Turn on gridlines (graduations) for the value axis
        chart.setShowGraduations(true);
```

> **Почему это важно:** Сетка даёт зрителям визуальную ориентацию для каждой точки данных, упрощая выявление тенденций. По умолчанию значение `false`, поэтому её необходимо явно включать при необходимости.

Вы также можете настроить другие аспекты, такие как крупная сетка, подписи осей или расположение легенды. Ниже пример изменения заголовка диаграммы и позиции легенды — оба являются частью **изменения параметров диаграммы**.

```java
        // Change the chart title
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);

        // Move the legend to the bottom
        chart.getLegend().setPosition(LegendPosition.BOTTOM);
```

## Шаг 5: Сохраните документ с обновлёнными настройками диаграммы

После изменения диаграммы сохраните изменения. Этот шаг завершает фазу **сохранения обновлённого документа**.

```java
        // Replace with the desired output path
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // Save the modified document
        doc.save(outputPath);
        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

Запуск программы создаст `output.docx`, где диаграмма теперь отображает сетку, новый заголовок и перемещённую легенду. Откройте файл в Microsoft Word, чтобы проверить визуальные изменения.

## Полный исходный код (готов к запуску)

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document that contains a chart
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Locate the first chart shape in the document
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
        Shape chartShape = (Shape) shapes.get(0);
        Chart chart = (Chart) chartShape.getChart();

        // 3️⃣ Enable chart gridlines (graduations)
        chart.setShowGraduations(true);

        // 4️⃣ Change chart options (title and legend)
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);
        chart.getLegend().setPosition(LegendPosition.BOTTOM);

        // 5️⃣ Save the document with the updated chart settings
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

### Ожидаемый результат

При открытии `output.docx`:

* Диаграмма отображает мелкую сетку по оси значений.  
* Заголовок читается **«Sales Overview 2026»**.  
* Легенда расположена внизу диаграммы.

Если у исходной диаграммы уже была сетка, визуальный вид останется без изменений, подтверждая, что код **идемпотентен**.

## Часто задаваемые вопросы и обработка граничных случаев

### Что делать, если в документе нет диаграммы?

Попытка привести форму, не являющуюся диаграммой, вызовет `ClassCastException`. Защищайтесь, проверяя тип формы:

```java
if (chartShape.getShapeType() == ShapeType.CHART) {
    Chart chart = (Chart) chartShape.getChart();
    // proceed with modifications
}
```

### Как отредактировать конкретную диаграмму, а не первую?

Пройдитесь по `shapes` и сопоставьте известный заголовок или альтернативный идентификатор:

```java
for (Node node : shapes) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart c = (Chart) shape.getChart();
        if ("Revenue Q1".equals(c.getTitle().getText())) {
            // modify this chart
        }
    }
}
```

### Можно ли позже отключить сетку?

Да, просто установите свойство в `false`:

```java
chart.setShowGraduations(false);
```

### Работает ли это с файлами `.doc` (бинарными)?

Aspose.Words абстрагирует формат файла, поэтому тот же код работает с `.doc` и `.docx`. Однако некоторые новые функции диаграмм (например, деления) сохраняются только в формате OOXML, поэтому эффект будет виден только при сохранении как `.docx`.

## Советы для production‑ready кода

* **Проверяйте пути ввода** — используйте `Files.exists(Paths.get(inputPath))` перед загрузкой.  
* **Оборачивайте вызовы API** в блоки try‑catch, чтобы выводить детали `Exception`, особенно при работе с повреждёнными документами.  
* **Освобождайте ресурсы** — хотя Aspose.Words управляет памятью, вызов `doc.close()` (или использование try‑with‑resources, если доступно) может освободить нативные дескрипторы раньше.  
* **Проверка версии** — убедитесь, что версия библиотеки во время выполнения ≥ 24.9 перед вызовом `setShowGraduations`. При необходимости можно запросить `License.getVersion()` для программной проверки.

## Заключение

Теперь вы знаете **как редактировать диаграммы** в документе Word с помощью Java. Процесс — загрузить документ, найти диаграмму, включить сетку, изменить параметры диаграммы и **сохранить обновлённый документ** — покрывает самые распространённые сценарии программного управления диаграммами.  

Далее вы можете исследовать дополнительные настройки, такие как изменение цветов серий данных, применение стилей диаграмм или экспорт диаграммы в изображение. Все эти задачи следуют той же схеме: получить экземпляр `Chart`, скорректировать его свойства и **сохранить обновлённый документ**.

Удачной разработки, экспериментируйте с другими настройками диаграмм, чтобы они соответствовали вашим требованиям к отчётности!

## Что следует изучить дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Как создать столбчатую диаграмму с помощью Aspose.Words для Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Как сохранить документ как PDF с помощью Aspose.Words для Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Установить параметры по умолчанию для подписей данных в диаграмме](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}