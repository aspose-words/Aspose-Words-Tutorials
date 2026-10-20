---
category: general
date: 2026-07-23
description: Создание кнопки в документе Word с помощью Aspose.Words – пошаговое руководство
  по вставке ActiveX CommandButton в файл .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document button
- ActiveX CommandButton
- DocumentBuilder
- InsertForms2OleControl
- Aspose.Words
language: ru
lastmod: 2026-07-23
og_description: 'Создайте кнопку создания документа Word с Aspose.Words: узнайте,
  как за несколько минут внедрить ActiveX CommandButton в файл Word.'
og_image_alt: Screenshot of a Word document showing an inserted CommandButton control
og_title: Кнопка создания Word‑документа – Полное руководство по Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  headline: create word document button with Aspose.Words – Full Code Example
  type: TechArticle
- description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  name: create word document button with Aspose.Words – Full Code Example
  steps:
  - name: '**Creates** an OLE object inside the Word file.'
    text: '**Creates** an OLE object inside the Word file.'
  - name: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
    text: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
  - name: '**Positions** it according to the rectangle we supplied.'
    text: '**Positions** it according to the rectangle we supplied.'
  - name: Launch Microsoft Word.
    text: Launch Microsoft Word.
  - name: Navigate to **File → Open** and select `CommandButton.docx`.
    text: Navigate to **File → Open** and select `CommandButton.docx`.
  - name: You should see a rectangular button labeled “CommandButton1”.
    text: You should see a rectangular button labeled “CommandButton1”.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
- CommandButton
title: Кнопка создания Word‑документа с Aspose.Words – полный пример кода
url: /ru/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# create word document button with Aspose.Words – Complete Programming Guide

Когда‑то вам нужно **create word document button**, но вы не знали, какой API использовать? Вы не одиноки — большинство разработчиков сталкиваются с трудностями, пытаясь встроить интерактивные элементы в файл .docx. Хорошая новость? С Aspose.Words для .NET вы можете добавить полностью функциональную ActiveX CommandButton в документ Word всего в несколько строк кода.

В этом руководстве мы пройдем весь процесс: от настройки проекта, инициализации `DocumentBuilder`, вставки кнопки с помощью `InsertForms2OleControl` и, наконец, сохранения файла, чтобы Word распознал элемент управления. К концу вы получите готовый к использованию файл Word, содержащий кликабельную кнопку — без необходимости использовать COM‑interop.

## What You’ll Need

Прежде чем начать, убедитесь, что у вас есть следующие предварительные условия:

- **.NET 6.0** или новее (код также работает с .NET Framework 4.6+).  
- **Aspose.Words for .NET** пакет NuGet (версия 23.9 или новее).  
- Базовое понимание C# (мы постараемся сделать синтаксис доступным для новичков).  
- Visual Studio 2022 или любой другой предпочитаемый IDE.

И всё — без дополнительных COM‑ссылок, без Office‑interop, только чистый управляемый код.

---

## Step 1: Set Up Aspose.Words to **create word document button**

Во‑первых, добавьте пакет Aspose.Words в ваш проект:

```bash
dotnet add package Aspose.Words
```

Или, если вы используете UI NuGet в Visual Studio, найдите “Aspose.Words” и нажмите **Install**. Эта одна строка даст вам доступ к `Document`, `DocumentBuilder` и методу `InsertForms2OleControl`, которые понадобятся позже.

> **Pro tip:** Держите ваши пакеты NuGet в актуальном состоянии; новые версии часто включают исправления ошибок, связанных с обработкой ActiveX.

---

## Step 2: Initialize **DocumentBuilder** for an **ActiveX CommandButton**

Теперь создаём новый документ Word и инициализируем `DocumentBuilder`. Считайте `DocumentBuilder` кистью, которой вы рисуете содержимое на холсте.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 2.1: Create a new empty document
        Document document = new Document();

        // Step 2.2: Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Обратите внимание, что мы импортируем `System.Drawing` — структура `Rectangle` определяет расположение и размер кнопки. Здесь будет находиться **ActiveX CommandButton**.

---

## Step 3: Use **InsertForms2OleControl** to **add a CommandButton**

Суть руководства: вставка самой кнопки. Метод `InsertForms2OleControl` принимает три аргумента — тип управления, `Rectangle` и, опционально, имя. Мы используем `OleControlType.CommandButton`, чтобы указать нужный элемент управления.

```csharp
        // Step 3: Insert an ActiveX CommandButton at (0,0) with width=100, height=30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));
```

Этот один вызов делает многое:

1. **Создаёт** OLE‑объект внутри файла Word.  
2. **Регистрирует** его как ActiveX CommandButton, который Word отобразит как кликабельный UI‑элемент.  
3. **Размещает** его согласно переданному прямоугольнику.

