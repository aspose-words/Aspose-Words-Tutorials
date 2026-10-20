---
category: general
date: 2026-09-18
description: Создайте пустой документ Word с помощью C# и задайте текст‑заполнитель,
  затем сохраните документ в формате docx. Узнайте, как вставить элемент управления
  простым текстом и добавить имя заполнителя.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save document as docx
- insert plain text control
- add placeholder name
language: ru
lastmod: 2026-09-18
og_description: Создайте пустой документ Word с помощью C#. Установите текст‑заполнитель,
  вставьте элемент управления простым текстом, добавьте имя заполнителя и сохраните
  документ в формате docx.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: Создать пустой документ Word с текстом‑заполнителем – руководство по C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  headline: Create blank Word document and insert a plain‑text control
  type: TechArticle
- description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  name: Create blank Word document and insert a plain‑text control
  steps:
  - name: An empty Word file (the **blank Word document** you created)
    text: An empty Word file (the **blank Word document** you created)
  - name: A plain‑text content control (the **insert plain text control** step)
    text: A plain‑text content control (the **insert plain text control** step)
  - name: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
    text: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
  - name: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
    text: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
  - name: A line of regular text after the control, demonstrating that normal content
      can follow
    text: A line of regular text after the control, demonstrating that normal content
      can follow
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Создать пустой документ Word и вставить элемент управления простым текстом
url: /ru/java/using-document-elements/create-blank-word-document-and-insert-a-plain-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создайте пустой документ Word и вставьте элемент управления простым текстом

Если вам нужно **программно создать пустой документ Word**, это руководство покажет, как сделать это с помощью C#. Вы узнаете, как **вставить элемент управления простым текстом**, **задать текст‑подсказку**, **добавить имя‑подсказку** и, наконец, **сохранить документ в формате docx**. Шаги полностью автономны, поэтому вы можете скопировать код в любой .NET‑проект и сразу запустить его.

Работа с файлами Word часто требует чистой отправной точки — пустого документа, уже содержащего элементы управления, которые пользователи заполнят. К концу этого руководства у вас будет файл `.docx`, содержащий элемент управления простым текстом с полезной подсказкой, а затем обычный контент.

## Предварительные требования

- .NET 6.0 или новее (код также работает с .NET Framework 4.6+)
- Ссылка на библиотеку **Aspose.Words for .NET** (доступна через NuGet `Install-Package Aspose.Words`)
- Базовые знания консольных приложений C#
- Права записи в папку вывода, указанную в `doc.save(...)`

## Что вы создадите

Итоговый документ (`SDT.docx`) содержит:

1. Пустой файл Word (созданный **пустой документ Word**)
2. Элемент управления простым текстом (шаг **вставить элемент управления простым текстом**)
3. Текст‑подсказка, отображаемый внутри элемента, пока пользователь ничего не ввёл (шаг **задать текст‑подсказку**)
4. Имя‑подсказка, которое можно использовать для программного доступа позже (шаг **добавить имя‑подсказку**)
5. Строка обычного текста после элемента, демонстрирующая, что обычный контент может следовать дальше

## Шаг 1: Создать пустой документ Word

Первой операцией является создание пустого объекта `Document`. Этот объект представляет полностью новый, **пустой документ Word** в памяти.

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Step 1: Create a new blank document
Document doc = new Document();
```

*Почему это важно:* Пустой `Document` даёт вам полный контроль над каждым добавляемым элементом, гарантируя отсутствие скрытых стилей или разделов, которые могли бы помешать вставляемому позже элементу управления.

## Шаг 2: Инициализировать DocumentBuilder

`DocumentBuilder` — вспомогательный класс, позволяющий писать в `Document`. Он отслеживает текущую позицию курсора и предоставляет методы для вставки самых разных объектов Word.

```csharp
// Step 2: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Почему это важно:* Использование `DocumentBuilder` упрощает процесс добавления **элемента управления простым текстом**, поскольку билдер знает точную точку вставки.

## Шаг 3: Вставить элемент управления простым текстом

Теперь добавляем **элемент управления простым текстом** (также известный как Structured Document Tag, или SDT). Тип элемента `StructuredDocumentTagType.PLAIN_TEXT` указывает Word обрабатывать содержимое как простой текст, без форматирования.

```csharp
// Step 3: Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");
```

*Почему это важно:* Метод `InsertStructuredDocumentTag` создаёт элемент управления и возвращает ссылку (`sdt`), которую можно дальше настраивать, например, задавать текст‑подсказку или пользовательское имя.

## Шаг 4: Задать текст‑подсказку и добавить имя‑подсказку

Текст‑подсказка даёт пользователям визуальный сигнал о том, что вводить. Шаг **добавить имя‑подсказку** присваивает программный идентификатор, который позже можно запросить через `doc.GetChildNodes` или аналогичные API.

