---
category: general
date: 2026-10-10
description: Узнайте, как повернуть диаграмму в файле Word и изменить её в Word, чтобы
  изменить размер кольцевой диаграммы, с полным примером на Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: ru
lastmod: 2026-10-10
og_description: Как повернуть диаграмму в файле Word и изменить её в Word, чтобы изменить
  размер кольцевой диаграммы, используя Aspose.Words для Java.
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: Как повернуть диаграмму в документе Word – пошаговое руководство на Java
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Как повернуть диаграмму в документе Word с помощью Aspose.Words
url: /ru/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как повернуть диаграмму в документе Word с помощью Aspose.Words

Если вам нужно **повернуть диаграмму** внутри файла Microsoft Word, это руководство покажет точные шаги. Вы также узнаете, как **изменять диаграмму в Word**, чтобы **изменить размер кольцевой диаграммы** без выхода из вашего Java‑кода.

Автоматизация Word часто кажется набором разрозненных вызовов API, но с Aspose.Words вы можете обращаться к диаграмме как к любому другому узлу документа. К концу этого урока у вас будет готовая программа, которая загружает существующий `.docx`, поворачивает кольцевую диаграмму на 45°, уменьшает отверстие до 50 % радиуса и сохраняет результат в новый файл.

## Требования

Прежде чем начать, убедитесь, что у вас есть:

* Java 17 или новее.
* Maven (или Gradle) для управления зависимостями.
* Входной документ Word (`input.docx`), уже содержащий кольцевую диаграмму.
* Действительная лицензия Aspose.Words for Java (или используйте режим оценки).

## Шаг 1: Настройка проекта Maven

Создайте новый проект Maven или добавьте следующую зависимость в ваш существующий `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

Выполнение `mvn clean install` загрузит библиотеку и сделает классы доступными в вашем classpath.

## Шаг 2: Загрузка документа Word, содержащего диаграмму

Первой операцией является открытие существующего документа. Класс `Document` представляет весь файл.

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Загрузка файла **не** изменяет его; она просто создаёт представление в памяти, которое можно запросить и отредактировать.

## Шаг 3: Создание DocumentBuilder для навигации

`DocumentBuilder` предоставляет API, похожее на курсор, для обхода дерева документа. Мы будем использовать его, чтобы найти первую форму диаграммы.

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder начинается в начале документа, но при необходимости вы можете переместить его к любому узлу позже.

## Шаг 4: Получение первой формы диаграммы

Диаграммы хранятся как узлы `Shape`. Отфильтровав дочерние узлы типа `NodeType.SHAPE`, мы можем извлечь объект диаграммы.

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

Если документ содержит несколько диаграмм, вы можете перебрать `getChildNodes` и проверять каждый `Shape` на наличие `hasChart()` перед приведением типа.

## Шаг 5: Поворот диаграммы (как повернуть диаграмму)

Кольцевая диаграмма по сути является круговой диаграммой с отверстием. Поворот изменяет начальный угол первого сектора.

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

Метод `setStartAngle` принимает `double`, представляющий градусы. Положительные значения вращают по часовой стрелке, отрицательные — против часовой стрелки.

## Шаг 6: Изменение размера отверстия кольца (изменить размер кольцевой диаграммы)

Размер отверстия задаётся как доля радиуса диаграммы. Значение `0.5` означает, что отверстие занимает 50 % от общего радиуса.

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**Совет:** Допустимый диапазон — от `0.0` (без отверстия, т.е. обычный круг) до `0.9` (очень тонкое кольцо). Значения вне этого диапазона вызовут `IllegalArgumentException`.

## Шаг 7: Сохранение изменённого документа

Наконец, запишите изменения обратно на диск.

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

Когда вы откроете `DoughnutFormatted.docx` в Microsoft Word, вы увидите кольцевую диаграмму, повернутую на 45°, а отверстие уменьшено вдвое от исходного размера.

## Полный, готовый к запуску пример

Объединив все части, получаем полную программу, которую можно скопировать и вставить в вашу IDE:

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### Ожидаемый вывод

Запуск программы выводит:

```
Chart rotated and doughnut size changed successfully.
```

Открытие `DoughnutFormatted.docx` показывает кольцевую диаграмму, у которой первый сектор начинается под углом 45°, а внутренний радиус составляет половину внешнего радиуса.

## Распространённые варианты и граничные случаи

| Ситуация | Что нужно изменить | Почему это важно |
|-----------|-------------------|-------------------|
| **Несколько диаграмм** | Перебрать `getChildNodes(NodeType.SHAPE, true)` и проверять `shape.hasChart()` для каждой | Гарантирует, что вы изменяете нужную диаграмму, а не первую |
| **Гистограмма или линейная диаграмма** | `setStartAngle` не применяется; используйте `chart.getSeries().get(0).setFillFormat(...)` для других визуальных настроек | Не все типы диаграмм поддерживают вращение; только кольцевые/круговые имеют начальный угол |
| **Диаграмма без отверстия** | Пропустить `setDoughnutHoleSize` или сначала преобразовать тип диаграммы в кольцевой через `chart.setChartType(ChartType.DONUT)` | Попытка изменить размер отверстия у диаграммы без него вызовет исключение |
| **Большие документы** | Использовать `DocumentBuilder.moveToDocumentStart()` и `builder.moveToNode(chartShape)` для целенаправленной навигации | Улучшает производительность, избегая полного обхода нерелевантных узлов |

## Профессиональные советы для надёжного управления диаграммами

* **Кешировать ссылку на диаграмму** — Если планируете менять несколько свойств, храните локальную переменную `Chart`, а не каждый раз вызывать `chartShape.getChart()`.
* **Проверять входные значения** — Перед вызовом `setStartAngle` или `setDoughnutHoleSize` убедитесь, что значение находится в допустимом диапазоне, чтобы избежать ошибок во время выполнения.
* **Использовать лицензию** — Режим оценки вставляет водяной знак на первую страницу. Применение лицензии (`License license = new License(); license.setLicense("Aspose.Words.lic");`) убирает его.

## Следующие шаги

Теперь, когда вы знаете **как повернуть диаграмму** и **изменить размер кольцевой диаграммы**, вы можете исследовать другие сценарии **модификации диаграмм в Word**:

* Изменить цвета секторов с помощью `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())`.
* Добавить подписи данных, вызвав `chart.getSeries().get(0).setHasDataLabel(true)`.
* Экспортировать диаграмму как изображение с помощью `chart.toImage(300, 300, ImageType.PNG)`.

Все эти расширения следуют одной схеме: получить объект `Chart`, вызвать нужный сеттер и сохранить документ.

---

**Вы только что освоили поворот и изменение размеров кольцевых диаграмм в Word с помощью Java.** Не стесняйтесь адаптировать код под другие типы диаграмм, интегрировать его в более крупный конвейер генерации документов или комбинировать с Aspose.Slides для автоматизации PowerPoint. Приятного кодинга!


## Что изучать дальше?


Следующие учебные материалы охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими вам освоить дополнительные возможности API и исследовать альтернативные подходы реализации в своих проектах.

- [Как создать столбчатую диаграмму с помощью Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Скрыть оси диаграммы в документе Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Вставить пузырьковую диаграмму в документ Word](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}