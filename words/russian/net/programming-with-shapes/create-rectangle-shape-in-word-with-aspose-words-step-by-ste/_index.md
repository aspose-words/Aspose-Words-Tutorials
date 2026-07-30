---
category: general
date: 2025-12-29
description: Создайте прямоугольную форму в документе Word с помощью Aspose.Words
  C#. Узнайте, как установить прозрачность формы, задать цвет тени и легко сохранить
  документ Word.
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: ru
og_description: Создайте прямоугольную форму в документе Word с помощью Aspose.Words
  C#. Это руководство показывает, как установить прозрачность формы, задать цвет тени
  и сохранить документ Word.
og_title: Создание прямоугольной формы в Word – Полное руководство по Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Создание прямоугольной фигуры в Word с помощью Aspose.Words – пошаговое руководство
url: /ru/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание прямоугольной фигуры в Word – Полный учебник Aspose.Words

Когда‑нибудь вам нужно было **создать прямоугольную фигуру** в документе Word, но вы не знали, с чего начать? Вы не одиноки; многие разработчики сталкиваются с этим при автоматизации отчетов или счетов. В этом руководстве мы пройдем все шаги по созданию прямоугольной фигуры, установке прозрачности фигуры, установке цвета тени и, наконец, **сохранить документ Word** с помощью Aspose.Words для .NET.  

Мы охватим всё от начального объекта документа до конечного файла `.docx` на диске, так что к концу вы сможете **создавать документы Word** программно без догадок. Без внешних ссылок, только автономное решение, которое вы можете скопировать и вставить в свой проект.

## Требования

- .NET 6.0 или новее (код также работает с .NET Framework 4.7+)
- Пакет NuGet Aspose.Words для .NET (`Install-Package Aspose.Words`)
- Базовое знакомство с синтаксисом C#
- Любая IDE по вашему выбору (Visual Studio, Rider, VS Code и т.д.)

> **Совет:** Если вы используете бесплатную пробную версию Aspose.Words, библиотека добавит водяной знак в выходной файл. Для продакшна вам понадобится действующая лицензия.

## Шаг 1: Инициализация документа и Builder

Первое, что мы делаем, — создаём новый пустой документ Word и `DocumentBuilder`, который позволяет вставлять содержимое. Думайте о Builder как о виртуальной ручке, рисующей на странице.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Почему это важно:** Без `DocumentBuilder` вам пришлось бы напрямую манипулировать низкоуровневым деревом узлов, что склонно к ошибкам и труднее читается.

## Шаг 2: Создание прямоугольной фигуры

Теперь мы действительно **создаёмоугольную фигуру**. Метод `InsertShape` принимает перечисление `ShapeType`, ширину и высоту (в пунктах). Возвращаемый объект `Shape` позволяет позже настраивать визуальные свойства.

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

На данном этапе прямоугольник представляет собой сплошную чёрную коробку, привязанную к текущему абзацу. При необходимости вы можете переместить её, изменить размер или даже повернуть позже.

![создание прямоугольной фигуры с тенью](/images/rectangle-shadow.png "Документ Word, показывающий прямоугольную фигуру со светлой тенью")

*Текст alt изображения: создание прямоугольной фигуры с тенью в документе Word*

## Шаг 3: Установка прозрачности фигуры

Прозрачность — это уровень “прозрачности” заливки фигуры. Aspose.Words использует свойство `Transparency` в диапазоне от `0.0` (непрозрачный) до `1.0` (полностью прозрачный). Здесь мы **устанавливаем прозрачность фигуры** на 40 %, чтобы подлежащий текст оставался читаемым.

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **Особый случай:** Если вам нужна полностью невидимая фигура, но тень должна оставаться, установите `Transparency` в `1.0` и задайте фигуре ненулевую ширину контура.

## Шаг 4: Настройка тени

Тонкая падающая тень добавляет глубину. Мы **установим цвет тени** в средний серый, отрегулируем её радиус размытия и сместим её на несколько пунктов по горизонтали и вертикали.

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **Почему это важно:** Тень, слишком резкая или слишком тёмная, может выглядеть как артефакт печати. Регулируйте `Blur` и `Transparency`, пока не будет выглядеть естественно.

## Шаг 5: Сохранение документа Word

Наконец мы **сохраняем документ Word** на диск. Метод `Save` автоматически определяет формат файла по расширению; `.docx` — современный формат OpenXML.

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

Если папка не существует, Aspose.Words выбросит `ArgumentException`. Убедитесь, что путь действителен, или создайте каталог заранее.

## Полный рабочий пример

Ниже приведена полная, готовая к запуску программа, объединяющая все шаги. Скопируйте её в новый консольный проект и нажмите **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Ожидаемый результат

Откройте `ShadowRectangle.docx` в Microsoft Word. Вы должны увидеть светло‑серый прямоугольник с мягкой, слегка смещённой тенью, оба отрисованы с 40 % прозрачностью. Фигура находится на пустой странице, готовая к добавлению контента.

## Часто задаваемые вопросы и варианты

**Что если мне нужна другая фигура?**  
Замените `ShapeType.Rectangle` на любое другое значение перечисления (`Ellipse`, `Triangle`, `Star` и т.д.). Остальная часть кода остаётся той же.

**Могу ли я изменить цвет контура?**  
Да — используйте `rectangleShape.StrokeColor = System.Drawing.Color.Blue;` и при желании задайте `rectangleShape.StrokeWeight = 1.5;`.

**Как разместить фигуру в определённом месте страницы?**  
Установите `rectangleShape.WrapType = WrapType.None;`, а затем отрегулируйте свойства `rectangleShape.Left` и `rectangleShape.Top` (значения в пунктах).

**Можно ли добавить текст внутри прямоугольника?**  
Конечно. После создания фигуры вы можете вызвать `rectangleShape.AppendChild(new Paragraph(document))` и затем добавить `Run` с вашим текстом. Не забудьте установить свойства `rectangleShape.TextBox`, если требуется более сложное форматирование.

## Профессиональные советы и подводные камни

- **Получите лицензию заранее:** Если забыть применить лицензию, Aspose.Words вставит водяной знак на первую страницу, что может сбивать с толку во время тестирования.
- **Совет по производительности:** При генерации множества документов в цикле переиспользуйте один экземпляр `Document` и вызывайте `document.RemoveAllChildren();` после каждого сохранения, чтобы избежать избыточного давления на сборщик мусора.
- **Видимость тени:** На экранах с низким разрешением тонкая тень может быть невидима. Увеличьте `Blur` или `OffsetX/Y` для отладки, затем уменьшите для продакшна.

## Следующие шаги

Теперь, когда вы знаете, как **создавать прямоугольную фигуру**, **устанавливать прозрачность фигуры**, **устанавливать цвет тени** и **сохранять документ Word**, рассмотрите возможность расширения учебника:

- Добавьте несколько фигур и сгруппируйте их.
- Вставьте прямоугольник в ячейку таблицы для макета отчёта.
- Скомбинируйте фигуру с `DocumentBuilder.InsertHtml` для наложения HTML‑стилизованного контента.
- Исследуйте другие визуальные эффекты, такие как `Glow` или `Reflection`, для более богатых UI‑подобных документов.

Экспериментируйте, ломайте вещи, а затем дорабатывайте — программная генерация документов — это площадка, где визуальный дизайн встречается с кодом.

---

*Счастливого кодинга! Если вы столкнулись с проблемами, оставьте комментарий ниже, и мы разберём их вместе.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}