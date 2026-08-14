---
category: general
date: 2026-08-14
description: Как быстро добавить SDT с помощью Aspose.Words. Узнайте, как создать
  заполнитель Word и вставить элемент управления простым текстом в файл .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add sdt
- create word placeholder
- insert plain text control
- Aspose.Words SDT
- C# Word automation
language: ru
lastmod: 2026-08-14
og_description: Как добавить SDT в C# с помощью Aspose.Words. Следуйте этому руководству,
  чтобы создать заполнитель Word и вставить элемент управления простым текстом для
  динамических документов.
og_image_alt: Screenshot of a Word document showing a plain‑text Structured Document
  Tag placeholder
og_title: Как добавить SDT в C# — пошаговое руководство по заполнителям Word
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add SDT quickly with Aspose.Words. Learn to create word placeholder
    and insert plain text control in a .docx file.
  headline: How to add SDT in C# – complete guide for Word placeholders
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- SDT
- Document Automation
title: Как добавить SDT в C# – полное руководство по заполнителям Word
url: /ru/java/using-document-elements/how-to-add-sdt-in-c-complete-guide-for-word-placeholders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как добавить SDT в C# – полное руководство по заполнителям Word

Если вам нужно **how to add sdt** в файле Word, это руководство покажет точные шаги с использованием Aspose.Words for .NET. К концу руководства вы сможете **create word placeholder**‑теги, позволяющие конечным пользователям вводить текст напрямую в документ, и вы поймёте, как надёжно **insert plain text control**.

Работа со Structured Document Tags (SDT) устраняет необходимость в ручных полях формы и предоставляет чистый программный способ создания динамических контрактов, отчётов или писем. Пример ниже охватывает всё — от настройки проекта до сохранения окончательного .docx‑файла, так что вы можете скопировать‑вставить код в своё решение, не пропустив ни одной зависимости.

## Требования

Прежде чем начать, убедитесь, что у вас есть:

- .NET 6.0 или новее (код также работает с .NET Framework 4.6+)
- Visual Studio 2022 или любой другой предпочитаемый IDE для C#
- Лицензия Aspose.Words for .NET (временная бесплатная лицензия подходит для тестирования)
- Базовое знакомство с синтаксисом C# и концепцией SDT

> **Совет:** Если планируете распространять сгенерированные документы, внедрите файл лицензии, чтобы избавиться от водяного знака оценки.

## Шаг 1: Создайте проект и импортируйте Aspose.Words

Создайте новое консольное приложение и добавьте пакет Aspose.Words через NuGet:

```bash
dotnet new console -n SdtDemo
cd SdtDemo
dotnet add package Aspose.Words
```

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

Эти директивы `using` дают доступ к классам `Document`, `DocumentBuilder` и `StructuredDocumentTag`, необходимым для операций **insert plain text control**.

## Шаг 2: Инициализируйте документ и builder

Первый блок кода создаёт пустой документ Word и `DocumentBuilder`, который позволяет писать содержимое в него.

```csharp
// Step 2: Create a new document and a builder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` работает как курсор; каждый последующий вызов добавляет контент в текущую позицию. Инициализация документа — фундамент для любого сценария **how to add sdt**, потому что SDT должен принадлежать живому экземпляру `Document`.

## Шаг 3: Вставьте Structured Document Tag (SDT) простого текста

Теперь мы **insert plain text control**, который выступает как заполнитель, где пользователь может ввести имя, дату или любое другое значение.

```csharp
// Step 3: Insert a plain‑text Structured Document Tag (SDT)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);
```

- `StructuredDocumentTagType.PlainText` указывает Aspose.Words создать простое текстовое поле.
- `SdtAppearanceTags.Default` задаёт тегу стандартный визуальный стиль Word (затенённый блок при открытии документа в Word).

## Шаг 4: Настройте SDT с заголовком и текстом‑заполнителем

Хорошо названный SDT делает документ самодокументируемым для конечных пользователей. Здесь мы **create word placeholder**‑метаданные и задаём подсказку, отображаемую внутри поля.

```csharp
// Step 4: Give the SDT a meaningful title and placeholder text
plainTextTag.Title = "CustomerName";
plainTextTag.PlaceholderName = "Enter name here";
```

