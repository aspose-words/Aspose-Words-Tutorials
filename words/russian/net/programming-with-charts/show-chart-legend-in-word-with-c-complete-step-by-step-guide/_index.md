---
category: general
date: 2026-06-02
description: Отобразите легенду диаграммы в документе Word с помощью C#. Узнайте,
  как добавить легенду, применить предустановленный стиль диаграммы и настроить визуальные
  элементы диаграммы Word за несколько минут.
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: ru
og_description: Покажите легенду диаграммы в документе Word мгновенно. Это руководство
  проведёт вас через добавление легенды, применение предустановленного стиля диаграммы
  и обработку особых случаев.
og_title: Показать легенду диаграммы в Word – Полный учебник C#
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: Отображение легенды диаграммы в Word с помощью C# – Полное пошаговое руководство
url: /ru/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Показать легенду диаграммы в Word с C# – Полное пошаговое руководство

Когда‑нибудь задумывались **как добавить легенду** к диаграмме, находящейся внутри документа Word? Вы не одиноки. Во многих отчетах отсутствие легенды делает данные непонятными, а исправить это не должно быть головной болью.  

В этом руководстве мы **покажем легенду диаграммы** в файле Word, используя Aspose.Words for .NET, применим предустановленный стиль диаграммы и убедимся, что легенда отображается именно там, где вам нужно. К концу у вас будет готовый к запуску пример, который можно добавить в любой проект C#.

## Что покрывает это руководство

Мы пройдем весь процесс:

1. Загрузить существующий *.docx*, который уже содержит диаграмму.  
2. Получить первую диаграмму (или любую нужную вам диаграмму).  
3. **Применить предустановленный стиль диаграммы**, чтобы придать визуалу профессиональный вид.  
4. **Показать легенду диаграммы**, разместить её справа и обработать особые случаи, такие как Waterfall‑диаграммы.  
5. Сохранить изменённый документ.

Никаких внешних инструментов, без ручного вмешательства в пользовательский интерфейс — только чистый код. Единственное требование — ссылка на пакет NuGet Aspose.Words (версия 23.10 или новее) и базовое понимание C#.

## Требования

- .NET 6.0 или новее (пример также работает с .NET Framework 4.7.2).  
- Библиотека Aspose.Words for .NET установлена (`Install-Package Aspose.Words`).  
- Файл Word (`input.docx`), который уже содержит хотя бы одну диаграмму.  
- Visual Studio, Rider или любая предпочитаемая IDE.

## Шаг 1: Настройка проекта и загрузка документа

