---
category: general
date: 2026-04-05
description: 学习如何在 C# 中将 DOCX 转换为 Markdown 并从 DOCX 中提取图像。一步步指南，附完整代码和技巧。
draft: false
keywords:
- convert docx to markdown
- extract images from docx
- Aspose.Words markdown conversion
- C# document processing
- image extraction C#
language: zh
og_description: 使用 Aspose.Words 将 DOCX 转换为 Markdown 并提取 DOCX 中的图像。完整的 C# 教程，包含代码、说明和最佳实践技巧。
og_title: 将 DOCX 转换为 Markdown – 在 C# 中从 DOCX 提取图片
tags:
- Aspose.Words
- C#
- Markdown
- DOCX
- Image extraction
title: 将 DOCX 转换为 Markdown – 使用 Aspose.Words 从 DOCX 提取图像
url: /zh/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-extract-images-from-docx-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 将 DOCX 转换为 Markdown – 从 DOCX 中提取图片（C#）

是否曾经**将 DOCX 转换为 Markdown**却苦恼于图片在输出中消失？你并非唯一。很多项目中，Markdown 版非常适合版本控制或静态站点生成器，但图片却被遗漏，使得原本丰富的文档变成了枯燥的文本文件。  

好消息是，只需几行 C# 代码和 Aspose.Words，你就可以**将 DOCX 转换为 Markdown** *并且* **自动从 DOCX 中提取图片**。本指南将完整演示整个过程，解释每一步的意义，并展示如何保持图片文件夹整洁。

## 你将学到

- 如何加载包含图片的 DOCX。
- 如何定义自定义 `IResourceSavingCallback` 来决定每张图片的保存位置。
- 如何配置 `MarkdownSaveOptions`，让生成的 Markdown 正确引用提取出的图片。
- 处理重复图片名称或非 PNG 格式等边缘情况的技巧。
- 一个完整的、可直接复制粘贴运行的代码示例。

### 前置条件

- .NET 6.0 或更高（API 在 .NET Core、.NET Framework 和 .NET 5+ 上均可运行）。
- **Aspose.Words for .NET** 授权（免费试用版可用于测试）。
- 基本的 C# 与 Visual Studio（或你喜欢的 IDE）使用经验。

如果你满足以上条件，下面开始吧。

---

## 第一步：创建项目并安装 Aspose.Words

首先，新建一个控制台应用（或在已有解决方案中集成）。

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

> **小贴士：** 使用最新的 NuGet 版本（截至 2026 年 4 月为 24.12），可获得最新的 Markdown 导出改进。

---

## 第二步：创建回调以将图片保存到指定位置

Aspose.Words 允许在 Markdown 导出过程中拦截每个资源（图片、SVG 等）。实现 `IResourceSavingCallback` 后，你可以：

1. 选择一个与 Markdown 文件同级的文件夹。
2. 生成唯一的文件名（避免覆盖已有图片）。
3. 决定保存格式（这里统一为 PNG 以保持一致性）。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Saves each image extracted from the DOCX into a dedicated folder
/// with a GUID‑based filename. The markdown file will reference the
/// new filename via <c>args.ResourceFileName</c>.
/// </summary>
class ImageResourceSaver : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageResourceSaver(string targetFolder)
    {
        _targetFolder = targetFolder;
        // Ensure the folder exists before we start writing files.
        Directory.CreateDirectory(_targetFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Generate a unique name to avoid collisions.
        string newFileName = $"img_{Guid.NewGuid():N}.png";

        // Full physical path where the image will be written.
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // Tell the markdown exporter what name to use in the .md file.
        args.ResourceFileName = newFileName;

        // Provide a stream that writes to the desired location.
        args.Stream = new FileStream(fullPath, FileMode.Create);
    }
}
```

### 为什么使用基于 GUID 的名称？

如果源 DOCX 中有两张图片的原始名称相同，直接复制粘贴会导致其中一张被覆盖。使用 `Guid.NewGuid()` 能保证唯一性，特别适合在自动化流水线中多次运行转换时使用。

---

## 第三步：加载 DOCX 并配置 Markdown 选项

现在把文档加载到内存，并挂载刚才创建的回调。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------------
        // 1️⃣  Define paths – adjust these to match your environment.
        // --------------------------------------------------------------------
        string sourceDocx = @"C:\Docs\WithImages.docx";
        string outputMarkdown = @"C:\Docs\DocWithImages.md";
        string imagesFolder = @"C:\Docs\MarkdownResources";

        // --------------------------------------------------------------------
        // 2️⃣  Load the Word document.
        // --------------------------------------------------------------------
        Document doc = new Document(sourceDocx);

        // --------------------------------------------------------------------
        // 3️⃣  Configure MarkdownSaveOptions with our custom saver.
        // --------------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This tells Aspose.Words to call ImageResourceSaver for each image.
            ResourceSavingCallback = new ImageResourceSaver(imagesFolder)
        };

        // --------------------------------------------------------------------
        // 4️⃣  Perform the conversion.
        // --------------------------------------------------------------------
        doc.Save(outputMarkdown, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown saved to: {outputMarkdown}");
        Console.WriteLine($"Images saved to:   {imagesFolder}");
    }
}
```

### 代码逐步说明

