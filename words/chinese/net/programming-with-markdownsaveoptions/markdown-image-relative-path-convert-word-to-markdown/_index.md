---
category: general
date: 2026-04-28
description: 了解在将 Word 转换为 Markdown 时如何设置 Markdown 图像的相对路径、从 Word 中提取图像以及为导出的图像创建资源文件夹。
draft: false
keywords:
- markdown image relative path
- convert word to markdown
- extract images from word
- create resources folder
- export images from docx
language: zh
og_description: 在将 Word 转换为 Markdown 时，设置 Markdown 图片的相对路径，提取 Word 中的图片，并为导出的图片创建资源文件夹。
og_title: Markdown 图像相对路径 – 将 Word 转换为 Markdown
tags:
- Aspose.Words
- C#
- Markdown
- Image Export
title: Markdown 图像相对路径 – 将 Word 转换为 Markdown
url: /zh/net/programming-with-markdownsaveoptions/markdown-image-relative-path-convert-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# markdown image relative path – 将 Word 转换为 Markdown

是否曾在 **markdown image relative path** 的同时 **convert Word to markdown** 时遇到需求？你并不孤单。大多数开发者在生成的 Markdown 将图片指向平铺文件夹时会卡住，这会破坏你在静态站点或 GitHub 仓库中期望的相对链接结构。

在本教程中，我们将逐步演示一个完整的端到端解决方案，**extracts images from Word**，**creates a resources folder**，并重写图片引用，使其使用干净的 *markdown image relative path*。完成后，你将拥有一个可直接发布的 `.md` 文件以及一个整齐组织的 `Resources` 目录，包含从原始 `.docx` 中提取的所有图片。

> **你将获得：** 一个单文件 C# 程序（无需外部脚本），对每个部分 *why* 重要性的清晰解释，以及一些可直接复制粘贴到自己项目中的实用技巧。

## 前置条件

- **.NET 6.0** 或更高版本已安装（你也可以针对 .NET Framework 4.7+，但 .NET 6 是新项目的最佳选择）。
- **Aspose.Words for .NET**（撰写时的最新 NuGet 包，版本 23.12）。使用以下方式安装：
  ```bash
  dotnet add package Aspose.Words
  ```
- 一个实际包含图片的 Word 文档——我们称之为 `WithImages.docx`。
- 一个用于存放输出 markdown 和图片的文件夹，例如 `C:\Projects\MarkdownExport`。

不需要额外的库；其他所有工作均由 Aspose.Words 处理。

## 步骤 1：加载源 Word 文档（convert word to markdown 的起点）

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Adjust the path to point at your own .docx file.
        string sourcePath = @"C:\Projects\MarkdownExport\WithImages.docx";

        // Load the document – this is where Aspose.Words parses the Word file.
        Document doc = new Document(sourcePath);
        
        // The rest of the workflow follows…
    }
}
```

*为什么重要：* 加载文档后我们可以访问内部节点树，其中包含后续需要 **export images from docx** 的图片部分。如果加载失败，后续步骤都不会执行，请再次检查路径和文件权限。

## 步骤 2：使用自定义回调配置 `MarkdownSaveOptions`（create resources folder 的核心）

`ResourceSavingCallback` 让我们在 Aspose.Words 每次尝试写入图片文件时进行干预。在回调内部，我们将 **create a Resources sub‑folder** 并调整引用，使生成的 markdown 使用 *markdown image relative path*。

```csharp
// Inside Main(), after loading the document:
string outputFolder = @"C:\Projects\MarkdownExport";
string resourcesFolder = Path.Combine(outputFolder, "Resources");

// Make sure the folder exists before we start saving anything.
Directory.CreateDirectory(resourcesFolder);

// Set up the Markdown save options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Hook that runs for every image resource.
    ResourceSavingCallback = new MyMarkdownResourceCallback(resourcesFolder)
};

