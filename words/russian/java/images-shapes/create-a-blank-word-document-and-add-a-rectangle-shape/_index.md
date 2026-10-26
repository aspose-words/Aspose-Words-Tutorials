---
category: general
date: 2026-10-23
description: Создайте пустой документ Word, добавьте форму‑прямоугольник и скройте
  её в Word с помощью Aspose.Words. Пошаговый код для разработчиков .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- how to insert shape
- hide shape word
language: ru
lastmod: 2026-10-23
og_description: Создайте пустой документ Word, добавьте прямоугольник и скройте его
  в Word с помощью Aspose.Words. Следуйте полному примеру на C#.
og_image_alt: Screenshot of a Word document containing a hidden rectangle shape
og_title: Создайте пустой документ Word и добавьте скрытую прямоугольную форму
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create a blank Word document, add a rectangle shape, and hide the shape
    in Word using Aspose.Words. Step‑by‑step code for .NET developers.
  headline: Create a blank Word document and add a rectangle shape
  type: TechArticle
tags:
- Aspose.Words
- .NET
- Word automation
title: Создайте пустой документ Word и добавьте прямоугольную форму
url: /ru/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создайте пустой документ Word и добавьте форму‑прямоугольник

Если вам нужно **создать пустой документ Word**, это руководство покажет, как сделать это с помощью Aspose.Words for .NET. Вы также узнаете, **как вставить форму** — конкретно прямоугольник — и **скрыть форму в Word**, чтобы она не влияла на макет.

В учебнике подробно рассматривается каждая строка кода, объясняется, почему каждый шаг важен, и описываются типичные подводные камни, такие как видимость скрытой формы в разных режимах просмотра Word. К концу вы получите полностью рабочий файл `.docx`, содержащий скрытую форму‑прямоугольник, которую позже можно будет раскрыть или управлять ею программно.

## Предварительные требования

- .NET 6.0 или новее (код также работает с .NET Framework 4.6+)
- NuGet‑пакет Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Среда разработки, например Visual Studio 2022 или VS Code с расширениями C#
- Базовое знакомство с синтаксисом C# и концепциями документов Word

Дополнительная установка Office не требуется, поскольку Aspose.Words полностью работает в памяти.

## Создание пустого документа Word

Первый шаг — создать пустой объект `Document`. Этот объект представляет файл Word, который пока не содержит секций, абзацев или другого контента.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

**Почему это важно:**  
Пустой `Document` дает вам чистый холст. Если начать с готового шаблона, скрытые формы могут унаследовать нежелательные стили. Начало с нуля гарантирует, что добавляемая позже форма будет единственным контролируемым элементом.

## Добавление формы‑прямоугольника в документ

Далее нам нужен `DocumentBuilder` для размещения контента в документе. Метод `InsertShape` билдера — стандартный способ **вставки формы** (прямоугольники, круги, пользовательские рисунки и т.д.).

```csharp
// Step 2: Initialize a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(document);

// Step 3: Insert a rectangle shape of size 200x100 points
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Почему это важно:**  
`InsertShape` возвращает объект `Shape`, который можно дополнительно настроить (цвет, стиль линии и т.п.). Размеры задаются в пунктах (1 пункт = 1/72 дюйма), что соответствует внутренней системе измерений Word.

### Необязательно: стилизация прямоугольника

Если вы хотите, чтобы у прямоугольника была видимая граница после раскрытия, можно задать толщину линии и её цвет:

```csharp
rectangleShape.LineWeight = 0.5;               // Thin border
rectangleShape.LineColor = System.Drawing.Color.Blue;
```

Эти строки необязательны, поскольку форма будет скрыта на следующем этапе.

## Скрытие формы в Word

Word позволяет скрывать формы из макета, оставляя их частью объектной модели документа. Установка свойства `Hidden` в `true` делает форму невидимой в обычном просмотре, но её всё равно можно выбрать через API.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
rectangleShape.Hidden = true;
```

**Почему это важно:**  
Скрытая форма полезна для хранения метаданных, заполнителей для последующей обработки или условного контента, который раскрывается только при определённых обстоятельствах (например, при генерации окончательного отчёта). Форма остаётся в файле, её можно программно раскрыть позже с помощью `rectangleShape.Hidden = false;`.

