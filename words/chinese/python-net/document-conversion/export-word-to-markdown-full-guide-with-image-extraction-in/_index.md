---
category: general
date: 2026-06-21
description: 使用 Python 将 Word 导出为 Markdown 并保存 Word 中的图片。学习如何将 docx 转换为 markdown，使用
  Python 写入二进制文件，以及从 docx 中提取图片。
draft: false
keywords:
- export word to markdown
- convert docx to markdown
- save images from word
- write binary file python
- how to extract images from docx
language: zh
og_description: 将 Word 导出为 Markdown 并自动保存 Word 中的图片。本分步指南展示了如何将 docx 转换为 markdown、使用
  Python 写入二进制文件以及从 docx 中提取图片。
og_title: 将 Word 导出为 Markdown – 完整的 Python 教程
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Export Word to Markdown and save images from Word using Python. Learn
    how to convert docx to markdown, write binary file python, and extract images
    from docx.
  headline: Export Word to Markdown – Full Guide with Image Extraction in Python
  type: TechArticle
- description: Export Word to Markdown and save images from Word using Python. Learn
    how to convert docx to markdown, write binary file python, and extract images
    from docx.
  name: Export Word to Markdown – Full Guide with Image Extraction in Python
  steps:
  - name: Expected Output Example
    text: 'If `input.docx` contained a single picture named `image1.png`, the resulting
      `output.md` might look like:'
  - name: What if the document has duplicate image names?
    text: 'Aspose.Words will suggest the same name for identical images. Our callback
      uses the suggested name directly, which could cause overwrites. To avoid that,
      modify the callback to append a unique identifier:'
  - name: Can I change the image format during extraction?
    text: Absolutely. After writing the binary data, you could open it with Pillow
      (`PIL.Image`) and save it as a different format (e.g., JPEG). This is useful
      when you need to **convert docx to markdown** for a web‑optimized site.
  - name: Does this work on macOS/Linux as well as Windows?
    text: Yes. The code uses `os.path` and avoids hard‑coded path separators, so it’s
      cross‑platform. Just remember to grant the script write permissions to the target
      directory.
  - name: What if I need to export tables or footnotes too?
    text: '`MarkdownSaveOptions` supports a range of features—tables become markdown
      tables, footnotes become inline references. No extra code is required; just
      experiment with the generated markdown to see how it renders.'
  type: HowTo
tags:
- python
- docx
- markdown
- image-extraction
title: 将 Word 导出为 Markdown – 使用 Python 的完整指南与图像提取
url: /zh/python/document-conversion/export-word-to-markdown-full-guide-with-image-extraction-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Export Word to Markdown – Full Guide with Image Extraction in Python

有没有想过如何 **export Word to markdown** 而不丢失文档中嵌入的图片？你并不是唯一的提问者——开发者们经常寻找一种轻松的方式，将 `.docx` 转换为干净的 markdown 并保留所有图片。

在本教程中，我们将完整演示一个解决方案，既能 **convert docx to markdown**，又能 **save images from word** 文件，全部使用纯 Python。完成后，你将拥有一个可直接运行的脚本，能够 **write binary file python** 风格地写入二进制文件并提取所有所需图片。

## What This Guide Covers

- 安装正确的库（Aspose.Words for Python）  
- 定义一个回调函数，将二进制数据写入磁盘  
- 将 Word 文档转换为 markdown 并处理图片  
- 验证输出并排查常见问题  

无需外部服务，无需手动复制粘贴——只需一个自包含脚本，随时可以放入任何项目中使用。

## Prerequisites

在开始之前，请确保你具备以下条件：

| Requirement | Why it matters |
|-------------|----------------|
| Python 3.8+ | 现代语法和类型提示 |
| `pip` access | 用于安装 Aspose.Words 包 |
| Write permission to a folder | 回调函数将 **write binary file python** 风格写入文件 |
| A `.docx` file with images | 以实际展示 **save images from word** 功能 |

