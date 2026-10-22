---
category: general
date: 2026-06-27
description: 使用 Python 将 docx 转换为 markdown。学习从 Word 中提取图片，并使用自定义回调保存 markdown 输出。
draft: false
keywords:
- convert docx to markdown
- extract images from word
- convert word to markdown
- python docx to markdown
- save markdown output
language: zh
og_description: 在 Python 中将 docx 转换为 markdown，提取 Word 中的图片，并使用自定义资源回调保存 markdown 输出。
og_title: 将 docx 转换为 markdown – 带图像提取的 Python 指南
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert docx to markdown using Python. Learn to extract images from
    Word and save markdown output with a custom callback.
  headline: Convert docx to markdown – Complete Python Guide with Image Extraction
  type: TechArticle
- description: Convert docx to markdown using Python. Learn to extract images from
    Word and save markdown output with a custom callback.
  name: Convert docx to markdown – Complete Python Guide with Image Extraction
  steps:
  - name: Expected Output
    text: '```markdown # Sample Document'
  - name: Quick sanity check
    text: '```bash # On Unix/macOS cat YOUR_DIRECTORY/output.md ls YOUR_DIRECTORY/images/
      ```'
  - name: Dealing with duplicate image names
    text: 'Word sometimes reuses the same internal name for different pictures. To
      avoid overwriting, you can tweak `image_saver`:'
  - name: Converting large documents
    text: 'For multi‑megabyte documents, consider streaming the output to avoid memory
      spikes:'
  type: HowTo
tags:
- Python
- Aspose.Words
- Document Conversion
title: 将 docx 转换为 markdown —— 完整的 Python 指南与图片提取
url: /zh/python/document-conversion/convert-docx-to-markdown-complete-python-guide-with-image-ex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 将 docx 转换为 markdown – 完整的 Python 指南并提取图片

有没有想过如何 **将 docx 转换为 markdown** 且不丢失 Word 文件中嵌入的图片？你并不是唯一有此困惑的人。许多开发者在转换时会遇到图片丢失的问题，导致 markdown 中出现断开的链接，甚至根本没有图片。

好消息是，只需几行 Python 代码和 Aspose.Words，就能轻松将 `.docx` 转换为干净的 markdown **并** 将每张图片提取到你指定的文件夹中。在本教程中，我们将从安装库到编写回调函数，完整演示整个过程。

阅读完本指南后，你将能够 **将 word 转换为 markdown**，提取所有图形，并 **保存 markdown 输出**，以供静态站点生成器、文档流水线或任何 markdown‑first 工作流使用。

## 你需要准备的环境

- Python 3.8 或更高（代码在 3.9+ 也可运行）  
- 可使用 `pip` 安装第三方包的环境  
- 有效的 Aspose.Words for Python 许可证（免费试用版可用于评估）  
- 一个包含文本和至少一张图片的示例 `input.docx`  

就这些——不需要笨重的 Office 安装，不需要 COM 互操作，只需纯 Python。

## 第一步：安装 Aspose.Words for Python

首先，获取库。打开终端并运行：

```bash
pip install aspose-words
```

如果出现权限错误，请在命令前加 `--user` 或使用虚拟环境。安装完成后，你就可以使用 `aspose.words` 包（示例中导入为 `aw`）。

> **Pro tip:** 保持你的 `requirements.txt` 整洁；添加 `aspose-words==<latest-version>`，这样协作者可以精确复现环境。

## 第二步：设置自定义图片保存回调

Aspose.Words 允许你通过 *资源保存回调* 挂接到保存管道。可以把它想象成一个中间人，接收每张图片的字节流并告诉库在生成的 markdown 文件中如何引用它。

下面是回调的核心代码：

```python
# Step 1: Define a callback to store extracted images in a custom folder
def image_saver(image_bytes, image_name):
    """
    Saves an image to YOUR_DIRECTORY/images/ and returns the relative path
    that will be placed in the markdown file.
    """
    # Ensure the target folder exists
    import os
    target_dir = os.path.join("YOUR_DIRECTORY", "images")
    os.makedirs(target_dir, exist_ok=True)

    # Build the full path on disk
    file_path = os.path.join(target_dir, image_name)

    # Write the raw image bytes to disk
    with open(file_path, "wb") as f:
        f.write(image_bytes)

    # Return the path that markdown will use (relative to the .md file)
    return os.path.join("images", image_name)
