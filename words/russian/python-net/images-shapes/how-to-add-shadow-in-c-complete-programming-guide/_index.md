---
category: general
date: 2025-12-25
description: Как добавить тень в C# с простым примером кода. Узнайте, как установить
  расстояние тени, настроить цвет и создать глубину для вашей графики.
draft: false
keywords:
- how to add shadow
- how to set shadow distance
language: ru
og_description: Как добавить тень в C# объясняется пошагово. Следуйте руководству,
  чтобы установить расстояние тени, цвет и размытие для профессионально выглядящих
  фигур.
og_title: Как добавить тень в C# – Полное руководство по программированию
tags:
- C#
- graphics
- Aspose.Words
- shadows
title: Как добавить тень в C# – Полное руководство по программированию
url: /ru/python/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как добавить тень в C# – Полное руководство по программированию

Как добавить тень в C# — это распространённая задача, когда хочется, чтобы графика выглядела объёмной. В этом руководстве мы пройдём по точным шагам настройки тени фигуры, включая установку расстояния тени, регулировку размытия и выбор правильного цвета.  

Если вы когда‑нибудь смотрели на плоский прямоугольник и думали «нужна небольшая глубина», вы попали по адресу. Мы начнём с пустого документа, добавим фигуру и завершим полированной тенью, как будто её разместил дизайнер. Без лишних слов, только практический, готовый к запуску пример, который можно скопировать‑вставить уже сегодня.

## Что вы узнаете

- Как создать новый документ и программно вставить фигуру.  
- Как применить мягкое размытие к тени фигуры.  
- **Как установить расстояние тени**, чтобы тень выглядела естественно смещённой.  
- Как выбрать цвет тени, подходящий к любому фону.  
- Как сохранить результат в PDF (или в любом другом нужном формате).  

### Предварительные требования

- .NET 6.0 или новее (код работает с .NET Core и .NET Framework).  
- Aspose.Words for .NET (бесплатная пробная версия или лицензия).  
- Базовое понимание синтаксиса C#.  

И всё — без дополнительных библиотек, без магии. Приступим.

