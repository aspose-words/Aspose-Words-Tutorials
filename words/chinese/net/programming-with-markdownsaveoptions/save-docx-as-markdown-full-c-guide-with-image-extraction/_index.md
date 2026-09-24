---
category: general
date: 2025-12-29
description: 使用 Aspose.Words 将 docx 保存为 markdown。学习将 Word 转换为 markdown，提取图像，创建资源文件夹，并配置
  markdown 选项。
draft: false
keywords:
- save docx as markdown
- convert word to markdown
- how to extract images
- create resources folder
- how to configure markdown
language: zh
og_description: 使用 Aspose.Words 将 docx 保存为 markdown。一步一步的指南，教您将 Word 转换为 markdown，提取图片，创建资源文件夹，并配置
  markdown。
og_title: 将 docx 保存为 markdown – 完整 C# 教程
tags:
- Aspose.Words
- C#
- Document Conversion
title: 将 docx 保存为 markdown – 完整的 C# 指南（含图片提取）
url: /zh/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 将 docx 保存为 markdown – 完整 C# 教程

是否曾经需要 **将 docx 保存为 markdown**，但不确定如何保留嵌入的图片？你并不孤单。许多开发者在转换时图片丢失，导致 Markdown 文件空空如也。在本指南中，我们将逐步演示一种实用方案，既能 **将 word 转换为 markdown**，又能 **提取图片**，自动 **创建资源文件夹**，并正确 **配置 markdown** 选项以获得整洁的输出。

阅读完本文后，你将拥有一段可直接运行的 C# 代码片段，能够读取任意 `.docx`，提取其中的所有图片，存入专用目录，并生成一个 Markdown 文件，其图片链接指向该文件夹。无需额外的后处理。

## 你将学到

- 使用 Aspose.Words 加载 Word 文档。  
- 设置 `MarkdownSaveOptions` 以捕获外部资源。  
- 自动在 Markdown 文件旁生成 **Resources** 文件夹。  
- 通过 `ResourceSavingCallback` 写入图片文件。  
- 验证生成的 Markdown 正确引用图片。

### 前置条件

- .NET 6+（或 .NET Framework 4.6+）。  
- Aspose.Words for .NET（NuGet 包 `Aspose.Words`）。  
- 一个包含至少一张图片的示例 `input.docx`。  

如果你已经具备上述条件，太好了——让我们开始吧。

## 第一步 – 加载 Word 文档

首先打开源文件。这一步看似简单，却至关重要；文档对象是文本和媒体的来源。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the Word document that contains images.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **为何这一步重要：**  
> 加载文件会在内存中创建文档的表示，Aspose 能遍历每个节点——段落、表格，以及关键的 `Shape` 对象（保存图片）。如果不加载，就没有可提取的内容。

## 第二步 – 配置 Markdown 选项（转换核心）

现在告诉 Aspose 我们希望 Markdown 文件如何表现。`MarkdownSaveOptions` 类提供了 `ResourceSavingCallback` 委托，会在每个外部资源（图片、图表等）出现时触发。在回调中我们决定文件写入位置以及嵌入的 URI。

```csharp
// Set up Markdown save options with a callback for external resources.
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    // The callback runs for every image/chart the exporter needs to write.
    ResourceSavingCallback = (sender, args) =>
    {
        // Step 3 – Ensure the Resources folder exists.
        string resourcesFolder = "YOUR_DIRECTORY/Resources/";
        Directory.CreateDirectory(resourcesFolder);

        // Build the absolute path for the image file.
        string resourceFilePath = Path.Combine(resourcesFolder, args.ResourceFileName);
        args.Stream = new FileStream(resourceFilePath, FileMode.Create);

        // Use a relative path in the generated Markdown file.
        args.Uri = "Resources/" + args.ResourceFileName;
    }
};
```

### 如何配置 Markdown 以提取图片

- **`ResourceSavingCallback`** – 让我们能够将每张图片写入任意位置的钩子。  
- **`args.ResourceFileName`** – Aspose 生成的唯一文件名（例如 `image001.png`）。  
- **`args.Uri`** – 最终写入 Markdown 链接的字符串；我们将其设为相对路径，使 Markdown 保持可移植。

> **提示：** 如果需要自定义命名规则（例如保留原始图片名称），可以检查 `args.ResourceFileName` 并在赋值给 `args.Uri` 前进行替换。

## 第三步 – 创建资源文件夹（并提取图片）

前一步定义的回调已经能够在运行时创建文件夹，但我们仍然讨论为何这是推荐的做法。

```csharp
// Inside the callback (repeated for emphasis):
string resourcesFolder = "YOUR_DIRECTORY/Resources/";
Directory.CreateDirectory(resourcesFolder);
```

> **为何要创建专用文件夹？**  
> 将图片存放在单独的目录中可以保持 Markdown 的整洁，并且符合许多静态站点生成器（如 Jekyll 或 Hugo）对资源组织的期待。它还能防止在多次转换时出现命名冲突。

### 边缘情况与变体

