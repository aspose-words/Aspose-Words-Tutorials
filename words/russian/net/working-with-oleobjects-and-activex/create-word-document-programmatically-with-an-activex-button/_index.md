---
category: general
date: 2026-10-20
description: Создайте документ Word программно и добавьте кнопку команды с помощью
  Aspose.Words. Узнайте, как вставить элемент управления ActiveX и задать подпись
  кнопки.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: ru
lastmod: 2026-10-20
og_description: Создайте документ Word программно и внедрите кнопку ActiveX. В этом
  руководстве объясняется, как вставить элемент управления и задать его подпись с
  помощью Aspose.Words.
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: Создать документ Word программно – добавить кнопку ActiveX
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Создать документ Word программно с помощью кнопки ActiveX
url: /ru/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание Word‑документа программно с помощью кнопки ActiveX

Создайте Word‑документ программно с помощью Aspose.Words, а затем добавьте кнопку‑команду, по которой пользователи могут кликать. Это руководство покажет, как вставить элемент управления ActiveX, настроить его свойства и сохранить результат в файл **.docx**.

Вы увидите полностью готовый, исполняемый пример, который можно скопировать в консольное приложение. К концу урока вы сможете генерировать Word‑файл, содержащий полностью функционирующую кнопку‑команду, и поймёте, как **add command button**, **add activex control**, **insert activex button** и **set button caption** без выхода из кода C#.

## Prerequisites

Прежде чем начать, убедитесь, что у вас есть:

* .NET 6.0 SDK или более поздняя версия, установленная  
* Visual Studio 2022 (или любая IDE, поддерживающая C#)  
* Файл лицензии Aspose.Words for .NET (бесплатная trial‑версия подходит для этого примера)  
* Базовые знания C# и системы проектов .NET  

Дополнительные пакеты NuGet не требуются, кроме **Aspose.Words**, так как поддержка ActiveX встроена в библиотеку.

## Step 1: Set up the project and add Aspose.Words

1. Откройте терминал или Visual Studio и создайте новый консольный проект:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. Добавьте пакет Aspose.Words:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (Опционально) Если у вас есть файл лицензии, поместите его в корень проекта и добавьте следующую строку в начало `Program.cs`, чтобы избавиться от водяных знаков оценки:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## Step 2: Create Word document programmatically – initialize the document

Первая операция — **create Word document programmatically**. Делается это путём создания объекта `Document` и `DocumentBuilder`, который позволяет редактировать содержимое документа.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` представляет весь файл, а `DocumentBuilder` поддерживает курсор, который можно перемещать в любое место документа. Такое разделение сохраняет чистоту API и позволяет **add activex control** позже без ручного управления низкоуровневыми структурами.

## Step 3: Add command button – inserting an ActiveX control

Теперь вы **add command button**, вставив элемент управления ActiveX типа `OleControlType.CommandButton`. Метод `InsertForms2OleControl` требует тип управления, расположение (`Point`) и размер (`Size`).

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

Вызов выше **insert activex button** в документ в точных координатах, которые вы укажете. Координаты измеряются в пунктах (1 pt ≈ 1/72 in). Если нужна кнопка в конкретном абзаце, сначала переместите курсор билдера:

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## Step 4: Set button caption – customizing the command button text

Кнопка без подписи сбивает с толку, поэтому вы **set button caption** на что‑то осмысленное. Свойство `Caption` задаёт текст, отображаемый на кнопке, а `Name` даёт элементу программный идентификатор.

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

Если позже вы экспортируете документ в формат с поддержкой макросов (`.docm`), значение `OnClick` должно совпадать с именем VBA‑макроса. Для обычного `.docx` свойство сохраняется, но не исполняется, что приемлемо для большинства сценариев автоматизации.

## Step 5: Save the document containing the ActiveX button

После настройки элемента управления вы можете **save the document**. Выберите каталог, в который у вас есть права записи, и используйте расширение `.docx` для максимальной совместимости.

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

Когда вы откроете сгенерированный файл в Microsoft Word, вы увидите кнопку с надписью **Submit** в указанных координатах. Нажатие на кнопку в настольном клиенте попытается выполнить макрос `SubmitForm` (если он существует).

## Step 6: Verify the result and troubleshoot common issues

1. Откройте `ActiveXCommandButton.docx` в Microsoft Word.  
2. Перейдите в **Design Mode** (вкладка Developer → **Design Mode**), чтобы увидеть границы кнопки.  
3. Если кнопка не отображается, проверьте, включена ли вкладка **Developer** и поддерживает ли ваша версия Word элементы управления ActiveX.  
4. Для файлов с макросами (`.docm`) убедитесь, что имя макроса в `OnClick` совпадает с процедурой VBA; иначе Word покажет предупреждение о безопасности.

### Pro tip

Элементы управления ActiveX работают только в Windows. Если нужна кроссплатформенная интерактивность, рассмотрите использование **Content Controls** (`RichTextContentControl`) вместо кнопки ActiveX.

## Full source code

Ниже приведена полная, готовая к запуску программа. Скопируйте её в `Program.cs` и выполните `dotnet run`.



## What Should You Learn Next?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы реализации в собственных проектах.

- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [create word document button with Aspose.Words – Full Code Example](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}