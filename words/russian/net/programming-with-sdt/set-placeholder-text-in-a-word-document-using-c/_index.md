---
category: general
date: 2026-10-20
description: Установите текст‑заполнитель в документ Word с помощью C#. Узнайте, как
  быстро добавить элемент управления и задать заполнитель с помощью Aspose.Words для .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- how to add control
- how to set placeholder
- generate word c#
language: ru
lastmod: 2026-10-20
og_description: Установите текст‑заполнитель в документ Word с помощью C#. Этот учебник
  покажет, как добавить элемент управления, установить заполнитель и программно генерировать
  файлы Word.
og_image_alt: Screenshot of a Word document showing placeholder text created with
  C# code
og_title: Установите текст‑заполнитель в документ Word с помощью C# – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Set placeholder text in a Word document using C#. Learn how to add
    control and set placeholder quickly with Aspose.Words for .NET.
  headline: Set placeholder text in a Word document using C#
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, and .NET
      6+. The same code runs unchanged.
    question: Does this work with .NET Core?
  - answer: Use `sdt.SetText("Default value")` after creating the SDT. The placeholder
      disappears once a value is set.
    question: Can I set a default value in addition to the placeholder?
  - answer: 'Load the document, locate the SDT by its `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag,
      true)`) and read `sdt.GetText()`. ## Conclusion You now know how to **set placeholder
      text** in a Word document using C#. By creating a plain‑text `StructuredDocumentTag`,
      assigning a title and place'
    question: What if I need to retrieve the entered value later?
  type: FAQPage
tags:
- C#
- Aspose.Words
- Word automation
- Content control
title: Установить текст‑заполнитель в документ Word с помощью C#
url: /ru/net/programming-with-sdt/set-placeholder-text-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Установить текст‑заполнитель в документ Word с помощью C#

Если вам нужно **установить текст‑заполнитель** в файл Microsoft Word при его генерации с помощью C#, это руководство покажет, как именно. Вы увидите краткое, сквозное решение, которое добавляет элемент управления содержимым, задаёт его заполнитель и сохраняет документ — всё с помощью Aspose.Words for .NET.

Многие разработчики задаются вопросом **как добавить элемент управления** в документ Word или **как задать заполнитель** без ручного открытия Word. Это руководство отвечает на эти вопросы и также демонстрирует чистый способ **генерировать Word C#** файлы, готовые к вводу пользователем.

## Что вы достигнете

* Создать пустой документ Word программно.  
* Вставить простейший Structured Document Tag (SDT) в виде обычного текста, который является техническим названием элемента управления содержимым.  
* Назначить SDT осмысленное название и текст‑заполнитель.  
* Сохранить полученный файл `.docx` на диск.  

Дополнительные инструменты не требуются, кроме библиотеки Aspose.Words и среды разработки .NET 6 (или новее).

## Предварительные требования

* .NET 6 SDK или новее, установленный.  
* Visual Studio 2022 (или любая IDE, поддерживающая .NET).  
* NuGet‑пакет Aspose.Words for .NET (`Install-Package Aspose.Words`).  

> **Совет:** Используйте бесплатную оценочную версию Aspose.Words, если вы просто тестируете; она добавляет водяной знак, но в остальном работает так же, как лицензированная версия.

## Шаг 1: Настройте проект и импортируйте пространства имён

Создайте новый консольный проект и добавьте необходимые директивы `using`. Они делают доступными основные классы Aspose.Words и пространство имён разметки.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // The complete solution starts here.
        }
    }
}
```

*Почему этот шаг важен:* Импорт `Aspose.Words.Markup` даёт доступ к `StructuredDocumentTag`, `SdtType` и `MarkupLevel` — объектам, необходимым для **добавления элемента управления** и **задания заполнителя**.

## Шаг 2: Создайте пустой документ и DocumentBuilder

`Document` представляет весь файл Word, а `DocumentBuilder` предоставляет удобный курсор для вставки элементов.

```csharp
// Step 2: Initialize a new empty document.
Document doc = new Document();

// DocumentBuilder starts at the beginning of the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Почему этот шаг важен:* Начало с чистого документа гарантирует, что заданный вами заполнитель появится точно там, где вы хотите, без вмешательства существующего содержимого.

## Шаг 3: Создайте элемент управления содержимым (Structured Document Tag)

Здесь мы создаём простейший SDT в виде обычного текста, задаём ему название и устанавливаем текст‑заполнитель, который пользователь увидит, когда элемент управления будет пустым.

```csharp
// Step 3: Build a plain‑text Structured Document Tag (SDT).
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,                     // Parent document
    SdtType.PlainText,       // Control type – plain text box
    MarkupLevel.Inline);     // Inline placement (behaves like a word)

