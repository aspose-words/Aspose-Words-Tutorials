---
category: general
date: 2026-09-24
description: Узнайте, как создать диаграмму в Word с помощью Java, вставить радиальную
  диаграмму и сохранить документ в формате docx с помощью Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create chart in word
- save document as docx
- add chart to word
- create word document java
- insert radial chart
language: ru
lastmod: 2026-09-24
og_description: Создайте диаграмму в Word с помощью Java и Aspose.Words. Этот учебник
  покажет, как добавить радиальную диаграмму, настроить данные и сохранить документ
  в формате docx.
og_image_alt: Radial chart inserted in a Word document using Java code
og_title: Создание диаграммы в Word с помощью Java – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  headline: How to create chart in Word with Java and Aspose.Words
  type: TechArticle
- description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  name: How to create chart in Word with Java and Aspose.Words
  steps:
  - name: You should see a single page with a centered radial chart.
    text: You should see a single page with a centered radial chart.
  - name: If you added series data, the chart displays four slices labeled Q1‑Q4.
    text: If you added series data, the chart displays four slices labeled Q1‑Q4.
  - name: Right‑click the chart → **Edit Data** to confirm the underlying data table.
    text: Right‑click the chart → **Edit Data** to confirm the underlying data table.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Chart
- DOCX
title: Как создать диаграмму в Word с помощью Java и Aspose.Words
url: /ru/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать диаграмму в Word с помощью Java и Aspose.Words

Если вам нужно **create chart in Word** из Java‑приложения, это руководство проведёт вас через весь процесс. Вы увидите, как добавить радиальную диаграмму, при необходимости заполнить её серии и в конце **save document as docx** с помощью библиотеки Aspose.Words for Java.

Генерация визуальных данных внутри файла Word является распространённой задачей для отчётности, выставления счетов или автоматической генерации документов. К концу этого руководства вы сможете создавать проекты **create word document java**, которые **add chart to Word** файлы без какого‑либо ручного редактирования.

## Предварительные требования

* Java Development Kit (JDK) 8 или новее.
* Maven или Gradle для управления зависимостями.
* IDE, например IntelliJ IDEA, Eclipse или VS Code.
* Действительная лицензия Aspose.Words for Java (бесплатная пробная версия подходит для разработки).

Эти инструменты обеспечивают основу для последующих примеров кода.

## Шаг 1: Настройка Maven‑проекта

Создайте новый Maven‑проект (или обновите существующий) и добавьте зависимость Aspose.Words в ваш `pom.xml`:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word‑chart‑demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

Выполнение `mvn clean install` загружает библиотеку и делает такие классы, как `Document`, `DocumentBuilder` и `ChartType`, доступными в classpath.

> **Pro tip:** Держите версию библиотеки актуальной. Новые релизы добавляют типы диаграмм и улучшают производительность рендеринга.

## Шаг 2: Создание нового документа Word

Первый программный шаг для **create chart in Word** — создать пустой объект `Document`. Этот объект представляет весь пакет `.docx`.

```java
import com.aspose.words.*;

public class RadialChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a blank Word document
        Document doc = new Document();

        // Step 2.2: Obtain a DocumentBuilder to insert content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` работает как курсор; он знает текущую точку вставки и предоставляет методы для текста, таблиц и диаграмм. На данном этапе вы **created word document java** стиль — чистый холст, готовый к наполнению.

## Шаг 3: Вставка радиальной диаграммы

Aspose.Words поддерживает множество типов диаграмм. Чтобы **insert radial chart**, вызовите `insertChart` с параметром `ChartType.RADIAL`. Метод также требует указать ширину и высоту в пунктах (1 point ≈ 1/72 дюйма).

```java
        // Step 3: Insert a radial chart (400 × 300 points)
        Shape chart = builder.insertChart(ChartType.RADIAL, 400, 300);
```

Возвращаемый объект `Shape` содержит вложенный объект диаграммы. Диаграмма автоматически отображает деления для раскладки 24,9°, что является значением по умолчанию для радиальных диаграмм в Word.

### Почему использовать радиальную диаграмму?

Радиальная диаграмма визуализирует данные, оборачивающиеся вокруг круга, что делает её идеальной для отображения циклических паттернов (например, ежемесячных продаж, метрик в виде циферблата). Тот же API может вставлять столбчатые, круговые или линейные диаграммы, но радиальный тип придаёт отличительный вид без дополнительного кода стилизации.