```

**这有什么意义：**  
- **可控性** – 你可以决定文件夹结构、命名规则，甚至在需要时进行图片格式转换。  
- **可移植性** – 返回的相对路径使得 markdown 在不同机器间保持可用，只要 `images` 文件夹随同移动。  
- **性能** – 回调对每张图片只执行一次，避免重复写入。

## 第三步：配置 Markdown 保存选项

现在把回调绑定到 `MarkdownSaveOptions` 对象。这样 Aspose.Words 在遇到图片资源时就会使用我们的 `image_saver`。

```python
# Step 2: Create Markdown save options and attach the callback
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = image_saver
```

这里还可以微调一些可选设置，例如 `export_images_as_base64`（设为 `False`，因为我们希望生成独立文件）或 `add_table_of_contents`（如果需要目录）。本指南中我们使用默认设置。

## 第四步：加载源 Word 文档

加载 `.docx` 非常简单。只需把文件路径传给 Aspose.Words：

```python
# Step 3: Load the source Word document
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

如果文档很大，可以考虑使用 `aw.LoadOptions` 进行流式加载，但对大多数场景来说，直接构造即可。

## 第五步：保存为 Markdown – 让回调完成繁重工作

最后，调用 Aspose.Words 将文档写出为 markdown 文件。库会为每个嵌入的图片调用 `image_saver`，保存文件并在 markdown 中插入正确的图片链接。

```python
# Step 4: Save the document as Markdown, letting the callback handle image resources
doc.save("YOUR_DIRECTORY/output.md", md_options)
```

过程结束后，你会看到两件事：

1. 包含类似 `![](images/image1.png)` 行的 `output.md`  
2. 一个填充了所有提取图片的 `images` 子文件夹

### 预期输出

```markdown
# Sample Document

This is a paragraph from the Word file.

![](images/image1.png)

Another paragraph follows the picture.
```

在任意 markdown 预览器（VS Code、GitHub、MkDocs）中打开 `output.md`，应能看到图片与原始 Word 文件中完全一致的渲染效果。

## 第六步：验证结果并处理边缘情况

### 快速检查

```bash
# On Unix/macOS
cat YOUR_DIRECTORY/output.md
ls YOUR_DIRECTORY/images/
```

确保图片文件名与 markdown 中的路径相匹配。如果发现缺失图片，请检查回调返回的是 **相对** 路径（而非绝对路径），并确认 `images` 文件夹的引用正确。

### 处理重复的图片名称

Word 有时会为不同图片使用相同的内部名称。为避免覆盖，你可以修改 `image_saver`：

```python
import uuid

def image_saver(image_bytes, image_name):
    unique_name = f"{uuid.uuid4().hex}_{image_name}"
    # rest of the code uses unique_name instead of image_name
    ...
    return os.path.join("images", unique_name)
```

### 转换大文档

对于多兆字节的文档，考虑使用流式输出以避免内存峰值：

```python
with open("YOUR_DIRECTORY/output.md", "w", encoding="utf-8") as out_file:
    doc.save(out_file, md_options)
```

Aspose.Words 在内部已经实现了流式处理，你无需将整个 markdown 加载到内存中。

## 第七步：自动化工作流（可选）

如果需要批量处理文件夹中的 Word 文档，可以将逻辑放入循环：

```python
import glob

for doc_path in glob.glob("YOUR_DIRECTORY/*.docx"):
    doc = aw.Document(doc_path)
    base_name = os.path.splitext(os.path.basename(doc_path))[0]
    md_path = f"YOUR_DIRECTORY/{base_name}.md"
    doc.save(md_path, md_options)
    print(f"Converted {doc_path} → {md_path}")
```

现在只需把数百个 `.docx` 文件放入目录，脚本就会逐个转换，每个文档都有自己的 `images` 子文件夹。

## 结论

我们已经完整演示了如何在 **将 docx 转换为 markdown** 的同时保留所有图片，使用简洁的 Python 脚本和 Aspose.Words 强大的回调机制。现在你已经掌握了：

- 通过自定义 `resource_saving_callback` **从 Word 中提取图片**  
- 使用最少配置 **将 word 转换为 markdown**  
- **保存 markdown 输出** 并配合整齐的图片文件夹  

接下来，你可以尝试添加更多 markdown 扩展（表格、脚注），或将脚本集成到 CI 流水线，实现文档的自动构建。只要保持图片保存逻辑的灵活性，markdown 就会保持整洁。

对边缘情况或许可证有疑问？在下方留言吧，祝编码愉快！

## 接下来你应该学习什么？

以下教程与本指南紧密相关，帮助你进一步掌握相关 API 功能并探索其他实现思路：

- [How to Save Markdown from Word – Complete Python Guide](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)
- [Convert Docx File To Markdown](/words/english/net/basic-conversions/docx-to-markdown/)
- [Convert Word to Markdown – Embed Images as Base64](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}