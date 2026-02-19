---
category: general
date: 2026-02-18
description: 使用简易步骤将文档导出为 Markdown 并将图片保存到子文件夹。学习如何在 C# 中将文档保存为 Markdown。
draft: false
keywords:
- create markdown from document
- export document to markdown
- save document as markdown
- save images to subfolder
language: zh
og_description: 使用 C# 将文档转换为 Markdown，并学习在导出 Markdown 时将图片保存到子文件夹。请按照分步指南操作。
og_title: 从文档创建 Markdown – 导出并保存图片
tags:
- C#
- Aspose.Words
- Markdown export
title: 从文档创建 Markdown – 导出并保存图像
url: /zh/java/document-conversion-and-export/create-markdown-from-document-export-and-save-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 从文档创建 Markdown – 导出并保存图片

是否曾经想要 **从文档创建 markdown**，却不确定如何让嵌入的图片保持整洁？你并不孤单。在许多项目中，我们会以编程方式生成报告、手册或博客草稿，最不想看到的就是一堆散落在输出文件夹中的图片文件。

在本教程中，我们将一步步演示一个完整、可直接运行的解决方案，**将文档导出为 markdown**，将每张图片存放在专用的 *md‑resources* 子文件夹中，最后使用 Aspose.Words for .NET API **将文档保存为 markdown**。完成后，你将拥有一个可以直接嵌入任何 C# 代码库的方法，以及处理边缘情况的若干技巧。

> **快速概览：**  
> • 设置 `MarkdownSaveOptions`  
> • 提供一个 `IResourceSavingCallback` 将图片重定向到子文件夹  
> • 使用配置好的选项调用 `Document.Save`  

如果你想了解为什么我们选择回调而不是后处理，请继续阅读——我们会一步步解释原因。

---

## 前置条件

- .NET 6.0 或更高（代码同样适用于 .NET Framework 4.7+）  
- Aspose.Words for .NET（NuGet 包 `Aspose.Words`）  
- 一个源 `Document` 对象（可以是 .docx、.pdf、.rtf 等）  

不需要额外的库；回调 API 已内置于 Aspose.Words。

---

## 第一步：从文档创建 markdown – 配置保存选项

我们首先实例化 `MarkdownSaveOptions`。该对象告诉 Aspose.Words 转换时的行为，例如使用哪种 Markdown 方言、是否将图片嵌入为 Base64，以及生成的文件放在哪里。

```csharp
// Step 1: Initialize Markdown save options
var markdownSaveOptions = new Aspose.Words.Saving.MarkdownSaveOptions();
```

> **为什么重要：**  
> 如果不显式创建 `MarkdownSaveOptions`，库会回退到默认设置，将图片直接嵌入 Markdown 文件为 Base64 字符串。这会导致文件体积巨大，失去拥有整洁 *images* 文件夹的意义。

---

## 第二步：导出文档为 markdown 并定义资源处理

现在我们告诉保存器 **把每张图片放到哪里**。`IResourceSavingCallback` 接口为我们提供了一个钩子，在导出过程中每发现一个资源（图片、SVG 等）时都会触发。在回调内部我们：

1. 确保目标文件夹存在（`md-resources/`）。  
2. 将 `OutputFileName` 设置为文件夹路径加上原始资源名称。  

```csharp
// Step 2: Hook into the resource‑saving pipeline
markdownSaveOptions.ResourceSavingCallback = new Aspose.Words.Saving.IResourceSavingCallback(
    (args) =>
    {
        // All images will be placed in "md-resources" relative to the output .md file
        const string folder = "md-resources/";
        Directory.CreateDirectory(folder);          // Create folder if it doesn’t exist

        // Preserve the original file name (e.g., image001.png) but prepend the folder path
        args.OutputFileName = Path.Combine(folder, args.ResourceFileName);

        // Optional: you could also change the format here (e.g., convert BMP to PNG)
        // args.ResourceFileName = Path.ChangeExtension(args.ResourceFileName, ".png");
    });
```

> **常见问题：** *如果我想把图片嵌入而不是保存呢？*  
> 只需跳过回调或在回调中设置 `args.OutputFileName = null;`——保存器会自动将图片以 Base64 字符串嵌入。

> **边缘情况：** 某些旧文档会出现重复的图片名称。上面的回调会覆盖之前的文件。为避免冲突，你可以在文件名后追加 GUID：

