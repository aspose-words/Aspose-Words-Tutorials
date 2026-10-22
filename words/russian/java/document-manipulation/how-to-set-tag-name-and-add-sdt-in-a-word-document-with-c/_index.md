---
category: general
date: 2026-09-08
description: Установите имя тега и создайте элемент управления содержимым (SDT) в
  документе Word с помощью C#. Узнайте, как добавить SDT, записать текст в тег и изменить
  документ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set tag name
- how to add sdt
- modify word document
- create content control
- write text to tag
language: ru
lastmod: 2026-09-08
og_description: Установите имя тега и создайте элемент управления содержимым (SDT)
  в документе Word с помощью C#. Следуйте этому пошаговому руководству, чтобы добавить
  SDT, записать текст в тег и изменить документ.
og_image_alt: Screenshot showing a Word document with a StructuredDocumentTag whose
  tag name is set
og_title: Задайте имя тега и добавьте SDT в документ Word – руководство по C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Set tag name and create a content control (SDT) in a Word document
    using C#. Learn how to add SDT, write text to tag, and modify the document.
  headline: How to set tag name and add SDT in a Word document with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Как установить имя тега и добавить SDT в документ Word с помощью C#
url: /ru/java/document-manipulation/how-to-set-tag-name-and-add-sdt-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как задать имя тега и добавить SDT в документ Word с помощью C#

Если вам нужно **задать имя тега** для StructuredDocumentTag (SDT) при работе с файлами Word, это руководство покажет, как это сделать. Вы увидите полностью готовый, исполняемый пример, который **создаёт элемент управления содержимым**, записывает текст в тег и **модифицирует документ Word** от начала до конца.

Разработчики часто спрашивают: *«как добавить sdt* в существующий .docx и затем *записать текст в тег*?» – ответ заключается в использовании API Aspose.Words for .NET. К концу этого урока вы сможете открыть файл Word, вставить SDT простого текста, задать его имя тега, заполнить его содержимым и сохранить изменения без оставления висячих ресурсов.