如果这些听起来陌生，请不要慌——接下来我们会一步步演示如何配置。

## Step 1: Install Aspose.Words for Python via pip

Aspose.Words 是一个强大的库，能够完整解析 Word 文档格式，包括嵌入的媒体。使用以下命令一键安装：

```bash
pip install aspose-words
```

> **Pro tip:** 使用虚拟环境（`python -m venv venv`）来保持依赖整洁。这还能避免与其他项目的版本冲突。

## Step 2: Create a Resource‑Saving Callback (Write Binary File Python)

解决方案的核心是一个回调函数，它接收每个二进制资源（如图片），并决定将其保存到何处。这正是我们 **write binary file python** 的实现位置。

```python
def my_resource_saver(resource: bytes, suggested_name: str) -> str:
    """
    Save a binary resource (e.g., an image) to a custom folder and
    return the relative path for markdown linking.

    :param resource: Raw binary data of the resource.
    :param suggested_name: A filename suggested by Aspose.Words.
    :return: Relative path to be used in the markdown file.
    """
    # Build a relative path inside a custom folder.
    folder = "custom_images"
    os.makedirs(folder, exist_ok=True)          # Ensure the folder exists.
    file_path = os.path.join(folder, suggested_name)

    # Write the binary data to disk – classic write binary file python.
    with open(file_path, "wb") as f:
        f.write(resource)

    # Return the path so the Markdown writer can reference it.
    return file_path
```

**Why a callback?**  
Aspose.Words 并不知道你希望图片保存到哪里。通过提供 `my_resource_saver`，你可以完全控制命名、文件夹结构，甚至在需要时进行后处理（如图片压缩）。

## Step 3: Load the Source Word Document

现在让库指向你想要转换的 `.docx` 文件。

```python
import aspose.words as aw
import os

# Adjust the path to your actual file location.
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

如果找不到文件，请检查路径并确保脚本拥有读取权限。Windows 上常见的错误是混用正斜杠和反斜杠；使用 `os.path.join` 可以自动处理这些差异。

## Step 4: Configure Markdown Save Options and Attach the Callback

这一步将所有内容串联起来。我们告诉 Aspose.Words 使用 markdown 作为输出格式，并在遇到图片时调用我们的 `my_resource_saver`。

```python
# Create Markdown save options.
md_save = aw.saving.MarkdownSaveOptions()

# Attach the resource‑saving callback.
md_save.resource_saving_callback = my_resource_saver
```

这里可以微调 markdown 输出（例如，将 `md_save.export_images_as_base64 = False` 设置为 `False`，以使用外部图片）。对于 **how to extract images from docx** 的需求，保持图片为独立文件通常更清晰。

## Step 5: Export the Document – The Final Export Word to Markdown Call

剩下的只是一行代码，完成所有繁重工作。

```python
output_md = "YOUR_DIRECTORY/output.md"
doc.save(output_md, md_save)
print(f"✅ Markdown saved to {output_md}")
print(f"🖼️ Images stored in ./custom_images/")
```

运行脚本后，你会在同目录下看到一个 `output.md` 文件，以及一个 `custom_images` 文件夹，里面存放了原始 Word 文件中的所有图片。markdown 会使用相对路径引用这些图片，方便用于静态站点生成器或 GitHub 渲染。

### Expected Output Example

如果 `input.docx` 包含一张名为 `image1.png` 的图片，生成的 `output.md` 可能如下所示：

```markdown
# Sample Document

Here is an illustration:

![image1.png](custom_images/image1.png)

More text follows...
```

对应的文件夹结构：

```
/YOUR_DIRECTORY/
│─ input.docx
│─ output.md
└─ custom_images/
   └─ image1.png
```

## Common Questions & Edge Cases

### What if the document has duplicate image names?

Aspose.Words 会为相同的图片建议相同的名称。我们的回调直接使用建议的名称，可能导致覆盖。为避免此问题，可修改回调以追加唯一标识符：

```python
import uuid