```csharp
args.OutputFileName = Path.Combine(folder,
    $"{Path.GetFileNameWithoutExtension(args.ResourceFileName)}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}");
```

---

## 第三步：将文档保存为 markdown 并验证已保存的图片

在完整配置好选项后，最后只需一行代码即可将 Markdown 文件及其关联图片写入磁盘。

```csharp
// Step 3: Perform the actual export
string outputPath = @"C:\Exports\MyReport.md";
doc.Save(outputPath, markdownSaveOptions);
```

如果一切顺利，你会看到：

- `MyReport.md` – 源文档的 Markdown 表示。  
- `md-resources/` – 与 .md 文件同级的文件夹，包含所有提取的图片（例如 `image001.png`、`image002.jpg`）。  

**示例 Markdown 片段**（由 Aspose.Words 自动生成）：

```markdown
# Sample Report

Here is an introductory paragraph.

![Sample image](md-resources/image001.png)

More text follows...
```

> **专业提示：** 在 VS Code 或任意 Markdown 预览器中打开生成的 `.md` 文件；由于相对路径与文件夹结构匹配，图片应能即时渲染。

---

## 完整、可运行的示例

下面是一个自包含的控制台程序，你可以将其粘贴到新的 .NET 项目中直接运行。它会创建一个简单的 Word 文档，插入一张图片，然后 **从文档创建 markdown** 并将图片存放在子文件夹中。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample Word document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, this is a test document.");
        builder.InsertImage("sample-image.png"); // Ensure this file exists next to exe

        // 2️⃣ Configure markdown export options (see Step 1 & 2 above)
        var markdownOptions = new MarkdownSaveOptions();
        markdownOptions.ResourceSavingCallback = new IResourceSavingCallback(
            (args) =>
            {
                const string folder = "md-resources/";
                Directory.CreateDirectory(folder);
                args.OutputFileName = Path.Combine(folder, args.ResourceFileName);
            });

        // 3️⃣ Save as markdown (Step 3)
        string outputFolder = Path.Combine(Environment.CurrentDirectory, "output");
        Directory.CreateDirectory(outputFolder);
        string markdownPath = Path.Combine(outputFolder, "ExportedDoc.md");
        doc.Save(markdownPath, markdownOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("📂 Images saved in: md-resources/");
    }
}
```

**运行后你应该看到的输出**：

```
✅ Markdown saved to: C:\MyProject\output\ExportedDoc.md
📂 Images saved in: md-resources/
```

打开 `ExportedDoc.md` —— 图片引用将指向 `md-resources/sample-image.png`，并且在任何 Markdown 查看器中都能正确显示。

---

## 常见变体

| 场景 | 如何调整代码 |
|----------|----------------------|
| **跳过图片导出**（嵌入为 Base64） | 完全省略 `ResourceSavingCallback`，或在回调中设置 `args.OutputFileName = null;`。 |
| **更改图片格式**（例如全部转为 PNG） | 在回调中修改 `args.ResourceFileName`，并在写入前可选地转换流。 |
| **自定义文件夹名称** | 将 `"md-resources/"` 替换为任意相对或绝对路径。 |
| **批量处理多个文档** | 对 `Document` 集合进行循环，复用同一个 `MarkdownSaveOptions` 实例（只需确保每次运行前清空或为文件夹使用唯一名称）。 |

---

## 结论

我们已经演示了 **如何从文档创建 markdown**、**将文档导出为 markdown**，以及 **使用回调方式将图片保存到子文件夹** 的整洁方法。关键要点如下：

- 使用 `MarkdownSaveOptions` 获得对导出的细粒度控制。  
- 实现 `IResourceSavingCallback` 将图片导向专用文件夹，保持 Markdown 的整洁。  
- 同样的模式适用于其他资源类型（SVG、音频）——只需检查 `args.ResourceType`。  

接下来，你可以探索 **使用自定义标题样式保存文档为 markdown**，或将此例程集成到返回 `.md` 文件及其资源 ZIP 包的 ASP.NET Web API 中。无论哪种方式，这些构建块已经在你的工具箱中。

有问题，或发现我们未覆盖的特殊情况？欢迎在下方留言，祝编码愉快！

---

![create markdown from document example](placeholder.png "create markdown from document example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}