---
category: general
date: 2026-11-25
description: Узнайте, как создать круговую диаграмму в Java, вставить её в документ
  Word, отделить сектор диаграммы и изменить ориентацию диаграммы с помощью понятных
  примеров кода.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: ru
lastmod: 2026-11-25
og_description: Создайте круговую диаграмму в Java, вставьте её в документ, «взрыв»
  сектора и измените ориентацию диаграммы с пошаговым кодом.
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: Создание круговой диаграммы в Java – вставка, взрыв сектора и вращение
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: Как создать круговую диаграмму, вставить её и настроить ориентацию в Java
url: /ru/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать круговую диаграмму, вставить её и настроить ориентацию в Java

Если вам нужно **создать круговую диаграмму** в документе Word, это руководство покажет, как это сделать. Вы увидите, как **вставить круговую диаграмму**, «взрывать» (выделять) сектор для акцента и **изменить ориентацию диаграммы** простым вращением.

В уроке охвачено всё, что необходимо — от настройки библиотеки Aspose.Words for Java до получения готового файла `.docx` с повернутой, «взрывной» круговой диаграммой. Внешняя документация не требуется; просто следуйте шагам и запустите код.

## Требования

Прежде чем начать, убедитесь, что у вас есть:

* Java 17 или новее.
* Maven или Gradle для управления зависимостями.
* Действительная лицензия Aspose.Words for Java (или используйте бесплатный режим оценки).

Добавьте зависимость Aspose.Words в ваш `pom.xml` (Maven) или `build.gradle` (Gradle). Пример для Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **Совет:** Держите версию библиотеки актуальной; последняя версия (24.10 на момент написания) содержит исправления ошибок рендеринга диаграмм.

## Шаг 1: Создать круговую диаграмму и вставить её в документ

Первый шаг — **создать объект круговой диаграммы** и встроить его в файл Word. Ниже представленный код создает простой документ, добавляет заполнитель диаграммы и вставляет круговую диаграмму размером 400 × 300 пикселей.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**Почему это важно:** `builder.insertChart` создаёт заполнитель диаграммы, который Aspose.Words автоматически преобразует в OOXML‑диаграмму при сохранении документа. Параметр `ChartType.PIE` указывает библиотеке отрисовать круговую диаграмму, удовлетворяя требование **вставить круговую диаграмму**.

## Шаг 2: «Взорвать» сектор диаграммы для выделения сегмента

«Взрывание» сектора привлекает внимание к определённому пункту данных. Следующая строка «взрывает» первый сектор (индекс 0) на 10 пунктов:

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

Вы можете изменить индекс, чтобы выбрать другой сектор, или скорректировать расстояние «взрыва» для более тонкого эффекта. «Взрывание» сектора — стандартный способ **взрывать сектор круговой диаграммы** в Aspose.Words.

## Шаг 3: Изменить ориентацию диаграммы, поворачивая её

Поворот диаграммы дает новый визуальный взгляд. Используйте `setRotationAngle`, чтобы повернуть всю диаграмму по часовой стрелке (угол измеряется в градусах).

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

Вызов выше удовлетворяет требованиям **повернуть круговую диаграмму** и **изменить ориентацию диаграммы**. Принимается любой угол от 0 до 360 градусов.

## Полный исполняемый пример

Объединив всё вместе, получаем полностью автономную программу, которая создаёт круговую диаграмму, «взрывает» сектор и вращает диаграмму. Запустите её из IDE или из командной строки с `java -cp <classpath> PieChartDemo`.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### Ожидаемый результат

* В рабочем каталоге появляется файл **CreatePieChartDemo.docx**.
* При открытии файла в Microsoft Word отображается круговая диаграмма размером 400 × 300 пикселей.
* Первый сектор (Q1) смещён наружу на 10 пунктов, создавая эффект **взрыва сектора**.
* Вся диаграмма наклонена на 45 градусов, демонстрируя **изменение ориентации диаграммы** и **поворот круговой диаграммы**.

## Распространённые варианты и граничные случаи

| Ситуация | Как адаптировать код |
|-----------|-----------------------|
| **Другой размер диаграммы** | Измените аргументы `400, 300` в `insertChart`. |
| **Несколько рядов** | Добавьте дополнительные объекты `ChartSeries` в `chart.getSeries()`. |
| **Взрыть другой сектор** | Используйте `setExplode(sliceIndex, distance)` с нужным `sliceIndex`. |
| **Без вращения** | Уберите вызов `setRotationAngle` или задайте угол `0`. |
| **Экспорт в PDF вместо DOCX** | После построения документа вызовите `doc.save("output.pdf")` с форматом PDF. |

> **Осторожно:** Указание отрицательного расстояния «взрыва» вызывает `IllegalArgumentException`. Всегда задавайте неотрицательное значение.

## Совет по производительности

Если вы генерируете множество диаграмм в цикле, переиспользуйте один объект `DocumentBuilder` и вызывайте `insertChart` только для каждой итерации. Это уменьшит расход памяти и ускорит обработку.

## Заключение

Теперь вы знаете, как **создать круговую диаграмму**, **вставить круговую диаграмму**, **взрывать сектор** и **поворачивать круговую диаграмму** с помощью Aspose.Words for Java. Полный пример демонстрирует весь процесс — от инициализации документа до сохранения файла, визуализирующего повернутую, «взрывную» круговую диаграмму.

Далее вы можете изучить **изменение ориентации диаграммы** более глубоко, применяя 3‑D‑эффекты, или поэкспериментировать с другими типами диаграмм, такими как **Bar** или **Line**. Те же шаблоны API применимы, поэтому расширять этот урок будет просто.

Не стесняйтесь менять данные, индекс сектора или угол вращения под свои отчётные задачи и делиться результатами с сообществом!

## Что изучать дальше?

Следующие руководства охватывают близкие темы, которые опираются на техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}