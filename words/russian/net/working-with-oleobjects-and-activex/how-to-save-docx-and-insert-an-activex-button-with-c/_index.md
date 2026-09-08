---
category: general
date: 2026-09-08
description: Как сохранить docx при вставке ActiveX‑контрола в C#. Следуйте этому
  пошаговому руководству, чтобы программно добавить кнопку команды.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save docx
- insert activex control
- add activex button
- create word document programmatically
- how to add command button
language: ru
lastmod: 2026-09-08
og_description: Как сохранить docx при вставке ActiveX‑контрола в C#. Этот учебник
  пошагово покажет, как программно создать документ Word, добавить кнопку‑команду
  и сохранить файл.
og_image_alt: How to save docx with an ActiveX command button displayed in the document
og_title: Как сохранить docx и встроить кнопку ActiveX в C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: How to save docx while inserting an ActiveX control in C#. Follow this
    step‑by‑step guide to add a command button programmatically.
  headline: How to save docx and insert an ActiveX button with C#
  type: TechArticle
tags:
- C#
- Word automation
- ActiveX
- Docx
title: Как сохранить docx и вставить кнопку ActiveX с помощью C#
url: /ru/net/working-with-oleobjects-and-activex/how-to-save-docx-and-insert-an-activex-button-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как сохранить docx и вставить кнопку ActiveX с помощью C#

Если вам нужно программно создать документ Word, а затем сохранить docx с интерактивной кнопкой, это руководство покажет, как это сделать. Вы научитесь вставлять элемент управления ActiveX, добавлять кнопку ActiveX и сохранять полученный файл .docx с помощью C# и библиотеки Aspose.Words.

В руководстве рассматриваются все шаги, необходимые для **create word document programmatically**, встраивания **command button** и сохранения файла на диск. Предыдущий опыт работы с объектами COM не требуется, но у вас должны быть базовые знания C# и установлен Visual Studio.

## Предварительные требования

