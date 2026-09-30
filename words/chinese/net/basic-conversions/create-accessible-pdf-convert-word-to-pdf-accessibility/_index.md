---
category: general
date: 2026-02-10
description: 在 C# 中从 Word 文档创建可访问的 PDF。了解如何将 Word 转换为 PDF、将 docx 导出为 PDF，以及使用 Aspose.Words
  为 PDF 添加可访问性。
draft: false
keywords:
- create accessible pdf
- convert word to pdf
- export docx as pdf
- save document as pdf
- add accessibility to pdf
language: zh
og_description: 使用 C# 从 Word 文件创建可访问的 PDF。本指南展示如何将 Word 转换为 PDF，导出 docx 为 PDF，并为 PDF
  添加可访问性。
og_title: 创建无障碍 PDF – 将 Word 转换为 PDF 可访问性
tags:
- Aspose.Words
- PDF/UA
- C#
- Document Conversion
title: 创建可访问的PDF – 将Word转换为PDF可访问性
url: /zh/net/basic-conversions/create-accessible-pdf-convert-word-to-pdf-accessibility/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建可访问的 PDF – 将 Word 转换为 PDF 可访问性

是否曾需要 **创建可访问的 PDF**，但不确定哪些设置真正起作用？你并不孤单。许多开发者面对 `docx` 时会疑惑为何生成的 PDF 未通过屏幕阅读器检查。好消息是，只需几行 C# 代码并使用正确的保存选项，就可以 **将 Word 转换为 PDF**、**导出 docx 为 PDF**，并 **为 PDF 添加可访问性**，整个过程流畅无阻。

在本教程中，我们将一步步演示完整流程，解释每个设置为何重要，并提供可直接运行的代码示例。完成后，你将拥有符合 PDF/UA‑2（通用可访问性标准）的 PDF，并了解如何在自己的项目中进行调整。

## 你需要准备的东西

- **Aspose.Words for .NET**（最新版本，例如 24.9）。这是商业库，但提供免费试用，足以用于测试。
- .NET 开发环境（Visual Studio、Rider，或 `dotnet` CLI 都可以）。
- 一个简单的 Word 文档（`input.docx`），你希望使其可访问。
- 可选：PDF/UA 验证工具（如 PAC 2021），用于二次检查合规性。

就这些——无需额外的 NuGet 包，无需繁琐的 XML，仅需纯 C#。

![创建可访问的 pdf 示例](image.png "创建可访问的 pdf 示例")

## 步骤 1：加载 Word 文档

首先加载源 `.docx`。Aspose.Words 抽象了文件格式，你无需担心 Office interop 或 COM。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source Word document
Document doc = new Document(@"C:\MyFiles\input.docx");
```

**为什么重要：** 加载文档会在内存中创建一个 DOM，供后续保存前进行操作。如果文件包含标题、表格或图片，Aspose.Words 会保留它们的结构，这对后续的可访问性至关重要。

> **小技巧：** 如果文档位于流中（例如通过 API 上传），可以直接将流传给 `Document` 构造函数——无需先写入磁盘。

## 步骤 2：配置 PDF 保存选项以 **创建可访问的 PDF**

现在告诉 Aspose 我们希望如何生成 PDF。关键属性是 `PdfCompliance`，我们将其设为 `PdfCompliance.PdfUAXmpa2`。此标志指示库生成符合 PDF/UA‑2 标准的文件，自动将水平线（`<hr>`）等元素视为 *artifact*（装饰性元素），而非内容——这正是可访问性检查器关注的点。

```csharp
// Configure PDF save options for PDF/UA‑2 compliance
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions
{
    // This ensures the output meets PDF/UA‑2 (PDF/UA‑2) standards
    PdfCompliance = PdfCompliance.PdfUAXmpa2,

    // Optional: embed the source document's fonts for better rendering
    EmbedFullFonts = true,

    // Optional: preserve the original document's structure tree
    PreserveFormFields = true
};
```

**为什么重要：**  
- **PDF/UA‑2 合规** 确保辅助技术能够正确解释标题、表格和装饰性元素。  
- **嵌入字体** 防止在未安装原始字体的设备上出现布局错位。  
- **保留表单字段** 使交互元素对屏幕阅读器可用。

如果只需要普通的、非可访问 PDF，可以去掉 `PdfCompliance` 那一行——但随之也会失去我们追求的可访问性优势。

## 步骤 3：将文档保存为可访问的 PDF

最后，将文件写入磁盘（或流）。相同的 `Save` 方法适用于 Aspose 支持的所有格式，因此本质上是一次调用 **导出 docx 为 PDF**。

```csharp
// Save the document as an accessible PDF
string outputPath = @"C:\MyFiles\Accessible.pdf";
doc.Save(outputPath, pdfSaveOptions);
```

运行此行代码后，`Accessible.pdf` 应能在任意 PDF 查看器中打开，并通过基本的 PDF/UA 检查。你可以使用 **PAC 2021** 或 **PDF Accessibility Checker (PAC)** 等工具进行验证。

**预期结果：**  
- PDF 包含与 Word 标题相匹配的逻辑阅读顺序。  
- 水平线等装饰元素被标记为 *artifact*，而非内容。  
- 所有文字可搜索、可选中，图片保留其 alt 文本（如果你在 Word 中已设置）。

## 验证可访问性（可选但推荐）

运行验证工具是快速确认你已 **为 PDF 添加可访问性** 的方法。

```csharp
using System.Diagnostics;

