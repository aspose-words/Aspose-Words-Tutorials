---
category: general
date: 2025-12-08
description: Быстро добавьте тень к фигуре с помощью Aspose.Words. Узнайте, как создать
  документ Word, используя Aspose, как добавить тень к фигуре и применить прозрачность
  тени в C#.
draft: false
keywords:
- add shadow to shape
- create word document using aspose
- how to add shape shadow
- apply shadow transparency
language: ru
og_description: Добавьте тень к фигуре в файле Word с помощью Aspose.Words. Это пошаговое
  руководство показывает, как создать документ, добавить фигуру и применить прозрачность
  тени.
og_title: Добавить тень к фигуре – учебник Aspose.Words C#
tags:
- Aspose.Words
- C#
- Word Automation
title: Добавить тень к фигуре в документе Word – Полное руководство Aspose.Words
url: /russian/net/images-and-shapes/add-shadow-to-shape-in-a-word-document-complete-aspose-words/
---

{{< layout-start >}}

{{< layout-start >}}

# Добавление тени к фигуре – Полное руководство по Aspose.Words

Когда‑то вам нужно **добавить тень к фигуре** в файле Word, но вы не знали, какие вызовы API использовать? Вы не одиноки. Многие разработчики сталкиваются с проблемой, пытаясь добавить правильную падающую тень к прямоугольнику или любому элементу рисунка, особенно при работе с Aspose.Words для .NET.

В этом руководстве мы пройдём всё, что вам нужно знать: от **создания документа Word с помощью Aspose** до настройки тени, изменения её размытия, расстояния, угла и даже **применения прозрачности тени**. К концу вы получите готовую к запуску программу на C#, которая создаёт файл `.docx` с аккуратно затенённым прямоугольником — без ручных правок в Word.

---

## Что вы узнаете

- Как настроить проект Aspose.Words в Visual Studio.  
- Точные шаги для **создания документа Word с помощью Aspose** и вставки фигуры.  
- **Как добавить тень к фигуре** с полным контролем над размитием, расстоянием, углом и прозрачностью.  
- Советы по устранению распространённых проблем (например, отсутствие лицензии, неверные единицы измерения).  
- Полный пример кода, готовый к копированию и запуску сегодня.

> **Требования:** .NET 6+ (или .NET Framework 4.7.2+), действующая лицензия Aspose.Words (или бесплатная пробная версия) и базовые знания C#.

---

## Шаг 1 – Настройте проект и добавьте Aspose.Words

Сначала откройте Visual Studio, создайте новое **Console App (.NET Core)** и добавьте пакет Aspose.Words через NuGet:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Если у вас есть файл лицензии (`Aspose.Words.lic`), скопируйте его в корень проекта и загрузите при старте. Это избавит от водяного знака, появляющегося в режиме бесплатной оценки.

```csharp
// Load the license (optional but recommended)
var license = new Aspose.Words.License();
license.SetLicense("Aspose.Words.lic");
```

---

## Шаг 2 – Создайте новый пустой документ

Теперь мы действительно **создаём документ Word с помощью Aspose**. Этот объект будет служить холстом для нашей фигуры.

```csharp
// Step 2: Initialize a new blank document
Document doc = new Document();   // Represents an empty .docx file
```

Класс `Document` — точка входа для всего остального: абзацев, секций и, конечно же, графических объектов.

---

## Шаг 3 – Вставьте прямоугольную фигуру

Когда документ готов, мы можем добавить фигуру. Здесь мы выбираем простой прямоугольник, но та же логика работает для кругов, линий или пользовательских полигонов.

```csharp
// Step 3: Create a rectangular shape that will hold the shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 150,   // Width in points (1 point = 1/72 inch)
    Height = 100    // Height in points
};
```

> **Почему фигура?** В Aspose.Words объект `Shape` может содержать текст, изображения или просто выступать в качестве декоративного элемента. Добавление тени к фигуре гораздо проще, чем попытка изменить рамку изображения.

---

## Шаг 4 – Настройте тень (Add Shadow to Shape)

Это сердце руководства — **как добавить тень к фигуре** и точно настроить её внешний вид. Свойство `ShadowFormat` даёт вам полный контроль.

```csharp
// Step 4: Enable the shadow and configure its appearance
rectangle.ShadowFormat.Visible       = true;   // Turn the shadow on
rectangle.ShadowFormat.Blur          = 5.0;    // Blur radius – higher = softer edges
rectangle.ShadowFormat.Distance      = 3.0;    // Offset distance from the shape
rectangle.ShadowFormat.Angle         = 45;     // Direction in degrees (0 = right, 90 = down)
rectangle.ShadowFormat.Transparency  = 0.3;    // 30 % transparent – this is how we **apply shadow transparency**
```

### Что делает каждое свойство

