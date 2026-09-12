---
category: general
date: 2026-09-11
description: Узнайте, как создавать forms2olecontrol в коде с помощью Aspose.Words DocumentBuilder.
  Это пошаговое руководство охватывает вставку ActiveX‑кнопки‑команды, использование setOleClassName и
  настройку размеров.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: ru
lastmod: 2026-09-11
og_description: Создайте forms2olecontrol в коде с помощью Aspose.Words. Следуйте
  этому руководству, чтобы вставить кнопку ActiveX, задать её имя класса и отрегулировать
  её размер.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: Создание forms2olecontrol в коде – полное руководство по Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Как создать forms2olecontrol в коде с помощью Aspose.Words
url: /ru/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать forms2olecontrol в коде с помощью Aspose.Words

Если вам нужно **создать forms2olecontrol в коде**, это руководство покажет, как сделать это с использованием API Aspose.Words .NET. Независимо от того, автоматизируете ли вы шаблон, требующий кнопки ActiveX command button, или просто хотите программно обогатить документ Word, нижеописанные шаги охватывают всё — от вставки элемента управления до настройки его внешнего вида.

В этом учебнике вы узнаете, как использовать **Aspose.Words DocumentBuilder** для вставки **ActiveX command button**, задать его класс с помощью **setOleClassName method** и отрегулировать **Forms2OleControl size**. Никакие внешние инструменты не требуются — только среда разработки .NET и библиотека Aspose.Words.

## Prerequisites

Перед началом убедитесь, что у вас есть:

* .NET 6.0 или новее установлен (код также работает с .NET Framework 4.7+)
* Последняя версия пакета NuGet Aspose.Words для .NET
* Базовые знания C# и концепции ActiveX‑элементов управления в документах Word

Если чего‑то не хватает, установите пакет NuGet с помощью:

```bash
dotnet add package Aspose.Words
```

## What this tutorial covers

* Создание экземпляра `DocumentBuilder`
* Вставка `Forms2OleControl` (базовый объект для кнопки ActiveX command button)
* Назначение правильного имени класса с помощью `setOleClassName`
* Установка визуальной ширины и высоты с помощью свойств **Forms2OleControl size**
* Сохранение документа и проверка результата

К концу руководства у вас будет полностью функционирующий файл Word, содержащий кликабельную кнопку, которую можно дополнительно настроить или привязать к макросам VBA.

---

## How to create forms2olecontrol in code – step‑by‑step

### Step 1: Initialise the DocumentBuilder

Класс `DocumentBuilder` является точкой входа для большинства задач генерации документов в Aspose.Words. Он предоставляет методы для добавления текста, изображений, таблиц и, что особенно важно для этого урока, OLE‑элементов управления.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Почему это важно:**  
`DocumentBuilder` поддерживает текущую позицию курсора внутри документа. Создав его заранее, вы гарантируете, что любые последующие вставки — например, **ActiveX command button** — появятся точно там, где вам нужно.

### Step 2: Insert the Forms2OleControl

Метод `insertForms2OleControl` возвращает объект `Forms2OleControl`. Этот объект представляет собой заполнитель OLE‑элемента, который Word отобразит как кнопку ActiveX.

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**Почему это важно:**  
Без этого вызова вы не сможете управлять свойствами элемента. Возвращённый `Forms2OleControl` даёт полный доступ к **setOleClassName method**, атрибутам размеров и другим настройкам, специфичным для OLE.

### Step 3: Specify the ActiveX class with setOleClassName

Word должен знать, какой тип ActiveX‑элемента отобразить. Имя класса для стандартной кнопки команд — `"Forms.CommandButton.1"`.

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**Почему это важно:**  
Метод `setOleClassName` связывает общий OLE‑заполнитель с конкретной **ActiveX command button**. Использование неверного имени класса приводит к появлению пустого объекта или ошибке выполнения при открытии документа.

### Step 4: Adjust the Forms2OleControl size

Кнопка, слишком маленькая или слишком большая, выглядит непрофессионально. Вы можете управлять её размерами с помощью `setWidth` и `setHeight`.

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**Почему это важно:**  
Эти свойства образуют **Forms2OleControl size**. Они влияют на то, как кнопка выглядит в интерфейсе Word, и гарантируют, что прикреплённый макрос имеет достаточную область для клика.

### Step 5: Save the document and test

После настройки элемента сохраните документ в выбранное вами место.

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

Откройте `ActiveXButton.docx` в Microsoft Word. Вы должны увидеть кнопку с подписью «CommandButton1» (подпись по умолчанию). При нажатии ничего не произойдёт, если вы не добавите макрос VBA, но сам элемент полностью функционирует.

