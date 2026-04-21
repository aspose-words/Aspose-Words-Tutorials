---
category: general
date: 2026-04-21
description: Создайте документ Word со стилизованным прямоугольником и тенью. Узнайте,
  как добавить тень, вставить форму прямоугольника, задать цвет тени и многое другое
  в C#.
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: ru
og_description: Создайте документ Word и добавьте прямоугольник с тенью в C#. Следуйте
  этому руководству, чтобы легко задать цвет тени, размытие и смещения.
og_title: Создайте документ Word с прямоугольником в тени — пошагово
tags:
- Aspose.Words
- C#
- Document Automation
title: Создание документа Word с прямоугольником с тенью – полное руководство
url: /ru/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Создание Word‑документа с прямоугольником в тени – Полное руководство

Когда‑нибудь вам нужно было **create word document**, который выглядит более профессионально, чем обычная страница текста? Возможно, вы создаёте шаблон отчёта или листовку, и простой прямоугольник с лёгкой тенью решит задачу. В этом руководстве мы пошагово покажем, как вставить форму‑прямоугольник, включить тень и настроить её цвет, размытие и смещения — всё с помощью C# и Aspose.Words.

Мы также расскажем, **how to add shadow** так, чтобы это работало в Word 2016, 2019 и последней сборке Office 365. К концу вы получите готовый к сохранению файл *.docx* с красиво затенённым прямоугольником и поймёте, «почему» каждый параметр установлен именно так.

## Prerequisites

- .NET 6 (или любая современная версия .NET Framework)  
- Aspose.Words for .NET NuGet‑пакет (`Install-Package Aspose.Words`)  
- Базовое знакомство с синтаксисом C#  
- IDE, например Visual Studio (подойдёт любой редактор)

Дополнительные библиотеки не требуются; всё необходимое находится в Aspose.Words.

## Step 1 – Initialize the Document and Builder (Create Word Document)

Чтобы **create word document** программно, начните с класса `Document`. `DocumentBuilder` — это ваша кисть; он позволяет добавлять текст, фигуры и другие элементы.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters:* Объект `Document` представляет весь файл .docx. Без него нет места, куда можно прикрепить прямоугольник или его тень.

## Step 2 – Insert a Rectangle Shape (Insert Rectangle Shape)

Теперь действительно **insert rectangle shape**. Метод `InsertShape` принимает перечисление `ShapeType`, а также ширину и высоту в пунктах.

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*Pro tip:* 1 пункт ≈ 1/72 дюйма, поэтому 200 пт ≈ 2,78 дюйма в ширину. Подгоняйте эти значения под ваш макет.

## Step 3 – Enable the Shadow (How to Add Shadow)

Тени по умолчанию отключены. Переключите флаг `Visible`, чтобы включить её.

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*What’s happening?* Когда `Visible` равно `true`, Word отрисует падающую тень, используя свойства, которые вы зададите дальше.

## Step 4 – Customize Shadow Appearance (Set Shadow Color, Blur, Offsets)

Здесь вы **set shadow color**, радиус размытия и смещения по X/Y. Экспериментируйте — разные значения дают мягкое свечение, глубокую тень или даже «парящий» эффект.

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*Why these numbers?* Размытие 5 пт создаёт нежный перьевый край, а смещение 4 пт сдвигает тень вниз‑вправо, имитируя источник света сверху‑слева. Замените `Color` на `Color.Black` для более контрастной тени или используйте `Color.FromArgb(128, 0, 0, 0)` для полупрозрачного чёрного.

### Edge Cases & Variations

- **No blur:** Установите `Blur = 0` для чёткой, жёсткой тени.  
- **Negative offsets:** Используйте `OffsetX = -4`, чтобы сдвинуть тень влево.  
- **Different shapes:** Те же свойства тени работают для кругов, треугольников и даже произвольно нарисованных фигур — просто измените `ShapeType` в Шаге 2.  
- **Compatibility:** Aspose.Words записывает данные тени в формате Office Open XML, который поддерживается в Word 2010‑2021 и Office 365.

## Step 5 – Save the Document (Create Word Document)

Наконец, сохраняем файл на диск. Можно выбрать любой поддерживаемый формат (`.docx`, `.pdf`, `.odt`, …), но в этом руководстве будем использовать классический формат Word.

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

Когда откроете **ShadowRectangle.docx** в Microsoft Word, вы увидите серый прямоугольник с лёгкой размытой тенью, смещённой вниз‑вправо — точно то, что мы запрограммировали.

### Expected Output

- Одностраничный файл *.docx*.  
- Прямоугольник 200 pt × 100 pt, центрированный в месте курсора в момент вызова `InsertShape`.  
- Серая тень, смещённая на 4 пт вправо и 4 пт вниз, с размитием 5 pt.

Если фигура выглядит смещённой, переместите курсор с помощью `builder.MoveTo` перед вставкой или отрегулируйте свойства `Left` и `Top` у фигуры после вставки.

## Common Questions & Troubleshooting

**Q: Тень не отображается в Word.**  
A: Убедитесь, что `ShadowFormat.Visible` установлен в `true`. Также проверьте, что используете актуальную версию Aspose.Words (функция тени была добавлена в версии 20.3).

**Q: Можно ли применить градиент к тени?**  
A: Не напрямую через `ShadowFormat`. В пользовательском интерфейсе Word поддерживает градиентные тени, но схема Open XML (к которой следует Aspose.Words) предоставляет только сплошные цветные тени. Для градиента придётся вручную редактировать XML — более продвинутый сценарий.

**Q: А если нужен прозрачный прямоугольник, оставив только тень?**  
A: После вставки установите `rectangle.FillColor = Color.Transparent;`. Тень будет отображаться, так как она независима от заливки.

## Pro Tips for Production Code

- **Reuse the builder:** При добавлении нескольких фигур используйте один и тот же экземпляр `DocumentBuilder` — создание нового для каждой фигуры создаёт лишние накладные расходы.  
- **Batch saves:** Сохраняйте документ один раз после всех изменений; частые операции ввода‑вывода замедляют генерацию больших документов.  
- **Error handling:** Оберните весь блок в `try / catch` и логируйте исключения `Aspose.Words`; они часто содержат полезные номера строк, если шаблон документа повреждён.

## Next Steps (Related Topics)

- **How to add shadow** к изображениям или текстовым блокам (аналогичное использование `ShadowFormat`).  
- **Insert rectangle shape** внутри ячейки таблицы для кастомного оформления ячейки.  
- **Create rectangle in Word** с помощью нативного XML Word (для тех, кто предпочитает чистый Open XML).  
- **Set shadow color** динамически в зависимости от ввода пользователя или цветовой схемы темы.

Экспериментируйте с разными цветами, радиусами размытия и смещениями — возможно, мягкое синее свечение для корпоративного отчёта или глубокая чёрная тень для драматичной листовки. Возможностей множество, а изменения в коде минимальны.

---

### Quick Recap

- Мы **created a word document** с нуля.  
- Мы **inserted a rectangle shape** и включили её тень.  
- Мы **set shadow color**, размытие и смещения для профессионального вида.  
- Мы сохранили файл, готовый к распространению.

Теперь у вас есть надёжная база для добавления визуального шарма в любой проект автоматизации Word. Есть идеи? Оставляйте комментарий, и будем обсуждать дальше. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}