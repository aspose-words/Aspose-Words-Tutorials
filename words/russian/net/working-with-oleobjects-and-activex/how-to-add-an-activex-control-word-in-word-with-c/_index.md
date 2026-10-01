---
category: general
date: 2026-09-30
description: Добавьте элемент управления ActiveX в документ Word с помощью C#. Узнайте,
  как вставить кнопку ActiveX, добавить кнопку управления и сделать её кликабельной.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: ru
lastmod: 2026-09-30
og_description: Добавьте элемент управления ActiveX в документ Word с помощью C#.
  Следуйте этому полному руководству, чтобы вставить кнопку ActiveX, добавить кнопку
  команды и сделать её кликабельной.
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: Добавьте элемент управления ActiveX в документы Word – пошаговое руководство
  на C#
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: Как добавить элемент управления ActiveX в Word с помощью C#
url: /ru/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как добавить ActiveX control word в Word с C#

Если вам нужно встроить **ActiveX control word** в файл Microsoft Word, это руководство покажет, как это сделать. Вы увидите полностью готовый, исполняемый пример, который вставляет кликабельную кнопку, сохраняет документ и работает с последней версией Aspose.Words for .NET.

Добавление ActiveX control word позволяет создавать интерактивные формы, пользовательские диалоговые окна или простые элементы UI, которые ведут себя как родные элементы Word. Независимо от того, создаёте ли вы шаблон контракта, требующий взаимодействия пользователя, или отчёт, которому нужна кнопка «Run», нижеописанные шаги охватывают всё необходимое.

## Требования

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6.0 SDK или новее (код также работает с .NET Framework 4.8)
* Visual Studio 2022 (или любая IDE, поддерживающая C#)
* Aspose.Words for .NET установлен (`dotnet add package Aspose.Words`)
* Базовое понимание C# и структуры документов Word

> **Pro tip:** Метод `InsertForms2OleControl` работает только с устаревшими контролами “Forms 2.0”, которые являются ActiveX‑контроллами, используемыми Word для полей формы. Если вы нацеливаетесь на более новые версии Office, контрол всё равно корректно отображается в настольном клиенте.

## Шаг 1: Создайте проект и импортируйте пространства имён

Создайте новый консольный проект и добавьте необходимые `using`‑директивы. Это позволит компилятору найти классы `Document`, `DocumentBuilder` и `OleControlType`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Пространство имён `Aspose.Words` предоставляет высокоуровневые API для обработки Word, а `Aspose.Words.Drawing` содержит перечисление `OleControlType`, необходимое для указания типа ActiveX‑контролла.

## Шаг 2: Загрузите исходный документ Word

Нужно начать с файла Word, который вы собираетесь изменить. Следующий код загружает `input.docx` из указанной папки.

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

Если файл не существует, Aspose.Words выбрасывает `FileNotFoundException`. Оберните вызов в `try/catch`, если требуется более гибкая обработка ошибок.

## Шаг 3: Создайте DocumentBuilder для редактирования документа

`DocumentBuilder` — основной инструмент для вставки текста, изображений и контролов. Он поддерживает курсор, указывающий место, где будет размещён следующий элемент.

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

По умолчанию курсор билдера находится в начале первой секции. Вы можете переместить его с помощью методов вроде `MoveToDocumentEnd()` или `MoveToParagraph(index)`, если хотите разместить кнопку в другом месте.

## Шаг 4: Вставьте ActiveX CommandButton

Теперь к главному: вставка **ActiveX control word**, который выглядит как кликабельная кнопка. Метод `InsertForms2OleControl` принимает два аргумента — тип контрола и подпись (или имя) для него.

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **Почему `OleControlType.CommandButton`?**  
  Он указывает Word создать классическую кнопку Forms 2.0, которая отображает подпись и может быть привязана к макросу или VBA‑скрипту позже.

* **Что делает подпись?**  
  Строка `"ClickMe"` становится видимым текстом кнопки. Вы можете изменить её на любой другой текст, соответствующий вашему UI.

### Вставка кнопки в конкретное место

Если нужна кнопка после определённого абзаца, сначала переместите билдер:

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## Шаг 5: Сохраните изменённый документ

После вставки контрола сохраните изменения в новый файл (или перезапишите оригинал).

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Когда откроете `output.docx` в настольной версии Word, вы увидите кнопку с надписью **ClickMe** (или **Submit**, в зависимости от выбранной подписи). По умолчанию нажатие кнопки в режиме разработки ничего не делает; позже вы можете привязать к ней макрос через вкладку «Developer».

## Полный, исполняемый пример

Ниже приведена самостоятельная программа, демонстрирующая весь процесс. Скопируйте её в `Program.cs` нового консольного приложения и запустите.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### Ожидаемый результат

* Консоль выводит сообщение об успешном завершении с указанием пути к результату.
* Открытие `output.docx` показывает кнопку **ClickMe** в том месте, где билдер её вставил.
* Кнопку можно выбрать, изменить её размер или назначить макрос через **Developer → Design Mode** в Word.

## Часто задаваемые вопросы и обработка граничных случаев

| Question | Answer |
|----------|--------|
| **How to insert an ActiveX button in the header/footer?** | Move the builder to the header/footer with `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` before calling `InsertForms2OleControl`. |
| **What if I need a checkbox instead of a button?** | Use `OleControlType.CheckBox` and provide a caption like `"Agree"`. |
| **Will the button work in Word Online?** | No. Word Online does not support legacy Forms 2.0 ActiveX controls. The button only renders in the desktop client. |
| **Can I set the button’s size programmatically?** | After insertion, retrieve the `Shape` object via `builder.CurrentParagraph.Runs[0].GetShape()` and adjust `Width`/`Height`. |
| **Is there a way to assign a macro from code?** | Aspose.Words does not expose macro editing. You must open the document in Word and attach a macro manually or use the Office Interop API. |

## Советы для продакшн‑использования

* **Avoid hard‑coded paths** – use `Path.Combine` and configuration files.
* **Dispose of `Document`** – wrap it in a `using` statement if you work with large files to free memory promptly.
* **Validate the output** – programmatically check that the document contains a shape of type `OleControl` by iterating `doc.GetChildNodes(NodeType.Shape, true)`.
* **Security note** – ActiveX controls can run code on the client machine. Only distribute documents to trusted users and consider digital signatures.

## Заключение

Теперь вы знаете, как добавить **ActiveX control word** в документ Word с помощью C#. Загрузив документ, создав `DocumentBuilder`, вставив кнопку командой `InsertForms2OleControl` и сохранив файл, вы можете автоматизировать создание интерактивных форм Word. Экспериментируйте с другими значениями `OleControlType`, размещайте контролы в заголовках или таблицах и комбинируйте их с макросами для более богатого пользовательского опыта.

---

*Next steps*: explore **how to insert ActiveX** controls of other types, learn **how to add command button** event handlers via VBA, and read about **insert ActiveX button** best practices for cross‑platform compatibility.

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом гайде. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Embedding OLE Objects and ActiveX Controls in Word Documents](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}