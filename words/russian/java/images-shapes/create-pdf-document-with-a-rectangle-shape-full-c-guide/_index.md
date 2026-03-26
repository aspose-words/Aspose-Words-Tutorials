---
category: general
date: 2026-03-25
description: Создайте PDF‑документ на C# и узнайте, как добавить прямоугольник, установить
  цвет заливки, настроить размер формы и задать её прозрачность всего за несколько
  шагов.
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: ru
og_description: Создайте PDF‑документ на C# и посмотрите, как добавить прямоугольник,
  установить его цвет заливки, размер и прозрачность для полированного PDF‑вывода.
og_title: Создание PDF‑документа с прямоугольной фигурой – учебник C#
tags:
- C#
- PDF
- Aspose.Words
title: Создание PDF‑документа с прямоугольной фигурой – Полное руководство по C#
url: /ru/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание PDF‑документа с прямоугольной фигурой – Полное руководство на C#

Когда‑нибудь вам нужно **создать PDF‑документ**, содержащий пользовательскую форму, но вы не знали, с чего начать? Вы не одиноки. Будь то генератор отчётов или рекламный листовка, возможность программно нарисовать прямоугольник, задать его цвет заливки, изменить размер и даже настроить прозрачность делает ваши PDF‑файлы гораздо более профессиональными.

В этом руководстве мы пройдём полный, готовый к запуску пример на C#, который **создаёт PDF‑документ**, **добавляет прямоугольную форму**, **устанавливает цвет заливки**, **задаёт размер формы** и **настраивает прозрачность формы** для лёгкой внешней тени. В конце у вас будет один PDF‑файл (`shadow.pdf`), который можно открыть и увидеть результат.

> **Pro tip:** Тот же подход работает с другими типами фигур (эллипс, линия и т.д.) — просто замените `ShapeType.RECTANGLE` на нужный тип.

---

## Что вам понадобится

| Требование | Почему это важно |
|------------|------------------|
| **.NET 6+** (или .NET Framework 4.6+) | Библиотека Aspose.Words ориентирована на современные среды выполнения. |
| **Aspose.Words for .NET** NuGet‑пакет | Предоставляет `Document`, `Shape`, `ShadowEffect` и связанные классы. |
| **IDE для C#** (Visual Studio, Rider, VS Code) | Делает отладку и запуск примера простыми. |
| **Базовые знания C#** | Вы сможете понять синтаксис без глубокого погружения. |

Вы можете установить библиотеку через командную строку:

```bash
dotnet add package Aspose.Words
```

И всё — никаких дополнительных DLL, никаких нативных зависимостей. Как только пакет установлен, код ниже скомпилируется и выполнится.

---

## Пошаговая реализация

Ниже процесс разбит на пять логических шагов. Каждый шаг имеет чёткий заголовок (чтобы модели ИИ могли его индексировать) и короткий блок кода, который можно скопировать‑вставить напрямую.

### ## 1. Создать PDF‑документ и подготовить холст

Первое, что мы делаем, — создаём объект `Document`. Представьте его как пустой холст, который в итоге станет вашим PDF‑файлом.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **Почему?** `Document` хранит все секции, абзацы и формы. Начало с чистого объекта гарантирует отсутствие скрытых артефактов от предыдущих запусков.

### ## 2. Добавить прямоугольную форму – задать цвет заливки и размер формы

Теперь мы создаём прямоугольник, задаём ему яркую жёлтую заливку и определяем его размеры. Это покрывает **add rectangle shape**, **set fill color** и **set shape size**.

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **Примечание:** Ширина/высота измеряются в пунктах (1 пункт = 1/72 дюйма). Подгоните эти числа под ваш макет.

### ## 3. Применить внешнюю тень и задать прозрачность формы

Тени добавляют глубину, а управление их непрозрачностью — суть **set shape transparency**. Ниже мы настраиваем серую внешнюю тень с 30 % прозрачностью.

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **Зачем задавать прозрачность?** Тень с 30 % прозрачностью выглядит деликатно, не делая прямоугольник «плоским» на странице.

### ## 4. Вставить форму в тело документа

Теперь мы помещаем прямоугольник в первый абзац первой секции документа. Этот шаг связывает всё вместе.

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **Крайний случай:** Если нужна форма на новой странице, добавьте перед вставкой `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;`.

### ## 5. Сохранить документ как PDF‑файл

Наконец, сохраняем структуру из памяти в физический PDF‑файл. Файл будет записан в указанную вами папку.

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

При запуске программы появится файл `shadow.pdf`. Открыв его, вы увидите жёлтый прямоугольник с мягкой серой тенью, смещённой на 4 пункта — точно то, что описывает наш код.

> **Ожидаемый результат:** Одностраничный PDF, где прямоугольник расположен в левом‑верхнем углу страницы, заполнен жёлтым, размером 200 × 100 пунктов и отбрасывает полупрозрачную внешнюю тень.

---

## Полный рабочий пример (готов к копированию)

Ниже весь исходный файл, готовый к вставке в новый консольный проект.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **Подсказка:** Замените `YOUR_DIRECTORY` на абсолютный путь, например `C:\Temp`, или относительный, например `.\output`. Программа создаст папку, если её ещё нет.

---

## Часто задаваемые вопросы (FAQ)

**В: Можно ли изменить позицию прямоугольника на странице?**  
О: Конечно. Установите `rectangle.Left` и `rectangle.Top` (оба измеряются в пунктах) перед добавлением его в абзац.

**В: Что если мне нужна прозрачная заливка вместо прозрачной тени?**  
О: Используйте `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` — первый аргумент это альфа‑канал (0‑255), где 128 даёт примерно 50 % прозрачности.

**В: Работает ли это с .NET Core?**  
О: Да. Aspose.Words поддерживает .NET Standard 2.0+, так что тот же код можно запускать на .NET 6, .NET 7 или .NET Framework 4.6+.

**В: Как добавить несколько фигур?**  
О: Просто повторите шаги 2‑4 для каждой формы, при необходимости вставляя их в разные абзацы или секции.

---

## Заключение

Мы только что **создали PDF‑документ** с нуля, **добавили прямоугольную форму**, **задали её цвет заливки**, **определили размер** и **отрегулировали прозрачность формы**, добившись изящного эффекта тени. Пример кода автономный, выполняется менее чем за минуту и демонстрирует основные концепции, необходимые для более сложных PDF‑макетов.

Готовы к следующему вызову? Попробуйте заменить прямоугольник на форму со скруглёнными углами, встроить изображение внутрь формы или автоматически сгенерировать оглавление. Тот же API позволяет накладывать текст, изображения и векторные элементы — возможности безграничны.

Если это руководство оказалось полезным, поставьте звёздочку на GitHub, поделитесь им с коллегой или оставьте комментарий со своими вариантами. Счастливого кодинга! 

---

![create pdf document with rectangle shape example](/images/rectangle-shadow.png "Screenshot showing the created PDF with a yellow rectangle and gray outer shadow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}