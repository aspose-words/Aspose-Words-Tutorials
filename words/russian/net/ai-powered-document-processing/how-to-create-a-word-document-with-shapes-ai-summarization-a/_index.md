---
category: general
date: 2026-11-25
description: Узнайте, как создать документ Word, добавить прямоугольную форму, суммировать
  документ с помощью ИИ, переводить текст с помощью ИИ и сохранять документ в формате
  DOCX, используя Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- summarize document with ai
- save document as docx
- translate text using ai
language: ru
lastmod: 2026-11-25
og_description: Создайте документ Word, добавьте форму прямоугольника, резюмируйте
  документ с помощью ИИ, переведите текст с помощью ИИ и сохраните документ в формате
  DOCX — всё в одном учебнике по C#.
og_image_alt: Screenshot showing a generated Word document with a rectangle shape
  and AI‑generated summary
og_title: Создайте документ Word с фигурами, AI‑резюме и переводом на C#
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a Word document, add rectangle shape, summarize
    document with AI, translate text using AI, and save document as DOCX using Aspose.Words.
  headline: How to create a Word document with shapes, AI summarization, and translation
    in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- AI integration
title: Как создать документ Word с фигурами, AI‑резюмированием и переводом в C#
url: /ru/net/ai-powered-document-processing/how-to-create-a-word-document-with-shapes-ai-summarization-a/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать документ Word с фигурами, суммированием ИИ и переводом на C#

Если вам нужно **программно создать документ Word**, это руководство покажет, как именно это сделать. С помощью Aspose.Words for .NET вы научитесь **добавлять прямоугольную фигуру**, вызывать сервис ИИ для **суммирования документа с помощью ИИ**, переводить абзац с помощью **перевода текста с помощью ИИ**, а затем **сохранять документ как DOCX**.

Многие разработчики сталкиваются с проблемой объединения автоматизации документов и современных функций ИИ. К концу этого урока у вас будет единый, автономный проект C#, который генерирует полностью отформатированный файл *.docx*, содержащий визуальную фигуру, сгенерированное ИИ резюме и многоязычное содержание.

## Предварительные требования

Прежде чем начать, убедитесь, что у вас есть:

- .NET 6.0 SDK или более поздняя версия  
- Visual Studio 2022 (или любая IDE для C#)  
- Лицензия Aspose.Words for .NET (или бесплатный ключ оценки)  
- Доступ в Интернет для вызовов ИИ‑суммирования и перевода  

Дополнительные пакеты NuGet не требуются, кроме `Aspose.Words` и `Aspose.Words.AI`.

## Шаг 1: Настройка проекта и добавление необходимых пакетов

Создайте новый консольный проект и подключите библиотеки Aspose.Words.

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **Совет:** Если вы планируете использовать режим оценки, вызовите `Aspose.Words.License.SetLicense("Aspose.Words.lic");` в начале `Main`, чтобы избавиться от водяных знаков.

## Шаг 2: Инициализация документа – ядро **create word document**

Первая исполняемая строка кода создает новый объект **Word document**. Этот объект служит холстом для всех последующих операций.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // Create a new, empty Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` упрощает вставку текста, фигур и элементов управления без необходимости вручную работать с низкоуровневыми деревьями узлов.

## Шаг 3: **Add rectangle shape** в документ

Прямоугольная фигура может использоваться как визуальный заполнитель, фон метки или простая графика. Сначала мы создаём `GroupShape`, затем вставляем в неё `Rectangle`.

```csharp
        // Step 3: Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

Прямоугольник имеет ширину 100 пунктов и высоту 50 пунктов. Поскольку он находится внутри `GroupShape`, позже вы сможете добавить другие элементы (например, текстовые поля), не беспокоясь о конфликте раскладки.

## Шаг 4: Вставка простого StructuredDocumentTag (SDT)

Объекты StructuredDocumentTag полезны для элементов управления содержимым, которые позже можно привязать к источникам данных.

```csharp
        // Step 4: Add a plain‑text StructuredDocumentTag (SDT) to the document
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);
```

Флаг `true` помечает тег как **повторяющийся** контроль, что удобно для шаблонов.

## Шаг 5: Добавление элемента управления ActiveX CommandButton (опциональный UI)

Если генерируемый документ будет использоваться в среде, поддерживающей ActiveX, вы можете встроить кнопку.

```csharp
        // Step 5: Insert an ActiveX CommandButton control (Forms2 OLE control)
        builder.InsertForms2OleControl(OleControlType.CommandButton);
