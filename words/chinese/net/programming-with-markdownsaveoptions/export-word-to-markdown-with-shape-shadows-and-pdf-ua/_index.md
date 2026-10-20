---
category: general
date: 2026-03-28
description: 学习如何使用 Aspose.Words 在 C# 中将 Word 导出为 Markdown、添加形状阴影以及保存 PDF/UA——一步步指南。
draft: false
keywords:
- export word to markdown
- add shape shadow
- save pdf ua
- Aspose.Words markdown
- C# document conversion
language: zh
og_description: 将 Word 导出为 markdown，添加形状阴影，并使用 Aspose.Words 在 C# 中保存 PDF/UA。完整教程，附代码和技巧。
og_title: 将 Word 导出为 Markdown – 添加形状阴影并保存 PDF/UA
tags:
- Aspose.Words
- C#
- Markdown
- PDF/UA
title: 导出 Word 为 Markdown，包含形状阴影和 PDF/UA
url: /zh/net/programming-with-markdownsaveoptions/export-word-to-markdown-with-shape-shadows-and-pdf-ua/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 将 Word 导出为 Markdown 并保留形状阴影及 PDF/UA

是否曾需要 **将 Word 导出为 markdown**，同时保留那些精美的形状阴影，并且仍然符合 PDF/UA 标准？你并不孤单。许多开发者在尝试在保持视觉保真度的同时切换格式时会遇到阻碍，尤其是当可访问性（PDF/UA）是必需时。

在本指南中，我们将通过一个完整、可运行的示例，演示如何 **将 Word 导出为 markdown**、**为绘图添加形状阴影**，以及最终 **以浮动形状强制内联的方式保存 PDF/UA**。我们将使用 Aspose.Words for .NET，这是一款用于稳健文档转换的首选库。无需外部脚本，也不需要手写解析器——只需一段干净的 C# 代码，即可直接放入控制台应用程序中使用。

> **专业提示：** 如果尚未安装 Aspose.Words，请获取最新的 NuGet 包（`Install-Package Aspose.Words`）——它兼容 .NET 6+、.NET Framework 4.8，甚至 .NET Core。

## 所需环境

- **Visual Studio 2022**（或任何支持 .NET 6+ 的 IDE）
- **Aspose.Words for .NET**（NuGet 版本 23.8 或更高）
- 一个包含至少一个形状（例如矩形）的示例 `input.docx`
- 基础的 C# 知识——我们会保持语法简洁

准备好这些前置条件后，下面开始动手。

![Diagram showing export word to markdown flow](export_word_to_markdown_diagram.png){alt="export word to markdown example"}

## 步骤 1：以恢复模式加载 Word 文档  

在对文档进行任何修改之前，需要先将其加载到内存中。使用 **RecoveryMode.Recover** 可以捕获字体替换警告，这在源文件使用了本机未安装的字体时非常有用。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Saving;

// 1️⃣ Load the document while collecting warnings
var loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Recover,
    WarningCallback = new WarningInfoCollection()
};

Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*为什么使用 RecoveryMode？*  
如果原始文件引用了缺失的字体，Aspose 会进行替换并抛出警告。通过捕获这些警告，我们可以稍后记录它们——这对调试和合规报告都很有帮助。

## 步骤 2：为形状添加阴影  

文档已加载后，让我们增强一下形状的外观。我们将获取第一个 `Shape` 节点并启用细微的投影阴影。

```csharp
// 2️⃣ Find the first shape and enable its shadow
Shape shape = (Shape)doc.GetChildNodes(NodeType.Shape, true)[0];
shape.ShadowFormat.Visible = true;
shape.ShadowFormat.BlurRadius = 4;   // soft edges
shape.ShadowFormat.Distance = 2;    // how far the shadow is from the shape
shape.ShadowFormat.Angle = 30;      // direction of the light source
```

*为什么要调整阴影？*  
阴影可以增加层次感，使形状在 Word 和导出的 markdown 图像（如果后续将形状转换为图像）中更突出。这也是快速验证视觉属性是否能够在转换管道中保留下来的简便方式。

## 步骤 3：将文档导出为 Markdown（含 LaTeX 数学）  

Aspose.Words 能将 Word 文件转换为干净的 markdown。这里我们还指定将所有 OfficeMath 公式导出为 LaTeX，这是科学文档的事实标准。

```csharp
// 3️⃣ Configure markdown export options
var markdownOptions = new MarkdownSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,
    // Store all extracted images in a dedicated folder
    ResourceSavingCallback = (s, e) =>
    {
        string assetsFolder = "YOUR_DIRECTORY/assets";
        Directory.CreateDirectory(assetsFolder);
        e.FileName = Path.Combine(assetsFolder, e.FileName);
    }
};

// Save as markdown
doc.Save("YOUR_DIRECTORY/output.md", markdownOptions);
```

