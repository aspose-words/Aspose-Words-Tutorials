---
category: general
date: 2026-03-01
description: Быстро добавьте прямоугольник в PDF с помощью Aspose.Words. Узнайте,
  как вставить форму в PDF, добавить графику в PDF и программно создать PDF‑документ
  с пользовательской тенью.
draft: false
keywords:
- add rectangle to pdf
- insert shape pdf
- add graphics to pdf
- create pdf document programmatically
- create pdf with shape
language: ru
og_description: Добавьте прямоугольник в PDF с помощью Aspose.Words. Этот учебник
  показывает, как вставить форму в PDF, добавить графику в PDF и программно создать
  PDF‑документ на C#.
og_title: Добавить прямоугольник в PDF с помощью Aspose.Words – Полное руководство
tags:
- pdf
- aspnet
- csharp
- graphics
title: Добавить прямоугольник в PDF с помощью Aspose.Words – пошаговое руководство
url: /ru/python/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Добавление прямоугольника в PDF с помощью Aspose.Words – Полное руководство

Когда‑нибудь вам нужно было **add rectangle to PDF**, но вы не знали, какой вызов API подходит? Вы не одиноки — разработчики постоянно спрашивают: «Как **insert shape PDF** и при этом сохранить файл лёгким?» Хорошая новость в том, что Aspose.Words делает это проще простого. В этом руководстве мы пройдём весь процесс, от программного создания PDF‑документа до стилизации прямоугольника с тенью.

Мы также добавим несколько дополнительных полезностей: вы узнаете, как **add graphics to PDF**, увидите точные шаги для **insert shape PDF**, и завершите готовым к запуску примером, который **creates PDF with shape**. Никаких внешних ссылок, только автономное решение, которое вы можете скопировать и вставить сегодня.

## Предварительные требования

- .NET 6.0 или новее (Aspose.Words работает с .NET Standard 2.0+)
- Действительная лицензия Aspose.Words for .NET или временный оценочный ключ
- Visual Studio 2022 (или любая IDE по вашему выбору)
- Базовые знания C# — ничего сложного, просто возможность запустить консольное приложение

Вот и всё. Если у вас есть всё перечисленное, вы готовы начинать.

## Шаг 1: Программное создание PDF‑документа

Первое, что вы делаете, когда хотите **add rectangle to PDF**, — создаёте пустой документ. Представьте класс `Document` как чистый холст; всё, что вы добавляете позже, живёт внутри него.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – initialise a new empty document
        Document doc = new Document();

        // The rest of the steps follow...
```

Зачем начинать с пустого документа? Потому что это гарантирует полный контроль над каждым элементом — без скрытых заголовков или нижних колонтитулов, с которыми пришлось бы разбираться позже.

## Шаг 2: Инициализация DocumentBuilder для **insert shape PDF**

`DocumentBuilder` — это ваша кисть для рисования. Он умеет размещать текст, изображения и, что особенно важно для нас, фигуры. Без него вам пришлось бы самостоятельно манипулировать низкоуровневым деревом узлов — кошмар для большинства разработчиков.

```csharp
        // Step 2 – create a builder that will let us add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Обратите внимание, что мы ещё не добавляли страниц. Builder автоматически создаст страницу при первой вставке чего‑либо, что делает код аккуратным.

## Шаг 3: Вставка прямоугольника — ядро «add rectangle to PDF»

Теперь начинается интересная часть: вставка прямоугольника. Метод `InsertShape` поддерживает десятки значений `ShapeType`; мы выберем `ShapeType.Rectangle` и зададим размер 200 × 100 пунктов.

```csharp
        // Step 3 – insert a rectangle (200 × 100 points) into the document
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

На данном этапе PDF уже содержит простой прямоугольник. Если открыть файл сейчас, вы увидите простую коробку в левом верхнем углу первой страницы. Это основа для **add graphics to PDF**.

## Шаг 4: Стилизация прямоугольника — добавление пользовательской тени

Прямоугольник без стиля скучен. Дадим ему лёгкую падающую тень, чтобы он *выделялся* при рендеринге PDF. Объект `ShadowFormat` управляет всем — от радиуса размытия до непрозрачности.

```csharp
        // Step 4 – configure a custom shadow for the shape
        ShadowFormat shadow = rectangle.ShadowFormat;
        shadow.Visible = true;
        shadow.BlurRadius = 8.0;          // pixels
        shadow.Distance = 5.0;           // points from the shape
        shadow.Direction = 45.0;         // degrees clockwise
        shadow.Opacity = 0.6;            // 0‑1 range
        shadow.Color = Color.Black;
