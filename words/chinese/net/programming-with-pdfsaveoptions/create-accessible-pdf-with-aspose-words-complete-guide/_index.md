---
category: general
date: 2026-06-08
description: 使用 Aspose.Words 在 C# 中创建可访问的 PDF。了解如何使 PDF 可访问，并使用适当的合规设置导出可访问的 PDF。
draft: false
keywords:
- create accessible pdf
- make pdf accessible
- export accessible pdf
- configure pdf accessibility
language: zh
og_description: 快速在 C# 中创建可访问的 PDF。本指南展示了如何使 PDF 可访问、导出可访问的 PDF，以及正确配置 PDF 可访问性。
og_title: 使用 Aspose.Words 创建可访问的 PDF – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Create accessible PDF using Aspose.Words in C#. Learn how to make PDF
    accessible and export accessible PDF with proper compliance settings.
  headline: Create Accessible PDF with Aspose.Words – Complete Guide
  type: TechArticle
- description: Create accessible PDF using Aspose.Words in C#. Learn how to make PDF
    accessible and export accessible PDF with proper compliance settings.
  name: Create Accessible PDF with Aspose.Words – Complete Guide
  steps:
  - name: '**Tagging** – Every paragraph, heading, and table receives a PDF tag (`<P>`,
      `<H1>`, `<Table>`).'
    text: '**Tagging** – Every paragraph, heading, and table receives a PDF tag (`<P>`,
      `<H1>`, `<Table>`).'
  - name: '**Language Declaration** – The document’s default language is set to `en-US`
      unless you override it.'
    text: '**Language Declaration** – The document’s default language is set to `en-US`
      unless you override it.'
  - name: '**Reading Order** – Content is ordered logically, matching the visual flow.'
    text: '**Reading Order** – Content is ordered logically, matching the visual flow.'
  - name: '**Alternative Text** – Images without explicit alt text are marked as decorative,
      preventing screen readers from announcing meaningless blobs.'
    text: '**Alternative Text** – Images without explicit alt text are marked as decorative,
      preventing screen readers from announcing meaningless blobs.'
  - name: Choose **File → Properties → Description** – you should see the title you
      set.
    text: Choose **File → Properties → Description** – you should see the title you
      set.
  - name: Go to **View → Show/Hide → Navigation Panes → Tags** – the tags tree should
      list `Document → Part → Art → Fig` etc., mirroring our Word structure.
    text: Go to **View → Show/Hide → Navigation Panes → Tags** – the tags tree should
      list `Document → Part → Art → Fig` etc., mirroring our Word structure.
  - name: Run **Tools → Accessibility → Full Check** – the report should return *No
      errors* for PDF/UA compliance.
    text: Run **Tools → Accessibility → Full Check** – the report should return *No
      errors* for PDF/UA compliance.
  type: HowTo
tags:
- PDF
- Accessibility
- C#
- Aspose.Words
title: 使用 Aspose.Words 创建可访问的 PDF – 完整指南
url: /zh/net/programming-with-pdfsaveoptions/create-accessible-pdf-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words 创建可访问 PDF – 完整指南

是否曾需要**创建可访问的 PDF**，但不确定哪些设置真正实现了可访问性？你并不孤单。无论是构建合规性要求高的发票系统，还是只想让每位阅读者获得良好体验，学习**如何使 PDF 可访问**都是值得掌握的技能。

在本教程中，我们将完整演示整个过程——从空的 `Document` 对象到符合 PDF/UA‑2 标准的文件，你可以自豪地发布。没有模糊的引用，只有具体的代码、清晰的解释，以及一些你明天就能实际使用的专业技巧。

## 本指南涵盖内容

- 使用 Aspose.Words 库设置 .NET 项目  
- 构建包含文本、标题和表格的简单文档  
- **Configure PDF accessibility** 通过调整 `PdfSaveOptions`  
- **Export accessible PDF** 使用单个方法调用导出到磁盘  
- 快速验证生成的文件是否符合 PDF/UA‑2 标准  

