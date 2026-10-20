---
category: general
date: 2026-08-04
description: Создайте документ Word программно, используя C#. Узнайте, как программно
  добавить кнопку команды с помощью Aspose.Words всего за несколько шагов.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: ru
lastmod: 2026-08-04
og_description: Создайте документ Word программно с помощью Aspose.Words. Это руководство
  показывает, как программно добавить кнопку команды, настроить её и сохранить файл.
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: Создание Word‑документа программно – полный учебник по C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Создание документа Word программно — пошаговое руководство
url: /ru/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание Word‑документа программно – полный C#‑урок

Если вам нужно **создать Word‑документ программно**, это руководство покажет, как это сделать с помощью Aspose.Words for .NET. Всего в нескольких строках C# вы сможете сгенерировать пустой файл `.docx`, **программно добавить элементы управления командной кнопкой**, задать их свойства и сохранить результат.  

Ниже описаны все шаги от настройки проекта до обработки граничных случаев, так что вы сможете скопировать код в своё приложение и запустить его без изменений.

## Что вы получите

К концу этого урока вы сможете:

* Инициализировать новый документ Word полностью в памяти.  
* **Программно добавить OLE‑элемент командной кнопки** в любое место и любого размера.  
* Настроить подпись кнопки, внутреннее имя и другие свойства OLE.  
* Сохранить сгенерированный документ на диск или в поток для дальнейшей обработки.

### Предварительные требования

* .NET 6.0 или новее (код также работает с .NET Framework 4.6+).  
* Действительная лицензия Aspose.Words for .NET (или бесплатная оценочная версия).  
* Базовые знания C# и Visual Studio (или любой другой IDE).  

> **Pro tip:** Если запустить пример без лицензии, Aspose.Words добавит небольшую оценочную водяную метку на первую страницу.

## Шаг 1: Настройка проекта и импорт необходимых пространств имён

Создайте новое консольное приложение (или интегрируйте в существующий сервис) и добавьте пакет Aspose.Words через NuGet:

```bash
dotnet add package Aspose.Words
```

Затем подключите необходимые пространства имён в начале вашего `.cs`‑файла:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Эти импорты дают доступ к `Document`, `DocumentBuilder`, `Forms2OleControl` и структуре `RectangleF`, используемой для позиционирования.

## Шаг 2: Инициализация нового документа Word

Первая операция в любом **create word document programmatically**‑процессе – создать объект `Document`. Этот объект существует только в памяти, пока вы явно не сохраните его.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` работает как курсор, отслеживая, где будет размещён следующий элемент. Его использование делает код лаконичным и имитирует ввод непосредственно в Word.

## Шаг 3: Вставка OLE‑элемента командной кнопки

Aspose.Words предоставляет метод `InsertForms2OleControl` для встраивания OLE‑объектов, таких как командные кнопки, флажки или комбобоксы. Методу требуются три аргумента:

1. Значение перечисления `ControlType` (здесь `CommandButton`).  
2. `RectangleF`, определяющий позицию X‑Y и ширину‑высоту элемента (измеряется в пунктах, где 72 pt = 1 inch).  
3. При необходимости дополнительные свойства OLE (для базовой кнопки не нужны).

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Почему это работает:** `InsertForms2OleControl` создаёт OLE‑контейнер в документе и возвращает обёртку `Forms2OleControl`. Через эту обёртку можно управлять вложенным OLE‑объектом (самой кнопкой), не прибегая к низкоуровневому COM‑интеропу.

## Шаг 4: Настройка подписи и внутреннего имени кнопки

После вставки обычно требуется задать пользователю видимую подпись и внутренний идентификатор, к которому может обращаться ваш макрос или ад‑ин.

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

* `Caption` – текст, отображаемый на кнопке в интерфейсе Word.  
* `Name` – программный идентификатор, используемый VBA или внешними скриптами автоматизации.

### Необязательно: Привязать макрос к кнопке

Если планируется запуск VBA‑макроса при нажатии кнопки, можно указать имя макроса:

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **Граничный случай:** Если целевой документ откроют на машине без данного макроса, Word покажет предупреждение о безопасности. Всегда подписывайте макросы или информируйте пользователей о необходимых настройках.

## Шаг 5: Сохранение документа

Файл можно записать на диск, в `MemoryStream` или напрямую в объект ответа веб‑API. Самый простой способ для консольного демо – сохранить в локальную папку:

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Получившийся `.docx` откроется в Microsoft Word с рабочей командной кнопкой, на которой написано «Click Me». При нажатии кнопка вызовет привязанный макрос (если он указан) или просто отобразит сообщение по умолчанию.

## Полный рабочий пример

Скопируйте программу ниже в `Program.cs` и запустите её. Пример демонстрирует весь **create word document programmatically**‑процесс, включая обработку ошибок.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**Ожидаемый результат:** При открытии `CommandButton.docx` в Word отображается кнопка с подписью «Click Me». При наведении курсора на кнопку в панели свойств появляется имя `cmdClickMe`.

## Часто задаваемые вопросы и устранение неполадок

| Вопрос | Ответ |
|----------|--------|
| *Можно ли добавить кнопку в существующий документ?* | Да. Загрузите файл с помощью `new Document("Existing.docx")`, затем используйте тот же вызов `InsertForms2OleControl`. |
| *В каких единицах измеряется `RectangleF`?* | В пунктах (1 inch = 72 pt). Корректируйте значения для точного позиционирования кнопки. |
| *Будет ли кнопка работать в Word for Mac?* | OLE‑элементы поддерживаются только в Windows‑версии Word. На Mac кнопка отображается как статическое изображение. |
| *Нужна ли лицензия для продакшн‑использования?* | Коммерческая лицензия убирает оценочные водяные знаки и раскрывает весь функционал. |
| *Как изменить размер кнопки после вставки?* | Измените `commandButton.Width` и `commandButton.Height` или пере‑вставьте элемент с новым `RectangleF`. |

## Расширение решения

Теперь, когда вы знаете, как **программно добавить командную кнопку**, можете изучить связанные темы:

* **Вставка других элементов управления формой** – используйте `ControlType.CheckBox`, `ControlType.OptionButton` и т.д. (покрывает вторичное ключевое слово *Aspose.Words InsertForms2OleControl*).  
* **Заполнение документа динамическими данными** – объединяйте данные из базы в таблицы или поля слияния.  
* **Экспорт в PDF** – после добавления кнопки вызовите `doc.Save("output.pdf", SaveFormat.Pdf)`, чтобы получить PDF‑версию (релевантно *C# Word automation*).  

## Заключение

У вас теперь есть полностью готовый, пригодный для продакшна шаблон для **create word document programmatically** и **programmatically add command button** с помощью Aspose.Words for .NET. В уроке рассмотрены настройка проекта, инициализация документа, вставка OLE‑кнопки, конфигурация свойств и сохранение файла. Не стесняйтесь адаптировать код для вставки других элементов управления, привязки макросов или интеграции логики в веб‑сервисы и фоновые задачи.

Удачной разработки и приятной автоматизации Word‑документов!

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, помогающие освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}