| 步骤 | 目的 |
|------|------|
| **定义路径** | 让项目更灵活；无需重新编译即可指向任意文件夹。 |
| **加载 DOCX** | `Document` 解析 Word 文件，使所有元素（段落、表格、图片）可访问。 |
| **配置 `MarkdownSaveOptions`** | `ResourceSavingCallback` 是提取图片的钩子。若不设置，Aspose.Words 会将图片嵌入为 base64 字符串或直接丢弃，取决于设置。 |
| **保存** | `doc.Save` 写入 Markdown 文件，并为每张图片触发回调。 |

---

## 第四步：验证输出 – 你应该看到什么？

运行程序后，打开 `DocWithImages.md`。你会看到类似下面的 Markdown 图片链接：

```markdown
![img_1a2b3c4d5e6f7g8h9i0j.png](MarkdownResources/img_1a2b3c4d5e6f7g8h9i0j.png)
```

在 `C:\Docs\MarkdownResources` 中，你会找到一系列以 GUID 命名的 PNG 文件。打开任意一个，它们应与原始 DOCX 中嵌入的图片完全相同。

如果在支持相对路径的查看器中打开（例如 VS Code 预览、GitHub 或静态站点生成器），图片会像在 Word 中一样渲染。

### 常见问题及规避方法

| 症状 | 可能原因 | 解决办法 |
|------|----------|----------|
| 图片显示为失效链接 | `ResourceFileName` 未设置，导致 Markdown 指向了不存在的文件。 | 在回调中确保 `args.ResourceFileName = newFileName;` |
| PNG 文件体积过大 | 原始图片为 JPEG 或 BMP，转换为 PNG 会增大体积。 | 通过 `args.ResourceContentType` 检测原始格式并保留：`args.ResourceFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";` |
| 仍出现重复图片 | 使用了静态文件名而非 GUID。 | 恢复 GUID 逻辑或为每种图片类型添加计数器。 |
| 转换抛出 `FileNotFoundException` | DOCX 路径错误或文件夹缺少读取权限。 | 检查路径并授予相应的文件系统权限。 |

---

## 第五步：高级调优（可选）

### 5.1 保持原始图片格式

如果希望输出图片保留原始扩展名，可修改回调：

```csharp
public void ResourceSaving(ResourceSavingArgs args)
{
    string ext = Path.GetExtension(args.ResourceFileName).ToLowerInvariant();
    // Default to .png if Aspose couldn't determine an extension.
    if (string.IsNullOrEmpty(ext)) ext = ".png";

    string newFileName = $"img_{Guid.NewGuid():N}{ext}";
    string fullPath = Path.Combine(_targetFolder, newFileName);
    args.ResourceFileName = newFileName;
    args.Stream = new FileStream(fullPath, FileMode.Create);
}
```

### 5.2 将图片嵌入为 Base64（当你*不*想要单独文件时）

有时单文件 Markdown 更方便（例如通过邮件发送）。修改选项：

```csharp
mdOptions.ImagesFolder = string.Empty; // disables external folder
mdOptions.ExportImagesAsBase64 = true;
```

但请记住：对大多数静态站点工作流而言，**从 DOCX 中提取图片** 是主要目标，文件夹方式通常更合适。

---

## 完整可运行示例（复制粘贴即可）

下面是一整个文件的完整程序。只需替换为自己的路径后运行。

```csharp
// ---------------------------------------------------------------
// Convert DOCX to Markdown – Extract Images from DOCX
// ---------------------------------------------------------------
// NuGet: Aspose.Words (>= 24.12)
// ---------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class ImageResourceSaver : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageResourceSaver(string targetFolder) => Directory.CreateDirectory(_targetFolder = targetFolder);

    public void ResourceSaving(ResourceSavingArgs args)
    {
        string ext = Path.GetExtension(args.ResourceFileName).ToLowerInvariant();
        if (string.IsNullOrEmpty(ext)) ext = ".png";
        string newFileName = $"img_{Guid.NewGuid():N}{ext}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        args.ResourceFileName = newFileName;
        args.Stream = new FileStream(fullPath, FileMode.Create);
    }
}

class Program
{
    static void Main()
    {
        // 👉 Adjust these paths:
        string sourceDocx = @"C:\Docs\WithImages.docx";
        string outputMd  = @"C:\Docs\DocWithImages.md";
        string imgFolder = @"C:\Docs\MarkdownResources";

        // Load the DOCX.
        Document doc = new Document(sourceDocx);

        // Set up markdown options with our image saver.
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageResourceSaver(imgFolder)
        };

        // Perform conversion.
        doc.Save(outputMd, mdOptions);

        Console.WriteLine("✅ DOCX successfully converted to Markdown.");
        Console.WriteLine($"📄 Markdown: {outputMd}");
        Console.WriteLine($"🖼️ Images folder: {imgFolder}");
    }
}
```

使用 `dotnet run` 执行。当控制台打印出 ✅ 行时，打开 Markdown 文件，你应能看到图片正确渲染。

---

## 结论

现在你拥有一个**完整、可投入生产的解决方案**，使用 Aspose.Words 在 C# 中**将 DOCX 转换为 Markdown 并提取图片**。本文的关键词在整个指南中多次出现，提升了对搜索引擎和 AI 助手的相关性。  

代码一次性完成以下工作：

1. 加载 Word 文档。
2. 通过 `IResourceSavingCallback` 拦截每张图片。
3. 将每张图片保存到可预测的文件夹并使用唯一名称。
4. 生成引用这些图片的 Markdown。

接下来你可以：

- 将

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}