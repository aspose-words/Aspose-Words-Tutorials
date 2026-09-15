---
category: general
date: 2026-09-14
description: Вставьте радарную диаграмму в Word с помощью C#. Узнайте, как задать
  заголовок диаграммы, добавить несколько рядов и создать диаграмму программно всего
  за несколько строк.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert radar chart
- set chart title
- create radar chart word
- multiple series radar chart
- create chart programmatically
language: ru
lastmod: 2026-09-14
og_description: Вставьте радиальную диаграмму в Word с помощью C#. Этот учебник показывает,
  как задать заголовок диаграммы, добавить несколько рядов и создать диаграмму программно.
og_image_alt: Screenshot of a Word document displaying a radar chart with sales data
og_title: Вставка радарной диаграммы в Word с C# – краткое руководство по программированию
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Insert radar chart in Word with C#. Learn how to set chart title, add
    multiple series, and create the chart programmatically in just a few lines.
  headline: Insert radar chart in Word using C# – step‑by‑step guide
  type: TechArticle
tags:
- radar chart
- C#
- Aspose.Words
title: Вставка радиальной диаграммы в Word с помощью C# — пошаговое руководство
url: /ru/net/programming-with-charts/insert-radar-chart-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Вставка радиальной диаграммы в Word с помощью C# – пошаговое руководство

Если вам нужно **вставить радиальную диаграмму** в документ Word, это руководство покажет, как сделать это программно на C#. Вы также узнаете, как **установить заголовок диаграммы**, добавить **радиальную диаграмму с несколькими сериями** и сохранить файл, не покидая IDE.

В учебнике рассматривается всё: от настройки проекта до окончательного вызова `doc.Save`, так что вы можете скопировать‑вставить полный пример и сразу запустить его. Поиск внешней документации не требуется.

## Предварительные требования

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6 (или новее) установлен.
* Действительная лицензия Aspose.Words for .NET (или временный оценочный ключ).
* Visual Studio 2022 или любой другой предпочитаемый IDE для C#.

> **Полезный совет:** Если вы используете бесплатную пробную версию, не забудьте установить лицензию до первой создания `Document`, чтобы избежать водяного знака оценки.

## Шаг 1: Вставка радиальной диаграммы в документ Word

Первая операция – создать новый `Document` и `DocumentBuilder`. Builder предоставляет доступ к содержимому документа и позволяет разместить **радиальную диаграмму** точно там, где это необходимо.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank Word document.
Document doc = new Document();

// DocumentBuilder provides methods to insert content.
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a radar (radial) chart at the current cursor position.
Chart chart = builder.InsertChart(ChartType.Radar);
```

*Почему этот шаг важен:* `InsertChart` создаёт объект диаграммы, который можно полностью настроить до сохранения документа. Использование `ChartType.Radar` сообщает Word отрисовать радиальную диаграмму вместо столбчатой или линейной.

## Шаг 2: Установка заголовка диаграммы и делений осей

Диаграмма без заголовка может сбивать с толку. Здесь мы **устанавливаем заголовок диаграммы** на «Sales Radar» и включаем деления на обеих осях (доступно, начиная с Aspose.Words 24.9).

```csharp
// Give the chart a meaningful title.
chart.Title.Text = "Sales Radar";

// Enable graduations (grid lines) on both X and Y axes.
chart.AxisX.HasGraduations = true;
chart.AxisY.HasGraduations = true;
```

*Почему этот шаг важен:* Заголовок даёт контекст читателям, а деления повышают читаемость, показывая, где каждый пункт данных находится на шкале.

## Шаг 3: Создание нескольких серий для радиальной диаграммы

**Радиальная диаграмма с несколькими сериями** позволяет сравнивать разные периоды рядом. Ниже мы добавляем две серии — Q1 и Q2 — каждая с тремя точками данных.

```csharp
// Series 1: Q1 data.
chart.Series.Add(
    "Q1",                                 // Series name
    new[] { "Jan", "Feb", "Mar" },        // Category labels
    new[] { 10, 20, 30 }                  // Values
);