// Assuming you have PAC installed and added to PATH
Process.Start("pac.exe", $"\"{outputPath}\"");
```

如果工具报告零错误，说明一切顺利。若出现缺少 alt 文本的警告，请返回原始 Word 文档为图片添加描述——Aspose 会自动携带这些信息。

## 常见变体与边缘情况

| 场景 | 需要调整的内容 | 原因 |
|----------|----------------|-----|
| **大型文档（100+ 页）** | 在 `PdfSaveOptions` 中将 `MemoryUsage` 设置为 `MemoryUsageMode.LowMemory` | 防止 32 位进程出现内存不足异常 |
| **自定义 PDF 标签** | 使用 `doc.CustomDocumentProperties` 或 `doc.Markup` 添加 `StructureTreeRoot` 条目 | 为可访问性树提供细粒度控制 |
| **受密码保护的 PDF** | 在 `pdfSaveOptions.EncryptionDetails` 中设置用户密码 | 在保持可访问性的同时确保 PDF 安全 |
| **图片缺少 alt 文本** | 预处理 Word 文件：`foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true)) { if (string.IsNullOrEmpty(shape.AlternativeText)) shape.AlternativeText = "Descriptive alt text"; }` | 确保屏幕阅读器有可朗读的内容 |

这些调整让你能够 **将文档保存为 PDF**，同时满足项目约束而不牺牲可访问性。

## 完整可运行示例

下面是完整的、可直接运行的程序。将其粘贴到控制台应用中，修改路径后按 **F5**。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

namespace AccessiblePdfDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source Word document
            string inputPath = @"C:\MyFiles\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Configure PDF save options for PDF/UA‑2 compliance
            PdfSaveOptions pdfSaveOptions = new PdfSaveOptions
            {
                PdfCompliance = PdfCompliance.PdfUAXmpa2,
                EmbedFullFonts = true,
                PreserveFormFields = true
            };

            // Optional: handle large files gracefully
            // pdfSaveOptions.MemoryUsage = MemoryUsageMode.LowMemory;

            // 3️⃣ Save the document as an accessible PDF
            string outputPath = @"C:\MyFiles\Accessible.pdf";
            doc.Save(outputPath, pdfSaveOptions);

            Console.WriteLine($"✅ Accessible PDF created at: {outputPath}");
        }
    }
}
```

运行后，用 Adobe Reader 打开 `Accessible.pdf`。选择 **文件 → 属性 → 描述**，你会在 “PDF/A 合规性” 下看到 “PDF/UA”。这正是你已经成功 **创建可访问的 pdf** 的视觉提示。

## 常见问题

**问：这在 .NET Core 上能工作吗？**  
答：完全可以。Aspose.Words 支持 .NET Standard 2.0+，相同代码可在 .NET 5/6/7 上直接运行，无需修改。

**问：如果需要批量转换大量文件怎么办？**  
答：将逻辑封装在一个循环或并行任务中即可。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}