## Требования

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6.0 или более поздняя версия.
* Действительная лицензия Aspose.Words for .NET (или вы можете работать с оценочной версией).
* Visual Studio 2022 (или любая IDE, поддерживающая C#).
* Входной документ Word (`input.docx`), размещённый в папке, к которой вы можете обратиться из кода.

## Шаг 1: Настройка проекта и импорт пространств имён

Создайте новый проект Console App и добавьте пакет Aspose.Words через NuGet:

```bash
dotnet new console -n WordSdtDemo
cd WordSdtDemo
dotnet add package Aspose.Words
```

Затем добавьте необходимые директивы `using` в начало файла `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;
```

Эти пространства имён предоставляют доступ к `Document`, `DocumentBuilder` и классу `StructuredDocumentTag`, которые необходимы для **модификации документа Word**.

## Шаг 2: Загрузка существующего документа Word

Первой операцией является загрузка файла, который вы хотите отредактировать. Этот шаг обязателен для любого сценария, где вы **модифицируете содержимое документа Word**.

```csharp
// Load an existing Word document from disk
string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
Console.WriteLine($"Loaded document: {inputPath}");
```

> **Почему мы загружаем документ сначала** – Объект `Document` представляет весь пакет .docx в памяти. Только после загрузки вы можете безопасно вставлять новые узлы, такие как SDT.

## Шаг 3: Вставка StructuredDocumentTag (SDT) и задание имени тега

Теперь мы отвечаем на основной вопрос: **как добавить sdt** и **задать имя тега**. Мы используем `DocumentBuilder.InsertStructuredDocumentTag` с `SdtType.PlainText`. Второй аргумент – это имя тега, которое позже можно будет использовать программно или через пользовательский интерфейс Word.

```csharp
// Create a DocumentBuilder attached to the loaded document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag (content control) at the cursor position
// The second parameter ("MyTag") is the tag name we are setting.
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Confirm that the tag name has been set
Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");
```

> **Объяснение** – `InsertStructuredDocumentTag` возвращает экземпляр `StructuredDocumentTag`. Передавая `"MyTag"`, мы **задаём имя тега** сразу при создании. Если понадобится изменить его позже, можно присвоить новое значение свойству `sdt.Tag`.

## Шаг 4: Запись текста в только что созданный тег

После создания SDT обычно требуется **записать текст в тег**, чтобы конечные пользователи видели заполнитель или значение по умолчанию. Метод `SetText` делает именно это.

```csharp
// Populate the SDT with sample content
sdt.SetText("Sample content");

// Optionally, you can also set the placeholder text that appears when the tag is empty
sdt.PlaceholderName = "Enter your text here";
Console.WriteLine("Text written to the SDT.");
```

> **Почему используется SetText** – Прямое присваивание свойству `Text` заменило бы всю иерархию узлов. `SetText` безопасно обновляет внутренний текст элемента управления содержимым, сохраняя его структуру.

## Шаг 5: Сохранение изменённого документа

Наконец, сохраняем изменения в новый файл. Это завершает рабочий процесс **модификации документа Word**.

```csharp
// Define the output path
string outputPath = @"YOUR_DIRECTORY\output.docx";

// Save the document with the inserted content control
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Когда вы откроете `output.docx` в Microsoft Word, вы увидите элемент управления простым текстом с меткой **MyTag**, содержащий текст «Sample content». Элемент можно редактировать вручную, а имя тега остаётся доступным через инструменты разработчика Word.

## Полный исходный код

Ниже приведена полная, автономная программа. Скопируйте её в `Program.cs` и запустите; дополнительные фрагменты кода не требуются.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the existing Word document
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);
            Console.WriteLine($"Loaded document: {inputPath}");

            // 2️⃣ Create a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and set its tag name
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText, "MyTag");
            Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");

            // 4️⃣ Write text to the tag (and optionally set a placeholder)
            sdt.SetText("Sample content");
            sdt.PlaceholderName = "Enter your text here";
            Console.WriteLine("Text written to the SDT.");

            // 5️⃣ Save the modified document
            string outputPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Ожидаемый вывод в консоли

```
Loaded document: YOUR_DIRECTORY\input.docx
Inserted SDT with tag name: MyTag
Text written to the SDT.
Document saved to: YOUR_DIRECTORY\output.docx
```

### Как выглядит получившийся файл Word

![Word document showing a content control named MyTag with the text “Sample content”](/images/word-sdt-example.png){: .img-fluid alt="Пример установки имени тега в документе Word"}

*Скриншот демонстрирует SDT с **именем тега** *MyTag* и видимым встроенным текстом.*

## Распространённые варианты и граничные случаи

| Ситуация | Как решить |
|-----------|------------------|
| **Создать rich‑text SDT** | Использовать `SdtType.RichText` вместо `PlainText`. |
| **Изменить имя тега после вставки** | `sdt.Tag = "NewTag";` – имя тега можно переопределять в любой момент. |
| **Добавить SDT в определённый абзац** | Переместите курсор билдера (`builder.MoveToParagraph(index)`) перед вызовом `InsertStructuredDocumentTag`. |
| **Несколько SDT в одном документе** | Повторите шаги 3‑4 для каждого элемента; каждый может иметь уникальное имя тега. |
| **Работа с защищёнными документами** | Убедитесь, что документ не защищён (`doc.Unprotect()`) перед вставкой SDT. |

## Профессиональные советы для надёжной автоматизации Word

* **Лицензировать заранее** – В начале `Main` вызовите `Aspose.Words.License license = new Aspose.Words.License(); license.SetLicense("Aspose.Words.lic");`, чтобы избавиться от водяных знаков оценки.
* **Освобождать ресурсы** – Оберните `Document` в блок `using`, если вы целитесь в .NET Framework, чтобы гарантировать освобождение файловых дескрипторов.
* **Проверять наличие тега** – При последующем чтении документа используйте `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`, чтобы находить теги по свойству `Tag`.
* **Производительность** – Для больших документов загружайте только необходимые части, используя `LoadOptions` с `LoadFormat.Docx` и `LoadFormat.Auto`.  

## Заключение

Теперь вы знаете, как **задать имя тега**, **создать элемент управления содержимым**, **записать текст в тег** и **модифицировать документ Word** с помощью C#. Полный пример демонстрирует стандартный шаблон для **добавления sdt** и безопасного сохранения изменений.

From here


## Что изучать дальше?


Следующие уроки охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Word Document - How to Remove Content](/words/english/net/remove-content/)
- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}