// Series 2: Q2 data.
chart.Series.Add(
    "Q2",
    new[] { "Jan", "Feb", "Mar" },
    new[] { 15, 25, 35 }
);
```

*Почему этот шаг важен:* Добавление нескольких серий демонстрирует, как сравнивать наборы данных на одной радиальной диаграмме, что часто требуется для продаж, показателей эффективности или результатов опросов.

## Шаг 4: Программное сохранение документа Word

Наконец, вы **программно создаёте диаграмму** и сохраняете документ на диск. Метод `Save` записывает файл `.docx`, который можно открыть в Microsoft Word.

```csharp
// Define the output path. Adjust the directory as needed.
string outputPath = Path.Combine(
    Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
    "RadialGraduations.docx"
);

// Save the document containing the radar chart.
doc.Save(outputPath);
```

Когда вы откроете `RadialGraduations.docx`, вы увидите радиальную диаграмму с заголовком «Sales Radar» и двумя сериями (Q1 и Q2), построенными по месяцам Jan‑Mar.

### Ожидаемый результат

![Диаграмма радиальная в Word](https://example.com/radar-chart.png){: .align-center alt="Документ Word, показывающий радиальную диаграмму с двумя сериями данных"}

Скриншот (или сам файл) подтверждает, что диаграмма была вставлена, получила заголовок и корректно заполнена.

## Полный, исполняемый пример

Объединив всё вместе, получаем автономную программу, которую можно скомпилировать и запустить:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a radar chart.
        Chart chart = builder.InsertChart(ChartType.Radar);

        // 3. Set chart title and enable axis graduations.
        chart.Title.Text = "Sales Radar";
        chart.AxisX.HasGraduations = true;
        chart.AxisY.HasGraduations = true;

        // 4. Add two data series.
        chart.Series.Add("Q1", new[] { "Jan", "Feb", "Mar" }, new[] { 10, 20, 30 });
        chart.Series.Add("Q2", new[] { "Jan", "Feb", "Mar" }, new[] { 15, 25, 35 });

        // 5. Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialGraduations.docx"
        );
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Запустите программу, откройте сгенерированный файл и убедитесь, что операция **вставки радиальной диаграммы** прошла успешно.

## Часто задаваемые вопросы и особые случаи

| Вопрос | Ответ |
|----------|--------|
| **Можно ли изменить тип диаграммы после вставки?** | Да. После `InsertChart` присвойте новое значение `ChartType` свойству `chart.Type`. Однако создание диаграммы с нужным типом сразу более эффективно. |
| **Что делать, если нужно больше двух серий?** | Вызывайте `chart.Series.Add` для каждой дополнительной серии. Диаграмма автоматически скорректирует легенду и цвета. |
| **Как настроить цвета или маркеры?** | Используйте `chart.Series[i].Format.Fill.ForeColor` для цветов заливки и `chart.Series[i].Marker` для стилей маркеров. |
| **Совместим ли API с .NET Framework?** | Тот же код работает с .NET Framework 4.7+; просто подключите соответствующую библиотеку Aspose.Words DLL. |
| **Что если я использую более старую версию Aspose.Words?** | Деления (`HasGraduations`) появились в версии 24.9. В более старых версиях можно добавить сетку вручную через `chart.AxisX.MajorGridLines` и `chart.AxisY.MajorGridLines`. |

## Заключение

Теперь вы знаете, как **вставить радиальную диаграмму** в документ Word с помощью C#, **установить заголовок диаграммы**, добавить **радиальную диаграмму с несколькими сериями** и **программно создать диаграмму**. Это сквозное решение позволяет автоматизировать отчётность, панели мониторинга или любые сценарии, где требуется визуальное сравнение категорий.

Далее изучайте связанные темы, такие как **настройка цветов диаграммы**, **экспорт диаграмм в изображения** или **встраивание диаграмм в PDF‑файлы**. Экспериментируйте с различными наборами данных, чтобы увидеть, как радиальная визуализация адаптируется.

Удачной разработки!

## Что стоит изучить дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающие вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Вставка столбчатой диаграммы в Word с помощью Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Вставка пузырьковой диаграммы в Word с помощью Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)
- [Вставка областной диаграммы в документ Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}