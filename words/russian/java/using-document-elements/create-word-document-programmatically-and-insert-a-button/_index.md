---
category: general
date: 2026-09-21
description: Создайте документ Word программно и изучите, как сохранить кнопку сохранения
  документа Word, вставить кнопку команды Word и установить подпись кнопки команды
  с помощью DocumentBuilder.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: ru
lastmod: 2026-09-21
og_description: Создайте документ Word программно с помощью Aspose.Words. Узнайте,
  как добавить кнопку сохранения документа Word, вставить кнопку управления, задать
  подпись кнопки и использовать DocumentBuilder для интерактивных форм.
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: Создать документ Word программно и добавить кнопку
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Создать документ Word программно и вставить кнопку
url: /ru/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание Word‑документа программно и вставка кнопки

Если вам нужно **создавать Word‑документ программно**, Aspose.Words предоставляет удобный API, который позволяет добавлять интерактивные элементы управления, такие как CommandButton. В этом руководстве также объясняется **как использовать DocumentBuilder**, как **сохранить кнопку Word‑документа**, и как **установить подпись кнопки**, так, чтобы кнопка отображалась точно так, как вы ожидаете, внутри файла .docx.

Вы узнаете, как:

* Инициализировать пустой документ с помощью `Document`.
* Работать с `DocumentBuilder` для редактирования документа.
* Вставить **CommandButton** (`insert command button word`).
* Установить имя кнопки и видимую подпись (`set command button caption`).
* Сохранить результат на диск (`save word document button`).

Шаги написаны для разработчиков .NET, использующих C# и последнюю версию Aspose.Words for .NET (v24.10). Дополнительные пакеты NuGet не требуются, кроме Aspose.Words.

---

## Что вам понадобится перед началом

| Требование | Причина |
|------------|---------|
| Visual Studio 2022 (или любая IDE C#) | Для компиляции и запуска примера кода. |
| .NET 6.0 SDK или новее | Обеспечивает среду выполнения для примера. |
| Aspose.Words for .NET (v24.10 или новее) | Библиотека, позволяющая **создавать Word‑документ программно** и управлять элементами формы. |
| Базовое знакомство с C# и концепциями ООП | Необходимо для понимания потока кода. |

Вы можете установить Aspose.Words через NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Создание Word‑документа программно

Первый шаг — создать пустой объект `Document`. Этот объект представляет весь файл Word в памяти.

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

Создание документа программно дает вам чистый холст, на который можно добавлять абзацы, таблицы или интерактивные элементы управления.  

---

## Как использовать DocumentBuilder

`DocumentBuilder` — основной класс для редактирования `Document`. Он предоставляет методы для вставки текста, изображений и полей формы. В этом руководстве мы используем его для размещения CommandButton.

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder поддерживает внутренний курсор, указывающий текущее место вставки. По умолчанию он начинается в начале первой секции, что идеально подходит для нашего примера.

---

## Вставка CommandButton в Word

Aspose.Words рассматривает CommandButton как элемент управления ActiveX. Метод `InsertForms2OleControl` создает общий OLE‑контролл, который мы затем настраиваем как кнопку.

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

На данном этапе контролл существует в документе, но не имеет визуального представления, пока мы не определим его тип.

---

## Установка подписи кнопки

Теперь мы указываем OLE‑контроллу, что он должен вести себя как CommandButton, и задаём ему понятную метку.

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

Установка **подписи кнопки** является обязательной, поскольку Word отображает этот текст на поверхности кнопки. Если опустить `SetCaption`, кнопка будет отображаться с общим ярлыком.

---

## Сохранение Word‑документа с кнопкой

Наконец, сохраняем документ на диск. Метод `Save` записывает весь пакет Word, включая только что вставленную кнопку, в файл .docx.

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

Файл `CommandButton.docx` теперь содержит полностью функционирующую кнопку с меткой **Submit**. Когда пользователь открывает файл в Microsoft Word и нажимает кнопку, будет выполнено действие по умолчанию (которое позже можно привязать через VBA).

---

## Полный рабочий пример

Ниже представлен полный код программы, который вы можете скопировать, вставить и запустить. Он демонстрирует весь процесс от создания документа до сохранения кнопки.

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

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Ожидаемый результат**

* Файл с именем `CommandButton.docx`, расположенный по указанному вам пути.
* При открытии файла в Microsoft Word отображается одна кнопка **Submit** на первой странице.
* Кнопку можно выбрать, изменить её размер или привязать к макросу на вкладке **Developer** в Word.

---

## Часто задаваемые вопросы и обработка граничных случаев

| Вопрос | Ответ |
|--------|-------|
| *Что если мне нужно более одной кнопки?* | Повторите шаги 3–6 с разными именами и подписями. Каждая кнопка должна иметь уникальное значение `SetName`. |
| *Можно ли задать размер кнопки?* | Да. После вставки элемента управления вы можете изменить его свойства `Width` и `Height` через объект `OleFormat`. |
| *Будет ли кнопка работать во всех версиях Word?* | Элементы управления ActiveX поддерживаются в настольной версии Word (Windows). Они не отображаются в Word Online и на macOS. |
| *Как добавить обработчик клика?* | Необходимо написать VBA‑код, который ссылается на имя кнопки (`btnSubmit`). VBA‑макрос можно встроить с помощью `doc.VbaProject`. |
| *Что если нужно вставить кнопку в ячейку таблицы?* | Переместите курсор builder в нужную ячейку (`builder.MoveTo(cell.FirstParagraph)`) перед вызовом `InsertForms2OleControl`. |

---

## Профессиональные советы

* **Pro tip:** Всегда задавайте осмысленное имя с помощью `SetName`. Это упрощает автоматизацию VBA и облегчает отладку.
* **Watch out for:** Не забывайте вызывать `SetControlType`. Без этого вызова объект OLE отображается как общий заполнитель, а не как кликабельная кнопка.
* **Performance tip:** Если вы генерируете много документов в цикле, переиспользуйте один экземпляр `DocumentBuilder` и вызывайте `builder.MoveToDocumentEnd()` перед каждой вставкой, чтобы избежать лишних сбросов курсора.

---

## Следующие шаги

Теперь, когда вы знаете, как **создавать Word‑документ программно**, **вставлять CommandButton в Word**, **устанавливать подпись кнопки** и **сохранять Word‑документ с кнопкой**, вы можете изучать более продвинутые сценарии:

* Добавить элементы управления **TextFormField** для ввода пользователем.
* Скомбинировать кнопки с полями **MacroButton** для непосредственного выполнения VBA.
* Использовать **DocumentBuilder.InsertImage** для размещения иконок на ваших кнопках.
* Интегрировать с ASP.NET для генерации Word‑форм на

---

## Что вам следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}