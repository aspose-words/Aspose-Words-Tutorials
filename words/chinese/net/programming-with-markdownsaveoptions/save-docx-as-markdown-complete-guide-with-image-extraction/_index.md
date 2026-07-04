---
category: general
date: 2026-05-29
description: 使用 Aspose.Words 将 docx 保存为 markdown，并学习如何在单个工作流中从 docx 中提取图像。一步一步的代码和技巧。
draft: false
keywords:
- save docx as markdown
- extract images from docx
- convert word to markdown
- convert docx to markdown
- how to extract images
language: zh
og_description: 使用 Aspose.Words 将 docx 保存为 markdown。了解在将 Word 转换为 markdown 时如何从 docx
  中提取图像，附带完整代码。
og_title: 将 docx 保存为 markdown – 完整教程及图片提取
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Save docx as markdown using Aspose.Words and learn how to extract images
    from docx in a single workflow. Step‑by‑step code and tips.
  headline: Save docx as markdown – Complete Guide with Image Extraction
  type: TechArticle
- description: Save docx as markdown using Aspose.Words and learn how to extract images
    from docx in a single workflow. Step‑by‑step code and tips.
  name: Save docx as markdown – Complete Guide with Image Extraction
  steps:
  - name: – Load the source document
    text: First we need a `Document` object that points at the Word file we want to
      transform.
  - name: – Define a callback that extracts images from docx
    text: The magic lives in `IResourceSavingCallback`. Aspose.Words calls `ResourceSaving`
      for every external resource (images, fonts, etc.) it needs to write out. By
      providing our own implementation we gain total control over the file name, folder,
      and even the stream used.
  - name: – Wire the callback into Markdown save options
    text: Now we create a `MarkdownSaveOptions` instance and assign our custom saver.
  - name: – Save the document as markdown
    text: Finally, we ask Aspose.Words to write out the markdown file. The images
      are saved automatically by the callback we just hooked.
  type: HowTo
tags:
- Aspose.Words
- C#
- Document Conversion
title: 将 docx 保存为 markdown – 完整指南与图片提取
url: /zh/net/programming-with-markdownsaveoptions/save-docx-as-markdown-complete-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 将 docx 保存为 markdown – 完整指南及图片提取

有没有想过如何 **save docx as markdown** 而不丢失 Word 文件中隐藏的图片？你并不是唯一的遇到这个问题的人。许多开发者在尝试把富文本文档转换为干净的 markdown 时会卡住，最终得到破损的图片链接。

在本教程中，我们将一步步演示一种实用方案，既能 **convert docx to markdown**，又能 **extract images from docx** 自动完成。结束时，你将拥有可直接运行的 C# 代码片段、一系列最佳实践提示，以及运行代码时的预期结果概览。

## 你将学到的内容

- 为 .NET 配置 Aspose.Words，以处理 Word‑to‑markdown 转换。  
- 实现自定义 `IResourceSavingCallback`，将每张嵌入的图片保存到你指定的文件夹。  
- 了解回调为何重要，以及它如何在生成的 markdown 中保持图片引用完整。  
- 查看完整、可运行的示例以及你将得到的确切 markdown 输出。  

**先决条件** – 需要 .NET 6（或任意较新的 .NET 版本）、Visual Studio 2022（或 VS Code），以及有效的 Aspose.Words for .NET 许可证（免费试用版可用于测试）。不需要其他第三方库。

---

## 使用 Aspose.Words 将 docx 保存为 markdown 的步骤

下面是我们将遵循的高层流程：

1. 加载包含图片的源 `.docx`。  
2. 创建一个回调类，决定每张提取的图片写入的位置。  
3. 将回调绑定到 `MarkdownSaveOptions`。  
4. 保存文档——markdown 写入磁盘，图片则保存到你指定的文件夹。

每一步都会详细说明，并在说明后直接展示代码。

### 步骤 1 – 加载源文档

