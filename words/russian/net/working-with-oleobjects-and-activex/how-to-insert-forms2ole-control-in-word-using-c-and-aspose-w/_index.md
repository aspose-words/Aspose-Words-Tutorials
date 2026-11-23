---
category: general
date: 2026-11-22
description: Научитесь вставлять элемент управления Forms2Ole в Word с помощью C#.
  Это пошаговое руководство охватывает DocumentBuilder, размещение кнопки команды
  и сохранение .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: ru
lastmod: 2026-11-22
og_description: Вставьте элемент управления Forms2Ole в Word с помощью C#. Следуйте
  этому руководству, чтобы добавить кнопку команды, используя Aspose.Words и DocumentBuilder.
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: Вставка элемента управления Forms2Ole в Word с помощью C# – полное руководство
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Как вставить элемент управления Forms2Ole в Word с помощью C# и Aspose.Words
url: /ru/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как вставить Forms2Ole control в Word с помощью C# и Aspose.Words

Если вам нужно **вставить Forms2Ole control в Word**, этот учебник покажет, как сделать это с помощью C#. Независимо от того, создаёте ли вы заполняемый шаблон или автоматизируете создание форм, приведённое решение позволяет программно добавить кнопку команды.

Вы узнаете, как создать пустой документ, использовать `DocumentBuilder` для размещения элемента управления и сохранить результат в формате `.docx`. Руководство также охватывает распространённые подводные камни, такие как системы координат и совместимость со старыми версиями Word.

## Предварительные требования

* .NET 6.0 или новее (код также работает с .NET Framework 4.6+)
* Aspose.Words for .NET (пакет NuGet `Aspose.Words`)
* Базовые знания C# и модели объектов Word
* IDE, например Visual Studio или VS Code

## Шаг 1: Настройка проекта и импорт пространств имён

Создайте новое консольное приложение и добавьте пакет Aspose.Words:

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

В `Program.cs` импортируйте необходимые пространства имён:

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **Совет:** Используйте последнюю версию Aspose.Words, чтобы получить полную поддержку API `Forms2OleControl`.

## Шаг 2: Создание пустого документа и инициализация DocumentBuilder

Класс `Document` представляет файл Word, а `DocumentBuilder` предоставляет методы для вставки содержимого.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` работает как курсор; после этой строки вы можете размещать элементы в любой части документа.

## Шаг 3: Определение позиции и размера кнопки

Word измеряет координаты в пунктах (1 pt ≈ 1/72 in). Структура `Rectangle` из `System.Drawing` описывает границы элемента управления.

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` размещает элемент управления в левом верхнем углу текущей страницы.
* Измените `x` и `y`, чтобы переместить кнопку в другое место (например, `new Rectangle(150, 200, 100, 30)`).

## Шаг 4: Вставка команды кнопки Forms2Ole

Теперь используйте `InsertForms2OleControl` для добавления элемента управления. Метод требует тип элемента, имя и границы, определённые выше.

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

Возвращаемый объект `Forms2OleControl` позволяет изменять свойства, такие как `Enabled`, `Visible`, или даже позже привязать имя макроса.

### Зачем использовать Forms2Ole?

* **Совместимость со старыми версиями** – элементы управления Forms2Ole работают в Word 97‑2003 (`.doc`) и более новых файлах `.docx`.
* **Поддержка макросов** – они могут вызывать VBA‑макросы, что делает их идеальными для интерактивных шаблонов.
* **Точное размещение** – в отличие от элементов управления содержимым, вы контролируете точные координаты.

## Шаг 5: Сохранение документа

Наконец, запишите файл на диск. Выберите папку, в которую у вас есть права записи.

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Откройте `output.docx` в Microsoft Word. Вы увидите кнопку с надписью **ClickMe** в левом верхнем углу первой страницы. Нажатие на неё в Word ничего не сделает, пока вы не назначите макрос, но элемент управления полностью функционален.

## Обработка распространённых граничных случаев

| Ситуация | Как решить проблему |
|-----------|-------------------|
| **Кнопка находится за пределами страницы** | Убедитесь, что координаты `Rectangle` находятся внутри полей страницы. Используйте `builder.PageSetup.PageWidth` и `PageHeight` для расчёта безопасных границ. |
| **Элемент управления не виден в старых версиях Word** | Сохраните документ как `.doc` (`doc.Save("output.doc", SaveFormat.Doc)`) чтобы обеспечить совместимость Forms2Ole с Word 97‑2003. |
| **Необходимо изменить подпись** | После вставки установите `commandButton.Caption = "Submit";`. |
| **Назначить макрос** | Установите `commandButton.MacroName = "MyMacro"`; макрос должен существовать в VBA‑проекте документа. |
| **Несколько кнопок** | Повторите Шаг 4 с разными значениями `Rectangle` и уникальными именами. |

## Полный, исполняемый пример

Объединив всё вместе, представляем автономную программу, которую можно скопировать, вставить и запустить:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Ожидаемый результат:** После запуска программы `output.docx` откроется в Word с кликабельной кнопкой с надписью *Click Me!* в левом верхнем углу первой страницы.

## Заключение

Теперь вы знаете, как **вставить Forms2Ole control в Word** с помощью C# и Aspose.Words. Процесс включает создание `Document`, позиционирование `Rectangle` и вызов `InsertForms2OleControl` через `DocumentBuilder`. С полным примером кода и рекомендациями по граничным случаям вы можете интегрировать кнопки команд в любой автоматизированный процесс работы с Word.

### Следующие шаги

* Исследуйте другие значения `ControlType`, такие как `CheckBox` или `OptionButton`.
* Сочетайте элементы управления Forms2Ole с VBA‑макросами для интерактивных форм.
* Используйте `DocumentBuilder.MoveTo` для размещения кнопок в определённых абзацах или таблицах.
* Ознакомьтесь с документацией Aspose.Words по **Forms2Ole** для расширенных настроек свойств.

Удачной разработки и приятного создания более функциональных документов Word с C# и Aspose.Words!

## Что следует изучить дальше?

Следующие учебники охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Как вставить кнопку OLE в документ Word с помощью C#](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [как добавить ActiveX‑элемент в Word с Aspose.Words – пошаговое руководство](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Добавить кнопку команды в документ Word с Aspose.Words – Полное руководство](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}