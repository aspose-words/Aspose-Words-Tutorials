---
category: general
date: 2026-03-13
description: 将 Word 保存为 Markdown，并在转换 DOCX 为 Markdown 的同时提取图像。了解如何使用 Aspose.Words
  在 C# 中从 DOCX 中提取图像。
draft: false
keywords:
- save word as markdown
- convert docx to markdown
- extract images from docx
- how to extract images
- extract embedded images word
language: zh
og_description: 在 C# 中将 Word 保存为 Markdown。本指南展示如何将 DOCX 转换为 Markdown 并提取图片，提供可直接运行的解决方案。
og_title: 将 Word 保存为 Markdown – 转换 DOCX 并提取图片
tags:
- Aspose.Words
- C#
- Markdown
title: 将 Word 保存为 Markdown – 完整指南：转换 DOCX 并提取图片
url: /zh/net/programming-with-markdownsaveoptions/save-word-as-markdown-complete-guide-to-convert-docx-and-ext/
---

with the right pictures!"

Now we need to ensure we preserve all markdown formatting.

Let's produce the translated content.

We'll keep shortcodes at top and bottom unchanged.

Let's start.

We need to output only the translated content, no explanations.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 将 Word 保存为 Markdown – 完整的 DOCX 转换与图片提取指南

是否曾经想要 **将 Word 保存为 markdown**，却不确定如何保留图片？你并不孤单。许多开发者在 DOCX 文件中嵌入了图形，而简单的转换器会生成一堆损坏的链接。

在本教程中，我们将演示一种实用的方案，**将 DOCX 转换为 markdown** **并** 将每张图片提取到你可控制的文件夹中。完成后，你将拥有一个干净的 `.md` 文件、一个整洁的 `markdown_resources` 目录，以及对回调方式为何是处理资源最可靠方法的深入理解。

> **小贴士：** 同样的模式也适用于 CSS、字体或 Aspose.Words 在保存操作期间可能输出的任何外部资源。

![将 Word 保存为 Markdown 的转换流程图](conversion-diagram.png "转换流程图")

## 你将学到的内容

- 如何使用 Aspose.Words for .NET **将 Word 保存为 markdown**。
- 在保留图片的前提下 **将 docx 转换为 markdown** 的完整步骤。
- 一个可复用的 `IResourceSavingCallback` 实现，**从 docx 中提取图片**。
- 常见陷阱（例如文件名重复、文件夹缺失）以及规避方法。
- 生成的 markdown 长什么样，图片会保存到哪里。

你需要最近版本的 **Aspose.Words for .NET**（本指南在 24.12 版本上测试通过）以及 .NET 6+ 运行时。无需其他第三方库。

---

## 前置条件

| Requirement | Why it matters |
|-------------|----------------|
| Aspose.Words for .NET（NuGet `Aspose.Words`） | 提供 `Document` 类和 `MarkdownSaveOptions`。 |
| .NET 6 或更高版本 | 确保 `using` 语句等语言特性无需额外 ceremony。 |
| 包含图片的 DOCX 文件（例如 `Images.docx`） | 我们要转换并从中提取图片的源文件。 |
| 对输出文件夹的写入权限 | 回调会写入图片文件；没有权限会抛出异常。 |

如果你已经具备这些条件，太好了——让我们开始吧。

---

## 第一步：加载源 DOCX – Save Word as Markdown 的起点

首先打开 Word 文档。Aspose.Words 会将文件读取到内存中，保留所有内部结构（段落、表格、图片等）。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the DOCX that contains images.
Document sourceDoc = new Document("YOUR_DIRECTORY/Images.docx");
```

> **为什么这很重要：** 预先加载文件可以让我们检查其内容（例如 `sourceDoc.GetChildNodes(NodeType.Shape, true)`），在调试缺失图片时非常有帮助。

---

## 第二步：使用图片保存回调配置 Markdown 保存选项

当 Aspose.Words 写入 markdown 文件时，可能需要存储外部资源（如图片）。通过附加 `ResourceSavingCallback`，我们可以完全控制这些文件的保存位置和文件名。

```csharp
// Prepare markdown options and tell Aspose.Words to use our callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // The callback fires for every image, CSS file, etc.
    ResourceSavingCallback = new ImageSavingCallback()
};
```

> **如何提取图片：** 回调会收到一个 `ResourceSavingArgs` 实例，其中包含图片流、原始文件名和索引。我们可以重命名文件、移动位置，甚至完全跳过保存。

---

## 第三步：将文档保存为 Markdown – Save Word as Markdown 的核心

现在调用 `Document.Save`。库会为每张图片调用我们的回调，将图片文件写入指定位置，最后输出带有正确 `![]()` 链接的 markdown 文件。

```csharp
// Execute the conversion. The markdown file will reference the extracted images.
sourceDoc.Save("YOUR_DIRECTORY/DocWithImages.md", mdOptions);
```

此时在 `YOUR_DIRECTORY` 中你应该看到两样东西：

1. `DocWithImages.md` – 原始 Word 文件的 markdown 表示。
2. `markdown_resources` 文件夹 – 包含 `img_0.png`、`img_1.jpg` … 等文件的集合。

---

## 第四步：实现图片保存回调 – 如何从 DOCX 中提取图片

下面是完整的回调类实现。它会在需要时创建文件夹，生成唯一文件名，写入图片流，然后通过设置 `args.FileName` 告诉 Aspose.Words 使用我们的文件名，并通过 `args.Stream = null` 跳过默认保存。

```csharp
public class ImageSavingCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Ensure the resources folder exists.
        string resourcesFolder = "YOUR_DIRECTORY/markdown_resources";
        Directory.CreateDirectory(resourcesFolder);

        // 2️⃣ Build a unique name – img_0.png, img_1.jpg, etc.
        string imageFileName = Path.Combine(
            resourcesFolder,
            $"img_{args.ImageIndex}{Path.GetExtension(args.FileName)}");

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = new FileStream(imageFileName, FileMode.Create))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Tell the markdown writer to reference the new name.
        args.FileName = Path.GetFileName(imageFileName);
        args.Stream = null; // Prevent default saving – we already handled it.
    }
}
```

### 为什么这样可行

- **确定性的文件名** – 使用 `args.ImageIndex` 可保证即使原始 DOCX 中有重复名称也能唯一。
- **文件夹隔离** – 所有提取的资源都放在 `markdown_resources` 下，保持项目整洁。
- **性能** – 直接复制流，无额外缓冲或图像处理，转换速度快。

---

## 第五步：验证输出 – Markdown 的实际效果

在任意编辑器中打开 `DocWithImages.md`，你应该看到类似如下内容：

```markdown
# Sample Document

