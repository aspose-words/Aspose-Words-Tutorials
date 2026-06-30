---
category: general
date: 2026-06-30
description: 如何在将 DOCX 转换为 Markdown 时重命名图片。学习更改图片名称并将 Word 保存为带自定义图片文件名的 Markdown。
draft: false
keywords:
- how to rename images
- convert docx to markdown
- change image names
- save word as markdown
- custom image filenames
language: zh
og_description: 如何在将 DOCX 转换为 Markdown 时重命名图片。本指南展示了如何更改图片名称、将 Word 保存为 Markdown，以及使用自定义图片文件名。
og_title: 将 DOCX 转换为 Markdown 时如何重命名图片
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  headline: How to Rename Images When Converting DOCX to Markdown
  type: TechArticle
- description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  name: How to Rename Images When Converting DOCX to Markdown
  steps:
  - name: Why Use a GUID?
    text: '* **Uniqueness** – A GUID (`uuid4`) guarantees that two images will never
      clash, even across multiple runs. * **Traceability** – If you need to debug
      later, the GUID can be logged alongside the original Word paragraph number.
      * **Portability** – No reliance on the original Word naming scheme, which '
  - name: Expected Output (excerpt)
    text: '```markdown # Sample Document'
  - name: What if the document contains non‑image resources?
    text: Our callback already checks the file extension and returns `True` for anything
      that isn’t an image. This means CSS files, fonts, or embedded OLE objects keep
      their original names, which is usually what you want when you **save word as
      markdown**.
  - name: Can I use a custom naming scheme instead of GUIDs?
    text: 'Absolutely. Replace the `uuid.uuid4()` call with any function that returns
      a string. For example, you could prepend the original paragraph index:'
  - name: How does this affect performance on large documents?
    text: The callback runs once per resource, so the overhead is minimal—mostly the
      time to generate a GUID. Even a 200‑page report with dozens of images finishes
      in under a second on a modern laptop.
  - name: What if I need the image filenames to be deterministic (e.g., for CI builds)?
    text: 'Swap `uuid.uuid4()` for a hash of the original image bytes:'
  type: HowTo
tags:
- Aspose.Words
- Python
- Markdown
- Image Processing
title: 将 DOCX 转换为 Markdown 时如何重命名图片
url: /zh/python/document-conversion/how-to-rename-images-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在将 DOCX 转换为 Markdown 时重命名图像

是否曾经想过在将 DOCX 文件转换为 Markdown 时**自动重命名图像**？你并不是唯一有此困惑的人。在许多文档流水线中，默认的图像名称（如 `image1.png`）会变成难以追踪的噩梦，尤其是当相同的 Markdown 在团队之间进行版本控制时。  

好消息是，Aspose.Words for Python 让**即时更改图像名称**变得轻而易举，你可以保持 Markdown 的整洁，同时保留一个命名规范的资源文件夹。  

在本教程中，你将学习如何：

* 在 Python 中加载 Word 文档（`.docx`）。  
* 使用回调函数挂钩到 Markdown 保存过程，为每个图像分配基于 GUID 的文件名。  
* 将文档保存为 Markdown，使生成的文件引用新命名的图像。  

如果你熟悉基础的 Python 并已安装 Aspose.Words，你可以在五分钟内完成整个流程。无需外部脚本，无需手动重命名——只需一个独立的程序即可为你完成繁重的工作。

---

## 前置条件 — 开始之前需要准备的内容

| Requirement | Why It Matters |
|-------------|----------------|
| **Python 3.7+** | 示例使用了 3.6 引入的 f‑string 和类型提示，但 3.7+ 提供了 `os.path.splitext` 的便利。 |
| **Aspose.Words for Python via .NET** (`pip install aspose-words`) | 该库提供了我们依赖的 `aw.Document` 类和 `MarkdownSaveOptions`。 |
| **Write permission** to the output folder | 回调函数会创建新的图像文件，因此脚本必须拥有写入权限。 |
| **A DOCX file** you want to convert | 任意从简单报告到复杂手册的 DOCX 文件均可。 |

> **小贴士：** 如果你使用虚拟环境，请在安装 Aspose.Words 前激活它。这样可以隔离依赖，避免版本冲突。

## 步骤 1：加载 Word 文档  

当你想要**将 docx 转换为 markdown**时，首先要做的就是打开源文件。Aspose.Words 抽象了所有底层的 OPC 处理，只需一行代码即可完成。

