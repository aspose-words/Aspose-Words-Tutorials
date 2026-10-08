---
category: general
date: 2026-02-26
description: 创建文件夹 C# 教程，展示如何将 Word 转换为 Markdown，提取 docx 中的图片，并将流复制到文件——一步完成。
draft: false
keywords:
- create folder c#
- convert word to markdown
- extract images from docx
- copy stream to file
language: zh
og_description: Create folder C# 教程带您逐步了解将 Word 转换为 markdown、从 docx 中提取图片以及将流复制到文件的清晰代码示例。
og_title: 创建文件夹 C# – 将 Word 转换为 Markdown 并提取图片
tags:
- C#
- Aspose.Words
- Markdown
- Image Extraction
title: 创建文件夹 C# – 将 Word 转换为 Markdown 并提取图片
url: /zh/net/programming-with-markdownsaveoptions/create-folder-c-convert-word-to-markdown-extract-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建文件夹 C# – 将 Word 转换为 Markdown 并提取图像

是否曾经需要 **create folder C#** 的同时将 Word 文档转换为 markdown 并提取其中的所有图片？你并不是唯一为此抓耳挠腮的人。在许多自动化流水线中，你往往需要同时处理文件系统操作、格式转换以及二进制数据处理——一次性完成。  

在本指南中，我们将逐步演示一个完整且可运行的解决方案：它会创建目标目录，将 `.docx` 转换为 markdown，提取每个嵌入的图像，并使用 **copy stream to file** 逻辑将图像保存到指定位置。无需外部脚本，无需手动步骤。仅使用纯 C# 和 Aspose.Words 库。

> **你将获得**  
> * 一个清晰的文件夹结构，准备好存放 markdown 和资源  
> * 一个 markdown 文件，正确引用提取的图片  
> * 完整的源代码，可直接放入任何 .NET 项目  

在深入之前，请确保你已经：

* 安装了 .NET 6.0（或更高）SDK —— 代码使用了现代语言特性。  
* 拥有 **Aspose.Words for .NET** 的许可证（免费试用版可用于测试）。  
* 使用 Visual Studio 2022 或你喜欢的编辑器。  

如果你在想 *为什么* 要提取图像而不是直接嵌入，想想静态站点生成器：它们喜欢使用相对图片路径的 markdown，而将资源放在专用文件夹中可以保持整洁并有利于缓存。

---

## 创建文件夹 C# 并准备输出结构

我们首先需要在磁盘上准备一个存放所有内容的地方。这一步就是 **create folder C#** 动作发生的地方，得益于 `Directory.CreateDirectory`，实现非常简单。该方法是幂等的——如果文件夹已存在不会抛异常，省去了额外的检查。

```csharp
using System;
using System.IO;

// Define the base output directory (adjust as needed)
string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");

// Subfolders for markdown and images
string markdownFolder = Path.Combine(baseOutput, "markdown");
string imagesFolder   = Path.Combine(baseOutput, "MyImages");

// Ensure the folders exist
Directory.CreateDirectory(markdownFolder);
Directory.CreateDirectory(imagesFolder);

Console.WriteLine($"Created folders:\n • {markdownFolder}\n • {imagesFolder}");
```

**为什么这很重要：**  
提前创建文件夹可以确保后续保存步骤不会因 `DirectoryNotFoundException` 而失败。它还为你提供了可预测的布局：`output/markdown` 用于 `.md` 文件，`output/MyImages` 用于我们提取的每张图片。

> **小贴士：** 如果多次运行程序，可能需要先清空图片文件夹（`Directory.GetFiles(imagesFolder).ToList().ForEach(File.Delete);`），以避免残留文件。

---

## 使用 Aspose.Words 将 Word 转换为 Markdown

目录结构准备好后，让我们把 Word 文档转换为 markdown。Aspose.Words 完成繁重的工作——无需手动处理 OpenXML 或第三方转换器。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source DOCX (replace with your actual path)
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
var doc = new Document(inputPath);

// Configure markdown options and attach the image callback (we’ll define it later)
var mdOptions = new MarkdownSaveOptions
{
    // The callback will redirect each extracted image to our custom folder
    ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
};

// Save the markdown file into the previously created folder
string markdownPath = Path.Combine(markdownFolder, "output.md");
doc.Save(markdownPath, mdOptions);

