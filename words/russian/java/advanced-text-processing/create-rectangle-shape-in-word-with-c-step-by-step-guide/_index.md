---
category: general
date: 2026-03-04
description: Learn how to create rectangle shape, add shadow to shape and apply shadow
  effect in a Word document, then save Word document automatically.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- save word document
- create blank document
language: ru
og_description: Создайте прямоугольную форму, добавьте к ней тень и примените эффект
  тени в документе Word с помощью C#. Следуйте этому руководству, чтобы легко сохранять
  документ Word.
og_title: Создание прямоугольной формы в Word – Полный учебник по C#
tags:
- C#
- Aspose.Words
- Document Automation
title: Создание прямоугольной фигуры в Word с помощью C# – пошаговое руководство
url: /ru/java/advanced-text-processing/create-rectangle-shape-in-word-with-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание прямоугольной формы в Word с помощью C# – Полный учебный материал

Когда‑нибудь вам нужно было **create rectangle shape** в файле Word, но вы не знали, с чего начать? Вы не одиноки — многие разработчики сталкиваются с этим, когда впервые погружаются в программную генерацию документов. Хорошая новость в том, что с помощью нескольких строк C# вы можете вставить прямоугольник, **add shadow to shape**, и **apply shadow effect**, не открывая Word. В этом руководстве мы пройдем весь процесс, от свежего **create blank document** до сохранения окончательного **save word document** на диск.

Мы рассмотрим всё, что вам нужно: требуемый пакет NuGet, точные API, почему каждое свойство важно, и несколько советов, как избежать самых распространённых подводных камней. К концу у вас будет полностью исполняемый пример, который можно вставить в любой проект .NET.

## Требования

- .NET 6.0 или новее (код также работает с .NET Framework 4.7+)
- Visual Studio 2022 или любой предпочитаемый IDE
- **Aspose.Words for .NET** установлен через NuGet (`Install-Package Aspose.Words`)
- Базовое знакомство с синтаксисом C#

Дополнительные библиотеки Word interop не требуются — Aspose.Words обрабатывает всё в памяти.

## Шаг 1 — Создание пустого документа

Первое, что мы делаем, — **create blank document**. Считайте его пустым холстом, на котором позже мы **create rectangle shape**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a new blank document
Document doc = new Document();   // This gives us a fresh Word file
```

> **Почему это важно:** Начало с чистого объекта `Document` гарантирует, что скрытые стили или секции не будут влиять на позиционирование формы позже.

## Шаг 2 — Вставка прямоугольной формы в документ

Теперь мы действительно **create rectangle shape**. Мы зададим её размер, позицию и укажем Word не обтекать текст вокруг неё.

```csharp
// Step 2: Add a rectangle shape
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 200;          // Width in points (1 point = 1/72 inch)
rectangle.Height = 100;         // Height in points
rectangle.WrapType = WrapType.None; // No text wrapping
```

> **Совет профессионала:** если вам нужно, чтобы прямоугольник находился внутри ячейки таблицы, измените `WrapType` на `WrapType.Inline`. Для большинства отчётов `None` удерживает форму плавающей над текстом.

## Шаг 3 — Добавление тени к форме и настройка её внешнего вида

Здесь происходит волшебство: мы **add shadow to shape** и **apply shadow effect**. Тень делает прямоугольник более заметным на странице, особенно при печати.

```csharp
// Step 3: Enable shadow and set its properties
rectangle.ShadowFormat.Visible = true;          // Turn on the shadow
rectangle.ShadowFormat.BlurRadius = 5.0;        // Softness of the shadow edge
rectangle.ShadowFormat.Transparency = 0.3;      // 30 % transparent
rectangle.ShadowFormat.OffsetX = 8;             // Horizontal shift
rectangle.ShadowFormat.OffsetY = 8;             // Vertical shift
rectangle.ShadowFormat.Color = Color.Blue;     // Shadow colour
```

> **Почему эти значения?**  
> - **BlurRadius** контролирует, насколько размыты края; значение около `5` даёт мягкий, профессиональный вид.  
> - **Transparency** позволяет сохранять читаемость подлежащего текста.  
> - **OffsetX/Y** смещают тень от формы, создавая глубину.  
> - Использование оттенка **blue** — лишь пример; любой `System.Drawing.Color` подходит.

## Шаг 4 — Добавление настроенной формы в тело документа

После полной стилизации прямоугольника мы теперь **add rectangle shape** в первую секцию документа. Этот шаг фактически помещает форму в файл.

```csharp
// Step 4: Append the shape to the first section's body
doc.FirstSection.Body.AppendChild(rectangle);
```

> **Особый случай:** если ваш документ уже содержит секции, возможно, вы захотите обратиться к конкретной (`doc.Sections[2]`, например). Приведённый код работает для одно‑секционного документа, что обычно для быстрых отчётов.

## Шаг 5 — Сохранение документа Word

Наконец, мы **save word document** на диск. Файл будет содержать прямоугольник с тенью, готовый к открытию в Microsoft Word.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\shadowed_rectangle.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Подсказка:** используйте `doc.Save(outputPath, SaveFormat.Docx)`, если нужно явно указать формат. Метод `Save` автоматически определяет расширение, но явное указание может избежать путаницы, когда путь генерируется программно.

## Полный, исполняемый пример

Ниже представлен полный код программы, который можно скопировать и вставить в консольное приложение. Он включает все директивы `using` и метод `Main`, так что вы можете сразу запустить его.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document
            Document doc = new Document();

            // 2️⃣ Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 200;
            rectangle.Height = 100;
            rectangle.WrapType = WrapType.None;

            // 3️⃣ Apply shadow effect
            rectangle.ShadowFormat.Visible = true;
            rectangle.ShadowFormat.BlurRadius = 5.0;
            rectangle.ShadowFormat.Transparency = 0.3;
            rectangle.ShadowFormat.OffsetX = 8;
            rectangle.ShadowFormat.OffsetY = 8;
            rectangle.ShadowFormat.Color = Color.Blue;

            // 4️⃣ Insert the shape into the document body
            doc.FirstSection.Body.AppendChild(rectangle);

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\shadowed_rectangle.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document saved at {outputPath}");
        }
    }
}
```

