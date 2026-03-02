---
category: general
date: 2026-03-01
description: Создайте документ Word с помощью Aspose.Words и узнайте, как добавить
  прямоугольную форму, как добавить тень, как установить прозрачность и как создать
  форму — всё на C#.
draft: false
keywords:
- create word document
- add rectangle shape
- how to add shadow
- how to create shape
- how to set transparency
language: ru
og_description: Создайте документ Word с помощью Aspose.Words на C#. Узнайте, как
  добавить прямоугольную форму, применить внешнюю тень и установить прозрачность за
  несколько шагов.
og_title: Создание документа Word с прямоугольной фигурой и тенью – руководство
tags:
- Aspose.Words
- C#
- Document Generation
title: Создание документа Word с прямоугольной фигурой и тенью — пошаговое руководство
url: /ru/net/programming-with-shapes/create-word-document-with-a-rectangle-shape-and-shadow-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание Word‑документа с прямоугольной фигурой и тенью – пошаговое руководство

Когда‑нибудь вам нужно было **создать Word‑документ**, который содержит пользовательский прямоугольник? Возможно, вы создаёте шаблон отчёта и хотите добавить лёгкую тень, чтобы макет выглядел более выразительно. Вы не один — разработчики постоянно спрашивают: «Как программно добавить прямоугольную фигуру и тень?» Хорошая новость: с Aspose.Words это можно сделать в нескольких строках кода.

В этом руководстве мы пройдём весь процесс: от создания пустого Word‑файла, до добавления прямоугольной фигуры и настройки внешней тени с прозрачностью. К концу вы получите готовый к использованию `Shadow.docx`, который можно открыть в Word и сразу увидеть эффект. Никаких внешних инструментов, без сложного XML — только чистый C#‑код и понятные объяснения.

## Что вы узнаете

- **How to create shape** объекты в документе Word с использованием Aspose.Words.
- **How to add rectangle shape** в абзац без нарушения существующего содержимого.
- **How to add shadow** (outer shadow) и управлять её цветом, смещением, размытием и прозрачностью.
- **How to set transparency** тени, чтобы она выглядела профессионально.
- Советы, подводные камни и варианты, которые могут понадобиться в реальных проектах.

### Prerequisites

- .NET 6.0 или новее (API также работает с .NET Framework 4.6+).
- Aspose.Words for .NET, установленный через NuGet (`Install-Package Aspose.Words`).
- Базовое понимание синтаксиса C# — ничего сложного, только обычные `using`‑операторы и создание объектов.

> **Pro tip:** Если вы используете Visual Studio, включите «nullable reference types», чтобы раннее обнаруживать потенциальные ошибки null‑reference.

## Step 1 – Create a Blank Word Document

Чтобы **создать Word‑документ** мы начинаем с класса `Document`. Считайте его пустым холстом; позже можно добавить разделы, абзацы, таблицы или фигуры.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new blank document
Document document = new Document();
```

Зачем нам нужен новый экземпляр `Document`? Потому что каждая фигура, абзац или стиль живут внутри модели объектов документа (DOM). Начало с чистого документа гарантирует, что добавляемый прямоугольник не будет конфликтовать с существующим содержимым.

## Step 2 – Define the Rectangle Shape

Теперь мы **how to create shape** прямоугольник. Конструктор `Shape` принимает документ‑владельца и тип фигуры. Мы также задаём его ширину и высоту в пунктах (1 pt ≈ 1/72 in).

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width = 200;   // 200 pt ≈ 2.78 in
rectangleShape.Height = 100; // 100 pt ≈ 1.39 in
```

Вы можете задаться вопросом: «Могу ли я использовать сантиметры вместо пунктов?» API принимает только пункты, но вы можете конвертировать: `points = centimeters * 28.35`. Это небольшое преобразование удобно, когда вы выравниваете фигуры по полям страницы.

## Step 3 – Add an Outer Shadow and Set Transparency

Здесь происходит магия: **how to add shadow** и **how to set transparency** этой тени. Свойство `ShadowFormat` даёт полный контроль.

```csharp
// Enable shadow visibility
rectangleShape.ShadowFormat.Visible = true;

// Choose a shadow color
rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;

// Set transparency (0 = opaque, 1 = fully transparent)
rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent

// Position the shadow relative to the shape
rectangleShape.ShadowFormat.OffsetX = 5; // horizontal offset in points
rectangleShape.ShadowFormat.OffsetY = 5; // vertical offset in points

// Blur makes the shadow look softer
rectangleShape.ShadowFormat.BlurRadius = 4;

// Specify that this is an outer shadow (instead of inner)
rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;
```

**Почему такие настройки?**  
- **Transparency** позволяет увидеть текстуру подложки страницы, не делая тень слишком тяжёлой.  
- **OffsetX/Y** создают ощущение, что фигура поднята над страницей.  
- **BlurRadius** смягчает края — без него тень выглядела бы как жёсткий прямоугольник, что выглядит неестественно.

Если нужен более драматичный эффект, увеличьте `OffsetX/Y` до 10 и `BlurRadius` до 8. Для более тонкой подсказки оставьте их на 2 и 2 соответственно.

