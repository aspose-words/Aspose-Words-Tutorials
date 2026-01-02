---
category: general
date: 2026-01-02
description: Создайте документ Word с прямоугольной фигурой, задайте цвет заливки
  фигуры и сохраните файл docx с помощью Aspose.Words. Узнайте, как за несколько минут
  создать прямоугольник с тенью.
draft: false
keywords:
- create word document
- add rectangle shape
- set shape fill color
- save docx file
- how to create rectangle
language: ru
og_description: Создайте документ Word с пользовательским прямоугольником, задайте
  его цвет заливки, добавьте тень и сохраните как DOCX. Полный код и объяснения.
og_title: Создайте документ Word с прямоугольной фигурой – пошагово
tags:
- Aspose.Words
- C#
- Document Generation
title: Создание документа Word с прямоугольной фигурой и тенью – полное руководство
url: /ru/net/programming-with-shapes/create-word-document-with-rectangle-shape-and-shadow-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание Word документа с прямоугольной фигурой и тенью – Полное руководство

Когда‑то задавались вопросом, как **создать word document**, содержащий красиво оформленный прямоугольник? Возможно, вам нужен заполнитель для логотипа, цветной баннер или просто визуальный маркер в отчёте. В этом руководстве мы **добавим прямоугольную фигуру**, зададим ей цвет заливки, применим лёгкую тень и, наконец, **сохраним docx файл** – всё с помощью Aspose.Words для .NET.

Вы получите готовый к запуску фрагмент C#, понятное объяснение каждой строки и несколько советов, которые можно переиспользовать в своих проектах. Без лишних слов, только практическое решение, готовое к копированию‑вставке.

## Что понадобится

- .NET 6 или новее (код также работает на .NET Framework)  
- Visual Studio 2022 (или любой другой предпочитаемый редактор)  
- **Aspose.Words** NuGet‑пакет (`Install-Package Aspose.Words`)  

Если всё уже установлено – отлично, приступаем.

## Шаг 1 – Инициализация нового документа (How to create word document)

Первое, что нужно сделать, – **создать word document** в памяти. Представьте это как открытие чистого холста, на котором позже будет нарисован ваш прямоугольник.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // for Color struct

// Create a fresh, empty document
Document document = new Document();

// DocumentBuilder helps us add content step‑by‑step
DocumentBuilder builder = new DocumentBuilder(document);

// Write a simple heading so you can see something when you open the file
builder.Writeln("Shadow Demo");
```

> **Почему это важно:** `Document` представляет весь файл DOCX, а `DocumentBuilder` – удобный помощник, позволяющий вставлять текст, таблицы, изображения и фигуры без ручного управления внутренним деревом узлов.

## Шаг 2 – Вставка прямоугольной фигуры (Add rectangle shape)

Теперь мы **добавим прямоугольную фигуру** в документ. Метод `InsertShape` принимает тип фигуры и её размеры в пунктах (1 пункт = 1/72 дюйма).

```csharp
// Insert a rectangle that will later receive a custom shadow
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue background so it stands out
rect.FillColor = Color.LightBlue;
```

> **Pro tip:** Если понадобится другая геометрия (эллипс, треугольник и т.д.), просто замените `ShapeType.Rectangle` на нужное значение перечисления.

## Шаг 3 – Настройка тени (Set shape fill color & shadow)

Тень делает плоскую фигуру более объёмной. Здесь мы включаем тень и подправляем её параметры.

```csharp
// Turn the shadow on
rect.ShadowFormat.Enabled = true;

// Choose a subtle gray for the shadow color
rect.ShadowFormat.Color = Color.Gray;

// Blur softens the edge of the shadow – 8 points looks nice
rect.ShadowFormat.BlurRadius = 8;

// Distance controls how far the shadow is offset from the shape
rect.ShadowFormat.Distance = 5;

// Angle determines the direction; 45° gives a bottom‑right offset
rect.ShadowFormat.Angle = 45;

// Transparency makes the shadow partially see‑through (0 = opaque, 1 = invisible)
rect.ShadowFormat.Transparency = 0.3; // 30 % transparent
```

> **Почему такие значения?** Небольшой радиус размытия и расстояние в 5 пунктов не позволяют тени «перекрыть» фигуру, а угол 45° имитирует источник света сверху‑слева – распространённый UI‑приём.

## Шаг 4 – Сохранение документа (Save docx file)

Наконец, мы **сохраняем docx файл** на диск. Подкорректируйте путь под свою среду.

```csharp
// Replace with the folder you actually want to use
string outputPath = @"C:\Temp\ShadowDemo.docx";

