---
category: general
date: 2026-10-10
description: Установите текст кнопки и добавьте кнопку ActiveX в C# с помощью Aspose.Words.
  Узнайте, как вставить кнопку, создать элемент управления кнопкой и настроить подпись
  в документе Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: ru
lastmod: 2026-10-10
og_description: Установите текст кнопки и добавьте кнопку ActiveX в C# с помощью Aspose.Words.
  Следуйте этому пошаговому руководству, чтобы вставить кнопку, создать элемент управления
  кнопкой и настроить её подпись.
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: Установите текст кнопки и добавьте кнопку ActiveX в C# – полное руководство
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: Установить текст кнопки и добавить кнопку ActiveX в C#
url: /ru/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Установить текст кнопки и добавить кнопку ActiveX в C#

Если вам нужно **установить текст кнопки** на кнопке ActiveX внутри документа Word, это руководство покажет, как это сделать. К концу урока вы сможете **вставить кнопку**, создать **элемент управления кнопкой** и настроить её подпись всего несколькими строками кода C#.

Работа с элементами управления ActiveX часто требуется, когда нужны интерактивные формы в Word — будь то шаблон контракта, опрос или внутренний инструмент. В примере используется Aspose.Words for .NET, библиотека, позволяющая манипулировать файлами Word без установленного Microsoft Office.

## Требования

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6.0 SDK или более поздняя версия  
* Visual Studio 2022 (или любая IDE, поддерживающая C#)  
* Лицензия Aspose.Words for .NET (бесплатная оценочная версия подходит для обучения)  

Также необходимо добавить ссылку на пакет `Aspose.Words` из NuGet:

```bash
dotnet add package Aspose.Words
```

## Как вставить кнопку в документ Word

Первый шаг — создать новый `Document` и `DocumentBuilder`. Builder служит точкой входа для добавления содержимого, включая элементы управления ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Почему это важно:** `Document` представляет весь файл .docx, а `DocumentBuilder` предоставляет высокоуровневые методы, такие как `InsertParagraph` и `InsertFormField`. Начало с чистого документа гарантирует, что кнопка появится точно там, где вы хотите.

## Создание элемента управления кнопкой с помощью Forms2OleControl

Теперь создаём сам элемент управления кнопкой. `Forms2OleControl` — это класс Aspose.Words, используемый для всех объектов ActiveX, а тип `COMMANDBUTTON` отображается в Word как кликабельная кнопка.

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**Пояснение:**  
* `InsertForms2OleControl` размещает элемент управления в точных координатах, которые вы указываете.  
* Размер задаётся в пунктах (1 пункт = 1/72 дюйма). Отрегулируйте эти числа под ваш макет.

## Добавление элемента управления ActiveX и присвоение уникального имени

Каждому объекту ActiveX следует задавать уникальное имя, чтобы позже можно было ссылаться на него (например, при обработке событий в VBA).

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**Совет:** Избегайте пробелов и специальных символов в имени; Word рассматривает имя как идентификатор во внутренней модели формы.

## Установка текста кнопки (подписи) на элементе ActiveX

Именно здесь вступает в действие основной запрос **set button text**. Свойство `Caption` определяет метку, которую видят пользователи на кнопке.

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

Вы можете изменить подпись в любой момент до сохранения документа. Если позже понадобится локализовать интерфейс, просто вызовите `SetCaption` снова с другой строкой.

## Сохранение документа и проверка результата

Наконец, запишите документ на диск. Открытие файла в Microsoft Word покажет кнопку с пользовательской подписью.

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**Ожидаемый результат:** При открытии *ActiveXButton.docx* в Word вы увидите кнопку, расположенную в указанных координатах, с надписью **Click Me**. Нажатие кнопки вызовет стандартное поведение кнопки команд в Word (которое позже можно настроить с помощью VBA).

![Set button text example](https://example.com/activex-button.png){alt="Пример установки текста кнопки"}

## Добавление кнопки ActiveX и обработка событий (необязательно)

Если требуется, чтобы кнопка выполняла пользовательское действие, можно добавить макрос VBA, реагирующий на событие `Click`. Макрос может быть внедрён программно, но это выходит за рамки данного руководства. Главное, что кнопка уже присутствует, а её подпись установлена — готова к любой обработке событий, которую вы выберете.

## Распространённые ошибки и способы их избежать

| Проблема | Почему происходит | Решение |
|----------|-------------------|----------|
| Кнопка отображается смещённо | Координаты задаются в пунктах, а не в пикселях | Преобразуйте пиксели в пункты (`points = pixels * 72 / DPI`) |
| Подпись не меняется после сохранения | `SetCaption` вызван после `Save` | Всегда задавайте подпись **до** вызова `doc.Save` |
| Элемент не виден в старых версиях Word | Некоторые старые сборки Word не поддерживают полностью ActiveX | Тестируйте на целевой версии Word; при необходимости используйте `CheckBox` или `DropDownList` в качестве альтернативы |
| Предупреждение о лицензии в выводе | Оценочная лицензия истекла | Примените действительную лицензию Aspose.Words через `License license = new License(); license.SetLicense("Aspose.Words.lic");` |

## Полный, готовый к запуску пример

Ниже приведена полная программа, которую можно скопировать, вставить и запустить. В ней включены все необходимые директивы `using` и демонстрируется весь процесс от создания документа до его сохранения.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

Запустите программу командой `dotnet run`. После выполнения откройте *ActiveXButton.docx*, чтобы убедиться, что подпись кнопки отображает **Click Me**.

## Краткое резюме изученного

* Вы узнали, как **установить текст кнопки** на элементе ActiveX с помощью Aspose.Words.  
* Вы увидели точные шаги по **вставке кнопки**, **созданию элемента управления кнопкой** и **добавлению элемента управления ActiveX** в документ Word.  
* Теперь у вас есть переиспользуемый фрагмент кода, который можно адаптировать для любого проекта автоматизации Word с формами.

## Следующие шаги

* Исследуйте другие значения `Forms2OleControlType`, такие как `CHECKBOX` или `LISTBOX`, чтобы создавать более сложные формы.  
* Скомбинируйте кнопку с макросом VBA для выполнения вычислений или проверки данных.  
* Используйте API `FormField` Aspose.Words для чтения пользовательского ввода после заполнения документа.

Экспериментируйте с размером, позицией и подписью, чтобы они соответствовали вашим требованиям к дизайну. Если возникнут проблемы, документация Aspose.Words предоставляет подробные ссылки на каждый класс, используемый в этом руководстве.

Счастливого кодинга!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Создать пустой документ Word с Aspose.Words – Пошаговое руководство](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Добавить тень к фигуре в Word с Aspose.Words – Пошагово](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Добавить номера страниц в нижний колонтитул документа Word с помощью Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}