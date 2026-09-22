---
category: general
date: 2026-01-13
description: Создайте документ Word с помощью Aspose.Words и узнайте, как вставить
  прямоугольную форму, как добавить тень и как добавить тень к форме в C#. Включён
  полный пример.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: ru
og_description: Создайте документ Word с помощью Aspose.Words, посмотрите, как вставить
  прямоугольную форму и как добавить тень. Следуйте полному примеру на C#.
og_title: Создайте документ Word с прямоугольником с тенью — полный учебник
tags:
- Aspose.Words
- C#
- Document Automation
title: Создайте документ Word с прямоугольником с тенью — пошаговое руководство
url: /ru/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание Word‑документа с затенённым прямоугольником – пошаговое руководство

Когда‑нибудь вам нужно было **create word document**, содержащий аккуратно затенённый прямоугольник, но вы не знали, с чего начать? Вы не одиноки — многие разработчики сталкиваются с тем же, когда впервые работают с Aspose.Words.  

В этом руководстве мы пройдёмся по всему, что нужно, чтобы **create word document** программно, **insert rectangle shape**, и покажем **how to add shadow**, чтобы фигура действительно выделялась. К концу вы получите готовый к запуску фрагмент C#, который можно вставить в любой проект .NET.

## Что вы узнаете

- Точный код для **how to insert shape** (прямоугольник) в файл Word.  
- Свойства, которые необходимо настроить, чтобы **add shape shadow** и контролировать его внешний вид.  
- Как сохранить результат и убедиться, что тень видна.  
- Несколько практических советов и замечаний о крайних случаях, которые спасут вас от головной боли позже.

Никакой внешней документации не требуется — всё находится здесь.

## Требования

Перед тем как начать, убедитесь, что у вас есть:

1. **.NET 6.0** (или любая современная версия .NET), установленный.  
2. **license** для Aspose.Words for .NET, либо вы можете использовать бесплатный режим оценки для тестов.  
3. Среда разработки — Visual Studio 2022 отлично подходит, но любой редактор, способный компилировать C#, подойдёт.

И всё. Дополнительные пакеты NuGet, кроме `Aspose.Words`, не требуются.

## Шаг 1 – Настройка проекта и подключение Aspose.Words

Сначала создайте новое консольное приложение и добавьте пакет Aspose.Words:

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **Pro tip:** Если вы используете бесплатную пробную версию, не забудьте вызвать `License.SetLicense` с вашим файлом лицензии; иначе библиотека добавит водяной знак.

## Шаг 2 – Инициализация Document Builder

Теперь мы начинаем фактический процесс **create word document**. Класс `Document` предоставляет пустой холст, а `DocumentBuilder` позволяет рисовать на нём.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

Зачем нужен builder? Он абстрагирует детали низкоуровневого OpenXML, так что вы можете сосредоточиться на *чём* хотите, а не на *как* файл структурирован. Это и есть ядро **how to insert shape** быстро.

## Шаг 3 – Вставка прямоугольника

Здесь мы действительно **insert rectangle shape**. Прямоугольник будет размером 150 × 100 пунктов (примерно 2 дюйма × 1,3 дюйма).

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

Метод `InsertShape` возвращает объект `Shape`, который мы можем дальше настраивать. На данном этапе прямоугольник — просто сплошная белая коробка, без тени.

## Шаг 4 – Как добавить тень (Add Shape Shadow)

Добавление тени удивительно простое, как только вы знаете, какие свойства менять. Объект `ShadowFormat` управляет видимостью, цветом, размытием, смещением и размером.

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

Этот блок отвечает на вопрос **how to add shadow** простыми словами: включите её, выберите цвет, отрегулируйте прозрачность, смещение, размытость и размер. Вы можете экспериментировать с этими числами, чтобы получить тяжёлую падающую тень или лёгкую, почти незаметную.

### Общие варианты

- **Разные цвета:** используйте `Color.Black` для классической тени или `Color.BlueViolet` для стилизованного эффекта.  
- **Нулевое размытие:** задайте `BlurRadius = 0` для чёткой, резкой границы.  
- **Большие смещения:** увеличьте `OffsetX`/`OffsetY`, чтобы тень отодвигалась дальше от фигуры.

## Шаг 5 – Сохранение документа и проверка

Наконец, запишите документ на диск. Файл будет стандартным `.docx`, который любой современный процессор Word сможет открыть.

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Откройте полученный *ShadowRectangle.docx* в Microsoft Word. Вы должны увидеть прямоугольник с мягкой серой тенью, смещённой вниз‑вправо — точно то, что указано в коде.

> **Expected output:** Одностраничный Word‑файл, содержащий прямоугольник 150 × 100 пунктов с 30 % полупрозрачной серой тенью, смещённой на 5 пт, размытой на 4 пт и масштабированной до 75 % от фигуры.

## Полный рабочий пример

Объединив всё вместе, получаем полностью готовую к запуску программу:

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Запустите программу (`dotnet run`), и у вас появится свежий Word‑файл с аккуратно затенённым прямоугольником — идеально для отчётов, сертификатов или любого визуального элемента, который вам нужен.

## Часто задаваемые вопросы (FAQs)

**Q: Можно ли вставлять другие фигуры (эллипс, звезду) и всё равно использовать тот же код тени?**  
A: Абсолютно. Метод `InsertShape` принимает любое значение перечисления `ShapeType`. Как только у вас есть экземпляр `Shape`, свойства `ShadowFormat` работают одинаково, так что **how to add shadow** не зависит от формы.

**Q: Что если мне нужна тень с обеих сторон фигуры?**  
A: Aspose.Words поддерживает только одну падающую тень на фигуру. Чтобы имитировать двойную тень, продублируйте фигуру, сместите каждую копию по‑разному и установите `ShadowFormat.Visible` у одной в `false`, оставив тень включённой у другой.

**Q: Работает ли это на .NET Framework 4.8?**  
A: Да. API не зависит от версии; просто подключите соответствующий DLL Aspose.Words для вашей целевой платформы.

## Советы и подводные камни

- **Не забудьте установить `Visible = true`** — иначе свойства тени игнорируются.  
- **Значения прозрачности находятся в диапазоне от 0.0 (непрозрачно) до 1.0 (полностью прозрачно).** Частая ошибка — использовать `30` вместо `0.3`.  
- **Сохранение в папку только для чтения вызывает исключение.** Убедитесь, что каталог вывода доступен для записи.

## Следующие шаги

Теперь, когда вы знаете **how to insert shape**, **add shape shadow** и **create word document** с помощью Aspose.Words, вы можете исследовать:

- Добавление **text inside the rectangle** с помощью `builder.InsertParagraph()` перед вставкой фигуры.  
- Применение **gradient fills** или **patterned borders** для более богатого визуального стиля.  
- Автоматизацию генерации нескольких страниц, каждая с разной затенённой фигурой, для создания динамических отчётов.

Не стесняйтесь экспериментировать — изменение цвета тени, размытости или размера может кардинально изменить внешний вид вашего документа.

---

*Готовы вывести это в продакшн? Возьмите код, подкорректируйте параметры и наблюдайте, как ваши Word‑файлы за секунды получают профессиональный блеск.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}