// Persist the document as a .docx file
document.Save(outputPath);
```

Открыв `ShadowDemo.docx` в Word, вы увидите светло‑голубой прямоугольник с мягкой серой тенью, как на скриншоте ниже.

![Create Word Document with rectangle shape and shadow](https://example.com/images/rectangle-shadow.png "Create Word Document with rectangle shape and shadow")

*Текст alt изображения:* **Create Word Document** показывающий прямоугольную фигуру с тенью.

## Полный готовый к запуску пример (How to create rectangle and save)

Объединив всё вместе, получаем полную программу, которую можно скопировать в консольное приложение:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Initialize the document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);
            builder.Writeln("Shadow Demo");

            // Step 2: Insert the rectangle
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rect.FillColor = Color.LightBlue;   // set shape fill color

            // Step 3: Apply shadow formatting
            rect.ShadowFormat.Enabled = true;
            rect.ShadowFormat.Color = Color.Gray;
            rect.ShadowFormat.BlurRadius = 8;
            rect.ShadowFormat.Distance = 5;
            rect.ShadowFormat.Angle = 45;
            rect.ShadowFormat.Transparency = 0.3;

            // Step 4: Save the file
            string output = @"C:\Temp\ShadowDemo.docx";
            doc.Save(output);

            System.Console.WriteLine($"Document saved to {output}");
        }
    }
}
```

### Ожидаемый результат

- В целевой папке появляется файл **ShadowDemo.docx**.  
- При открытии в Microsoft Word отображается одна страница с текстом «Shadow Demo», за которым следует светло‑голубой прямоугольник.  
- Прямоугольник отбрасывает мягкую серую тень под углом 45°, создавая лёгкое 3‑D ощущение.

## Часто задаваемые вопросы и особые случаи

### Что делать, если нужен другой размер?

Просто измените аргументы `200, 100` в `InsertShape`. Эти числа – ширина и высота в пунктах. Для квадрата используйте одинаковые значения.

### Можно ли сделать тень более выраженной?

Увеличьте `BlurRadius` для более плавного края, поднимите `Distance` для большего смещения или уменьшите `Transparency` (например, `0.1`), чтобы сделать её темнее.

### Как добавить границу вокруг прямоугольника?

```csharp
rect.LineColor = Color.DarkBlue;   // border color
rect.LineWidth = 2;                // thickness in points
```

### Совместима ли эта функция со старыми версиями Aspose.Words?

Да. Класс `ShadowFormat` существует с ранних релизов 2020 года. Если вы используете очень старую версию, возможно, потребуется обновление для доступа ко всем свойствам.

## Советы и подводные камни

- **Pro tip:** Всегда освобождайте большие документы (`doc.Dispose()`), когда они больше не нужны, особенно в веб‑приложениях, чтобы освободить нативные ресурсы.  
- **Осторожно:** Использование относительного пути без соответствующих прав может вызвать `UnauthorizedAccessException`. Предпочтительно использовать абсолютные пути или убедиться, что пул приложений имеет права записи.  
- **Помните:** Свойство `FillColor` принимает любой `System.Drawing.Color`. Можно, например, задать `Color.FromArgb(255, 173, 216, 230)` для пользовательского пастельного оттенка.

## Следующие шаги

Теперь, когда вы знаете, как **создать word document**, **добавить прямоугольную фигуру**, **задать цвет заливки** и **сохранить docx файл**, можно экспериментировать дальше:

- Вставлять несколько фигур и располагать их с помощью `RelativeHorizontalPosition` и `RelativeVerticalPosition`.  
- Комбинировать прямоугольник с текстом, используя `Shape.TextBox` для подписей.  
- Экспортировать тот же документ в PDF (`doc.Save("output.pdf")`) для распространения.

Если интересуют более продвинутые графические возможности, ознакомьтесь с поддержкой **WordArt**, **диаграмм** и **встроенных изображений** в Aspose.Words. Во всех случаях схема одинаковая: создать узел, настроить свойства и сохранить.

---

### TL;DR

- Используйте `Document` и `DocumentBuilder` для **создания word document**.  
- Вызовите `InsertShape(ShapeType.Rectangle, …)` для **добавления прямоугольной фигуры**.  
- Установите `FillColor` для нужного фона.  
- Включите `ShadowFormat` и подправьте её свойства для профессионального вида.  
- Завершите вызовом `document.Save("yourPath.docx")` для **сохранения docx файла**.

Приятного кодинга и наслаждайтесь более стильными Word‑файлами!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}