---
category: general
date: 2026-01-03
description: 一次性将 Word 转换为 Markdown 并将图像嵌入为 base64。了解如何将 Word 保存为 Markdown、从 Word
  生成 Markdown，以及使用 base64 图像数据 URI。
draft: false
keywords:
- convert word to markdown
- embed images as base64
- save word as markdown
- base64 image data uri
- generate markdown from word
language: zh
og_description: 将 Word 转换为 Markdown，并将图像嵌入为 base64 数据 URI。此一步一步的教程展示了如何将 Word 保存为
  Markdown，以及如何从 Word 生成 Markdown。
og_title: 将 Word 转换为 Markdown – Base64 图像嵌入指南
tags:
- Aspose.Words
- C#
- Markdown
title: 将 Word 转换为 Markdown – 将图片嵌入为 Base64
url: /zh/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 将 Word 转换为 Markdown – 将图片嵌入为 Base64

是否曾经想要 **将 Word 转换为 markdown**，却总是被图片卡住？你并不孤单。Word 喜欢把图片存为独立文件，而 markdown 更倾向于使用 `data:image/...;base64,` 这种字符串，将所有内容整洁地保存在单个文件中。  

在本教程中，我们将一步步演示一个完整、可直接运行的方案，**将 Word 保存为 markdown**、**将图片嵌入为 base64**，并展示如何使用 Aspose.Words for .NET **从 Word 生成 markdown**。完成后，你将得到一个单独的 `.md` 文件，渲染效果与原始文档完全一致——无需外部图片文件夹。

## 你需要准备的环境

- **.NET 6.0 或更高**（任何能够引用 NuGet 包的环境）
- **Aspose.Words for .NET**（免费试用版足以进行测试）
- 一个包含几张图片的简单 `.docx` 文件（我们称之为 `input.docx`）
- 你喜欢的 IDE（Visual Studio、Rider、VS Code——任选其一）

如果这些都已经就绪，太好了——直接开始吧。如果还没有，安装 NuGet 包只需一行代码：

```bash
dotnet add package Aspose.Words
```

## 第一步：加载 Word 文档 — **convert word to markdown** 的起点

首先需要把 `.docx` 加载到内存中。转换的魔法就从这里开始。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file that contains the images.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **为什么这一步很重要：**  
> 加载文档后，Aspose 能够完整访问文本、样式以及所有嵌入的资源。没有这一步，就没有可转换的内容。

## 第二步：使用资源保存回调设置 MarkdownSaveOptions

Aspose 允许你拦截每一个本应写入磁盘的资源（如图片）。通过提供自定义的 `IResourceSavingCallback`，我们可以将默认的文件保存方式替换为 **base64 图片 data uri**。

```csharp
// Configure Markdown save options so that images become Base64 URIs.
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceHandler()
};
```

### 自定义处理器 – 将图片转换为 Base64

下面是完整实现。请注意我们检查 `args.ResourceType == ResourceType.Image`，随后：

1. 将图片写入 `MemoryStream`。
2. 将字节数组转换为 Base64 字符串。
3. 构造 `data:image/jpeg;base64,` URI 并赋值给 `args.Uri`。

```csharp
// Custom handler that converts each image resource to a Base64 data URI.
class MyResourceHandler : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only process images – leave other resources untouched.
        if (args.ResourceType == ResourceType.Image)
        {
            // Prepare an in‑memory stream for the image.
            using (MemoryStream ms = new MemoryStream())
            {
                // Save the image using default JPEG options.
                args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                // Build the Base64 data URI.
                string base64 = Convert.ToBase64String(ms.ToArray());
                args.Uri = $"data:image/jpeg;base64,{base64}";
                // No need to keep the stream open after we set the URI.
                args.KeepResourceStreamOpen = false;
            }
        }
    }
}
```

> **专业提示：** 如果源 Word 使用 PNG， 将 `ImageSaveOptions.DefaultJpeg` 替换为 `ImageSaveOptions.DefaultPng`，并相应地修改 MIME 类型为 `image/png`。

## 第三步：将文档保存为 Markdown – **save word as markdown** 的最终步骤

回调准备就绪后，实际保存只需一行代码。

```csharp
// Save the document to a Markdown file. Images are already embedded.
document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
```

在任意 markdown 查看器（VS Code 预览、GitHub 等）中打开 `output.md`，你会看到文本与原始 Word 完全一致，图片也会以内联方式显示，无需单独的图片文件。

## 预期输出

```markdown
# Sample Title

Here’s a paragraph that originally lived in Word.

![Embedded Image](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxISEhU...
```

