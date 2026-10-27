---
category: general
date: 2026-03-25
description: 使用 Aspose.Words 将 DOCX 快速转换为 Markdown，并提取 Word 中的图片。通过完整代码一步步学习。
draft: false
keywords:
- convert docx to markdown
- extract images from word
language: zh
og_description: 使用 Aspose.Words 将 DOCX 转换为 Markdown 并提取 Word 中的图片。请按照本完整教程获取可直接运行的解决方案。
og_title: 在 C# 中将 DOCX 转换为 Markdown – 步骤指南
tags:
- Aspose.Words
- C#
- Markdown
title: 在 C# 中将 DOCX 转换为 Markdown – 完整指南
url: /zh/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 将 DOCX 转换为 Markdown 使用 Aspose.Words

是否曾需要 **将 DOCX 转换为 markdown**，但不确定如何保留嵌入的图片？你并不孤单——许多开发者在尝试将 Word 内容迁移到静态站点生成器或文档仓库时都会遇到这个问题。  
好消息是 Aspose.Words for .NET 可以为你完成繁重的工作，并且通过一个小回调，你还可以 **从 Word 文件中提取图片**。

在本教程中，我们将通过一个真实案例，加载 `.docx`，将其保存为 Markdown 文件，并将每张图片写入专用文件夹。完成后，你将拥有一个可直接运行的控制台应用程序，能够放入任何 .NET 项目中使用。

> **技巧提示：** 如果你只需要文本而不在乎图片，可以完全跳过 `ResourceSavingCallback` —— 代码仍会生成干净的 Markdown。

## 你需要的条件

- **Aspose.Words for .NET**（最新版本，例如 24.12）。你可以从 NuGet 获取：`Install-Package Aspose.Words`。
- **.NET 6.0** 或更高（该 API 也可在 .NET Framework 上运行，但 .NET 6 提供最佳性能）。
- 一个简单的控制台项目或任何你喜欢的 C# 主机。
- 一个输入的 Word 文件（`input.docx`），其中至少包含一张图片，以便我们看到提取效果。

就是这样——无需额外库，也不需要繁琐的命令行工具。让我们开始吧。

![将 docx 转换为 markdown 示例](images/convert-docx-to-markdown.png)

*图片替代文字：将 docx 转换为 markdown 示例*

## 第一步 – 设置项目并添加 Aspose.Words

为了保持整洁，创建一个全新的控制台应用程序：

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

打开 `Program.cs` 并清除自动生成的代码。我们稍后会粘贴完整的解决方案，但现在只需确保项目能够编译。

## 第二步 – 加载源 DOCX

我们首先让 Aspose.Words 读取 Word 文件。此操作 **快速**——库在不打开 Word 本身的情况下解析文档结构。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Path to your source document
string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

// Load the DOCX into a Document object
Document doc = new Document(inputPath);
```

为什么要在 `Path.Combine` 中包装路径？它使代码在 Windows、macOS 和 Linux 上都可移植——当你将项目迁移到 CI 流水线时，你会感激这一点。

## 第三步 – 使用资源回调配置 Markdown 保存选项

当你让 Aspose.Words 保存为 Markdown 时，它通常会将图片嵌入为 Base64 字符串。对于小图标这没问题，但对于较大的照片会导致文件体积膨胀。相反，我们附加一个 **资源保存回调**，将每张图片写入磁盘并更新 Markdown 链接。

```csharp
// Define where the Markdown and resources will live
string outputDir = Path.Combine("YOUR_DIRECTORY", "Output");
string resourcesDir = Path.Combine(outputDir, "Resources");

// Ensure directories exist
Directory.CreateDirectory(outputDir);
Directory.CreateDirectory(resourcesDir);

