---
category: general
date: 2026-08-04
description: Создайте пустой документ Word и вставьте кнопку управления с помощью
  Aspose.Words. Узнайте, как задать размер кнопки и добавить кликабельную кнопку на
  C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: ru
lastmod: 2026-08-04
og_description: Создайте пустой документ Word с помощью Aspose.Words и вставьте кнопку
  команды. Это руководство показывает, как задать размер кнопки, добавить кликабельную
  кнопку и сохранить файл.
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: Создайте пустой документ Word и добавьте кнопку управления – полный учебник
  по C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Создайте пустой документ Word с кнопкой команды – пошаговое руководство
url: /ru/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание пустого документа Word с кнопкой команды – пошаговое руководство

Если вам нужно **create blank word document**, содержащий интерактивную кнопку, это руководство покажет, как сделать это с помощью Aspose.Words for .NET. Вы узнаете, как **insert command button**, настроить её внешний вид и сделать её кликабельной — всё это в нескольких строках C#.

Руководство охватывает всё от настройки проекта до сохранения конечного файла, так что вы можете скопировать‑вставить полное решение в своё приложение. По пути мы также объясним, как **add clickable button**, **set button size** и **create command button** программно.

## Требования

* .NET 6.0 SDK или более новая версия, установленная.
* Visual Studio 2022 (или любая IDE, поддерживающая .NET).
* NuGet‑пакет Aspose.Words for .NET (`Aspose.Words` версии 23.12 или новее).
* Базовое знакомство с C# и объектно‑ориентированным программированием.

Для работы не требуются дополнительные сборки Office Interop, поскольку Aspose.Words полностью независим от Microsoft Word.

## Шаг 1: Настройка проекта .NET

Создайте консольное приложение, которое будет содержать код автоматизации Word.

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Эта команда создаёт новую папку `WordButtonDemo` с готовым к запуску `Program.cs` и добавляет библиотеку Aspose.Words.

## Шаг 2: Создание пустого документа Word

Первая операция — **create blank word document**. Aspose.Words предоставляет класс `Document`, который представляет пустой файл Word сразу из коробки.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

Создание пустого документа даёт вам чистое полотно, на которое можно добавлять абзацы, таблицы или, в данном случае, OLE‑кнопку команды.

## Шаг 3: Инициализация DocumentBuilder

`DocumentBuilder` — вспомогательный класс, позволяющий вставлять содержимое в документ. Его необходимо привязать к только что созданному документу.

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder поддерживает текущую позицию курсора, поэтому любые последующие вставки происходят точно там, где вы хотите.

## Шаг 4: Вставка command button

Теперь мы **insert command button** (OLE `Forms2OleControl`) в документ. Метод `InsertForms2OleControl` требует три аргумента:

1. ProgID OLE‑контроля – `"CommandButton"` для стандартной кнопки.
2. `Rectangle`, определяющий **set button size** и позицию.
3. Подпись, отображаемая на кнопке.

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

Когда документ открывается в Word, кнопка ведёт себя как любой нативный элемент формы — её можно нажать, и Word выполнит связанный макрос (если он существует). Это удовлетворяет требование **add clickable button**.

### Зачем использовать Forms2OleControl?

`Forms2OleControl` встраивает OLE‑объект непосредственно в файл DOCX, сохраняя свойства элемента управления без необходимости сборки Word Interop. Это самый надёжный способ **create command button**, который работает во всех версиях Word.

## Шаг 5: Настройка кнопки (необязательно)

Возможно, вы захотите более точно **set button size** или изменить дополнительные свойства, такие как шрифт или цвет фона. Aspose.Words раскрывает внутренний OLE‑объект, позволяя вносить дальнейшие настройки.

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

Если нужен другой размер, просто измените значения `Rectangle` в Шаге 4. Координаты измеряются в пунктах (1 pt = 1/72 дюйма), поэтому `120` примерно соответствует ширине 1,67 дюйма.

## Шаг 6: Сохранение документа

Наконец, запишите документ на диск. Полученный файл содержит **blank word document** с полностью функциональной command button.

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

Когда вы откроете `CommandButtonDemo.docx` в Microsoft Word, вы увидите кнопку с надписью «Click Me». При нажатии на кнопку откроется диалоговое окно макроса по умолчанию, если вы не привяжете пользовательский макрос.

## Полный исходный код

Ниже приведена полная программа, которую вы можете скопировать в `Program.cs`. Она включает все описанные выше шаги и компилируется без изменений.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Ожидаемый результат

Запуск программы создаёт `CommandButtonDemo.docx`. Открытие файла в Word показывает:

* Одна страница, содержащая кнопку с надписью **Click Me**.
* Кнопка учитывает **set button size** (120 × 30 пунктов).
* Нажатие на кнопку вызывает стандартное поведение command‑button в Word, подтверждая, что операция **add clickable button** выполнена успешно.

## Распространённые вопросы и особые случаи

| Вопрос | Ответ |
|----------|--------|
| **Работает ли это с файлами .doc?** | Да. Измените расширение файла в `doc.Save("file.doc")`. OLE‑контроль также сохраняется в старом бинарном формате. |
| **Что делать, если нужны несколько кнопок?** | Вызовите `InsertForms2OleControl` несколько раз, корректируя `Rectangle` для каждой новой кнопки, чтобы избежать перекрытия. |
| **Можно ли привязать макрос к кнопке?** | Сама кнопка не содержит кода макроса. Вы должны добавить VBA‑макрос в документ вручную или через коллекцию `Modules` объекта `Document`. |
| **Отображается ли кнопка при экспорте в PDF?** | При экспорте DOCX в PDF с помощью Aspose.Words кнопка отображается как статическое изображение, а не как интерактивный элемент. |
| **Какие версии Word поддерживаются?** | OLE‑кнопка команды работает в Word 2007 и новее, так как соответствует стандартной спецификации Forms2.0. |

## Заключение

Теперь вы знаете, как **create blank word document**, **insert command button**, **add clickable button** и **set button size** с помощью Aspose.Words for .NET. Полный пример демонстрирует процесс **create command button** от начала до конца, предоставляя прочную основу для более сложных задач автоматизации Word.

## Следующие шаги

* Исследуйте другие OLE‑контролы (например, `CheckBox`, `ListBox`), изменяя ProgID в `InsertForms2OleControl`.
* Сочетайте кнопку с VBA‑макросом для выполнения пользовательских действий при её нажатии.
* Используйте `DocumentBuilder` из Aspose.Words для добавления дополнительного содержимого, такого как таблицы, изображения или сноски, перед вставкой кнопки.
* Экспериментируйте со значениями **set button size**, чтобы соответствовать требованиям макета вашего документа.

Удачной разработки и наслаждайтесь созданием более богатых документов Word с интерактивными элементами!

## Что следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Создание групповой фигуры в документе Word с использованием Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Создание пустого документа Word с фигурой прямоугольника с тенью — пошаговое руководство](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Создание документа Word с Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}