Если нужно изменить подпись кнопки или другие свойства, сделайте это после вставки, получив доступ к базовому `OleFormat`. Для большинства сценариев подпись по умолчанию (“CommandButton1”) подходит.

---

## Step 4: Save the Word Document Containing the **CommandButton**

Сохранение простое — укажите папку, в которую у вас есть права записи. Расширение файла должно быть `.docx`, иначе кнопка не сохранится.

```csharp
        // Step 4: Save the document with the embedded button
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Когда откроете `CommandButton.docx` в Microsoft Word, вы увидите небольшую кнопку в левом верхнем углу первой страницы. По умолчанию она ничего не делает (для этого нужен VBA), но элемент полностью функционирует и может быть привязан позже.

> **Why this works:** Aspose.Words записывает OLE‑поток напрямую в пакет DOCX, обходя необходимость генерации элемента управления Word‑ом во время выполнения. Это гарантирует, что кнопка появится точно там, где вы её разместили.

---

## Step 5: Verify the Button in Word

Откройте сгенерированный файл:

1. Запустите Microsoft Word.  
2. Перейдите в **File → Open** и выберите `CommandButton.docx`.  
3. Вы должны увидеть прямоугольную кнопку с надписью “CommandButton1”.  

Если кнопка не отображается, убедитесь, что включён **Design Mode** (Developer → Design Mode). Это переключает визуальное представление ActiveX‑элементов.

---

## Step 6: Advanced Options – Customizing the **ActiveX CommandButton**

Ниже несколько быстрых настроек, которые могут пригодиться:

| Goal | Code Snippet |
|------|--------------|
| Change caption | ```csharp<br/>OleFormat ole = builder.CurrentParagraph.Runs[0].OleFormat;<br/>ole.OleControlCaption = "Submit";``` |
| Set macro name (requires Word macro support) | ```csharp<br/>ole.OleControlMacroName = "MyMacro";``` |
| Resize after insertion | ```csharp<br/>builder.MoveToDocumentEnd();<br/>builder.InsertForms2OleControl(OleControlType.CommandButton, new Rectangle(0,0,150,40));``` |

Эти фрагменты демонстрируют гибкость `InsertForms2OleControl`. Вы даже можете внедрять другие ActiveX‑элементы, такие как `CheckBox` или `ListBox`, заменив значение перечисления `OleControlType`.

---

## Full Working Example

Ниже полностью готовая к копированию программа, которая **creates a word document button** с нуля:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class CreateWordDocumentButton
{
    static void Main()
    {
        // 1️⃣ Create a new empty document
        Document document = new Document();

        // 2️⃣ Initialize DocumentBuilder – the tool that lets us edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert an ActiveX CommandButton at position (0,0) with size 100x30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));

        // 4️⃣ Save the .docx file – this is where the button lives
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);

        Console.WriteLine($"✅ Document with button saved to: {outputPath}");
    }
}
```

**Ожидаемый вывод при запуске программы:**

```
✅ Document with button saved to: C:\Temp\CommandButton.docx
```

Откройте полученный файл — кнопка будет точно там, где её разместил код.

---

## Common Pitfalls & How to Avoid Them

- **Missing `System.Drawing` reference** – Структура `Rectangle` находится в этом пространстве имён; без неё компилятор выдаст ошибку.  
- **Using an older Aspose.Words version** – Ранние версии не полностью поддерживали `InsertForms2OleControl`. Обновитесь до последней стабильной сборки.  
- **Saving as `.doc` instead of `.docx`** – В старом бинарном формате OLE‑поток отбрасывается, из‑за чего кнопка исчезает.  
- **Running on a headless server without Word installed** – Кнопка останется в файле, но вы не сможете её предварительно просмотреть без Word. Это нормально для автоматических конвейеров генерации.

---

## Next Steps – Extending the **create word document button** Workflow

Теперь, когда вы освоили основы, рассмотрите следующие идеи более высокого уровня:

- **Attach VBA macros** к кнопке для пользовательской бизнес‑логики.  
- **Generate multiple buttons** в цикле для динамических форм.  
- **Combine with Aspose.PDF** для экспорта того же документа в PDF, сохраняя визуальное расположение (кнопка в PDF будет статическим изображением).  
- **


## What Should You Learn Next?

Следующие руководства охватывают близкие темы, расширяющие техники, продемонстрированные в этом гиде. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, помогающими вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Создать документ Word с Aspose.Words для .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)  
- [Создать прямоугольную форму в Word с Aspose.Words – пошаговое руководство](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)  
- [Вставить встроенное изображение в документ Word с помощью Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}