Console.WriteLine($"Word document converted to markdown at: {markdownPath}");
```

**内部发生了什么？**  
`MarkdownSaveOptions` 告诉 Aspose 输出 markdown 语法。默认情况下，库会把图像放在与 markdown 文件相同的文件夹中，并使用自动生成的名称。通过提供 `ResourceSavingCallback`，我们拦截该行为，并在我们选择的位置 **copy stream to file**。

---

## 从 DOCX 中提取图像并保存

回调类实现了 `IResourceSavingCallback`。在其中我们收到一个 `ResourceSavingArgs` 对象，里面包含原始图像流和建议的文件名。随后我们将该流写入磁盘，必要时重命名文件，并告知 Aspose 已完成处理。

```csharp
using Aspose.Words.Saving;
using System.IO;

/// <summary>
/// Handles image extraction during markdown conversion.
/// </summary>
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageSavingCallback(string targetFolder)
    {
        _targetFolder = targetFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Ensure the target folder exists (defensive, though we created it earlier)
        Directory.CreateDirectory(_targetFolder);

        // Build a new, friendly file name – you can customize the pattern
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // **Copy stream to file** – the core of the image extraction
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Tell Aspose to use our new path in the markdown reference
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true; // Prevent default saving logic
    }
}
```

### Markdown 的最终效果

转换完成后，生成的 `output.md` 将包含类似以下的行：

```markdown
![Image 1](MyImages/img_picture1.png)
```

因为我们将 `args.ResourceFileName` 改为相对路径，markdown 直接指向我们创建的文件夹。这正是静态站点生成器所期望的。

**边缘情况处理：**  
*如果文档中出现重复的图片名称*，在原名称前加上前缀 `img_` 通常可以避免冲突，当然也可以加入 GUID（`Guid.NewGuid()`）以实现绝对唯一。

---

## Copy stream to file – 处理图像数据

你可能会想，为什么不直接调用 `File.WriteAllBytes`。答案在于 **stream flexibility**。`args.Stream` 可能是内存流、网络流或其他实现。使用 `CopyTo` 可以保持对流类型的无感知，让 .NET 高效地处理缓冲区大小。

下面是一个紧凑的工具方法，供你在需要将通用流复制到其他位置时使用：

```csharp
/// <summary>
/// Copies any readable stream to a file on disk.
/// </summary>
public static void CopyStreamToFile(Stream source, string destinationPath)
{
    using (var file = new FileStream(destinationPath, FileMode.Create, FileAccess.Write))
    {
        source.CopyTo(file);
    }
}
```

如果你更倾向于单一职责的做法，可以用 `CopyStreamToFile` 替代 `ImageSavingCallback` 中的内联复制代码。

---

## 完整可运行示例

把所有代码片段组合在一起，就得到一个可以从命令行直接运行的自包含程序：

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the folder structure
        string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");
        string markdownFolder = Path.Combine(baseOutput, "markdown");
        string imagesFolder   = Path.Combine(baseOutput, "MyImages");
        Directory.CreateDirectory(markdownFolder);
        Directory.CreateDirectory(imagesFolder);

        // 2️⃣ Load the DOCX
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(inputPath);

        // 3️⃣ Set up markdown options with our image callback
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
        };

        // 4️⃣ Save as markdown
        string markdownPath = Path.Combine(markdownFolder, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown: {markdownPath}");
        Console.WriteLine($"Images folder: {imagesFolder}");
    }
}

// ---------- ImageSavingCallback (same as earlier) ----------
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageSavingCallback(string targetFolder) => _targetFolder = targetFolder;

    public void ResourceSaving(ResourceSavingArgs args)
    {
        Directory.CreateDirectory(_targetFolder);
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true;
    }
}
```

**预期结果**

* `output/markdown/output.md` – 一个 markdown 文件，图像引用形如 `![Alt text](MyImages/img_picture1.png)`。  
* `output/MyImages/` – 每张原本位于 `input.docx` 中的图片对应一个 PNG/JPEG 文件。  

在任意查看器（VS Code、GitHub 或静态站点生成器）中打开该 markdown，你会看到图片正如在原始 Word 文件中出现的那样被渲染。

---

## 常见问题与故障排除

| 问题 | 答案 |
|----------|--------|
| **如果目标文件夹已经有文件怎么办？** | `Directory.CreateDirectory` 不会覆盖已有文件。如果需要一次干净的运行，请先删除目标文件夹中的内容。 |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}