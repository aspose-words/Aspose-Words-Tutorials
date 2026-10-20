---
category: general
date: 2026-09-21
description: Создайте пустой документ Word с помощью Aspose.Words, задайте размер
  фигуры, её позицию, цвет и сохраните файл docx в одном пошаговом процессе.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: ru
lastmod: 2026-09-21
og_description: Создайте пустой документ Word, задайте размер фигуры, позицию фигуры,
  цвет фигуры и сохраните файл docx с помощью Aspose.Words за считанные минуты.
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: Создайте пустой документ Word и добавьте цветные фигуры – руководство Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Создайте пустой документ Word и добавьте цветные фигуры с помощью Aspose.Words
url: /ru/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создать пустой документ Word и добавить цветные фигуры с помощью Aspose.Words

Если вам нужно **создать пустой документ Word** программно, это руководство покажет, как сделать это с помощью Aspose.Words. Вы узнаете, как **установить размер фигуры**, **установить позицию фигуры**, **установить цвет фигуры**, и наконец **сохранить файл docx** не выходя из вашей IDE.

Работа с файлами Word в C# часто подразумевает использование низкоуровневых вызовов OpenXML, но Aspose.Words абстрагирует эту сложность. К концу этого руководства у вас будет полностью рабочий `.docx`, содержащий сгруппированную фигуру из двух цветных прямоугольников — идеально подходит для отчетов, сертификатов или пользовательских шаблонов.

## Требования

- .NET 6.0 или новее (код также работает с .NET Framework 4.7+)
- Aspose.Words for .NET 23.9 или новее (установить через NuGet: `Install-Package Aspose.Words`)
- Базовое знакомство с C# и Visual Studio (или любой C# редактор)

Существующий файл Word не требуется; руководство начинается с **создания пустого документа Word** с нуля.

## Создание пустого документа Word с помощью Aspose.Words

Первый шаг — создать объект `Document`. Этот объект представляет пустой файл Word в памяти.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` изначально пуст, что именно то, что вам нужно при **создании пустого документа Word**. `builder` позже будет использован для вставки группы фигур в текущую позицию курсора.

## Установка размера фигуры и создание GroupShape

`GroupShape` работает как контейнер, способный содержать несколько отдельных фигур. Сначала определите общие размеры контейнера.

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

Здесь мы **устанавливаем размер фигуры** для самой группы (300 × 200). Те же имена свойств (`Width`, `Height`) используются для каждой дочерней фигуры, предоставляя точный контроль над каждым элементом.

## Добавление первого прямоугольника и установка цвета фигуры

Теперь добавьте прямоугольник в группу и задайте ему цвет фона.

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

Свойство `FillColor` **устанавливает цвет фигуры**. Использование `System.Drawing.Color` позволяет выбрать любое предопределённое или пользовательское ARGB значение.

## Добавление второго прямоугольника, установка его размера, позиции и цвета

Второй прямоугольник демонстрирует, как **установить позицию фигуры** относительно группы и как изменить её цвет.

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

Поскольку ширина группы составляет 300 пунктов, два прямоугольника по 120 пунктов удобно помещаются с зазором в 30 пунктов. При необходимости измените `Left` и `Top` для иной раскладки.

## Вставка GroupShape в документ

После полной настройки группы разместите её в текущей позиции курсора.

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode` записывает фигуру непосредственно в тело документа, сохраняя точно **установленную позицию фигуры**, которую вы задали ранее.

## Сохранение файла docx

Последний шаг — сохранить документ на диск. Это демонстрирует операцию **save docx file**.

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

После запуска программы откройте `GroupShape.docx` в Microsoft Word. Вы должны увидеть пустую страницу с группой фигур, содержащей два цветных прямоугольника, расположенных рядом.

### Ожидаемый результат

- Одностраничный файл `.docx`.
- На странице находится группа фигур, расположенная на расстоянии 100 пт от левого и верхнего полей.
- Внутри группы слева находится светло‑голубой прямоугольник, а справа — светло‑коралловый прямоугольник, каждый размером 120 × 80 пт.

## Полный, исполняемый пример

Ниже приведена полная программа, которую вы можете скопировать и вставить в консольное приложение. Дополнительные файлы не требуются.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Запуск этой программы создаёт точно такой же документ, как описано выше, удовлетворяя всем четырём целям: **create blank word document**, **set shape size**, **set shape position**, **set shape color**, и **save docx file**.

## Общие варианты и граничные случаи

| Сценарий | Что изменить | Почему это важно |
|----------|----------------|----------------|
| **Разные типы фигур** | Заменить `ShapeType.Rectangle` на `ShapeType.Ellipse`, `ShapeType.Triangle` и т.д. | Позволяет создавать более сложную графику без внешних изображений. |
| **Динамические размеры** | Вычислять `Width` и `Height` из ввода пользователя или файлов конфигурации. | Делает решение переиспользуемым в нескольких шаблонах документов. |
| **Сохранение в PDF** | Вызвать `document.Save("output.pdf", SaveFormat.Pdf);` | Если получателям нужен неизменяемый формат, PDF — безопасный выбор. |
| **Добавление текста внутрь фигуры** | Создать фигуру `TextBox` и задать `TextBox.Text`. | Полезно для создания помеченных бейджей или выноски. |
| **Несколько групп на одной странице** | Повторить шаги 2‑5 с другими значениями `Left`/`Top`. | Позволяет создавать панели инструментов или многосекционные макеты. |

### Совет профессионала

Когда необходимо точно выровнять фигуры, используйте свойство `ShapeBase.WrapType = WrapType.Inline` перед вставкой группы. Это заставляет группу вести себя как абзац, предотвращая неожиданное обтекание текста вокруг неё.

## Заключение

Теперь вы знаете, как **create a blank Word document** с помощью Aspose.Words, **set shape size**, **set shape position**, **set shape color**, и **save the docx file**. Полный пример демонстрирует чистый, переиспользуемый шаблон для добавления сгруппированной графики в любой проект автоматизации Word.

Отсюда вы можете изучить:

- Добавление большего количества фигур или изображений в тот же `GroupShape` (вариации **set shape size**, **set shape color**).
- Использование `ShapeBase.Rotation` для вращения прямоугольников с декоративным эффектом.
- Экспорт того же документа в PDF или HTML для расширения распространения (альтернатива **save docx file**).

Не стесняйтесь экспериментировать с различными цветами, размерами и логикой расположения, чтобы соответствовать вашим конкретным потребностям в отчетности или шаблонах. Приятного кодинга!

## Что вам стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, которые развивают техники, продемонстрированные в этом руководстве. Каждый ресурс включает полные работающие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы к реализации в ваших проектах.

- [Создать групповую фигуру в документе Word с помощью Aspose.Words для .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Создать прямоугольную фигуру в Word с помощью C# – пошаговое руководство](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Учебник по теням фигур Aspose.Words – добавить тень к фигуре Word в C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}