阅读完本页后，你将拥有一个可运行的控制台应用程序，生成的 **可访问 PDF** 可以在 Adobe Acrobat 中打开并查看可访问性树。无需额外工具——只需我们提供的代码。

### 前提条件

| 需求 | 原因 |
|------|------|
| .NET 6.0 or later | 现代语言特性和更佳性能 |
| Aspose.Words for .NET (NuGet `Aspose.Words`) | 该库可让我们操作 Word 文档并导出为 PDF/UA |
| Basic C# knowledge | 你将逐行跟随代码 |

如果你已经有项目，跳过第一步。否则，继续阅读——设置过程非常简单。

## 步骤 1：设置你的 .NET 项目并添加 Aspose.Words

首先，打开终端（或 PowerShell），运行以下命令：

```bash
dotnet new console -n AccessiblePdfDemo
cd AccessiblePdfDemo
dotnet add package Aspose.Words
```

这会创建一个名为 **AccessiblePdfDemo** 的全新控制台项目，并从 NuGet 拉取最新的 Aspose.Words 包。  
*技巧提示：* 如果需要特定版本，可使用 `--version` 参数；该库对我们将使用的功能保持向后兼容。

## 步骤 2：创建具有有意义结构的简单文档

打开 `Program.cs` 并将其内容替换为以下代码。该代码添加了标题、章节标题、段落和表格——这些元素是辅助技术喜爱导航的对象。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document
        Document doc = new Document();

        // 2️⃣ Add a title (Heading 1) – this becomes a logical bookmark in the PDF
        Paragraph title = doc.FirstSection.Body.AppendParagraph("Quarterly Report");
        title.ParagraphFormat.StyleIdentifier = StyleIdentifier.Title;

        // 3️⃣ Add a heading (Heading 2) – useful for navigation
        Paragraph heading = doc.FirstSection.Body.AppendParagraph("Executive Summary");
        heading.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;

        // 4️⃣ Add a paragraph with some sample text
        doc.FirstSection.Body.AppendParagraph(
            "This report provides an overview of the financial performance for Q2. " +
            "All figures are presented in USD and are rounded to the nearest million."
        );

        // 5️⃣ Insert a simple 2×2 table – tables are automatically tagged for accessibility
        Table table = new Table(doc);
        doc.FirstSection.Body.AppendChild(table);
        // Define table borders (optional, but improves visual clarity)
        table.SetBorder(BorderType.Left, LineStyle.Single, 1.0, System.Drawing.Color.Black, true);
        table.SetBorder(BorderType.Right, LineStyle.Single, 1.0, System.Drawing.Color.Black, true);
        table.SetBorder(BorderType.Top, LineStyle.Single, 1.0, System.Drawing.Color.Black, true);
        table.SetBorder(BorderType.Bottom, LineStyle.Single, 1.0, System.Drawing.Color.Black, true);
        // Populate cells
        for (int i = 0; i < 2; i++)
        {
            Row row = new Row(doc);
            table.AppendChild(row);
            for (int j = 0; j < 2; j++)
            {
                Cell cell = new Cell(doc);
                row.AppendChild(cell);
                cell.AppendParagraph($"R{i + 1}C{j + 1}");
            }
        }

        // 6️⃣ Call the method that configures accessibility and saves the PDF
        SaveAsAccessiblePdf(doc);
    }

    // ------------------------------------------------------------------------
    // Helper method that **configure pdf accessibility** and **export accessible pdf**
    // ------------------------------------------------------------------------
    static void SaveAsAccessiblePdf(Document doc)
    {
        // Create PDF save options and enable PDF/UA‑2 compliance
        PdfSaveOptions pdfOptions = new PdfSaveOptions
        {
            // PDF/UA‑2 is the current ISO standard for accessible PDFs
            Compliance = PdfCompliance.PdfUATwo,

            // Optional: set the document title – appears in PDF metadata
            Title = "Quarterly Report – Accessible PDF"
        };

        // Save the document to the output folder
        string outputPath = "AccessibleReport.pdf";
        doc.Save(outputPath, pdfOptions);
        Console.WriteLine($"✅ Accessible PDF saved to: {outputPath}");
    }
}
```

**为什么这很重要：**  
- 使用 **样式**（`Title`, `Heading2`）会自动映射为 PDF 标签，辅助技术将其读取为标题。  
- `Table` 类被识别为结构化表格，而非仅仅是图形。  
- `PdfSaveOptions.Compliance = PdfCompliance.PdfUATwo` 这一行是 **configure pdf accessibility** 的 **核心**——它指示 Aspose 嵌入 PDF/UA‑2 规范所需的标签、语言属性和逻辑结构。

## 步骤 3：**使 PDF 可访问** – 理解 PDF/UA‑2 合规性

PDF/UA（通用可访问性）是 ISO 14289‑1 标准。当你设置 `Compliance = PdfCompliance.PdfUATwo` 时，Aspose 在内部会执行多项操作：

1. **标记** – 每个段落、标题和表格都会获得 PDF 标签（`<P>`, `<H1>`, `<Table>`）。  
2. **语言声明** – 文档的默认语言被设为 `en-US`，除非你手动覆盖。  
3. **阅读顺序** – 内容按逻辑顺序排列，匹配视觉流。  
4. **替代文本** – 没有显式 alt 文本的图像会被标记为装饰性，防止屏幕阅读器朗读无意义的内容。  

如果需要为图像提供自定义 alt 文本，可以这样做：

```csharp
// Example: Adding an image with alt text
Shape picture = new Shape(doc, ShapeType.Image);
picture.ImageData.SetImage("logo.png");
picture.Title = "Company Logo"; // This becomes the alt text in the PDF
doc.FirstSection.Body.FirstParagraph.AppendChild(picture);
```

**边缘情况提示：** 如果嵌入视频或交互式表单，需要手动添加额外的标签；PDF/UA‑2 并不会自动处理这些。

## 步骤 4：**导出可访问 PDF** – 正确保存文件

`doc.Save` 在辅助方法中的调用以一行代码完成 **export accessible PDF**。不过，你可能想微调以下几个细节：

| 设置 | 作用 | 何时调整 |
|------|------|----------|
| `PdfSaveOptions.Title` | 设置 PDF 文档标题元数据（在阅读器的“属性”中可见） | 使用与文档目的相符的描述性标题 |
| `PdfSaveOptions.SaveFormat` | 通常从文件扩展名推断，但你可以强制为 `SaveFormat.Pdf` | 当动态构建文件名时很有帮助 |
| `PdfSaveOptions.OutputFileName` | 允许为 PDF/UA 逻辑结构嵌入自定义名称 | 很少需要，但在大批量导出时可能有帮助 |

如果需要在循环中生成多个 PDF，只需复用同一个 `PdfSaveOptions` 实例——不会产生性能惩罚。

## 步骤 5：验证 PDF 是否真正可访问（可选但推荐）

运行控制台应用后，在 **Adobe Acrobat Pro** 中打开 `AccessibleReport.pdf`：

1. 选择 **文件 → 属性 → 描述** —— 应看到你设置的标题。  
2. 前往 **视图 → 显示/隐藏 → 导航窗格 → 标签** —— 标签树应列出 `Document → Part → Art → Fig` 等，映射我们的 Word 结构。  
3. 运行 **工具 → 可访问性 → 完整检查** —— 报告应返回 *No errors*，表示符合 PDF/UA 标准。

如果检查标记缺少 alt 文本，请返回代码并为相应的 `Shape` 对象添加 `Title` 或 `AlternativeText`。

## 常见问题 &

## 接下来应该学习什么？

以下教程涵盖与本指南紧密相关的主题，基于本指南展示的技术进行扩展。每个资源都包含完整的可运行代码示例和逐步解释，帮助你掌握更多 API 功能并在自己的项目中探索替代实现方案。

- [创建可访问 PDF – PDF/UA 合规性逐步指南](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-step-by-step-guide-for-pdf-ua-complian/)
- [从 Word 创建可访问 PDF – 完整指南](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)
- [使用 C# 从 Word 创建可访问 PDF – 逐步指南](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-with-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}