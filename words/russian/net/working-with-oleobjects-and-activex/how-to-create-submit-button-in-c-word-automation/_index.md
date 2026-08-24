---
category: general
date: 2026-08-23
description: Создайте кнопку отправки в автоматизации Word на C#. Узнайте, как добавить
  кнопку ActiveX, задать имя кнопки, подпись и текст программно.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create submit button
- set button text
- set button name
- add activex button
- set button caption
language: ru
lastmod: 2026-08-23
og_description: Создайте кнопку отправки в автоматизации Word на C#. В этом руководстве
  показано, как добавить кнопку ActiveX, задать её имя, подпись и текст с использованием
  Aspose.Words.
og_image_alt: Screenshot of a Word document showing a created submit button
og_title: Создать кнопку отправки в автоматизации Word на C#
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  headline: How to create submit button in C# Word automation
  type: TechArticle
- description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  name: How to create submit button in C# Word automation
  steps:
  - name: Expected output
    text: 'Running the program creates `SubmitButton.docx`. When you open the file
      in Microsoft Word:'
  - name: Handling naming collisions
    text: 'If you run the routine multiple times on the same document, Word may auto‑rename
      duplicate controls. To guarantee uniqueness, you can prepend a GUID:'
  - name: Localizing the button caption
    text: 'For multilingual documents, store captions in a resource file and assign
      them at runtime:'
  - name: Responding to the button click
    text: 'The button itself does not contain click logic in C#. You typically attach
      a VBA macro:'
  type: HowTo
tags:
- C#
- Word automation
- ActiveX
- Aspose.Words
title: Как создать кнопку отправки в автоматизации Word на C#
url: /ru/net/working-with-oleobjects-and-activex/how-to-create-submit-button-in-c-word-automation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать кнопку отправки в автоматизации Word на C#

Если вам нужно **создать кнопку отправки** внутри документа Word с помощью C#, это руководство проведёт вас через весь процесс. Вы увидите, как добавить кнопку ActiveX, задать программное имя и установить подпись кнопки, чтобы она выглядела как обычный элемент *Submit*.

Автоматизация элементов форм в Word может заменить ручную работу по размещению и обеспечить согласованность в сотнях документов. В нижеприведённых шагах вы также узнаете, как **установить текст кнопки**, **установить имя кнопки** и **установить подпись кнопки** — всё это необходимо, когда кнопка участвует в макрос‑управляемом рабочем процессе.

## Требования

Перед началом убедитесь, что у вас есть:

* .NET 6.0 (или новее) установлен.
* Ссылка на **Aspose.Words for .NET** (библиотека, предоставляющая `DocumentBuilder.InsertForms2OleControl`).
* Базовые знания C# и форм ActiveX в Word.

Вы можете установить Aspose.Words через NuGet:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Используйте последнюю стабильную версию Aspose.Words, чтобы получить исправления ошибок и новые возможности, связанные с элементами ActiveX.

## Обзор решения

Учебник разбит на три чётких шага:

1. **Добавить кнопку ActiveX** — используйте метод `InsertForms2OleControl`, чтобы разместить кнопку команду в документе.  
2. **Установить имя кнопки** — задайте уникальный программный идентификатор с помощью свойства `Name`.  
3. **Установить подпись кнопки** — определите видимый текст на кнопке через свойство `Caption` (которое также управляет **set button text**, который вы видите в интерфейсе).

К концу руководства у вас будет полностью рабочая процедура **create submit button**, которую можно переиспользовать в любом проекте автоматизации Word.

## Шаг 1: Добавить кнопку ActiveX в документ

