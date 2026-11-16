---
category: general
date: 2026-11-15
description: Узнайте, как создать круговую диаграмму в документе Word и сохранить
  файл docx в PDF с помощью Java. В этом руководстве также рассматривается конвертация
  Word в PDF и добавление диаграммы.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: ru
lastmod: 2026-11-15
og_description: Создайте круговую диаграмму в файле Word и сохраните docx как PDF
  с помощью Java. Следуйте этому пошаговому руководству, чтобы преобразовать Word
  в PDF и добавить диаграммы.
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: Создайте круговую диаграмму в Word и сохраните docx в PDF – руководство
  по Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: Как создать круговую диаграмму в Word и сохранить документ в формате PDF
url: /ru/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать круговую диаграмму в Word и сохранить docx как PDF

Если вам нужно **создать круговую диаграмму** внутри документа Word, а затем **сохранить docx как PDF**, этот учебник покажет, как это сделать. Вы увидите полностью готовый, исполняемый пример, который конвертирует файл .docx в PDF, внедряя при этом круговую диаграмму, так что сможете ответить на вопрос «как добавить диаграмму», не ищя фрагменты кода в разных местах.

В этом руководстве вы научитесь:

* Загружать существующий *.docx* (или начинать с нуля)  
* Использовать Aspose.Words for Java для **создания круговой диаграммы** и заполнения данными  
* **Сохранять docx как PDF** с корректно отрисованной диаграммой  
* Понимать нюансы **конвертации Word в PDF**, когда в документе есть диаграммы  

Шаги работают с Aspose.Words 2024‑x.x и Java 17, но концепции применимы к любой библиотеке, поддерживающей работу с диаграммами Word.

## Требования

Перед тем как начать, убедитесь, что у вас есть:

| Требование | Почему это важно |
|------------|-------------------|
| Java 17 (или новее) | Требуется последней версии Aspose.Words JAR |
| Инструмент сборки Maven или Gradle | Упрощает управление зависимостями |
| Aspose.Words for Java (последняя версия) | Предоставляет классы `Document`, `Chart` и `ChartType` |
| Входной **.docx** файл (или пустой документ) | Диаграмма будет вставлена в этот файл |

Добавьте зависимость Aspose.Words в ваш `pom.xml` (Maven) или `build.gradle` (Gradle). Пример для Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Шаг 1: Загрузить документ Word (или создать новый)

Первое действие — получить экземпляр `Document`. Если у вас уже есть шаблон, укажите его путь; иначе создайте пустой документ.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*Зачем это нужно?* Объект `Document` является контейнером для всего содержимого Word, включая диаграммы. Загрузка существующего файла позволяет сохранить окружающий текст и стили, добавив новый визуальный элемент.

## Шаг 2: **Создать круговую диаграмму** – ядро «как создать диаграмму»

Теперь мы создаём объект `Chart` с типом `ChartType.PIE`. Это автоматически создаёт заполнитель для круговой диаграммы, который позже можно заполнить данными.

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*Объяснение*: `ChartType.PIE` указывает Aspose.Words использовать шаблон круговой диаграммы. Диаграмма добавляется в тело документа, поэтому появляется в нужном месте. Это удовлетворяет требование «как добавить диаграмму» одним вызовом.

## Шаг 3: Заполнить диаграмму – ответ на «как добавить диаграмму» данными

Круговая диаграмма бессмысленна без данных серии. Используйте коллекцию `Series`, чтобы добавить категории и значения.

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*Почему это важно*: Каждый вызов `add` создаёт отдельный сектор круга. Первый аргумент — метка, второй — числовое значение. Их можно заменить динамическими данными из базы данных или CSV‑файла.

### Необязательно: Настроить внешний вид (необязательно, но полезно)

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

Эти правки показывают, как можно **создать диаграмму** с профессиональным видом, не выходя из Java‑кода.

## Шаг 4: **Сохранить docx как PDF** – завершающая часть «конвертации Word в PDF»

После внедрения диаграммы экспортируйте документ в PDF. Aspose.Words рендерит диаграмму как векторную графику, сохраняя качество.

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*Ключевой момент*: Метод `save` автоматически конвертирует файл Word в PDF, обрабатывая растеризацию диаграмм, встраивание шрифтов и разметку страниц. Это реализует цель **сохранить docx как pdf** и демонстрирует надёжный способ **конвертации Word в PDF**, когда в документе присутствуют диаграммы.

### Ожидаемый результат

Запуск программы создаёт `output.pdf`, содержащий:

* Исходное содержимое `input.docx` (если оно было)  
* Полностью отрисованную круговую диаграмму с заголовком *Sales Distribution Q1*  
* Точные проценты секторов, соответствующие данным (40 %, 30 %, 30 %)

Откройте PDF в любом просмотрщике — вы увидите чёткую круговую диаграмму, идентичную той, что в файле Word.

## Распространённые проблемы и как их избежать

| Проблема | Причина | Решение |
|----------|---------|----------|
| Диаграмма отображается пустой в PDF | Отсутствуют настройки шрифтов или рендеринга диаграмм | Убедитесь, что используете последнюю версию Aspose.Words; она включает необходимые библиотеки рендеринга. |
| Значения данных округляются неверно | Используются целочисленные значения с большими числами | Передайте `double` значения или масштабируйте числа перед добавлением в серию. |
| Полученный PDF слишком большой | Встроенные изображения с высоким DPI | Установите `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)`, если также вставляете изображения. |
| «конвертация Word в PDF» бросает `UnsupportedOperationException` | Используется устаревшая версия Java (< 11) | Обновите до Java 17 или новее, требуемой Aspose.Words 24.x. |

## Совет профессионала: Повторное использование кода создания диаграммы

Если нужно добавить несколько диаграмм в один документ, вынесите код построения диаграммы в вспомогательный метод:

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

Теперь вы можете вызывать `doc.getFirstSection().getBody().appendChild(createPieChart(...));` для каждого набора данных, поддерживая принцип DRY (Don’t Repeat Yourself).

## Заключение

Теперь вы знаете, как **создать круговую диаграмму** внутри документа Word, заполнить её данными и **сохранить docx как PDF** с помощью Java. Этот сквозной пример охватывает весь рабочий процесс **конвертации Word в PDF**, отвечает на вопрос **как добавить диаграмму** и демонстрирует **как создать диаграмму** программно.  

Дальше вы можете исследовать:

* Добавление столбчатых или линейных диаграмм (`ChartType.BAR`, `ChartType.LINE`) – ещё один сценарий **как создать диаграмму**.  
* Экспорт в другие форматы, такие как PNG или HTML (`SaveFormat.PNG`, `SaveFormat.HTML`).  
* Динамическое создание входного документа с таблицами или заполнителями перед вставкой диаграмм.

Экспериментируйте с различными наборами данных, параметрами стилей или даже вставляйте несколько диаграмм на страницу. Приятного кодинга!

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to save word as pdf and create accessible PDF in Java](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [How to create chart in Word with Java and Aspose.Words](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}