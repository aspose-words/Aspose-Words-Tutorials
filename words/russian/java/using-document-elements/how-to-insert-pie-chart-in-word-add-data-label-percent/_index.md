---
category: general
date: 2026-07-20
description: Как вставить круговую диаграмму в Word с помощью Aspose.Words. Узнайте,
  как добавить процентные подписи данных и отобразить проценты на диаграмме для профессиональных
  документов.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: ru
lastmod: 2026-07-20
og_description: как вставить круговую диаграмму в Word с помощью Aspose.Words. Это
  руководство показывает, как добавить процентные подписи данных и отобразить проценты
  на диаграмме всего за несколько строк.
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: как вставить круговую диаграмму в Word — быстрое руководство
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: Как вставить круговую диаграмму в Word – добавить процент в подписи данных
url: /ru/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# как вставить круговую диаграмму в Word – добавить процент в подписи данных

Когда‑то задумывались **как вставить круговую диаграмму** в документ Word без мучений с интерфейсом? Вы не одиноки. Во многих сценариях отчётности необходимо *добавить круговую диаграмму в Word* и, что ещё важнее, **показать процент на круговой диаграмме**, чтобы читатели сразу понимали распределение данных.

В этом руководстве мы пройдём весь процесс с помощью Aspose.Words for Java. К концу вы точно будете знать, как **добавить процент в подписи данных**, **отобразить проценты на диаграмме**, и получите отшлифованную круговую диаграмму, которая выглядит правильно с первого раза. Никаких дополнительных плагинов, никаких ручных правок — только чистый код, который можно вставить в любой проект.

---

## Требования

- Java 17 (или новее) — текущая LTS‑версия, поддерживаемая Aspose.Words.
- Aspose.Words for Java 24.x (самая свежая на момент написания, июль 2026).
- Базовая настройка Maven или Gradle для загрузки библиотеки.
- Любая удобная IDE (IntelliJ IDEA, Eclipse, VS Code… подойдёт любая).

Если всё уже готово, отлично — приступим.

---

## Шаг 1: Создать проект и импортировать библиотеку

Сначала добавьте зависимость Aspose.Words в ваш `pom.xml` (Maven) или `build.gradle` (Gradle). Это даст вам доступ к классам `Document`, `DocumentBuilder` и к классам диаграмм.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Держите номер версии актуальным; новые релизы часто включают исправления, связанные с диаграммами, которые делают **отображение процентов на диаграмме** более надёжным.

---

## Шаг 2: Создать новый документ Word и builder

Builder — ваш швейцарский нож для вставки контента. Здесь мы создаём новый документ и привязываем к нему `DocumentBuilder`.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Зачем нужен builder? Он абстрагирует низкоуровневые структуры OpenXML, позволяя сосредоточиться на *чём* мы хотим — например **добавить круговую диаграмму в word** — вместо того, *как* выглядит XML.

---

## Шаг 3: Вставить круговую диаграмму

Теперь переходим к основной части **как вставить круговую диаграмму**. Мы просим builder разместить круговую диаграмму заданного размера. Размеры указываются в пунктах (1 pt ≈ 1/72 in).

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

На данном этапе диаграмма пустая, но её место уже находится в документе. Вы только что **добавили круговую диаграмму в word** программно.

---

## Шаг 4: Заполнить диаграмму данными

Круговой диаграмме нужен хотя бы один ряд значений. Давайте передадим ей примерные данные, представляющие долю рынка.

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

Если понадобится несколько рядов (слоёные круги, пончики и т.п.), можно вызвать `pieChart.getSeries().add()` и повторить шаги. Та же логика применяется, когда вы хотите **отобразить проценты на диаграмме** для каждого сектора.

---

## Шаг 5: **add data label percent** — показать проценты на секторах

Это часть, которую большинство разработчиков забывают: настроить подписи данных так, чтобы показывать проценты. Без этого диаграмма выводит только сырые числа, что может быть неоднозначно.

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

Вызов `setShowPercent(true)` сообщает Aspose.Words отрисовать подпись как «30 %», «45 %» и т.д. Именно так вы **показываете процент на круговой диаграмме** без дополнительного форматирования.

---

## Шаг 6: Сохранить документ

