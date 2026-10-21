---
category: general
date: 2026-10-04
description: Узнайте, как «взрывать» срез в диаграмме Word, «взрывать» срез круговой
  диаграммы и изменять размер кольцевой диаграммы с пошаговым примером на Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: ru
lastmod: 2026-10-04
og_description: Как взрывать срез в диаграмме Word и настраивать круговые или кольцевые
  диаграммы с помощью Java. Следуйте полному примеру, чтобы изменить диаграмму в Word.
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: Как отделить сектор в диаграмме Word — полное руководство по Java
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Как отделить сектор в диаграмме Word и настроить его внешний вид
url: /ru/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как «взрывать» срез в диаграмме Word и настроить её внешний вид

Если вам нужно **как «взрывать» срез** в диаграмме Word, это руководство покажет точный порядок действий. Будь то подготовка презентации по продажам или финансового отчёта, «взрыв» сектора круговой диаграммы или изменение размера отверстия кольцевой диаграммы поможет выделить самые важные данные. В последующих разделах вы также узнаете, как **модифицировать диаграмму в Word**, **взрывать сектор круговой диаграммы**, **изменять размер кольцевой диаграммы** и **настраивать документы Word с круговыми диаграммами** с помощью Aspose.Words for Java.

В конце этого руководства вы получите полностью готовую к запуску Java‑программу, которая загружает файл `.docx`, «взрывает» первый сектор круговой диаграммы, меняет размер отверстия кольцевой диаграммы и сохраняет результат. Никакие внешние скрипты или ручное редактирование не требуются.

## Предварительные требования

- Java 17 или новее, установленная на вашей машине разработки.  
- Maven 3.6+ (или Gradle) для управления зависимостями.  
- Библиотека Aspose.Words for Java (бесплатная пробная версия подходит для разработки).  
- Документ Word (`input.docx`), содержащий хотя бы одну диаграмму (круговую или кольцевую).

## Шаг 1: Добавьте Aspose.Words в ваш проект

Если вы используете Maven, добавьте следующую зависимость в ваш `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Для Gradle поместите это в `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Держите версию библиотеки актуальной; новые релизы добавляют поддержку дополнительных типов диаграмм и повышают производительность.

## Шаг 2: Загрузите документ Word, содержащий диаграмму

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**Почему это важно:** Загрузка документа создаёт представление в памяти, которое может обходить Aspose.Words. Без этого объекта вы не сможете получить доступ к узлам диаграммы.

## Шаг 3: Получите первую диаграмму в документе

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **Explanation:** `NodeType.SHAPE` охватывает все графические объекты, включая диаграммы. Параметр `true` заставляет Aspose выполнять рекурсивный поиск, гарантируя, что первая диаграмма будет найдена даже если она вложена в таблицу.

## Шаг 4: «Взрыв» первого сектора круговой диаграммы

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**Как это работает:** Метод `setExplosion` принимает числовое значение, определяющее, насколько далеко сектор будет смещён от центра. Значение `20` визуально заметно, но не нарушает макет диаграммы.

## Шаг 5: Регулировка размера отверстия кольцевой диаграммы

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**Почему это полезно:** Большое отверстие кольцевой диаграммы улучшает читаемость при большом количестве точек данных. Метод `setDoughnutHoleSize` ожидает процент (0‑100).

## Шаг 6: Сохраните изменённый документ

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### Ожидаемый результат

- Первый сектор первой круговой диаграммы смещён наружу, делая его более заметным.  
- Если диаграмма является кольцевой, центральное отверстие расширяется до 40 % радиуса диаграммы.  
- Полученный файл `PieChart.docx` можно открыть в Microsoft Word, LibreOffice или любом совместимом просмотрщике, где будут видны внесённые программно визуальные изменения.

## Полный, готовый к запуску пример

Ниже представлен весь код программы в одном блоке. Скопируйте его в `ChartExploder.java`, скорректируйте пути к файлам и запустите командой `mvn compile exec:java` (или через конфигурацию запуска вашей IDE).

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

Запуск этого кода **модифицирует диаграмму в Word**, **взрывает сектор круговой диаграммы** и **изменяет размер кольцевой диаграммы** автоматически.

## Часто задаваемые вопросы и особые случаи

| Вопрос | Ответ |
|----------|--------|
| *Что если документ содержит несколько диаграмм?* | Пример ориентирован на **первую** диаграмму (`NodeType.SHAPE, 0`). Чтобы работать с другими, измените индекс или пройдитесь по `doc.getChildNodes(NodeType.SHAPE, true)` и отфильтруйте по `shape.getChart() != null`. |
| *Можно ли «взорвать» не первый сектор?* | Да. Получите нужную серию через `chart.getSeries().get(seriesIndex)` и вызовите `setExplosion(value)`. Индексы начинаются с нуля. |
| *Работает ли это с файлами Word 2007‑2021?* | Aspose.Words поддерживает `.doc`, `.docx`, `.dot` и `.dotx`. Один и тот же код работает во всех версиях, так как библиотека абстрагирует формат файла. |
| *Что если диаграмма — столбчатая или линейная?* | `setExplosion` и `setDoughnutHoleSize` применимы только к круговым типам диаграмм. Код безопасно пропускает эти операции, если тип диаграммы отличается. |
| *Нужна ли лицензия для Aspose.Words?* | Бесплатная оценочная лицензия снимает ограничение в 30 дней, но добавляет водяной знак. Для продакшн‑использования приобретите лицензию, чтобы убрать водяной знак и получить полный набор функций. |

## Заключение

Теперь вы знаете, **как «взрывать» срез** в диаграмме Word, как **модифицировать диаграмму в Word** и как **изменять размер кольцевой диаграммы** с помощью Aspose.Words for Java. Полный пример демонстрирует весь рабочий процесс — от загрузки документа, поиска диаграммы, применения визуальных настроек до сохранения результата — чтобы вы могли интегрировать эти шаги в любой конвейер отчётности или генерации документов.

**Следующие шаги**

- Исследуйте другие настройки диаграмм, такие как изменение цветов, добавление подписей данных или переключение типа диаграммы (`chart.setChartType(ChartType.BAR_CLUSTERED)`).  
- Скомбинируйте эту логику с Aspose.PDF для создания PDF‑версии того же отчёта.  
- Автоматизируйте процесс для пакета документов, перебирая файлы в каталоге.

Экспериментируйте с различными значениями «взрыва» и процентами отверстия кольцевой диаграммы, чтобы соответствовать вашим дизайнерским требованиям. Приятного кодинга!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Как создать столбчатую диаграмму с помощью Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Скрыть оси диаграммы в документе Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Вставить пузырьковую диаграмму в документ Word](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}