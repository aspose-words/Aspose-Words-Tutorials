---
category: general
date: 2026-03-06
description: Создайте прямоугольную форму в Word и добавьте к ней тень с помощью Aspose.Words.
  Узнайте, как вставить прямоугольник в Word и как добавить тень к форме на C#.
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: ru
og_description: Создайте прямоугольную форму в Word и добавьте к ней тень с помощью
  Aspose.Words. Пошаговое руководство по вставке прямоугольника в Word и добавлению
  тени к фигуре.
og_title: Создайте прямоугольную фигуру с тенью в Word с помощью Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Создать прямоугольную форму с тенью в Word с помощью Aspose.Words
url: /ru/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание прямоугольной фигуры с тенью в Word с помощью Aspose.Words

Когда‑нибудь вам нужно было **create rectangle shape** в документе Word, но вы не знали, как придать ему отшлифованный вид? Вы не одиноки — большинство разработчиков сталкиваются с тем же препятствием, когда впервые пытаются добавить визуальный акцент в автоматические документы. Хорошая новость? С Aspose.Words для .NET вы можете как **create rectangle shape**, так и **add shape shadow** всего за несколько строк C#.

В этом руководстве мы подробно покажем, **how to insert rectangle in Word**, а затем продемонстрируем, **how to add shadow to shape**, чтобы фигура «выделялась» на странице. К концу вы получите готовый к сохранению `Shadow.docx`, который можно открыть в Word и увидеть серый прямоугольник с мягкой падающей тенью. Никаких дополнительных изображений, никаких ручных настроек — только код.

## Что вы узнаете

- Точные C#‑операторы, необходимые для **create rectangle shape** с Aspose.Words.  
- Как включить и настроить тень с помощью объекта `Shadow`.  
- Почему важен каждый параметр (например, `Transparency`, `Blur`, `Angle`).  
- Распространённые подводные камни (единицы измерения, совместимость версий) и быстрые решения.  
- Полный, готовый к копированию и вставке пример программы, который можно запустить уже сегодня.

### Предварительные требования

- .NET 6+ (или .NET Framework 4.7+).  
- Aspose.Words for .NET 23.10 или новее (пакет NuGet — `Aspose.Words`).  
- Базовое понимание C# и Visual Studio (или любой другой предпочитаемой IDE).  

Если всё это уже есть, давайте сразу приступим.

---

## Шаг 1: Настройте проект и импортируйте пространства имён

Сначала создайте новое консольное приложение (или используйте существующее) и добавьте пакет NuGet Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Теперь подключите необходимые пространства имён в ваш `Program.cs`:

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **Pro tip:** Если вы нацелены на .NET 6+, можете включить глобальные директивы `using`, чтобы не повторять эти строки в каждом файле.

## Шаг 2: **Create rectangle shape** в пустом документе Word

Мы начнём с нового объекта `Document` и `DocumentBuilder` для его изменения. Метод `InsertShape` билдера — это место, где происходит магия.

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Почему 200 × 100 пунктов? В Word один пункт равен 1/72 дюйма, поэтому прямоугольник получается примерно 2.8 × 1.4 дюйма — достаточно крупным, чтобы его заметили, но не перегрузить страницу. Вы можете изменить эти числа под свой макет; просто помните, что измеряется они в **points**, а не в пикселях.

## Шаг 3: **Add shape shadow** – настройка внешнего вида

Теперь, когда у нас есть прямоугольник, добавим к нему лёгкую серую тень. Объект `Shadow` находится в `Shape` и предоставляет несколько удобных свойств.

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### Что делает каждое свойство

| Свойство | Эффект | Типичные значения |
|----------|--------|-------------------|
| **Enabled** | Включает/выключает тень | `true` or `false` |
| **Color** | Базовый цвет тени | Любой `System.Drawing.Color` |
| **Transparency** | Непрозрачность (0 = сплошная, 1 = прозрачная) | 0.0 – 1.0 |
| **Blur** | Мягкость края | 0 – 10 (чем выше, тем мягче) |
| **Distance** | Расстояние между фигурой и тенью | 0 – 20 пунктов |
| **Angle** | Направление источника света | 0 – 360 градусов |
| **Size** | Масштаб тени относительно фигуры | 0 – 200 % |

> **Почему стоит настраивать эти параметры?**  
> Тонкая настройка тени позволяет соответствовать корпоративным рекомендациям по брендингу (например, лёгкая прозрачность 20 % для профессионального вида) без обращения к внешним графическим редакторам.

## Шаг 4: Сохраните документ и проверьте результат

Наконец, запишите файл на диск. Вы можете выбрать любую папку; просто замените `YOUR_DIRECTORY` реальным путём.

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Откройте `Shadow.docx` в Microsoft Word, и вы увидите серый прямоугольник с мягкой падающей тенью, смещённой под углом 45°. Этот визуальный приём делает фигуру «поднятой» над страницей — именно то, что ожидается от отшлифованного отчёта или счёта‑фактуры.

## Полный рабочий пример

Ниже представлен полный код программы, который можно скопировать‑вставить в `Program.cs`. Ничего не пропущено; он компилируется и работает «как есть».

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Ожидаемый результат

- **File:** `Shadow.docx`, размещённый в папке выполнения проекта.  
- **Visual:** Один прямоугольник, центрированный на странице, заполненный стандартным белым цветом, и серая тень, смещённая на 4 пункта вниз‑вправо, слегка размытая для естественного вида.

## Часто задаваемые вопросы и особые случаи

### 1. Что если мне нужна другая единица измерения (например, сантиметры)?

Aspose.Words работает в пунктах, но вы можете преобразовать сантиметры в пункты простой формулой:  
`points = centimeters * 28.3465`.  

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. Работает ли это со старыми версиями Aspose.Words?

API `Shadow` был введён в версии 14.0. Если вы используете более старый релиз, потребуется обновление через NuGet. Остальная часть кода (создание фигур) стабильно работает уже много лет, поэтому вы не столкнётесь с ломающими изменениями.

### 3. Могу ли я добавить тень к другим фигурам (например, кругам)?

Конечно — любой объект `Shape` имеет свойство `Shadow`. Просто замените `ShapeType.Rectangle` на `ShapeType.Ellipse` или `ShapeType.Cloud`, а затем примените те же настройки тени.

### 4. Что если мне нужна цветная тень (например, синяя для бренда)?

Замените `Color.Gray` на любой желаемый `Color`:

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

Не забудьте скорректировать `Transparency`, чтобы цвет не стал слишком доминирующим.

## 🎨 Визуальное резюме

![создание прямоугольной фигуры с тенью в Word с помощью Aspose.Words](image-placeholder.png "создание прямоугольной фигуры с тенью в Word с помощью Aspose.Words")

*Alt text: создание прямоугольной фигуры с тенью в Word с помощью Aspose.Words*

Скриншот (заполнитель) показывает окончательный документ — только прямоугольник и его мягкая серая тень.

## Заключение

Теперь вы знаете, как **create rectangle shape** в файле Word, **add shape shadow**, и как точно настроить каждый визуальный аспект с помощью Aspose.Words для .NET. Краткая программа, которую мы создали, охватывает весь рабочий процесс—from

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}