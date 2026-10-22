---
category: general
date: 2026-08-10
description: Создайте документ Word программно с помощью Aspose.Words, затем добавьте
  кнопку ActiveX. Вставьте кнопку управления ActiveX за считанные минуты.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: ru
lastmod: 2026-08-10
og_description: Создайте документ Word программно с помощью Aspose.Words, затем добавьте
  кнопку ActiveX. Узнайте, как быстро вставить кнопку команды ActiveX.
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: Создать документ Word программно – добавить кнопку ActiveX в C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: Создать документ Word программно и добавить кнопку ActiveX
url: /ru/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание Word‑документа программно и добавление кнопки ActiveX

Если вам нужно **создавать Word‑документ программно**, это руководство проведёт вас через весь процесс с Aspose.Words for .NET. Вы также узнаете, как **добавлять элементы управления ActiveX в Word** и **вставлять объекты кнопки ActiveX CommandButton** в одном, автономном примере.

Генерация файлов Word из кода устраняет необходимость вручную открывать Microsoft Word, позволяя автоматически создавать отчёты, счета‑фактуры или контракты, основанные на данных. К концу этого руководства у вас будет готовое к запуску консольное приложение C#, которое создаёт файл `.docx`, содержащий интерактивную кнопку ActiveX CommandButton.

## Предварительные требования

* .NET 6.0 SDK или новее (код также работает с .NET Framework 4.6+)
* Visual Studio 2022 или любая IDE, поддерживающая разработку на .NET
* Действительная лицензия Aspose.Words for .NET (для тестирования можно использовать бесплатный ключ оценки)
* Базовое знакомство с синтаксисом C# и концепцией COM/ActiveX‑элементов управления

> **Полезный совет:** Если вы планируете распространять сгенерированный документ пользователям, у которых нет установленного Word, включите файлы среды выполнения ActiveX‑контроля рядом с `.docx` или предоставьте шаблон с поддержкой макросов.

## Создание Word‑документа программно – начальная настройка

Сначала добавьте пакет Aspose.Words NuGet в ваш проект:

```bash
dotnet add package Aspose.Words
```

Затем создайте новый консольный проект (если у вас его ещё нет):

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

Откройте сгенерированный файл `Program.cs` — мы заменим его содержимое полным решением, приведённым ниже.

## Шаг 1: Импорт пространств имён и настройка лицензии

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*Почему это важно*: Импорт `Aspose.Words.Drawing` даёт доступ к `Forms2OleControl` — классу, представляющему ActiveX‑контроль внутри Word‑документа. Установка лицензии на раннем этапе предотвращает предупреждения во время выполнения в продакшене.

## Шаг 2: Создание пустого документа и DocumentBuilder

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Объект `Document` представляет собой в‑памяти структуру файла `.docx`. `DocumentBuilder` работает как курсор, которым вы перемещаетесь по документу для вставки элементов.

## Шаг 3: Вставка элемента управления ActiveX CommandButton

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` создаёт OLE‑объект, который Word воспринимает как ActiveX‑контроль. Система координат использует пункты (1 пункт = 1/72 дюйма), что соответствует движку разметки Word.

## Шаг 4: Установка подписи кнопки и дополнительных свойств

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

Установка свойства `Caption` — самый распространённый способ задать подпись кнопки. Если требуется, чтобы кнопка запускала VBA‑макрос, присвойте имя макроса свойству `OnAction`. В этом руководстве акцент делается на визуальной части; интеграция макросов рассматривается в разделе «Следующие шаги».

## Шаг 5: Сохранение документа

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

При запуске программы вы увидите сообщение в консоли, подтверждающее, что `ActiveX_CommandButton.docx` был записан на диск.

### Полный исходный код (готовый к копированию)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Выполнение фрагмента кода создаёт Word‑файл, содержащий кликабельную **кнопку ActiveX command button**. Откройте файл в Microsoft Word, переключитесь в **режим разработки** (вкладка Developer → Design Mode), и вы увидите кнопку, отрисованную точно в том месте, где вы её разместили.

## Шаг 6: Проверка результата

1. Откройте `ActiveX_CommandButton.docx` в Microsoft Word.
2. Включите вкладку **Developer**, если она не видна (`File → Options → Customize Ribbon → check Developer`).
3. Нажмите **Design Mode**. Кнопка должна появиться с подписью «Submit».
4. Если вы добавили макрос `OnAction`, нажмите кнопку при выключенном режиме Design Mode, чтобы запустить макрос.

Если кнопка не отображается, убедитесь, что настройки безопасности Word позволяют использовать ActiveX‑контролы (`File → Options → Trust Center → Trust Center Settings → ActiveX Settings`).

## Часто задаваемые вопросы и особые случаи

| Вопрос | Ответ |
|----------|--------|
| **Можно ли вставлять другие типы ActiveX?** | Да. Перечисление `Forms2OleControlType` включает `CheckBox`, `OptionButton`, `ComboBox` и т.д. Замените `CommandButton` на нужное значение перечисления |

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и изучить альтернативные подходы к реализации в ваших проектах.

- [Создать групповую форму в документе Word с помощью Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Создать документ Word с верхним и нижним колонтитулом с помощью Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Вставить встроенное изображение в документ Word с помощью Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}