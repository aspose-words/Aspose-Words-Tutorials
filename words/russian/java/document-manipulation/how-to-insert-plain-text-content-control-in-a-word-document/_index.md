---
category: general
date: 2026-10-26
description: Научитесь вставлять элемент управления простым текстом с помощью Aspose.Words
  в C#. Пошаговое руководство, охватывающее StructuredDocumentTag, заголовки и идентификаторы
  тегов.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert plain text content control
- structured document tag
- Aspose.Words DocumentBuilder
- C# content control
- SDT appearance
language: ru
lastmod: 2026-10-26
og_description: Вставьте элемент управления простым текстом с помощью Aspose.Words
  в C#. Следуйте этому руководству, чтобы добавить заголовки, идентификаторы тегов
  и настроить внешний вид.
og_image_alt: Screenshot of a Word document showing an inserted plain text content
  control
og_title: Вставка простого текстового элемента управления в Word с помощью C# — полное
  руководство
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  headline: How to insert plain text content control in a Word document with C#
  type: TechArticle
- description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  name: How to insert plain text content control in a Word document with C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Markup;'
  - name: Insert the plain‑text content control (SDT)
    text: '```csharp // Insert a plain‑text Structured Document Tag (SDT) with the
      default appearance. StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
      SdtType.PlainText, // The control type – plain text. SdtAppearance.Default);
      // Visual style; Default shows a light gray shading. ```'
  - name: Set a title and a tag identifier
    text: '```csharp // Give the SDT a friendly title that appears in the Content
      Controls pane. sdt.Title = "MyTag";'
  - name: Variations you might need
    text: '| Scenario | Code change | |----------|-------------| | **No visual shading**
      (border‑less) | Use `SdtAppearance.Hidden` instead of `Default`. | | **Read‑only
      field** | After insertion, set `sdt.LockContentControl = true`. | | **Pre‑populate
      with data** | Set `sdt.Text = "John Doe";` after creating '
  - name: What’s next?
    text: '- Explore other SDT types such as `RichText` or `ComboBox` for dropdowns.
      - Combine multiple content controls inside tables or repeat them using `RepeatingSection`.
      - Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` to read or modify
      control values programmatically.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Как вставить элемент управления простым текстом в документ Word с помощью C#
url: /ru/java/document-manipulation/how-to-insert-plain-text-content-control-in-a-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Вставка plain text content control в документ Word с C#

Если вам нужно **insert plain text content control** в файл Word, этот учебник покажет, как сделать это с помощью Aspose.Words for .NET. Независимо от того, создаёте ли вы сервис генерации документов или автоматизируете создание форм, нижеописанные шаги позволяют добавить переиспользуемый редактируемый регион, который конечные пользователи могут заполнять.

Вы узнаете, как создать `Document`, использовать `DocumentBuilder` для размещения plain‑text Structured Document Tag (SDT), задать удобочитаемый заголовок и присвоить уникальный идентификатор тега. Руководство также объясняет распространённые варианты — например, изменение внешнего вида или вложение контролов — чтобы вы могли адаптировать решение под любой проект.

## Необходимые условия

- .NET 6.0 или новее (код также работает с .NET Framework 4.6+)
- Действительная лицензия Aspose.Words for .NET (или бесплатный ключ оценки)
- Visual Studio 2022 или любой совместимый с C# IDE
- Базовое знакомство с синтаксисом C#

> **Pro tip:** Если вы используете бесплатную оценочную версию, помните, что выходной документ будет содержать водяной знак. Лицензированная версия удалит его автоматически.

## Как вставить plain text content control с помощью Aspose.Words

The core of the solution is a three‑step process:

1. **Создать `Document` и `DocumentBuilder`.**  
2. **Вставить plain‑text Structured Document Tag (SDT) с внешним видом по умолчанию.**  
3. **Назначить заголовок и идентификатор тега SDT.**  

Each step is explained below, with complete, runnable code.

### Шаг 1: Инициализация документа и builder'а

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document doc = new Document();

        // DocumentBuilder lets you insert content into the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` представляет весь файл Word, а `DocumentBuilder` предоставляет методы, такие как `InsertParagraph`, `InsertImage` и, что особенно важно для этого учебника, `InsertStructuredDocumentTag`. Их предварительная инициализация дает вам холст, на котором можно разместить **plain text content control**.

### Шаг 2: Вставка plain‑text content control (SDT)

```csharp
        // Insert a plain‑text Structured Document Tag (SDT) with the default appearance.
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText,          // The control type – plain text.
            SdtAppearance.Default);    // Visual style; Default shows a light gray shading.
```

`SdtType.PlainText` указывает Aspose.Words создать **plain text content control**, который ведёт себя как простой текстовый блок, редактируемый пользователями. `SdtAppearance.Default` отображает контроль с лёгким фоном, делая очевидным в документе, что область редактируемая.

> **Why use `SdtAppearance.Default`?**  
> Внешний вид по умолчанию является наиболее совместимым стилем во всех версиях Word. Если вам нужен вид без границы, позже можно переключить на `SdtAppearance.Hidden`.

### Шаг 3: Установка заголовка и идентификатора тега

