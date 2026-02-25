---
category: general
date: 2026-02-24
description: Создайте прямоугольную форму в C# с помощью Aspose.Words, добавьте к
  ней тень и сохраните документ в PDF. Узнайте, как добавить тень и как сохранить
  PDF за несколько минут.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: ru
og_description: Создайте прямоугольную форму в C# с помощью Aspose.Words, затем добавьте
  к ней тень и сохраните документ в PDF — полное пошаговое руководство.
og_title: Создайте прямоугольную форму, добавьте тень и сохраните PDF
tags:
- Aspose.Words
- C#
- PDF generation
title: Создать прямоугольную форму, добавить тень и сохранить PDF
url: /ru/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

-backtop-button >}}

We keep them unchanged.

Now ensure we didn't miss any markdown links. There are none besides image.

Check for any code block placeholders: CODE_BLOCK_0-5. Keep them.

Now produce final output with all translations and original shortcodes.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создать прямоугольную форму, добавить тень и сохранить PDF

Когда‑нибудь вам нужно было **create rectangle shape** в документе Word, но также хотелось добавить приятную падающую тень и получить PDF‑вывод? Вы не одиноки. Во многих проектах по созданию отчетов или счетов визуальная отделка — например, тонкая тень — делает разницу между «просто еще одним файлом» и «документом профессионального уровня».  

В этом руководстве мы подробно рассмотрим именно это: используя **Aspose.Words for .NET** для создания прямоугольной формы, добавления тени к форме и, наконец, **save document as PDF**. К концу вы получите готовое к запуску консольное приложение C#, которое генерирует PDF с затемнённым прямоугольником, и поймёте, как настроить тень или изменить параметры экспорта.

## Что понадобится

- .NET 6 SDK (или любая недавняя версия .NET) – API работает одинаково и на .NET Framework 4.x.  
- NuGet‑пакет Aspose.Words for .NET (`Aspose.Words`) – установите его с помощью `dotnet add package Aspose.Words`.  
- Редактор кода – подойдёт Visual Studio, VS Code или Rider.  

Для этого примера не требуется дополнительная лицензия; бесплатный режим оценки достаточен, чтобы увидеть PDF‑вывод.

## Шаг 1: Настройка проекта и импорт пространств имён

Сначала создадим консольный проект и подключим необходимые классы.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*Почему это важно:* `Document` и `DocumentBuilder` предоставляют нам холст, а `Shape` и `ShadowFormat` позволяют рисовать и стилизовать прямоугольник. Предварительный импорт упрощает последующий код.

## Шаг 2: **Create rectangle shape** с нужными размерами

Теперь мы действительно создаём пустой документ и вставляем прямоугольник. Обратите внимание, что метод `InsertShape` возвращает объект `Shape`, который мы можем сразу стилизовать.

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*Объяснение*: Размер задаётся в пунктах (1 pt = 1/72 in). Подгоните числа под ваш макет. Мы также задаём фигуре светло‑голубую заливку, чтобы тень выделялась.

## Шаг 3: **Add shadow to shape** – тонкая настройка эффекта

Тень — это не просто «вкл/выкл». Вы можете управлять её цветом, размытием, расстоянием, направлением и даже прозрачностью. Ниже представлена практическая конфигурация, хорошо работающая для большинства отчетов.

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*Почему вы можете изменить эти значения:*  
- **BlurRadius** – увеличьте для мечтательного эффекта, уменьшите для чёткой границы.  
- **Direction** – 0° указывает вправо, 90° вниз, 180° влево и т.д. Поверните, чтобы соответствовать макету страницы.  
- **Transparency** – установите `0` для сплошной тени, `0.5` для полупрозрачной и т.д.

### Как добавить тень – альтернативные подходы

Если вам нужна **multiple‑layer shadow** (например, более тёмная внешняя тень плюс более светлая внутренняя), можно создать вторую форму, сместить её и задать другой `ShadowFormat`. Или, для быстрого вида без размытия, установить `BlurRadius = 0`.

## Шаг 4: **Save document as PDF** – финальный экспорт

Когда прямоугольник и его тень готовы, последний шаг — записать файл в формате PDF. Aspose.Words выполняет конвертацию внутри; вам достаточно вызвать `Save` с нужным форматом.

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*Совет*: Если нужно контролировать соответствие PDF (PDF/A, PDF/X) или встраивать шрифты, используйте перегруженный метод:

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

Это и есть суть **how to save pdf** в двух словах.

## Полный, исполняемый пример

Ниже приведена полная программа, которую можно скопировать и вставить в `Program.cs`. Она компилируется и работает сразу (только убедитесь, что папка вывода существует).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### Ожидаемый результат

Откройте сгенерированный `ShadowRectangle.pdf`. Вы увидите одну страницу со светло‑голубым прямоугольником, мягкой серой тенью, смещённой на 45° вниз‑вправо, и чистыми краями. PDF должен открываться в любом современном просмотрщике (Adobe Acrobat, Edge, Chrome).

![Создать прямоугольную форму с тенью в PDF](/images/shadow-rectangle.png "Создать прямоугольную форму с тенью в PDF")

*(Текст alt изображения включает основной ключевой запрос для SEO.)*

## Часто задаваемые вопросы и обработка граничных случаев

**Что делать, если тень исчезает в PDF?**  
Убедитесь, что используете последнюю версию Aspose.Words (≥23.3). В более старых сборках была ошибка, из‑за которой некоторые свойства тени игнорировались при конвертации в PDF.

**Можно ли изменить цвет тени, чтобы он соответствовал бренду?**  
Конечно — просто замените `System.Drawing.Color.Gray` на любой нужный `Color`, например `Color.FromArgb(128, 0, 0, 255)` для полупрозрачного синего.

**Как добавить тень к другим формам (эллипс, звезда и т.д.)?**  
Тот же `ShadowFormat` работает с любым объектом `Shape`. После создания формы получите её `ShadowFormat` и задайте свойства.

**Что насчёт DPI или проблем масштабирования?**  
Отрисовка PDF учитывает размер формы в пунктах. Если требуется вывод более высокого разрешения (для печати), скорректируйте размеры формы или задайте `PdfSaveOptions.ImageResolution`.

**Можно ли экспортировать в другие форматы, например PNG?**  
Да — просто вызовите `document.Save("output.png", SaveFormat.Png)`. Тень будет отрисована так же.

## Профессиональные советы и лучшие практики

- **Reuse the builder**: Если вы добавляете несколько фигур, храните один экземпляр `DocumentBuilder`; это дешевле, чем создавать их много.  
- **Batch saving**: При генерации множества PDF в цикле переиспользуйте объект `PdfSaveOptions`, чтобы избежать повторных выделений памяти.  
- **Testing**: Всегда открывайте PDF после сохранения, чтобы убедиться, что тень отображается как ожидается. Некоторые просмотрщики PDF отображают тени немного иначе; Adobe Acrobat — самый надёжный ориентир.  
- **Performance**: Для больших документов отключите автоматические разрывы страниц у `DocumentBuilder.InsertShape`, установив `builder.PageSetup.DifferentFirstPageHeaderFooter = false`, если они не нужны.  

## Заключение

Мы рассмотрели всё, что необходимо для **create rectangle shape**, **add shadow to shape** и **save document as PDF** с помощью Aspose.Words for .NET. Код компактный, концепции объяснены, и теперь у вас есть прочная база для экспериментов с другими формами, стилями теней и параметрами экспорта.  

Следующие шаги? Попробуйте заменить прямоугольник на скруглённый‑

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}