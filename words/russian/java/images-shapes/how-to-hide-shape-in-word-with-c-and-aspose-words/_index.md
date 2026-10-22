---
category: general
date: 2026-09-11
description: Узнайте, как скрыть фигуру в Word с помощью C#. В этом руководстве также
  показано, как вставить прямоугольную фигуру и как добавить её в документ Word с
  помощью Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: ru
lastmod: 2026-09-11
og_description: Как скрыть фигуру в Word с помощью C# и Aspose.Words. Следуйте пошаговому
  руководству, чтобы вставить прямоугольную фигуру и управлять фигурами в документе
  Word.
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: Как скрыть форму в Word – полное руководство по C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Как скрыть форму в Word с помощью C# и Aspose.Words
url: /ru/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как скрыть форму в Word с помощью C# и Aspose.Words

Если вам нужно скрыть форму в Word, оставив её в структуре документа, этот учебник покажет, как это сделать. С помощью Aspose.Words for .NET вы можете вставить прямоугольную форму, скрыть её и при этом сохранить её позицию для последующей обработки.

Автоматизация Word часто требует тонкого контроля над формами — будь то генерация шаблонов, подготовка отчётов или построение сервиса редактирования документов. К концу этого руководства вы сможете:

* Вставить прямоугольную форму в документ Word (`insert rectangle shape`).
* Скрыть любую форму без её удаления (`how to hide shape in word`).
* Сохранить результат и убедиться, что скрытая форма не отображается в визуальном представлении (`insert shape into word document`).

Пример работает с Aspose.Words 24.10 или новее и ориентирован на .NET 6.0+, но концепции применимы и к более ранним версиям.

## Требования

* **Aspose.Words for .NET** ≥ 24.10. Бесплатную временную лицензию можно получить на сайте Aspose.
* **.NET SDK** 6.0 или новее, установленный на вашем компьютере.
* Среда разработки, например Visual Studio 2022, VS Code или Rider.
* Базовые знания C# и концепции Word Open XML (необязательно, но полезно).

## Как скрыть форму в Word с помощью Aspose.Words

Ниже приведена полная, готовая к запуску программа, демонстрирующая весь процесс — от создания документа до вставки прямоугольной формы и её последующего скрытия.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### Пояснение к каждому шагу

1. **Создание нового документа** — `Document` представляет файл Word в памяти. `DocumentBuilder` предоставляет удобный API для вставки контента.
2. **Вставка прямоугольной формы** — `InsertShape` создаёт объект рисунка типа `Rectangle`. Размеры задаются в пунктах (1 pt ≈ 1/72 in). Это удовлетворяет требованию `insert rectangle shape`.
3. **Скрытие формы** — Установка `Shape.Hidden = true` помечает форму как скрытую в разметке Word (`<w:hidden/>`). Форма остаётся частью дерева документа, её можно позже раскрыть или обратиться к ней программно. Это ядро задачи `how to hide shape in word`.
4. **Сохранение файла** — Документ записывается в `output.docx`. При открытии в Microsoft Word прямоугольник будет невидим, но он по‑прежнему присутствует в XML и может быть проверен с помощью ZIP‑просмотрщика или Open XML SDK.

### Ожидаемый результат

Откройте `output.docx` в Microsoft Word:

* Документ выглядит пустым — никаких видимых форм.
* Если просмотреть внутренний XML (`word/document.xml`), вы найдёте элемент `<w:pict>` с атрибутом `<w:hidden/>`, подтверждающий, что форма присутствует, но скрыта.

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

Скрытую форму можно снова отобразить, установив `Hidden = false` и повторно сохранив документ.

## Вставка прямоугольной формы в документ Word