| Свойство | Эффект | Типичные значения |
|----------|--------|-------------------|
| **Visible** | Включает/выключает тень. | `true` / `false` |
| **Blur** | Смягчает края тени. | `0` (жёсткая) до `10` (очень мягкая) |
| **Distance** | Отодвигает тень от фигуры. | обычно `1`–`5` пунктов |
| **Angle** | Управляет направлением смещения. | `0`–`360` градусов |
| **Transparency** | Делает тень полупрозрачной. | `0` (непрозрачная) до `1` (невидимая) |

> **Edge case:** Если установить `Transparency` в `1`, тень полностью исчезнет — удобно для программного переключения.

---

## Шаг 5 – Добавьте фигуру в документ

Теперь мы присоединяем фигуру к первому абзацу тела документа. Aspose автоматически создаёт абзац, если его нет.

```csharp
// Step 5: Append the shape to the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);
```

Если ваш документ уже содержит контент, вы можете вставить фигуру в любой узел с помощью `InsertAfter` или `InsertBefore`.

---

## Шаг 6 – Сохраните документ

Наконец, запишите файл на диск. Вы можете выбрать любой поддерживаемый формат (`.docx`, `.pdf`, `.odt` и т.д.), но в этом руководстве мы останемся с нативным форматом Word.

```csharp
// Step 6: Save the document with the shadowed shape
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Откройте полученный `ShadowedShape.docx` в Microsoft Word, и вы увидите прямоугольник с мягкой тенью под углом 45° и прозрачностью 30 % — именно так, как мы настроили.

---

## Полный рабочий пример

Ниже представлен **полный готовый к копированию** код, включающий все шаги выше. Сохраните его как `Program.cs` и запустите командой `dotnet run`.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // OPTIONAL: Load Aspose.Words license (remove if using trial)
        // -------------------------------------------------
        try
        {
            var license = new License();
            license.SetLicense("Aspose.Words.lic");
        }
        catch (Exception ex)
        {
            Console.WriteLine("License not found – running in evaluation mode: " + ex.Message);
        }

        // -------------------------------------------------
        // 1. Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // 2. Insert a rectangle shape
        // -------------------------------------------------
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 150,
            Height = 100
        };

        // -------------------------------------------------
        // 3. Configure the shadow – this is where we **add shadow to shape**
        // -------------------------------------------------
        rectangle.ShadowFormat.Visible      = true;   // Show the shadow
        rectangle.ShadowFormat.Blur         = 5.0;    // Soft edges
        rectangle.ShadowFormat.Distance     = 3.0;    // Offset distance
        rectangle.ShadowFormat.Angle        = 45;     // Direction in degrees
        rectangle.ShadowFormat.Transparency = 0.3;    // 30 % transparent (apply shadow transparency)

        // -------------------------------------------------
        // 4. Add the shape to the document
        // -------------------------------------------------
        doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);

        // -------------------------------------------------
        // 5. Save the file
        // -------------------------------------------------
        string outFile = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
        doc.Save(outFile);
        Console.WriteLine($"Document created successfully: {outFile}");
    }
}
```

**Ожидаемый результат:** Файл `ShadowedShape.docx`, содержащий один прямоугольник с лёгкой, полупрозрачной падающей тенью под углом 45°.

---

## Вариации и продвинутые советы

### Изменение цвета тени

По умолчанию тень наследует цвет заливки фигуры, но вы можете задать собственный цвет:

```csharp
rectangle.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### Несколько фигур с разными тенями

Если требуется несколько фигур, просто повторите шаги создания и настройки. Не забудьте дать каждой фигуре уникальное имя, если планируете обращаться к ним позже.

### Экспорт в PDF с сохранёнными тенями

Aspose.Words сохраняет эффекты тени при сохранении в PDF:

```csharp
doc.Save("ShadowedShape.pdf");
```

### Распространённые ошибки

| Симптом | Вероятная причина | Решение |
|---------|-------------------|---------|
| Тень не видна | `ShadowFormat.Visible` оставлен `false` | Установите `true`. |
| Тень выглядит слишком жёстко | `Blur` установлен в `0` | Увеличьте `Blur` до 3–6. |
| Тень исчезает в PDF | Используется старая версия Aspose.Words (< 22.9) | Обновите библиотеку до последней версии. |

---

## Заключение

Мы рассмотрели **как добавить тень к фигуре** с помощью Aspose.Words, от инициализации документа до тонкой настройки размытия, расстояния, угла и **применения прозрачности тени**. Полный пример демонстрирует чистый, готовый к продакшену подход, который можно адаптировать под любую фигуру или макет документа.

Есть вопросы о **создании документа Word с помощью Aspose** для более сложных сценариев — например, таблиц с тенями или динамически генерируемых фигур? Оставляйте комментарий ниже или смотрите связанные руководства по работе с изображениями и форматированием абзацев в Aspose.Words.

Счастливого кодинга и приятного добавления визуального блеска вашим документам Word! 

--- 

![add shadow to shape example](shadowed_shape.png "add shadow to shape example")

{{< layout-end >}}

{{< layout-end >}}