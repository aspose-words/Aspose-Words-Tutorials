---
category: general
date: 2026-08-17
description: Вставьте пример OleControlType.CommandButton в Word с помощью Aspose.Words.
  Узнайте, как программно добавлять элементы управления формой в документ Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: ru
lastmod: 2026-08-17
og_description: Вставьте пример OleControlType.CommandButton в Word с помощью Aspose.Words.
  Следуйте этому руководству, чтобы добавить элементы управления формой в документ
  Word.
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: Вставить пример OleControlType.CommandButton в Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Вставить пример OleControlType.CommandButton в Word
url: /ru/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Вставка примера OleControlType.CommandButton в Word

Если вам нужно **insert OleControlType.CommandButton example** в файл Word, это руководство покажет, как это сделать. Вы узнаете **как добавить элементы управления формой в документ Word** с помощью Aspose.Words, с полным, исполняемым C#‑программой.

Элементы управления формы, такие как кнопки ActiveX, позволяют создавать интерактивные шаблоны Word — полезные для контрактов, опросников или внутренних инструментов. Ниже приведённые шаги охватывают всё от настройки проекта до проверки того, что кнопка отображается корректно в сохранённом файле `.docx`.

## Требования

- .NET 6.0 SDK или более поздняя версия, установленная  
- Visual Studio 2022 (или любой C# IDE)  
- Лицензия Aspose.Words для .NET или бесплатная временная лицензия  
- Базовое знакомство с C# и концепциями файлов Word  

> **Pro tip:** Если вы используете бесплатную пробную версию, поместите файл лицензии в ту же папку, что и исполняемый файл, и загрузите его в начале `Main`.

## Шаг 1: Создать новый консольный проект и добавить Aspose.Words

Open a terminal and run:

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

Это создаёт чистый проект и загружает последнюю версию пакета Aspose.Words, который предоставляет API `Document`, `DocumentBuilder` и `InsertForms2OleControl`, необходимые для **insert OleControlType.CommandButton example**.

## Шаг 2: Написать полную программу

Создайте или замените `Program.cs` следующим кодом. Он содержит все необходимые директивы `using`, загрузку лицензии и четырёхшаговый рабочий процесс, показанный в оригинальном фрагменте.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Почему важна каждая строка

* **License loading** – гарантирует, что вы не ограничены ограничениями оценки.  
* **`Document doc = new Document();`** – создаёт контейнер для всего содержимого Word; это основа **insert OleControlType.CommandButton example**.  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – предоставляет удобный API для добавления текста, изображений и элементов управления.  
* **`InsertForms2OleControl`** – основной метод, реализующий **how to add form controls to a Word document**. Значение перечисления `OleControlType.CommandButton` указывает Aspose.Words создать кнопку ActiveX.  
* **`new Rectangle(100, 100, 80, 30)`** – позиционирует кнопку на расстоянии 100 пт от левого и верхнего полей, ширина 80 пт и высота 30 пт. При необходимости скорректируйте эти значения под ваш макет.  
* **`doc.Save`** – сохраняет файл .docx на диск; файл теперь содержит встроенную кнопку.

## Шаг 3: Скомпилировать и запустить программу

From the project folder, execute:

```bash
dotnet run
```

You should see the console message:

```
Document saved to ActiveXButton.docx
```

Откройте `ActiveXButton.docx` в Microsoft Word. Вы увидите кнопку с надписью **ClickMe**, расположенную примерно в середине страницы. Нажатие на кнопку вызывает стандартное поведение ActiveX (обычно ничего не делает, если не привязать макрос).

![insert olecontroltype.commandbutton example – кнопка ActiveX CommandButton, отображённая в документе Word](/images/activex-button.png "ActiveX CommandButton, вставленный в документ Word")

## Шаг 4: Настройка кнопки (необязательно)

Базовый **insert OleControlType.CommandButton example** создаёт кнопку по умолчанию. Вы можете изменить её подпись, шрифт или даже привязать макрос, отредактировав базовый OLE‑объект. Ниже показан краткий способ изменить подпись кнопки после вставки:

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **Note:** Прямое изменение свойств OLE требует понимания базового COM‑интерфейса. В большинстве случаев подпись по умолчанию достаточна.

## Шаг 5: Распространённые проблемы и как их избежать

| Проблема | Почему происходит | Решение |
|----------|-------------------|---------|
| Кнопка не отображается в Word | Документ был сохранён как `.docx`, но открыт в просмотрщике, который удаляет OLE‑элементы (например, Google Docs). | Откройте файл в Microsoft Word или Word Online с правами редактирования. |
| Ошибка выполнения `ArgumentOutOfRangeException` | Координаты `Rectangle` находятся за пределами полей страницы. | Используйте значения внутри размеров страницы (например, 0‑500 для A4). |
| Исключение лицензии | Пробная лицензия истекает через 30 дней. | Загрузите действительный файл лицензии или запросите продленную пробную версию у Aspose. |

## Шаг 6: Как этот пример вписывается в более крупные проекты автоматизации

Когда вам нужно **how to add form controls to Word document** в больших объёмах — например, генерировать сотни шаблонов контрактов — оберните логику вставки в переиспользуемый метод:

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

Затем вы можете вызывать `AddCommandButton` внутри циклов, обрабатывающих строки данных, гарантируя, что каждый сгенерированный документ содержит кнопку с уникальным именем (например, `Approve_001`, `Approve_002`).

## Заключение

Теперь у вас есть полный **insert OleControlType.CommandButton example**, демонстрирующий **how to add form controls to a Word document** с помощью Aspose.Words для .NET. В руководстве рассмотрены настройка проекта, полный исходный код, советы по настройке и распространённые шаги по устранению неполадок.

Отсюда вы можете изучить:

- Добавление других типов элементов управления, таких как **CheckBox** или **ComboBox** (`OleControlType.CheckBox`, `OleControlType.ComboBox`).  
- Привязка кнопки к макросу VBA для более интерактивного поведения.  
- Создание PDF из того же документа с сохранением полей формы.

Экспериментируйте с различными размерами, позициями и именами элементов управления, чтобы они соответствовали вашему конкретному случаю использования. Приятного кодирования!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Вставка поля формы Combo Box в документ Word](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [Вставка поля формы Check Box в документ Word](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [Вставка поля формы Text Input в документ Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}