![Пример фигуры с мягкой чёрной тенью – как добавить тень](https://example.com/placeholder-shadow.png "пример добавления тени")

## Шаг 1: Настройка проекта и импорт пространств имён

Сначала создайте новое консольное приложение (или любой проект C#) и добавьте пакет NuGet Aspose.Words:

```bash
dotnet new console -n ShadowDemo
cd ShadowDemo
dotnet add package Aspose.Words
```

Теперь откройте `Program.cs` и подключите необходимые пространства имён:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;
```

> **Совет:** Если вы используете Visual Studio, IDE подскажет вам `using`‑операторы по мере ввода `Document`.

## Шаг 2: Создание нового документа и добавление фигуры

После подключения библиотек мы можем создать объект `Document` и разместить простой прямоугольник на первой странице.

```csharp
// Step 2: Initialize the document
Document doc = new Document();

// Add a blank page (Aspose.Words creates one automatically)
Section section = doc.FirstSection;

// Insert a rectangle shape – this will be the object we give a shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    // Size the shape (width, height) in points (1 point = 1/72 inch)
    Width = 200,
    Height = 100,
    
    // Position the shape 100 points from the left and 150 from the top
    Left = 100,
    Top = 150,
    
    // Fill the shape with a light gray so the shadow stands out
    FillColor = System.Drawing.Color.LightGray
};

// Add the shape to the document's first page
section.Body.FirstParagraph.AppendChild(rectangle);
```

Почему прямоугольник? Это нейтральный холст, позволяющий оценить эффект тени без отвлечения. Вы можете заменить `ShapeType.Rectangle` на `Ellipse` или `Star` — логика тени останется той же.

## Шаг 3: Как добавить тень — применяем размытие, расстояние и цвет

Теперь переходим к сердцу руководства: **как добавить тень** к этому прямоугольнику. Aspose.Words предоставляет объект `Shadow` для каждой фигуры, позволяя настраивать размытие, расстояние и цвет.

```csharp
// Step 3: Access the shape's shadow settings
Shadow shadow = rectangle.Shadow;

// 3a) Apply a soft blur – larger values make the shadow fuzzier
shadow.Blur = 5.0;          // 5 points blur gives a subtle, professional look

// 3b) Set the shadow's offset distance – this determines how far the shadow is displaced
shadow.Distance = 3.0;      // 3 points offset is enough to suggest depth without looking detached

// 3c) Choose a shadow color – black works on most backgrounds, but you can experiment
shadow.Color = Color.Black; // Solid black; you could use Color.FromArgb(128, 0, 0, 0) for semi‑transparent

// OPTIONAL: Rotate the shadow to match a light source direction (45 degrees works well)
shadow.Angle = 45.0;
```

Обратите внимание на комментарий `// 3b) Set the shadow's offset distance`. Эта строка непосредственно отвечает на вопрос **как установить расстояние тени**. Регулируя `shadow.Distance`, вы контролируете визуальный зазор между фигурой и её тенью, имитируя источник света под определённым углом.

### Почему такие значения?

- **Blur = 5.0** — Нежное размытие избегает резкой силуэтной линии, оставаясь при этом заметным.  
- **Distance = 3.0** — Тень находится достаточно близко, чтобы выглядеть отбрасываемой самой фигурой.  
- **Color = Black** — Обеспечивает контраст как на светлом, так и на тёмном фоне.  

Не стесняйтесь менять эти цифры; API принимает любые значения `double`, которые вам нужны.

## Шаг 4: Сохранение документа и проверка результата

После настройки тени мы просто записываем файл на диск. Aspose.Words может выводить множество форматов; PDF — популярный выбор для обмена.

```csharp
// Step 4: Save the document as a PDF (you could also use .docx, .png, etc.)
string outputPath = "ShadowedShape.pdf";
doc.Save(outputPath, SaveFormat.Pdf);

Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
```

Откройте `ShadowedShape.pdf`, и вы увидите серый прямоугольник с мягкой чёрной тенью, слегка смещённой вниз‑вправо. Если тень кажется слишком слабой, увеличьте `shadow.Blur` или `shadow.Distance` и запустите программу снова.

## Часто задаваемые вопросы и особые случаи

### Что делать, если нужна прозрачная тень?

Используйте ARGB‑цвет с альфа‑каналом меньше 255:

```csharp
shadow.Color = Color.FromArgb(80, 0, 0, 0); // 80/255 opacity = ~31% transparent
```

### Можно ли применить одну и ту же тень к нескольким фигурам?

Конечно. Создайте вспомогательный метод:

```csharp
static void ApplyStandardShadow(Shape shape)
{
    shape.Shadow.Blur = 5.0;
    shape.Shadow.Distance = 3.0;
    shape.Shadow.Color = Color.Black;
}
```

Вызовите `ApplyStandardShadow(rectangle);` для каждой добавляемой фигуры.

### Работает ли это со старыми версиями .NET Framework?

Да. Aspose.Words 22.9+ поддерживает .NET Framework 4.5 и выше. Просто скорректируйте файл проекта соответствующим образом.

## Полный рабочий пример

Ниже представлен весь код программы, который можно скопировать в `Program.cs`. Он компилируется и запускается сразу (при установленном пакете NuGet).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;

namespace ShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Initialize the document
            Document doc = new Document();
            Section section = doc.FirstSection;

            // Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 100,
                Top = 150,
                FillColor = System.Drawing.Color.LightGray
            };
            section.Body.FirstParagraph.AppendChild(rectangle);

            // Apply shadow – this is the core of "how to add shadow"
            Shadow shadow = rectangle.Shadow;
            shadow.Blur = 5.0;                // Soft blur
            shadow.Distance = 3.0;            // How to set shadow distance
            shadow.Color = Color.Black;       // Classic black shadow
            shadow.Angle = 45.0;              // Light source direction

            // Save as PDF
            string outputPath = "ShadowedShape.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
        }
    }
}
```

Запустите программу:

```bash
dotnet run
```

В папке проекта появится `ShadowedShape.pdf`. Откройте его в любом PDF‑просмотрщике, чтобы убедиться, что тень выглядит как описано.

## Заключение

Мы рассмотрели **как добавить тень** к фигуре в C# от начала до конца и показали **как установить расстояние тени** вместе с размитием и цветом. Всего лишь несколькими строками кода вы можете придать графике профессиональный, трёхмерный вид — без внешних дизайнерских инструментов.

Теперь, когда вы освоили основы, экспериментируйте:

- Смените цвет тени на лёгкий синий для более холодного ощущения.  
- Увеличьте размытие для мечтательного, диффузного эффекта.  
- Примените ту же технику к диаграммам, изображениям или текстовым блокам.  

Каждая вариация укрепляет те же базовые концепции, так что вы быстро научитесь настраивать тени под любые сценарии.  

Есть вопросы? Оставляйте комментарий, и счастливого кодинга!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}