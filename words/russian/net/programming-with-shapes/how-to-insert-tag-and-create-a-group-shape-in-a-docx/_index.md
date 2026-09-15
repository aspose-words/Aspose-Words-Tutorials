---
category: general
date: 2026-09-14
description: Узнайте, как вставлять тег, добавлять фигуры, создавать группу и сохранять
  документ в формате DOCX, используя Aspose.Words в C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert tag
- save document as docx
- how to create group
- how to add shapes
- how to save docx
language: ru
lastmod: 2026-09-14
og_description: Как вставить тег, добавить фигуры, создать группу и сохранить документ
  в формате DOCX с помощью Aspose.Words. Следуйте пошаговому руководству.
og_image_alt: Diagram showing how to insert tag inside a grouped shape before saving
  as DOCX
og_title: Как вставить тег и создать сгруппированную фигуру в DOCX с помощью C#
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to insert tag, add shapes, create a group, and save document
    as DOCX using Aspose.Words in C#.
  headline: How to insert tag and create a group shape in a DOCX
  type: TechArticle
tags:
- Aspose.Words
- C#
- DOCX manipulation
title: Как вставить тег и создать групповую фигуру в DOCX
url: /ru/net/programming-with-shapes/how-to-insert-tag-and-create-a-group-shape-in-a-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как вставить тег и создать групповую форму в DOCX

Если вам нужно знать **how to insert tag** при построении сложного макета, это руководство покажет полное, исполняемое решение. Вы увидите, как добавить фигуры, создать группу и, наконец, **save document as DOCX** с помощью Aspose.Words for .NET.

Генерация документов часто требует сочетания текстовых тегов с графическими элементами. В этом руководстве вы узнаете точно **how to insert tag**, как **add shapes**, как **create group**, и правильный способ **save docx**, чтобы файл можно было открыть в Word без потери качества.

## Предварительные требования

- .NET 6.0 или новее (код также работает с .NET Framework 4.7+)
- NuGet‑пакет Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Базовое знакомство с синтаксисом C#
- IDE, например Visual Studio или VS Code

Дополнительные библиотеки не требуются; весь пример работает с одной ссылкой NuGet.

## Как создать группу и добавить фигуры

Первый логический шаг — создать **group**, которая будет содержать несколько фигур. Группировка удерживает фигуры вместе, когда вы перемещаете или вращаете их позже.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

// 1️⃣ Create an empty document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// 2️⃣ Build a GroupShape (200 × 200 points) and set its bounds
GroupShape groupShape = new GroupShape(document, 200, 200);
groupShape.Bounds = new RectangleF(50, 50, 200, 200);

// 3️⃣ Add a rectangle shape
groupShape.AppendChild(new Shape(document, ShapeType.Rectangle)
{
    Width = 80,
    Height = 80,
    Left = 0,
    Top = 0
});

// 4️⃣ Add an ellipse shape next to the rectangle
groupShape.AppendChild(new Shape(document, ShapeType.Ellipse)
{
    Width = 80,
    Height = 80,
    Left = 100,
    Top = 0
});
```

**Почему это важно:**  
`GroupShape` работает как контейнер. Когда вы позже перемещаете группу, и прямоугольник, и эллипс перемещаются вместе, сохраняя свои относительные позиции. Это рекомендуемый способ управления несколькими графическими элементами, принадлежащими к одному логическому блоку.

## Как вставить тег в документ

Теперь, когда группа готова, вы можете **insert tag** (StructuredDocumentTag, также известный как SDT) сразу после группы. Тег может содержать обычный текст, форматированный текст или даже повторяющийся контент.

```csharp
// 5️⃣ Insert the group at the current builder position
builder.InsertNode(groupShape);

// 6️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and write content
builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");
builder.Writeln("Content inside the SDT");
```

**Почему следует использовать StructuredDocumentTag:**  
SDT предоставляет семантический маркер, который Word может распознать для элементов управления содержимым, привязки данных или сценариев заполнения форм. Используя `InsertStructuredDocumentTag`, вы явно **how to insert tag** таким образом, чтобы он сохранялся при последующем редактировании в Microsoft Word.

## Как сохранить docx и проверить результат

Последний шаг — сохранить документ. Приведённый ниже код демонстрирует правильный способ **save document as docx** и где найти выходной файл.

```csharp
// 7️⃣ Save the document to the file system
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "GroupAndSDT.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Когда вы откроете *GroupAndSDT.docx* в Word, вы должны увидеть сгруппированную графику прямоугольник‑эллипс, за которой следует элемент управления содержимым обычного текста с названием **MyTag**, содержащий строку «Content inside the SDT».

### Ожидаемый результат

- Группа размером 200 × 200 пунктов, расположенная в точке (50, 50) на странице.
- Внутри группы: синний прямоугольник слева и эллипс справа (цвета по умолчанию).
- Сразу под группой: элемент управления содержимым с меткой **MyTag** и текстом «Content inside the SDT».