**Ожидаемый результат:**  

![Документ Word с вставленной кнопкой ActiveX](/images/activeX-button.png "Скриншот документа Word, показывающий недавно созданную кнопку ActiveX, вставленную через код")

*Текст alt‑изображения содержит основной ключевой запрос для доступности и SEO.*

---

## Understanding the ActiveX Forms2OleControl class

Класс `Forms2OleControl` оборачивает низкоуровневую инфраструктуру OLE, которую Word использует для ActiveX‑элементов. Он наследуется от `Shape`, что означает возможность применения типичного форматирования фигур (например, границы, вращение), если это необходимо.

* **ActiveX command button** – Наиболее распространённый сценарий; её можно привязать к макросу через инструменты разработчика Word.  
* **setOleClassName method** – Определяет, какой COM‑класс загрузит Word; другими допустимыми значениями являются `"Forms.TextBox.1"` и `"Forms.ComboBox.1"`.  
* **Forms2OleControl size** – Управляется через `SetWidth`/`SetHeight`. Эти методы принимают значения в пунктах (1 pt = 1/72 in).

### When to use Forms2OleControl vs. Content Controls

Если вам нужен лишь простой ввод данных (например, обычное текстовое поле), встроенные в Word элементы управления контентом легче по весу. Используйте `Forms2OleControl`, когда требуется полная функциональность ActiveX, такая как обработка событий или взаимодействие с пользовательским VBA.

---

## Setting additional properties (optional)

Хотя основные шаги достаточны для **создания forms2olecontrol в коде**, часто требуется тонко настроить внешний вид или поведение кнопки.

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**Почему это важно:**  
`SetOleData` позволяет записывать произвольные значения свойств напрямую в OLE‑поток. Это самый гибкий способ кастомизировать **ActiveX command button** без обращения к VBA.

---

## Common pitfalls and troubleshooting

| Симптом | Вероятная причина | Решение |
|--------|-------------------|---------|
| Кнопка отображается как серый квадрат | Неправильное имя класса, переданное в `setOleClassName` | Убедитесь, что строка точно `"Forms.CommandButton.1"` (учитывая регистр) |
| Размер не меняется | Ширина/высота заданы до вставки элемента | Всегда вызывайте `SetWidth`/`SetHeight` **после** `InsertForms2OleControl` |
| При открытии документа появляется ошибка «OLE object not found» | Отсутствует лицензия Aspose.Words (оценочная версия может ограничивать OLE) | Примените действующую лицензию или используйте бесплатную пробную версию с полной поддержкой OLE |
| Подпись кнопки остаётся «CommandButton1» | `SetOleData` не использован или макрос не читает свойство | Используйте VBA‑макрос для чтения свойства `"Caption"` или задайте подпись через интерфейс Word |

---

## Full, runnable example

Ниже приведено полное консольное приложение, которое можно скопировать, вставить и запустить. Оно демонстрирует всё, что было покрыто в этом руководстве.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Объяснение каждой части**

* **Using directives** – Подключают пространство имён Aspose.Words, необходимое для `Document`, `DocumentBuilder` и `Forms2OleControl`.  
* **Document creation** – Создаёт пустой файл Word.  
* **InsertForms2OleControl** – Размещает OLE‑элемент в текущей позиции курсора builder’а.  
* **SetOleClassName** – Информирует Word, что элемент — **ActiveX command button**.  
* **SetWidth / SetHeight** – Регулируют **Forms2OleControl size** для профессионального вида.  
* **SetOleData (optional)** – Показано, как записать дополнительные свойства, например подпись.  
* **Save** – Записывает готовый файл `.docx` на диск.

Запустите программу (`dotnet run`) и откройте `ActiveXButton.docx`. Вы увидите кнопку, к которой позже можно привязать макрос.

---

## Conclusion

Теперь вы знаете, как **создать forms2olecontrol в коде** с помощью Aspose.Words, начиная с инициализации `DocumentBuilder` и заканчивая настройкой **ActiveX command button** через `setOleClassName` и управлением её **Forms2OleControl size**. Такой подход позволяет автоматизировать сложные документы Word, встраивать интерактивные элементы UI и держать всю логику внутри приложения.

## What Should You Learn Next?

Следующие учебные материалы охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Как создавать поля формы и добавлять контент с помощью DocumentBuilder в Aspose.Words для Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Создание групповой фигуры в документе Word с использованием Aspose.Words для .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Создание прямоугольной фигуры в Word с Aspose.Words — пошаговое руководство](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}