```python
import aspose.words as aw

# Replace YOUR_DIRECTORY with the folder that holds your .docx file
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*为什么重要：* 如果不加载文档，你无法检查其资源，Markdown 导出器也没有东西可写。`aw.Document` 对象在内存中保存了整个 Word 包，使得在保存之前对其进行安全操作成为可能。

## 步骤 2：编写一个**重命名图像资源**的回调函数  

Aspose.Words 允许你将 `resource_saving_callback` 插入到 `MarkdownSaveOptions` 中。回调函数在每个资源（图像、CSS 等）写入磁盘之前被调用。通过修改 `resource.file_name`，我们可以强制使用**自定义图像文件名**。

```python
def rename_image_resource(resource):
    """
    Rename image resources with a unique GUID before saving.
    This is where we implement how to rename images.
    """
    import uuid, os

    # Guard: only process image resources, ignore CSS or other files
    if not resource.file_name.lower().endswith(('.png', '.jpg', '.jpeg', '.gif', '.bmp')):
        return True  # Let Aspose handle non‑image resources unchanged

    # Extract the original extension so we keep PNG as PNG, JPG as JPG, etc.
    _, ext = os.path.splitext(resource.file_name)

    # Generate a globally unique identifier and tack the original extension on
    new_name = f"{uuid.uuid4()}{ext}"
    resource.file_name = new_name

    # Returning True tells Aspose to proceed with the default saving logic
    return True
```

### 为什么使用 GUID？

* **唯一性** – GUID（`uuid4`）保证即使在多次运行中，两个图像也永不冲突。  
* **可追溯性** – 如果以后需要调试，GUID 可以与原始 Word 段落编号一起记录。  
* **可移植性** – 不依赖原始 Word 的命名方案，后者可能包含空格或特殊字符，导致 Markdown 链接失效。

## 步骤 3：将回调函数附加到 Markdown 保存选项  

现在我们告诉 Aspose 在将图像写入输出文件夹时使用我们的重命名逻辑。

```python
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = rename_image_resource

# Optional: control where images are placed relative to the markdown file
md_options.images_folder = "images"  # creates a sub‑folder called 'images'
```

*解释：* `MarkdownSaveOptions` 类控制从换行到图像文件夹位置的所有细节。通过设置 `resource_saving_callback`，你获得了一个在每个嵌入资源写入磁盘前触发的**钩子**，从而有机会在文件写入前**更改图像名称**。

## 步骤 4：将文档保存为 Markdown – 最后一步  

有了回调函数，最后一步就非常直接。

```python
output_path = "YOUR_DIRECTORY/CustomResources.md"
doc.save(output_path, md_options)
print(f"Markdown saved to {output_path}")
```

脚本执行完毕后，你会看到：

* `CustomResources.md` – 你的 Word 文件的 Markdown 表示。  
* 一个 `images/` 文件夹（或你设置的任何文件夹），其中包含类似 `d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png` 的文件。  

Markdown 文件将引用新的基于 GUID 的文件名，因此任何下游处理器（GitHub、MkDocs 等）都会自动获取正确的图像，无需手动重命名。

### 预期输出（摘录）

```markdown
# Sample Document

Here is an image that was originally called `image1.png` in the DOCX:

![d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e](images/d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png)

And another one:

![a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6](images/a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6.jpg)
```

每次运行的 GUID 会不同，但模式保持不变。

## 处理边缘情况和常见问题  

### 如果文档包含非图像资源怎么办？

我们的回调已经检查文件扩展名，对非图像的资源返回 `True`。这意味着 CSS 文件、字体或嵌入的 OLE 对象会保留原始名称，这通常是你在**将 word 保存为 markdown**时想要的行为。

### 我可以使用自定义命名方案而不是 GUID 吗？

完全可以。将 `uuid.uuid4()` 调用替换为返回字符串的任意函数。例如，你可以在前面加上原始段落索引：

```python
new_name = f"para{resource.resource_id}{ext}"
```

只需确保生成的名称在整个文档中是唯一的。

### 这对大文档的性能有何影响？

回调函数对每个资源运行一次，因此开销极小——主要是生成 GUID 的时间。即使是包含数十张图像的 200 页报告，在现代笔记本上也能在不到一秒的时间内完成。

### 如果需要图像文件名是确定性的（例如用于 CI 构建）怎么办？

将 `uuid.uuid4()` 替换为原始图像字节的哈希值：

```python
import hashlib
hash = hashlib.sha256(resource.raw_bytes).hexdigest()[:12]
new_name = f"{hash}{ext}"
```

这样在对相同源图像运行脚本时，每次都会生成相同的文件名。

## 完整可运行脚本 – 复制、粘贴、运行  



## 接下来该学习什么？

以下教程涵盖与本指南技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步解释，帮助你掌握更多 API 功能并在自己的项目中探索替代实现方案。

- [将 docx 保存为 markdown – 完整 C# 指南（含图像提取）](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/)
- [如何从 DOCX 保存 Markdown – 步骤指南](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}