## Полный, исполняемый пример

Ниже приведена полная программа, которую вы можете скопировать и вставить в консольное приложение. Она включает все необходимые директивы `using`, обработку ошибок и комментарии, объясняющие каждый шаг.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeWordsGroupAndTag
{
    class Program
    {
        static void Main()
        {
            // Create a new empty document and a DocumentBuilder to work with it
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Build a GroupShape (200x200) and define its bounds
            GroupShape groupShape = new GroupShape(document, 200, 200);
            groupShape.Bounds = new RectangleF(50, 50, 200, 200);

            // Add a rectangle to the group
            groupShape.AppendChild(new Shape(document, ShapeType.Rectangle)
            {
                Width = 80,
                Height = 80,
                Left = 0,
                Top = 0
            });

            // Add an ellipse to the group
            groupShape.AppendChild(new Shape(document, ShapeType.Ellipse)
            {
                Width = 80,
                Height = 80,
                Left = 100,
                Top = 0
            });

            // Insert the group into the document at the current builder position
            builder.InsertNode(groupShape);

            // Insert a plain‑text StructuredDocumentTag (SDT) and write some content inside it
            builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");
            builder.Writeln("Content inside the SDT");

            // Save the resulting document
            string outputPath = Path.Combine(
                Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
                "GroupAndSDT.docx");

            document.Save(outputPath);
            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

Запустите программу, перейдите к своему рабочему столу и дважды щёлкните *GroupAndSDT.docx*, чтобы убедиться, что группа и тег отображаются как описано.

## Часто задаваемые вопросы и особые случаи

| Вопрос | Ответ |
|----------|--------|
| **Можно ли добавить более двух фигур в группу?** | Да. Вызовите `groupShape.AppendChild(new Shape(...))` для каждой дополнительной фигуры перед вставкой группы. |
| **Что делать, если нужен тег rich‑text вместо plain‑text?** | Используйте `StructuredDocumentTagType.RichText` в `InsertStructuredDocumentTag`. |
| **Как изменить цвет прямоугольника или эллипса?** | Установите свойство `FillColor` у каждого экземпляра `Shape`, например, `shape.FillColor = Color.LightBlue;`. |
| **Можно ли вращать всю группу?** | Установите `groupShape.Rotation = 45;` (градусы) перед вставкой узла. |
| **Нужно ли вызывать `Dispose()` для каких‑либо объектов?** | Aspose.Words управляет большинством ресурсов самостоятельно; вызов `Dispose()` для `Document` необязателен в короткоживущем консольном приложении. |

## Лучшие практики сохранения файлов DOCX

- **Всегда используйте абсолютный путь** (или чётко определённый относительный путь) при вызове `document.Save`. Это предотвращает ошибку «файл не найден», которая может возникнуть из‑за неоднозначных рабочих каталогов.
- **Предпочитайте перегрузки `Save`, принимающие поток**, если вам нужно отправить документ по HTTP или сохранить его в базе данных.
- **Установите `CompatibilityOptions`**, если необходимо целиться в более старые версии Word (например, Word 2003). Для большинства современных сценариев параметры по умолчанию работают нормально.

## Следующие шаги

Теперь, когда вы знаете **how to insert tag**, как **add shapes**, как **create group** и как **save docx**, вы можете изучать более продвинутые сценарии:

- Объединяйте несколько групп для построения сложных диаграмм.
- Используйте `StructuredDocumentTag` для привязки данных в шаблонах Word.
- Экспортируйте тот же документ в PDF (`document.Save("output.pdf")`), сохраняя сгруппированную графику.
- Автоматизируйте заполнение форм, программно задавая содержимое SDT (`builder.MoveToDocumentEnd(); builder.Write("New value");`).

Экспериментируйте с различными значениями `ShapeType` (например, `ShapeType.Polygon`, `ShapeType.Line`), чтобы увидеть, как они ведут себя внутри `GroupShape`. Та же схема работает для таблиц, изображений или любого другого узла, который вы хотите держать вместе.

---

**Итоги:** В этом руководстве продемонстрировано **how to insert tag** внутри групповой формы, как **add shapes**, как **create group**, и правильный способ **save document as docx** с использованием Aspose.Words for .NET. Теперь у вас есть прочная база для программного создания богатых интерактивных файлов DOCX.

## Что изучать дальше?

Следующие руководства охватывают тесно связанные темы, опирающиеся на техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Как сохранить Markdown из DOCX – пошаговое руководство](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [Как восстановить DOCX – полное руководство с использованием Aspose.Words](/words/english/net/programming-with-loadoptions/how-to-recover-docx-complete-guide-using-aspose-words/)
- [Как проверить грамматику в DOCX с помощью Aspose.Words – использовать gpt-4 turbo](/words/english/net/ai-powered-document-processing/how-to-check-grammar-in-docx-with-aspose-words-use-gpt-4-tur/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}