---
category: general
date: 2026-06-24
description: 如何在保存为 Markdown 时设置回调以导出 DOCX 中的图像。了解如何提取图像、从 Word 中提取 SVG，以及使用自定义处理将
  DOCX 保存为 Markdown。
draft: false
keywords:
- how to set callback
- export images from docx
- how to extract images
- save docx as markdown
- extract svg from word
language: zh
og_description: 如何在将 DOCX 转换为 Markdown 时设置回调以导出图像。本指南将向您展示如何高效提取图像和 SVG。
og_title: 如何为从 DOCX 导出图像设置回调
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  headline: How to Set Callback for Exporting Images from DOCX
  type: TechArticle
- description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  name: How to Set Callback for Exporting Images from DOCX
  steps:
  - name: '**Deterministic names** – useful for version control or CDN publishing.'
    text: '**Deterministic names** – useful for version control or CDN publishing.'
  - name: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
    text: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
  - name: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
    text: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Conversion
title: 如何为从 DOCX 导出图像设置回调
url: /zh/python/content-extraction-and-manipulation/how-to-set-callback-for-exporting-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何为从 DOCX 导出图像设置回调

是否曾想过 **如何设置回调**，以便在将 DOCX 转换为 Markdown 时 **导出图像**？你并不是唯一遇到这个问题的人。许多开发者在默认转换将所有图像导入一个通用文件夹，甚至更糟的是，完全丢失 SVG 图形时，都会卡住。

在本教程中，我们将演示一个完整、可直接运行的解决方案，回答“如何设置回调”这一问题，展示 **如何提取图像**，并涵盖 **从 Word 中提取 SVG**。完成后，你将能够 **将 DOCX 保存为 Markdown**，并为每个图像资源使用自定义命名方案——无需手动操作。

## 你将学到的内容

- 为什么回调是控制转换期间图像文件名的最简洁方式。  
- 如何挂接到 Aspose.Words 的 `MarkdownSaveOptions.resource_saving_callback`。  
- 步骤清晰的代码，提取 **PNG**、**JPG**、**SVG** 以及其他嵌入资源。  
- 处理文件名冲突、大文件以及跨平台路径细节的技巧。  

> **专业提示：** 如果你已经在更大的流水线中使用 Aspose.Words，只需将此回调加入即可，无需改动其他代码。

---

![How to set callback diagram](https://example.com/images/how-to-set-callback.png "how to set callback")

## 前置条件

- Python 3.8+（示例使用 f‑strings，3.6+ 即可）。  
- 已安装 `aspose-words` 包（`pip install aspose-words`）。  
- 包含光栅图像 **和** 矢量图形（SVG）的 DOCX 文件。  
- 对 Python 函数和文件 I/O 有基本了解。

如果满足以上条件，下面开始吧。

---

## 如何为从 DOCX 导出图像设置回调

解决方案的核心在于 **资源保存回调**。当你调用 `document.save` 时，Aspose.Words 会为每个要写入的图像或 SVG 调用此委托。通过返回元组 `(new_name, data)`，你可以同时决定文件名和字节数据。

```python
import aspose.words as aw
import os
import hashlib

# Step 1: Load the source document
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

### 为什么需要回调？

如果没有回调，Aspose.Words 会创建 `image1.png`、`image2.svg` 等文件，并将它们放在 Markdown 文件旁的文件夹中。这对快速演示还算可以，但在生产环境中通常需要：

1. **确定性的名称**——便于版本控制或 CDN 发布。  
2. **避免冲突**——相同原始名称的两张图片不会相互覆盖。  
3. **自定义文件夹结构**——比如将所有资产放在 `/assets/docs/` 下。

回调让你对上述三点拥有完整控制权。

---

## 使用资源回调导出 DOCX 中的图像

下面是回调实现。它对二进制数据进行哈希以生成唯一后缀，保留原始文件扩展名，并返回新文件名以及原始字节。

```python
def resource_callback(resource):
    """
    Called for every image/SVG that MarkdownSaveOptions wants to write.
    Returns a tuple (new_name, data) to control the saved file name.
    """
    # Preserve the original extension (.png, .svg, …)
    extension = os.path.splitext(resource.name)[1]

    # Compute a short hash of the image bytes – guarantees uniqueness
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]

    # Build a deterministic, collision‑free filename
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data
```

#### 边缘情况处理

- **大文件：** SHA‑256 对任何大小都适用；哈希在内存中计算，处理超大 PDF 时请注意内存限制。  
- **缺少扩展名：** 某些旧版 Word 文件可能不带显式扩展名，此时 `extension` 为空；你可以默认使用 `.bin`，或检查前几个字节来猜测格式。  
- **非图像资源：** 回调会针对每个外部资源（例如 OLE 对象）触发。如果只关心图像/SVG，可在处理前通过 `resource.type` 进行过滤。

---

## 如何从 Word 中提取图像和 SVG

现在我们把回调接入 Markdown 保存流程。`MarkdownSaveOptions` 对象正是为此提供 `resource_saving_callback` 属性。

```python
# Step 2: Configure Markdown save options to use the callback
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = resource_callback