```csharp
        // Give the SDT a friendly title that appears in the Content Controls pane.
        sdt.Title = "MyTag";

        // Assign a unique tag identifier; this is useful for programmatic access later.
        sdt.Tag = "TagId";

        // (Optional) Add placeholder text inside the control.
        sdt.PlaceholderName = "Enter your text here";

        // Save the document to verify the result.
        doc.Save("output.docx");
    }
}
```

- **Title** (`sdt.Title`) отображается в панели *Content Controls* Word, помогая конечным пользователям понять назначение поля.  
- **Tag** (`sdt.Tag`) — идентификатор, ориентированный на разработчика, который можно запросить позже через `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.  
- **PlaceholderName** предоставляет серый подсказочный текст, улучшая пользовательский опыт.

Полный фрагмент кода выше образует автономную программу, которую можно собрать и запустить. После выполнения `output.docx` будет содержать один plain‑text content control с заголовком *MyTag* и тегом *TagId*.

![Диаграмма, показывающая вставку plain text content control в документ Word](image.png){alt="вставка plain text content control"}

## Понимание StructuredDocumentTag (SDT) и его свойств

A **Structured Document Tag** (SDT) is the underlying object model for Word content controls. The most relevant properties for inserting a plain text control are:

| Свойство | Назначение | Типичные значения |
|----------|------------|-------------------|
| `SdtType` | Определяет тип контроля (plain text, rich text, picture и т.д.) | `PlainText`, `RichText`, `ComboBox`, `DatePicker` |
| `SdtAppearance` | Визуальный стиль контроля | `Default`, `Hidden`, `BoundingBox`, `Tags` |
| `Title` | Человекочитаемое имя, отображаемое в панели *Content Controls* | Any short string |
| `Tag` | Машиночитаемый идентификатор, используемый в коде | Alphanumeric string |
| `PlaceholderName` | Текст, отображаемый, когда контроль пуст | Custom hint text |

When you set `SdtType.PlainText`, Word restricts the content to plain characters, preventing rich formatting. This makes the control ideal for simple form fields such as *Name*, *Email*, or *Phone Number*.

### Возможные варианты

| Сценарий | Изменение кода |
|----------|----------------|
| **Отсутствие визуального затенения** (без границы) | Use `SdtAppearance.Hidden` instead of `Default`. |
| **Только для чтения** | After insertion, set `sdt.LockContentControl = true`. |
| **Предзаполнение данными** | Set `sdt.Text = "John Doe";` after creating the tag. |
| **Несколько контролов в таблице** | Insert the SDT inside a table cell using `builder.InsertCell();` before the `InsertStructuredDocumentTag` call. |

## Распространённые ошибки и как их избежать

1. **Забыть задать заголовок** – Word всё равно создаст контроль, но пользователи не увидят значимое описание в панели *Content Controls*. Всегда назначайте `sdt.Title`.  
2. **Использовать неверный `SdtType`** – если вам нужен plain text, но вы случайно выбрали `RichText`, контроль позволит форматирование, что может нарушить последующую обработку. Дважды проверьте значение enum.  
3. **Сохранение в папку только для чтения** – вызов `doc.Save` бросит `UnauthorizedAccessException`. Убедитесь, что целевой каталог доступен для записи, или используйте `Path.GetTempPath()` для тестирования.  
4. **Лицензия не применена** – без действительной лицензии выходной документ будет содержать водяной знак оценки. Примените лицензию в начале программы:

```csharp
License lic = new License();
lic.SetLicense("Aspose.Words.lic");
```

## Полный, исполняемый пример

Below is the entire program, ready to copy‑paste into a new console project.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace InsertPlainTextContentControl
{
    class Program
    {
        static void Main()
        {
            // Apply license (optional for evaluation)
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1️⃣ Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text Structured Document Tag (SDT) with default appearance
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,          // Plain text control
                SdtAppearance.Default);    // Light gray shading

            // 3️⃣ Assign a title and a tag identifier to the SDT
            sdt.Title = "MyTag";          // Human‑readable title
            sdt.Tag = "TagId";            // Unique machine identifier
            sdt.PlaceholderName = "Enter your text here";

            // (Optional) Add some introductory text before the control
            builder.MoveToDocumentStart();
            builder.Writeln("Please fill in the following field:");

            // 4️⃣ Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Expected output:** Opening `output.docx` in Microsoft Word shows a line of text *“Please fill in the following field:”* followed by a light‑gray boxed region labeled *MyTag*. The placeholder *Enter your text here* appears in light gray until the user types.

## Заключение

You now know how to **insert plain text content control** into a Word document using Aspose.Words for .NET. The tutorial covered initializing a `Document`, inserting a `StructuredDocumentTag` of type `PlainText`, and customizing its title, tag, and placeholder. By understanding the `SdtAppearance` options and common pitfalls, you can confidently build forms, templates, and automated reports that rely on editable content controls.

### Что дальше?

- Исследуйте другие типы SDT, такие как `RichText` или `ComboBox` для выпадающих списков.  
- Комбинируйте несколько content controls внутри таблиц или повторяйте их с помощью `RepeatingSection`.  
- Используйте `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`, чтобы программно считывать или изменять значения контролов.

Feel free to experiment with the variations shown earlier, and integrate the pattern into your larger document‑generation pipelines. Happy coding!

## Что вам стоит изучить дальше?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step‑by‑step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Как создать content control в C# с Aspose.Words](/words/english/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/)
- [Создать новый документ Word и вставить content control в C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [Добавить контент с помощью Document Builder в Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}