---
category: general
date: 2026-02-18
description: 使用 Aspose.Words 将 Word 转换为 Markdown 并从 docx 中提取图像。学习如何使用完整的 C# 示例从 Word
  生成 Markdown。
draft: false
keywords:
- convert word to markdown
- extract images from docx
- how to extract images
- generate markdown from word
- how to convert docx to markdown
language: zh
og_description: 使用 Aspose.Words 将 Word 转换为 Markdown 并从 docx 中提取图像。本指南逐步演示如何从 Word
  生成 Markdown。
og_title: 将 Word 转换为 Markdown – 在 C# 中提取图像
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: 将 Word 转换为 Markdown – 在 C# 中提取图片
url: /zh/net/programming-with-markdownsaveoptions/convert-word-to-markdown-extract-images-in-c/
---

Also ensure we keep the shortcodes exactly.

Proceed.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Convert Word to Markdown – Extract Images in C#

有没有想过在 **将 Word 转换为 Markdown** 的同时，把 `.docx` 文件里的每张图片都提取出来？你并不是唯一的遇到这种需求的人。很多开发者在需要把最初用 Word 编写的合同、博客文章或技术规范转换成干净的 markdown 时会卡住。好消息是？使用 Aspose.Words for .NET，只需几行代码，你就能得到一个 markdown 文件 *外加* 一个包含原始图片的文件夹。

在本教程中，我们将逐步演示一个完整、可直接运行的 C# 程序，它 **从 Word 生成 markdown**，从 docx 中提取图片，并将所有内容保存到磁盘。完成后，你将清楚地知道如何 **将 docx 转换为 markdown**，如何 **从 docx 中提取图片**，以及如何为自己的项目微调此过程。

## What You’ll Need

- **Aspose.Words for .NET**（v23.10 或更高）。可以使用 `Install-Package Aspose.Words` 获取免费试用的 NuGet 包。
- .NET 6+ SDK（任意近期版本均可）。
- 一个包含至少一张图片的示例 `input.docx`。
- 一个用于存放 markdown 和图片资源的文件夹。

不需要其他第三方库。下面的代码已经包含了所有必需的 `using` 指令，直接复制到控制台应用程序中并按 **F5** 即可运行。

![Convert Word to Markdown example](/images/convert-word-to-markdown.png "convert word to markdown")

*图片说明：将 Word 文件转换为带图片的 Markdown 文件的示意图。*

---

## Step 1: Load the Source Word Document

首先，需要让 Aspose.Words 指向你想要转换的文件。把 `Document` 看作是通往 `.docx` 内部所有内容（文本、表格、图片等）的入口。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 👉 Step 1: Load the Word document that contains images.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document document = new Document(inputPath);
```

> **Why this matters:** 加载文档一次即可保持内存占用低，并让库检查内部包结构，这对后续提取图片至关重要。

---

## Step 2: Tell Aspose.Words How to Save as Markdown

Aspose.Words 附带了 `MarkdownSaveOptions` 类。它让你可以控制从换行符到外部资源（如图片）保存文件夹的所有细节。

```csharp
        // 👉 Step 2: Configure Markdown save options with a resource‑saving callback.
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
        {
            // The callback fires for each external resource (e.g., an image) that needs a file.
            ResourceSavingCallback = new ResourceSavingCallback(args =>
            {
                // 👉 Step 3 inside the callback: decide where and how to store each image.
                string resourceFolder = @"YOUR_DIRECTORY\markdown-resources";
                Directory.CreateDirectory(resourceFolder); // creates if it doesn’t exist

                // Give each image a unique name to avoid collisions.
                string uniqueFileName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";
                args.FileName = Path.Combine(resourceFolder, uniqueFileName);

                // Optional: you could compress PNGs here by manipulating args.Stream.
            })
        };
