---
category: general
date: 2026-09-14
description: Создайте ActiveX‑элемент в документе Word с помощью C#. Узнайте, как
  вставить ActiveX, добавить интерактивную кнопку и программно сгенерировать файл
  .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: ru
lastmod: 2026-09-14
og_description: Создайте элемент управления ActiveX в документе Word с помощью C#.
  Следуйте этому полному примеру, чтобы вставить ActiveX, добавить интерактивную кнопку
  и сохранить файл.
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: Создание ActiveX‑контрола в Word с использованием C# – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: Как создать элемент управления ActiveX в документе Word с помощью C#
url: /ru/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать ActiveX‑элемент в документе Word с помощью C#

Если вам нужно **создать ActiveX‑элемент** внутри файла Microsoft Word, это руководство покажет вам полное, готовое к запуску решение. Вы увидите точно, как вставить ActiveX CommandButton, задать его свойства и сохранить полученный файл `.docx`, используя только код C#.

Добавление интерактивной кнопки в документ Word — распространённое требование, когда вы хотите, чтобы конечные пользователи запускали макросы или пользовательскую логику непосредственно из интерфейса документа. Пример ниже демонстрирует **как вставить ActiveX** без использования сторонних инструментов, а также охватывает **как программно создать документ Word**.

К концу этого руководства вы сможете **создать кнопку с помощью кода**, настроить её подпись и создать переносимый файл Word, сохраняющий ActiveX‑элемент.

## Предварительные требования

- .NET 6.0 или новее (библиотека Aspose.Words для .NET работает с .NET Core и .NET Framework)
- Ссылка на пакет `Aspose.Words` NuGet  
  ```bash
  dotnet add package Aspose.Words
  ```
- Базовые знания C# и объектно‑ориентированного программирования

## Шаг 1: Настройте проект и импортируйте пространства имён

Создайте новый консольный проект (или интегрируйте код в любое существующее C#‑приложение). Импортируйте необходимые пространства имён, чтобы компилятор мог находить классы обработки Word.

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **Почему этот шаг важен** – API `Aspose.Words` предоставляет классы `Document`, `DocumentBuilder` и `Forms2OleControl`, позволяющие манипулировать файлами Word на уровне объектов. Без этих ссылок остальной код не скомпилируется.

## Шаг 2: Создайте новый документ Word и DocumentBuilder

Объект `Document` представляет весь пакет `.docx`, тогда как `DocumentBuilder` предоставляет удобный API для вставки содержимого.

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Объяснение** – Создание нового `Document` даёт вам чистый холст. Курсор builder'а начинается в начале первой секции, готовый к следующей вставке.

## Шаг 3: Вставьте ActiveX CommandButton

Используйте `InsertForms2OleControl`, чтобы разместить ActiveX‑элемент в определённом месте. Метод требует тип элемента и `RectangleF`, определяющий координаты X/Y и размер (в пунктах).

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Почему это работает** – `OleControlType.CommandButton` указывает API создать стандартный Windows CommandButton. Прямоугольник позиционирует кнопку относительно верхнего‑левого угла страницы, позволяя вам **добавить интерактивную кнопку** точно там, где это необходимо.

## Шаг 4: Настройте свойства кнопки

Теперь задайте видимый текст кнопки (`Caption`) и её внутреннее имя (`Name`). Эти свойства видят пользователи и к которым может обращаться VBA‑код позже.

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **Практический совет** – `Name` должно быть уникальным в пределах документа; в противном случае макросы VBA могут ссылаться на неправильный элемент.

## Шаг 5: Сохраните документ

Наконец, запишите файл на диск. ActiveX‑элемент хранится внутри пакета Word, поэтому сохранённый файл сохранит полную функциональность при открытии в Microsoft Word.

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Результат** – При открытии `CommandButton.docx` в Word отображается кликабельный CommandButton с надписью «Click Me». Элемент можно связать с макросом через интерфейс Word (`Developer → Design Mode → Properties`).

## Полный список исходного кода

Объединение всех шагов приводит к единой, автономной программе, которую можно скопировать, вставить и запустить.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Ожидаемый вывод

Запуск программы выводит строку подтверждения:

```
Document saved to C:\Temp\CommandButton.docx
```

Когда вы откроете сгенерированный файл в Microsoft Word, вы увидите **CommandButton**, размещённый в указанных координатах. При щелчке по кнопке в режиме дизайна она будет выделена; в режиме выполнения она ведёт себя как любой стандартный ActiveX‑элемент.

## Общие варианты и граничные случаи

| Сценарий | Корректировка |
|----------|---------------|
| **Другой тип элемента** | Замените `OleControlType.CommandButton` на `OleControlType.CheckBox`, `OleControlType.OptionButton` и т.д. |
| **Несколько кнопок** | Вызовите `InsertForms2OleControl` несколько раз, обновляя координаты `RectangleF` для каждой новой кнопки. |
| **Динамический размер** | Вычисляйте размеры прямоугольника на основе размера страницы (`builder.PageSetup.PageWidth`). |
| **Сохранение в поток** | Используйте `document.Save(stream, SaveFormat.Docx)`, когда необходимо вернуть файл из веб‑API. |
| **Формат Word 97‑2003** | Измените формат сохранения на `SaveFormat.Doc`, чтобы получить файл `.doc`, который всё ещё содержит ActiveX‑элемент. |

> **Pro tip:** Всегда тестируйте сгенерированный документ в целевой версии Word, так как старые версии могут применять настройки безопасности, отключающие ActiveX‑элементы по умолчанию.

## Часто задаваемые вопросы

**Работает ли это с .NET Core?**  
Да. Библиотека Aspose.Words кросс‑платформенная и полностью совместима с .NET Core и .NET 5/6+.

**Можно ли программно назначить макрос кнопке?**  
API не встраивает VBA‑код напрямую. После генерации документа откройте его в Word, включите вкладку Developer и запишите или напишите макрос, который ссылается на `btnClick`.

**Что делать, если кнопка не отображается?**  
Убедитесь, что вкладка `Developer` включена в Word и документ не открыт в **Protected View**. Также проверьте, что координаты прямоугольника находятся внутри полей страницы.

## Заключение

Теперь вы знаете, как **создать ActiveX‑элемент** внутри файла Word с помощью C#. Руководство охватило **как вставить ActiveX**, продемонстрировало **добавление интерактивной кнопки**, показало **как создать документ Word** с нуля и проиллюстрировало **создание кнопки с помощью кода**, которая сохраняется после сохранения.

Отсюда вы можете исследовать дополнительные типы ActiveX, связать кнопку с макросами VBA или встроить логику в более крупный сервис генерации документов. Экспериментируйте с различными размерами, позициями и свойствами элементов, чтобы достичь нужного пользовательского опыта.

---

## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, помогающие вам освоить дополнительные возможности API и изучить альтернативные подходы к реализации в ваших проектах.

- [Создать новый документ Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Создать проект VBA в документе Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Создать и оформить документ Word в Aspose.Words for .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}