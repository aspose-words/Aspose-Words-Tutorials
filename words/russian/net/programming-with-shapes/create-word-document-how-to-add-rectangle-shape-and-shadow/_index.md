---
category: general
date: 2026-03-19
description: Создайте документ Word на C# с помощью Aspose.Words, узнайте, как добавить
  форму, добавить прямоугольную форму, применить тень и сохранить документ в формате docx
  за несколько минут.
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: ru
og_description: Создайте документ Word с помощью Aspose.Words, добавьте прямоугольную
  форму, примените внешнюю тень и сохраните документ в формате docx. Пошаговое руководство.
og_title: Создать документ Word – добавить прямоугольную форму и тень
tags:
- Aspose.Words
- C#
- Document Automation
title: Создать документ Word – Как добавить прямоугольную форму и тень
url: /ru/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создать Word документ – Как добавить прямоугольную форму и тень

Когда‑нибудь вам нужно было **create word document** программно и вы задавались вопросом, с чего начать? Вы не одиноки. Многие разработчики сталкиваются с тем же самым, когда впервые пытаются сгенерировать файл .docx, содержащий пользовательскую графику. В этом руководстве мы пройдем весь процесс — как добавить форму, конкретно **add rectangle shape**, придать ей стильную **add shadow to shape**, и, наконец, **save document as docx**.  

К концу руководства у вас будет готовый к использованию фрагмент C#, который можно вставить в любой проект .NET. Никаких расплывчатых ссылок, только полный, готовый к запуску пример.  

## Требования

- .NET 6.0 или новее (код также работает с .NET Framework).  
- Установлен Aspose.Words для .NET (NuGet‑пакет `Aspose.Words`).  
- Базовое понимание синтаксиса C# — ничего сложного не требуется.  

Если у вас нет библиотеки, выполните:

```bash
dotnet add package Aspose.Words
```

Вот и всё — никаких дополнительных SDK, без COM‑interop, только одна ссылка NuGet.

---

## Шаг 1: Создать Word документ (основная цель)

Первое, что нам нужно, — чистый холст. Представьте класс `Document` как чистую страницу в Microsoft Word; он содержит секции, абзацы и всё остальное, что вы добавите позже.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

Зачем начинать с пустого `Document`? Потому что это гарантирует, что никакое скрытое форматирование не попадёт из шаблона. По моему опыту, начало с нуля избавляет от загадочных сдвигов макета при последующем вставлении фигур.

---

## Шаг 2: Вставить прямоугольную форму — добавление визуального элемента

Теперь, когда у нас есть документ, давайте **add rectangle shape** в первый абзац. Объект `Shape` универсален; вы можете выбрать `ShapeType.Rectangle`, `Ellipse` или даже пользовательские рисунки. Вот минимальный код:

```csharp
// Step 2: Create a rectangle and attach it to the first paragraph
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.78 inches)
    Height = 100,              // Height in points (≈1.39 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};

// Append the shape to the first paragraph (creates one if missing)
Paragraph firstPara = doc.FirstSection.Body.FirstParagraph;
firstPara.AppendChild(rect);
```

**Что происходит под капотом?**  
- `ShapeType.Rectangle` сообщает Aspose, что нам нужен простой прямоугольник.  
- `WrapType.Inline` гарантирует, что прямоугольник перемещается вместе с потоком текста, что обычно ожидается в сценариях обработки текста.  
- Добавляя к `FirstParagraph`, мы избегаем необходимости вручную вставлять новый абзац; Aspose создаст его, если документ действительно пуст.

> **Совет:** Если вам нужно, чтобы форма находилась *за* текстом, переключите `WrapType` на `WrapType.Transparent`. Это небольшое изменение может сильно повлиять на визуальный результат.

---

## Шаг 3: Применить внешнюю тень — улучшение внешнего вида

Плоский прямоугольник — … ну, плоский. Добавление **add shadow to shape** придаёт ему глубину без дополнительных изображений. `ShadowFormat` от Aspose делает это в одну строку.

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

Зачем использовать именно такие значения?  
- **Blur** со значением `5.0` даёт лёгкое размытие краёв, выглядящее профессионально на большинстве мониторов.  
- **Distance** со значением `3.0` и **Angle** `45` создают естественный источник света сверху‑слева, что является распространённым дизайнерским приёмом.  
- **Color.Gray** работает как в светлой, так и в тёмной темах; при необходимости более сильного контраста можно заменить его на `Color.Black`.  

Если вам понадобится *внутренняя* тень (например, у вдавленной кнопки), просто замените `ShadowType.OuterShadow` на `ShadowType.InnerShadow`. Те же свойства остаются применимыми.

---

