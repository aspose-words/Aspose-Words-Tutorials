---
category: general
date: 2026-02-18
description: Создайте прямоугольную форму с помощью Aspose.Words и узнайте, как добавить
  тень, задать размер формы и сохранить документ Word за несколько минут.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: ru
og_description: Создайте прямоугольную форму в файле Word, научитесь добавлять тень,
  задавать размер формы и сохранять документ с помощью Aspose.Words на C#.
og_title: Создание прямоугольной фигуры в Word – Полный учебник по Aspose.Words
tags:
- Aspose.Words
- C#
- Word automation
title: Создание прямоугольной фигуры в Word с помощью Aspose.Words – пошаговое руководство
url: /ru/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание прямоугольной фигуры в Word с помощью Aspose.Words – пошаговое руководство

Когда‑нибудь вам нужно было **создать прямоугольную фигуру** в файле Word, но вы не знали, с чего начать? Вы не одиноки — разработчики часто спрашивают: «как добавить тень к фигуре и при этом оставить документ редактируемым?» В этом руководстве мы ответим на этот вопрос, а также покажем, как **добавить тень**, **установить размер фигуры** и **сохранить документ Word** в одном плавном процессе.

Мы пройдём всё, что вам нужно, от инициализации нового документа (да, это первый шаг к **how to create document**) до сохранения финального *.docx* на диск. Никаких внешних ссылок, только автономный пример, который вы можете скопировать‑вставить в Visual Studio и запустить уже сегодня.

---

## Prerequisites

- .NET 6+ (или .NET Framework 4.7+). Aspose.Words работает с любой современной средой .NET.
- Действительная лицензия Aspose.Words (или бесплатный оценочный ключ) — иначе будет отображаться водяной знак.
- Visual Studio, Rider или любой другой редактор C#, который вам удобен.
- Базовые знания C# — ничего сложного, только возможность запустить консольное приложение.

> **Pro tip:** Если вы работаете на Mac, тот же код запускается под .NET 6 с VS Code — просто убедитесь, что подключён пакет `Aspose.Words` из NuGet.

---

## Step 1: Initialize the document – the foundation of **how to create document**

Прежде чем что‑то рисовать, нам нужен чистый холст. В Aspose.Words это называется `Document`.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **Why this matters:** Объект `Document` представляет весь файл *.docx*. Все фигуры, абзацы и секции, которые вы добавляете, становятся дочерними элементами этого объекта. Начало с чистого документа гарантирует отсутствие скрытых стилей, которые могут помешать вашему прямоугольнику.

---

## Step 2: Define the rectangle and **set shape size**

Прямоугольник — это просто `Shape` с `ShapeType.Rectangle`. Мы зададим ему явные размеры, чтобы он выглядел точно так, как задумано.

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **What the numbers mean:** Aspose.Words использует пункты (1 pt = 1/72 in). Подгоняйте значения под ваш макет; для типичной страницы A4 ширина 200 pt выглядит комфортно.

---

## Step 3: **How to add shadow** – making the shape pop

Тени дают визуальный сигнал, что фигура «поднята» над страницей. Свойство `Shadow` позволяет настроить цвет, расстояние, прозрачность и размытие.

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **Why use transparency?** Полностью непрозрачная тень может выглядеть резко. Установка значения 0.4 делает эффект более тонким и профессиональным.

---

## Step 4: Position the rectangle – inline flow with surrounding text

Если вы хотите, чтобы фигура вела себя как символ в абзаце, установите её `WrapType` в `Inline`. Это делает макет предсказуемым, особенно когда документ позже редактируется.

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **Edge case:** Если необходимо, чтобы прямоугольник плавал над текстом (например, как водяной знак), измените `WrapType` на `Square` или `BehindText`.

---

## Step 5: Insert the shape into the document body

Теперь мы действительно помещаем прямоугольник в первый абзац. Если в документе ещё нет содержимого, `FirstParagraph` создаётся автоматически.

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Tip:** Вы также можете сначала создать новый абзац, а затем добавить к нему фигуру — это удобно, когда нужен окружающий текст.

---

## Step 6: **Save Word document** – the final step

Когда всё готово, сохранение файла занимает одну строку кода. Укажите любой путь; в примере используется заполнитель, который следует заменить на ваш собственный каталог.

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **Result:** Откройте сгенерированный *.docx* в Microsoft Word. Вы увидите прямоугольник с чёрной тенью, шириной 200 pt и высотой 100 pt, расположенный в строке с первым абзацем.

---

## Expected output

При открытии **ShadowShape.docx** документ будет показывать:

- Один абзац, содержащий прямоугольную фигуру.
- Прямоугольник имеет лёгкую чёрную тень со смещением 5 pt.
- Размер фигуры соответствует параметрам, заданным в Шаге 2.
- Дополнительный текст не появляется, если вы не добавите его вручную.

Если фигура не отображается, проверьте, что вы подключили правильную версию Aspose.Words и что ваша лицензия (или пробная версия) активна.

---

## Common Questions & Variations

| Question | Answer |
|----------|--------|
| *Can I change the shadow color to something other than black?* | Absolutely—set `rectangleShape.Shadow.Color = Color.Blue;` or any `System.Drawing.Color`. |
| *What if I need a larger rectangle?* | Adjust `Width` and `Height` values. Remember they’re in points; 72 pt = 1 in. |
| *Is it possible to place the shape at an absolute position?* | Yes—use `WrapType = WrapType.Absolute` and set `Top`/`Left` properties. |
| *Does this work with .NET Core?* | It does. Aspose.Words is cross‑platform; just install the NuGet package for .NET Standard. |
| *Can I add text inside the rectangle?* | Not directly; you’d need to insert a `TextBox` shape instead of a plain rectangle. |

---

## Full Working Example (Copy‑Paste Ready)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

Запустите программу, перейдите к `C:\Temp\ShadowShape.docx`, и вы увидите прямоугольник с тенью точно так, как описано.

---

## Conclusion

Теперь вы знаете, как **create rectangle shape** в файле Word с помощью Aspose.Words, как **set shape size**, **add shadow** и, наконец, **save Word document** с внесёнными изменениями. Весь процесс — от **how to create document** до сохранения результата — укладывается в несколько строк C# и может быть расширен для более сложных макетов.

Готовы к следующему вызову? Попробуйте заменить прямоугольник на форму с закруглёнными углами, поэкспериментировать с разными цветами тени или встроить фигуру в ячейку таблицы. Каждое изменение укрепляет те же базовые концепции, которые мы рассмотрели здесь.

Если это руководство оказалось полезным, поделитесь им, оставьте комментарий со своими вариантами или изучите наши другие уроки по автоматизации Word, такие как вставка изображений или генерация таблиц с Aspose.Words. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}