*你将看到的结果：*  
- 一个 `output.md` 文件，使用标准 markdown 语法。  
- 所有嵌入的图像（包括刚才添加阴影的形状）保存在 `assets/` 目录下。  
- 任何公式都会以 `$…$` LaTeX 块的形式出现，可由 MathJax 或 KaTeX 渲染。

## 步骤 4：将同一文档保存为 PDF/UA  

PDF/UA（PDF/Universal Accessibility）确保 PDF 符合 ISO 14289‑1 标准。我们还会强制将浮动形状保存为内联标签，这有助于简化可访问性标记。

```csharp
// 4️⃣ Set up PDF/UA compliance and inline floating shapes
var pdfOptions = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfUAX2,
    ExportFloatingShapesAsInlineTag = true
};

// Save the PDF/UA file
doc.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*为什么选择 PDF/UA？*  
如果你的受众包括使用屏幕阅读器的用户，或需要满足法律可访问性标准，PDF/UA 是正确的选择。`ExportFloatingShapesAsInlineTag` 标志可防止浮动对象破坏逻辑阅读顺序。

## 步骤 5：检查字体替换警告  

完成转换后，最好把在 **步骤 1** 中捕获的字体相关警告展示出来。

```csharp
// 5️⃣ List font‑substitution warnings (if any)
var warnings = (WarningInfoCollection)loadOptions.WarningCallback;
foreach (var warning in warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"⚠️ {warning.Description}");
}
```

如果看到类似 *“Font 'Calibri' was substituted with 'Arial'”* 的信息，你就能明确哪些字体缺失，并决定是嵌入替代字体还是随应用程序一起分发缺失的字体。

## 完整工作示例  

将以下完整程序复制粘贴到新的控制台项目中即可运行：

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load with recovery mode and capture warnings
        var loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.Recover,
            WarningCallback = new WarningInfoCollection()
        };
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Add a shadow to the first shape
        Shape shape = (Shape)doc.GetChildNodes(NodeType.Shape, true)[0];
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.BlurRadius = 4;
        shape.ShadowFormat.Distance = 2;
        shape.ShadowFormat.Angle = 30;

        // Export to Markdown with LaTeX math and custom assets folder
        var markdownOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            ResourceSavingCallback = (s, e) =>
            {
                string assetsFolder = "YOUR_DIRECTORY/assets";
                Directory.CreateDirectory(assetsFolder);
                e.FileName = Path.Combine(assetsFolder, e.FileName);
            }
        };
        doc.Save("YOUR_DIRECTORY/output.md", markdownOptions);

        // Save as PDF/UA, forcing floating shapes inline
        var pdfOptions = new PdfSaveOptions
        {
            Compliance = PdfCompliance.PdfUAX2,
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // Print any font‑substitution warnings
        var warnings = (WarningInfoCollection)loadOptions.WarningCallback;
        foreach (var warning in warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ {warning.Description}");
        }
    }
}
```

### 预期结果  

- `output.md` 包含干净的 markdown、LaTeX 编码的公式，以及类似 `![Shape](assets/shape0.png)` 的图片链接。  
- `output.pdf` 为符合 PDF/UA 的文件，能够通过 Adobe Acrobat 可访问性检查。  
- 控制台输出列出所有字体替换警告，帮助你跟踪缺失的字体。

## 常见问题与边缘情况  

**如果文档中有多个形状怎么办？**  
遍历 `doc.GetChildNodes(NodeType.Shape, true)`，对每个元素应用阴影设置。  

**可以更改阴影颜色吗？**  
可以——在保存前设置 `shape.ShadowFormat.Color = Color.Gray;`。  

**在 Web 部署时需要调整 assets 文件夹路径吗？**  
必须的。使用相对路径或在 `ResourceSavingCallback` 中配置 CDN URL，以高效提供图像。  

**Markdown 导出会丢失 Word 专有的功能吗？**  
像修订、批注或复杂的 SmartArt 等特性在 markdown 中不会被表示。如果需要这些功能，建议保留 PDF/UA 版本作为备份。

## 结论  

你已经学会了如何使用 Aspose.Words 在 C# 中 **将 Word 导出为 markdown**、**为形状添加阴影**，以及 **保存 PDF/UA**。完整代码示例展示了一个面向生产的工作流，能够处理字体警告、资源管理和可访问性合规——全部集中在一段易读的脚本中。

接下来可以尝试更改阴影参数，实验不同的 `MarkdownSaveOptions`（例如 `ExportImagesAsBase64`），或将此管道集成到 ASP.NET Core API 中，实现对用户上传的 Word 文件的即时转换。如果你对其他输出格式感兴趣，欢迎查看 Aspose 的 **HTML**、**EPUB** 或 **TIFF** 导出选项——它们的使用模式大同小异。

祝编码愉快，愿你的文档始终如你所愿完美呈现！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}