* .NET 6.0 SDK или новее  
* Visual Studio 2022 (или любой IDE для C#)  
* Aspose.Words for .NET пакет NuGet (`Install-Package Aspose.Words`)  
* Понимание структуры проекта C#  

Эти элементы гарантируют, что код компилируется и запускается без дополнительной настройки.

## Шаг 1: Создать новый консольный проект C#

Создайте консольное приложение, которое будет содержать логику автоматизации Word.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

Эта команда создает папку с именем **WordActiveXDemo**, добавляет ссылку на Aspose.Words и подготавливает проект к компиляции.

## Шаг 2: Программно создать документ Word

Откройте сгенерированный файл `Program.cs` и добавьте необходимые директивы `using`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;   // not used directly but required for some overloads
```

Теперь создайте экземпляр пустого объекта `Document`. Этот объект представляет весь файл Word в памяти.

```csharp
// Step 2: Create a new blank document
Document document = new Document();
```

Класс `Document` является точкой входа для всех операций обработки Word. На данном этапе документ не содержит страниц, но Aspose.Words автоматически создаст раздел по умолчанию, когда вы добавите содержимое.

## Шаг 3: Вставить элемент управления ActiveX – добавить кнопку activex

Объект **Forms2OleControl** позволяет встраивать элемент управления ActiveX внутри абзаца Word. Следующий код вставляет **CommandButton** шириной 150 pt и высотой 30 pt.

```csharp
// Step 3: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX CommandButton control with the desired size
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

`InsertForms2OleControl` создает элемент управления и возвращает строго типизированный экземпляр `Forms2OleControl`, который можно дополнительно настроить. Метод автоматически добавляет новый абзац для размещения элемента, поэтому вам не нужно вручную управлять объектами абзацев.

## Шаг 4: Настроить кнопку команды – как добавить свойства кнопки команды

Установите свойства **Name** и **Caption** кнопки, чтобы она была идентифицируема во время выполнения и удобна для пользователя в интерфейсе.

```csharp
// Step 4: Set the control's name and caption
commandButton.Name = "cmdSubmit";
commandButton.Caption = "Submit";
```

Атрибут `Name` полезен, когда вы позже обрабатываете событие нажатия кнопки через VBA или макрос Word. `Caption` — это текст, который пользователь видит на поверхности кнопки.

### Совет профессионала
Если вы планируете автоматизировать обработку клика из C#, внедрите VBA‑макрос, который ссылается на `cmdSubmit`. При открытии документа Word предложит пользователю включить макросы, что является стандартным поведением безопасности для элементов управления ActiveX.

## Шаг 5: Как сохранить docx

После размещения элемента управления сохраните документ в файл .docx. Метод `Save` автоматически выбирает соответствующий формат на основе расширения файла.

```csharp
// Step 5: Save the document containing the CommandButton
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Сохранение файла завершает процесс **how to save docx**. Полученный файл можно открыть в Microsoft Word, где кнопка ActiveX появится на первой странице. При нажатии кнопки Word отобразит сообщение-заполнитель, если макрос не привязан.

## Шаг 6: Запустить программу и проверить результат

Скомпилируйте и выполните консольное приложение:

```bash
dotnet run
```

После завершения программы откройте `C:\Temp\CommandButton.docx` в Microsoft Word:

* Документ содержит одну страницу с кнопкой **Submit** в верхней части.  
* При наведении курсора на кнопку отображается всплывающая подсказка с именем `cmdSubmit`.  
* Содержимое не теряется, а размер файла сопоставим со стандартным пустым .docx.

Если кнопка не отображается, проверьте следующее:

1. Настройки **Trust Center** в Word разрешают элементы управления ActiveX.  
2. Файл сохранён с расширением `.docx` (а не `.doc`).  

## Пограничные случаи и распространённые варианты

| Situation | Recommended adjustment |
|-----------|------------------------|
| Вам нужен другой размер кнопки | Измените аргументы ширины и высоты в `InsertForms2OleControl`. |
| Вы хотите разместить кнопку на определённой странице | Используйте `builder.MoveToDocumentEnd();` после добавления страниц или вставьте разрыв страницы перед элементом управления. |
| Необходимо поддерживать среды без Aspose.Words | Используйте Open XML SDK для вставки элемента `w:object`, но код станет значительно сложнее. |
| Требуется документ с поддержкой макросов | Сохраните с расширением `.docm` (`document.Save("MyDoc.docm");`) и внедрите VBA‑модуль, который обрабатывает `cmdSubmit_Click`. |

## Полный исходный код

Ниже представлен полный, автономный код программы, который можно скопировать в `Program.cs` и запустить без изменений (за исключением пути вывода).

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
            // Create a new blank document
            Document document = new Document();

            // Initialize a DocumentBuilder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control with the desired size
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Set the control's name and caption
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // Save the document containing the CommandButton
            string outputPath = @"C:\Temp\CommandButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Ожидаемый вывод в консоли

```
Document saved to C:\Temp\CommandButton.docx
```

Открытие файла в Word отображает кнопку с надписью **Submit**. При нажатии кнопка запускает стандартное поведение ActiveX (сообщение, указывающее, что макрос не привязан).

## Заключение

В этом руководстве продемонстрировано **how to save docx** при встраивании **ActiveX control**, конкретно **add activex button**, который функционирует как кнопка команды. Теперь вы знаете, как **create word document programmatically**, настроить свойства кнопки и сохранить файл для взаимодействия с конечным пользователем.

Далее вы можете изучить:

* Добавление VBA‑макросов для обработки `cmdSubmit_Click`.  
* Вставка других элементов управления ActiveX, таких как флажки или комбобоксы.  
* Создание многостраничных документов с несколькими интерактивными элементами.  

Экспериментируйте с различными типами элементов управления и вариантами компоновки, чтобы создавать богатые интерактивные шаблоны Word, упрощающие бизнес‑процессы.

## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, основанные на техниках, продемонстрированных в этом руководстве. Каждый ресурс содержит полностью работающие примеры кода с пошаговыми объяснениями, помогающие освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Aspose.Words – Save docx as txt and Export Word Equations as LaTeX – Complete Guide](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [how to recover docx – C# guide for corrupted Word files](/words/english/net/programming-with-loadoptions/how-to-recover-docx-c-guide-for-corrupted-word-files/)
- [How to Save Word as Markdown – Complete C# Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-word-as-markdown-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}