def my_resource_saver(resource, suggested_name):
    unique_name = f"{uuid.uuid4().hex}_{suggested_name}"
    # rest of the code unchanged...
```

### Can I change the image format during extraction?

完全可以。在写入二进制数据后，你可以使用 Pillow（`PIL.Image`）打开并保存为其他格式（如 JPEG）。这在你需要 **convert docx to markdown** 为网页优化站点时非常有用。

### Does this work on macOS/Linux as well as Windows?

可以。代码使用 `os.path` 并避免硬编码路径分隔符，因而跨平台。只需确保脚本对目标目录拥有写入权限。

### What if I need to export tables or footnotes too?

`MarkdownSaveOptions` 支持多种功能——表格会转换为 markdown 表格，脚注会变为内联引用。无需额外代码，只需查看生成的 markdown，观察其渲染效果即可。

## Full Script – Ready to Copy & Paste

下面是完整、可直接运行的示例，整合了本文所有内容。将其保存为 `export_word_to_md.py`，然后执行 `python export_word_to_md.py`。

```python
import os
import uuid
import aspose.words as aw

def my_resource_saver(resource: bytes, suggested_name: str) -> str:
    """
    Save binary resources (images) to a custom folder and return
    the relative path for markdown references.
    """
    folder = "custom_images"
    os.makedirs(folder, exist_ok=True)

    # Ensure unique filenames to avoid collisions.
    unique_name = f"{uuid.uuid4().hex}_{suggested_name}"
    file_path = os.path.join(folder, unique_name)

    with open(file_path, "wb") as f:
        f.write(resource)

    return file_path

def main():
    # ------------------------------------------------------------------
    # 1️⃣ Load the Word document you want to convert.
    # ------------------------------------------------------------------
    doc_path = "YOUR_DIRECTORY/input.docx"
    if not os.path.isfile(doc_path):
        raise FileNotFoundError(f"❌ {doc_path} does not exist.")
    doc = aw.Document(doc_path)

    # ------------------------------------------------------------------
    # 2️⃣ Set up markdown options and plug in the image callback.
    # ------------------------------------------------------------------
    md_save = aw.saving.MarkdownSaveOptions()
    md_save.resource_saving_callback = my_resource_saver

    # ------------------------------------------------------------------
    # 3️⃣ Perform the export – this is the core **export word to markdown** step.
    # ------------------------------------------------------------------
    output_md = "YOUR_DIRECTORY/output.md"
    doc.save(output_md, md_save)

    print(f"✅ Markdown exported to: {output_md}")
    print(f"🖼️ Extracted images are in the folder: ./custom_images/")

if __name__ == "__main__":
    main()
```

运行后，用任意 markdown 查看器打开 `output.md`，你将看到原始 Word 内容——文本、标题、**save images from word**，以及所有其他元素——都被忠实再现。

## Conclusion

我们刚刚演示了一种稳健的方式，能够 **export word to markdown** 并保留每一张嵌入图片。通过 Aspose.Words 与自定义 **resource‑saving callback**，你可以 **convert docx to markdown**、**write binary file python**，并一次性解决 **how to extract images from docx** 的经典难题。

接下来可以尝试在回调中使用 Pillow 对图片进行压缩，或将脚本集成到 CI 流水线中，自动为静态站点转换文档。可能性无限，而你已经拥有了坚实的基础。

有反馈或遇到问题？欢迎在下方留言——祝编码愉快！

## What Should You Learn Next?

以下教程与本指南紧密相关，帮助你进一步掌握 API 功能并探索替代实现方式：

- [How to Save Markdown from Word – Complete Python Guide](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)
- [Recover Corrupted DOCX & Convert Word to Markdown](/words/english/python-net/document-conversion/recover-corrupted-docx-convert-word-to-markdown/)
- [Save Word Images – Convert Word to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}