```

Этот шаг необязателен; вы можете удалить его, если ваша целевая аудитория никогда не будет взаимодействовать с документом в Windows‑окружении.

## Шаг 6: **Summarize document with AI**

Aspose.Words.AI предоставляет удобный обёртка вокруг сервисов больших языковых моделей. Здесь мы вызываем `DocumentSummarizer.Summarize` с бэкендом OpenAI.

```csharp
        // Step 6: Summarize the document content using an AI service
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);
```

Метод анализирует текущие узлы дерева, извлекает наиболее релевантные предложения и возвращает лаконичный абзац. Это ядро функции **summarize document with AI**.

## Шаг 7: **Translate text using AI**

Далее демонстрируется, как перевести примерную строку с английского на французский. Метод `Translator.Translate` внутри вызывает модель Google AI.

```csharp
        // Step 7: Translate a sample paragraph to French using Google AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);
```

Вы можете заменить `Language.French` на любое поддерживаемое значение перечисления языка, позволяя генерировать многоязычные документы «на лету».

## Шаг 8: **Save document as DOCX**

Наконец, сохраняем изменённый документ на диск. Метод `Save` автоматически записывает файл *.docx*, если указать расширение `.docx`.

```csharp
        // Step 8: Save the modified document
        document.Save("Result.docx"); // **save document as docx**
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

Файл `Result.docx` теперь содержит:

- Прямоугольную фигуру внутри групповой фигуры  
- Простой текстовый элемент управления содержимым (SDT)  
- Кнопку ActiveX CommandButton (если вы оставили Шаг 5)  
- Абзац с резюме, сгенерированным ИИ  
- Французский перевод фразы «Hello world»

Вы можете открыть файл в Microsoft Word, чтобы проверить каждый элемент.

## Полный исходный код

Ниже представлена полностью готовая к запуску программа. Скопируйте её в `Program.cs` и выполните `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // 1. Create a new Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3. Add a plain‑text StructuredDocumentTag (SDT)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);

        // 4. Insert an ActiveX CommandButton (optional)
        builder.InsertForms2OleControl(OleControlType.CommandButton);

        // 5. Summarize the document using AI
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);

        // 6. Translate a paragraph to French using AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);

        // 7. Save the document as DOCX
        document.Save("Result.docx");
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

### Ожидаемый вывод

```
Document summary:
[AI‑generated concise summary of the document’s current content]

Translated paragraph (English → French):
Bonjour le monde

Document saved as Result.docx
```

Когда вы откроете `Result.docx`, вы увидите прямоугольную фигуру в верхней части, заполнитель SDT, кнопку, абзац с резюме и французский перевод, вставленные как обычный текст.

## Заключение

Теперь вы знаете, как **создать документ Word** с нуля, **добавить прямоугольную фигуру**, **суммировать документ с помощью ИИ**, **перевести текст с помощью ИИ** и **сохранить документ как DOCX** — всё это несколькими лаконичными строками C#. Этот подход масштабируется: вы можете заменить жёстко закодированные строки динамическими данными, добавить больше фигур или диаграмм и переключить провайдера ИИ, изменив параметры `SummarizerOptions` или `Translator`.

### Что дальше?

- Исследуйте варианты **add rectangle shape**: измените цвет заливки, стиль линии или добавьте текст внутри фигуры.  
- Используйте **summarize document with AI** для больших документов, чтобы автоматически генерировать исполнительные резюме.  
- Расширьте **translate text using AI**, чтобы пакетно обрабатывать целые абзацы или таблицы для многоязычных отчётов.  
- Комбинируйте API построения диаграмм Aspose.Words для встраивания визуализаций данных рядом с ИИ‑сгенерированными инсайтами.  

Экспериментируйте и делитесь результатами в комментариях или на GitHub. Приятного кодинга!

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Create a blank word document and add a rectangle shape](/words/english/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Add Text Watermark in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}