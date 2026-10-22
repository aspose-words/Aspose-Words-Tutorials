---
category: general
date: 2026-09-21
description: Узнайте, как создать кнопку управления ActiveX в документе Word с помощью
  Aspose.Words и C#. Пошаговое руководство охватывает вставку, позиционирование и
  сохранение.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: ru
lastmod: 2026-09-21
og_description: Создайте кнопку команд ActiveX в документе Word с помощью C# и Aspose.Words.
  Следуйте этому полному руководству, чтобы программно вставить, разместить и сохранить
  кнопку.
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: Создайте кнопку ActiveX в Word с помощью C# – полное руководство
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: Как создать кнопку ActiveX в Word с помощью C#
url: /ru/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать кнопку ActiveX в Word с помощью C#

Если вам нужно **создать кнопку ActiveX** внутри файла Word, это руководство покажет точные шаги. С помощью Aspose.Words for .NET вы можете добавить, разместить и настроить кнопку полностью из кода C#.

Программное вставление кнопки ActiveX устраняет ручную работу с интерфейсом и позволяет автоматизировать генерацию документов для форм, отчётов или интерактивных шаблонов. В этом уроке вы узнаете, как использовать **DocumentBuilder**, метод **InsertForms2OleControl** и связанные свойства для создания полностью функционирующей кнопки.

## Что вам понадобится

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6.0 SDK или новее (код также работает с .NET Framework 4.7+)
* Aspose.Words for .NET (NuGet‑пакет `Aspose.Words`)
* IDE, например Visual Studio 2022 или VS Code
* Базовые знания C# и концепций Word‑документов

Дополнительная установка Office не требуется, поскольку Aspose.Words работает независимо от Microsoft Word.

## Шаг 1: Настройка проекта C#

Создайте новый консольный проект и добавьте пакет Aspose.Words.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

Библиотека `Aspose.Words` предоставляет класс **DocumentBuilder**, которым мы будем управлять документом.

## Шаг 2: Инициализация документа и builder’а

Первый блок кода создаёт пустой документ и экземпляр `DocumentBuilder`. Этот объект является точкой входа для всех операций обработки Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Почему это важно:** `DocumentBuilder` хранит текущую позицию курсора, поэтому любое последующее вставление появится ровно там, где находится курсор.

## Шаг 3: Вставка кнопки ActiveX

Метод **InsertForms2OleControl** создаёт ActiveX‑контролл требуемого типа. Здесь мы запрашиваем `CommandButton` и указываем его размер в пунктах (200 × 30 pt).

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**Объяснение:**  
* `OleControlType.CommandButton` сообщает Aspose.Words создать кнопку, а не другой тип контроля.  
* Метод возвращает объект `Forms2OleControl`, который предоставляет поля позиционирования и свойства.

## Шаг 4: Позиционирование кнопки и установка её свойств

После вставки вы можете переместить кнопку в любое место страницы и задать ей программное имя и видимую подпись.

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**Совет:** Система координат начинается в левом верхнем углу страницы. Настройте `Left` и `Top`, чтобы выровнять кнопку с другими полями формы.

## Шаг 5: Сохранение документа

Наконец, запишите документ на диск. Файл будет содержать кнопку ActiveX, готовую к открытию в Microsoft Word, где кнопка станет интерактивной.

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

Когда вы откроете `ActiveXCommandButton.docx` в Word, вы увидите кнопку с подписью **Submit** в указанном месте. Щелчок по ней в Word вызовет стандартное поведение кнопки (которое позже можно настроить с помощью VBA или надстроек Word).

## Полный, готовый к запуску пример

Собрав все части вместе, получаем автономную программу, которую можно скопировать, вставить и запустить.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**Ожидаемый вывод:** Консоль выводит *“Document created successfully.”*, а в папке появляется `ActiveXCommandButton.docx`. Открытие файла в Microsoft Word показывает кликабельную кнопку **Submit**, расположенную на 100 pt от левого поля и 150 pt от верхнего края страницы.

## Распространённые ошибки и как их избежать

| Проблема | Почему происходит | Решение |
|----------|-------------------|---------|
| Кнопка появляется за пределами страницы | Значения `Left`/`Top` превышают размеры страницы | Используйте `doc.FirstSection.PageSetup.PageWidth` и `PageHeight` для расчёта безопасных координат |
| Кнопка не видна в Word | Документ сохранён в формате, который удаляет ActiveX‑контроллы (например, `.txt`) | Всегда сохраняйте как `.docx` или `.doc` |
| Ошибка выполнения `ArgumentOutOfRangeException` | Ширина или высота установлены в ноль или отрицательное значение | Убедитесь, что аргументы размера, передаваемые в `InsertForms2OleControl`, положительные |

## Расширение решения

Вы можете дополнительно настроить кнопку, задав свойства `Enabled`, `Visible` или привязав макрос через VBA. Класс **Forms2OleControl** также позволяет вставлять другие ActiveX‑контроллы, такие как флажки (`OleControlType.CheckBox`) или комбобоксы (`OleControlType.ComboBox`).

Если нужно генерировать несколько кнопок в цикле, вынесите логику вставки в вспомогательный метод:

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## Заключение

Теперь вы знаете, как **создать кнопку ActiveX** в документе Word с помощью C# и Aspose.Words. В руководстве рассмотрены настройка проекта, вставка кнопки через `InsertForms2OleControl`, её позиционирование и сохранение финального файла. На этой основе вы сможете автоматизировать сложные формы, встраивать интерактивные элементы и интегрировать Word‑документы в более крупные .NET‑решения.

Далее изучайте связанные темы, такие как **Aspose.Words ActiveX** формы, продвинутое стилизование с **C# DocumentBuilder**, или программное добавление **ActiveX‑контроллов в Word** для флажков и выпадающих списков. Экспериментируйте с различными координатами и размерами, чтобы подогнать элементы под ваш макет. Приятного кодинга!

## Что вам следует изучить дальше?

Следующие уроки охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Создание Word‑документа с Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Создание прямоугольной фигуры в Word с Aspose.Words – пошаговое руководство](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Создание Word‑документа с таблицей с помощью Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}