`![Embedded Image]` 行是一个 **base64 image data uri**——整个图片就在这里被编码。没有额外文件夹，也没有失效链接。

## 边缘情况及处理方法

| 情况 | 处理办法 |
|-----------|------------|
| **大图片** – Base64 会使体积膨胀约 33% | 考虑在转换前先缩放：`args.ResourceData.Save(ms, new ImageSaveOptions { ImageResolution = 72 })`。 |
| **非 JPEG 图片**（PNG、GIF） | 通过 `args.ResourceData.ImageType` 检测原始格式，并设置正确的 MIME 类型（`image/png`、`image/gif`）。 |
| **超长文档**（上百张图片） | 注意内存使用；如果内存不足，可暂时将每张图片流式写入磁盘。 |
| **需要单独的图片文件**（例如用于静态站点） | 在回调中对想保留为文件的图片返回 `false`，让 Aspose 将它们写入指定文件夹。 |

## 常见问题（提前解答）

- **这能处理 .doc 文件吗？** 能——Aspose.Words 同样可以加载传统 `.doc` 文件，只需 `new Document("myfile.doc")` 即可。
- **表格和脚注怎么办？** Markdown 导出器完全支持它们。表格会转换为 markdown 表格，脚注会变为内联引用。
- **可以更改 markdown 的方言吗？** `MarkdownSaveOptions` 提供 `MarkdownVersion` 属性（CommonMark、GitHub 等），在保存前设置即可满足特定语法需求。

## 完整、可直接运行的示例

下面是可以直接复制到控制台应用中的完整程序。它包含所有 using 语句、处理器类以及错误处理。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                // 1️⃣ Load the source Word document.
                Document doc = new Document("YOUR_DIRECTORY/input.docx");

                // 2️⃣ Prepare Markdown options with our custom image handler.
                MarkdownSaveOptions options = new MarkdownSaveOptions
                {
                    ResourceSavingCallback = new MyResourceHandler()
                };

                // 3️⃣ Save as Markdown – images become Base64 URIs.
                string outputPath = "YOUR_DIRECTORY/output.md";
                doc.Save(outputPath, options);

                Console.WriteLine($"✅ Success! Markdown saved to {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Conversion failed: {ex.Message}");
            }
        }
    }

    // Custom callback that embeds images as Base64 data URIs.
    class MyResourceHandler : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType == ResourceType.Image)
            {
                using (MemoryStream ms = new MemoryStream())
                {
                    // Preserve original format if you prefer PNG/GIF.
                    args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                    string base64 = Convert.ToBase64String(ms.ToArray());
                    args.Uri = $"data:image/jpeg;base64,{base64}";
                    args.KeepResourceStreamOpen = false;
                }
            }
        }
    }
}
```

运行程序，打开生成的 `output.md`，你会看到 Word 文件的完美 markdown 副本——**convert word to markdown** 从未如此简单。

## 小结

我们从 **convert word to markdown** 时图片内联的问题出发。通过加载文档、配置 `MarkdownSaveOptions` 回调并保存文件，实现了一个整洁的 **save word as markdown** 方案，生成了 **base64 image data uri** 字符串。现在你也掌握了 **embed images as base64** 的方法、边缘情况的处理以及不同图片类型的调优技巧。

## 接下来可以做什么？

- **生成 HTML 而非 markdown** – 将 `MarkdownSaveOptions` 替换为 `HtmlSaveOptions`，复用相同的回调。
- **批量转换多个文件** – 将逻辑包装在 `foreach` 循环中，遍历文件夹。
- **集成到 CI 流水线** – 自动为静态站点生成文档。

欢迎随意实验，调节图片质量，甚至实现自定义资源处理（例如上传图片到 CDN 并插入 URL）。当 Aspose.Words 与一点点 C# 创意结合时，可能性无限。

祝编码愉快，愿你的 markdown 始终完美渲染！ 

![将 Word 转换为 markdown 流程图 – 将图片嵌入为 Base64](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNjAwIiBoZWlnaHQ9IjQwMCIgdmlld0JveD0iMCAwIDYwMCA0MDAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PHJlY3Qgd2lkdGg9IjYwMCIgaGVpZ2h0PSI0MDAiIGZpbGw9IiNmZmYiIHN0cm9rZT0iI2NjYyIgLz48dGV4dCB4PSI1MCIgeT0iMjAwIiBmb250LXNpemU9IjM2IiBmaWxsPSIjMDAwIj5JbWFnZSBJbWFnZSBJbWFnZSBJbWFnZTwvdGV4dD48L3N2Zz4= "convert word to markdown flow diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}