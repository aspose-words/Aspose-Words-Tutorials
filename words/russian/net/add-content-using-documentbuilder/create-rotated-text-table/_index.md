---
title: Создайте таблицу с вращённым текстом в документе Word с помощью Aspose.Words for .NET
weight: 110
limit:
description: Научитесь создавать таблицу Word с фиксированными ширинами столбцов, вращённым текстом, точными высотами строк и заполненными ячейками, используя Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: Научитесь создавать таблицу Word с фиксированными ширинами столбцов,
    вращённым текстом, точными высотами строк и заполненными ячейками, используя Aspose.Words
    for .NET.
  headline: Создайте таблицу с вращённым текстом в документе Word с помощью Aspose.Words
    for .NET
  type: TechArticle
- description: Научитесь создавать таблицу Word с фиксированными ширинами столбцов,
    вращённым текстом, точными высотами строк и заполненными ячейками, используя Aspose.Words
    for .NET.
  name: Создайте таблицу с вращённым текстом в документе Word с помощью Aspose.Words
    for .NET
  steps:
  - name: Создайте новый объект Document и DocumentBuilder, которые будут использоваться
      для построения таблицы.
    text: Создайте новый объект Document и DocumentBuilder, которые будут использоваться
      для построения таблицы.
  - name: Начните новую таблицу, вставьте первую ячейку и зафиксируйте ширины столбцов,
      чтобы они не автонастраивались.
    text: Начните новую таблицу, вставьте первую ячейку и зафиксируйте ширины столбцов,
      чтобы они не автонастраивались.
  - name: Выравнивайте содержимое по центру вертикально в текущей ячейке и запишите
      текст первой ячейки первой строки.
    text: Выравнивайте содержимое по центру вертикально в текущей ячейке и запишите
      текст первой ячейки первой строки.
  - name: Вставьте вторую ячейку первой строки и запишите её текст.
    text: Вставьте вторую ячейку первой строки и запишите её текст.
  - name: Закройте первую строку, завершив её макет.
    text: Закройте первую строку, завершив её макет.
  - name: Начните первую ячейку второй строки, установите высоту строки ровно 100
      пунктов, поверните текст вверх и запишите текст ячейки.
    text: Начните первую ячейку второй строки, установите высоту строки ровно 100
      пунктов, поверните текст вверх и запишите текст ячейки.
  - name: Вставьте вторую ячейку второй строки, поверните её текст вниз и запишите
      текст ячейки.
    text: Вставьте вторую ячейку второй строки, поверните её текст вниз и запишите
      текст ячейки.
  - name: Закройте вторую строку, завершив вторую линию таблицы.
    text: Закройте вторую строку, завершив вторую линию таблицы.
  - name: Завершите построение таблицы, закрепив её структуру.
    text: Завершите построение таблицы, закрепив её структуру.
  - name: Сохраните готовый документ в файл формата .docx.
    text: Сохраните готовый документ в файл формата .docx.
  type: HowTo
- questions:
  - answer: После фиксации ширин столбцов задайте ширину каждой ячейки с помощью `builder.CellFormat.Width
      = <valueInPoints>;` перед вставкой следующей ячейки; таблица сохранит эти точные
      ширины.
    question: Как задать конкретные ширины столбцов после вызова `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?
  - answer: '`builder.CellFormat.VerticalAlignment` — это настройка уровня ячейки,
      поэтому её необходимо установить повторно для ячеек второй строки (например,
      `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) перед
      записью их содержимого.'
    question: Почему вертикальное выравнивание влияет только на первую строку, а не
      на вторую?
  - answer: Да — задайте `builder.RowFormat.Height` и `builder.RowFormat.HeightRule
      = HeightRule.Exactly` перед каждым вызовом `builder.EndRow();`; следующая строка
      может иметь другое значение высоты.
    question: Могу ли я задать каждой строке разную точную высоту, и если да, то как?
  - answer: Сбросьте ориентацию, присвоив `builder.CellFormat.Orientation = TextOrientation.Horizontal;`
      перед записью в следующую ячейку.
    question: Как вернуть ориентацию текста к значению по умолчанию после использования
      `TextOrientation.Upward` или `Downward`?
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: Создайте таблицу с вращённым текстом в Word с помощью Aspose.Words
og_description: Пошаговый код для создания таблицы с фиксированной шириной, вертикально вращённым текстом и точными высотами строк.
og_image_alt: Скриншот, показывающий документ Word с таблицей, у которой фиксированные ширины столбцов, вращённый текст в ячейках и заданные высоты строк, созданный с помощью Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Создайте таблицу с вращённым текстом в документе Word с помощью Aspose.Words
В этом руководстве показано, как создать документ Word и добавить таблицу, у которой столбцы имеют фиксированные ширины, строки — точные высоты, а текст в ячейках вращён вертикально. Вы научитесь задавать вертикальное выравнивание, применять ориентацию текста, заполнять каждую ячейку содержимым и в конце сохранять документ — всё с помощью Aspose.Words for .NET.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Как задать конкретные ширины столбцов после вызова `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?**  
A: После фиксации ширин столбцов задайте ширину каждой ячейки с помощью `builder.CellFormat.Width = <valueInPoints>;` перед вставкой следующей ячейки; таблица сохранит эти точные ширины.

**Q: Почему вертикальное выравнивание влияет только на первую строку, а не на вторую?**  
A: `builder.CellFormat.VerticalAlignment` — это настройка уровня ячейки, поэтому её необходимо установить повторно для ячеек второй строки (например, `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) перед записью их содержимого.

**Q: Могу ли я задать каждой строке разную точную высоту, и если да, то как?**  
A: Да — задайте `builder.RowFormat.Height` и `builder.RowFormat.HeightRule = HeightRule.Exactly` перед каждым вызовом `builder.EndRow();`; следующая строка может иметь другое значение высоты.

**Q: Как вернуть ориентацию текста к значению по умолчанию после использования `TextOrientation.Upward` или `Downward`?**  
A: Сбросьте ориентацию, присвоив `builder.CellFormat.Orientation = TextOrientation.Horizontal;` перед записью в следующую ячейку.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}