### Ожидаемый результат

Когда вы откроете *shadowed_rectangle.docx* в Microsoft Word, вы увидите прямоугольник с синей границей, плавающий рядом с верхом первой страницы, с мягкой синей тенью, смещённой на 8 pt вправо и вниз. Дополнительный текст вокруг него отсутствует, потому что мы задали `WrapType.None`.

## Часто задаваемые вопросы и варианты

| Question | Answer |
|----------|--------|
| **Могу ли я изменить форму на эллипс?** | Да — замените `ShapeType.Rectangle` на `ShapeType.Ellipse`. Все свойства тени останутся прежними. |
| **Что если мне нужно несколько форм?** | Просто повторите Шаги 2‑4 для каждого нового экземпляра `Shape`, корректируя `OffsetX/Y` или `Left/Top`, чтобы избежать наложения. |
| **Можно ли сделать цвет тени совпадающим с заливкой формы?** | Конечно. Сначала задайте `rectangle.FillColor`, затем присвойте `rectangle.ShadowFormat.Color = rectangle.FillColor;`. |
| **Как вставить форму в ячейку таблицы?** | Используйте `cell.FirstParagraph.AppendChild(rectangle);` после нахождения нужного объекта `Cell`. |
| **Будет ли это работать на .NET Core?** | Да — Aspose.Words кросс‑платформенный. Просто убедитесь, что вы используете соответствующую версию пакета NuGet для .NET Core/5/6. |

## Распространённые подводные камни и профессиональные советы

- **Pitfall:** Забвение установки `ShadowFormat.Visible = true`. Свойства тени будут тихо игнорироваться.  
  **Fix:** Всегда включайте видимость перед изменением других параметров тени.

- **Pitfall:** Использование слишком большого `BlurRadius` (например, 20) может сделать тень размытой и непрофессиональной.  
  **Fix:** Придерживайтесь значений от `3` до `8` для большинства деловых документов.

- **Pro tip:** Если вам нужно, чтобы форма была доступна для выбора позже (например, для редактирования пользователем), избегайте установки `WrapType.Inline`. Плавающие формы (`WrapType.None`) проще перемещать программно.

- **Pro tip:** При генерации множества документов в цикле переиспользуйте один экземпляр `Document` и вызывайте `doc.Clone(true)` для каждой итерации, чтобы повысить производительность.

## Связанные темы, которые могут вас заинтересовать

- **Add text inside a rectangle shape** — узнайте, как использовать `Shape.TextPath` для меток.  
- **Create complex diagrams** — комбинируйте несколько форм, соединители и группировку.  
- **Export to PDF** — преобразуйте тот же документ в PDF одной командой `doc.Save("output.pdf")`.  
- **Apply different fill styles** — градиенты, текстуры или даже изображения внутри форм.

## Заключение

Мы только что **create rectangle shape**, **add shadow to shape**, и **apply shadow effect** в файле Word с помощью C#. Следуя пяти лаконичным шагам, вы получили переиспользуемый шаблон для любой задачи автоматизации документов и знаете, как надёжно **save word document**. Не стесняйтесь менять размеры, цвета или даже заменять прямоугольник другой геометрией — Aspose.Words делает всё это простым.

Если этот учебник оказался полезным, поставьте звёздочку на GitHub или поделитесь своими вариантами в комментариях. Приятного кодинга, и пусть ваши документы всегда выглядят так же безупречно, как этот прямоугольник с тенью!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}