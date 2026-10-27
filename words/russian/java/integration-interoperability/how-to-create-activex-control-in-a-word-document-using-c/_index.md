---
category: general
date: 2026-08-20
description: Узнайте, как создать ActiveX‑элемент, задать размер кнопки и добавить
  кнопку в Word с полным примером на C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: ru
lastmod: 2026-08-20
og_description: Создайте элемент управления ActiveX в файле Word с помощью C#. Этот
  учебник показывает, как задать размер кнопки, добавить кнопку в Word и сделать её
  кликабельной.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: Создание ActiveX‑контрола в Word – пошаговое руководство на C#
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: Как создать элемент управления ActiveX в документе Word с помощью C#
url: /ru/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать элемент управления ActiveX в документе Word с помощью C#

Если вам нужно **создать элемент управления ActiveX** внутри файла Microsoft Word, это руководство покажет, как это сделать. Вы увидите, как **добавить кнопку в Word**, задать её размеры и сделать элемент кликабельным — всё с помощью небольшого, автономного C#‑приложения.

В этом уроке вы:

* Поймёте, почему элемент управления ActiveX полезен для интерактивных документов Word.  
* Узнаете точный код, необходимый для **установки размера кнопки** и задания подписи.  
* Посмотрите, как **создать кликабельную кнопку**, которую позже можно привязать к макросу или внешней логике.  

Шаги работают с Aspose.Words .NET 23.12 или новее и требуют только среды разработки .NET.

> **Prerequisite** – У вас есть действующая лицензия Aspose.Words (или вы используете оценочную версию) и Visual Studio 2022 или любой другой C# IDE.

---

## Как создать элемент управления ActiveX в документе Word

Первый шаг — создать пустой `Document` и `DocumentBuilder`. Builder предоставляет высокоуровневый API для вставки объектов, таких как элементы управления ActiveX.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

Метод `InsertActiveXButton` (определён ниже) содержит логику **как вставить кнопку** и настроить её.

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

Запуск программы создаёт **ActiveXButton.docx**. Открытие файла в Word показывает кнопку с надписью **Submit**. Элемент полностью функционален — при нажатии будет вызван стандартный событие `CommandButton_Click`, которое позже можно привязать к VBA‑макросу.

### Почему это работает

* `InsertForms2OleControl` указывает Word встроить OLE‑объект типа **CommandButton**, класс классической кнопки ActiveX.  
* Параметры ширины и высоты напрямую **устанавливают размер кнопки**; Word переводит значения из пунктов (1 pt ≈ 1/72 in).  
* Присвоение имени элементу (`Name = "btnSubmit"`) упрощает его поиск из VBA (`ActiveDocument.InlineShapes("btnSubmit")`).  

---

## Установить размер кнопки и подпись

Если нужен иной внешний вид, измените числовые аргументы в вызове `InsertForms2OleControl`. Сигнатура метода выглядит так:

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – Программный идентификатор класса ActiveX (`"CommandButton"` для стандартной кнопки).  
* **width / height** – Размер в пунктах. Для кнопки шириной 2 см используйте `width = 56.7` (2 см ≈ 56.7 pt).  

Подпись можно изменить после вставки:

```csharp
commandButton.Caption = "Send Request";
```

Изменение подписи не влияет на размер, но меняет визуальную обратную связь для пользователя.

### Pro tip

Если нужна квадратная кнопка, задайте одинаковые значения обеим сторонам:

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## Добавить кнопку в Word и сделать её кликабельной

Приведённый выше код уже **добавляет кнопку в Word**. Чтобы кнопка выполняла действие, необходимо написать VBA‑макрос, обрабатывающий событие `Click`. Ниже минимальный макрос, который можно вставить в редактор VBA Word (`Alt+F11` → Insert → Module):

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

Поскольку элемент называется `btnSubmit`, Word автоматически сопоставляет событие `Click` с `btnSubmit_Click`. Это стандартный способ **создать кликабельную кнопку** без внешних библиотек.

> **Note:** Параметры безопасности макросов в Word могут блокировать элементы управления ActiveX. Убедитесь, что выбран режим «Enable all macros» или «Enable VBA macros», либо подпишите макрос цифровой подписью для использования в продакшене.

---

## Часто задаваемые вопросы: как вставить кнопку и устранить проблемы

### 1. Что делать, если кнопка не появляется после сохранения?

* Убедитесь, что версия Aspose.Words поддерживает `InsertForms2OleControl`. В версиях до 22.5 эта возможность отсутствует.  
* Проверьте, что целевой формат файла — `.docx` или `.doc`. Старые форматы, такие как `.rtf`, не могут хранить объекты ActiveX.

### 2. Можно ли вставить кнопку в конкретную закладку?

Да. Переместите builder к закладке перед вызовом `InsertForms2OleControl`:

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. Как **установить размер кнопки** динамически в зависимости от длины текста?

Вычислите требуемую ширину с помощью метода `Graphics.MeasureString` (из `System.Drawing`) и преобразуйте пиксели в пункты (`points = pixels * 72 / DPI`). Затем передайте полученную ширину в `InsertForms2OleControl`.

### 4. Есть ли способ добавить несколько кнопок в цикле?

Конечно. Оберните логику вставки в `for`‑цикл и корректируйте свойства `Left` и `Top` для каждой итерации:

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## Ожидаемый результат

После запуска программы и открытия **ActiveXButton.docx**:

* На первой странице в левом верхнем углу появляется одна кнопка **Submit**.  
* Размер кнопки соответствует указанным вами параметрам (`100 pt × 30 pt`).  
* Если вы добавили VBA‑макрос, при нажатии на кнопку появится сообщение: “You clicked the Submit button!”.

Вы успешно **создали элемент управления ActiveX**, **установили размер кнопки** и **добавили кнопку в Word**, а также изучили, как **вставлять кнопку** и **создавать кликабельную кнопку** для будущих задач автоматизации.

---

## Заключение

В этом уроке вы узнали, как **создать элемент управления ActiveX** внутри документа Word с помощью C#. Следуя инструкциям, вы сможете **установить размер кнопки**, задать элементу осмысленное имя и **добавить кнопку в Word**, сделав её **кликабельной** и привязанной к VBA‑макросу.  

Дальше вы можете исследовать:

* Привязку кнопки к .NET COM‑надстройке вместо VBA.  
* Использование других классов ActiveX, таких как `CheckBox` или `ComboBox`.  
* Автоматизацию создания полноценных форм с множеством элементов управления.

Не стесняйтесь экспериментировать с различными размерами


## Что вам следует изучить дальше?


Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Создать документ Word с плавающим изображением в .NET](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Создать документ Word с верхним и нижним колонтитулом с помощью Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Создать доступный PDF из Word – Полное руководство](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}