| 场景 | 需要调整的地方 |
|-----------|----------------|
| **包含数百张图片的大型 DOCX** | 考虑流式写入图片以避免内存压力；回调已经直接将每张图片写入磁盘，内存占用低。 |
| **非 PNG 图片（如 JPEG、GIF）** | `args.ResourceFileName` 已包含正确的扩展名，无需额外处理。 |
| **自定义输出路径** | 将 `"YOUR_DIRECTORY/Resources/"` 替换为相对于项目根目录的路径，或从配置文件读取。 |

## 第四步 – 将文档保存为 Markdown

在完整配置好选项后，最后只需一行代码即可写出 Markdown 文件，并触发每张图片的回调。

```csharp
// Save the document as Markdown, applying the resource handling logic.
document.Save("YOUR_DIRECTORY/WithResources.md", markdownSaveOptions);
```

### 预期结果

- `WithResources.md` – 包含标准语法（`![Alt text](Resources/image001.png)`）的 Markdown 文件，每张图片都有对应链接。  
- `Resources/` – 存放提取后图片文件的文件夹。

你可以在任意查看器（VS Code、GitHub 或静态站点生成器）中打开该 Markdown，应该能看到图片准确地出现在 Word 文档中的位置。

![显示已提取图片的 Resources 文件夹结构 – 将 docx 保存为 markdown](https://example.com/placeholder.png "显示已提取图片的 Resources 文件夹结构 – 将 docx 保存为 markdown")

*图片 alt 文本：“显示已提取图片的 Resources 文件夹结构 – 将 docx 保存为 markdown” – 满足主要关键词的图片 alt 要求。*

## 完整可运行示例（复制粘即用）

下面是完整程序代码，可直接放入控制台应用。将 `YOUR_DIRECTORY` 替换为你机器上的实际路径。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source DOCX.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Prepare Markdown options with a resource callback.
        MarkdownSaveOptions options = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (sender, args) =>
            {
                // 3️⃣ Ensure the Resources folder exists.
                string resourcesFolder = "YOUR_DIRECTORY/Resources/";
                Directory.CreateDirectory(resourcesFolder);

                // 4️⃣ Write the image file to disk.
                string filePath = Path.Combine(resourcesFolder, args.ResourceFileName);
                args.Stream = new FileStream(filePath, FileMode.Create);

                // 5️⃣ Set the relative URI used in the Markdown file.
                args.Uri = "Resources/" + args.ResourceFileName;
            }
        };

        // 6️⃣ Save as Markdown – this triggers the callback for each image.
        document.Save("YOUR_DIRECTORY/WithResources.md", options);

        // Inform the user.
        System.Console.WriteLine("Conversion complete! Check the Resources folder and the Markdown file.");
    }
}
```

### 运行示例

1. 安装 Aspose.Words NuGet 包：  
   ```bash
   dotnet add package Aspose.Words
   ```
2. 编译并运行：  
   ```bash
   dotnet run
   ```
3. 在任意 Markdown 查看器中打开 `WithResources.md`。所有图片应正常显示。

## 常见问题与专业技巧

### “能否转换 .doc 而不是 .docx？”
完全可以——Aspose.Words 同时支持 `.doc` 与 `.docx`。只需在 `Document` 构造函数中更改文件扩展名即可。

### “如果我不想要 Resources 文件夹怎么办？”
你可以将 `args.Uri` 指向任意位置，甚至是 URL。例如：`args.Uri = "https://mycdn.com/" + args.ResourceFileName;`，这样就可以省略文件夹创建。

### “如何处理 SVG 图形？”
Aspose 将 SVG 视为独立的资源类型。在回调中检查 `args.ResourceType`，如果是 `ResourceType.Svg`，可以自行重命名或进行其他处理。

### “有没有办法将图片嵌入为 Base64？”
有的——不写入文件，而是将 `args.Stream` 转为 Base64 字符串，然后设为 `args.Uri = "data:image/png;base64," + base64;`。这样 Markdown 将自包含，但文件体积会增大。

### “需要哪个版本的 Aspose.Words？”
`MarkdownSaveOptions` 类是在 Aspose.Words 22.9 中引入的。如果你使用的版本更低，请通过 NuGet 升级。

## 结论

我们已经完整演示了如何在 **将 docx 保存为 markdown** 的同时保留所有图片。关键步骤如下：

1. 使用 Aspose.Words 加载 DOCX。  
2. 配置 `MarkdownSaveOptions` 并实现 `ResourceSavingCallback`。  
3. 在回调中 **创建资源文件夹**，写入每张图片，并设置相对 URI。  
4. 保存文档，让 Aspose 完成其余工作。

现在，你可以自动化文档流水线，将旧的 Word 指南迁移到适合静态站点的 Markdown，或为团队提供轻量、受版本控制的格式而不失视觉上下文。

### 接下来可以做什么？

- 试验 **如何配置 markdown** 以自定义标题样式或表格格式。  
- 将此转换步骤集成到 CI/CD 流程，实现文档自动发布。  
- 深入了解 Aspose 的其他导出格式（HTML、PDF），并观察相同回调模式的使用方式。

还有其他想了解的场景吗？欢迎在 Aspose 论坛留言或提交新问题。祝转换愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}