// Create Markdown options and plug in the callback
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver(resourcesDir)
};
```

请注意，我们将 `resourcesDir` 传入回调的构造函数——这使得路径逻辑不在回调内部，从而使类可复用。

## 第四步 – 实现资源保存回调

该回调实现了 `IResourceSavingCallback`。对于 Aspose.Words 想要写入的每张图片，它会提供一个 `ResourceSavingArgs` 对象。我们决定 **将文件存放在哪里**，为其分配唯一名称，然后告诉引擎跳过默认的保存行为。

```csharp
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a unique, deterministic file name
        string ext = Path.GetExtension(args.FileName);          // e.g., ".png"
        string fileName = $"img_{args.Index}{ext}";            // img_0.png, img_1.jpg, …

        // Full path on disk
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Write the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown URI so it points to the saved image
        args.Uri = $"Resources/{fileName}";

        // Tell Aspose.Words we handled the saving
        args.Cancel = true;
    }
}
```

**为什么这很重要：** 通过设置 `args.Uri`，我们可以精确控制生成的 `.md` 文件中图片的引用方式。相对路径 `Resources/img_0.png` 在 VS Code、GitHub 或静态站点生成器中都能正常工作。

## 第五步 – 将文档保存为 Markdown

现在是最后一步：让 Aspose.Words 写入 Markdown 文件。我们设置的回调会自动为每张图片触发。

```csharp
// Destination Markdown file
string markdownPath = Path.Combine(outputDir, "output.md");

// Perform the conversion
doc.Save(markdownPath, mdOptions);
```

当该行执行完毕后，你将得到：

- `output.md` – 原始 Word 内容的干净 Markdown 表示。
- `Resources/` 文件夹 – 包含从 DOCX 中提取的所有图片。

## 完整工作示例

下面是 **完整、可直接复制粘贴** 的程序。将 `YOUR_DIRECTORY` 替换为包含你的 `input.docx` 的绝对或相对路径。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // ------------------------------------------------------------
        // 1️⃣  Define paths
        // ------------------------------------------------------------
        string baseDir = Path.Combine(Environment.CurrentDirectory, "DemoFiles");
        string inputPath = Path.Combine(baseDir, "input.docx");
        string outputDir = Path.Combine(baseDir, "Output");
        string resourcesDir = Path.Combine(outputDir, "Resources");

        // Create folders if they don't exist
        Directory.CreateDirectory(outputDir);
        Directory.CreateDirectory(resourcesDir);

        // ------------------------------------------------------------
        // 2️⃣  Load the DOCX
        // ------------------------------------------------------------
        Document doc = new Document(inputPath);

        // ------------------------------------------------------------
        // 3️⃣  Prepare Markdown options with a resource callback
        // ------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyResourceSaver(resourcesDir)
        };

        // ------------------------------------------------------------
        // 4️⃣  Save as Markdown
        // ------------------------------------------------------------
        string markdownPath = Path.Combine(outputDir, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown file: {markdownPath}");
        Console.WriteLine($"Images folder: {resourcesDir}");
    }
}

// -----------------------------------------------------------------
// Callback that writes each image to the Resources folder
// -----------------------------------------------------------------
class MyResourceSaver : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyResourceSaver(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Create a deterministic file name like img_0.png
        string extension = Path.GetExtension(args.FileName);
        string fileName = $"img_{args.Index}{extension}";
        string filePath = Path.Combine(_resourcesFolder, fileName);

        // Persist the image bytes
        using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Update the Markdown link to point to the saved image
        args.Uri = $"Resources/{fileName}";

        // Cancel default saving because we already wrote the file
        args.Cancel = true;
    }
}
```

### 预期输出

在任意 Markdown 查看器中打开 `Output/output.md`，你应该会看到类似如下内容：

```markdown
# My Sample Document

Here is a paragraph that came from Word.

![Image 1](Resources/img_0.png)

Another paragraph with **bold** text.
```

`Resources` 文件夹将包含 `img_0.png`、`img_1.jpg` 等，匹配最初嵌入在 `input.docx` 中的图片。

## 常见问题解答 (FAQ)

**这能用于 .doc 文件吗？**  
是的。Aspose.Words 可以加载 `.doc`、`.docx`、`.rtf` 以及许多其他格式。只需在 `inputPath` 中更改文件扩展名即可。

**如果我需要图片的绝对 URL 呢？**  
将 `args.Uri = $"Resources/{fileName}";` 替换为类似 `args.Uri = $"https://mycdn.com/docs/{fileName}";` 的写法。Markdown 将引用远程位置。

**我能控制图片质量或格式吗？**  
回调会收到原始的图片流。如果你想将 PNG 转为 JPEG，可以将流加载到 `System.Drawing.Image`，重新编码后再写入新字节，然后再设置 `args.Uri`。

**`ResourceSavingCallback` 是线程安全的吗？**  
Aspose.Words 会对每个资源顺序调用回调，因此

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}