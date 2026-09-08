---
category: general
date: 2026-09-08
description: Узнайте, как вставить элемент управления содержимым в документ Word с
  помощью C# и Aspose.Words. Включает шаги по созданию элемента управления содержимым,
  установке заполнителя и сохранению файла.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert content control
- create content control
language: ru
lastmod: 2026-09-08
og_description: Вставьте элемент управления содержимым в файл Word с помощью C# и
  Aspose.Words. Следуйте этому руководству, чтобы создать элемент управления содержимым,
  установить текст‑заполнитель и сохранить документ.
og_image_alt: Insert content control example in a Word document
og_title: Вставка элемента управления содержимым в Word с помощью C# – пошаговое руководство
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to insert content control in a Word document using C# and
    Aspose.Words. Includes steps to create content control, set placeholder, and save
    the file.
  headline: How to insert content control in a Word document with C#
  type: TechArticle
tags:
- content control
- Aspose.Words
- C#
- Word automation
title: Как вставить элемент управления содержимым в документ Word с помощью C#
url: /ru/net/programming-with-sdt/how-to-insert-content-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как вставить элемент управления содержимым в документ Word с помощью C#

Если вам нужно **вставить элемент управления содержимым** в документ Word, это руководство покажет вам полное, готовое к выполнению решение. Вы также узнаете, как **создавать элемент управления содержимым** программно, задавать текст‑заполнитель и записывать файл на диск.

Элементы управления содержимым позволяют определять области, которые пользователи могут заполнять, повторять или блокировать. Они широко используются в шаблонах, формах и динамических отчетах. Нижеописанные шаги используют библиотеку Aspose.Words для .NET, которая работает с .NET 6+, .NET Framework 4.6+ и .NET Core.

## Как вставить элемент управления содержимым в документ Word

1. **Добавьте Aspose.Words в ваш проект**  
   Откройте терминал в папке проекта и выполните:

   ```bash
   dotnet add package Aspose.Words
   ```

   Пакет содержит классы `Document`, `DocumentBuilder` и `StructuredDocumentTag`, необходимые для элементов управления содержимым.

2. **Создайте новый пустой документ**  

   ```csharp
   // Step 1: Create a new empty document and a DocumentBuilder
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

   Объект `Document` представляет весь файл .docx, тогда как `DocumentBuilder` предоставляет удобный курсор для вставки узлов.

## Создание элемента управления содержимым с помощью Aspose.Words

Элементы управления содержимым представлены классом `StructuredDocumentTag` (SDT). Следующий код создает **plain‑text** элемент управления содержимым и задает ему заголовок, который можно будет запросить позже.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (content control)
//         - Set a title that can be used to identify the control
//         - Provide placeholder text that appears when the control is empty
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,
    SdtType.PlainText,      // Plain‑text control
    MarkupLevel.Block);    // Block‑level control (behaves like a paragraph)

sdt.Title = "CustomerName";
sdt.PlaceholderName = "Enter name here";
```

*Почему это важно:*  
- `SdtType.PlainText` гарантирует, что элемент принимает только обычные символы.  
- `MarkupLevel.Block` заставляет элемент вести себя как полноценный абзац, что идеально подходит для полей формы.  
- Свойство `Title` является стабильным идентификатором, который можно использовать при поиске или привязке данных.

## Установка текста‑заполнителя и текста по умолчанию

Текст‑заполнитель подсказывает пользователю, что вводить, до того как он начнет печатать. Вы также можете предварительно заполнить элемент управлением содержимым значением по умолчанию.

```csharp
// Step 4: Optionally set default content for the control
sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");
```

XML‑фрагмент должен соответствовать типу данных элемента. Для plain‑text элементов требуется элемент `<text>`. Если пропустить этот шаг, будет отображён ранее определённый текст‑заполнитель.

## Вставка элемента управления содержимым в нужное место

Курсор `DocumentBuilder` определяет, где появится элемент. По умолчанию курсор находится в начале документа.

```csharp
// Step 3: Insert the StructuredDocumentTag into the document at the builder's current position
builder.InsertNode(sdt);
```

Если нужен элемент внутри таблицы, заголовка или после существующих абзацев, сначала переместите билдер:

```csharp
builder.MoveToDocumentEnd();   // Example: place the control at the end of the file
builder.InsertNode(sdt);
```

## Сохранение документа с вставленным элементом управления содержимым

```csharp
// Step 5: Save the document with the content control
doc.Save(@"C:\Temp\SDT.docx");
```

Файл `SDT.docx` теперь содержит plain‑text элемент управления содержимым с заголовком **CustomerName**, текст‑заполнителем «Enter name here» и текстом по умолчанию «John Doe».

![Пример вставки элемента управления содержимым в документ Word](insert-content-control.png)

*Текст альтернативного изображения:* Пример вставки элемента управления содержимым в документ Word

### Ожидаемый результат

При открытии `SDT.docx` в Microsoft Word:

- Серая подсказка «Enter name here» появляется, если удалить текст по умолчанию.  
- Элемент выделяется, когда вы щёлкаете внутри него, указывая, что его можно редактировать.  
- Вкладка **Developer** (если включена) показывает заголовок элемента **CustomerName** в панели свойств.

## Полный рабочий пример

Ниже приведена единая, автономная программа, которую можно скопировать, скомпилировать и запустить. Она демонстрирует каждый шаг от настройки проекта до сохранения файла.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class InsertContentControlDemo
{
    static void Main()
    {
        // 1. Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a plain‑text content control (StructuredDocumentTag)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            doc,
            SdtType.PlainText,
            MarkupLevel.Block);

        sdt.Title = "CustomerName";          // Identifier for later use
        sdt.PlaceholderName = "Enter name here";

        // 3. Insert the control at the current cursor position
        builder.InsertNode(sdt);

        // 4. Set default text (optional)
        sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");

        // 5. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Запустите программу командой `dotnet run`. После выполнения откройте сгенерированный файл, чтобы убедиться, что элемент управления содержимым появился как описано.

## Практические советы и распространённые подводные камни

| Ситуация | Рекомендуемый подход |
|-----------|----------------------|
| **Несколько элементов управления одного типа** | Присвойте каждому элементу уникальный `Title`. Позже можно получить элемент с помощью `doc.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().FirstOrDefault(s => s.Title == "YourTitle")`. |
| **Элемент управления не виден в Word** | Убедитесь, что документ сохранён с расширением `.docx` и что версия `Aspose.Words` совместима с вашей версией Office. |
| **Требуется элемент управления rich‑text** | Используйте `SdtType.RichText` вместо `PlainText`. Тогда XML‑фрагмент будет содержать элементы `<w:richText>`. |
| **Размещение элемента управления внутри ячейки таблицы** | Сначала переместите билдер в ячейку: `builder.MoveTo(cell.FirstParagraph); builder.InsertNode(sdt);`. |
| **Производительность при работе с большими документами** | Создайте `StructuredDocumentTag` один раз и переиспользуйте его, если нужно много одинаковых элементов; клонируйте его через `sdt.Clone(true)`. |

## Следующие шаги

- **Создайте повторяющиеся элементы управления содержимым** (`SdtType.RepeatingSection`) для таблиц, которые динамически расширяются.  
- **Привяжите элементы управления содержимым к XML‑данным** с помощью `sdt.XmlMapping.LoadXml(xmlString)`.  
- **Заблокируйте элемент** (`sdt.LockContentControl = true`), чтобы предотвратить редактирование пользователем, но позволить программные обновления.  

Изучение этих тем углубит ваши навыки создания надёжных шаблонов Word с помощью Aspose.Words.

---

**Заключение**  
Теперь вы знаете, как **вставить элемент управления содержимым** в документ Word с помощью C#. В руководстве рассмотрено создание элемента, установка текста‑заполнителя и текста по умолчанию, вставка в нужное место и сохранение окончательного файла. Имея эту основу, вы сможете создавать сложные формы, шаблоны слияния писем и автоматические отчёты, использующие нативные возможности элементов управления содержимым Word.

## Что следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Установить стиль элемента управления содержимым](/words/english/net/programming-with-sdt/set-content-control-style/)
- [Установить цвет элемента управления содержимым](/words/english/net/programming-with-sdt/set-content-control-color/)
- [Как создавать поля формы и добавлять содержимое с помощью DocumentBuilder в Aspose.Words для Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}