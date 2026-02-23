---
category: general
date: 2026-02-23
description: Создайте пустой документ Word с помощью C# и Aspose.Words. Узнайте, как
  добавить прямоугольную форму, добавить тень к слову и сохранить документ Word с
  фигурой за несколько минут.
draft: false
keywords:
- create blank word document
- add rectangle shape
- how to add shape
- add shadow word
- save word with shape
language: ru
og_description: Быстро создайте пустой документ Word. В этом руководстве показано,
  как добавить прямоугольную форму, добавить тень к слову и сохранить документ Word
  с фигурой, используя Aspose.Words.
og_title: Создать пустой документ Word – Полный учебник по C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Создание пустого документа Word с помощью Aspose.Words – пошаговое руководство
url: /ru/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/
---

.

Also maintain list items in FAQ.

Now produce final content with all shortcodes.

Let's write.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание пустого Word‑документа – Полный учебник C#

Когда‑нибудь задумывались, как **create blank word document** программно, не открывая Microsoft Word? Вы не одиноки. Во многих проектах автоматизации нам нужен свежий файл .docx, на него нужно разместить форму, добавить этой форме красивую тень, а затем **save word with shape** для последующего использования.  

В этом руководстве мы пройдём именно через это — начнём с пустого документа, **adding a rectangle shape**, настроим эффект **add shadow word**, и в конце сохраним файл. К концу вы получите полностью готовый, исполняемый фрагмент кода, который можно вставить в любое .NET‑консольное приложение. Никаких загадок, никаких недостающих частей.

## Что понадобится

- **Aspose.Words for .NET** (любая современная версия, например 24.10).  
- .NET 6 или новее (код также работает с .NET Framework 4.7+).  
- Любая базовая IDE для C# — Visual Studio, Rider или даже VS Code с расширением C#.  

Вот и всё. Нет дополнительных пакетов NuGet, кроме Aspose.Words, и установка Word не требуется.

---

## Шаг 1: Создать пустой Word‑документ

Первое, что делаете, когда хотите **create blank word document**, — создаёте экземпляр класса `Document`. Представьте его как чистый холст, который предоставляет вам Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1 – initialize an empty document
Document document = new Document();   // this is a brand‑new, blank Word file
```

> **Почему это важно:** Объект `Document` хранит все секции, абзацы и формы. Начало с пустого экземпляра гарантирует полный контроль над каждым элементом, который будет добавлен позже.

---

## Шаг 2: Добавить прямоугольную форму в документ

Теперь, когда у нас чистый документ, давайте **add rectangle shape**. Прямоугольник — это простая `Shape` с `ShapeType.Rectangle`. Конечно, можно выбрать другие типы, но прямоугольник отлично подходит для демонстрации.

```csharp
// Step 2 – create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width = 200,   // width in points (≈2.78 inches)
    Height = 100   // height in points (≈1.39 inches)
};
```

> **Pro tip:** Если когда‑нибудь захотите **how to add shape**, которая не является прямоугольником, просто замените `ShapeType.Rectangle` на любое другое значение перечисления, например `ShapeType.Ellipse` или `ShapeType.Polygon`. Остальной код остаётся без изменений.

---

## Шаг 3: Настроить пользовательскую тень для формы

Простой прямоугольник выглядит несколько скучно, поэтому мы **add shadow word**, чтобы он стал более выразительным. Aspose.Words предоставляет объект `ShadowFormat` со множеством свойств.

```csharp
// Step 3 – enable and style the shadow
rectangleShape.ShadowFormat.Enabled = true;                // turn on the shadow
rectangleShape.ShadowFormat.Color = Color.Gray;           // shadow color
rectangleShape.ShadowFormat.OffsetX = 5;                  // horizontal offset (points)
rectangleShape.ShadowFormat.OffsetY = 5;                  // vertical offset (points)
rectangleShape.ShadowFormat.Transparency = 0.3;           // 30 % transparent
rectangleShape.ShadowFormat.BlurRadius = 4;               // soft edge blur
```

> **Почему это важно:** Тень придаёт лёгкую глубину, особенно когда документ просматривается на экране. Настройте `OffsetX`, `OffsetY` и `BlurRadius` под ваш дизайн.

---

## Шаг 4: Вставить форму в документ

С готовой формой её нужно разместить где‑то. Самое простое место — первый абзац первой секции. Если в документе ещё нет абзацев, Aspose автоматически создаст один.

```csharp
// Step 4 – put the rectangle into the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Edge case:** Если планируете вставить форму в конкретное место (например, после определённого заголовка), найдите целевой `Paragraph` через `document.GetChildNodes(NodeType.Paragraph, true)` и используйте `InsertAfter` или `InsertBefore` соответственно.

