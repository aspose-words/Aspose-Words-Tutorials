---
category: general
date: 2026-09-21
description: Как создать гистограмму в Word с помощью Aspose.Words. Узнайте, как задать
  интервалы гистограммы и настроить их для точной визуализации данных.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create histogram in word
- how to set histogram bins
- configure histogram bins
language: ru
lastmod: 2026-09-21
og_description: Как создать гистограмму в Word с помощью Aspose.Words. Этот учебник
  покажет, как задать интервалы гистограммы и настроить их для точных диаграмм.
og_image_alt: Screenshot of a Word document showing a histogram chart created with
  Aspose.Words
og_title: Создайте гистограмму в Word с помощью Aspose.Words – полное руководство
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to create histogram in Word with Aspose.Words. Learn how to set
    histogram bins and configure histogram bins for precise data visualisation.
  headline: How to create histogram in Word with Aspose.Words
  type: TechArticle
- description: How to create histogram in Word with Aspose.Words. Learn how to set
    histogram bins and configure histogram bins for precise data visualisation.
  name: How to create histogram in Word with Aspose.Words
  steps:
  - name: Prepare the development environment.
    text: Prepare the development environment.
  - name: Build a blank Word document and obtain a `DocumentBuilder`.
    text: Build a blank Word document and obtain a `DocumentBuilder`.
  - name: Insert a histogram chart and adjust its properties.
    text: Insert a histogram chart and adjust its properties.
  - name: Save the document and verify the result.
    text: Save the document and verify the result.
  type: HowTo
tags:
- histogram
- Aspose.Words
- C#
- Word automation
title: Как создать гистограмму в Word с помощью Aspose.Words
url: /ru/net/programming-with-charts/how-to-create-histogram-in-word-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать гистограмму в Word с помощью Aspose.Words

Если вам нужно создать гистограмму в Word, Aspose.Words делает процесс простым. Это руководство проведет вас через каждый шаг, от настройки проекта до конфигурации корзин гистограммы для четкой визуализации данных. Вы также увидите, как задавать корзины гистограммы и настраивать их в соответствии с требованиями вашего отчета.

## Как создать гистограмму в Word – общий рабочий процесс

1. Подготовьте среду разработки.  
2. Создайте пустой документ Word и получите `DocumentBuilder`.  
3. Вставьте диаграмму гистограммы и настройте её свойства.  
4. Сохраните документ и проверьте результат.

Каждая фаза подробно описана ниже, а полный исходный код предоставлен в конце статьи.

## Настройка среды разработки

Перед тем как писать код, убедитесь, что у вас есть следующие предварительные требования:

| Требование | Причина |
|------------|---------|
| .NET 6.0 или новее | Обеспечивает среду выполнения для проектов C#. |
| Visual Studio 2022 (или любая IDE, поддерживающая .NET) | Позволяет компилировать и отлаживать пример. |
| Aspose.Words for .NET NuGet package | Поставляет классы `Document`, `DocumentBuilder` и классы диаграмм. |

Вы можете добавить пакет Aspose.Words с помощью NuGet CLI:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Используйте фиксированную версию (например, `23.9.0`) в продакшене, чтобы избежать неожиданного ломания изменений.

## Вставка гистограммы

С готовой средой создайте новый консольный проект и откройте файл `Program.cs`. Первые две строки кода создают пустой документ и `DocumentBuilder`, позволяющий манипулировать документом:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank document and a DocumentBuilder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Затем вызовите `InsertChart`, чтобы добавить гистограмму. Метод требует тип диаграммы, ширину и высоту в пунктах:

```csharp
// Insert a histogram chart with a specific size (400x300 points)
Chart histogram = builder.InsertChart(ChartType.Histogram, 400, 300);
```

На данном этапе документ содержит пустой заполнитель гистограммы. При открытии сгенерированного *.docx* файла вы увидите серую область диаграммы, готовую для данных.

![Заполнитель гистограммы в документе Word](/images/histogram-placeholder.png){: .img-fluid alt="Скриншот документа Word, показывающий заполнитель гистограммы, созданный с помощью Aspose.Words"}

## Как задать корзины гистограммы

Гистограмма визуализирует распределение числовых данных, группируя значения в *корзины*. Свойство `HistogramBins` управляет тем, сколько корзин отображает диаграмма. Установка этого свойства до добавления данных гарантирует, что диаграмма резервирует правильное количество столбцов.

```csharp
// Set the number of bins (bars) in the histogram
histogram.HistogramBins = 10;
```

Вы можете изменить количество корзин, чтобы соответствовать детализации вашего набора данных. Например, набор данных от 0 до 100 с количеством корзин 10 создаст интервалы по 10 единиц каждый (0‑9, 10‑19, …, 90‑100).

> **Why it matters:** Выбор слишком малого количества корзин может скрыть важные закономерности, а слишком большое — сделать диаграмму шумной. Протестируйте несколько значений, чтобы найти оптимальный вариант для ваших данных.

## Настройка корзин гистограммы для лучшей читаемости

Помимо количества корзин, часто требуется подписать каждую корзину, чтобы читатели видели точный счёт. Свойство `ShowBinLabels` переключает видимость этих подписей:

```csharp
// Display the value of each bin on the chart
histogram.ShowBinLabels = true;
```

Когда `ShowBinLabels` установлено в `true`, Word отображает числовую подпись над каждым столбцом. Этот небольшой шаг настройки значительно повышает интерпретируемость диаграммы, особенно в отчётах, где у аудитории может не быть исходного набора данных.

Вы также можете настроить внешний вид подписи, например размер шрифта или цвет, через объект `HistogramLabel` (доступен в более поздних версиях Aspose.Words). Ниже приведён типичный пример настройки:

```csharp
// Optional: make bin labels bold and increase font size
histogram.HistogramLabel.Font.Size = 10;
histogram.HistogramLabel.Font.Bold = true;
```

> **Edge case:** Если задать `HistogramBins` значением, превышающим количество уникальных точек данных, некоторые корзины окажутся пустыми. Диаграмма всё равно отрисуется корректно, но визуально может выглядеть разреженной. В таких сценариях рекомендуется уменьшить количество корзин.

## Добавление серии данных в гистограмму

Гистограмма требует одну серию данных, представляющую базовые числовые значения. Вы можете заполнить серию массивом, `List<double>` или любой перечислимой коллекцией. Ниже приведён лаконичный пример, добавляющий случайный набор данных:

```csharp
// Create a data series for the histogram
ChartSeries series = histogram.Series[0];
double[] sampleData = { 12, 45, 23, 67, 34, 89, 54, 31, 22, 78, 41, 60 };
series.DataPoints.AddRange(sampleData);
```

Метод `AddRange` преобразует каждое значение в корзину согласно ранее определённому `HistogramBins`. После этого шагa диаграмма отображает полностью заполненную гистограмму.

## Сохранение и просмотр полученного документа

Наконец, запишите документ на диск. Вы можете выбрать любое доступное приложению место. Следующая строка сохраняет файл как `output.docx`:

```csharp
// Save the document so you can view the chart
doc.Save("output.docx");
```

Откройте `output.docx` в Microsoft Word, чтобы увидеть гистограмму с десятью корзинами, подписанными значениями и вашими образцовыми данными. Диаграмма будет выглядеть аналогично изображению ниже:

![Готовая гистограмма в Word](/images/histogram-complete.png){: .img-fluid alt="Документ Word, отображающий готовую гистограмму с десятью корзинами и метками"}

## Полный, исполняемый пример

Объединив все части, получаем автономную программу, которую можно скопировать, вставить и запустить:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a histogram chart (400×300 points)
        Chart histogram = builder.InsertChart(ChartType.Histogram, 400, 300);

        // 3️⃣ Configure the histogram
        histogram.HistogramBins = 10;          // How to set histogram bins
        histogram.ShowBinLabels = true;       // Configure histogram bins to show labels
        histogram.HistogramLabel.Font.Size = 10;
        histogram.HistogramLabel.Font.Bold = true;

        // 4️⃣ Add a data series
        ChartSeries series = histogram.Series[0];
        double[] data = { 12, 45, 23, 67, 34, 89, 54, 31, 22, 78, 41, 60 };
        series.DataPoints.AddRange(data);

        // 5️⃣ Save the document
        doc.Save("output.docx");
    }
}
```

**Expected output:** При открытии `output.docx` отображается гистограмма с десятью равномерно распределёнными столбцами, каждый из которых подписан своим счётом. Диаграмма отражает распределение массива `data`, делая тенденции сразу видимыми.

## Часто задаваемые вопросы и устранение неполадок

| Вопрос | Ответ |
|--------|-------|
| *Что если мне нужно более одной серии данных?* | Гистограммы обычно представляют одно распределение. Если требуется несколько серий, рассмотрите использование столбчатой диаграммы. |
| *Можно ли изменить размер диаграммы после вставки?* | Да. Отрегулируйте свойства `histogram.Width` и `histogram.Height` или вызовите `builder.InsertChart` снова с другими размерами. |
| *Работает ли это с .NET Framework 4.8?* | Абсолютно. Aspose.Words поддерживает .NET Framework 4.5 и новее, поэтому тот же код работает без изменений. |
| *Как экспортировать диаграмму как изображение?* | Используйте `histogram.ToImage()` для получения `System.Drawing.Image`, затем сохраните его с помощью `image.Save("chart.png")`. |

## Заключение

Теперь вы знаете, как создать гистограмму в Word с помощью Aspose.Words, как задать корзины гистограммы и как настроить их для ясного, подписанного вывода. Полный пример демонстрирует готовый к производству подход, который можно адаптировать к любой задаче отчётности, основанной на данных.  

Далее изучайте связанные темы, такие как **как создать круговые диаграммы в Word**, **настройка цветов диаграмм** и **встраивание источников данных Excel**. Все они опираются на тот же рабочий процесс `DocumentBuilder`, поэтому расширить решение будет легко.

Happy charting!

## Что следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Как создать столбчатую диаграмму с помощью Aspose.Words для Java](/words/english/java/document-conversion-and-export/using-charts/)
- [как создать PDF из Word – Полное руководство C#](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Как загружать документы Word с помощью Aspose.Words LoadOptions](/words/english/net/programming-with-loadoptions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}