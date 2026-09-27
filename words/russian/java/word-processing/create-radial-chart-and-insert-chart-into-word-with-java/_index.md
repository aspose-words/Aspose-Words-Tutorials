---
category: general
date: 2026-09-27
description: Создайте радиальную диаграмму на Java и вставьте её в Word. Узнайте,
  как задать размер диаграммы, добавить серию данных и создать пустой документ Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: ru
lastmod: 2026-09-27
og_description: Создайте радиальный график в Java, затем вставьте график в Word. Это
  руководство показывает, как задать размер графика, добавить серию данных и создать
  пустой документ Word.
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: Создать радиальный график и вставить его в Word с помощью Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: Создать радиальный график и вставить его в Word с помощью Java
url: /ru/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создать радиальную диаграмму и вставить её в Word с помощью Java

Если вам нужно **создать радиальную диаграмму** в файле Word, используя Java, этот учебник покажет, как это сделать. Вы увидите, как **вставить диаграмму в Word**, задать размеры диаграммы и построить **пустой документ Word** с нуля.

Мы пройдём каждый необходимый шаг, от инициализации документа до добавления серии данных и сохранения конечного `.docx`. К концу у вас будет полностью функционирующий файл Word, содержащий радиальную диаграмму, и вы поймёте, **как задать размер диаграммы** и **добавить серию данных в диаграмму** для будущих настроек.

## Предварительные требования

* Java 17 или новее (код компилируется любой современной JDK)
* Aspose.Words for Java 24.9 или новее – метод `setShowGraduations` доступен только с этой версии
* IDE или система сборки (Maven/Gradle), способная включить JAR Aspose.Words
* Базовое знакомство с синтаксисом Java и управлением зависимостями Maven/Gradle

> **Совет:** Если вы используете Maven, добавьте следующее в ваш `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Шаг 1: Создать пустой документ Word

Пустой документ — это холст, на котором будет размещена диаграмма. Класс `Document` представляет весь файл `.docx`.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

Создание пустого документа гарантирует, что никакое предсуществующее содержимое не помешает размещению диаграммы.

## Шаг 2: Инициализировать DocumentBuilder

`DocumentBuilder` предоставляет удобные методы для вставки объектов, текста и других элементов в документ.

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Позже builder будет использован для **вставки диаграммы в Word**.

## Шаг 3: Построить радиальную диаграмму

Aspose.Words поддерживает множество типов диаграмм; `ChartType.RADIAL` создаёт радиальную (полярную) диаграмму.

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

На данном этапе диаграмма существует, но у неё нет данных, размеров или визуальных параметров.

## Шаг 4: Добавить серию данных в диаграмму

Диаграмма без серии данных пуста. Метод `add` принимает имя серии и массив значений.

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

Можно добавить несколько серий, вызывая `add` многократно. Это удовлетворяет требованию **добавить серию данных в диаграмму**.

## Шаг 5: Включить деления (необязательно)

Деления — это радиальные сетки, которые повышают читаемость. Они доступны только, начиная с версии 24.9.

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

Если вы используете более старую версию Aspose.Words, эта строка вызовет исключение — поэтому сначала проверьте версию библиотеки.

## Шаг 6: Задать размеры диаграммы

Контроль размера диаграммы позволяет удобно разместить её в полях страницы. Это отвечает на вопрос **как задать размер диаграммы**.

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

Вы можете изменить значения ширины и высоты в соответствии с вашими требованиями к макету. Помните, что 1 пункт ≈ 1/72 дюйма.

## Шаг 7: Вставить диаграмму в документ Word

Теперь диаграмма готова к размещению. Метод `insertChart` класса `DocumentBuilder` осуществляет вставку.

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

Это ядро операции **вставить диаграмму в Word**.

## Шаг 8: Сохранить документ

Наконец, запишите документ на диск. Файл будет содержать созданную радиальную диаграмму.

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Запуск программы создаст `RadialChart.docx` в рабочем каталоге проекта. Открытие файла в Microsoft Word покажет радиальную диаграмму с тремя точками данных и видимыми делениями.

### Ожидаемый результат

* Файл Word с именем `RadialChart.docx`
* Внутри файла — одна страница, содержащая радиальную диаграмму размером 400 × 300 пунктов
* Диаграмма отображает одну серию под названием **Series 1** со значениями **10, 20, 30**
* Деления (радиальные сетки) видимы вокруг диаграммы

## Общие варианты и граничные случаи

| Ситуация | Что изменить | Причина |
|-----------|----------------|--------|
| **Несколько серий** | Вызвать `chart.getSeries().add(...)` для каждой серии | Позволяет сравнивать данные |
| **Другой тип диаграммы** | Заменить `ChartType.RADIAL` на `ChartType.COLUMN` (или любой другой) | Использовать тип диаграммы, лучше подходящий для ваших данных |
| **Пользовательские цвета** | Обратиться к `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` | Улучшает визуальный брендинг |
| **Старая версия Aspose.Words** | Удалить строку `setShowGraduations` или обновить библиотеку | Предотвращает `NoSuchMethodError` |
| **Сохранение в другой формат** | Использовать `doc.save("RadialChart.pdf", SaveFormat.PDF)` | Генерирует PDF вместо DOCX |

## Полный рабочий пример

Ниже приведена полная, автономная Java‑программа. Скопируйте её в файл `RadialChartExample.java`, добавьте зависимость Aspose.Words и запустите.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## Заключение

Теперь вы знаете, как **создать радиальную диаграмму** программно, **добавить серию данных в диаграмму**, управлять **тем, как задать размер диаграммы**, и **вставить диаграмму в Word**, начиная с **пустого документа Word**. Пример использует Aspose.Words for Java 24.9, но те же концепции применимы к другим библиотекам диаграмм с аналогичным API.

### Что дальше?

* Исследуйте другие типы диаграмм (`ChartType.PIE`, `ChartType.LINE` и т.д.) — это связано с вторичным ключевым словом **insert chart into word**.
* Настройте подписи осей, легенды и цвета в соответствии с вашими бренд‑гайдами.
* Генерируйте диаграммы динамически из запросов к базе данных или CSV‑файлов.
* Преобразуйте полученный `.docx` в PDF для распространения (`doc.save("output.pdf", SaveFormat.PDF)`).

Не стесняйтесь экспериментировать с размерами, данными серий и параметрами стилей, чтобы создать именно тот визуальный элемент, который вам нужен. Приятного кодинга!

## Что вам стоит изучить дальше?

Следующие учебники охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}