- `Title` — внутренний идентификатор, который можно использовать позже при извлечении или обновлении значения программно.
- `PlaceholderName` — серый подсказочный текст в Word, подсказывающий пользователю, что вводить.

## Шаг 5: Добавьте окружающий контент

Документ редко состоит из одного SDT. Обычно нужны обычные абзацы до и после заполнителя. Используйте метод `WriteLine` builder‑а для добавления статического текста.

```csharp
// Step 5: Add regular content before and after the SDT
builder.Writeln("Dear ");
builder.InsertNode(plainTextTag);   // Re‑insert the tag at the current cursor position
builder.Writeln(",");
builder.Writeln("After the SDT");
```

Вызов `InsertNode` помещает ранее созданный SDT точно туда, где он нужен, сохраняя окружающий поток текста.

## Шаг 6: Сохраните документ в файл .docx

Наконец, сохраняем документ на диск. Путь может быть абсолютным или относительным к папке проекта.

```csharp
// Step 6: Save the document to a file
string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Открытие `SDT.docx` в Microsoft Word показывает серый заполнитель с надписью **Enter name here**. Пользователи могут кликнуть по полю, ввести значение, и документ сохранит это значение при следующем сохранении.

## Полный, исполняемый пример

Собрав все части вместе, получаем автономную программу, которую можно запустить сразу:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text SDT
        StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);

        // Configure the SDT
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // Add surrounding content
        builder.Writeln("Dear ");
        builder.InsertNode(plainTextTag);
        builder.Writeln(",");
        builder.Writeln("After the SDT");

        // Save the file
        string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Ожидаемый вывод** при запуске программы:

```
Document saved to C:\YourProject\bin\Debug\net6.0\SDT.docx
```

Открытие сгенерированного `SDT.docx` показывает:

```
Dear [Enter name here],
After the SDT
```

Текст в квадратных скобках — это заполнитель **insert plain text control**, который пользователь может заменить.

## Распространённые варианты и граничные случаи

| Ситуация | Как адаптировать код |
|-----------|-----------------------|
| **Несколько заполнителей** | Вызывайте `InsertStructuredDocumentTag` многократно, задавая каждому тегу уникальный `Title`. |
| **Rich‑text SDT** | Используйте `StructuredDocumentTagType.RichText` вместо `PlainText`. |
| **Блокировать заполнитель** | Установите `plainTextTag.LockContentControl = true;`, чтобы пользователи не могли удалить поле. |
| **Предзаполнить значением** | Присвойте `plainTextTag.Text = "John Doe";` перед сохранением. |
| **Условное отображение** | Используйте `plainTextTag.SdtType = StructuredDocumentTagType.CheckBox;` для чек‑бокса. |

Эти варианты позволяют **create word placeholder**‑структуры, подходящие почти для любого сценария, похожего на форму.

## Советы по устранению неполадок

- **Заполнитель не виден** — Убедитесь, что открываете файл в Microsoft Word (или совместимом просмотрщике). Некоторые лёгкие редакторы скрывают SDT.
- **Предупреждение о лицензии** — Если виден водяной знак оценки, проверьте, что файл лицензии загружен корректно (`License license = new License(); license.SetLicense("Aspose.Words.lic");`).
- **Неправильная позиция курсора** — После вставки SDT курсор builder‑а остаётся *после* тега. Если нужно добавить текст *внутри* тега, используйте `builder.MoveTo(plainTextTag);` перед записью.

## Заключение

Теперь вы знаете, **how to add sdt** в документ Word с помощью Aspose.Words for .NET, как **create word placeholder**‑теги и как **insert plain text control**, который пользователи могут редактировать непосредственно в Word. Полный пример демонстрирует инициализацию, вставку тега, настройку, добавление окружающего контента и сохранение — всё в одной исполняемой программе.

Далее изучайте связанные темы, такие как **insert rich text control**, **populate SDTs from a database** или **convert the final document to PDF**. Все они опираются на те же фундаментальные принципы, изложенные здесь, так что вы сможете уверенно расширять свой конвейер автоматизации.

Удачной разработки, экспериментируйте с различными типами SDT, чтобы удовлетворить потребности автоматизации ваших документов!


## Что изучать дальше?


Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Create Editable Ranges in Read-Only Documents Using Aspose.Words for Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)
- [Add Bookmarks Word with Aspose.Words for Java – Insert, Update, Delete](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}