---
category: general
date: 2026-10-23
description: Создайте пустой документ Word с помощью C# и изучите, как вставлять элементы
  управления ActiveX, включая кнопку, используя Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: ru
lastmod: 2026-10-23
og_description: Создайте пустой документ Word с помощью C# и узнайте, как вставлять
  элементы управления ActiveX, включая кнопку, используя Aspose.Words.
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: Создайте пустой документ Word и добавьте кнопку ActiveX в C#
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Создайте пустой документ Word и добавьте кнопку ActiveX в C#
url: /ru/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создайте пустой документ Word и добавьте кнопку ActiveX в C#

Если вам нужно **создать пустой документ Word** программно, это руководство покажет вам, как это сделать. Вы увидите полный, исполняемый пример, который создает новый документ, вставляет кнопку ActiveX CommandButton и сохраняет файл — всё с помощью Aspose.Words for .NET.

Работа с файлами Word часто требует большего, чем простой текст. Добавление **ActiveX button** позволяет внедрять интерактивный функционал, который может использоваться в шаблонах с поддержкой макросов или решениях только для Windows. К концу этого руководства вы сможете вставлять любой элемент управления ActiveX, но мы сосредоточимся на наиболее распространённом сценарии: **word document activex button**, отправляющей форму.

## Требования

* .NET 6.0 или новее (код также работает с .NET Framework 4.7+)
* Visual Studio 2022 (или любой IDE для C#)
* **Aspose.Words for .NET** пакет NuGet  
  ```bash
  dotnet add package Aspose.Words
  ```
* Базовое знакомство с синтаксисом C#

> **Pro tip:** Aspose.Words — коммерческая библиотека, но она предоставляет бесплатную временную лицензию для тестирования. Установите лицензию заранее, чтобы избежать водяного знака оценки.

## Шаг 1: Создать пустой документ Word с помощью Aspose.Words

Первый шаг — создать объект `Document`. Он представляет пустой файл `.docx` в памяти.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` начинается без разделов, страниц и содержимого. Это чистый лист, необходимый для сценариев **создать пустой документ Word**, таких как генерация отчетов с нуля.

## Шаг 2: Получить DocumentBuilder для редактирования документа

`DocumentBuilder` предоставляет удобный API для добавления текста, изображений и элементов управления. Мы будем использовать его для позиционирования ActiveX‑контроля.

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

Builder автоматически добавляет раздел по умолчанию и первую страницу, поэтому вы можете сразу начинать вставлять объекты.

## Шаг 3: Как вставлять ActiveX‑контролы в документ

Aspose.Words предоставляет `InsertForms2OleControl` для внедрения OLE/ActiveX объектов. Метод требует тип контрола, ширину и высоту (в пунктах). Ниже мы вставляем **CommandButton** — классическую кнопку формы, которую вы видите в устаревших шаблонах Word.

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **Почему это работает:** `Forms2OleControlType.COMMANDBUTTON` указывает Word создать кнопку, которая может реагировать на события клика, когда документ открыт в Windows‑окружении, поддерживающем ActiveX.

## Шаг 4: Создать ActiveX‑контрол — задать его свойства

Теперь мы задаём кнопке программное имя и видимую подпись. Это часть **create activex control**, которую разработчики часто упускают из виду.

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` — идентификатор, который вы будете использовать в VBA‑макросах (`ActiveDocument.InlineShapes("btnSubmit")`).
* `Caption` — подпись, отображаемая на самой кнопке.

## Шаг 5: Сохранить документ Word с кнопкой ActiveX

Наконец, запишите документ на диск. Расширение файла должно быть `.docx` (или `.docm`, если вы планируете добавить макросы позже). Пример сохраняет в папку‑заполнитель — замените её на свой путь.

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Когда вы откроете полученный файл в Microsoft Word (только Windows), вы увидите рабочий **word document activex button**, который можно привязать к VBA‑коду.

## Полный рабочий пример

Ниже приведена полная программа, которую вы можете скопировать и вставить в новый консольный проект.

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
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Ожидаемый вывод при запуске программы**

```
Document saved to C:\Temp\ActiveXButton.docx
```

Откройте сгенерированный `ActiveXButton.docx` в Word, и вы увидите кнопку с надписью **Submit**, расположенную в верхней части первой страницы.

## Пограничные случаи и распространённые подводные камни

| Ситуация | На что обратить внимание | Рекомендация |
|-----------|-------------------|----------------|
| Запуск на macOS или Linux | ActiveX — технология, доступная только в Windows, поэтому кнопка будет отображаться как заполнитель. | Используйте руководство только для шаблонов, ориентированных на Windows. |
| Документ открыт в Word Online | ActiveX‑контролы не поддерживаются в браузерном просмотре. | Предоставьте запасной интерфейс или попросите пользователей открыть файл в настольном клиенте. |
| Необходим файл с поддержкой макросов | Файлы `.docx` не могут хранить VBA‑код. | Сохраните как `.docm` (`document.Save("MyFile.docm", SaveFormat.Docm)`) и добавьте макрос отдельно. |
| Несоответствие размеров контрола | Значения ширины/высоты указаны в пунктах (1 pt ≈ 1/72 in). | Отрегулируйте числовые значения, чтобы получить желаемый визуальный размер. |

## Часто задаваемые вопросы

**Как вставлять ActiveX‑контролы, отличные от кнопки?**  
Используйте тот же метод `InsertForms2OleControl`, но передайте другое значение перечисления `Forms2OleControlType`, например `COMBOBOX` или `LISTBOX`.

**Могу ли я изменить шрифт или цвет кнопки?**  
Внешний вид ActiveX‑кнопки определяется хост‑приложением (Word) и темой Windows. Вы можете изменить свойства, такие как `ForeColor` и `BackColor`, через VBA после открытия документа.

**Можно ли добавить обработчик клика напрямую из C#?**  
Нет. Событие клика должно обрабатываться VBA или надстройкой Word, потому что кнопка работает внутри процесса Word, а не вашего .NET‑приложения.

## Заключение

Теперь вы знаете, как **создать пустой документ Word** программно и внедрить **ActiveX button** с помощью Aspose.Words for .NET. Охваченные шаги:

1. Создать объект `Document`.
2. Использовать `DocumentBuilder` для работы с файлом.
3. Вызвать `InsertForms2OleControl` для **how to insert activex** контролов.
4. Настроить свойства контрола (**create activex control**).
5. Сохранить файл, получив **word document activex button**, готовую к интеграции с VBA.

Отсюда вы можете исследовать добавление других типов контролов, привязку VBA‑макросов или конвертацию документа в PDF с сохранением кнопки (в виде статического изображения). Экспериментируйте с различными размерами, подписями и именами.

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [How to add ActiveX button in a Word document with Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}