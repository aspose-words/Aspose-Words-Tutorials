---
category: general
date: 2026-08-07
description: Узнайте, как добавить ActiveX‑элемент в документ Word с помощью C#. Включает
  привязку макроса к кнопке и добавление кликабельной кнопки, примеры Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: ru
lastmod: 2026-08-07
og_description: Как добавить элемент управления ActiveX в документ Word с помощью
  Aspose.Words. Следуйте этому руководству, чтобы вставить кнопку, связать макрос
  с кнопкой и добавить кликабельную кнопку в документ.
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: как добавить ActiveX‑элемент в Word – полный учебник по C#
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Как добавить ActiveX‑элемент в Word с помощью Aspose.Words – пошаговое руководство
url: /ru/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как добавить ActiveX‑элемент в Word с помощью Aspose.Words

Если вам нужно **how to add activex control** в файл Microsoft Word программно, этот учебник покажет вам точные шаги с использованием Aspose.Words для .NET. Вы увидите, как вставить кнопку **CommandButton**, задать её подпись и **associate macro with button**, чтобы элемент реагировал при щелчке пользователя. В конце у вас будет файл с поддержкой макросов `.docm`, содержащий полностью функционирующую кнопку.

Добавление ActiveX‑кнопки — распространённое требование при создании интерактивных шаблонов, таких как заявки на кредит, формы адаптации сотрудников или автоматические отчёты. Это руководство проходит по каждой строке кода, объясняет **why** каждый шаг важен и охватывает типичные подводные камни, с которыми вы можете столкнуться.

## Предварительные требования

* .NET 6 (или .NET Core 3.1 / .NET Framework 4.8) установлен.
* Действительная лицензия Aspose.Words for .NET или временный оценочный ключ.
* Visual Studio 2022 (или любая IDE, поддерживающая C#).
* Базовые знания макросов Word (VBA), если вы планируете писать макрос, который будет вызываться кнопкой.

> **Pro tip:** При запуске примера сохраняйте вывод в папку, где у вас есть права записи, иначе `doc.Save` выбросит исключение.

## Как добавить ActiveX‑элемент в документ Word с помощью Aspose.Words

Основой решения является небольшая программа на C#, которая создаёт новый документ, вставляет ActiveX **CommandButton** и сохраняет файл как документ с поддержкой макросов (`.docm`). Код полностью готов к копированию и вставке.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### Почему важна каждая строка

| Строка | Описание |
|--------|----------|
| `Document doc = new Document();` | Создаёт новый пакет Word в памяти. |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | Предоставляет удобный API для вставки содержимого, включая ActiveX‑элементы. |
| `InsertForms2OleControl` | Единственный метод Aspose.Words, создающий ActiveX‑элемент; вы указываете тип элемента (`CommandButton`) и его геометрию. |
| `commandButton.Caption = "Click Me";` | Устанавливает **add clickable button word**, которое видит конечный пользователь. Без подписи кнопка будет пустой. |
| `commandButton.OnAction = "MyMacro";` | **associate macro with button** – указывает Word, какой VBA‑макрос выполнять при щелчке по элементу. |
| `doc.Save("CommandButton.docm");` | Сохраняет документ как файл с поддержкой макросов; обычный `.docx` удалит элемент и макрос. |

> **Note:** Координаты (left, top) измеряются в пунктах (1 pt ≈ 1/72 in). Отрегулируйте их, чтобы разместить кнопку в нужном месте на странице.

## Как связать макрос с кнопкой

Свойство `OnAction` связывает кнопку с VBA‑макросом под названием `MyMacro`. Вы всё равно должны создать этот макрос внутри файла Word, либо вручную, либо программно внедрив VBA‑код (Aspose.Words не записывает VBA‑код). Ниже минимальный макрос, который можно добавить через редактор **Developer → Visual Basic** в Word:

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

Когда пользователь откроет `CommandButton.docm` и нажмёт кнопку, Word выполнит `MyMacro` и покажет окно сообщения. Если уровень безопасности макросов установлен в **Disable all macros without notification**, кнопка будет отключена. Посоветуйте пользователям включить макросы для документа или подписать макрос доверенным сертификатом.

### Распространённые подводные камни при связывании макроса

* **Macro security settings** – Если документ открывается на машине со строгими политиками безопасности, макрос может быть заблокирован. Предоставьте инструкции по снижению уровня безопасности или подпишите макрос.
* **Naming conflicts** – Имя макроса должно быть уникальным внутри VBA‑проекта документа; иначе Word выдаст ошибку «duplicate procedure name».
* **64‑bit vs 32‑bit Word** – ActiveX‑элементы работают одинаково, но редактор VBA может показывать разные предупреждения в зависимости от версии Office.

## Как добавить подпись кнопки в форму Word

Свойство `Caption` определяет, что пользователи видят на кнопке. Вы можете дополнительно настроить его:

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

Если требуется, чтобы подпись менялась динамически в зависимости от ввода пользователя, позже можно обратиться к элементу через объектную модель Word:

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### Пограничный случай: длинные подписи

Word обрезает подписи, превышающие ширину кнопки. Чтобы избежать усечения, либо увеличьте параметр ширины в `InsertForms2OleControl`, либо сократите текст. Рекомендуется тестировать с разными языками (например, немецким или японским), так как ширина символов различается.

## Как добавить программное имя кнопки для автоматизации формы

Помимо визуальной подписи, концепция **add command button word** охватывает программное имя элемента. Aspose.Words не предоставляет прямое свойство `Name` для ActiveX‑элементов, но вы можете задать поле `AltText`, которое Word рассматривает как идентификатор элемента:

```csharp
commandButton.AltText = "SubmitButton";
```

Позже в VBA можно ссылаться на кнопку по её значению `AltText`:

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

Эта техника полезна, когда у вас несколько кнопок и необходимо различать их программно.

## Полный рабочий пример

Ниже полностью готовая программа, которую можно собрать и запустить как консольное приложение. В ней есть необязательное стилизование, привязка макроса и блок комментариев, описывающий каждый шаг.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**Expected result:** При открытии `SubmitForm.docm` в Microsoft Word отображается синяя кнопка с подписью *Submit Form*. Нажатие кнопки запускает VBA‑макрос `SubmitMacro` (при условии, что вы добавили макрос в документ). Кнопку можно перемещать, менять её размер или дополнительно стилизовать, используя тот же объект `Forms2OleControl`.

## Тестирование решения

1. Соберите и запустите консольное приложение C#.
2. Откройте сгенерированный `SubmitForm.docm` в Word.
3. Если будет предложено, включите макросы.
4. Нажмите кнопку *Submit Form* — вы должны увидеть сообщение, определённое в `SubmitMacro`.

Если кнопка отображается, но ничего не делает, дважды проверьте, что имя макроса точно совпадает (`SubmitMacro`) и что уровень безопасности макросов не блокирует их выполнение.

## Часто задаваемые вопросы

| Вопрос | Ответ |
|--------|-------|
| *Могу ли я добавить более одной ActiveX‑кнопки?* | Да. Вызывайте `InsertForms2OleControl` несколько раз с разными координатами. Используйте разные значения `OnAction` и `AltText` для их различения. |
| *Отображается ли ActiveX‑элемент в Word Online?* | Нет. |

## Что следует изучить дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Добавление содержимого с помощью Document Builder в Aspose.Words для .NET](/words/english/net/add-content-using-document-builder/)
- [Учебник по теням фигур Aspose.Words – Добавление тени к фигуре Word на C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Добавление нового раздела в документ Word | Aspose.Words для .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}