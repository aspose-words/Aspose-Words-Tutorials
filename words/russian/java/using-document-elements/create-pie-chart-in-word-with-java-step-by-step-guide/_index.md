---
category: general
date: 2026-08-14
description: Создайте круговую диаграмму в Word с помощью Java и Aspose.Words. Узнайте,
  как добавить данные серии в диаграмму и повернуть сектор круговой диаграммы всего
  за несколько строк.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: ru
lastmod: 2026-08-14
og_description: Создайте круговую диаграмму в Word с помощью Java и Aspose.Words.
  Этот учебник показывает, как быстро добавить данные серии к диаграмме и повернуть
  её сектор.
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: Создание круговой диаграммы в Word с помощью Java – полное руководство по
  программированию
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Создание круговой диаграммы в Word с помощью Java – пошаговое руководство
url: /ru/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание круговой диаграммы в Word с помощью Java – пошаговое руководство

Если вам нужно **создать круговую диаграмму в Word** программно, это руководство покажет, как сделать это с помощью Java и Aspose.Words. Вы узнаете полный рабочий процесс: от вставки диаграммы до добавления точек данных и поворота первого сектора.

Генерация диаграммы непосредственно в файле `.docx` избавляет от ручного копирования‑вставки и позволяет автоматизировать отчёты, счета или дашборды. По пути мы также рассмотрим **как добавить данные серии в диаграмму** и **как повернуть сектор круговой диаграммы** для лучшего визуального акцента.

## Создание круговой диаграммы в Word – обзор

Aspose.Words for Java предоставляет удобный API `DocumentBuilder`, который может вставлять объект диаграммы в документ Word. Выбранный тип диаграммы определяет её базовый макет, а вы можете настраивать серии, цвета, углы и даже переключаться на форму кольца одним вызовом метода.

### Почему стоит использовать Aspose.Words?

* **Не требуется Microsoft Office** – библиотека работает на любом сервере или в CI‑окружении.  
* **Полная точность .docx** – сгенерированная диаграмма выглядит идентично той, что создана вручную в Word.  
* **Зависимость в одном файле** – достаточно добавить JAR‑файл, и вы готовы к работе.

## Как добавить данные серии в диаграмму

Диаграмма без данных – просто заполнитель. Объект `Chart` предоставляет коллекцию `Series`; каждая серия содержит список числовых значений, которые соответствуют секторам (для круговой) или точкам (для линейной). Добавление данных простое:

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**Что делает код:**  
* `chart.getSeries()` возвращает `List<ChartSeries>`.  
* `get(0)` выбирает первую серию, потому что круговая диаграмма по определению содержит только одну серию.  
* `add(double)` добавляет точку данных. Значения автоматически преобразуются в проценты, которые в сумме дают 100 % при отрисовке диаграммы.

> **Полезный совет:** Если ваш источник данных содержит более трёх категорий, продолжайте добавлять значения тем же способом. Aspose.Words автоматически создаст дополнительные сектора.

## Поворот сектора круговой диаграммы

Иногда требуется, чтобы определённый сектор начинался под конкретным углом, чтобы наиболее важный фрагмент был направлен к зрителю. Метод `setFirstSliceAngle(double)` вращает всю диаграмму, фактически смещая начало первого сектора:

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

Угол измеряется в градусах по часовой стрелке от вертикальной оси. Значение `0` (по умолчанию) размещает первый сектор вверху. Изменяйте его, чтобы выделить сектор или соответствовать дизайнерским требованиям.

> **Распространённый вопрос:** *Влияет ли вращение на порядок данных?*  
> Нет. Порядок данных остаётся прежним; меняется только визуальная стартовая позиция.

## Полный пример на Java

Ниже представлен полностью готовый к запуску пример, который создаёт документ Word с круговой диаграммой, добавляет данные серии, вращает сектор и сохраняет файл. Все необходимые импорты перечислены, так что вы можете скопировать код в любую IDE.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Ожидаемый результат

* В папке `output` появляется файл **PieChart.docx**.  
* При открытии в Microsoft Word отображается цветная круговая диаграмма с тремя секторами (40 %, 30 %, 30 %).  
* Диаграмма повернута на 45° по часовой стрелке, поэтому первый сектор начинается немного правее вертикальной оси.

## Распространённые ошибки и лучшие практики

| Проблема | Почему происходит | Решение |
|----------|-------------------|---------|
| **Диаграмма отображается пустой** | Документ был сохранён до полной отрисовки диаграммы. | Вызывайте `doc.save()` **после** всех модификаций диаграммы. |
| **Значения секторов не суммируются до 100 %** | Добавление «сырых» чисел, не представляющих проценты, приводит к неожиданному масштабированию. | Передавайте значения, логически отражающие части целого, либо позвольте Aspose.Words вычислять проценты автоматически. |
| **Поворот не оказывает эффекта** | Использование `ChartType.DOUGHNUT` без установки `holeSize` может скрыть эффект вращения. | Оставьте тип диаграммы `PIE` или скорректируйте `holeSize` после установки угла. |
| **Ошибки пути к файлу** | Относительные пути могут по‑разному разрешаться в Windows и Linux. | Используйте `Paths.get("output", "PieChart.docx").toString()` или абсолютный путь в продакшн‑коде. |

### Советы для продакшн‑использования

* **Повторно используйте `DocumentBuilder`** – можно вставлять несколько диаграмм в один документ, вызывая `insertChart` многократно.  
* **Стилизация** – используйте `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`, чтобы отображать проценты непосредственно на диаграмме.  
* **Производительность** – генерируйте диаграмму один раз и клонируйте её (`chart.deepClone()`), если нужны идентичные диаграммы в разных местах.

## Поворот сектора круговой диаграммы – продвинутые сценарии

* **Динамический угол** – вычисляйте угол на основе данных (например, чтобы крупнейший сектор начинался сверху).  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **Несколько серий** – хотя у круговой диаграммы обычно одна серия, Aspose.Words позволяет добавить больше для «stacked pies». Поворот всё равно применяется только к первой серии.

## Заключение

Теперь вы знаете, как **создать круговую диаграмму в Word** с помощью Java, как **добавить данные серии в диаграмму** и как **повернуть сектор круговой диаграммы** для визуального акцента. Полный пример демонстрирует весь процесс — от инициализации документа до сохранения финального `.docx`‑файла — чтобы вы могли интегрировать генерацию диаграмм в любой автоматизированный конвейер отчётов.

### Что дальше?

* Изучите другие типы диаграмм (`ChartType.BAR`, `ChartType.LINE`), чтобы расширить инструментарий автоматизации.  
* Сочетайте генерацию диаграмм с **mail merge**, чтобы создавать персонализированные отчёты для каждого получателя.  
* Погрузитесь в **Styling API** (`ChartFormat`, `DataLabel`, `ChartTitle`), чтобы привести внешний вид к корпоративному бренду.

Экспериментируйте с разными наборами данных, углами и стилями диаграмм. Приятного кодинга!

## Что стоит изучить дальше?

Следующие учебные материалы охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}