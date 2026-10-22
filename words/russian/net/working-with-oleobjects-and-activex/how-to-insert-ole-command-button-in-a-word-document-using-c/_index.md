---
category: general
date: 2026-10-07
description: Узнайте, как вставить OLE‑кнопку команды в документ Word с помощью Aspose.Words
  C#. Пошаговое руководство, охватывающее DocumentBuilder, свойства и сохранение файла.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: ru
lastmod: 2026-10-07
og_description: Вставьте OLE‑кнопку команду в документ Word с помощью C#. Следуйте
  этому краткому руководству, чтобы добавить, настроить и сохранить функциональную
  кнопку CommandButton с помощью Aspose.Words.
og_image_alt: Insert OLE command button example in Word document
og_title: Вставка OLE‑кнопки команды в Word с помощью C# — полное руководство Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: Как вставить OLE‑кнопку команды в документ Word с помощью C#
url: /ru/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как вставить OLE command button в документ Word с помощью C#

Если вам нужно **вставить OLE command button** в файл Word программно, это руководство покажет, как сделать это с помощью Aspose.Words for .NET. Независимо от того, создаёте ли вы отчёт с заполненными формами или автоматизируете шаблон, требующий взаимодействия с пользователем, нижеуказанные шаги предоставят полное, готовое к выполнению решение.

Вы узнаете, как создать пустой документ, использовать `DocumentBuilder` для размещения `Forms2OleControl`, задать подпись и имя кнопки и, наконец, сохранить файл в формате `.docx`. Ни какие внешние инструменты не требуются, кроме библиотеки Aspose.Words.

## Требования

Перед тем как начать, убедитесь, что у вас есть:

* .NET 6.0 или новее (код также работает с .NET Framework 4.7+)
* Действительная лицензия Aspose.Words for .NET или бесплатный оценочный ключ
* Visual Studio 2022 (или любой другой предпочитаемый IDE для C#)
* Базовые знания синтаксиса C# и концепций OLE в Word

> **Pro tip:** Если вы используете бесплатную оценочную версию, сгенерированный документ будет содержать небольшую водяную метку. Лицензированная версия удалит её автоматически.

## Шаг 1: Установите Aspose.Words

Добавьте пакет Aspose.Words в ваш проект через NuGet:

```bash
dotnet add package Aspose.Words
```

Пакет включает пространства имён `Aspose.Words.Drawing` и `Aspose.Words.Drawing.Ole`, необходимые для работы с OLE‑элементами.

## Шаг 2: Вставьте OLE command button с помощью DocumentBuilder

Основой учебника является метод `InsertForms2OleControl`. Он создаёт **Forms2 OLE CommandButton** в указанном месте и размере.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### Почему это работает

* `DocumentBuilder` — основной API для программного построения документов Word.  
* `InsertForms2OleControl` указывает Aspose.Words внедрить **Forms2 OLE control**, что представляет собой устаревшую технологию форм Word, поддерживающую кнопки, флажки и т.д.  
* Значение перечисления `OleControlType.CommandButton` определяет, что вставляемый элемент является **command button** — именно тот тип, который вы запросили, когда хотели **вставить OLE command button**.  
* `Rectangle` задаёт визуальное размещение. Отрегулируйте координаты X/Y или ширину/высоту, чтобы они соответствовали вашему макету.

## Шаг 3: Сохраните документ

После настройки кнопки запишите документ на диск. Вы можете выбрать любой формат, поддерживаемый Aspose.Words (`.docx`, `.pdf`, `.odt`, …). В этом учебнике мы сохраняем как документ Word.

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Когда вы откроете `CommandButton.docx` в Microsoft Word, вы увидите кликабельную кнопку с подписью **Click Me**. Нажатие её в Word вызывает диалоговое окно «Run Macro», поскольку кнопка является OLE‑формой; позже вы сможете привязать к ней макрос или VBA‑код при необходимости.

## Шаг 4: Проверьте результат (ожидаемый вывод)

Откройте сгенерированный файл:

1. Кнопка появляется в указанных координатах (примерно 1,4 дюйма от левого и верхнего края страницы).  
2. Подпись гласит **Click Me**.  
3. Свойство `Name` (`cmdSubmit`) видно в панели **Developer → Properties** в Word, что удобно, когда нужно ссылаться на элемент из VBA.

![Insert OLE command button example in Word document](insert-ole-button.png)

*Текст alt изображения*: **Пример вставки OLE command button в документ Word** (включает основной ключевой запрос для доступности и SEO).

## Пограничные случаи и часто задаваемые вопросы

### 1. Что делать, если кнопка не появляется там, где я ожидаю?

* Word использует пункты, а не пиксели. Преобразуйте пиксели экрана в пункты (`points = pixels * 72 / DPI`).  
* Убедитесь, что прямоугольник не пересекает поля страницы; иначе Word может сместить элемент.

### 2. Можно ли вставить кнопку в существующий документ?

Да. Загрузите документ с помощью `new Document("Existing.docx")` и используйте тот же workflow `DocumentBuilder`. Просто не забудьте переместить курсор билдера (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")` и т.д.) перед вызовом `InsertForms2OleControl`.

### 3. Как привязать макрос к кнопке?

Aspose.Words не создаёт VBA‑код, но вы можете внедрить макрос после генерации документа:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. Работает ли это с .NET Core на Linux?

OLE‑контроль — функция, специфичная для Windows, поскольку она опирается на COM. На Linux кнопка будет вставлена, но отобразится как статическое изображение без интерактивного поведения. Для кроссплатформенных интерактивных форм рассмотрите использование элементов управления содержимым (`StructuredDocumentTag`).

### 5. Что если мне нужен другой размер или несколько кнопок?

Создайте дополнительные объекты `Rectangle` с уникальными координатами и повторите вызов `InsertForms2OleControl`. Каждая кнопка может иметь собственные `Caption` и `Name`.

## Полный рабочий пример

Ниже приведена полная программа, которую можно скопировать и вставить в консольное приложение. В ней включены все необходимые директивы `using`, обработка ошибок и комментарии.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

Запустите программу, откройте сгенерированный `CommandButton.docx`, и вы увидите кнопку **Click Me**, готовую к дальнейшей настройке.

## Заключение

Теперь вы знаете, как **вставить OLE command button** в документ Word с помощью C# и Aspose.Words. В руководстве рассмотрены:

* Установка пакета Aspose.Words  
* Использование `DocumentBuilder.InsertForms2OleControl` с `OleControlType.CommandButton`  
* Настройка свойств кнопки (`Caption`, `Name`)  
* Сохранение и проверка результата  

Далее вы можете изучать связанные темы, такие как **Aspose.Words OLE control** для флажков, комбобоксов или встраивание целых листов Excel. Вы также можете поэкспериментировать с автоматизацией **Word OLE command button** в более крупных шаблонах или заменить OLE‑элементы современными **content controls** для лучшей кроссплатформенной поддержки.

Не стесняйтесь менять значения прямоугольника, добавлять несколько кнопок или привязывать VBA‑макросы в соответствии с потребностями вашего приложения. Приятного кодинга!

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Insert Ole Object In Word Document](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Insert Ole Object In Word Document As Icon](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Insert Ole Object In Word With Ole Package](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}