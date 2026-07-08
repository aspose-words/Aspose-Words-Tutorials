---
category: general
date: 2026-06-30
description: Как добавить тень в C# с помощью Aspose.Words. Узнайте, как изменить
  цвет тени, настроить её прозрачность, добавить тень к фигуре и сохранить изменённый
  документ.
draft: false
keywords:
- how to add shadow
- change shadow color
- save modified document
- add shadow to shape
- adjust shadow transparency
language: ru
og_description: Как добавить тень в C# с помощью Aspose.Words. Этот учебник показывает,
  как добавить тень к фигуре, изменить цвет тени, отрегулировать её прозрачность и
  сохранить изменённый документ.
og_title: Как добавить тень к фигурам Word – Полное руководство по C#
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: How to add shadow in C# using Aspose.Words. Learn to change shadow
    color, adjust shadow transparency, add shadow to shape, and save modified document.
  headline: How to Add Shadow to Word Shapes – Complete C# Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Как добавить тень к фигурам Word – полное руководство по C#
url: /ru/net/programming-with-shapes/how-to-add-shadow-to-word-shapes-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Как добавить тень к фигурам Word – Полное руководство на C#

Когда‑нибудь задавались вопросом **как добавить тень** к фигуре Word с помощью C#? Вы не одиноки. Разработчикам часто нужна эта тонкая глубина для отчетов, брошюр или любого документа, который должен выглядеть более профессионально. Хорошая новость? Всего несколькими строками кода можно включить тень, изменить её цвет и даже настроить прозрачность — всё это полностью автоматизировано.

В этом руководстве мы пройдемся по **добавлению тени** к фигуре, **изменению цвета тени**, **регулированию прозрачности тени** и, наконец, **сохранению изменённого документа**, чтобы изменения сохранились. К концу вы получите переиспользуемый фрагмент кода, который можно вставить в любой проект Aspose.Words.

## Требования

Прежде чем начать, убедитесь, что у вас есть:

* **Aspose.Words for .NET** (версия 23.11 или новее). Вы можете установить его через NuGet командой `Install-Package Aspose.Words`.
* Среда разработки **.NET 6+** (Visual Studio, Rider или VS Code).
* Входной файл Word (`input.docx`), уже содержащий хотя бы одну фигуру (например, прямоугольник, звезду или изображение).

И всё — никаких дополнительных библиотек, никаких ручных действий в UI. Готовы? Поехали.

## Шаг 1 – Загрузка документа Word (Как добавить тень)

Первое, что нужно знать **как добавить тень**, — это загрузить документ в объект `Aspose.Words.Document`. Это даст вам программный доступ к каждому узлу, включая фигуры.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the source document that contains the shape.
        Document doc = new Document(@"C:\Docs\input.docx");
```

> **Почему это важно:** Загрузка файла открывает путь к любой манипуляции. Без экземпляра `Document` вы не сможете добраться до дерева фигур и, соответственно, не сможете применить тень.

## Шаг 2 – Получение целевой фигуры (Добавить тень к фигуре)

Теперь, когда документ находится в памяти, найдём фигуру, которую хотим стилизовать. Этот шаг показывает **добавление тени к фигуре** для первой найденной фигуры, но вы легко можете расширить его, выбирая по имени или индексу.

```csharp
        // Retrieve the first shape in the document (searches recursively).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        if (shape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }
```

> **Подсказка:** Если в документе несколько фигур, замените `0` на нужный индекс или пройдитесь в цикле по `doc.GetChildNodes(NodeType.Shape, true)`.

## Шаг 3 – Включение тени и настройка её внешнего вида (Изменить цвет тени и регулировать прозрачность тени)

Вот сердце **как добавить тень**: включаем тень, задаём смещение, размытие, цвет и прозрачность. Экспериментируйте с числовыми значениями, чтобы получить нужный вид.

```csharp
        // Turn the shadow on.
        shape.ShadowFormat.Visible = true;

        // Position the shadow 4 points to the right and 4 points down.
        shape.ShadowFormat.OffsetX = 4; // Horizontal offset in points.
        shape.ShadowFormat.OffsetY = 4; // Vertical offset in points.

        // Adjust shadow transparency – this demonstrates **adjust shadow transparency**.
        shape.ShadowFormat.Transparency = 0.3; // 30 % transparent.

        // Change the shadow color – this is the **change shadow color** part.
        shape.ShadowFormat.Color = Color.Gray; // You can use any System.Drawing.Color.

        // Add a subtle blur to soften the edges.
        shape.ShadowFormat.BlurRadius = 5; // Blur radius in points.
