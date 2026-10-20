---
category: general
date: 2026-08-07
description: Вставьте прямоугольную форму в C# с помощью Aspose.Words и узнайте, как
  скрыть форму, задать цвет заливки и эффективно добавить прямоугольную форму в документ
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: ru
lastmod: 2026-08-07
og_description: Вставьте прямоугольную форму в документ Word с помощью C#. Узнайте,
  как скрыть форму, задать цвет заливки и добавить прямоугольную форму, используя
  Aspose.Words.
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: Вставка прямоугольной фигуры в C# – полный учебник по Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: Вставка прямоугольной формы в C# с Aspose.Words – пошаговое руководство
url: /ru/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Вставка прямоугольной фигуры в C# с Aspose.Words – пошаговое руководство

Если вам нужно **вставить прямоугольную фигуру** в документ Word из C#, это руководство покажет, как это сделать. Вы увидите, как задать цвет заливки, скрыть фигуру, чтобы она не отображалась в окончательном макете, и сохранить файл — всё это с помощью нескольких строк кода.

В последующих разделах мы рассмотрим всё, что вам необходимо знать: предварительные требования, полный список кода, объяснения каждого шага и советы по распространённым вариантам, таким как повторное отображение фигуры или использование другого цвета. К концу вы сможете **добавлять прямоугольную фигуру** в любой файл .docx программно.

## Предварительные требования

Прежде чем начать, убедитесь, что у вас есть:

* **Aspose.Words for .NET** (версия 23.10 или новее). Установить её можно через NuGet:

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK или более поздняя версия, установленная на вашем компьютере.
* Базовые знания C# и Visual Studio (или любой другой предпочитаемой IDE).

Дополнительные библиотеки не требуются — API, связанные с фигурами, входят в основной пакет Aspose.Words.

## Вставка прямоугольной фигуры с Aspose.Words

Суть решения — короткая, автономная программа, которая создаёт пустой документ, вставляет прямоугольник, задаёт ему цвет, скрывает его и сохраняет файл. Ниже представлен полный исходный код с встроенными комментариями, объясняющими *почему* каждая строка нужна.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### Что делает каждый шаг

| Шаг | Причина |
|------|--------|
| **Create a new document** | Обеспечивает чистый холст; вы также можете загрузить существующий .docx, передав путь к файлу в `new Document(path)`. |
| **Initialize DocumentBuilder** | `DocumentBuilder` — высокоуровневый помощник, позволяющий вставлять текст, таблицы и фигуры без работы с низкоуровневыми деревьями узлов. |
| **Insert rectangle shape** | Метод `InsertShape` возвращает объект `Shape`, который можно дополнительно настроить (размер, позицию, границы и т.д.). |
| **Set fill color** | Свойство `FillColor` задаёт внутренний цвет; можно использовать любое значение `Color` (`Color.Red`, `Color.FromArgb(255, 0, 255, 0)` и т.п.). |
| **Hide the shape** | `Hidden = true` сообщает Word игнорировать фигуру при построении макета, оставляя её в XML‑документа. Это стандартный способ хранения невидимых объектов. |
| **Save the document** | Сохраняет изменения в файл .docx. Сохранённый файл будет содержать скрытую прямоугольную фигуру. |

## Как задать цвет заливки для фигуры

Изменить цвет заливки так же просто, как присвоить `System.Drawing.Color` свойству `FillColor`. Если нужен пользовательский оттенок, используйте `Color.FromArgb`:

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*Почему это важно*: Цвет заливки хранится в XML фигуры (`<w:fill>` атрибут). Когда фигура скрыта, цвет всё равно сохраняется, что может быть полезно для последующей обработки (например, извлечения метаданных по кодам цветов).

## Как скрыть фигуру в окончательном документе

Флаг `Hidden` — булево свойство класса `Shape`. Установка его в `true` гарантирует, что фигура будет игнорироваться движком макета Word.

```csharp
rectangleShape.Hidden = true;
```

**Распространённые подводные камни**

* **Hidden vs. Visible** — Если позже понадобится отобразить фигуру, просто установите `Hidden = false`.
* **Compatibility** — Более старые версии Word (до 2007) могут по‑другому обрабатывать скрытые графические объекты. Aspose.Words сохраняет совместимость, записывая флаг в соответствующий элемент OOXML.

## Как программно вставить фигуру

Хотя в примере используется прямоугольник, тот же метод `InsertShape` работает и для многих других фигур (эллипс, треугольник, линия и т.д.). Первый аргумент — значение перечисления `ShapeType`:

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**Подсказка**: Если нужно разместить фигуру в определённом месте страницы, используйте `builder.MoveTo` для установки точки вставки перед вызовом `InsertShape`.

## Добавление прямоугольной фигуры в существующий документ

Часто требуется доработать шаблон, а не создавать документ с нуля. Замените шаг 1 на:

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

Все последующие шаги остаются без изменений, и прямоугольник будет добавлен туда, где находится курсор `builder` (обычно в конце документа по умолчанию).

## Обработка крайних случаев и вариантов

### 1. Повторное отображение фигуры

Если на более позднем этапе вашего процесса нужно раскрыть скрытый прямоугольник, переключите флаг:

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. Добавление границы (обводки)

Скрытая фигура может иметь видимую границу, когда вы решите её показать. Установите свойства `LineColor` и `LineWidth`:

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. Абсолютное позиционирование прямоугольника

Для точного контроля макета переключите `WrapType` фигуры на `WrapType.Inline` (по умолчанию) или `WrapType.TopBottom` и настройте свойства `Left`/`Top`:

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. Использование другой единицы измерения

Aspose.Words работает в пунктах (1 pt = 1/72 дюйма). Если предпочитаете сантиметры, сначала выполните преобразование:

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## Полный исполняемый пример

Ниже представлен *полный* код программы, который можно скопировать, вставить и запустить. Он содержит все необходимые директивы `using` и использует абсолютные пути, которые следует скорректировать под вашу среду.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Ожидаемый результат**: Файл `HiddenRectangleShape.docx` открывается в Microsoft Word без видимой фигуры, но скрытый прямоугольник присутствует в XML документа. Его наличие можно проверить, открыв .docx как zip‑архив и изучив `word/document.xml` на наличие элемента `<w:shape>` с атрибутами `w:fill="yellow"` и `w:hidden="true"`.

## Заключение

Теперь вы знаете, как **вставлять прямоугольную фигуру** в документ Word с помощью C# и Aspose.Words, как **задать цвет заливки** и как **скрыть фигуру**, чтобы она оставалась невидимой в окончательном макете. Та же схема работает для других типов фигур, пользовательских цветов и существующих шаблонов. Экспериментируйте с границами, абсолютным позиционированием и различными единицами измерения, чтобы адаптировать фигуру под точные требования.

### Следующие шаги

* Изучите **как вставлять фигуру** внутри таблиц или в колонтитулы/нижние колонтитулы для создания водяных знаков.
* Скомбинируйте **добавление прямоугольной фигуры** с элементами управления содержимым для создания динамических заполнителей.
* Ознакомьтесь с API **манипуляции фигурами** Aspose.Words для продвинутых возможностей, таких как вращение, градиентные заливки и импорт SVG.

Не стесняйтесь адаптировать код под свой проект и сообщите в комментариях, какой следующий вызов, связанный с фигурами, вы решили!

## Что следует изучить дальше?

Следующие учебные материалы охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс включает полностью рабочие примеры кода с пошаговыми объяснениями, помогающими освоить дополнительные возможности API и исследовать альтернативные подходы в ваших проектах.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}