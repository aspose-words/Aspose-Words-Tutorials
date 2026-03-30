---
category: general
date: 2026-03-30
description: Узнайте, как задать тень для фигуры Word с помощью C#. В этом руководстве
  также показано, как добавить тень к фигуре, настроить её прозрачность и добавить
  тень к прямоугольнику.
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: ru
og_description: Как задать тень для фигуры Word в C#? Следуйте этому пошаговому руководству,
  чтобы добавить тень к фигуре, настроить её прозрачность и добавить тень к прямоугольнику.
og_title: Как установить тень для формы Word – учебник C#
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Как установить тень у фигуры Word – учебник C#
url: /ru/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как установить тень на форму Word – C# Учебник

Задумывались ли вы когда‑нибудь **как установить тень** на форму внутри документа Word, не возясь с пользовательским интерфейсом? Вы не одиноки. Во многих отчётах или маркетинговых презентациях лёгкая тень‑падения делает прямоугольник более выразительным, а программное её добавление экономит часы.

В этом руководстве мы пройдем полный, готовый к запуску пример, который не только демонстрирует **как установить тень**, но также охватывает **add shape shadow**, **adjust shape transparency** и даже **add rectangle shadow** для классических подсказочных блоков. К концу вы получите файл Word (`output.docx`), выглядящий отшлифованным, и поймёте, почему важен каждый параметр.

## Требования

- .NET 6+ (или .NET Framework 4.7.2) с компилятором C#.  
- NuGet‑пакет Aspose.Words для .NET (`Install-Package Aspose.Words`)  
- Базовое знакомство с C# и объектной моделью Word  

Дополнительные библиотеки не требуются — всё находится внутри Aspose.Words.

## Как установить тень на форму Word в C#

Ниже приведён полный исходный файл. Сохраните его как `Program.cs` и запустите из вашей IDE или командой `dotnet run`. Код загружает существующий `.docx`, находит первую форму (по умолчанию прямоугольник), включает её тень, корректирует несколько визуальных параметров и сохраняет результат.

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **Что вы увидите** – Прямоугольник теперь имеет чёрную тень‑падения с 30 % прозрачностью, смещённую на 5 pt вправо и вниз, с лёгким размитием. Откройте `output.docx` в Word, чтобы проверить.

## Регулировка прозрачности формы — почему это важно

Прозрачность — это не просто эстетический параметр; она влияет на читаемость. Значение 0.0 делает тень полностью непрозрачной, а 1.0 полностью скрывает её. В приведённом выше фрагменте мы использовали `0.3`, чтобы достичь лёгкого эффекта, подходящего как для светлых, так и для тёмных фонов. Не стесняйтесь экспериментировать:

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

Помните, что **adjust shape transparency** можно также применить к цвету заливки формы, если вам нужен полупрозрачный сам прямоугольник.

## Добавление тени к различным объектам

Код, который мы использовали, работает с объектом `Shape`, но те же свойства `ShadowFormat` существуют у объектов **Image**, **Chart** и даже **TextBox**. Вот быстрый шаблон, который вы можете скопировать и вставить:

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

Таким образом, независимо от того, **add shape shadow** логотипу или декоративной иконке, подход остаётся одинаковым.

## Как добавить тень к любой форме — особые случаи

1. **Форма без ограничивающего прямоугольника** — Некоторые формы Word (например, свободные штрихи) не поддерживают тени. Попытка установить `ShadowFormat.Visible` завершится без ошибки. При необходимости проверьте `shape.IsShadowSupported`.  
2. **Старые версии Word** — Свойства тени соответствуют функциям Word 2007 и новее. Если необходимо поддерживать Word 2003, тень будет игнорироваться при открытии файла.  
3. **Несколько теней** — В текущей версии Aspose.Words поддерживается только одна тень на форму. Если нужен двойной эффект, продублируйте форму, сместите её и задайте разные параметры тени.

## Добавление тени к прямоугольнику — практический пример

Представьте, что вы генерируете квартальный отчёт, и каждый заголовок раздела — это цветной прямоугольник. Добавление **add rectangle shadow** придаёт странице вид «карточки». Шаги идентичны базовому примеру; просто убедитесь, что выбранная форма действительно является прямоугольником (`shape.ShapeType == ShapeType.Rectangle`). Если нужно создать прямоугольник с нуля, смотрите фрагмент ниже:

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

Запуск полной программы с этим дополнением создаст новый прямоугольник, уже имеющий желаемый эффект **add rectangle shadow**.

![Word shape with shadow](placeholder-image.png){alt="как установить тень на форму в Word"}

*Рисунок: Прямоугольник после применения настроек тени.*

## Краткое резюме (шпаргалка в виде пунктов)

- **Load** документ с помощью `new Document(path)`.  
- **Locate** форму через `doc.GetChild(NodeType.Shape, index, true)`.  
- **Enable** тень: `shape.ShadowFormat.Visible = true;`.  
- **Set color** с любым `System.Drawing.Color`.  
- **Adjust transparency** (`0.0–1.0`) для управления непрозрачностью.  
- **OffsetX / OffsetY** перемещают тень по горизонтали/вертикали (points).  
- **BlurRadius** смягчает края — более высокие значения = более размытой тени.  
- **Save** файл и откройте его в Word, чтобы увидеть результат.

## Что попробовать дальше?

- **Dynamic colors** — Получать цвет тени из темы или ввода пользователя.  
- **Conditional shadows** — Применять тень только когда ширина формы превышает пороговое значение.  
- **Batch processing** — Пройтись по всем формам в документе и автоматически **add shape shadow**.

*Счастливого кодинга! Если этот урок был вам полезен, оставьте комментарий или поделитесь своими приёмами работы с тенью. Чем больше мы учимся друг у друга, тем красивее становятся наши документы Word.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}