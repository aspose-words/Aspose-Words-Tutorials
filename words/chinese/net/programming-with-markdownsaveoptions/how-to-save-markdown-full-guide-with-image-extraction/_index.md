---
category: general
date: 2026-03-30
description: 如何在 C# 中保存 Markdown 文件，同时从 Markdown 中提取图像，并使用 Aspose.Words 将文档保存为 Markdown。
draft: false
keywords:
- how to save markdown
- extract images from markdown
- save document as markdown
- markdown resource handling
- C# markdown export
language: zh
og_description: 如何快速保存 Markdown。学习从 Markdown 中提取图片并将文档保存为 Markdown，附完整代码示例。
og_title: 如何保存 Markdown – 完整 C# 指南
tags:
- C#
- Markdown
- Aspose.Words
title: 如何保存 Markdown——完整指南与图片提取
url: /zh/net/programming-with-markdownsaveoptions/how-to-save-markdown-full-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何保存 Markdown – 完整 C# 指南

有没有想过 **如何保存 markdown** 并保持所有嵌入的图片完整？你并不是唯一遇到这个问题的人。许多开发者在库将图片随意放入某个文件夹，甚至根本不导出时会卡住。好消息是？只需几行 C# 代码和 Aspose.Words，你就可以将文档导出为 markdown，提取每张图片，并精确控制每个文件的保存位置。

在本教程中，我们将演示一个真实场景：获取 `Document` 对象，配置 `MarkdownSaveOptions`，并告诉保存器每张图片的保存位置。完成后，你将能够 **save document as markdown**、**extract images from markdown**，并拥有整洁的文件夹结构以便发布。没有模糊的引用——只有完整、可运行的示例，直接复制粘贴即可。

## 你需要的条件

- **.NET 6+**（任何近期的 SDK 都可）
- **Aspose.Words for .NET**（NuGet 包 `Aspose.Words`）
- 对 C# 语法的基本了解（我们会保持简单）
- 已有的 `Document` 实例（我们会演示创建一个）

如果你已经具备这些条件，下面开始吧。

## 步骤 1：设置项目并导入命名空间

首先，创建一个新的控制台应用（或集成到现有解决方案中）。然后添加 Aspose.Words 包：

```bash
dotnet add package Aspose.Words
```

现在引入所需的命名空间：

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

> **专业提示：** 将 `using` 语句放在文件顶部；这使得代码更易于人类和 AI 解析器阅读。

## 步骤 2：创建示例文档（或加载自己的文档）

为演示我们将构建一个包含段落和嵌入图片的微型文档。如果你已有源文件，请将此部分替换为 `Document.Load("YourFile.docx")`。

```csharp
// Step 2: Build a simple document with an image
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Add some text
builder.Writeln("Hello, Markdown world!");

// Insert an image from disk (make sure the path exists)
string imagePath = @"YOUR_DIRECTORY/sample-image.png";
builder.InsertImage(imagePath);
```

> **为什么这很重要：** 如果跳过图片，后续就没有 *extract* 的对象，也看不到回调的执行效果。

## 步骤 3：使用资源保存回调配置 MarkdownSaveOptions

这里是解决方案的核心。`ResourceSavingCallback` 会对 **每个** 外部资源——图片、字体、CSS 等——触发。我们将利用它创建专用的 `Resources` 子文件夹，并为每个文件生成唯一名称。

```csharp
// Step 3: Define markdown save options and attach a callback
var markdownSaveOptions = new MarkdownSaveOptions
{
    // This delegate runs for each resource the saver wants to write out
    ResourceSavingCallback = (sender, args) =>
    {
        // Ensure the Resources folder exists (creates it only once)
        string resourcesFolder = @"YOUR_DIRECTORY/Resources/";
        Directory.CreateDirectory(resourcesFolder);

        // Build a unique filename: img_0.png, img_1.jpg, etc.
        string resourceFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";

        // Tell the saver where to place the file
        args.SavePath = Path.Combine(resourcesFolder, resourceFileName);
    }
};
```

**发生了什么？**  
- `args.Index` 是从零开始的计数器，保证唯一性。  
- `Path.GetExtension(args.FileName)` 保留原始文件类型（PNG、JPG 等）。  
- 通过设置 `args.SavePath`，我们覆盖默认位置，使所有文件保持整洁。

## 步骤 4：将文档保存为 Markdown

配置好选项后，导出只需一行代码：

```csharp
// Step 4: Export to markdown using the configured options
string outputMarkdown = @"YOUR_DIRECTORY/Doc.md";
doc.Save(outputMarkdown, markdownSaveOptions);
```

运行后你会看到：

