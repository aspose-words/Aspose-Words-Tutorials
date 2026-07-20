---
category: general
date: 2026-07-19
description: Группируйте фигуры в Word с помощью Aspose.Words. Узнайте, как добавить
  прямоугольную фигуру, определить эллипс и вставить фигуру в документы Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- how to group shapes
- insert shape into word
- define ellipse shape
language: ru
lastmod: 2026-07-19
og_description: Группировка фигур в Word с помощью Aspose.Words. Добавление прямоугольной
  фигуры, определение эллипса и вставка фигуры в документы Word.
og_image_alt: Screenshot of grouped shapes in a Word document created with Aspose.Words
og_title: Группировка фигур в Word – пошаговое руководство по C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  headline: Group Shapes in Word with Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  name: Group Shapes in Word with Aspose.Words – Complete C# Guide
  steps:
  - name: Set Up the Document and Builder
    text: We start by creating an empty `Document` and a `DocumentBuilder`. The builder
      is our “pen” that lets us insert content wherever we need it.
  - name: Add Rectangle Shape (add rectangle shape)
    text: Now we **add rectangle shape** to the document. We set its size, position,
      and fill colour to make it stand out.
  - name: Define Ellipse Shape (define ellipse shape)
    text: Next, we **define ellipse shape**. Notice the different `ShapeType` and
      the offset (`Left = 120`) so the ellipse sits beside the rectangle.
  - name: (Optional) Insert Individual Shapes for Preview
    text: If you want to see each shape before grouping, you can **insert shape into
      Word** individually. This step is optional but handy for debugging.
  - name: How to Group Shapes – Create a GroupShape
    text: 'Here’s the core of the tutorial: **how to group shapes**. We create a `GroupShape`,
      attach our rectangle and ellipse, and decide how the group behaves with surrounding
      text.'
  - name: Insert the Grouped Shape into the Document (insert shape into word)
    text: Now we **insert shape into Word**—but this time it’s the grouped container,
      not the individual pieces.
  - name: Save the Document
    text: Finally, write the file to disk. You can change the path to suit your project
      layout.
  - name: What if I need more than two shapes?
    text: Just keep calling `groupShape.AppendChild(yourNewShape);` before inserting
      the group. The API imposes no limit on the number of child shapes.
  - name: Can I rotate or resize the whole group?
    text: Absolutely. `GroupShape` inherits from `Shape`, so you can set properties
      like `RotationAngle`, `Width`, or `Height` on the group itself, and all child
      shapes will follow.
  - name: How do I change the group’s background colour?
    text: Use `groupShape.FillColor`. This fills the invisible bounding box; it can
      be handy for highlighting.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: Группировка фигур в Word с Aspose.Words — Полное руководство по C#
url: /ru/net/programming-with-shapes/group-shapes-in-word-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Группировка фигур в Word – Полное руководство на C#

Когда‑нибудь задавались вопросом, как **группировать фигуры в Word** без возни с пользовательским интерфейсом? Вы не одиноки. Будь то генерация контрактов, листовок или диаграмм программным способом, возможность **добавить прямоугольную фигуру**, **определить эллипс** и затем **группировать фигуры в Word** может сэкономить часы ручной работы.

В этом руководстве мы пройдем реальный пример с использованием **Aspose.Words for .NET**. К концу вы точно будете знать, как **вставить фигуру в Word**, объединить их и получить отшлифованный документ, готовый к отправке клиентам или коллегам.

---

## Что понадобится

Прежде чем погрузиться в детали, убедитесь, что у вас есть следующее:

- **Aspose.Words for .NET** (последняя версия, например, 24.9). Вы можете получить её из NuGet с помощью `Install-Package Aspose.Words`.
- Среда разработки .NET (Visual Studio 2022 или VS Code с расширением C# подойдут отлично).
- Базовое знакомство с синтаксисом C# — ничего сложного, только обычные `using`‑директивы и создание объектов.

И всё. Никаких дополнительных библиотек, без COM‑interop, только чистый управляемый код.

---

## Как группировать фигуры в Word с помощью Aspose.Words

Ниже представлено пошаговое разборное описание, которое отражает ваш текущий код. Каждый шаг объясняет **почему** мы делаем то или иное, а не только **что** делает строка, чтобы вы могли адаптировать шаблон под любые фигуры.

### Шаг 1: Создание документа и билдера

Мы начинаем с создания пустого `Document` и `DocumentBuilder`. Билдер — наш «перо», позволяющее вставлять контент в нужные места.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
// The builder will help us place shapes and text
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Почему?** Объект `Document` представляет весь файл .docx, а `DocumentBuilder` предоставляет удобный API для вставки узлов (например, фигур) без необходимости напрямую работать с деревом узлов.

### Шаг 2: Добавление прямоугольной фигуры (add rectangle shape)

Теперь мы **добавляем прямоугольную фигуру** в документ. Устанавливаем её размер, позицию и цвет заливки, чтобы она выделялась.

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 100;                     // Width in points
rectangleShape.Height = 50;                      // Height in points
rectangleShape.Left   = 0;                       // X‑coordinate
rectangleShape.Top    = 0;                       // Y‑coordinate
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

> **Подсказка:** Вы можете изменить `FillColor` на любой `System.Drawing.Color`, который вам нужен. Это удобно, когда требуется цветовое кодирование разделов в отчёте.

### Шаг 3: Определение эллипса (define ellipse shape)

Далее мы **определяем эллипс**. Обратите внимание на другой `ShapeType` и смещение (`Left = 120`), чтобы эллипс оказался рядом с прямоугольником.

```csharp
// Create an ellipse shape
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width  = 80;
ellipseShape.Height = 40;
ellipseShape.Left   = 120;   // Position it to the right of the rectangle
ellipseShape.Top    = 0;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

> **Почему это важно:** Явно задавая позицию фигур, вы контролируете их расположение до группировки. При автоматическом размещении группировка может получиться смещённой.

### Шаг 4: (Опционально) Вставка отдельных фигур для предварительного просмотра

Если хотите увидеть каждую фигуру перед группировкой, можете **вставить фигуру в Word** по отдельности. Этот шаг необязателен, но полезен для отладки.

```csharp
// Insert the rectangle and ellipse separately (useful for preview)
builder.InsertNode(rectangleShape);
builder.InsertNode(ellipseShape);
```

> **Профессиональный совет:** Закомментируйте эти две строки, как только убедитесь, что фигуры выглядят правильно; иначе после группировки вы получите дублирующиеся визуальные элементы.

### Шаг 5: Как группировать фигуры — создание GroupShape

Вот ядро руководства: **как группировать фигуры**. Мы создаём `GroupShape`, присоединяем наш прямоугольник и эллипс и определяем, как группа будет вести себя относительно окружающего текста.

```csharp
// Create a container for the group
GroupShape groupShape = new GroupShape(document);

// Add the rectangle and ellipse to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// Set wrapping – Inline makes the group act like a character in the text flow
groupShape.WrapType = WrapType.Inline;
```

> **Объяснение:** `GroupShape` по сути мини‑холст, содержащий другие фигуры. Установив `WrapType` в `Inline`, вся группа перемещается как единый объект при добавлении или удалении текста.

### Шаг 6: Вставка сгруппированной фигуры в документ (insert shape into word)

Теперь мы **вставляем фигуру в Word**, но на этот раз это уже сгруппированный контейнер, а не отдельные элементы.

```csharp
// Insert the grouped shape at the current cursor position
builder.InsertNode(groupShape);
```

> **Что происходит «под капотом»?** Вызов `InsertNode` добавляет `GroupShape` в коллекцию узлов документа. Поскольку группа уже содержит прямоугольник и эллипс, они отображаются вместе как один объект.

### Шаг 7: Сохранение документа

Наконец, записываем файл на диск. При необходимости измените путь под структуру вашего проекта.

```csharp
// Save the resulting .docx file
document.Save("YOUR_DIRECTORY/GroupShape.docx");
```

> **Результат:** Откройте `GroupShape.docx` в Microsoft Word, и вы увидите светло‑голубой прямоугольник и коралловый эллипс, закреплённые вместе. Перетаскивание одного перемещает и другой — именно то, что обещает «группировать фигуры в Word».

---

## Визуальная проверка

Ниже показан макет того, как выглядят сгруппированные фигуры внутри Word‑файла.  

![Screenshot of grouped shapes in a Word document created with Aspose.Words](grouped_shapes_placeholder.png "group shapes in word")

*Текст alt‑изображения содержит основной ключевой запрос для доступности и SEO.*

---

## Часто задаваемые вопросы и особые случаи

### Что делать, если нужно больше двух фигур?

Просто продолжайте вызывать `groupShape.AppendChild(yourNewShape);` перед вставкой группы. API не накладывает ограничений на количество дочерних фигур.

### Можно ли вращать или изменять размер всей группы?

Конечно. `GroupShape` наследуется от `Shape`, поэтому вы можете задавать такие свойства, как `RotationAngle`, `Width` или `Height` непосредственно у группы, и все дочерние фигуры будут следовать за изменениями.

```csharp
groupShape.RotationAngle = 15;   // Rotate the entire group 15 degrees
groupShape.Width = 250;          // Stretch the group uniformly
```

### Как изменить цвет фона группы?

Используйте `groupShape.FillColor`. Это заполняет невидимый ограничивающий прямоугольник; может пригодиться для выделения.

```csharp
groupShape.FillColor = System.Drawing.Color.LightGray;
```

### Работает ли это со старыми форматами Word (.doc)?

`Aspose.Words` умеет сохранять и в `.doc`. Просто замените расширение файла в `Save`. Однако некоторые продвинутые возможности фигур (например, группировка) полностью поддерживаются только в формате OOXML `.docx`.

---

## Полный рабочий пример

Скопируйте‑вставьте следующий блок в новое консольное приложение, чтобы увидеть весь процесс в действии. Ничего не упущено; это **полный, исполняемый пример**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Add rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 100;
        rectangleShape.Height = 50;
        rectangleShape.Left   = 0;
        rectangleShape.Top    = 0;
        rectangleShape.FillColor = Color.LightBlue;

        // 3️⃣ Define ellipse shape
        Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
        ellipseShape.Width  = 80;
        ellipseShape.Height = 40;
        ellipseShape.Left   = 120;
        ellipseShape.Top    = 0;
        ellipseShape.FillColor = Color.LightCoral;

        // 4️⃣ (Optional) Preview individual shapes
        // builder.InsertNode(rectangleShape);
        // builder.InsertNode(ellipseShape);

        // 5️⃣ Group the shapes together
        GroupShape groupShape = new GroupShape(document);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.WrapType = WrapType.Inline;

        // 6️⃣ Insert the grouped shape into the document
        builder.InsertNode(groupShape);

        // 7️⃣ Save the file
        document.Save("GroupShape.docx");

        System.Console.WriteLine("Document created successfully!");
    }
}
```

**Ожидаемый результат:** При открытии `GroupShape.docx` вы увидите один сгруппированный объект, состоящий из светло‑голубого прямоугольника и светло‑кораллового эллипса, идеально выровненных рядом.

---

## Итоги

Мы рассмотрели всё, что нужно для **группировки фигур в Word** с помощью Aspose.Words:

1. Создайте документ и билдер.  
2. **Добавьте прямоугольную фигуру** и **определите эллипс** с явными размерами.  
3. (Опционально) **вставьте фигуру в Word** для быстрой проверки.  
4. Используйте `GroupShape` для **группировки фигур** — добавьте каждый дочерний элемент, задайте обтекание и вставьте.  
5. Сохраните файл и проверьте результат.

## Что изучать дальше?

Следующие руководства охватывают близкие темы, расширяющие техники, продемонстрированные в этом пособии. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, помогая вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}