Here is an illustration:

![](markdown_resources/img_0.png)

Another picture appears below:

![](markdown_resources/img_1.jpg)
```

如果在支持相对路径的查看器（VS Code 预览、GitHub 等）中打开 markdown，图片将正确渲染。

### 快速检查

```bash
# On Linux/macOS
cat YOUR_DIRECTORY/DocWithImages.md | grep -E '\!\[.*\]\(markdown_resources/img_.*\)'
```

每张图片应对应一行；行数应与 `Images.docx` 中嵌入的图片数量相匹配。

---

## 常见问题与边缘情况

### 如果 DOCX 包含 SVG 或 EMF 图形怎么办？

Aspose.Words 会自动将大多数矢量格式转换为 PNG。回调仍会收到流，文件扩展名为 `.png`。无需额外代码。

### 如何更改输出文件夹的名称？

只需修改 `ImageSavingCallback` 中的 `resourcesFolder` 变量。记得保持相对引用不变（`args.FileName = Path.GetFileName(imageFileName)`），这样 markdown 链接仍然正确。

### 能否跳过保存某些图片（例如非常大的）？

可以。在回调内部检查 `args.Stream.Length`。如果超过阈值，你可以将其重命名为占位符，或设置 `args.Cancel = true` 完全省略。

```csharp
if (args.Stream.Length > 5 * 1024 * 1024) // >5 MB
{
    args.Cancel = true; // Image will be omitted from markdown.
    return;
}
```

### 这种方式能用于 CSS 等其他资源类型吗？

完全可以。回调会针对任何外部资源触发。你可以根据 `args.ContentType` 对 CSS、字体或视频等进行不同处理。

---

## 完整可运行示例 – 复制粘贴即用

下面是一段自包含的程序代码，可直接放入控制台应用。将 `YOUR_DIRECTORY` 占位符替换为机器上的绝对或相对路径即可。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

namespace DocxToMarkdownDemo
{
    class Program
    {
        static void Main()
        {
            // ① Load the source DOCX that contains images.
            Document sourceDoc = new Document("YOUR_DIRECTORY/Images.docx");

            // ② Configure markdown options with our callback.
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new ImageSavingCallback()
            };

            // ③ Save as markdown – images will be stored by the callback.
            sourceDoc.Save("YOUR_DIRECTORY/DocWithImages.md", mdOptions);

            // ④ Inform the user.
            System.Console.WriteLine("Conversion complete! Check the markdown file and the markdown_resources folder.");
        }
    }

    // ⑤ Callback that extracts each image to a custom folder.
    public class ImageSavingCallback : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string resourcesFolder = "YOUR_DIRECTORY/markdown_resources";
            Directory.CreateDirectory(resourcesFolder);

            string imageFileName = Path.Combine(
                resourcesFolder,
                $"img_{args.ImageIndex}{Path.GetExtension(args.FileName)}");

            using (FileStream fileStream = new FileStream(imageFileName, FileMode.Create))
            {
                args.Stream.CopyTo(fileStream);
            }

            args.FileName = Path.GetFileName(imageFileName);
            args.Stream = null; // Skip default saving.
        }
    }
}
```

运行程序，打开生成的 markdown，你会看到所有图片恰好出现在原始 Word 文件中的位置。

---

## 结论

我们已经完整演示了 **如何将 Word 保存为 markdown** 并 **使用回调模式从 docx 中提取图片**。关键在于 `IResourceSavingCallback` 为每个外部文件提供了完全的控制，使转换在任何生产流水线中都可靠。

在一个可复制的示例中，我们：

1. 加载了包含图片的 DOCX。
2. 使用自定义 `ImageSavingCallback` 配置了 `MarkdownSaveOptions`。
3. 将文档保存为 markdown，让回调将每张图片写入 `markdown_resources`。
4. 验证了输出并讨论了如何针对边缘情况进行调整。

接下来你可以：

- 通过遍历目录批量 **将 docx 转换为 markdown**。
- 根据原始标题为图片重命名，以提升 SEO。
- 将 markdown 文件夹移动到 Hugo、Jekyll 等静态站点生成器的内容树中，实现自动化发布。
- 扩展回调以提取嵌入的字体或 CSS，实现完整的自包含 HTML 导出。

尽情实验吧——比如将图片命名方案改为 GUID 以实现绝对唯一，或添加日志行记录每个保存的资源。一旦掌握了保存管道，可能性无限。

祝编码愉快，愿你的 markdown 总能正确渲染图片！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}