```csharp
// Step 4a: Set a placeholder text that appears when the SDT is empty
sdt.SetPlaceholderName("Enter text…");

// Step 4b: Add a placeholder name (tag ID) for later retrieval
sdt.Tag = "MyTag";
```

*Почему это важно:* `SetPlaceholderName` управляет серым подсказочным текстом, отображаемым внутри элемента управления. Установка `Tag` (действие **добавить имя‑подсказку**) позволяет находить элемент в дереве документа без полного сканирования файла.

## Шаг 5: Добавить обычный контент после элемента

Чтобы продемонстрировать, что документ продолжается нормально после элемента, выводим простую строку текста.

```csharp
// Step 5: Add regular content after the SDT
builder.Writeln("After the tag.");
```

## Шаг 6: Сохранить документ в формате docx

Наконец, сохраняем документ из памяти на диск. Это операция **сохранить документ как docx**, создающая файл, который можно открыть в Microsoft Word.

```csharp
// Step 6: Save the document as a .docx file
string outputPath = @"YOUR_DIRECTORY/SDT.docx";
doc.Save(outputPath);
```

*Почему это важно:* Формат `.docx` обеспечивает максимальную совместимость с современными версиями Word, Google Docs и другими инструментами, поддерживающими Office‑форматы.

## Полный, готовый к запуску пример

Ниже приведена полная программа, которую можно скопировать в проект консольного приложения. Замените `YOUR_DIRECTORY` реальным путём к папке на вашем компьютере.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

namespace WordSdtExample
{
    class Program
    {
        static void Main()
        {
            // Create a new blank Word document
            Document doc = new Document();

            // Initialize a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // Set a placeholder text that appears when the SDT is empty
            sdt.SetPlaceholderName("Enter text…");

            // Add a placeholder name (tag) for later retrieval
            sdt.Tag = "MyTag";

            // Add regular content after the SDT
            builder.Writeln("After the tag.");

            // Save the document as a .docx file
            string outputPath = @"C:\Temp\SDT.docx"; // change to your folder
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Ожидаемый результат

- При открытии `SDT.docx` в Word отображается пустой серый блок с текстом **Enter text…** внутри.
- Этот блок — элемент управления простым текстом; в него можно вводить текст напрямую.
- Под блоком появляется строка **After the tag.** как обычный абзацный текст.

Если подсказка не отображается, проверьте, что вы используете актуальную версию Aspose.Words (v23.1 или новее) и что документ открывается в версии Word, поддерживающей элементы управления (Word 2007+).

## Распространённые варианты и граничные случаи

| Сценарий | Как адаптировать код |
|----------|----------------------|
| **Несколько подсказок** | Вызовите `InsertStructuredDocumentTag` ещё раз с другим идентификатором тега и именем подсказки. |
| **Элемент управления rich‑text** | Используйте `StructuredDocumentTagType.RichText` вместо `PlainText`. |
| **Установка текста по умолчанию** | После вставки задайте `sdt.Text = "Default value";` — этот текст заменит подсказку при загрузке документа. |
| **Сохранение в поток** | Замените `doc.Save(outputPath);` на `doc.Save(stream, SaveFormat.Docx);`, чтобы отправить файл по HTTP. |
| **Изменение цвета подсказки** | Используйте `sdt.PlaceholderTextColor = System.Drawing.Color.Gray;` (требуется `using System.Drawing`). |

## Профессиональные советы

- **Повторно используйте идентификатор тега**: Сохраняя тег (`MyTag`) одинаковым во всех документах, вы упрощаете последующее автоматическое заполнение данных через `doc.Range.Replace` или `StructuredDocumentTagCollection`.
- **Избегайте жёстко заданных путей**: Используйте `Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "SDT.docx")` для переносимого расположения вывода.
- **Производительность**: Если нужно генерировать тысячи документов, создайте один шаблон `Document` с уже присутствующим SDT, а затем клонируйте его с помощью `doc.Clone()` для каждой итерации.

## Заключение

Теперь вы знаете, как **создать пустой документ Word**, **вставить элемент управления простым текстом**, **задать текст‑подсказку**, **добавить имя‑подсказку** и **сохранить документ в формате docx** с помощью Aspose.Words for .NET. Этот шаблон служит основой для построения шаблонов Word с заполненными формами, автоматических отчётов или любых решений, требующих редактируемых пользователем подсказок.

Экспериментируйте с другими типами элементов управления, комбинируйте несколько подсказок или интегрируйте этот код в веб‑API, который напрямую возвращает сгенерированный файл `.docx` вызывающим. На следующем этапе изучите **заполнение элемента управления данными программно** или **конвертацию сгенерированного Word‑файла в PDF** с помощью встроенных функций конвертации Aspose.Words. Приятного кодинга!


## Что следует изучить дальше?


Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы реализации в ваших проектах.

- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}