```

> **Why a callback?** `ResourceSavingCallback` 让你完全掌控每张提取图片的文件名和保存位置。如果没有回调，Aspose 会把所有图片统一放在同一文件夹并使用通用名称，这在大型项目中会非常混乱。

---

## Step 3: Save the Document as Markdown

选项配置好后，保存只需要一行代码。库会完成繁重的工作：转换段落、标题、列表、表格，并且——得益于回调——把每张图片写入你指定的文件夹。

```csharp
        // 👉 Step 4: Save the document as a Markdown file.
        string outputPath = @"YOUR_DIRECTORY\output.md";
        document.Save(outputPath, markdownOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown saved to: {outputPath}");
        Console.WriteLine($"Images extracted to: {Path.GetDirectoryName(outputPath)}\\markdown-resources");
    }
}
```

### Expected Result

- `output.md` 包含 markdown 语法（例如 `![Image](markdown-resources/img_1234.png)`）。
- `markdown-resources` 文件夹保存了原始 Word 文件中的所有图片，且每个文件名都是唯一的。

在任意 markdown 查看器（VS Code、GitHub 或静态站点生成器）中打开 `output.md`，你应该能看到与原始 Word 布局相同的文本和图片，只是以轻量、适合网页的格式呈现。

---

## Step 4: Common Variations & Edge Cases

### 4.1 Handling Existing Resource Folders

如果多次运行转换，可能会留下旧的图片。可以在每次运行前加入一个快速的防护代码来清空文件夹：

```csharp
if (Directory.Exists(resourceFolder))
{
    foreach (var file in Directory.GetFiles(resourceFolder))
        File.Delete(file);
}
else
{
    Directory.CreateDirectory(resourceFolder);
}
```

### 4.2 Changing Image Formats

有时需要将所有图片统一为 JPEG 以便网页优化。可以在回调中重新编码流：

```csharp
using (var img = System.Drawing.Image.FromStream(args.Stream))
{
    var jpegStream = new MemoryStream();
    img.Save(jpegStream, System.Drawing.Imaging.ImageFormat.Jpeg);
    jpegStream.Position = 0;
    args.Stream = jpegStream;
    args.FileName = Path.ChangeExtension(args.FileName, ".jpg");
}
```

> **Pro tip:** `System.Drawing.Common` 适用于 Windows；在 Linux/macOS 上建议使用 `ImageSharp` 以获得跨平台安全性。

### 4.3 Preserving Table Styles

如果你的 Word 文档在表格格式上依赖较多，可以微调 `MarkdownSaveOptions`：

```csharp
markdownOptions.ExportTableColumnWidths = true;   // keeps column widths
markdownOptions.ExportTableBorders = true;       // adds markdown border syntax
```

### 4.4 Using a Different Output Directory

`Save` 方法接受任意绝对或相对路径。对于 CI 流水线，你可以指向临时构建文件夹：

```csharp
document.Save(Path.Combine(Path.GetTempPath(), "doc.md"), markdownOptions);
```

---

## Frequently Asked Questions

**Q: Does this work with `.doc` (binary) files?**  
A: Yes. `new Document("file.doc")` 会自动检测格式，所以相同代码同时适用于 `.doc` 和 `.docx`。

**Q: What if the Word file contains embedded SVG images?**  
A: Aspose.Words 会以原始格式提取它们。如果需要栅格版本，需要在回调中转换 SVG 流（例如使用 `Svg.Skia`）。

**Q: Can I skip the image extraction altogether?**  
A: 设置 `markdownOptions.ExportImagesAsBase64 = true;` 即可在 markdown 中直接使用 data URI 嵌入图片——这对生成单文件 README 非常有用。

---

## Recap & Next Steps

我们已经完整演示了 **convert word to markdown** 的工作流：

1. 加载 `.docx`。
2. 使用 `ResourceSavingCallback` 配置 `MarkdownSaveOptions`。
3. 保存文档，让回调把每张图片写入专用文件夹。

整个解决方案不到 50 行 C# 代码。

如果你想进一步扩展，可以考虑：

- **生成静态站点**：将 markdown 输入 Hugo 或 Jekyll 等生成器。
- **批量处理**：将代码包装在 `foreach` 循环中，自动处理大量文件。
- **高级图片处理**：在回调中实时调整大小、添加水印或转换格式。

尽情实验吧——替换回调逻辑、调整保存选项，或将其集成到更大的文档流水线中。前路无限，而你现在已经拥有了坚实的基础，能够在任何 **generate markdown from word** 项目中游刃有余。

Happy coding, and may your markdown always be clean and your images always found!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}