```

Зачем тень? Помимо эстетического эффекта, тень помогает различать перекрывающиеся графические элементы — то, что может понадобиться при **add graphics to PDF** в более сложных отчётах.

## Шаг 5: Сохранение файла — завершение процесса «create PDF with shape»

Последняя строка записывает всё на диск. Aspose.Words автоматически выбирает правильную версию PDF и встраивает необходимые ресурсы.

```csharp
        // Step 5 – save the document as a PDF file
        doc.Save(@"C:\Temp\ShapeWithShadow.pdf");
    }
}
```

Откройте `ShapeWithShadow.pdf`, и вы увидите красиво затенённый прямоугольник, гордо стоящий на странице. Это весь процесс **create pdf document programmatically**, упакованный в менее чем 30 строк кода.

## Полный рабочий пример — **create PDF with shape** от начала до конца

Ниже приведена полная программа, которую вы можете скопировать и вставить в новый проект Console App. Она включает все директивы `using`, метод `Main` и короткий заголовок‑комментарий для будущих справок.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectanglePdfDemo
{
    /// <summary>
    /// Demonstrates how to add a rectangle to PDF, configure a shadow,
    /// and save the result using Aspose.Words for .NET.
    /// </summary>
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty PDF document
            Document doc = new Document();

            // 2️⃣ Initialise a DocumentBuilder – the tool that lets us add content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a rectangle shape (200 × 100 points) – this is the core of "add rectangle to pdf"
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

            // 4️⃣ Apply a custom shadow – makes the graphic stand out
            ShadowFormat shadow = rect.ShadowFormat;
            shadow.Visible = true;
            shadow.BlurRadius = 8.0;   // pixels
            shadow.Distance = 5.0;    // points
            shadow.Direction = 45.0;  // degrees
            shadow.Opacity = 0.6;     // semi‑transparent
            shadow.Color = Color.Black;

            // 5️⃣ Save the document – the final step in creating a PDF with shape
            string outputPath = @"C:\Temp\ShapeWithShadow.pdf";
            doc.Save(outputPath);

            Console.WriteLine($"PDF saved successfully to {outputPath}");
        }
    }
}
```

**Ожидаемый результат:** одностраничный PDF, где прямоугольник 200 × 100 пунктов расположен рядом с левым верхним углом, украшён мягкой тенью под углом 45 градусов. Откройте файл в любом PDF‑просмотрщике, чтобы проверить.

## Часто задаваемые вопросы и особые случаи

### Работает ли это с другими типами фигур?

Конечно. Замените `ShapeType.Rectangle` на `ShapeType.Ellipse`, `ShapeType.Triangle` или любой из более чем 150 вариантов, поддерживаемых Aspose.Words. Те же свойства `ShadowFormat` применимы.

### Что если мне нужен прямоугольник на определённой странице?

После вставки фигуры вы можете переместить её на другую страницу, изменив свойство `CurrentPage` у builder перед вызовом `InsertShape`. Например:

```csharp
builder.MoveToPage(3);
Shape rectOnPage3 = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

### Можно ли изменить цвет заливки прямоугольника?

Конечно. Используйте свойство `FillColor`:

```csharp
rect.FillColor = Color.LightBlue;
```

### Как это влияет на размер файла?

Добавление простой фигуры и тени увеличивает размер всего на несколько килобайт. Если вы начинаете накладывать множество графических элементов, подумайте о сжатии изображений или использовании векторных фигур, чтобы PDF оставался небольшим.

### Требуется ли лицензия для продакшн?

Aspose.Words работает в режиме оценки, но полученный PDF будет содержать водяной знак. Приобретите лицензию для неограниченного использования и удаления водяного знака.

## Советы и приёмы (уровень Pro)

- **Batch insertion:** Если вам нужно десятки прямоугольников, пройдитесь по коллекции координат в цикле и переиспользуйте один `DocumentBuilder` — производительность остаётся линейной.
- **Layering:** Установите `rect.WrapType = WrapType.Inline`, если хотите, чтобы прямоугольник текствал вместе с текстом, или `WrapType.Square`, чтобы текст обтекал его.
- **PDF/A compliance:** Вызовите `doc.CompatibilityOptions.OptimizeForPdfA = true;` перед сохранением, если нужен архивный PDF/A‑совместимый документ.

## Визуальное резюме

![add rectangle to pdf example](https://example.com/rectangle-shadow.png "add rectangle to pdf example")

Изображение демонстрирует окончательный макет PDF: чистый прямоугольник с лёгкой тенью, точно такой, как генерирует наш код.

## Заключение

Теперь вы знаете **how to add rectangle to PDF** с помощью Aspose.Words, как **insert shape PDF**, и как **add graphics to PDF** с пользовательским стилем — всё это при **creating PDF document programmatically** и завершив примером **create PDF with shape**, который вы сможете использовать уже завтра.  

Далее попробуйте заменить прямоугольник логотипом или объединить несколько фигур для создания простой диаграммы. Вы также можете поэкспериментировать с обтеканием текста, вращением или даже встраиванием гиперссылки в фигуру. API достаточно мощный, чтобы превратить статический PDF в интерактивный, насыщенный графикой отчёт, не покидая C#.

Не стесняйтесь экспериментировать, а если возникнут проблемы, оставьте комментарий ниже. Счастливого кодинга!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}