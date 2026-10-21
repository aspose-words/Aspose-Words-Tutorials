---
category: general
date: 2026-10-13
description: Узнайте, как программно добавить кнопку команды с помощью Aspose.Words.
  В этом руководстве также показано, как создать кнопку в документе Word с полным
  кодом на C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: ru
lastmod: 2026-10-13
og_description: Программно добавьте кнопку команды в документ Word с помощью Aspose.Words.
  Следуйте этому полному руководству, чтобы создать кнопку в документе Word на C#.
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: Добавьте программно кнопку команды в документ Word – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Как программно добавить кнопку команды в документ Word
url: /ru/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как программно добавить кнопку команды в документ Word  

Если вам нужно **добавить кнопку команды программно**, Aspose.Words предоставляет чистый API, позволяющий внедрять OLE‑элементы управления формами непосредственно в файл .docx. Этот учебник проведёт вас через каждый шаг, необходимый для **создания кнопки в документе Word**, которая ведёт себя как обычная кнопка формы при открытии документа в Microsoft Word.  

Вы узнаете, как настроить среду разработки, вставить кнопку, сконфигурировать её свойства и проверить результат. Внешние утилиты не требуются — только проект .NET и библиотека Aspose.Words for .NET.  

## Предварительные требования  

* .NET 6.0 SDK или более поздняя версия, установленная на вашем компьютере.  
* Последняя версия Aspose.Words for .NET (в примерах используется 23.12, но подойдёт любой релиз 22.x+).  
* IDE, например Visual Studio 2022 или Visual Studio Code.  

Код работает на Windows, macOS и Linux, поскольку Aspose.Words независим от платформы.  

## Шаг 1: Настройка проекта и подключение Aspose.Words  

1. Создайте новый консольный проект:  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. Добавьте пакет Aspose.Words через NuGet:  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. Откройте **Program.cs** и замените его содержимое шаблоном, показанным в следующих шагах.  

Настройка проекта таким образом гарантирует, что компилятор сможет найти пространства имён `Aspose.Words` и `Aspose.Words.Drawing.Forms`, необходимые для элементов управления формами.  

## Шаг 2: Инициализация пустого документа и DocumentBuilder  

Класс `Document` представляет весь файл Word, а `DocumentBuilder` предоставляет удобный API для добавления содержимого.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*Почему этот шаг важен* – Без `DocumentBuilder` вы не сможете точно позиционировать кнопку на странице. Builder также учитывает текущую позицию курсора, что упрощает последующее добавление нескольких элементов управления.  

## Шаг 3: Вставка OLE‑контрола кнопки команды  

Aspose.Words рассматривает кнопку команды как OLE‑контрол типа `ControlType.CommandButton`. Вы задаёте её расположение и размер с помощью `RectangleF`, измеряемого в пунктах (1 пункт = 1/72 дюйма).  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**Ключевые моменты**  

* Начальная точка прямоугольника (X, Y) задаётся относительно левого верхнего угла страницы.  
* Изменение `Width` или `Height` меняет визуальный размер кнопки.  
* `InsertForms2OleControl` возвращает объект `Forms2OleControl`, который можно дополнительно настроить.  

## Шаг 4: Настройка имени и подписи кнопки  

**Имя** используется движком макросов Word для идентификации элемента, а **подпись** — это текст, видимый пользователю.  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

Если планируете добавить VBA‑макросы позже, используйте описательное имя, поскольку рекордер макросов Word ссылается именно на это свойство.  

## Шаг 5: (Опционально) Сохранить документ и проверить результат  

Сохранение файла позволяет открыть его в Microsoft Word и убедиться, что кнопка отображается и работает.  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

При открытии *CommandButtonDemo.docx* в Word вы должны увидеть кнопку с подписью **Submit**, расположенную примерно в 1,4 дюйма от левого поля и в 2,1 дюйма от верхнего края страницы. По умолчанию при нажатии ничего не происходит, так как макрос не привязан, но визуальный элемент полностью функционирует.  

## Шаг 6: Пограничные случаи и распространённые подводные камни  

| Ситуация | На что обратить внимание | Рекомендуемое решение |
|-----------|--------------------------|------------------------|
| **Кнопка перекрывает существующий текст** | Прямоугольник может пересекаться с абзацем, вызывая проблемы с разметкой. | Вставьте кнопку после вызова `builder.Writeln()`, чтобы переместить курсор на новую строку, либо скорректируйте координату `Y`. |
| **Документ открывается с предупреждением** | Некоторые версии Word помечают OLE‑элементы, у которых нет связанной программы. | Убедитесь, что тип элемента — `CommandButton`; Word рассматривает его как стандартный элемент формы и не требует внешней программы. |
| **Запуск на Linux в безголовом окружении** | Word нельзя запустить для тестирования UI, но файл остаётся валидным. | Используйте модульный тест, который читает свойства элемента (`commandButton.Name`, `commandButton.Caption`) для проверки их корректной установки. |
| **Необходимо несколько кнопок** | Повторное использование того же `DocumentBuilder` без перемещения курсора добавит кнопку поверх предыдущей. | Вызовите `builder.MoveToDocumentEnd()` или измените значение `Y` в прямоугольнике перед каждой вставкой. |

Устранение этих пограничных случаев на ранних этапах экономит время при масштабировании решения до полноценных форм с десятками элементов управления.  

## Шаг 7: Полный, исполняемый пример  

Ниже приведена автономная программа, которую можно скопировать, вставить и запустить без модификаций (за исключением восстановления пакетов NuGet).  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**Ожидаемый вывод**  

Запуск программы выводит путь, похожий на:  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

Открытие сгенерированного *CommandButtonDemo.docx* показывает одну кнопку **Submit**, размещённую в координатах, указанных в коде. Дополнительные UI‑элементы не появляются, что подтверждает успешное выполнение процесса **add command button programmatically**.  

## Заключение  

Теперь вы знаете, как **добавить кнопку команды программно** в документ Word с помощью Aspose.Words, а также понимаете, как **создать кнопку в документе Word**, которую позже можно привязать к VBA‑макросам или внешним средствам автоматизации. Процесс состоит из инициализации документа, вставки OLE‑контрола `CommandButton`, настройки его свойств и сохранения файла.  

Отсюда вы можете:  

* Добавлять дополнительные элементы управления (флажки, текстовые поля), повторяя шаг 3 с другими значениями `ControlType`.  
* Привязывать VBA‑макросы к кнопке для выполнения действий, таких как сохранение формы или отправка электронной почты.  
* Генерировать целые формы динамически, перебирая коллекцию определений полей, основанную на данных.  

Экспериментируйте с координатами прямоугольника и подписью кнопки, чтобы они соответствовали вашему дизайну UI. Приятного кодинга!  

## Что изучать дальше?  

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Добавить поле формы «Выпадающий список» в документ Word с помощью Aspose.Words для .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Добавить поле формы «Флажок» в документ Word с помощью Aspose.Words для .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Создать пустой документ Word с Aspose.Words – пошаговое руководство](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}