首先需要一个指向待转换 Word 文件的 `Document` 对象。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

// Load the source .docx that contains images.
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **为什么重要：** Aspose.Words 会解析 DOCX 包，构建内部对象模型，使每个段落、表格和图片都可访问。如果文件无法加载，后续管道将根本不会运行。

### 步骤 2 – 定义回调以从 docx 中提取图片

关键在于 `IResourceSavingCallback`。Aspose.Words 会为每个需要写出的外部资源（图片、字体等）调用 `ResourceSaving`。通过提供自定义实现，你可以完全控制文件名、文件夹，甚至使用的流。

```csharp
// Step 2: Define a callback that stores each extracted image in a sub‑folder
// and gives it a unique name.
class MyResourceSaver : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Create (or reuse) a folder for the images.
        string folder = "YOUR_DIRECTORY/markdown_images";
        Directory.CreateDirectory(folder);

        // Build a new file name like "img_0.png", "img_1.jpg", etc.
        string newName = Path.Combine(folder,
            $"img_{args.Index}{Path.GetExtension(args.ResourceFileName)}");

        // Tell Aspose.Words where to write the image.
        args.ResourceFileName = newName;
        args.Stream = new FileStream(newName, FileMode.Create, FileAccess.Write);

        // Allow the default saving process to continue.
        args.Cancel = false;
    }
}
```

> **小技巧：** `args.Index` 为零基索引，即使两张图片的原始文件名相同也能保证唯一性。这可以避免在多次转换时出现恼人的 “duplicate file name” 错误。

### 步骤 3 – 将回调接入 Markdown 保存选项

现在创建 `MarkdownSaveOptions` 实例并分配自定义 saver。

```csharp
// Step 3: Configure Markdown save options to use the custom resource saver.
MarkdownSaveOptions opts = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceSaver()
};
```

> **为何必不可少：** 若不使用回调，Aspose.Words 会将图片以 base‑64 字符串嵌入 markdown，或根据默认设置直接丢弃。我们的回调强制使用文件引用，能够兼容任何静态站点生成器。

### 步骤 4 – 将文档保存为 markdown

最后，调用 Aspose.Words 将 markdown 写出。图片会由刚才挂载的回调自动保存。

```csharp
// Step 4: Save the document as Markdown; images will be written to the folder above.
doc.Save("YOUR_DIRECTORY/output.md", opts);
```

代码执行完毕后，你会看到：

- `output.md` – 原始 Word 文件的 markdown 表示。  
- `markdown_images/` – 一个文件夹，里面包含 `img_0.png`、`img_1.jpg` … 等对应 DOCX 中每张图片的文件。

#### 预期的 markdown 片段

```markdown
# Sample Title

Here is some introductory text.

![Image 1](markdown_images/img_0.png)

More text after the picture.
```

图片链接指向步骤 2 中保存的文件，任何 markdown 查看器都能正确渲染该图片。

---

## 在转换为 markdown 的同时提取 docx 中的图片

如果你的唯一目标是 **how to extract images**，完全可以复用相同的回调而不必保存 markdown。只需调用 `doc.Save("dummy.md", opts)`，或使用 `doc.GetChildNodes(NodeType.Shape, true)` 枚举图片。回调会为每张图片触发，让你把它们保存到任意位置。

```csharp
// Example: extract images only – we still need a save call to trigger the callback.
doc.Save("YOUR_DIRECTORY/placeholder.md", opts);
```

> **注意：** 提取完毕后，临时的 markdown 文件可以删除；回调已经把图片写入磁盘。

---

## 使用自定义图片处理将 Word 转换为 markdown

搜索 “convert word to markdown” 时，常伴随 “preserve formatting”。Aspose.Words 在保留标题、列表、表格和代码块方面表现出色。唯一需要留意的是图片缩放。默认情况下，生成的 markdown 使用原始图片尺寸。如果需要缩略图，可在回调中先对图片进行缩放后再写出（例如使用 `System.Drawing` 或 `ImageSharp`）。

