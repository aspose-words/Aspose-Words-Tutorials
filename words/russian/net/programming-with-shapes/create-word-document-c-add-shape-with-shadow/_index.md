---
category: general
date: 2026-03-27
description: Создайте документ Word на C# и узнайте, как добавить форму, применить
  к ней тень и установить расстояние тени. Пошаговое руководство по Aspose.Words.
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: ru
og_description: Создайте документ Word на C# с прямоугольной фигурой и пользовательской
  тенью. Следуйте этому полному руководству, чтобы задать расстояние тени и её стиль.
og_title: Создание документа Word на C# – Добавление фигуры с тенью
tags:
- Aspose.Words
- C#
- Document Automation
title: Создание документа Word на C# – Добавление фигуры с тенью
url: /ru/net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создать Word документ C# – Добавить форму с тенью

Когда‑нибудь вам нужно было **create word document c#**, содержащий аккуратно оформленный прямоугольник? Возможно, вы создаёте шаблон отчёта и хотите добавить лёгкую тень, чтобы макет выглядел более выразительно. В этом руководстве мы пошагово покажем, как добавить форму, применить к ней тень и даже отрегулировать расстояние тени с помощью Aspose.Words.

Мы начнём с пустого документа, вставим прямоугольник, зададим предустановленную тень и завершим сохранением файла. К концу у вас будет готовый .docx, который можно открыть в Word и сразу увидеть эффект. Никаких внешних инструментов, только чистый C# код.

## Предварительные требования

- .NET 6 (или любой современный .NET Framework) установлен.
- Visual Studio 2022 или VS Code с расширением C#.
- NuGet‑пакет Aspose.Words for .NET (`Aspose.Words` версии 23.12 или новее).  
  Добавить его можно через консоль диспетчера пакетов:

  ```powershell
  Install-Package Aspose.Words
  ```

Это всё – никаких дополнительных DLL или COM‑interop не требуется.

## Шаг 1: Инициализация нового документа и билдера – *create word document c#* Основы

Сначала нам нужен объект `Document`, представляющий файл Word, и `DocumentBuilder` для его редактирования.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Why this step matters:** Класс `Document` является контейнером для всех частей Word (страницы, стили, изображения). Builder – это высокоуровневый API, который абстрагирует низкоуровневую работу с узлами, делая процесс **create word document c#** простым без необходимости работать с XML напрямую.

## Шаг 2: Вставка прямоугольной формы – *how to create rectangle*  

Теперь мы разместим прямоугольник на странице. Размер указывается в пунктах (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **Pro tip:** Если нужна другая форма, просто замените `ShapeType.Rectangle` на `ShapeType.Ellipse`, `ShapeType.Triangle` и т.д. Тот же код работает для **how to add shape** любого типа.

## Шаг 3: Применение предустановленной тени и её тонкая настройка – *apply shadow to shape*  

Aspose.Words поставляется с несколькими предустановленными форматами теней. Мы используем `Preset1`, а затем настраиваем расстояние, размытие, прозрачность и цвет.

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **Why customize the shadow?** Свойство `Distance` определяет, насколько далеко тень располагается от прямоугольника – это как «подъём», который вы видите в 3‑D‑визуализации. Изменение `BlurRadius` смягчает края, а `Transparency` позволяет создать тонкий, профессиональный вид. Это покрывает требование **set shadow distance** и показывает, как **apply shadow to shape** гибко настраивать.

## Шаг 4: Сохранение документа – *create word document c#* Завершение

Наконец, сохраняем документ на диск. Укажите путь к папке, в которую у вас есть права записи.

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Откройте полученный файл в Microsoft Word, и вы увидите светло‑синий прямоугольник с мягкой серой тенью, смещённой на 5 pt. Это визуальное подтверждение того, что вы успешно **create word document c#** с оформленной формой.

![Create Word Document C# with Shadowed Shape](shadow-example.png){: .img alt="create word document c# пример, показывающий прямоугольник с тенью"}

## Дополнительные варианты и граничные случаи

| Сценарий | Что изменить | Почему это важно |
|----------|----------------|----------------|
| **Другой стиль тени** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | Даёт более драматичный вид без дополнительного кода. |
| **Без предустановки – пользовательская тень** | Omit `Format` and set `OffsetX`, `OffsetY` manually. | Полный контроль над направлением и глубиной. |
| **Несколько фигур** | Call `builder.InsertShape` again before saving. | Полезно для сложных шаблонов с иконками, логотипами и т.д. |
| **Совместимость со старыми версиями Aspose** | Use `ShadowEffect` class (available in v20.x). | Гарантирует работу кода в устаревших проектах. |
| **Сохранение в PDF** | `document.Save("ShadowShape.pdf");` | Тень отображается одинаково в PDF‑выводе. |

> **Частый вопрос:** *Что делать, если тень не отображается в Word?*  
> Убедитесь, что используете актуальную версию Aspose.Words (≥ 22.9). В более старых версиях поддержка теней была ограничена. Также проверьте, что документ открыт в актуальной версии Word (2016+).

## Полный рабочий пример

Ниже приведена полностью готовая к копированию программа. В ней включены все директивы `using`, комментарии и обработка ошибок для комфортной работы.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

Запустите программу, перейдите к `C:\Temp\ShadowShape.docx`, и вы увидите прямоугольник с точно такой же тенью, которую мы настроили.

## Итоги и дальнейшие шаги

- Теперь вы знаете, как **create word document c#**, вставить прямоугольник и **apply shadow to shape** с пользовательским **set shadow distance**.  
- Пример использует Aspose.Words, который скрывает сложности OpenXML и гарантирует одинаковый рендеринг во всех версиях Word.  
- Хотите идти дальше? Попробуйте комбинировать несколько фигур, добавить текст внутрь прямоугольника или экспортировать тот же документ в PDF, чтобы увидеть, как тень переносится.

### Связанные темы, которые могут быть интересны

- **How to add shape** в верхний/нижний колонтитул для брендинга.  
- Использование **Aspose.Words** для программного вставления диаграмм и таблиц.  
- Настройка **shadow effects** на изображениях вместо векторных форм.  
- Автоматизация массовой генерации документов для счетов или сертификатов.

Экспериментируйте, ломайте код и затем восстанавливайте его – так быстрее всего усвоите материал. Если столкнётесь с проблемой, оставьте комментарий ниже или обратитесь к официальной документации Aspose.Words для более глубокого изучения API.

Счастливого кодинга и приятного улучшения ваших Word‑файлов!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}