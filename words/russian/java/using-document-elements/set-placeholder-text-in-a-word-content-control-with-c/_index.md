---
category: general
date: 2026-11-22
description: Установите текст‑заполнитель в элемент управления содержимым Word с помощью
  C#. Узнайте, как создать пользовательский тег, вставить элемент управления простым
  текстом и добавить заполнитель к тегу с использованием Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- create custom tag
- how to insert content control
- add placeholder to tag
- insert plain text control
language: ru
lastmod: 2026-11-22
og_description: Установите текст‑заполнитель в элемент управления содержимым Word
  с помощью C#. В этом руководстве показано, как создать пользовательский тег, вставить
  элемент управления простым текстом и добавить заполнитель к тегу для повышения интерактивности
  документа.
og_image_alt: Screenshot showing a Word document with a content control placeholder
  text set using C#
og_title: Установка текста‑заполнителя в элемент управления содержимым Word – руководство
  по C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Set placeholder text in a Word content control with C#. Learn how to
    create a custom tag, insert a plain text control, and add placeholder to tag using
    Aspose.Words.
  headline: Set placeholder text in a Word content control with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Установить текст‑заполнитель в элемент управления содержимым Word с помощью
  C#
url: /ru/java/using-document-elements/set-placeholder-text-in-a-word-content-control-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Установить текст-заполнитель в элемент управления содержимым Word с помощью C#

Если вам нужно **установить текст-заполнитель** в документ Word программно, это руководство покажет, как это сделать. С помощью Aspose.Words for .NET вы можете создать пользовательский тег, вставить элемент управления plain‑text и добавить заполнитель к тегу, чтобы документ был готов к вводу пользователем.

В этом учебнике вы узнаете, как **создать пользовательский тег**, **вставить элемент управления содержимым**, и **добавить заполнитель к тегу**, при этом код останется лаконичным и готовым к продакшн‑использованию. Внешние инструменты не требуются — только проект .NET и библиотека Aspose.Words.

## Требования

* .NET 6.0 SDK или более поздняя версия, установленная  
* Действительная лицензия Aspose.Words for .NET (или бесплатный оценочный ключ)  
* Базовые знания C# и Visual Studio (или любой предпочитаемой IDE)  

В следующих разделах предполагается, что вы создали консольный проект с именем `WordPlaceholderDemo`.

## Шаг 1: Установить Aspose.Words

Добавьте пакет NuGet в ваш проект:

```bash
dotnet add package Aspose.Words
```

> **Совет:** Используйте флаг `--version`, чтобы зафиксировать пакет на последней стабильной версии (например, `Aspose.Words.NET 24.9`).

## Шаг 2: Загрузить исходный документ и создать `DocumentBuilder`

Первое, что вам нужно сделать, — загрузить существующий файл `.docx` (или создать новый пустой документ) и создать экземпляр `DocumentBuilder`. Builder предоставляет удобный API для вставки элементов управления и текста.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Load an existing Word file or create a new one
            Document doc = new Document("input.docx");   // <-- replace with your path
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Этот код **подготавливает** вставку элемента управления содержимым. `DocumentBuilder` работает непосредственно с объектом `doc`, поэтому любые изменения автоматически отражаются.

## Шаг 3: Создать пользовательский тег (StructuredDocumentTag)

В Word *пользовательский тег* называется **StructuredDocumentTag (SDT)**. Его можно рассматривать как элемент управления содержимым, содержащий уникальный идентификатор. Создание такого тега является основной частью шага **create custom tag**.

```csharp
            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
```

Метод `InsertStructuredDocumentTag` принимает два аргумента:

1. Тип элемента управления (`PlainText` в данном случае).  
2. Строка, уникально идентифицирующая тег (`"MyTag"`).  

Используя **пользовательский тег**, вы позже сможете находить или управлять элементом управления программно.

## Шаг 4: Установить заголовок для доступности

Заголовок улучшает доступность и упрощает поиск элемента управления в интерфейсе Word.

