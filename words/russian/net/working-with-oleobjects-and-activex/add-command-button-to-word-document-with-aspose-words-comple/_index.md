---
category: general
date: 2026-07-29
description: Добавьте кнопку команды в документ Word с помощью Aspose.Words. Узнайте,
  как установить свойства ActiveX‑контрола и задать подпись кнопки команды за несколько
  простых шагов.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: ru
lastmod: 2026-07-29
og_description: Добавьте кнопку команды в документ Word с помощью Aspose.Words. Этот
  учебник показывает, как быстро установить свойства ActiveX‑контрола и задать подпись
  кнопки команды.
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: Добавить кнопку команды в документ Word – пошаговое руководство Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Добавление кнопки команды в документ Word с помощью Aspose.Words — Полное руководство
url: /ru/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Добавить кнопку команды в документ Word – Полный программный обзор

Когда‑то вам нужно было **добавить кнопку команды в документ Word**, но вы не знали, какие вызовы API использовать? Вы не одиноки; многие разработчики сталкиваются с этой проблемой, когда впервые пытаются внедрить интерактивные элементы в файл DOCX. Хорошая новость в том, что Aspose.Words делает это удивительно просто. В этом руководстве мы пройдёмся по созданию ActiveX‑контрола CommandButton, **установим свойства ActiveX‑контрола** и **задать подпись кнопки команды** — всё с чистым C#‑кодом, который вы можете скопировать‑вставить прямо сейчас.

К концу этого урока у вас будет полностью рабочий файл Word, содержащий кликабельную кнопку «Submit», готовую к открытию в Microsoft Word. Никаких внешних VBA‑скриптов, никакой ручной настройки UI — только чистое программное управление.

## Что вы узнаете

* Как создать пустой документ Word и `DocumentBuilder`.
* Точный вызов метода для **добавления кнопки команды в документ Word** с помощью Aspose.Words.
* Способы **установки свойств ActiveX‑контрола**, таких как размер, позиция и имя.
* Правильную технику **задания подписи кнопки команды**, чтобы кнопка отображала именно то, что вам нужно.
* Советы по обработке крайних случаев, таких как разные типы кнопок, масштабирование DPI и совместимость с версиями Word.

