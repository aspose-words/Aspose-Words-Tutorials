---
category: general
date: 2026-11-18
description: Создайте пустой документ Word и вставьте кнопку ActiveX с помощью C#.
  Узнайте, как добавить элемент управления, установить подпись кнопки и сохранить
  файл.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: ru
lastmod: 2026-11-18
og_description: Создайте пустой документ Word и вставьте кнопку ActiveX с помощью
  C#. Следуйте этому полному руководству, чтобы добавить элемент управления, задать
  подпись кнопки и сохранить результат.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: Создайте пустой документ Word и вставьте кнопку ActiveX — пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Создайте пустой документ Word и вставьте кнопку ActiveX
url: /ru/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создайте пустой документ Word и вставьте кнопку ActiveX

Если вам нужно **create a blank Word document** и разместить в нём интерактивную кнопку ActiveX, это руководство покажет, как сделать это с помощью Aspose.Words for .NET. Вы увидите полный код, поймёте, почему каждая строка важна, и узнаете, как **set button caption**, чтобы элемент выглядел готовым к взаимодействию с пользователем.

Помимо основной цели, мы рассмотрим **how to insert ActiveX**, шаги **how to add control** в файл Word и нюансы **insert ActiveX button** с пользовательской подписью. К концу у вас будет переиспользуемый шаблон для любой задачи автоматизации документов, требующей встроенных UI‑элементов.

## Что вы узнаете

* Как **create a blank Word document** программно.  
* Точные вызовы API, необходимые для **insert ActiveX button** и настройки его свойств.  
* Как **set button caption**, чтобы элемент отображал нужный текст.  
* Советы по сохранению файла в выбранном месте и обработке распространённых подводных камней.

### Требования

* .NET 6.0 или новее (код также работает с .NET Framework 4.6+).  
* Aspose.Words for .NET установлен (`Install-Package Aspose.Words`).  
* Базовое знакомство с C# и Visual Studio или любой .NET‑совместимой IDE.

---

## Создание пустого документа Word с помощью Aspose.Words

Первый шаг — создать пустой объект `Document`. Этот объект представляет файл Word, который не содержит содержимого, пока мы ничего не добавим.

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*Почему это важно*: Пустой `Document` предоставляет чистый холст. Позже вы можете добавлять абзацы, таблицы или элементы управления, не беспокоясь о существующем форматировании.

---

## Инициализация DocumentBuilder для работы с документом

`DocumentBuilder` — вспомогательный класс, позволяющий вставлять содержимое в текущую позицию курсора. Он автоматически отслеживает, где вы находитесь в документе.

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Почему это важно*: Без `DocumentBuilder` вам пришлось бы вручную манипулировать низкоуровневым деревом узлов. Builder упрощает вставку текста, изображений и элементов управления ActiveX.

---

## Как вставить кнопку ActiveX (insert activex button)

Now we use `InsertForms2OleControl` to embed an ActiveX control. The method requires three arguments:

1. Тип элемента управления (`OleControlType.CommandButton`).  
2. Внутреннее имя элемента (используется VBA или макросом).  
3. `RectangleF`, определяющий позицию и размер на странице.

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*Почему это важно*: Это ядро **how to insert activex** в документ Word. Координаты прямоугольника задаются в пунктах (1 пункт = 1/72 дюйма). Отрегулируйте их, чтобы разместить кнопку в нужном месте.

### Совет

Если вам нужно, чтобы кнопка появилась на определённой странице, сначала переместите курсор builder'а:

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## Как установить подпись кнопки (set button caption)

После размещения элемента управления вы можете изменить его свойства. Самое заметное свойство — `Caption`, которое определяет текст, отображаемый на кнопке.

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*Почему это важно*: Пользователи видят подпись, а не внутреннее имя. Изменив её, вы делаете кнопку значимой в окончательном документе.

---

## Сохранение документа с кнопкой

Наконец, запишите документ на диск. Вы можете выбрать любой поддерживаемый формат (`.docx`, `.pdf` и т.д.). Здесь мы сохраняем как документ Word.

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*Почему это важно*: Сохранение файла позволяет открыть его в Microsoft Word и протестировать кнопку. При открытии документа кнопка появится с подписью «Press».

### Ожидаемый результат

Открытие `with_button.docx` в Word показывает пустую страницу с прямоугольной кнопкой, помеченной **Press**. По умолчанию при нажатии ничего не происходит, так как не привязан VBA‑макрос, но элемент полностью функционален и позже может быть связан с кодом.

---

## Как добавить элемент управления в конкретный абзац (how to add control)

Иногда требуется разместить кнопку внутри определённого абзаца, например после пояснительного текста. Используйте `MoveTo`, чтобы позиционировать builder перед вставкой элемента управления.

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*Почему это важно*: Этот шаблон демонстрирует **how to add control** в контексте, обеспечивая логичность макета документа.

---

## Распространённые подводные камни и как их избежать

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| Button appears off‑page | Координаты Rectangle находятся за пределами полей страницы | Используйте `builder.PageSetup`, чтобы получить размеры страницы и вычислить безопасный `RectangleF`. |
| Caption does not show | `Caption` установлен до полной инициализации элемента управления | Установите `Caption` **после** вызова `InsertForms2OleControl`, как показано в Шаге 4. |
| Document saves without the button | Курсор builder'а был перемещён после вставки без фиксации изменений | Оставьте builder на той же странице или вызовите `builder.Document.UpdatePageLayout()` перед сохранением. |

---

## Полный, исполняемый пример

Ниже представлена полная программа, которую вы можете скопировать, вставить и запустить. Она создаёт пустой файл Word, вставляет кнопку ActiveX, задаёт её подпись и сохраняет результат.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Вывод**: После запуска программы откройте `C:\Temp\with_button.docx` в Microsoft Word. Вы увидите одну страницу с текстом «Below is an ActiveX button created programmatically:», за которым следует кнопка с подписью **Press**.

---

## Заключение

Теперь вы знаете, как **create a blank Word document**, **insert an ActiveX button**, **set button caption** и **save** результат с помощью Aspose.Words for .NET. Тот же шаблон можно расширить на другие элементы управления ActiveX (чекбоксы, списковые окна и т.д.), изменив `OleControlType`.  

Далее вы можете изучить события **how to insert ActiveX button** с VBA или **how to add control** в существующие документы, уже содержащие контент. Оба направления опираются непосредственно на рассмотренные здесь концепции.

Удачной разработки, и не стесняйтесь экспериментировать с различными размерами, позициями и подписями, чтобы они соответствовали требованиям UI вашего приложения!

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Как создать документ Word на C# с кнопкой ActiveX command button](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [Как добавить кнопку ActiveX в документ Word с помощью Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}