Хотя основная цель — скрыть форму, многие сценарии начинаются с её вставки. Метод `InsertShape` поддерживает множество значений `ShapeType`, включая `Rectangle`, `Ellipse`, `Line` и пользовательские изображения.

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**Почему именно прямоугольник?**  
Прямоугольник предоставляет чистый, выровненный по осям контейнер, который может содержать текст, изображения или другие вложенные формы. Он часто используется как заполнитель для динамического контента, такого как таблицы или диаграммы. Вставив прямоугольник сначала, вы сохраняете согласованность макета даже после его последующего скрытия.

## Вставка формы в документ Word — лучшие практики

При `insert shape into word document` учитывайте следующее:

* **Указывайте явные размеры** — Избегайте автоматического масштабирования; задавайте ширину и высоту в пунктах для обеспечения одинакового макета на разных платформах.
* **Определяйте позиционирование** — По умолчанию форма привязывается к текущему абзацу. Используйте `builder.MoveTo` или `builder.StartBookmark` для точного размещения.
* **Применяйте стили заранее** — Цвет заливки, стиль линии и обтекание влияют на окончательный вид. Даже скрытые формы выигрывают от правильного стилизования, поскольку разметка остаётся неизменной.
* **Совместимость версий** — Свойство `Hidden` доступно, начиная с Aspose.Words 24.10. Если вы используете более старую версию, можно вручную добавить атрибут `<w:hidden/>` через API `Node`.

### Ручное добавление атрибута hidden (резервный вариант)

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## Полный сквозной пример

Объединив всё вместе, получаем одну программу, которая:

1. Вставляет прямоугольную форму.
2. Скрывает её.
3. Вставляет видимую эллиптическую форму для контраста.
4. Сохраняет документ.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

Запуск программы создаёт `demo_output.docx`. При открытии вы увидите только коралловый эллипс; зелёный прямоугольник присутствует в XML, но скрыт от отображения.

## Часто задаваемые вопросы и особые случаи

**В: Влияет ли скрытие формы на разбиение на страницы?**  
О: Нет. Скрытые формы игнорируются движком разметки, поэтому они не занимают место. Это удобно для заполнителей, которые не должны влиять на разрывы страниц.

**В: Можно ли скрыть форму, находящуюся в колонтитуле?**  
О: Да. Свойство `Hidden` работает с формами в любой части дерева документа, включая колонтитулы и даже таблицы.

**В: Как скрыть сразу несколько форм?**  
О: Пройдитесь по коллекции `Document.GetChildNodes(NodeType.Shape, true)` и установите `Hidden = true` для каждой нужной формы.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**В: Сохраняется ли атрибут hidden при конвертации в PDF?**  
О: При конвертации в PDF скрытые формы по умолчанию опускаются, что соответствует поведению Word. Если они нужны в PDF, их необходимо раскрыть перед конвертацией.

## Советы и подводные камни

* **Pro tip:** Установите `shape.WrapType = WrapType.None` перед скрытием, если планируете позже раскрыть форму без нарушения окружающего текста.
* **Следите за версиями Aspose.Words:** Свойство `Hidden` бросает `NotSupportedException` до версии 24.10. В этом случае используйте ручной подход с XML.
* **Тестирование:** Всегда открывайте сгенерированный `.docx` в Word и включайте “Show XML markup” (вкладка Developer), чтобы убедиться, что атрибут `<w:hidden/>` присутствует.

## Заключение

Теперь вы знаете, как скрыть форму в Word с помощью C# и Aspose.Words, а также как вставлять прямоугольную форму и управлять её видимостью. Используя свойство `Hidden`, вы можете сохранять формы в модели документа для последующей обработки, предоставляя пользователям чистый вид.

Далее изучайте связанные темы, такие как **обновление свойств формы во время выполнения**, **конвертация скрытых форм в изображения** или **использование Open XML SDK для прямой работы со скрытыми элементами**. Эти расширения углубят ваши навыки.

## Что изучать дальше?

Следующие учебники охватывают тесно связанные темы, построенные на техниках, продемонстрированных в этом руководстве. Каждый ресурс содержит полностью работающие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}