## Step 4 – Insert the Shape into the Document

Мы теперь **add rectangle shape** в первый абзац документа. Если в документе нет содержимого, `FirstParagraph` будет автоматически создан.

```csharp
// Append the rectangle to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

А если нужно разместить фигуру в конкретной ячейке таблицы или в более позднем абзаце? Просто найдите нужный узел (`doc.GetChild(NodeType.Paragraph, index, true)`) и вызовите `AppendChild`. Тот же объект `Shape` можно клонировать, если нужны несколько копий.

## Step 5 – Save the Document

Наконец, мы **создаём Word‑документ** на диске. Используйте путь, подходящий вашей среде; в примере используется заполнитель.

```csharp
// Save the document as a .docx file
document.Save(@"YOUR_DIRECTORY/Shadow.docx");
```

Когда вы откроете `Shadow.docx` в Microsoft Word, вы увидите светло‑серый прямоугольник с мягкой внешней тенью, смещённой вниз‑вправо. Прозрачность тени 30 % гарантирует, что она не будет доминировать над страницей.

---

![Создать Word‑документ с фигурой прямоугольника с тенью](image.png "Создать Word‑документ с фигурой прямоугольника с тенью")

*Текст alt изображения: создать Word‑документ с фигурой прямоугольника с тенью*

## Full, Ready‑to‑Run Code

Ниже полная программа, которую можно скопировать и вставить в консольное приложение. Никаких недостающих частей, никаких «см. документацию».

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Add a rectangular shape and define its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width = 200;   // width in points
        rectangleShape.Height = 100;  // height in points

        // Step 3: Configure an outer shadow for the shape
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;
        rectangleShape.ShadowFormat.Transparency = 0.3;   // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;          // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;          // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;
        rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;

        // Step 4: Insert the shape into the first paragraph of the document
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // Step 5: Save the document with the shadowed shape
        document.Save(@"YOUR_DIRECTORY/Shadow.docx");

        Console.WriteLine("Word document created successfully at YOUR_DIRECTORY/Shadow.docx");
    }
}
```

### Expected Result

- Файл с именем **Shadow.docx** появляется в целевой папке.
- При открытии в Word отображается прямоугольник (200 × 100 pt) с темно‑серой внешней тенью.
- Тень смещена на 5 pt по горизонтали и вертикали, размыта и имеет 30 % прозрачности.

## Common Questions & Edge Cases

| Question | Answer |
|----------|--------|
| **Can I change the shadow color to match my brand?** | Absolutely—just replace `System.Drawing.Color.DarkGray` with any `Color` you prefer, e.g., `Color.FromArgb(255, 0, 120, 215)` for a blue accent. |
| **What if I need an inner shadow instead of outer?** | Set `ShadowFormat.Style = ShadowStyle.InnerShadow`. The rest of the properties behave the same. |
| **Is transparency supported in older Word versions?** | Yes. Aspose.Words writes the appropriate XML that Word 2007+ understands. Older versions may ignore the transparency value but will still show the shadow. |
| **Can I add multiple shapes with different shadows?** | Sure—just create new `Shape` instances, configure each shadow independently, and append them to the desired nodes. |
| **What about performance for hundreds of shapes?** | Creating many shapes can increase memory usage. Reuse a single `Document` instance and add shapes in a loop; dispose of temporary objects if you run into pressure. |

## Tips for Real‑World Projects

- **Batch generation:** При генерации отчётов для множества пользователей создавайте один шаблон `Document` и клонируйте его для каждой итерации. Заменяйте заполнители перед добавлением фигур.
- **Dynamic sizing:** Используйте размеры страницы (`document.FirstSection.PageSetup.PageWidth`), чтобы вычислять размер фигуры относительно страницы, обеспечивая одинаковый макет на разных форматах бумаги.
- **Testing:** Всегда открывайте сгенерированный `.docx` в Word после изменения параметров тени. Визуальная проверка быстрее, чем угадывать числа.

## Next Steps

Теперь, когда вы знаете **how to add rectangle shape**, **how to add shadow** и **how to set transparency**, рассмотрите возможность изучения:

- Добавление **gradient fills** к фигурам (`Shape.FillFormat`).
- Встраивание **pictures** в фигуры для эффекта водяного знака.
- Использование **tables** для выравнивания нескольких фигур с тенью в сетке.
- Экспорт того же документа в PDF (`document.Save("output.pdf")`) с сохранением теней.

Каждый из этих пунктов опирается на те же базовые концепции, поэтому вы будете чувствовать себя уверенно, расширяя код.

---

### Recap

Мы начали с **создания Word‑документа** с помощью Aspose.Words, затем **how to create shape** прямоугольник, применили **how to add shadow**, настроили **how to set transparency** и сохранили результат. Весь процесс укладывается в компактный, переиспользуемый шаблон, который можно адаптировать к любой задаче автоматизации.

Не стесняйтесь экспериментировать — меняйте цвета, играйте со смещениями или комбинируйте несколько фигур. Если возникнут трудности, вернитесь к разделам выше; они созданы как быстрый справочник. Приятного кодинга, и пусть ваши документы всегда выглядят безупречно!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}