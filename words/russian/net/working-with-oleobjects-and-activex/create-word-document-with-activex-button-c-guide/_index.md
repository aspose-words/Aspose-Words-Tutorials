---
category: general
date: 2026-07-19
description: Создайте документ Word с помощью Aspose.Words C# и узнайте, как добавить
  кнопку ActiveX, задать её размер и вставить кнопку программно.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: ru
lastmod: 2026-07-19
og_description: Создайте документ Word с помощью Aspose.Words C# и внедрите кнопку
  ActiveX за считанные секунды. Следуйте пошаговому руководству, чтобы легко задать
  размер кнопки и вставить её.
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: Создание документа Word с кнопкой ActiveX – учебник C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Создание документа Word с кнопкой ActiveX – руководство по C#
url: /ru/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание Word‑документа с кнопкой ActiveX – Полное руководство на C#

Когда‑нибудь задавались вопросом, как **создать word document**, содержащий работающую кнопку ActiveX? Возможно, вы автоматизируете отчёт и вам нужен кликабельный элемент «Одобрить» прямо внутри файла. В этом руководстве мы пошагово покажем, как с помощью Aspose.Words for .NET добавить кнопку командного управления ActiveX, задать её размер и разместить её там, где нужно.  

Если вы когда‑либо думали *как добавить activex*‑элементы без ручного открытия Word, вы попали по адресу. К концу вы получите готовый пример, понятное объяснение каждого шага и советы по работе с типичными подводными камнями.

## Что вы узнаете

- Как настроить Aspose.Words в проекте C#  
- Точный код для **create word document** и встраивания кнопки ActiveX  
- Способы **set button size** и настройки подписи и имени кнопки  
- Правильный метод **insert command button** и **how to insert button** в любое место документа  
- Особенности крайних случаев (версия Word, ограничения платформы, предупреждения безопасности)

### Предварительные требования

- .NET 6.0 или новее (код также работает на .NET Framework 4.7+).  
- Действительная лицензия Aspose.Words for .NET (или бесплатный оценочный ключ).  
- Visual Studio 2022 (или любая другая IDE).  
- Базовое знакомство с C# и объектно‑ориентированным программированием.

Никаких дополнительных сторонних библиотек не требуется.

---

## Шаг 1: Создание Word‑документа – настройка проекта

Прежде чем мы сможем **insert command button**, нам нужен пустой Word‑файл. Этот шаг также демонстрирует классический шаблон «create word document» с использованием Aspose.Words.

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Почему это важно:** `Document` представляет весь файл .docx, а `DocumentBuilder` отслеживает текущую позицию курсора. Все последующие вставки (включая наш элемент ActiveX) происходят относительно этого builder’а.

---

## Шаг 2: Как добавить ActiveX – создание элемента CommandButton

Теперь, когда документ существует, займёмся частью **how to add activex**. Aspose.Words предоставляет класс `Forms2OleControl` для объектов ActiveX. Здесь мы создаём кнопку командного управления и настраиваем её свойства, включая требование **set button size**.

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **Полезный совет:** Размер измеряется в пунктах (1 пункт = 1/72 дюйма). Подберите значения под ваш макет; для типичной кнопки панели инструментов удобно 120 × 30.

---

## Шаг 3: Вставка кнопки командного управления – ядро **Insert Command Button**

Когда элемент готов, мы **insert command button** в документ в текущей позиции builder’а. При необходимости можно переместить builder (например, после абзаца) перед вызовом этого метода.

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

Если нужно **how to insert button** в конкретную закладку, сначала переместите builder:

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **Что происходит за кулисами?** Aspose.Words записывает необходимые потоки OLE‑объекта в пакет .docx, поэтому Word может отобразить кнопку без дополнительных макросов.

---

## Шаг 4: Сохранение документа – завершение цикла **Create Word Document**

Последний шаг прост: сохранить файл на диск. Это завершает полный цикл **create word document**, встраивания ActiveX и сохранения.

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

Откройте полученный файл в Microsoft Word (только Windows). Вы увидите кликабельную кнопку с надписью «Click Me». При нажатии будет выполнено действие по умолчанию для CommandButton — ничего не произойдёт, если не привязать VBA‑код, но элемент полностью функционален.

> **Ожидаемый результат:** Файл .docx с одной страницей, кнопкой, центрированной в точке вставки, размером 120 × 30 pt, с подписью «Click Me».  
> ![Вставленная кнопка ActiveX в документ Word](placeholder-image.png)  
> *Текст alt изображения:* **Вставленная кнопка ActiveX в документ Word с использованием C#** (соответствует `og_image_alt`).

---

## Шаг 5: Крайние случаи, безопасность и лучшие практики

### Ограничения платформы
- Элементы ActiveX работают только в Windows‑версии Word. Пользователи macOS или Word Online увидят статическое изображение.
- В некоторых корпоративных средах ActiveX отключён из соображений безопасности; возможно, понадобится подписать документ или попросить пользователей включить содержимое.

### Взаимодействие с VBA (по желанию)
Если требуется, чтобы кнопка запускала макрос, после сохранения необходимо добавить VBA‑проект в документ. Aspose.Words не генерирует VBA‑код автоматически, но можно воспользоваться API `Document.VbaProject` для его внедрения.

### Конфликты имён
Всегда задавайте каждому элементу уникальное `Name`. Повторное использование одного и того же имени может вызвать ошибки выполнения, когда Word пытается разрешить элемент.

### Совет по производительности
При вставке большого количества элементов переиспользуйте один экземпляр `DocumentBuilder` и избегайте вызова `doc.Save` внутри цикла. Сгруппируйте вставки и сохраняйте один раз в конце.

---

## Полный рабочий пример

Объединив всё вместе, получаем полностью готовую к копированию и вставке программу:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Запустите программу, откройте сохранённый файл — и вы увидите кнопку точно в том месте, где находился builder.

---

## Заключение

Мы **создали word document** с нуля, изучили **how to add activex** через настройку `Forms2OleControl`, освоили свойства **set button size**, а также продемонстрировали правильный способ **insert command button** и **how to insert button** в любую позицию файла.  

Из одного примера кода вы получили прочную основу для более сложной автоматизации Word — будь то создание шаблонов с интерактивными формами, генерация контрактов, требующих подтверждения пользователем, или просто добавление нескольких удобных элементов в отчёт.

### Что дальше?

- **Стилизация кнопки** — изменение шрифтов, цветов или добавление фонового изображения.  
- **Привязка VBA‑макросов** — чтобы кнопка выполняла расчёты или запускала внешние программы.  
- **Комбинация с другими элементами** — чекбоксы, списки, или даже встроенные листы Excel.  

Экспериментируйте, а если возникнут вопросы, оставляйте комментарий ниже. Приятного кодинга и удачной автоматизации Word с Aspose.Words!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом гайде. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}