Первая задача — **add activex button** в файл Word. Aspose.Words предоставляет перечисление `Forms2OleControlType.CommandButton` для этой цели.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load or create a new document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a CommandButton ActiveX control at the cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton);
```

**Почему этот шаг важен:**  
Элементы ActiveX — единственные элементы формы Word, которые могут выполнять VBA‑макросы или взаимодействовать с внешним кодом. Добавление элемента создаёт заполнитель, который последующие шаги могут настроить.

> **Edge case:** Если документ уже содержит элемент с тем же именем, Word автоматически переименует новый (например, `CommandButton1`). Явное задание имени в следующем шаге избавит от подобных конфликтов.

## Шаг 2: Установить имя кнопки

Надёжный **set button name** критичен, когда необходимо ссылаться на элемент из VBA или из другого кода C#. Свойство `Name` задаёт программный идентификатор кнопки.

```csharp
// Assign a unique programmatic name
commandBtn.Name = "btnSubmit";
```

**Почему следует установить имя:**  
При открытии документа VBA может получить кнопку через `ActiveDocument.InlineShapes("btnSubmit")`. Осмысленное имя, например `btnSubmit`, также проясняет назначение при просмотре XML‑документа.

> **Pro tip:** Делайте имена короткими, буквенно‑цифровыми и начинайте их с буквы, чтобы они соответствовали правилам именования VBA.

## Шаг 3: Установить подпись кнопки (видимый текст)

Текст, который видят пользователи на кнопке, управляется свойством **set button caption**. В интерфейсе Word это отображается как метка кнопки, что также является **set button text**, который вы хотите показать.

```csharp
// Define the text shown on the button
commandBtn.Caption = "Submit";
```

**Почему подпись важна:**  
Подпись — это пользовательская метка. Изменение её позже не затрагивает имя кнопки, поэтому вы можете локализовать интерфейс, не ломая код, зависящий от `btnSubmit`.

> **Common question:** *Можно ли установить одновременно Caption и Value?*  
> Для `CommandButton` свойство `Caption` отвечает за метку, а `Value` не используется. Если нужен скрытый параметр, храните его в пользовательском свойстве документа.

## Полный рабочий пример

Объединив три шага, вы получаете готовую процедуру, которую можно вставить в любое консольное или Windows‑приложение:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert the ActiveX command button
        Forms2OleControl commandBtn = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton);

        // 3. Set a meaningful name for later reference
        commandBtn.Name = "btnSubmit";

        // 4. Set the visible caption (this is the button text)
        commandBtn.Caption = "Submit";

        // Optional: position the button (in points)
        commandBtn.Left = 100;   // distance from left margin
        commandBtn.Top = 200;    // distance from top margin
        commandBtn.Width = 80;
        commandBtn.Height = 30;

        // Save the document
        doc.Save("SubmitButton.docx");
        Console.WriteLine("Document with submit button created successfully.");
    }
}
```

### Ожидаемый результат

Запуск программы создаёт `SubmitButton.docx`. При открытии файла в Microsoft Word:

* Появляется кнопка **Submit** в указанном месте.
* Имя кнопки — `btnSubmit` (проверьте через *Developer → Design Mode → Properties*).
* При клике в режиме дизайна отображается подпись *Submit*.

Теперь у вас есть переиспользуемый строительный блок для любого решения на основе форм в Word.

## Дополнительные соображения

### Обработка конфликтов имён

Если запускать процедуру несколько раз в одном документе, Word может автоматически переименовать дублирующиеся элементы. Чтобы гарантировать уникальность, можно добавить GUID в начало имени:

```csharp
commandBtn.Name = $"btnSubmit_{Guid.NewGuid():N}";
```

### Локализация подписи кнопки

Для многоязычных документов храните подписи в файле ресурсов и присваивайте их во время выполнения:

```csharp
commandBtn.Caption = Resources.SubmitButtonLabel;
```

### Обработка клика по кнопке

Сама кнопка не содержит логики клика в C#. Обычно к ней привязывают VBA‑макрос:

```vba
Sub btnSubmit_Click()
    MsgBox "Form submitted!"
End Sub
```

Поскольку вы **set button name** задали как `btnSubmit`, имя макроса автоматически следует конвенции `<Name>_Click`.

## FAQ по устранению неполадок

| Вопрос | Ответ |
|----------|--------|
| **Почему кнопка отображается пустой?** | Убедитесь, что задали свойство `Caption`; без него кнопка не показывает текст. |
| **Можно ли использовать другой элемент ActiveX?** | Да. Замените `Forms2OleControlType.CommandButton` на `CheckBox`, `OptionButton` и т.д., но свойства будут отличаться. |
| **Совместимо ли это с .NET Core?** | Aspose.Words for .NET поддерживает .NET 6+, поэтому тот же код работает и в .NET Core, и в .NET Framework. |
| **Что делать, если в документе уже есть кнопка?** | Используйте уникальное `Name` (например, добавьте GUID), чтобы избежать конфликтов. |

## Заключение

Теперь вы знаете, как **create submit button** программно в документе Word с помощью C#. Следуя трем шагам — **add activex button**, **set button name** и **set button caption** — вы сможете надёжно **set button text**, **set button name** и **set button caption** для любого автоматизированного решения формы.

Дальше вы можете изучить:

* Добавление VBA‑макросов, реагирующих на клик **submit button**.  
* Стилизацию кнопки с помощью пользовательских шрифтов или цветов через базовый XML.  
* Генерацию нескольких кнопок в цикле для динамических форм.

Экспериментируйте с разными подписями, именами и позициями, чтобы подстроить процесс под ваш конкретный рабочий поток. Удачной автоматизации!

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогая вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}