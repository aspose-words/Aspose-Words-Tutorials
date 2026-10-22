---
title: 使用 Aspose.Words for .NET 在 Word 文档中创建旋转文本表格
weight: 110
limit:
description: 学习使用 Aspose.Words for .NET 构建具有固定列宽、旋转文本、精确行高和已填充单元格的 Word 表格。
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: 学习使用 Aspose.Words for .NET 构建具有固定列宽、旋转文本、精确行高和已填充单元格的 Word 表格。
  headline: 使用 Aspose.Words for .NET 在 Word 文档中创建旋转文本表格
  type: TechArticle
- description: 学习使用 Aspose.Words for .NET 构建具有固定列宽、旋转文本、精确行高和已填充单元格的 Word 表格。
  name: 使用 Aspose.Words for .NET 在 Word 文档中创建旋转文本表格
  steps:
  - name: 实例化一个新的 Document 和一个用于构建表格的 DocumentBuilder。
    text: 实例化一个新的 Document 和一个用于构建表格的 DocumentBuilder。
  - name: 开始一个新表格，插入第一个单元格，并固定列宽，使其不自动调整。
    text: 开始一个新表格，插入第一个单元格，并固定列宽，使其不自动调整。
  - name: 在当前单元格中垂直居中内容，并写入第一行第一个单元格的文本。
    text: 在当前单元格中垂直居中内容，并写入第一行第一个单元格的文本。
  - name: 插入第一行的第二个单元格并写入其文本。
    text: 插入第一行的第二个单元格并写入其文本。
  - name: 关闭第一行，完成其布局。
    text: 关闭第一行，完成其布局。
  - name: 开始第二行的第一个单元格，将行高设置为恰好 100 磅，向上旋转文本，并写入单元格文本。
    text: 开始第二行的第一个单元格，将行高设置为恰好 100 磅，向上旋转文本，并写入单元格文本。
  - name: 插入第二行的第二个单元格，将其文本向下旋转，并写入单元格文本。
    text: 插入第二行的第二个单元格，将其文本向下旋转，并写入单元格文本。
  - name: 关闭第二行，完成表格的第二行。
    text: 关闭第二行，完成表格的第二行。
  - name: 结束表格构建，固定表格结构。
    text: 结束表格构建，固定表格结构。
  - name: 将完成的文档保存为 .docx 文件。
    text: 将完成的文档保存为 .docx 文件。
  type: HowTo
- questions:
  - answer: 固定列宽后，在插入下一个单元格之前使用 `builder.CellFormat.Width = <valueInPoints>;` 为每个单元格分配宽度；表格将保持这些精确宽度。
    question: 在调用 `table.AutoFit(AutoFitBehavior.FixedColumnWidths)` 后，如何设置特定的列宽？
  - answer: '`builder.CellFormat.VerticalAlignment` 是单元格级别的设置，因此需要在写入第二行单元格内容之前再次为这些单元格设置（例如
      `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`）。'
    question: 为什么垂直对齐仅影响第一行，而不影响第二行？
  - answer: 可以——在每次调用 `builder.EndRow();` 之前设置 `builder.RowFormat.Height` 并将 `builder.RowFormat.HeightRule
      = HeightRule.Exactly`；下一行可以使用不同的高度值。
    question: 我可以为每一行设置不同的精确高度吗？如果可以，怎么做？
  - answer: 在写入下一个单元格之前，将 `builder.CellFormat.Orientation = TextOrientation.Horizontal;`
      赋值，以重置为水平方向。
    question: 在使用 `TextOrientation.Upward` 或 `Downward` 后，如何将文本方向恢复为默认？
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: 使用 Aspose.Words 在 Word 中创建旋转文本表格
og_description: 逐步代码示例，构建具有固定宽度、垂直旋转文本和精确行高的表格。
og_image_alt: 截图显示使用 Aspose.Words for .NET 创建的 Word 文档，其中表格具有固定列宽、单元格内旋转文本以及已定义的行高。
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 文档中创建旋转文本表格
本教程展示了如何生成 Word 文档并添加一个表格，该表格的列宽固定、行高精确、单元格文本垂直旋转。您将学习设置垂直对齐、应用文本方向、为每个单元格填充内容，最后保存文档——全部使用 Aspose.Words for .NET。

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

**Q: 在调用 `table.AutoFit(AutoFitBehavior.FixedColumnWidths)` 后，如何设置特定的列宽？**  
A: 固定列宽后，在插入下一个单元格之前使用 `builder.CellFormat.Width = <valueInPoints>;` 为每个单元格分配宽度；表格将保持这些精确宽度。

**Q: 为什么垂直对齐仅影响第一行，而不影响第二行？**  
A: `builder.CellFormat.VerticalAlignment` 是单元格级别的设置，因此需要在写入第二行单元格内容之前再次为这些单元格设置（例如 `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`）。

**Q: 我可以为每一行设置不同的精确高度吗？如果可以，怎么做？**  
A: 可以——在每次调用 `builder.EndRow();` 之前设置 `builder.RowFormat.Height` 并将 `builder.RowFormat.HeightRule = HeightRule.Exactly`；下一行可以使用不同的高度值。

**Q: 在使用 `TextOrientation.Upward` 或 `Downward` 后，如何将文本方向恢复为默认？**  
A: 在写入下一个单元格之前，将 `builder.CellFormat.Orientation = TextOrientation.Horizontal;` 赋值，以重置为水平方向。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}