- `Doc.md` 包含引用图片的 markdown 文本。  
- 与其同目录的 `Resources` 文件夹中存放 `img_0.png`、`img_1.jpg` …  

这就是 **how to save markdown** 的完整流程，包含资源提取。

## 步骤 5：验证结果（可选但推荐）

在任意文本编辑器中打开 `Doc.md`，你应该看到类似如下内容：

```markdown
Hello, Markdown world!

![image](Resources/img_0.png)
```

`Resources` 文件夹会包含你插入的原始图片。如果在查看器（如 VS Code、GitHub）中打开 markdown 文件，图片会正确渲染。

> **常见问题：** *如果我想把图片放在与 markdown 文件相同的文件夹中怎么办？*  
> 只需将 `resourcesFolder` 改为 `Path.GetDirectoryName(outputMarkdown)`，并相应调整 markdown 中的图片路径。

## 从 Markdown 中提取图片 – 高级技巧

有时你需要对命名约定进行更细粒度的控制，或想跳过某些资源类型。下面提供几种常用变体，供你参考。

### 5.1 跳过非图片资源

```csharp
ResourceSavingCallback = (sender, args) =>
{
    // Only process images; ignore CSS, fonts, etc.
    if (!args.ContentType.StartsWith("image/", StringComparison.OrdinalIgnoreCase))
        return; // Let the default handling continue

    // ...same folder creation logic as before...
};
```

### 5.2 保留原始文件名

如果你更喜欢使用原始文件名而不是 `img_0`，只需去掉 `args.Index` 部分：

```csharp
string resourceFileName = args.FileName; // uses the name from the source document
```

### 5.3 为每个文档使用自定义子文件夹

```csharp
string docName = Path.GetFileNameWithoutExtension(outputMarkdown);
string resourcesFolder = $@"YOUR_DIRECTORY/{docName}_Resources/";
Directory.CreateDirectory(resourcesFolder);
```

这些代码片段演示了 **extract images from markdown** 的灵活实现方式，满足不同项目约定。

## 常见问题 (FAQ)

| Question | Answer |
|----------|--------|
| **这在 .NET Core 上可用吗？** | Absolutely—Aspose.Words is cross‑platform, so the same code runs on Windows, Linux, or macOS. |
| **SVG 图片怎么办？** | SVGs are treated as images; the callback will receive a `.svg` extension. Ensure your markdown viewer supports SVG. |
| **我可以更改 markdown 语法吗（例如使用 HTML `<img>` 标签）？** | Set `markdownSaveOptions.ExportImagesAsBase64 = false` and adjust `ExportImagesAsHtml` if you need raw HTML tags. |
| **有没有办法批量处理多个文档？** | Wrap the above logic in a `foreach` loop over a file collection—just remember to give each document its own resources folder. |

## 完整可运行示例（复制粘贴即可）

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a document and add an image
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, Markdown world!");
        string imagePath = @"YOUR_DIRECTORY/sample-image.png"; // <-- change this
        builder.InsertImage(imagePath);

        // 2️⃣ Configure save options with a callback to extract images
        var markdownSaveOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (sender, args) =>
            {
                string resourcesFolder = @"YOUR_DIRECTORY/Resources/";
                Directory.CreateDirectory(resourcesFolder);

                string resourceFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
                args.SavePath = Path.Combine(resourcesFolder, resourceFileName);
            }
        };

        // 3️⃣ Save as markdown
        string outputPath = @"YOUR_DIRECTORY/Doc.md";
        doc.Save(outputPath, markdownSaveOptions);

        Console.WriteLine("Markdown saved successfully!");
        Console.WriteLine($"Check {outputPath} and the Resources folder for images.");
    }
}
```

运行程序（`dotnet run`），你会看到控制台消息确认成功。所有图片已整齐存放，markdown 文件正确指向它们。

## 结论

你刚刚学习了 **how to save markdown** 的同时 **extract images from markdown**，并确保文档能够 **saved document as markdown**，对资源位置拥有完整控制。关键在于 `ResourceSavingCallback`——它让你对导出器生成的每个外部文件拥有细粒度的管理权。

接下来你可以：

- 将此流程集成到 Web 服务中，实时将用户上传的 DOCX 文件转换为 markdown。  
- 扩展回调，根据符合 CMS 的命名约定重命名文件。  
- 与其他 Aspose.Words 功能（如 `ExportImagesAsBase64`）结合，实现内联图片的 markdown。

动手试一试，调整文件夹逻辑以适配你的项目，让 markdown 输出在文档流水线中大放异彩。

--- 

![如何保存 markdown 示例](/assets/how-to-save-markdown.png "如何保存 markdown 示例")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}