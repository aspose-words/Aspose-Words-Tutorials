---
category: general
date: 2026-09-11
description: Узнайте, как создать документ Word на C# и программно добавить кнопку
  команды с помощью Aspose.Words за несколько простых шагов.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: ru
lastmod: 2026-09-11
og_description: Создайте документ Word на C# и программно добавьте кнопку команды
  с Aspose.Words. Следуйте этому полному руководству для получения работающего решения.
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: Создать документ Word на C# — добавить кнопку команды программно
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: Как создать документ Word на C# и программно добавить кнопку команды
url: /ru/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как создать Word‑документ на C# и программно добавить кнопку команды

Если вам нужно **create word document c#** и встроить интерактивную кнопку, это руководство покажет, как это сделать. С помощью Aspose.Words вы можете программно добавить кнопку **CommandButton** всего в несколько строк кода, избавившись от необходимости вручную работать с интерфейсом в Word.

В этом уроке вы узнаете, как:

* Инициализировать пустой файл Word с помощью C#.
* Вставить элемент управления ActiveX **CommandButton**.
* Задать свойства кнопки, такие как имя и подпись.
* Сохранить документ, чтобы кнопка отображалась при открытии файла в Microsoft Word.

Никакие внешние инструменты не требуются, кроме библиотеки Aspose.Words for .NET, а шаги работают с .NET 6+ или .NET Framework 4.6.2 и новее.

## Требования

Перед началом убедитесь, что у вас есть:

| Требование | Причина |
|------------|--------|
| .NET 6 SDK (или .NET Framework 4.6.2+) | Предоставляет среду выполнения для проекта C#. |
| Visual Studio 2022 (или любой IDE для C#) | Обеспечивает удобство написания, сборки и запуска кода. |
| Aspose.Words for .NET NuGet‑пакет | Содержит классы `Document`, `DocumentBuilder` и `Forms2OleControl`, используемые в примере. |
| Базовые знания синтаксиса C# | Позволяют следовать коду без дополнительных кривых обучения. |

Вы можете добавить пакет Aspose.Words через консоль NuGet:

```powershell
Install-Package Aspose.Words
```

## Шаг 1: Создать новый консольный проект C#

Создайте консольное приложение, которое будет генерировать Word‑файл. Откройте терминал и выполните:

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Сгенерированный файл `Program.cs` будет содержать код, показанный в последующих шагах.

## Шаг 2: Создать пустой документ и DocumentBuilder

Первой операцией является создание объекта `Document`, представляющего пустой файл `.docx`, и `DocumentBuilder`, позволяющего редактировать содержимое документа.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Почему это важно:**  
`Document` — контейнер для всех элементов Word (абзацы, таблицы, элементы управления). `DocumentBuilder` предоставляет удобный API для вставки объектов в текущую позицию курсора без работы с низкоуровневыми коллекциями узлов.

## Шаг 3: Вставить элемент управления ActiveX CommandButton

Aspose.Words поддерживает вставку устаревших элементов управления ActiveX через метод `InsertForms2OleControl`. Метод требует тип управления и желаемый размер в пунктах.

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**Что происходит за кулисами:**  
Word рассматривает элемент управления ActiveX как объект OLE (Object Linking and Embedding). Класс `Forms2OleControl` оборачивает данные OLE и предоставляет свойства, такие как `Name` и `Caption`.

## Шаг 4: Настроить имя и подпись кнопки

После размещения элемента управления вы можете задать его свойства во время выполнения. Установка осмысленного `Name` помогает позже идентифицировать кнопку, а `Caption` определяет текст, отображаемый на кнопке.

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**Полезный совет:**  
Если вы планируете обрабатывать событие нажатия кнопки с помощью VBA, `Name` становится именем макроса, к которому вы будете обращаться, например, `Sub btnSubmit_Click()`.

## Шаг 5: Сохранить документ на диск

Наконец, запишите документ в файл `.docx`. Выберите папку, в которую у вас есть права записи; в примере используется относительный путь, который разрешается в каталог вывода проекта.

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Запуск программы создаёт `CommandButton.docx`. Открытие файла в Microsoft Word отображает кликабельную кнопку **Submit**:

![Word документ с кнопкой Submit](/images/command-button.png "Скриншот Word‑документа, содержащего кнопку Submit, созданную с помощью C#")

*Текст alt изображения (og_image_alt):* `Скриншот Word‑документа, содержащего кнопку Submit, созданную с помощью C#`

## Проверка результата

1. Запустите Word и откройте `CommandButton.docx`.  
2. Вы должны увидеть кнопку с подписью **Submit** в теле документа.  
3. При наведении курсора на кнопку в панели **Properties** (вкладка Developer → Properties) отобразится имя `btnSubmit`.  

Если кнопка не отображается, убедитесь, что вкладка **Developer** включена в Word (File → Options → Customize Ribbon → установить галочку *Developer*). Элементы управления ActiveX скрыты, когда вкладка отключена.

## Обработка распространённых вариантов и граничных случаев

| Ситуация | Рекомендуемая корректировка |
|-----------|------------------------|
| **Другой размер кнопки** | Измените аргументы ширины и высоты в `InsertForms2OleControl`. Например, `150, 40` создаст большую кнопку. |
| **Несколько кнопок** | Вызывайте `InsertForms2OleControl` многократно, перемещая курсор билдера между вызовами (`builder.Writeln();`). |
| **Кнопка без ActiveX** | Используйте `InsertFormField` для добавления устаревшего поля формы (например, флажка), если нужна совместимость со старыми версиями Word, блокирующими ActiveX. |
| **Кросс‑платформенное использование** | Элементы управления ActiveX работают только в Windows‑версии Word. Для Mac или веб‑просмотрщиков рассмотрите вставку гиперссылки, стилизованной как кнопка. |
| **Предупреждения безопасности** | Word может показать запрос безопасности при открытии документа с элементами управления ActiveX. Подпись документа доверенным сертификатом уменьшит эти трения. |

## Полный, готовый к запуску пример

Ниже приведена полная программа, которую можно скопировать в `Program.cs`. После добавления NuGet‑пакета Aspose.Words она компилируется и запускается без изменений.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Ожидаемый вывод в консоли:**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

Открытие сгенерированного файла показывает готовую к взаимодействию кнопку **Submit**.

## Заключение

Теперь вы знаете, как **create word document c#** и **programmatically add command button** с помощью Aspose.Words. Процесс сводится к инициализации `Document`, вставке `Forms2OleControl`, настройке его свойств и сохранению файла. Дальше вы можете:

* Добавлять другие элементы управления (например, флажки, текстовые поля), изменяя `ControlType`.  
* Привязывать VBA‑макросы к кнопке для пользовательской логики.  
* Комбинировать эту технику с другими возможностями Aspose.Words, такими как слияние писем или заполнение шаблонов.

Экспериментируйте с различными размерами, подписями и несколькими кнопками, чтобы подобрать оптимальное решение для вашего сценария автоматизации. Приятного кодинга!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогая вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}