Сначала создайте консольное приложение (или интегрируйте код в существующий проект). Добавьте директивы `using` и загрузите файл `.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **Почему это важно:** Загрузка документа — основа. Без экземпляра `Document` вы не сможете получить доступ к объектам диаграмм, которые предоставляет Aspose.Words.

## Шаг 2: Получение целевой диаграммы

Диаграммы хранятся как узлы внутри дерева документа. Метод `GetChild` выполняет глубокий поиск, позволяя нам получить первую диаграмму независимо от того, где она находится (в заголовке, теле, нижнем колонтитуле и т.д.).

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **Подсказка:** Если у вас несколько диаграмм, измените индекс `0` на `1`, `2`, … или перебирайте узлы через `doc.GetChildNodes(NodeType.Chart, true)`.

## Шаг 3: Применение предустановленного визуального стиля

Хорошо выглядящая диаграмма часто начинается со стиля. Aspose.Words поставляется с десятками встроенных стилей; `ChartStyle.Style12` — чистый, современный вариант.

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **Как это работает:** Свойство `Style` сопоставляется со встроенными стилями диаграмм Word, которые вы видите в пользовательском интерфейсе. Выбор предустановки экономит вам ручную настройку цветов, шрифтов и маркеров.

## Шаг 4: Включение легенды и её позиционирование

Теперь к главному элементу — **показать легенду диаграммы**. Мы включаем легенду, а затем привязываем её к правой стороне диаграммы.

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **Почему справа?** Размещение легенды справа сохраняет ширину области данных, что особенно полезно для гистограмм или столбчатых диаграмм.

## Шаг 5: Обработка Waterfall‑диаграмм (особый случай)

Waterfall‑диаграммы ведут себя немного иначе; легенда может быть скрыта по умолчанию. Следующее условие гарантирует, что легенда будет видна, когда тип диаграммы — Waterfall.

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **Примечание к граничному случаю:** Некоторые более старые версии Word игнорируют `HasLegend` для Waterfall‑диаграмм, поэтому явная установка `Legend.Show` гарантирует её отображение.

## Шаг 6: Сохранение изменённого документа

Наконец, запишите изменения обратно на диск. Вы можете перезаписать оригинальный файл или создать новый.

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

Запуск программы создаст `output.docx` с видимой легендой справа, стилизованной `Style12`. Откройте файл в Word, чтобы проверить результат.

## Полный рабочий пример (все шаги вместе)

Ниже приведён полный готовый к запуску код. Скопируйте и вставьте его в `Program.cs` (или любой C# файл) и при необходимости скорректируйте пути к файлам.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**Ожидаемый результат:** При открытии `output.docx` вы увидите оригинальную диаграмму с правой легендой, стилизованной современным `Style12`. Все серии данных чётко помечены, делая диаграмму сразу понятной.

## Часто задаваемые вопросы (FAQ)

### Как добавить легенду к конкретной диаграмме (не к первой?)

Замените индекс `0` в `GetChild(NodeType.Chart, 0, true)` на нулевой позиционный индекс вашей целевой диаграммы или перебирайте все узлы диаграмм:

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### Можно ли разместить легенду внизу вместо справа?

Конечно. Просто измените перечисление `LegendPosition`:

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### Что если у диаграммы уже есть легенда, но я хочу её скрыть?

Установите `HasLegend` в `false`:

```csharp
chart.HasLegend = false;
```

### Работает ли это с Word 2010, 2016 и более новыми версиями?

Да. Aspose.Words абстрагирует конкретную версию Word, поэтому один и тот же код работает со всеми современными .docx файлами.

## Профессиональные советы и распространённые подводные камни

- **Профессиональный совет:** После применения стиля вы всё ещё можете подправить отдельные элементы (цвета, подписи данных) через коллекцию `Chart.Series`. Стиль даёт надёжную основу.  
- **Осторожно:** Если диаграмма находится внутри ячейки таблицы, легенда может выглядеть сжато. Рассмотрите возможность увеличения размеров диаграммы (`chart.Width`, `chart.Height`) перед позиционированием легенды.  
- **Примечание о производительности:** Загрузка больших документов (сотни МБ) может требовать много памяти. Используйте `LoadOptions` с `LoadFormat.Docx`, чтобы снизить нагрузку, если вам нужна только работа с диаграммами.

## Следующие шаги

Теперь, когда вы знаете **как добавить легенду** и **применить предустановленный стиль диаграммы** в Word, вы можете исследовать:

- **Пользовательские цвета диаграммы** (`chart.Series[i].Format.Fill.ForeColor`).  
- **Форматирование подписей данных** (`chart.Series[i].HasDataLabel = true`).  
- **Экспорт диаграммы как изображения** (`chart.ToImage()`), полезно для встраивания в другие места.  

Каждая из этих тем базируется на той же объектной модели, поэтому кривая обучения будет плавной.

## Заключение

Мы только что продемонстрировали чистое, сквозное решение для **показа легенды диаграммы** в документе Word с использованием C#. Загрузив документ, получив диаграмму, применив предустановленный стиль, включив легенду и обработав особенности Waterfall, вы получаете отшлифованную диаграмму, готовую для любого бизнес‑отчёта.  

Не стесняйтесь экспериментировать с другими значениями `ChartStyle` или позициями легенды — ваши визуализации данных заслуживают лучшего представления. Если возникнут проблемы, оставьте комментарий ниже; приятного кодинга!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, которые опираются на техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Вставить столбчатую диаграмму в документ Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [Скрыть оси диаграммы в документе Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Использование API диаграмм Word](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}