## Шаг 4: Сохранить документ как DOCX — сохранение работы

Всё это здорово, но в конце концов вам понадобится файл на диске. Шаг **save document as docx** прост:

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

Несколько замечаний:  
- `SaveFormat.Docx` гарантирует использование современного формата Office Open XML, совместимого с Word 2007+.  
- Если нужно передать файл напрямую в веб‑ответ, замените путь к файлу на `MemoryStream` и запишите его в HTTP‑ответ.

После выполнения кода откройте `ShadowedRectangle.docx` в Microsoft Word. Вы должны увидеть серый прямоугольник с мягкой тенью, расположенный в строке с первым абзацем — именно то, чего мы добивались.

---

## Как добавить форму — альтернативные подходы

Приведённый выше пример использует подход *inline*, но иногда нужна форма, плавающая над текстом. Здесь в дело вступает **how to add shape** с различными типами обтекания.

```csharp
Shape floatingRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 250,
    Height = 120,
    WrapType = WrapType.Square, // Allows text to wrap around the shape
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    HorizontalAlignment = HorizontalAlignment.Center
};

doc.FirstSection.Body.FirstParagraph.AppendChild(floatingRect);
```

Здесь мы переключили `WrapType` на `Square` и центрировали форму на странице. Такой приём полезен для обложек или декоративных баннеров. Помните: плавающие формы немного увеличивают размер файла, так как Word сохраняет дополнительные данные о позиционировании.

---

## Ожидаемый результат и проверка

При открытии сгенерированного файла вы должны увидеть:

- Один абзац, содержащий серый прямоугольник.  
- Прямоугольник размером примерно 2.8 × 1.4 дюйма.  
- Лёгкую внешнюю тень, смещённую вниз‑вправо.  

Если форма появляется *вне* абзаца, проверьте `WrapType`. Если тень выглядит слишком резкой, уменьшите значение `Blur` или замените `Color` на более светлый оттенок.

---

## Распространённые ошибки и как их избежать

| Проблема | Почему происходит | Решение |
|----------|-------------------|---------|
| Фигура исчезает после сохранения | `WrapType` установлен в `Inline`, но абзац был удалён | Убедитесь, что абзац существует; используйте `doc.FirstSection.Body.FirstParagraph`, чтобы гарантировать его наличие. |
| Тень выглядит пиксельной | Используется слишком низкое значение `Blur` | Увеличьте `Blur` минимум до `3.0` для плавных краёв. |
| Размер файла резко растёт | Добавление множества изображений высокого разрешения вместе с формами | Вызовите `doc.RemoveUnusedResources()` перед сохранением, если вы добавляли изображения. |
| Цвет не отображается в тёмном режиме | Используется тёмный `Color` для самой формы | Выберите контрастный цвет (например, `Color.White`) для лучшей видимости. |

---

## Полный рабочий пример

Ниже представлен полный готовый к копированию код, включающий всё, о чём мы говорили. Смело запускайте его как консольное приложение.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank Word document
        Document doc = new Document();

        // 2️⃣ Add a rectangle shape to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 200,
            Height = 100,
            WrapType = WrapType.Inline
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Apply an outer shadow to the rectangle
        rect.ShadowFormat.Type = ShadowType.OuterShadow;
        rect.ShadowFormat.Blur = 5.0;
        rect.ShadowFormat.Distance = 3.0;
        rect.ShadowFormat.Angle = 45;
        rect.ShadowFormat.Color = Color.Gray;

        // 4️⃣ Save the document as a .docx file
        string outPath = @"C:\Temp\ShadowShape.docx";
        doc.Save(outPath, SaveFormat.Docx);

        // Optional: Let the user know we’re done
        System.Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Пояснение к каждому блоку** дано внутри в виде комментариев, удовлетворяя как читателей SEO, так и AI‑ассистентов, которым нравятся автономные ответы.

---

## Заключение

Мы только что **create word document** с нуля, узнали **how to add shape**, конкретно **add rectangle shape**, придали ей **add shadow to shape**, и, наконец, **save document as docx**. Шаги просты, код компактен, а результат выглядит отполированным.  

Если вы хотите пойти дальше, попробуйте заменить прямоугольник на пользовательское изображение, поэкспериментировать с разными цветами тени или сгенерировать целый отчёт с несколькими секциями, содержащими формы. API Aspose.Words достаточно гибок, чтобы справиться со всем — от счетов‑фактур до маркетинговых брошюр.  

Есть вопросы о других типах форм или нужна помощь с интеграцией в сервис ASP.NET Core? Оставьте комментарий ниже, и удачной разработки! 

![создать word документ с прямоугольной формой и тенью](placeholder-image.png "создать word документ с прямоугольной формой и тенью

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}