> **Требования:** Visual Studio (или любой IDE для C#) с установленным Aspose.Words для .NET (пакет NuGet `Aspose.Words`). Предыдущий опыт работы с ActiveX не требуется.

---

## Шаг 1: Настройка проекта и импорт пространств имён

Прежде чем мы сможем **добавить кнопку команды в документ Word**, нам нужен проект C#, который ссылается на Aspose.Words. Создайте новое консольное приложение .NET, затем добавьте пакет NuGet:

```bash
dotnet add package Aspose.Words
```

Теперь подключим необходимые пространства имён в ваш файл исходного кода:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

Эти три директивы `using` дают вам доступ к классам `Document`, `DocumentBuilder` и `Forms2OleControl`, которые отвечают за вставку ActiveX‑элементов.

*Совет:* Если вы используете Visual Studio, IDE автоматически предложит добавить эти директивы, когда вы начнёте вводить имена классов.

---

## Шаг 2: Создание пустого документа и билдера

Свежий объект `Document` представляет пустой файл Word. `DocumentBuilder` — наш удобный «перо», позволяющее рисовать, вставлять текст и, что особенно важно, размещать ActiveX‑контролы.

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

На данном этапе документ — просто чистый холст, как чистый лист бумаги, ожидающий вашу кнопку команды.

---

## Шаг 3: Вставка ActiveX‑контрола CommandButton

Теперь мы наконец **добавляем кнопку команды в документ Word**. Aspose.Words предоставляет метод `InsertForms2OleControl`, который принимает тип контрола и его размеры. Мы используем `Forms2OleControlType.CommandButton` и задаём удобную ширину 150 пунктов и высоту 30 пунктов.

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

Метод возвращает экземпляр `Forms2OleControl`, который мы будем использовать для **установки свойств ActiveX‑контрола** на следующем шаге.

---

## Шаг 4: Настройка контрола — имя, подпись и позиция

### Установка подписи

Подпись — это текст, отображаемый непосредственно на кнопке. Чтобы **задать подпись кнопки команды**, просто присвойте строку свойству `Caption`:

```csharp
commandButton.Caption = "Submit";
```

Вы можете заменить `"Submit"` на любой другой текст — «Save», «Export», «Launch» и т.д., — и Word отобразит именно его.

### Присвоение имени контролу

Присвоение контролу осмысленного имени упрощает последующее обращение к нему (например, при автоматизации макросов Word). Установим свойство `Name`:

```csharp
commandButton.Name = "btnSubmit";
```

### Позиционирование на странице

Word использует пункты (1/72 дюйма) для разметки. Отрегулируйте свойства `Left` и `Top`, чтобы разместить кнопку там, где вам нужно:

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

Если требуется выровнять кнопку относительно абзаца, сначала переместите курсор билдера, а затем вставьте контрол; координаты будут относительными к текущему положению курсора.

*Крайний случай:* На мониторах с высоким DPI визуальный размер может немного отличаться в Word. Чтобы сохранить физический размер кнопки одинаковым на разных устройствах, вычисляйте пункты исходя из целевого DPI (обычно 96 DPI для Word).

---

## Шаг 5: Сохранение документа

После полной настройки кнопки сохранение файла сводится к одной строке:

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

Полученный `CommandButton.docx` содержит полностью рабочую ActiveX‑кнопку. Откройте его в Microsoft Word, и вы увидите кнопку «Submit», расположенную точно там, где вы её разместили.

### Ожидаемый результат

1. Документ Word открывается одной страницей.  
2. Прямоугольная кнопка с надписью **Submit** появляется в указанных координатах.  
3. При правом клике по кнопке и выборе **Properties** вы увидите имя `btnSubmit` и другие заданные свойства.

---

## Шаг 6: Расширенные варианты и распространённые подводные камни

### Вставка других типов ActiveX

Метод `InsertForms2OleControl` не ограничивается только кнопками команды. Вы можете внедрять флажки, переключатели или даже пользовательские ActiveX‑объекты:

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

Тот же шаблон **установки свойств ActiveX‑контрола** применяется — просто замените тип в перечислении.

### Работа с разными версиями Word

Старые версии Word (до 2007) используют бинарный формат `.doc`, в котором ActiveX‑контролы хранятся иначе. Aspose.Words автоматически преобразует контрол при сохранении в `.doc`, но некоторые свойства (например, точное позиционирование) могут сместиться. Если вы нацелены на устаревшие форматы, протестируйте результат в конкретной версии Word.

### Настройки безопасности

Word может отключать ActiveX‑контролы на компьютерах с жёсткой политикой безопасности макросов. Чтобы избежать диалогового окна «Security Warning», рассмотрите следующие варианты:

* Подписать документ доверенным сертификатом.  
* Инструктировать пользователей включать содержимое ActiveX для данного расположения файла.  
* Использовать альтернативу без макросов (например, обычные элементы управления содержимым), если безопасность является критичным фактором.

---

## Шаг 7: Полный рабочий пример

Ниже представлена полностью готовая к запуску программа, включающая все обсуждаемые шаги. Скопируйте её в `Program.cs`, при необходимости измените путь вывода и нажмите **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**Что делает этот код:**

* Создаёт новый документ.  
* Вставляет кнопку команды, **устанавливает свойства ActiveX‑контрола** и **задает подпись кнопки команды**.  
* Добавляет короткий пояснительный абзац.  
* Сохраняет файл как `CommandButton.docx`.

Запустите программу, откройте сгенерированный файл, и вы увидите кнопку под пояснительным текстом.

---

## Заключение

Мы продемонстрировали, как **добавить кнопку команды в документ Word** с помощью Aspose.Words, как **установить свойства ActiveX‑контрола** и как **задать подпись кнопки команды** — всё в лаконичном, готовом к использованию фрагменте C#. Подход масштабируем: меняйте тип контрола, подгоняйте размеры или перебирайте источник данных, чтобы автоматически вставлять десятки кнопок.

Хотите пойти дальше? Попробуйте:

* Привязать кнопку к макросу, который экспортирует данные.  
* Добавить изображения или пользовательские иконки в кнопку через свойство `Picture`.  
* Построить полноценную форму с несколькими ActiveX‑элементами (текстовые поля, комбобоксы и т.д.).

Эксперименты — лучший способ овладеть автоматизацией Word. Если возникнут проблемы, проверьте расчёты DPI и настройки безопасности Word. Приятного кодинга, и пусть ваши документы становятся всё более интерактивными!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}