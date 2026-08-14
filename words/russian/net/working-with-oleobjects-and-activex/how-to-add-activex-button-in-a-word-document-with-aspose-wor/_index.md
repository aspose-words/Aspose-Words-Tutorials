---
category: general
date: 2026-08-14
description: Как добавить кнопку ActiveX в документ Word с помощью Aspose.Words –
  узнайте, как создать пустой документ Word и программно вставить кнопку ActiveX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: ru
lastmod: 2026-08-14
og_description: Как добавить кнопку ActiveX в документ Word с помощью Aspose.Words.
  Этот учебник показывает, как создать пустой документ Word, вставить кнопку ActiveX
  и сохранить результат.
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: Как добавить кнопку ActiveX в Word – руководство Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: Как добавить кнопку ActiveX в документ Word с помощью Aspose.Words
url: /ru/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как добавить кнопку ActiveX в документ Word с помощью Aspose.Words

Если вам нужно **добавить ActiveX**‑элементы управления в генерируемый файл Word, это руководство покажет точные шаги. Вы узнаете, как **программно вставить кнопку ActiveX**, начиная с **создания пустого документа Word** и заканчивая сохранением файла, который можно открыть в Microsoft Word.

Добавление кнопки, запускающей VBA‑код или макрос, является распространённой задачей для автоматических генераторов отчетов, шаблонов форм или интерактивных контрактов. Использование Aspose.Words для .NET позволяет создавать документ без запуска Office, что делает процесс быстрым и удобным для серверов.

## Требования

Прежде чем начать, убедитесь, что у вас есть:

* SDK .NET 6.0 (или новее) установлен.
* Visual Studio 2022 или любая IDE, поддерживающая C#.
* NuGet‑пакет Aspose.Words for .NET (`Aspose.Words` версии 24.9 или новее).  
  Установите его с помощью:
  ```bash
  dotnet add package Aspose.Words
  ```
* Windows‑окружение, если вы планируете тестировать кнопку ActiveX, поскольку элементы управления ActiveX требуют Windows‑версии Microsoft Word.

## Шаг 1: Создать пустой документ Word

Первая задача — **создать пустой документ Word** в памяти. Aspose.Words предоставляет класс `Document` для этой цели.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` представляет весь файл .docx. На данном этапе документ не содержит страниц, но вы можете сразу начинать добавлять содержимое.

## Шаг 2: Инициализировать DocumentBuilder

`DocumentBuilder` — вспомогательный класс, позволяющий вставлять текст, изображения и другие объекты в документ. Он работает с экземпляром `Document`, который вы только что создали.

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder поддерживает позицию курсора; всё, что вы вставляете после этой строки, появляется в начале первой страницы.

## Шаг 3: Вставить элемент управления ActiveX CommandButton

Aspose.Words предоставляет метод `InsertForms2OleControl` для добавления устаревших элементов формы, включая ActiveX. Метод требует тип элемента управления и его размер в пунктах.

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

Возвращаемый объект `Forms2OleControl` позволяет настроить свойства, такие как имя и подпись элемента управления.

## Шаг 4: Настроить свойства кнопки

Установка осмысленного `Name` позволяет позже ссылаться на элемент из VBA‑кода. `Caption` — это текст, который пользователь видит на кнопке.

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **Pro tip:** Делайте имя коротким и буквенно-цифровым; Word отклонит имена, содержащие пробелы или специальные символы.

## Шаг 5: Сохранить документ

Наконец, запишите документ на диск. Используйте расширение `.docx` для современных файлов Word; кнопка ActiveX работает аналогично в файлах `.doc`, но `.docx` является предпочтительным форматом для новых проектов.

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

Когда вы откроете `ActiveXButton.docx` в Microsoft Word, вы увидите кликабельную кнопку **Submit**. Если включить макросы, вы можете привязать VBA‑код к `btnSubmit_Click`, и он выполнится при нажатии пользователем кнопки.

## Полный, исполняемый пример

Собрав все части вместе, вы получаете автономную программу, которую можно скопировать, вставить и запустить.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Ожидаемый результат** – После запуска программы консоль выводит путь сохранения, а открытый в Word сгенерированный файл показывает кнопку с подписью **Submit**, расположенную в верхней части первой страницы.

## Обработка часто задаваемых вопросов и граничных случаев

### Работает ли кнопка во всех версиях Word?

Элементы управления ActiveX поддерживаются в настольной версии Word на Windows. Они не отображаются в Word Online, Word для macOS или мобильных клиентах. Если нужна кроссплатформенная интерактивность, рассмотрите использование контент‑контролов или решений на основе HTML.

### Что делать, если нужен другой размер или позиция?

`InsertForms2OleControl` размещает элемент управления в текущем месте курсора builder’а. Чтобы переместить его, скорректируйте курсор с помощью `builder.MoveTo` перед вставкой или измените свойства `Left` и `Top` у элемента после создания:

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### Можно ли добавить другие типы ActiveX?

Да. Перечисление `Forms2OleControlType` включает `CheckBox`, `OptionButton`, `ListBox` и другие. Замените `CommandButton` нужным значением перечисления и настройте свойства соответственно.

### Требуется ли макрос, чтобы кнопка что‑то делала?

Сама кнопка ничего не делает, пока вы не привяжете к ней VBA‑код. В Word нажмите **Alt+F11**, откройте редактор VBA, найдите `btnSubmit_Click` и напишите необходимую логику. Сгенерированный документ сохранит проект VBA, если вы используете формат **SaveFormat.Doc** (устаревший `.doc`), но файлы `.docx` не могут хранить макросы VBA. Используйте формат `.doc`, если нужен встроенный VBA.

## Заключение

Теперь вы знаете, **как добавить ActiveX**‑элементы управления в файл Word с помощью Aspose.Words. Следуя шагам по **созданию пустого документа Word**, инициализации `DocumentBuilder`, **вставке кнопки ActiveX**, настройке её свойств и сохранению файла, вы можете генерировать интерактивные шаблоны Word напрямую из вашего кода .NET.

Далее изучайте связанные темы, такие как обработка событий **insert ActiveX button**, добавление **create word document aspose** для таблиц или изображений, а также защита документов с макросами для корпоративного развертывания. Экспериментируйте с различными типами элементов управления и вариантами их расположения, чтобы адаптировать пользовательский опыт под нужды вашего приложения.

Удачной разработки!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Создать документ Word с верхним и нижним колонтитулом с помощью Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Создать групповую форму в документе Word с помощью Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Создать документ Word с таблицей с помощью Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}