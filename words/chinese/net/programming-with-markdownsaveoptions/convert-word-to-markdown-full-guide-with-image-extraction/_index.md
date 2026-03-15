---
category: general
date: 2026-03-14
description: 使用 Aspose.Words 快速将 Word 转换为 Markdown 并从 docx 中提取图像。面向开发者的逐步 C# 示例。
draft: false
keywords:
- convert word to markdown
- extract images from docx
- Aspose.Words C#
- markdown conversion tutorial
- docx image handling
language: zh
og_description: 使用 Aspose.Words 将 Word 转换为 Markdown 并从 docx 中提取图像。遵循本详细指南，轻松完成转换。
og_title: 将 Word 转换为 Markdown – 完整 C# 教程
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: 将 Word 转换为 Markdown——完整指南与图片提取
url: /zh/net/programming-with-markdownsaveoptions/convert-word-to-markdown-full-guide-with-image-extraction/
---

should keep them as is.

Also preserve blockquote formatting >.

Now produce final answer.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 将 Word 转换为 Markdown – 完整 C# 教程

是否曾经需要 **将 Word 转换为 Markdown**，但又不确定如何保留嵌入的图片？你并不孤单。许多开发者都会遇到文本能够成功转换，而图片却消失不见的难题。好消息是，只需几行 C# 代码和强大的 Aspose.Words 库，你就可以 **将 Word 转换为 Markdown** *并且* **从 docx 中提取图片**，一次性完成。

在本教程中，我们将逐步演示所有必需的操作：从安装 NuGet 包、加载 `.docx` 文件、配置 markdown 保存器，到编写回调将每张图片保存到自定义文件夹并重新写入图片链接。完成后，你将拥有一个可直接使用的 Markdown 文件以及一个整洁的 `resources` 目录，里面存放了原始 Word 文档中的所有图片。

## 您将学习的内容

- 如何在 C# 项目中设置 Aspose.Words for .NET。  
- 完整代码，能够 **将 Word 转换为 Markdown** 并保留图片。  
- 为什么 `ResourceSavingCallback` 对 **从 docx 中提取图片** 至关重要。  
- 常见陷阱（例如路径分隔符、文件名重复）以及规避方法。  
- 快速验证步骤，确保生成的 Markdown 正确渲染。

### 前置条件

| Requirement | Reason |
|-------------|--------|
| .NET 6.0 或更高（或 .NET Framework 4.7+） | Aspose.Words 同时支持两者；更新的运行时性能更佳。 |
| Visual Studio 2022（或任意 C# IDE） | 便于调试和管理 NuGet 包。 |
| 用于 NuGet 还原的网络连接 | 库会从官方源获取。 |
| 包含文本 **和** 图片的示例 `input.docx` | 以便演示图片提取过程。 |

无需额外的第三方工具——Aspose.Words 已经在内部完成所有工作。

---

## 步骤 1：通过 NuGet 安装 Aspose.Words

首先，将 Aspose.Words 包添加到项目中。打开 **Package Manager Console** 并运行：

```powershell
Install-Package Aspose.Words
```

或者使用 UI：右键点击项目 → *Manage NuGet Packages* → 搜索 “Aspose.Words” → 点击 **Install**。这会把核心 DLL 和后续需要的 `Saving` 命名空间引入项目。

> **专业提示：** 固定版本（例如 `22.12.0`）可以避免库自动更新时出现意外的破坏性更改。

---

## 步骤 2：加载源 Word 文档

库准备就绪后，我们即可加载 `.docx` 文件。使用指向源文档的绝对路径或相对路径均可。

```csharp
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file. Replace the placeholder with your actual path.
Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

> **为什么重要：** `Document` 会解析整个 Word 包，让我们能够访问段落、表格以及后续要提取的隐藏图片部分。

---

## 步骤 3：创建 Markdown 保存选项

Aspose.Words 提供了 `MarkdownSaveOptions` 类，可让我们微调转换行为。这里先实例化它，后续再挂载回调。

```csharp
// Instantiate the options object.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
```

你可以调整属性，例如将 `ExportImagesAsBase64` 设置为 `false`（因为我们希望图片为独立文件），或根据需要开启 `ExportHeadersFooters` 以在 Markdown 中保留页眉页脚。

---

## 步骤 4：配置 ResourceSavingCallback – 从 DOCX 中提取图像

这是本教程的核心。`ResourceSavingCallback` 会在保存器准备写入 **每个资源**（图片、字体等）时触发。通过自定义处理器，我们决定图片保存位置以及 Markdown 文件如何引用它们。

```csharp
mdOptions.ResourceSavingCallback = new ResourceSavingCallback(
    (sender, args) =>
    {
        // 1️⃣ Define the folder where we’ll dump extracted pictures.
        string imageFolder = @"YOUR_DIRECTORY\resources\";

        // 2️⃣ Ensure the folder exists – create it on the fly.
        Directory.CreateDirectory(imageFolder);

        // 3️⃣ Preserve the original filename (e.g., Image1.png).
        string imageFileName = Path.GetFileName(args.FileName);
        string targetPath   = Path.Combine(imageFolder, imageFileName);

        // 4️⃣ Write the image stream to disk.
        using (FileStream fs = new FileStream(targetPath, FileMode.Create))
        {
            args.Stream.CopyTo(fs);
        }

        // 5️⃣ Tell the Markdown generator to use a relative path.
        //    This is the step that **extract images from docx** correctly.
        args.ResourceFileName = $"resources/{imageFileName}";
    });