## Сохранение документа

Наконец, запишите документ на диск. Расширение файла определяет формат Word; `.docx` — современный формат Open XML.

```csharp
// Step 5: Save the document with the hidden shape
string outputPath = @"C:\Temp\HiddenShape.docx";
document.Save(outputPath);
```

**Результат:**  
Открывая `HiddenShape.docx` в Microsoft Word, вы видите пустую страницу. Прямоугольник не виден, но если перейти в **Home → Select → Selection Pane**, форма будет перечислена, и её видимость можно переключать.

## Полный рабочий пример

Ниже приведена полная программа, которую можно скопировать, вставить и запустить. В ней включены все необходимые `using`‑директивы и комментарии.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for content insertion
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape (200x100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Optional styling (comment out if not needed)
        rectangleShape.LineWeight = 0.5;
        rectangleShape.LineColor = System.Drawing.Color.Blue;

        // Hide the shape so it does not appear in the layout
        rectangleShape.Hidden = true;

        // Save the document
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Ожидаемый вывод:**  

- Консоль выводит путь сохранения.  
- `HiddenShape.docx` открывается как пустая страница в Word.  
- Прямоугольная форма существует, но скрыта; её можно проверить через *Selection Pane* или программно, установив `Hidden = false` и переоткрыв файл.

## Часто задаваемые вопросы и особые случаи

| Вопрос | Ответ |
|----------|--------|
| **Можно ли скрыть другие типы форм?** | Да. Любая `Shape` (например, `ShapeType.Ellipse`, `ShapeType.Picture`) поддерживает свойство `Hidden`. |
| **Увеличит ли скрытая форма размер файла?** | Увеличение незначительно (пару килобайт), так как данные формы хранятся в виде XML в пакете `.docx`. |
| **А если форма должна отображаться только в режиме печати?** | Используйте свойство `Shape.IsPrint` вместо `Hidden`. Установка `IsPrint = false` скрывает форму из печатного вывода, но оставляет её видимой на экране. |
| **Как позже раскрыть форму?** | Загрузите документ, найдите форму (например, по `Shape.Name`), затем установите `shape.Hidden = false;` и сохраните. |
| **Работает ли это с форматом .doc (binary)?** | Да, Aspose.Words может сохранять в `.doc` с помощью `document.Save("file.doc");`. Флаг скрытия сохраняется. |

## Профессиональные советы

- **Давайте форму имя**: `rectangleShape.Name = "PlaceholderRectangle";` упростит поиск позже через `document.GetChildNodes(NodeType.Shape, true).Cast<Shape>().FirstOrDefault(s => s.Name == "PlaceholderRectangle")`.
- **Пакетная обработка**: Если нужно добавить скрытые формы во множество документов, вынесите код в метод и переиспользуйте экземпляр `DocumentBuilder`.
- **Производительность**: Создание формы дешево, но частое сохранение больших документов может стать узким местом ввода‑вывода. Рассмотрите использование `MemoryStream` для промежуточной обработки.

## Заключение

Теперь вы знаете, как **создать пустой документ Word**, **добавить форму‑прямоугольник** и **скрыть форму в Word** с помощью Aspose.Words for .NET. Эта техника позволяет внедрять невидимые заполнители, которые можно раскрыть или изменить позже, что полезно для динамической генерации отчётов, условного контента и шаблонизации документов.

Дальнейшие шаги, которые стоит изучить:

- Заменить прямоугольник картинкой или диаграммой с помощью `ShapeType.Picture`.
- Использовать **how to insert shape** в секциях верхнего/нижнего колонтитула для заполнителей‑водяных знаков.
- Сочетать скрытые формы с **add rectangle shape**‑основанной валидацией данных (например, хранить JSON в свойстве `AlternativeText` формы).

Приятного кодинга, экспериментируйте с другими типами форм и параметрами видимости, чтобы адаптировать их под свои задачи автоматизации документов!

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Create Word Document – How to Add Rectangle Shape and Shadow](/words/english/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}