```csharp
            // Set a descriptive title (used by screen readers)
            sdt.Title = "CustomerName";
```

Свойство `Title` является необязательным, но его добавление считается лучшей практикой при **add placeholder to tag** для улучшения пользовательского опыта.

## Шаг 5: Добавить текст-заполнитель к тегу

Теперь наступает главная цель: **установить текст-заполнитель**. Этот текст отображается, когда элемент управления пуст, подсказывая пользователю, что ввести.

```csharp
            // Provide placeholder text that shows when the tag is empty
            sdt.PlaceholderText = "Enter name…";
```

Свойство `PlaceholderText` — именно то, что нужно для **add placeholder to tag**. Оно работает как серый подсказочный текст, который вы видите в современных полях формы.

## Шаг 6: Сохранить изменённый документ

После настройки элемента управления запишите документ обратно на диск.

```csharp
            // Save the document with the new content control
            doc.Save("output.docx");   // <-- replace with your desired path
        }
    }
}
```

Когда вы откроете `output.docx` в Microsoft Word, вы увидите элемент управления plain‑text с меткой «CustomerName» и заполнитель «Enter name…». При щелчке внутри элемента заполнитель исчезает, позволяя пользователю вводить текст.

### Ожидаемый результат

* Файл Word (`output.docx`) с единственным элементом управления plain‑text.  
* Элемент отображает заполнитель «Enter name…», пока пользователь не введёт что‑то.  
* Идентификатор тега элемента — `MyTag`, который можно запросить позже с помощью `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.

## Шаг 7: Как вставить элемент управления содержимым в другое место (расширенно)

Если вам нужно **how to insert content control** в определённое место — например, после конкретного абзаца — используйте метод `MoveTo` перед вставкой тега:

```csharp
            // Move the cursor to the end of the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            // Insert another plain‑text control with a different tag
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";
```

Этот фрагмент демонстрирует **insert plain text control** несколько раз в одном документе.

## Распространённые подводные камни и как их избежать

| Проблема | Почему происходит | Решение |
|----------|-------------------|---------|
| Placeholder not visible | The control already contains text (even a space) | Ensure `sdt.Text` is empty before setting `PlaceholderText`. |
| Tag identifier collision | Re‑using the same tag name (`MyTag`) in the same document | Use unique identifiers for each `StructuredDocumentTag`. |
| License exception | Running without a valid Aspose.Words license | Apply a license file (`license.SetLicense("Aspose.Words.lic")`) at the start of `Main`. |
| Document not saved | Forgetting to call `doc.Save` or using a read‑only path | Verify the output path is writable and call `doc.Save`. |

## Полный рабочий пример

Ниже приведена полная программа, которую вы можете скопировать и вставить в `Program.cs`. Она включает все шаги — **create custom tag**, **how to insert content control**, **add placeholder to tag**, и **insert plain text control** — в едином последовательном потоке.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Optional: apply your Aspose.Words license here
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // Load the source document (or create a new one)
            Document doc = new Document("input.docx");
            DocumentBuilder builder = new DocumentBuilder(doc);

            // --------- Create custom tag ----------
            StructuredDocumentTag nameTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
            nameTag.Title = "CustomerName";
            nameTag.PlaceholderText = "Enter name…";

            // Insert a second control after the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";

            // Save the result
            doc.Save("output.docx");
            Console.WriteLine("Document saved with placeholder text set.");
        }
    }
}
```

Запустите программу командой `dotnet run`. После выполнения откройте `output.docx`, чтобы убедиться, что оба элемента управления отображают свои соответствующие заполнители.

## Следующие шаги

* **Настроить внешний вид** — используйте `sdt.Font` для изменения размера шрифта, цвета или стиля внутри элемента управления.  
* **Привязать к XML‑данным** — изучите `sdt.XmlMapping`, если необходимо, чтобы элемент управления был связан

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, которые опираются на техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Create word document programmatically – add content control and placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Set Placeholder Text in Aspose.Words – Complete C# Guide](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Create new Word document and insert content control in C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}