---

## Шаг 5: Сохранить Word‑документ с формой

Наконец, мы **save word with shape** на диск. Метод `Save` автоматически определяет формат по расширению файла.

```csharp
// Step 5 – persist the document
string outputPath = @"C:\Temp\shadowedRectangle.docx";
document.Save(outputPath);
```

> **Что вы увидите:** Откройте `shadowedRectangle.docx` в Word (или любом совместимом просмотрщике) — вы увидите серый прямоугольник с мягкой тенью в верхней части первой страницы.

---

## Полный рабочий пример

Ниже приведена полная программа, которую можно скопировать и вставить в консольное приложение. В ней включены все директивы `using`, комментарии и точные шаги, о которых шла речь.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeWordShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank word document
            Document document = new Document();

            // 2️⃣ Add a rectangle shape
            Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100
            };

            // 3️⃣ Configure a custom shadow (add shadow word)
            rectangleShape.ShadowFormat.Enabled = true;
            rectangleShape.ShadowFormat.Color = Color.Gray;
            rectangleShape.ShadowFormat.OffsetX = 5;
            rectangleShape.ShadowFormat.OffsetY = 5;
            rectangleShape.ShadowFormat.Transparency = 0.3;
            rectangleShape.ShadowFormat.BlurRadius = 4;

            // 4️⃣ Insert the shape into the first paragraph
            document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

            // 5️⃣ Save the document (save word with shape)
            string outputFile = @"YOUR_DIRECTORY\shadow.docx";
            document.Save(outputFile);

            // Confirmation
            System.Console.WriteLine($"Document saved to {outputFile}");
        }
    }
}
```

Запустите программу, перейдите в `YOUR_DIRECTORY` и откройте сгенерированный `shadow.docx`. Вы должны увидеть прямоугольник с лёгкой серой тенью — именно то, что мы планировали.

---

## Часто задаваемые вопросы и советы

### Как изменить цвет формы?
```csharp
rectangleShape.FillColor = Color.LightBlue;
```
Просто задайте `FillColor` перед добавлением формы.

### Что делать, если нужно несколько форм на одной странице?
Создайте дополнительные объекты `Shape` и добавляйте каждый в тот же абзац или в разные абзацы. Вы также можете управлять расположением с помощью `WrapType` и `RelativeHorizontalPosition`.

### Можно ли экспортировать в PDF, сохранив тень?
Абсолютно. Используйте `document.Save("output.pdf")` — Aspose.Words сохраняет эффект тени при конвертации в PDF.

### Работает ли это в .NET Core?
Да. Aspose.Words кроссплатформен, тот же код работает в .NET Core, .NET 5+, и .NET Framework.

### Как добавить форму без абзаца?
Можно добавить форму напрямую в `Run` или в `Story`. Для более точного позиционирования задайте `rectangleShape.RelativeHorizontalPosition = RelativeHorizontalPosition.Page` и настройте свойства `Left`/`Top`.

---

## Визуальный результат

![Прямоугольная форма со серой тенью в документе Word – пример add shadow word](https://example.com/placeholder-image.png "пример add shadow word")

*Текст alt‑изображения включает вторичное ключевое слово **add shadow word** для SEO.*

---

## Заключение

Мы только что продемонстрировали, как **create blank word document**, **add rectangle shape**, применить эффект **add shadow word** и, наконец, **save word with shape** с помощью Aspose.Words for .NET. Процесс прост: создаём `Document`, формируем `Shape`, настраиваем её `ShadowFormat`, вставляем и вызываем `Save`.  

Отсюда вы можете экспериментировать — пробовать разные типы форм, играть с цветами или накладывать несколько форм. Если нужно объединить этот документ с существующим содержимым, просто загрузите файл через `new Document("existing.docx")` и выполните те же шаги.  

Есть вопросы? Оставляйте комментарий, и удачной разработки!

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}