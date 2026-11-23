---
category: general
date: 2026-11-22
description: Программно создать документ Word на C# и вставить прямоугольную форму,
  добавить несколько фигур и записать их в Word с помощью Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: ru
lastmod: 2026-11-22
og_description: Программно создавать документ Word на C# путем вставки прямоугольной
  формы, вставки нескольких форм и записи форм в Word с использованием Aspose.Words.
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: Программно создавать документ Word с фигурами на C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Программно создавать документ Word с фигурами на C#
url: /ru/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Программное создание Word‑документа с фигурами на C#

Если вам нужно **программно создать Word‑документ**, содержащий пользовательскую графику, это руководство покажет, как сделать это с помощью Aspose.Words for .NET. Вы научитесь вставлять прямоугольную фигуру, добавлять дополнительные фигуры, группировать их и, наконец, записывать фигуры в Word — всё в нескольких строках C#.

Создание Word‑файла с графикой больше не требует ручного редактирования или макросов. К концу этого урока у вас будет переиспользуемый метод, который генерирует файл `.docx` с прямоугольником и эллипсом, сгруппированными вместе, готовыми к дальнейшей обработке или отчетности.

## Что вам понадобится

- .NET 6.0 или новее (код также работает с .NET Framework 4.6+)
- Aspose.Words for .NET (NuGet‑пакет `Aspose.Words`)
- IDE, например Visual Studio 2022 (подойдёт любой редактор, способный компилировать C#)

> **Pro tip:** Установите пакет с помощью команды CLI `dotnet add package Aspose.Words` перед тем, как начать писать код.

## Программное создание Word‑документа – обзор

Общий процесс состоит из трёх логических фаз:

1. **Инициализация** нового `Document` и `DocumentBuilder`.  
2. **Вставка нескольких фигур** (прямоугольника и эллипса) и размещение их внутри `GroupShape`.  
3. **Запись фигур в Word** путём сохранения `Document` в файл `.docx`.

Каждая фаза оформлена в отдельном шаге ниже, так что вы можете скопировать‑вставить код прямо в свой проект.

![Программное создание Word‑документа с группированными фигурами](grouped-shapes.png){: .align-center alt="Программное создание Word‑документа с группированными фигурами"}

## Шаг 1: Инициализация документа и билдера

Класс `Document` представляет весь Word‑файл, а `DocumentBuilder` предоставляет удобный API для добавления содержимого.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Почему это важно:* Создание `Document` в первую очередь даёт чистый холст. `DocumentBuilder` отслеживает текущую точку вставки, что критично, когда позже вы будете привязывать фигуры к иерархии абзацев.

## Шаг 2: Вставка контейнера групповой фигуры

`GroupShape` позволяет рассматривать несколько отдельных фигур как единый объект. Это удобно, когда нужно перемещать или масштабировать их вместе.

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*Объяснение:* `InsertGroupShape` вставляет пустой контейнер и автоматически делает его текущей фигурой. Все последующие вставки фигур будут добавляться в этот контейнер, пока вы не закроете группу.

### Вставка прямоугольной фигуры

Теперь добавляем первую графику — прямоугольник. Это удовлетворяет требованию **insert rectangle shape**.

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Прямоугольник наследует контекст форматирования группы, поэтому он появляется внутри `GroupShape`. При необходимости позже можно задать цвет линии, заливку или текст.

### Вставка нескольких фигур

Чтобы продемонстрировать возможность **insert multiple shapes**, сразу после прямоугольника добавляем эллипс. Вы можете продолжать добавлять любое количество фигур (например, треугольники, звёзды) до закрытия группы.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

На данном этапе группа содержит две отдельные фигуры: прямоугольник и эллипс. Поскольку они имеют общего родителя, их можно перемещать как единый объект.

## Шаг 3: Присоединение групповой фигуры к иерархии абзацев

Word‑документы хранят содержимое в дереве абзацев. Чтобы группа была видна в конечном файле, её необходимо присоединить к текущему абзацу.

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*Почему этот шаг необходим:* Без добавления группы в абзац фигуры останутся только в памяти и будут опущены при сохранении документа.

## Шаг 4: Сохранение документа – запись фигур в Word

Наконец, сохраняем `Document`, находящийся в памяти, на диск. Это реализует цель **write shapes to word**.

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Когда вы откроете `GroupShape.docx` в Microsoft Word, вы увидите прямоугольник и эллипс, сгруппированные вместе, точно так, как их вставил код.

### Ожидаемый результат

- Файл с именем **GroupShape.docx**, расположенный в папке вывода проекта.  
- Внутри Word‑файла: один абзац, содержащий сгруппированный прямоугольник (100 pt × 50 pt) и эллипс (80 pt × 40 pt). Выбор любой фигуры выделяет всю группу.

## Обработка распространённых граничных случаев

| Ситуация | Рекомендация |
|-----------|----------------|
| **Разный DPI или размер страницы** | Явно задайте `builder.PageSetup.PaperSize` перед вставкой фигур, чтобы избежать неожиданного масштабирования. |
| **Необходимо точно позиционировать фигуры** | Используйте `builder.MoveTo` для перемещения точки вставки, затем задайте свойства `groupShape.Left` и `groupShape.Top` (значения указываются в пунктах). |

## Что вам следует изучить дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом уроке. Каждый ресурс включает полностью работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Создать Word‑документ – вставить прямоугольную фигуру и тень на C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Создать Word‑документ программно и группировать фигуры на C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Программно создать Word‑документ с групповой фигурой](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}