sdt.Title = "CustomerName";                 // Logical name for the control
sdt.PlaceholderName = "Enter name here";    // Text shown when empty
```

*Почему этот шаг важен:* Свойство `Title` позволяет позже ссылаться на элемент управления (например, для привязки данных). `PlaceholderName` — это именно тот **текст‑заполнитель**, который вы хотите отобразить, направляя конечного пользователя.

## Шаг 4: Вставьте элемент управления в текущую позицию курсора

С помощью `DocumentBuilder` вставьте SDT в документ в том месте, где в данный момент находится курсор builder'а.

```csharp
// Step 4: Insert the SDT into the document.
builder.InsertNode(sdt);
```

*Почему этот шаг важен:* Вставка узла присоединяет элемент управления к DOM документа. Если нужно добавить несколько заполнителей, можно переместить курсор builder'а и повторить этот шаг.

## Шаг 5: Сохраните документ

Наконец, запишите документ на диск. Замените `YOUR_DIRECTORY` реальным путём на вашем компьютере.

```csharp
// Step 5: Save the .docx file.
string outputPath = @"C:\Temp\SDT.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Когда вы откроете `SDT.docx` в Microsoft Word, вы увидите серым оттенком встроенный текстовый блок с надписью **Enter name here**. Щелчок внутри блока удалит заполнитель, позволяя пользователю ввести имя клиента.

### Ожидаемый результат

| Путь к файлу | Предпросмотр содержимого |
|--------------|--------------------------|
| `C:\Temp\SDT.docx` | Встроенный заполнитель **Enter name here** внутри простого текстового элемента управления с названием *CustomerName*. |

## Пограничные случаи и варианты

| Ситуация | Рекомендуемая корректировка |
|----------|-----------------------------|
| **Несколько заполнителей** | Создайте дополнительные объекты `StructuredDocumentTag` с разными значениями `Title` и `PlaceholderName`, затем вставляйте каждый там, где требуется. |
| **Заполнитель с форматированным текстом** | Используйте `SdtType.RichText` вместо `PlainText`, чтобы разрешить форматирование внутри заполнителя. |
| **Элемент управления уровня блока** | Измените `MarkupLevel.Inline` на `MarkupLevel.Block`, чтобы элемент управления вел себя как полноценный абзац. |
| **Заполнитель не виден** | Убедитесь, что настройки просмотра документа в Word не скрывают элементы управления (`File → Options → Advanced → Show content controls`). |
| **Сохранение в поток** | Вызовите `doc.Save(stream, SaveFormat.Docx)`, если нужно отправить файл по HTTP вместо записи на диск. |

## Полный, исполняемый пример

Ниже представлен полный код программы, который вы можете скопировать, вставить и запустить. Он включает все шаги выше в едином методе `Main`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Position a builder at the start of the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Define a plain‑text content control (SDT) with placeholder text.
            StructuredDocumentTag sdt = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Inline);

            sdt.Title = "CustomerName";                 // Logical identifier
            sdt.PlaceholderName = "Enter name here";    // The placeholder you see in Word

            // 4️⃣ Insert the SDT into the document.
            builder.InsertNode(sdt);

            // 5️⃣ Save the document to disk.
            string outputPath = @"C:\Temp\SDT.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document successfully saved to {outputPath}");
        }
    }
}
```

Запустите программу, откройте сгенерированный файл, и вы увидите текст‑заполнитель, готовый к вводу пользователем.

## Часто задаваемые вопросы

**В: Работает ли это с .NET Core?**  
A: Да. Aspose.Words for .NET совместим с .NET Core, .NET 5 и .NET 6+. Тот же код работает без изменений.

**В: Можно ли задать значение по умолчанию помимо заполнителя?**  
A: Используйте `sdt.SetText("Default value")` после создания SDT. Заполнитель исчезает, как только задаётся значение.

**В: Что делать, если нужно позже получить введённое значение?**  
A: Загрузите документ, найдите SDT по его `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`) и прочитайте `sdt.GetText()`.

## Заключение

Теперь вы знаете, как **установить текст‑заполнитель** в документ Word с помощью C#. Создавая простейший `StructuredDocumentTag`, задавая название и заполнитель, вставляя его с помощью `DocumentBuilder` и сохраняя файл, вы можете **добавлять элемент управления** и **генерировать Word C#** файлы программно.

Отсюда вы можете изучить:

* Добавление элементов управления с форматированным текстом или выпадающим списком (`SdtType.RichText`, `SdtType.DropDownList`).  
* Заполнение нескольких заполнителей из базы данных.  
* Преобразование сгенерированного `.docx` в PDF с помощью Aspose.Words.  

Экспериментируйте с различными типами элементов управления и стилями заполнителей, чтобы они соответствовали потребностям вашего приложения. Приятного кодинга!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, которые опираются на техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Установить текст‑заполнитель в Aspose.Words – Полное руководство C#](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Создать документ Word программно – добавить элемент управления содержимым и заполнитель](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Как добавить элемент управления содержимым и создать документ Word с Aspose – Полное руководство](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}