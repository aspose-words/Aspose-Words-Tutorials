---
category: general
date: 2026-06-27
description: 使用 Aspose.Words 将 docx 转换为 markdown 并保存 docx 中的图片。了解如何从 Word 文件中提取图片以及将
  Word 文档导出为 markdown。
draft: false
keywords:
- convert docx to markdown
- save images from docx
- extract images from word file
- export word document as markdown
language: zh
og_description: 将 docx 转换为 markdown 并保存 docx 中的图片。本指南展示了如何从 Word 文件中提取图片以及将 Word 文档导出为
  markdown。
og_title: 将 docx 转换为 markdown 并从 docx 中保存图片
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  headline: Convert docx to markdown & save images from docx
  type: TechArticle
- description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  name: Convert docx to markdown & save images from docx
  steps:
  - name: How the code works
    text: '- **Loading the document** (`new Document(inputPath)`) gives us an in‑memory
      representation of the Word file, complete with all its parts—paragraphs, tables,
      and **images**. - **`MarkdownSaveOptions`** is where the magic happens. By attaching
      a `ResourceSavingCallback`, we gain full control over eve'
  - name: Quick sanity check
    text: '- Does the Markdown file open without errors in VS Code’s preview pane?
      ✅ - Are all pictures displayed when you view the file on GitHub? ✅ - Did the
      `Images` directory contain one file per picture from the original `.docx`? ✅'
  - name: What’s next?
    text: '- **Style the Markdown** – add a front‑matter block for Jekyll or Hugo.
      - **Automate the pipeline** – embed this code in an Azure DevOps or GitHub Action
      step. - **Handle tables and footnotes** – explore other `MarkdownSaveOptions`
      flags like `ExportTableBorderStyles`.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Markdown
- Word
title: 将 docx 转换为 markdown 并从 docx 中保存图片
url: /zh/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-save-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 将 docx 转换为 markdown 并保存 docx 中的图片

是否曾想过在 **将 docx 转换为 markdown** 时不丢失 Word 文件中嵌入的图片？你并不孤单——开发者常常需要一个干净的 Markdown 版报告，同时保留每个图表、徽标或截图。

在本教程中，我们将演示一个完整、可直接运行的示例，**将 .docx 转换为 Markdown**、**将 docx 中的图片保存到自定义文件夹**，并展示如何使用强大的 Aspose.Words 库 **从 Word 文件中提取图片**。完成后，你还将了解如何用一行代码 **将 Word 文档导出为 markdown**。

## 你需要准备的环境

- 已在机器上安装 .NET 6+（或 .NET Framework 4.7.2+）  
- 对 `Aspose.Words` 的 NuGet 引用（免费试用版即可）  
- 一个包含至少一张图片的示例 `input.docx`  
- 你喜欢的 IDE——Visual Studio、Rider，甚至 VS Code 都可以  

无需额外的第三方工具，也不需要繁琐的命令行操作。只需纯 C# 代码。

## 将 docx 转换为 markdown – 概览

核心思路很简单：

1. 加载源 Word 文档。  
2. 告诉 Aspose.Words 如何处理外部资源（如图片）。  
3. 将文档保存为 Markdown，让库完成繁重的工作。

下面是 **完整、可运行的程序**。复制粘贴到新的控制台项目中，按 `Ctrl+F5` 运行即可。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load the source document that contains images
        // -----------------------------------------------------------------
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        Document doc = new Document(inputPath);

        // -----------------------------------------------------------------
        // Step 2: Configure Markdown save options with a custom callback
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This callback runs for each external resource (images, CSS, etc.)
            ResourceSavingCallback = (sender, args) =>
            {
                // ---------------------------------------------------------
                // Step 3a: Save images to a custom folder using a unique name
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.Image)
                {
                    string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
                    Directory.CreateDirectory(imageFolder); // ensures folder exists

                    // Use a GUID so we never clash with existing files
                    string uniqueName = Guid.NewGuid().ToString() + args.Extension;
                    args.SavePath = Path.Combine(imageFolder, uniqueName);
                }

                // ---------------------------------------------------------
                // Step 3b: Skip CSS files – they aren't needed for plain Markdown
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.CssStyleSheet)
                    args.Cancel = true;
            }
        };

        // -----------------------------------------------------------------
        // Step 4: Export the document to Markdown, applying the options
        // -----------------------------------------------------------------
        string outputPath = Path.Combine("YOUR_DIRECTORY", "output.md");
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("Conversion complete! Markdown saved to " + outputPath);
        Console.WriteLine("Images extracted to " + Path.Combine("YOUR_DIRECTORY", "Images"));
    }
}
```

### 代码工作原理

- **加载文档** (`new Document(inputPath)`) 会在内存中创建 Word 文件的表示，包含所有部分——段落、表格以及 **图片**。  
- **`MarkdownSaveOptions`** 是关键所在。通过附加 `ResourceSavingCallback`，我们可以完全控制 Aspose.Words 试图写出的每个外部资源。  
- 在回调中，我们通过检查 `args.ResourceType == ResourceType.Image` 来 **从 Word 文件中提取图片**。回调会收到图片字节、原始扩展名以及我们动态创建的文件夹路径 `SavePath`。使用 `Guid.NewGuid()` 能保证文件名唯一，避免意外覆盖。  
- 我们 **跳过 CSS** (`ResourceType.CssStyleSheet`)，因为普通 Markdown 不需要样式表，这样输出更简洁。  
- 最后，`doc.Save(outputPath, mdOptions)` 将 Markdown 文件写出，将 Word 构造转换为 Markdown 等价物（标题变为 `#`，表格变为管道分隔的行，等等）。