# Optional: set the folder where images will be placed relative to the .md file
markdown_options.resource_folder = "assets/images"
```

`resource_folder` 是可选的，但通常很方便。如果省略，它会把图像放在 Markdown 文件旁，容易导致项目根目录杂乱。

### 保存文档

```python
# Step 3: Save the document as Markdown, letting the callback store the resources
output_md_path = "YOUR_DIRECTORY/output.md"
document.save(output_md_path, markdown_options)
print(f"Markdown saved to {output_md_path}")
```

运行脚本后，你会看到类似以下的文件：

```
assets/images/img_a1b2c3d4e5.png
assets/images/img_f6g7h8i9j0.svg
```

生成的 `output.md` 将包含指向这些文件名的图像链接：

```markdown
![Image](assets/images/img_a1b2c3d4e5.png)
```

这就是 **提取图像** 的实际效果——每张图片，无论光栅还是矢量，都会成为单独、唯一命名的资源。

---

## 使用自定义图像处理保存 DOCX 为 Markdown

把所有内容整合在一起，下面是完整脚本，可直接复制到名为 `convert_docx_to_md.py` 的文件中：

```python
import aspose.words as aw
import os
import hashlib

def resource_callback(resource):
    """Control the naming of each exported image/SVG."""
    extension = os.path.splitext(resource.name)[1] or ".bin"
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data

def convert_docx_to_markdown(input_path, output_md_path, image_folder="assets/images"):
    # Load the DOCX
    document = aw.Document(input_path)

    # Set up Markdown options with our callback
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.resource_saving_callback = resource_callback
    md_options.resource_folder = image_folder

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_md_path), exist_ok=True)
    os.makedirs(os.path.join(os.path.dirname(output_md_path), image_folder), exist_ok=True)

    # Perform the conversion
    document.save(output_md_path, md_options)
    print(f"✅ Conversion complete! Markdown at: {output_md_path}")

if __name__ == "__main__":
    # Adjust these paths to your environment
    INPUT_DOCX = "YOUR_DIRECTORY/input.docx"
    OUTPUT_MD = "YOUR_DIRECTORY/output.md"
    convert_docx_to_markdown(INPUT_DOCX, OUTPUT_MD)
```

**工作原理说明：**  
- `resource_callback` 确保每个图像获得唯一且可复现的名称。  
- `resource_folder` 通过分离资产让 Markdown 更整洁。  
- `os.makedirs` 调用防止在全新机器上运行时出现 “文件夹未找到” 错误。

---

## 从 Word 中提取 SVG —— 矢量图形怎么办？

SVG 在回调中与 PNG 处理方式相同，因为它们都是 `resource`。唯一的细微差别是，某些旧版 Word 会把 SVG 作为 *OfficeArt* 对象嵌入，Aspose.Words 默认会将其转换为光栅 PNG，除非显式启用 **preserve SVG** 标志：

```python
md_options.export_svg = True  # Keep original SVG markup
```

在保存之前加入该行，回调将收到带 `.svg` 扩展名的资源，保留清晰的矢量数据——非常适合响应式网页文档。

---

## 常见问题与注意事项

| Question | Answer |
|----------|--------|
| **如果两张图片完全相同怎么办？** | SHA‑256 哈希会相同，导致文件名冲突。如需保留两份，可在哈希计算中加入原始 `resource.name`（例如 `hash(resource.name + resource.data)`）。 |
| **可以根据文件类型更改文件夹吗？** | 可以。在 `resource_callback` 中检查 `extension`，返回类似 `f"png/{new_name}"`（光栅图像）或 `f"svg/{new_name}"`（矢量图）的路径。 |
| **这在 Linux/macOS 上可用吗？** | 完全可以。代码使用 `os.path` 抽象路径分隔符。只需确保在付费版情况下能够访问 Aspose.Words 许可证文件 (`aspose.words.lic`)。 |
| **处理超大文档时内存占用如何？** | 回调会收到每个资源的 **完整字节数组**，意味着图像会暂时占用内存。对于多 GB 的文件，建议在回调内部将数据流式写入磁盘，而不是返回整个字节数组。 |

---

## 结论

现在你已经掌握了 **如何设置回调**，以在 **将 DOCX 保存为 Markdown** 时控制图像提取。该方法可以 **从 DOCX 导出图像**、**从 Word 中提取 SVG**，并保持 Markdown 文件整洁且具确定性。

在一个自包含的脚本中，我们演示了加载文档、定义资源保存回调、配置 `MarkdownSaveOptions`，以及处理文件名冲突和矢量图形等边缘情况。最终得到的是一组唯一命名的资产，配合完美链接的 Markdown 文件——可直接用于静态站点生成器、文档流水线或任何需要干净、可复用资产的工作流。

**下一步？**  
- 将其与 MkDocs 等静态站点生成器链式使用，实现 Word 文档的自动发布。  
- 若更喜欢内联图像，可尝试 `markdown_options.export_images_as_base64 = True`。  
- 深入探索 Aspose.Words 的其他回调（如 `document_saving_callback`），进一步控制 Markdown 输出本身。

如果你还有关于 **如何从其他 Office 格式提取图像** 的问题，或需要针对特定命名约定微调回调，欢迎在下方留言，祝编码愉快！

## 接下来该学习什么？

以下教程与本指南的技术紧密相关，帮助你进一步掌握 API 功能并探索替代实现方式：

- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}