```csharp
// Inside ResourceSaving, you could resize before saving:
using (var original = Image.Load(args.Stream))
{
    var thumbnail = original.Clone(ctx => ctx.Resize(new ResizeOptions
    {
        Size = new Size(300, 0),
        Mode = ResizeMode.Max
    }));
    thumbnail.Save(newName);
}
```

*（上面的片段使用 ImageSharp——如果走这条路，需要额外添加对应的 NuGet 包。）*

---

## 转换 docx 为 markdown 时的常见坑

| Pitfall | Why it happens | How to avoid it |
|---------|----------------|-----------------|
| Images end up as **base64** strings | Default `ResourceSavingCallback` is not set | Always provide a custom `IResourceSavingCallback` |
| Broken links after moving the markdown file | Relative paths point to a folder that no longer exists | Keep the `markdown_images` folder next to the `.md` file or adjust the path in `MarkdownSaveOptions.ImageFolder` |
| Duplicate image names | Two pictures share the same original name | Use `args.Index` (as we did) or a GUID in the file name |
| Out‑of‑memory on huge docs | Saving large images without streaming | Use `args.Stream = new FileStream(..., FileMode.Create, FileAccess.Write, FileShare.None, 4096, FileOptions.SequentialScan)` to stream efficiently |

---

## 高级场景：如何提取图片

有时你需要 **without** 任何 markdown 的图片，可能是要喂给机器学习模型。此时可以：

1. 将 `opts.SaveFormat = SaveFormat.Png`（或任意图片格式）以强制仅导出图片。  
2. 或者复用同一个 `MyResourceSaver`，但调用 `doc.Save("dummy.docx", SaveFormat.Docx)` 仅为触发回调。

这两种方式都可以复用相同的逻辑，让代码保持 DRY（Don’t Repeat Yourself）。

---

## 完整、可运行的示例

下面是可以直接复制到控制台应用中的完整程序。将 `YOUR_DIRECTORY` 替换为机器上实际存在的绝对或相对路径。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;

namespace DocxToMarkdownDemo
{
    // Step 2 – custom callback that saves each image.
    class MyResourceSaver : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            string folder = "YOUR_DIRECTORY/markdown_images";
            Directory.CreateDirectory(folder);

            string newName = Path.Combine(folder,
                $"img_{args.Index}{Path.GetExtension(args.ResourceFileName)}");

            args.ResourceFileName = newName;
            args.Stream = new FileStream(newName, FileMode.Create, FileAccess.Write);
            args.Cancel = false;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 1 – load the .docx.
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3 – set up save options with our callback.
            MarkdownSaveOptions opts = new MarkdownSaveOptions
            {
                ResourceSavingCallback = new MyResourceSaver()
            };

            // Step 4 – save as markdown; images will be extracted automatically.
            doc.Save("YOUR_DIRECTORY/output.md", opts);

            System.Console.WriteLine("Conversion complete! Check output.md and the markdown_images folder.");
        }
    }
}
```

**运行后你应该看到的结果：**  

- `output.md` 包含类似 `![Image](markdown_images/img_0.png)` 的图片链接。  
- `markdown_images` 文件夹中每个嵌入图片都有对应的文件。

---

## 结论

现在你已经掌握了一套完整的 **save docx as markdown** 方案，同时能够干净利落地 **extract images from docx**。关键在于 `IResourceSavingCallback`，它让你对每张图片的存储位置和方式拥有完全控制。

接下来你可以：

- 调整回调，以基于 alt‑text 或其他有意义的标题重命名文件。  
- 添加后处理，将 markdown 转换为 HTML 并配合静态站点生成器使用。

## 接下来该学习什么？

- [How to Embed Images in Markdown When Converting DOCX](/words/english/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/)
- [Save Word Images – Convert Word to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}