// Save the document as Markdown.
string markdownPath = Path.Combine(outputFolder, "Doc.md");
doc.Save(markdownPath, mdOptions);
```

请注意我们将 `resourcesFolder` 传入回调的构造函数——这使文件夹路径保持灵活，避免在代码中硬编码字符串。

## 步骤 3：实现回调以 **creates resources folder** 并重写路径

```csharp
/// <summary>
/// Handles image extraction and path rewriting for markdown export.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyMarkdownResourceCallback(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the full file system path where the image will be stored.
        string targetPath = Path.Combine(_resourcesFolder, args.ResourceFileName);
        
        // 2️⃣ Ensure the directory exists (in case Aspose creates sub‑folders).
        Directory.CreateDirectory(Path.GetDirectoryName(targetPath));

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = File.Create(targetPath))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Update the markdown reference to use a relative path.
        // This is the crucial line that gives us the markdown image relative path.
        args.ResourceFileName = Path.Combine("Resources", args.ResourceFileName);
    }
}
```

*为什么可行：* `args.Stream` 包含原始图片字节。将其复制到 `Resources` 文件夹中的文件时，我们安全地 **export images from docx**。随后我们将 `args.ResourceFileName` 替换为相对 URL（`Resources/image.png`）。当 Aspose.Words 稍后写入 markdown 时，它会注入该字符串，从而得到期望的 *markdown image relative path*。

## 步骤 4：验证生成的 Markdown（最终输出的样子）

在任意文本编辑器中打开 `Doc.md`。你应该会看到类似如下内容：

```markdown
# Sample Heading

Here is an inline picture:

![Image 0](Resources/Image_0.png)

And a picture inside a table:

![Image 1](Resources/Image_1.jpg)
```

重要的是每个图片引用都指向 `Resources/...` ——这正是我们想要的 **markdown image relative path**。

![markdown image relative path 示例](example.png "markdown image relative path 示例")

*提示：* 如果在支持相对链接的查看器中打开 markdown（如 VS Code 预览、GitHub 或静态站点生成器），图片将会正确渲染，无需额外配置。

## 步骤 5：常见陷阱与专业提示

| 问题 | 为什么会发生 | 如何解决 |
|------|--------------|----------|
| 图片最终位于根文件夹而不是 `Resources` | 回调未附加或 `args.ResourceFileName` 未被覆盖。 | 再次确认在调用 `doc.Save` 之前已设置 **ResourceSavingCallback**。 |
| 文件名包含非法字符 | Word 有时会使用空格或 Unicode 符号为图片命名。 | 在回调中使用 `Path.GetInvalidFileNameChars()` 清理 `args.ResourceFileName`。 |
| 大型文档处理时间较长 | 每个图片都是同步写入的。 | 如果使用 .NET 6+ 并需要性能，可切换为异步 I/O（`await args.Stream.CopyToAsync(fileStream)`）。 |
| 当 markdown 被移动时相对路径会失效 | 路径相对于 markdown 文件的位置。 | 保持 `Doc.md` 与 `Resources` 文件夹在同一目录，或在回调中使用不同的相对前缀（例如 `../assets`）。 |

## 步骤 6：扩展解决方案（如果需要更多控制怎么办？）

- **Multiple output formats:** 将 `MarkdownSaveOptions` 替换为 `HtmlSaveOptions` 或 `PdfSaveOptions`，同时保持相同的回调——Aspose.Words 将对每个图片调用它，无论格式为何。
- **Custom image naming:** 如果想重命名图片（例如 `figure-01.png`），在写入文件前于回调中修改 `args.ResourceFileName`。
- **Embedding images as Base64:** 将 `args.ResourceFileName` 设置为 data URI（`data:image/png;base64,...`），并跳过文件写入。这对单文件 markdown 导出非常有用。

## 结论

现在你拥有一个完整的 C# 程序，能够 **converts Word to markdown**，**extracts images from word**，**creates a resources folder**，并为每张图片保证干净的 **markdown image relative path**。代码自包含，兼容最新的 Aspose.Words 版本，可轻松嵌入任何 .NET 项目。

下一步？尝试将生成的 markdown 输入到 Hugo 或 Jekyll 等静态站点生成器，或实验回调以直接将图片嵌入为 Base64 字符串。如果遇到边缘情况——例如 SVG 图片或异常大的文件——请参考 “Common pitfalls” 表格；通常只需微调即可解决。

祝编码愉快，愿你的 markdown 永远指向正确的文件夹！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}