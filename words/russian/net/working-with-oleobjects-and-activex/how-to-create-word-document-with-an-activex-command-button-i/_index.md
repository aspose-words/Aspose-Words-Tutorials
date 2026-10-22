---
category: general
date: 2026-09-05
description: Создайте документ Word с помощью Aspose.Words C# и узнайте, как вставить
  кнопку ActiveX, задать её размер и добавить интерактивную функциональность.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: ru
lastmod: 2026-09-05
og_description: Создайте документ Word на C# и вставьте кнопку ActiveX. Этот учебник
  показывает, как задать размер кнопки и добавить интерактивные функции.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: Создание документа Word с кнопкой ActiveX в C# – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: Как создать документ Word с кнопкой ActiveX в C#
url: /ru/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать документ Word с кнопкой команд ActiveX в C#

Если вам нужно **создать документ Word** программно и встроить кликабельный элемент UI, это руководство покажет вам, как это сделать. С помощью Aspose.Words for .NET вы можете **создать документ Word**, **добавить кнопку команд**, и управлять её внешним видом — без открытия Microsoft Word.

Вы узнаете, как **вставлять ActiveX** элементы управления, **устанавливать размер кнопки**, и заставить кнопку вести себя как интерактивный UI‑компонент. Предыдущий опыт работы с COM или VBA не требуется; достаточно среды разработки .NET и библиотеки Aspose.Words.

## Что вы достигнете

К концу этого руководства вы сможете:

* **Создать документ Word** с нуля с помощью C#.
* **Вставить кнопку команд ActiveX** (классический элемент управления “Click Me”).
* **Установить размер кнопки** и точно задать её позицию.
* При желании добавить простую **интерактивную кнопку** логику (например, заполнить макросом).
* Сохранить файл как `.docx`, который можно открыть в Microsoft Word или любом совместимом просмотрщике.

### Предварительные требования

| Требование | Причина |
|-------------|--------|
| .NET 6.0 или новее | Обеспечивает среду выполнения для кода C#. |
| Aspose.Words for .NET (latest version) | Предоставляет API `Document`, `DocumentBuilder` и `Forms2OleControl`, используемые в примере. |
| Visual Studio 2022 (or any C# IDE) | Упрощает компиляцию и запуск примера. |
| Basic C# knowledge | Необходимо для понимания потока кода. |

> **Совет:** Если вы используете пробную версию Aspose.Words, убедитесь, что установили лицензию перед запуском кода, чтобы избежать водяных знаков оценки.

## Как создать документ Word – общий рабочий процесс

Процесс состоит из четырёх логических шагов:

1. **Инициализировать новый документ** и `DocumentBuilder` для его редактирования.  
2. **Вставить кнопку команд ActiveX** с помощью `InsertForms2OleControl`.  
3. **Настроить кнопку** – подпись, размер и позицию.  
4. **Сохранить** документ на диск.

Каждый шаг подробно описан в соответствующем разделе ниже.

![Документ Word с кнопкой ActiveX](/images/activex-button.png "Скриншот документа Word, содержащего кнопку команд ActiveX, созданную с помощью C#")

## Как вставить кнопку команд ActiveX

Часть **how to insert activex** начинается с метода `InsertForms2OleControl`. Этот метод создаёт COM‑базированный элемент управления, который Word воспринимает как объект ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**Почему это работает:** `OleControlType.CommandButton` сообщает Aspose.Words создать классическую кнопку в стиле VB. Размер и расположение задаются в пунктах (1 пункт = 1/72 дюйма), что обеспечивает точный контроль над разметкой.

## Как добавить кнопку команд и задать размер кнопки

После вставки элемента управления вы можете скорректировать его визуальные свойства. Шаг **add command button** также охватывает **set button size**.

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**Объяснение:**  

* `Caption` – подпись, отображаемая на кнопке.  
* `Width` и `Height` позволяют **задать размер кнопки** после первоначальной вставки – удобно, когда размер зависит от данных во время выполнения.  
* `Left` и `Top` перемещают элемент управления без необходимости пересоздавать документ.

> **Распространённая ошибка:** Использование пикселей вместо пунктов приведёт к тому, что кнопка будет слишком маленькой или большой. Всегда преобразуйте значения пикселей (`px * 72 / DPI`), если вы начинаете с измерений экрана.

## Как добавить интерактивную кнопку (опционально)

Кнопка ActiveX может выполнять макрос при щелчке, но внедрение VBA‑кода из C# выходит за рамки чистого рабочего процесса Aspose.Words. Вместо этого можно добавить свойство‑заполнитель, которое Word распознает как имя макроса.

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

Когда пользователь откроет сгенерированный `.docx` в Word, щелчок по кнопке попытается выполнить `MyMacroName`. Если макрос не существует, Word предложит создать его.

**Почему это может понадобиться:** Для корпоративных форм, где макрос заполняет поля, C#‑код лишь размещает кнопку; логика макроса находится в VBA‑проекте документа.

## Сохранить документ и проверить результат

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**Ожидаемый результат:** При открытии `CommandButton.docx` в Microsoft Word отображается кнопка с подписью **Click Me**, расположенная на 100 пт от левого поля и 120 пт от верхнего поля. Размеры кнопки – **200 пт × 80 пт**. Щелчок по кнопке запускает заполнитель макроса (если он присутствует).

## Полный рабочий пример

Ниже приведена полная, исполняемая программа, объединяющая всё вместе. Скопируйте её в новый проект Console App, добавьте пакет Aspose.Words через NuGet и запустите.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Запустите программу, затем откройте сгенерированный файл. Вы увидите **интерактивную кнопку**, готовую к дальнейшей настройке.

## Часто задаваемые вопросы

| Вопрос | Ответ |
|----------|--------|
| **Работает ли это с .NET Core?** | Да. Aspose.Words поддерживает .NET Standard, поэтому тот же код работает на .NET 5/6/7. |
| **Могу ли я использовать другие элементы управления ActiveX (например, CheckBox)?** | Конечно. Замените `OleControlType.CommandButton` на `OleControlType.CheckBox`, `OleControlType.OptionButton` и т.д. |
| **Что делать, если нужна более крупная кнопка на альбомной странице?** | Пропорционально скорректируйте свойства `Width`, `Height`, `Left` и `Top`. Помните, что пункты остаются теми же независимо от ориентации страницы. |
| **Нужен ли макрос, чтобы кнопка была кликабельной?** | Нет. Кнопка полностью функционирует как элемент UI; макрос добавляет только пользовательское поведение при щелчке. |

## Заключение

Теперь вы знаете, как **создать документ Word** с помощью Aspose.Words, **добавить кнопку команд**, **задать размер кнопки** и при желании связать кнопку с макросом для поведения **add interactive button**. Такой подход позволяет автоматизировать создание форм, генерировать динамические отчёты или создавать прототипы UI на базе Word непосредственно из C#.

Далее вы можете изучить:

* **Как вставить флажки ActiveX** для опросных форм.  
* **Как добавить богатый текст вокруг кнопки** с помощью `DocumentBuilder`.  
* **Как защитить документ**, оставив кнопку рабочей.  

Не стесняйтесь экспериментировать с различными типами элементов управления, размерами и именами макросов, чтобы подобрать оптимальное решение для вашего сценария. Happy coding!

## Что следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}