```

### 这段代码的作用

1. **创建** `resources` 子文件夹（如果尚不存在）。  
2. **复制** 每个传入的图片流到该文件夹，并保留原始文件名以避免混淆。  
3. **更新** Markdown 链接（`![alt](resources/Image1.png)`），使阅读器在渲染文件时能够显示图片。

> **边缘情况：** 若两个图片共享相同文件名，后者会覆盖前者。为防止冲突，可在保存前为文件名前缀添加 GUID，或使用 `Path.GetUniqueFileName`（自定义帮助方法）生成唯一名称。

---

## 步骤 5：将文档保存为 Markdown

回调配置完成后，最后一步只需一行代码即可写出 Markdown 文件。

```csharp
// Choose the output path for the Markdown file.
string markdownPath = @"YOUR_DIRECTORY\output.md";

doc.Save(markdownPath, mdOptions);
```

执行完此调用后，你将得到：

- `output.md`，其中包含 Markdown 文本以及类似 `![Image1](resources/Image1.png)` 的图片引用。  
- 一个 `resources` 文件夹，里面已填充原始 `.docx` 中提取的所有图片。

---

## 步骤 6：验证结果

在任意 Markdown 查看器（VS Code、GitHub、Typora）中打开 `output.md`。你应当能看到原始文档的标题、列表以及 **正确渲染的图片**。若发现图片缺失：

1. 检查 `resources` 文件夹中是否存在对应文件。  
2. 确认 Markdown 中的相对路径 (`resources/<filename>`) 与文件夹名称完全一致（Linux 上区分大小写）。  
3. 验证图片文件未损坏——直接在图片查看器中打开检查。

---

## 完整示例代码

下面是完整的、可直接运行的程序示例。将 `YOUR_DIRECTORY` 占位符替换为实际的文件夹路径。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class WordToMarkdown
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Load the source Word document.
        // -------------------------------------------------
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // -------------------------------------------------
        // 2️⃣ Prepare Markdown save options.
        // -------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // Export images as separate files, not Base64.
            ExportImagesAsBase64 = false
        };

        // -------------------------------------------------
        // 3️⃣ Set up the callback to **extract images from docx**.
        // -------------------------------------------------
        mdOptions.ResourceSavingCallback = new ResourceSavingCallback(
            (sender, args) =>
            {
                string imageFolder = @"YOUR_DIRECTORY\resources\";
                Directory.CreateDirectory(imageFolder);

                string imageFileName = Path.GetFileName(args.FileName);
                string targetPath = Path.Combine(imageFolder, imageFileName);

                using (FileStream fs = new FileStream(targetPath, FileMode.Create))
                {
                    args.Stream.CopyTo(fs);
                }

                // Update the reference used inside the Markdown file.
                args.ResourceFileName = $"resources/{imageFileName}";
            });

        // -------------------------------------------------
        // 4️⃣ Save as Markdown.
        // -------------------------------------------------
        string outputPath = @"YOUR_DIRECTORY\output.md";
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("Conversion complete! Check output.md and the resources folder.");
    }
}
```

**预期输出：** 打开 `output.md`，你会看到类似如下内容：

```markdown
# Sample Title

Here is some introductory text.

![Image1](resources/Image1.png)

More paragraphs…

![Diagram](resources/Diagram.jpg)
```

所有图片都会与文本并排显示，效果与原始 Word 文件完全一致。

---

## 常见问题与注意事项

**Q: 能在提取过程中更改图片格式吗？**  
A: 可以。在回调内部，你可以在写出之前重新编码流（例如转为 PNG）。使用 `System.Drawing` 或 `ImageSharp` 操作 `args.Stream` 即可。

**Q: 如果 Word 文档包含 SVG 或 EMF 图片怎么办？**  
A: Aspose.Words 默认会将大多数矢量格式转换为栅格 PNG。如果需要保留原始矢量，可设置 `mdOptions.ExportImageResolution` 并相应处理流。

**Q: 这在 Linux 上的 .NET Core 能运行吗？**  
A: 完全可以。只需确保 `resources` 路径使用正斜杠（`/`）或如示例中使用 `Path.Combine`。记住 Linux 文件系统区分大小写，保持文件夹名称一致即可。

**Q: 如何抑制脚注或评论？**  
A: 在保存前调整 `mdOptions.ExportFootnotes` 或 `mdOptions.ExportComments` 属性即可。

---

## 结论

我们已经完整演示了一个 **端到端的将 Word 转换为 Markdown** 方案，并可靠地 **从 docx 中提取图片**。通过利用 Aspose.Words 的 `MarkdownSaveOptions` 与 `ResourceSavingCallback`，你可以细粒度地控制文本转换和图片处理。代码自包含、跨所有 .NET 平台运行，并可轻松嵌入现有流水线，几乎不需要额外工作。

准备好下一步了吗？可以考虑批量转换、将此逻辑集成到 ASP.NET API，或扩展回调为每张提取的图片生成缩略图。只要核心转换已稳固，后续的可能性无限。

---

![将 Word 转换为 Markdown 示例](convert-word-to-markdown.png "将 Word 转换为 Markdown 示例")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}