```

> **Почему такие настройки?**  
> *`Visible`* включает эффект.  
> *`OffsetX`/`OffsetY`* имитируют источник света, создавая глубину.  
> *`Transparency`* позволяет сделать тень светлее или темнее без изменения цвета — классический способ **регулирования прозрачности тени**.  
> *`Color`* позволяет **изменить цвет тени**; серый подходит для большинства деловых документов, но вы можете использовать `Color.Black` или любой пользовательский `Color.FromArgb(...)`.  
> *`BlurRadius`* добавляет реализм — резкие тени выглядят искусственно.

## Шаг 4 – Сохранение изменённого документа (Сохранить изменённый документ)

Наконец, фиксируем изменения. Этот шаг отвечает на вопрос **сохранить изменённый документ** без какого‑либо ручного вмешательства.

```csharp
        // Save the updated document to a new file.
        doc.Save(@"C:\Docs\output.docx");

        Console.WriteLine("Shadow applied and document saved successfully.");
    }
}
```

> **Что происходит «под капотом»?** Aspose.Words записывает обновлённые XML‑части, включая элемент `<w:shadow>` со всеми только что установленными атрибутами. Полученный `output.docx` откроется в Word с уже применённой тенью.

## Полный рабочий пример

Собрав всё вместе, получаем готовую к копированию программу:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        Document doc = new Document(@"C:\Docs\input.docx");

        // 2️⃣ Retrieve the first shape (add shadow to shape).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Enable the shadow and configure its appearance.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.OffsetX = 4;
        shape.ShadowFormat.OffsetY = 4;
        shape.ShadowFormat.Transparency = 0.3;      // Adjust shadow transparency.
        shape.ShadowFormat.Color = Color.Gray;      // Change shadow color.
        shape.ShadowFormat.BlurRadius = 5;

        // 4️⃣ Save the modified document (save modified document).
        doc.Save(@"C:\Docs\output.docx");

        Console.WriteLine("Shadow applied and document saved successfully.");
    }
}
```

### Ожидаемый результат

Откройте `output.docx` в Microsoft Word. Первая фигура из `input.docx` теперь будет отображать мягкую серую тень, смещённую на 4 pt, с 30 % прозрачностью и лёгким размытием. Остальная часть документа останется без изменений.

## Распространённые варианты и граничные случаи

| Ситуация | Что изменить | Почему |
|-----------|----------------|-----|
| **Несколько фигур** | Пройтись в цикле по `doc.GetChildNodes(NodeType.Shape, true)` и применить те же настройки к каждой. | Обеспечивает одинаковую визуальную глубину для всех графических элементов. |
| **Разные цвета тени** | Использовать `shape.ShadowFormat.Color = Color.FromArgb(255, 100, 100);` для красноватого оттенка. | Позволяет поддерживать фирменный стиль или тематическую согласованность. |
| **Не нужна тень для конкретной фигуры** | Пропустить фигуру, проверив `shape.Name` или `shape.ShapeType`. | Предотвращает нежелательные эффекты на логотипах или иконках. |
| **Более высокая прозрачность** | Установить `Transparency = 0.7` для почти невидимой тени. | Полезно для тонких фоновых элементов. |
| **Производительность на больших документах** | Загружать документ с `LoadOptions`, которые пропускают ненужные шрифты. | Снижает потребление памяти при обработке множества файлов. |

## Советы и приёмы (Pro Tips)

* **Pro tip:** Если нужен *дроп‑шадоу*, похожий на Photoshop, увеличьте `BlurRadius` до 10‑12 и задайте `Transparency` = 0.2 для более чёткого вида.  
* **Обратите внимание:** Фигуры могут быть *inline* или *floating*. Inline‑фигуры наследуют форматирование абзаца, и их тень может отображаться иначе. Используйте `shape.IsInline`, чтобы решить, нужно ли сначала преобразовать её в плавающую.  
* **Переиспользуемый метод:** Вынесите логику тени в вспомогательный метод:

```csharp
static void ApplyShadow(Shape s, int offset = 4, double transparency = 0.3,
                        Color? color = null, int blur = 5)
{
    s.ShadowFormat.Visible = true;
    s.ShadowFormat.OffsetX = offset;
    s.ShadowFormat.OffsetY = offset;
    s.ShadowFormat.Transparency = transparency;
    s.ShadowFormat.Color = color ?? Color.Gray;
    s.ShadowFormat.BlurRadius = blur;
}
```

Теперь можно вызывать `ApplyShadow(shape);` где угодно.

## Заключение

Мы только что рассмотрели **как добавить тень** к фигуре Word с помощью C#. Шаги показали, как **добавить тень к фигуре**, **изменить цвет тени**, **регулировать прозрачность тени** и, наконец, **сохранить изменённый документ**. С этими знаниями вы сможете обогатить любой автоматизированный отчёт, маркетинговую брошюру или внутреннюю памятку профессиональным визуальным акцентом.

Что дальше? Попробуйте комбинировать это с другими функциями форматирования — например, градиентными заливками или 3‑D‑эффектами — чтобы создавать действительно привлекающие внимание документы. Или изучайте API Aspose.Words для работы с таблицами, диаграммами и слиянием писем, чтобы построить сквозные конвейеры создания документов.

Есть вопрос о конкретном типе фигуры или нужно применять тени условно? Оставьте комментарий ниже, и давайте продолжать обсуждение. Счастливого кодинга!

## Что стоит изучить дальше?

Следующие руководства охватывают тесно связанные темы, расширяющие техники, продемонстрированные в этом руководстве. Каждый ресурс содержит полностью рабочие примеры кода с пошаговыми объяснениями, чтобы помочь вам освоить дополнительные возможности API и исследовать альтернативные подходы в собственных проектах.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Add Text Watermark in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}