## Шаг 4: (Опционально) Заполнение данных серии диаграммы

Если вы хотите, чтобы диаграмма отображала реальные значения, необходимо добавить серии и точки. Следующий фрагмент добавляет одну серию с тремя точками данных:

```java
        // Optional: add data to the chart
        Chart chartObj = chart.getChart();
        chartObj.getSeries().clear(); // remove any default series

        // Create a new series
        ChartSeries series = chartObj.getSeries().add("Quarterly Revenue");

        // Add data points (value, category)
        series.getDataPoints().add(15000, "Q1");
        series.getDataPoints().add(21000, "Q2");
        series.getDataPoints().add(18000, "Q3");
        series.getDataPoints().add(24000, "Q4");
```

Вы можете повторять вызовы `add` столько раз, сколько требуется точек. Aspose.Words автоматически обновляет визуальное представление, поэтому вы видите, как радиальные сектора изменяются в соответствии с новыми значениями.

> **Common question:** *Что если мне нужно привязать данные из базы данных?*  
> Получите строки, пройдитесь по ним в цикле и вызовите `series.getDataPoints().add(value, label)` внутри цикла. API потокобезопасен и работает с любым `ResultSet`, который вы предоставляете.

## Шаг 5: Сохранение документа в формате DOCX

Когда диаграмма готова, последний шаг — **save document as docx**. Метод `save` определяет формат вывода по расширению файла.

```java
        // Step 5: Persist the document
        String outputPath = "output/RadialChartDemo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Сгенерированный файл содержит полностью функционирующую радиальную диаграмму, которую можно открыть в Microsoft Word, LibreOffice или любом просмотрщике, поддерживающем формат DOCX. Поскольку мы использовали расширение `.docx`, Word сохраняет файл в формате Open XML, который является современным стандартом для документов Word.

### Проверка результата

Откройте `RadialChartDemo.docx` в Word:

1. Вы должны увидеть одну страницу с центрированной радиальной диаграммой.
2. Если вы добавили данные серии, диаграмма отображает четыре сектора с метками Q1‑Q4.
3. Щелкните правой кнопкой мыши по диаграмме → **Edit Data**, чтобы подтвердить таблицу исходных данных.

Если диаграмма отображается пустой, дважды проверьте, что вы вызвали `chart.getChart()` перед добавлением серии, и убедитесь, что курсор DocumentBuilder находится в нужном месте для вставки диаграммы.

## Шаг 6: Расширенные советы по работе с диаграммами

| Совет | Почему это важно |
|-----|----------------|
| **Установить стиль диаграммы** – `chart.getChart().setStyle(ChartStyle.STYLE_PRESET_5);` | Улучшает визуальную согласованность без ручного форматирования каждого элемента. |
| **Изменить размер после вставки** – `chart.setWidth(500); chart.setHeight(350);` | Позволяет точно настроить размер диаграммы в зависимости от макета страницы. |
| **Добавить заголовок** – `chart.getChart().getTitle().setText("Revenue Overview");` | Даёт контекст читателям, просматривающим документ без окружающего текста. |
| **Экспорт в PDF** – `doc.save("RadialChartDemo.pdf");` | Полезно, когда нужна неизменяемая версия для распространения. |
| **Работа с лицензией** – `License lic = new License(); lic.setLicense("Aspose.Words.lic");` | Предотвращает появление водяного знака оценки в продакшн‑сборках. |

Эти улучшения являются опциональными, но демонстрируют, как можно дополнительно настроить диаграмму после того, как вы научились **add chart to Word**.

## Заключение

Теперь у вас есть полный, автономный пример, показывающий, как **create chart in Word** с помощью Java, **insert radial chart**, при необходимости заполнить её данными и **save document as docx**. Та же схема работает для других типов диаграмм, поэтому вы можете расширить это руководство до столбчатых, линейных или круговых диаграмм по мере необходимости.

Далее вы можете изучить:

* **create word document java** проекты, которые комбинируют таблицы, изображения и несколько диаграмм.
* Использование **save document as docx** вместе с **save document as pdf** для многоформатной отчётности.
* Добавление динамических данных из REST API или баз данных в ваши диаграммы.

Не стесняйтесь экспериментировать с параметрами стилей, размерами диаграмм и источниками данных. Приятного кодинга!

## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Как создать столбчатую диаграмму с помощью Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Создать пустой документ Word с Aspose.Words – пошаговое руководство](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Создать документ Word Java – добавить прямоугольную форму с эффектом тени](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}