Наконец, запишите документ на диск. Вы можете выбрать `.docx`, `.pdf` или даже `.html`. В этом руководстве мы останемся с современным форматом `.docx`.

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

Запустите программу, откройте `PieChartDemo.docx`, и вы увидите аккуратно отрисованную круговую диаграмму с процентными метками на каждом секторе.

---

## Ожидаемый результат

Ниже скриншот сгенерированного файла Word. Обратите внимание, как каждый сектор отображает свою долю в процентах — именно то, что мы хотели, задав **add data label percent**.

![Screenshot of a Word document containing a pie chart with percentage labels](/images/pie-chart-percent.png){.center width=600px alt="Скриншот, показывающий, как вставить круговую диаграмму в Word с процентными метками"}

*Текст alt включает основной ключевой запрос, удовлетворяя как SEO, так и требованиям доступности.*

---

## Часто задаваемые вопросы и обработка крайних случаев

| Вопрос | Ответ |
|----------|--------|
| **Можно ли изменить шрифт процентных меток?** | Да. После включения `setShowPercent(true)` получите объект `DataLabel` и измените его свойство `Font` (`dataLabel.getFont().setSize(10);`). |
| **А если нужен пончиковая диаграмма вместо круговой?** | Замените `ChartType.PIE` на `ChartType.DOUGHNUT` в вызове `insertChart`. Та же логика **add data label percent** работает. |
| **Отображаются ли проценты корректно в старых версиях Word (2007‑2010)?** | Aspose.Words пишет XML, независимый от версии, поэтому проценты видны в любой версии Word, поддерживающей диаграммы (2007+). |
| **Как добавить заголовок к диаграмме?** | Вызовите `pieChart.getTitle().setText("Market Share");` перед сохранением. |
| **Можно ли вставить диаграмму в конкретный абзац или ячейку таблицы?** | Конечно. Переместите `DocumentBuilder` в нужное место (`builder.moveToParagraph(index, true);` или `builder.moveToCell(table, row, column, true);`) перед вызовом `insertChart`. |

---

## Советы и лайфхаки из практики

- **Pro tip:** Если планируете генерировать много диаграмм в цикле, переиспользуйте один экземпляр `DocumentBuilder`; это уменьшит нагрузку на память.
- **Обратите внимание:** Очень маленькие сектора (< 2 %). Aspose.Words может опустить метку, чтобы избежать захламления; принудительно включить её можно через `dataLabel.setShowLabel(true);`.
- **Замечание о производительности:** Рендеринг диаграмм требует значительных CPU‑ресурсов. При массовой генерации отчётов рассмотрите многопоточность, но убедитесь, что каждый поток работает со своим экземпляром `Document`.
- **Проверка версии:** Метод `setShowPercent` появился в Aspose.Words 22.8. Если у вас более старая версия, обновитесь или вручную вычислите проценты и задайте их как пользовательские подписи.

---

## Итоги

Мы рассмотрели **как вставить круговую диаграмму** в документ Word с помощью Aspose.Words, показали, как **добавить процент в подписи данных**, и продемонстрировали самый простой способ **отобразить проценты на диаграмме**. Всего несколькими строками Java вы можете **добавить круговую диаграмму в word** и **показать процент на круговой диаграмме**, превращая сырые цифры в мгновенно понятные визуалы.

---

## Что дальше?

- Поэкспериментируйте с другими типами диаграмм (`BAR`, `LINE`, `AREA`) и посмотрите, как та же логика **add data label percent** применяется к ним.
- Сочетайте диаграммы с таблицами для более насыщенных отчётов — Aspose.Words позволяет легко разместить диаграмму рядом с таблицей данных.
- Исследуйте экспорт того же документа в PDF или HTML, чтобы увидеть, как проценты отображаются в разных форматах.

Не бойтесь менять размеры, цвета или источник данных (например, запрос к базе) — и наблюдайте, как ваши Word‑отчёты оживают. Если возникнут сложности, оставляйте комментарий ниже — приятного построения диаграмм!

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом пособии. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Вставить столбчатую диаграмму в Word с помощью Aspose.Words для .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Вставить областную диаграмму в документ Word | Aspose.Words для .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Вставить пузырьковую диаграмму в Word с помощью Aspose.Words для .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}