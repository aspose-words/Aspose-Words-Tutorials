---
category: general
date: 2026-08-10
description: Форматируйте разделитель сносок в C# с помощью Aspose.Words, чтобы настроить
  линии сносок и концевых сносок. Изучите форматирование сносок в C# за несколько
  минут.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: ru
lastmod: 2026-08-10
og_description: Отформатировать разделитель сносок в C# с помощью Aspose.Words. Следуйте
  этому руководству, чтобы быстро и надёжно оформить разделители сносок и концевых
  сносок.
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: Форматирование разделителя сносок в C# — полное руководство по Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: Форматировать разделитель сносок в C# с помощью Aspose.Words
url: /ru/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Форматирование разделителя сносок в C# с использованием Aspose.Words

Если вам нужно **отформатировать разделитель сносок** в документе Word, это руководство покажет, как сделать это с помощью Aspose.Words для .NET. Вы увидите полностью готовый, исполняемый пример, который изменяет выравнивание и цвет абзаца‑разделителя, а также узнаете, как применить ту же технику к разделителям концевых сносок.

В руководстве рассматривается каждый шаг — от загрузки исходного файла до сохранения изменённого документа — чтобы вы могли скопировать‑вставить код в свой проект без дополнительного поиска информации.

## Что понадобится

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6.0 или новее (код также работает с .NET Framework 4.6+)
* Действительная лицензия Aspose.Words для .NET (бесплатная пробная версия подходит для оценки)
* Файл Word, содержащий хотя бы одну сноску или концевую сноску (например, `Footnotes.docx`)
* Visual Studio 2022 или любой другой предпочитаемый IDE для C#

Наличие этих элементов позволяет сосредоточиться на **логике форматирования сносок в C#**, а не на настройке окружения.

## Шаг 1: Загрузите документ, содержащий сноски и концевые сноски

Первой операцией является создание объекта `Document`, указывающего на ваш исходный файл. Aspose.Words считывает весь пакет DOCX в память, предоставляя полный доступ к узлам сносок и концевых сносок.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*Почему это важно*: Загрузка документа — предпосылка для любой модификации. Если путь к файлу указан неверно, Aspose.Words выбросит `FileNotFoundException`, поэтому проверьте путь перед продолжением.

## Шаг 2: Получите узлы разделителя и продолжения‑разделителя

Разделители сносок и концевых сносок хранятся как специальные узлы внутри коллекций `Footnotes` и `Endnotes`. Каждая коллекция предоставляет свойства `Separator` и `ContinuationSeparator`, которые возвращают ссылку на объект `Node`.

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*Почему это важно*: Узел `Separator` представляет линию, визуально отделяющую основной текст от блока сносок. Получив ссылку, вы можете изменить формат абзаца, шрифт или даже полностью заменить узел.

## Шаг 3: Измените визуальный стиль разделителя сносок

В большинстве документов Word разделитель представляет собой один абзац, содержащий тире или звёздочку. Ниже приведён код, который проверяет, является ли разделитель объектом `Paragraph`, и, если да, центрирует его и меняет цвет текста на серый.

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### Форматирование разделителя продолжения (необязательно)

Разделитель продолжения появляется, когда сноска занимает несколько страниц. Его можно оформить аналогично:

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*Почему это важно*: Выравнивание разделителя улучшает читаемость, а изменение цвета отличает его от обычного текста абзаца. Вы можете заменить `ParagraphAlignment.Center` на `Left` или `Right`, чтобы соответствовать рекомендациям по дизайну вашего документа.

## Шаг 4: Сохраните изменённый документ

После применения желаемого стиля запишите документ обратно на диск. Можно перезаписать исходный файл или создать новую версию.

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

При открытии `Footnotes_Styled.docx` в Microsoft Word разделитель сносок будет отображаться по центру и серым цветом, точно как указано в коде.

## Расширенные варианты

### Форматирование разделителя концевой сноски

Если ваш документ также использует концевые сноски, ту же логику можно применить к коллекции `Endnotes`:

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### Использование пользовательской строки в качестве разделителя

Иногда требуется, чтобы разделителем была серия звёздочек (`***`). Замените существующие `Run` новым:

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### Обработка документов без узла разделителя

Редкий случай — документ, в котором узел разделителя отсутствует (например, автор удалил его). В такой ситуации `document.Footnotes.Separator` возвращает `null`. Защищайте код от этого:

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## Распространённые подводные камни и как их избежать

| Проблема | Почему происходит | Решение |
|----------|-------------------|---------|
| **Separator не является `Paragraph`** | В некоторых шаблонах Word в качестве разделителя используется `Table` или `Shape`. | Проверьте тип узла с помощью `is Paragraph` перед приведением типа. |
| **Коллекция `Runs` пуста** | Разделитель может быть пустым абзацем. | Убедитесь, что `Runs.Count > 0` перед обращением к `Runs[0]`. |
| **Лицензия не применена** | Без лицензии Aspose.Words вставляет водяной знак и может ограничивать использование API. | В начале программы вызовите `License license = new License(); license.SetLicense("Aspose.Words.lic");`. |
| **Сохранение в папку только для чтения** | Метод `Save` бросает `UnauthorizedAccessException`. | Убедитесь, что целевая директория имеет права записи. |

Устранение этих проблем на ранних этапах предотвращает исключения во время выполнения и обеспечивает плавный процесс **модификации разделителя сносок**.

## Полный, исполняемый пример

Ниже представлено автономное консольное приложение, демонстрирующее каждый из описанных выше шагов. Скопируйте код в новый .NET‑консольный проект, замените пути к файлам и запустите его.

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**Ожидаемый результат**  

При открытии `Footnotes_Styled.docx`:

* Линия разделителя сносок будет центрирована под основным текстом.  
* Её цвет будет светло‑серым, что делает её визуально отличимой.  
* Если документ содержит концевые сноски, их разделители также будут центрированы и окрашены в серый (или сланцевый) цвет.

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогая вам освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Set Footnote And Endnote Position](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Working With Footnote And Endnote](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}