## 将图片从 docx 保存 – 自定义文件夹策略

为什么要使用自定义文件夹？想象一下，你在 CI 流水线中生成文档。希望 Markdown 文件及其资源整齐地并排放置，便于复现。

```csharp
string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
Directory.CreateDirectory(imageFolder);
```

几个 **实用技巧**：

- **保持文件夹路径相对于项目根目录**。这样 Markdown 文件可以使用相对链接引用图片（`![Alt text](Images/abc123.png)`），在 GitHub、GitLab 或任何静态站点生成器上都能正常工作。  
- **如果需要确定的文件名**（例如，同一图片始终使用相同文件名），可以用图片字节的哈希代替 GUID：`MD5.Create().ComputeHash(args.Data)`。这是一点小改动，却对缓存非常有帮助。

## 从 Word 文件中提取图片 – 边缘情况

1. **多种图片格式** – Aspose.Words 支持 PNG、JPEG、GIF、BMP，甚至 SVG。`args.Extension` 已包含正确的文件扩展名，无需自行判断。  
2. **超大图片** – 如果源文档包含高分辨率照片，生成的文件可能会很大。可以在回调后加入压缩步骤，使用 `System.Drawing` 或 `ImageSharp`。  
3. **隐藏图片** – Word 可能在页眉/页脚或文本框中存储图片。回调会捕获它们，所以你会提取 **所有** 图片，而不仅仅是可见的。如果只想要正文图片，可根据 `args.ImageIndex` 过滤，或检查 `args.ImageType`。

## 将 Word 文档导出为 markdown – 验证结果

运行程序后，用任意 Markdown 查看器打开 `output.md`。你应当看到类似下面的内容：

```markdown
# My Report

Here is an introductory paragraph.

![Image1](Images/3f9c2d1e-7a5b-4c9e-9f6a-2b4e5d6f7a8b.png)

More text follows...
```

注意图片链接指向我们创建的 **Images** 文件夹。这正是一次成功的 **export Word document as markdown** 操作的标志。

### 快速检查

- Markdown 文件在 VS Code 预览窗格中能正常打开吗？ ✅  
- 在 GitHub 上查看时所有图片都显示了吗？ ✅  
- `Images` 目录是否包含了原始 `.docx` 中每张图片对应的文件？ ✅  

如果上述检查有任何不通过，请再次检查 `ResourceSavingCallback` 逻辑，并确保 `YOUR_DIRECTORY` 占位符指向可写入的位置。

## 常见坑点及规避方法

| Pitfall（坑点） | Why it happens（原因） | Fix（解决方案） |
|----------------|----------------------|----------------|
| **Images not appearing**（图片不显示） | 回调未触发，因为没有为 `ResourceSavingCallback` 赋值。 | 在调用 `doc.Save` **之前** 赋值回调。 |
| **Empty Images folder**（图片文件夹为空） | 不小心对所有资源都设置了 `args.Cancel = true`。 | 只对 CSS（`ResourceType.CssStyleSheet`）取消，保持图片不受影响。 |
| **File‑path too long on Windows**（Windows 文件路径过长） | 使用深层文件夹加 GUID 可能超过 260 字符限制。 | 保持文件夹层级浅，或在 Windows 10+ 启用长路径支持。 |
| **Duplicate image names**（图片名称重复） | 使用 `DateTime.Now.Ticks` 而非 GUID 在快速循环中会冲突。 | 使用 `Guid.NewGuid()` 确保唯一性。 |

## 小结

我们已经 **将 docx 转换为 markdown**、**保存了 docx 中的图片**，并演示了在 **导出 Word 文档为 markdown** 时 **从 Word 文件中提取图片** 的完整流程。整个过程依赖 Aspose.Words 的 `ResourceSavingCallback`，让你对每个外部资源拥有细粒度的控制。

### 接下来可以做什么？

- **美化 Markdown** – 为 Jekyll 或 Hugo 添加 front‑matter 块。  
- **自动化流水线** – 将此代码嵌入 Azure DevOps 或 GitHub Action 步骤。  
- **处理表格和脚注** – 探索 `MarkdownSaveOptions` 的其他标志，如 `ExportTableBorderStyles`。  

随意调整文件夹结构、加入图片压缩，甚至将输出格式切换为 HTML，只需把 `MarkdownSaveOptions` 换成 `HtmlSaveOptions`。当你拥有坚实的 **convert docx to markdown** 基础时，天地皆可为你所用。

祝编码愉快，愿你的文档始终既美观 **又** 机器可读！

## 接下来该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助你进一步掌握 API 功能并探索在项目中的其他实现方式。每篇资源都提供完整可运行的代码示例和逐步解释。

- [Save Word Images – Convert Word to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Convert Word to Markdown – Embed Images as Base64](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)
- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}