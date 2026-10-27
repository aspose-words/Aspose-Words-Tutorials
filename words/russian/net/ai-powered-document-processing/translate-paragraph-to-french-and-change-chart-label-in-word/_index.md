---
category: general
date: 2026-10-10
description: Переведите абзац на французский и узнайте, как изменить подпись данных
  диаграммы, настроить подпись данных диаграммы и сохранить отредактированный файл docx
  с помощью Aspose.Words AI.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: ru
lastmod: 2026-10-10
og_description: Переведите абзац на французский и узнайте, как изменить подпись данных
  диаграммы, настроить подпись данных диаграммы и сохранить отредактированный файл
  docx с помощью Aspose.Words AI.
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: Перевести абзац на французский и изменить подпись диаграммы в Word
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Translate paragraph to French and learn how to change chart data label,
    customize chart data label, and save edited docx file using Aspose.Words AI.
  headline: Translate paragraph to French and change chart label in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI translation
- chart customization
title: Перевести абзац на французский и изменить подпись диаграммы в Word
url: /ru/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Перевести абзац на французский и изменить подпись диаграммы в Word

Если вам нужно **перевести абзац на французский** и одновременно обновить диаграмму в том же документе Word, это руководство покажет, как это сделать. С помощью Aspose.Words AI вы можете автоматически переводить текст, затем изменять подпись данных диаграммы и, наконец, сохранять отредактированный файл `.docx` — всё в нескольких простых шагах.

В руководстве рассматривается всё: от загрузки исходного файла до сохранения изменений. К концу вы сможете переводить любой абзац, настраивать подпись данных диаграммы и создавать новый файл Word, готовый к распространению. Внешние скрипты не требуются; весь процесс реализован в одной программе на C#.

## Требования

- .NET 6.0 или новее (код также работает с .NET Framework 4.7+)
- Лицензия Aspose.Words for .NET (или бесплатный оценочный ключ)
- Доступ к Интернету для переводчика Google AI (класс `Translator` использует API Google)
- Документ Word (`input.docx`), содержащий как минимум один абзац и одну диаграмму

## Шаг 1: Настройте проект и импортируйте пространства имён

Создайте новое консольное приложение и добавьте пакет Aspose.Words через NuGet:

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Теперь включите необходимые пространства имён в начале файла `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

Эти импорты дают вам доступ к загрузке документов, AI‑переводу и функционалу редактирования диаграмм.

## Шаг 2: Загрузите исходный документ Word

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

Загрузка файла создаёт представление в памяти, которое можно запрашивать и изменять, не затрагивая оригинальный файл на диске.

## Шаг 3: Переведите первый абзац на французский

Первый абзац часто является заголовком или вводным предложением, поэтому его удобно переводить. Класс `Translator` инкапсулирует вызов модели AI от Google.

```csharp
// Retrieve the first paragraph in the first section
Paragraph paragraph = document.FirstSection.Body.FirstParagraph;

// Extract the raw text (including trailing paragraph mark)
string originalText = paragraph.GetText();

// Translate the text to French
string translatedText = Translator.Translate(originalText, Language.French);
Console.WriteLine($"Original: {originalText.Trim()}");
Console.WriteLine($"Translated: {translatedText.Trim()}");

// Replace the paragraph's runs with the translated text
paragraph.Runs.Clear();                     // Remove existing runs
paragraph.AppendChild(new Run(document, translatedText)); // Insert new run
```

**Почему это работает:**  
`paragraph.Runs.Clear()` удаляет все существующие текстовые сегменты, гарантируя, что новый перевод не будет конкатенирован со старым содержимым. `new Run(document, translatedText)` создаёт новый сегмент, наследующий форматирование абзаца.

## Шаг 4: Найдите первую диаграмму и настройте её подпись данных

Диаграммы хранятся как узлы `Shape` типа `NodeType.Shape`. Первую диаграмму можно получить с помощью `GetChild`.

```csharp
// Find the first chart in the document (deep search)
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    Console.WriteLine("No chart found in the document.");
    return;
}

// Access the first series and its first data label
ChartSeries series = chart.Series[0];
ChartDataLabel dataLabel = series.DataLabels[0];

// Change the label's position and text
dataLabel.Position = ChartDataLabelPosition.OutsideEnd; // Move label outside the bar
dataLabel.Text = "Ventes T1"; // French for "Sales Q1"
Console.WriteLine("Chart data label customized.");
```

**Объяснение ключевых шагов:**

- `GetChild(NodeType.Shape, 0, true)` выполняет поиск в глубину и возвращает первый объект shape, который в нашем случае является диаграммой.
- `ChartSeries` представляет коллекцию точек данных; первая серия (`Series[0]`) обычно соответствует основному набору данных.
- `ChartDataLabelPosition.OutsideEnd` перемещает подпись за конец столбца, улучшая читаемость.
- Установка `dataLabel.Text` в строку на французском согласует подпись с переведённым абзацем.

## Шаг 5: Сохраните документ с переведённым абзацем

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

На данном этапе документ содержит французский абзац, но всё ещё сохраняет исходную конфигурацию диаграммы.

## Шаг 6: Сохраните документ с обновлённой диаграммой

Вы можете повторно использовать тот же экземпляр `Document` — повторно загружать его не требуется — поскольку изменения диаграммы уже находятся в памяти.

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

Оба файла теперь готовы к распространению:

- **`translated.docx`** — содержит французский абзац.
- **`chart-updated.docx`** — содержит французский абзац *и* настроенную подпись диаграммы.

## Полный, исполняемый пример

Ниже приведена полная программа, которую вы можете скопировать и вставить в `Program.cs`. Она компилируется и запускается как есть, при условии, что вы заменили `YOUR_DIRECTORY` реальным путём к папке.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

namespace WordAiDemo
{
    class Program
    {
        static void Main()
        {
            // ---------- Load the source document ----------
            string inputPath = @"YOUR_DIRECTORY/input.docx";
            Document document = new Document(inputPath);
            Console.WriteLine("Document loaded.");

            // ---------- Translate the first paragraph ----------
            Paragraph paragraph = document.FirstSection.Body.FirstParagraph;
            string original = paragraph.GetText();
            string translated = Translator.Translate(original, Language.French);
            Console.WriteLine


## Что следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые расширяют техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в собственных проектах.

- [Настроить подпись данных диаграммы](/words/english/net/programming-with-charts/chart-data-label/)
- [Форматировать количество подписей данных в диаграмме](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Подпись данных диаграммы](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}