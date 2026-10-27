---
category: general
date: 2026-09-24
description: Вставьте круговую диаграмму в DOCX с помощью Aspose.Words для Java. Узнайте,
  как задать размер отверстия, «взрывать» сектор диаграммы, выделять сектор и создавать
  диаграммы в DOCX без усилий.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: ru
lastmod: 2026-09-24
og_description: Вставьте круговую диаграмму в DOCX с помощью Aspose.Words for Java.
  Овладейте настройкой размера отверстия, взрывом сектора, выделением сектора круговой
  диаграммы и создавайте диаграммы в DOCX за считанные минуты.
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: Вставка круговой диаграммы в Java – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: Вставка слова «pie chart» в Java — полное руководство
url: /ru/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Вставка круговой диаграммы в Java – полное руководство

Если вам нужно **вставить круговую диаграмму** в файл DOCX, этот учебник покажет, как это сделать с помощью Aspose.Words for Java. Вы увидите полный процесс от создания документа до настройки диаграммы, чтобы сектор был «взрывным», размер отверстия был установлен в ноль, а сектор выделен.

Работа с диаграммами в документах Word часто кажется отдельной задачей от обычной обработки текста, но Aspose.Words объединяет оба процесса. В следующих шагах вы также узнаете, как **создавать docx‑диаграммы** файлов, готовых к открытию в Microsoft Word, Google Docs или любом другом просмотрщике, поддерживающем DOCX.

## Что вы достигнете

* **Вставить круговую диаграмму** в пустой документ  
* **Установить размер отверстия** чтобы превратить диаграмму в полный круг (без пончика)  
* **Взрывной сектор** для привлечения внимания к определённому сегменту  
* **Выделить сектор круговой диаграммы** с пользовательским форматированием  
* **Создать docx‑диаграмму**, которую можно распространять или далее редактировать  

### Требования

* Java 17 или новее (код также компилируется с Java 8)  
* Библиотека Aspose.Words for Java (версия 23.9 или новее)  
* IDE или система сборки (Maven/Gradle), способная разрешить зависимость Aspose.Words  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## Как вставить круговую диаграмму в DOCX с помощью Aspose.Words

Первый шаг — создать новый пустой документ и получить `DocumentBuilder`. Builder предоставляет прямой доступ к потоку содержимого документа, что делает **вставку круговой диаграммы** тривиальной.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### Почему это важно
`Document` представляет весь файл Word, тогда как `DocumentBuilder` — это API высокого уровня, позволяющее вставлять абзацы, таблицы и диаграммы без работы с низкоуровневым XML. Начало с чистого документа гарантирует, что добавленная диаграмма будет единственным содержимым, что идеально для обучения или создания отчётов на основе шаблонов.

## Установить размер отверстия для создания полного круга

По умолчанию Aspose.Words создаёт пончиковую диаграмму, когда вы запрашиваете круговую диаграмму. Чтобы сделать её настоящим кругом, необходимо **установить размер отверстия** в `0`. Это удаляет внутреннее отверстие и даёт классический вид круговой диаграммы.

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### Практический совет
Если позже вы решите переключиться на пончиковую диаграмму, просто измените значение `holeSize` на процент (например, `30`). Один и тот же API работает для обоих типов диаграмм.

## Взрывной сектор диаграммы для выделения сегмента

Взрыв сектора делает его визуально выделяющимся. Операция **взрыва сектора** перемещает выбранный сектор наружу на процент от радиуса диаграммы.

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### Почему взрывать?
Взрывной сектор привлекает взгляд читателя к самой важной точке данных — идеально для панелей мониторинга или исполнительных резюме. Значение `20` означает 20 % от радиуса; вы можете регулировать его от `0` (без взрыва) до `100` (полностью отделённый).

## Выделить сектор круговой диаграммы с пользовательским форматированием

Помимо взрыва, вы можете захотеть **выделить сектор круговой диаграммы**, изменив его цвет заливки или границу. Хотя демонстрационный код сосредоточен на взрыве, вы можете расширить его следующим образом:

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### Примечание эксперта
Изменение цвета заливки конкретного сектора требует доступа к объекту `DataPoint`. Если у вас несколько серий, пройдитесь по `series.getDataPoints()` и применяйте стили условно.

## Сохранить и проверить созданную docx‑диаграмму

Наконец, вы **создаёте docx‑диаграмму**, сохранив `Document`. Полученный файл можно открыть в Microsoft Word, чтобы увидеть отформатированную круговую диаграмму.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### Ожидаемый результат
Открытие `PieChartFormatted.docx` показывает одну круговую диаграмму:

* Диаграмма занимает область 400 × 300 pt.  
* Размер отверстия `0`, поэтому диаграмма — полный круг.  
* Первый сектор взорван на 20 % и окрашен в красный цвет (если вы добавили необязательное форматирование).  

Теперь у вас есть **docx‑диаграмма**, которую можно распространять, встраивать в электронные письма или дальше редактировать программно.

---

## Общие варианты и граничные случаи

| Сценарий | Как адаптировать код |
|----------|----------------------|
| **Несколько серий** | Пройдитесь по `pieChart.getChart().getSeries()` и установите `Explosion` или `FillColor` для каждой серии. |
| **Динамические данные** | Заполните серии значениями из базы данных или CSV перед вызовом `setExplosion`. |
| **Другой размер диаграммы** | Измените аргументы ширины/высоты в `insertChart(ChartType.PIE, width, height)`. |
| **Экспорт в PDF** | После сохранения DOCX вызовите `doc.save("output.pdf")`, чтобы получить PDF‑версию той же диаграммы. |
| **Локализация** | Используйте `DocumentBuilder.insertChart` с локаль‑специфичным форматом чисел для меток. |

### Профессиональный совет
Всегда вызывайте `setHoleSize(0)` **после** `insertChart`. Если установить его до вставки, Aspose.Words вернёт размер пончика по умолчанию после создания диаграммы.

---

## Итоги

Теперь вы знаете, как **вставлять круговую диаграмму** в документ Word с помощью Java, как **устанавливать размер отверстия** для полного круга, как **взрывать сектор** для привлечения внимания и как **выделять сектор круговой диаграммы** пользовательскими цветами. Полный пример также демонстрирует, как **создавать docx‑диаграммы**, готовые к распространению.

---

## Следующие шаги

* Изучите другие типы диаграмм (`BAR`, `LINE`, `SCATTER`) с помощью `ChartType`.  
* Сочетайте генерацию диаграмм с рассылкой писем (mail merge) для создания персонализированных отчётов.  
* Интегрируйте сгенерированный DOCX в веб‑службу, которая возвращает файл по запросу.  

Если возникнут проблемы, убедитесь, что вы используете совместимую версию Aspose.Words и что каталог вывода существует и доступен для записи.

Удачной разработки!

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и изучить альтернативные подходы к реализации в ваших проектах.

- [Как создать столбчатую диаграмму с помощью Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Использование Word Chart API](/words/english/net/programming-with-charts/)
- [Вставка пузырьковой диаграммы в Word с помощью Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}