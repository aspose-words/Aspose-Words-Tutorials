---
category: general
date: 2026-10-04
description: 在 Aspose.Words 中启用恢复模式，以安全地恢复损坏的 Word 文档。请按照逐步指南查看完整的 Python 代码和说明。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- recover corrupted word document
- Aspose.Words load options
- document recovery Python
- handling damaged .docx files
language: zh
lastmod: 2026-10-04
og_description: 启用恢复模式以使用 Aspose.Words 恢复损坏的 Word 文档。本教程展示了完整的 Python 代码、其工作原理以及如何处理边缘情况。
og_image_alt: Screenshot of Python code loading a corrupted Word document with recovery
  mode enabled
og_title: 启用恢复模式以修复损坏的 Word 文档 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  headline: Enable recovery mode to recover a corrupted Word document
  type: TechArticle
- description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  name: Enable recovery mode to recover a corrupted Word document
  steps:
  - name: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
    text: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
  - name: Load the `.docx` using those options.
    text: Load the `.docx` using those options.
  - name: Verify the mode and optionally save a repaired copy.
    text: Verify the mode and optionally save a repaired copy.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document processing
- Error handling
title: 启用恢复模式以恢复损坏的 Word 文档
url: /zh/python/document-options-and-settings/enable-recovery-mode-to-recover-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 启用恢复模式以修复损坏的 Word 文档

如果您需要在加载 Word 文件时 **启用恢复模式**，本指南将向您展示如何使用 Aspose.Words for Python 完成此操作。通过打开恢复模式，您可以 **恢复损坏的 Word 文档**，否则会抛出异常。

在以下章节中，您将学习：

* 哪些类和属性控制恢复行为。  
* 如何在不导致应用程序崩溃的情况下加载可能受损的 `.docx` 文件。  
* 常见加载问题的排查技巧以及自定义恢复策略的方法。

> **先决条件** – 您已安装 Aspose.Words for Python（`pip install aspose-words`）并具备 Python 文件 I/O 的基本了解。

## 恢复模式的作用以及为何要启用它

Aspose.Words 在将 Word 文件内部结构解析为 `Document` 对象之前会先进行解析。当文件损坏——缺失部分、XML 损坏或关系无效时，解析器可以：

| 模式 | 行为 |
|------|------|
| `STRICT` | 在检测到任何损坏时立即抛出异常。 |
| `IGNORE_ERRORS` | 跳过不可读取的部分，但可能会悄然丢失内容。 |
| `RECOVER`（**启用恢复模式**选项） | 尝试重建文档，尽可能保留内容，并通过 `load_options.recovery_mode` 暴露所选模式。 |

在必须 **恢复损坏的 Word 文档** 以进行后续处理（如提取文本或转换为 PDF）时，推荐使用 `RECOVER`。

## 步骤 1：创建加载选项并启用恢复模式

第一步是实例化 `LoadOptions` 并将 `recovery_mode` 属性设为 `RecoveryMode.RECOVER`。这会告诉库在解析期间进入恢复路径。

```python
import aspose.words as aw

# Step 1: Create load options and enable recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER  # alternatives: .IGNORE_ERRORS, .STRICT
```

**原因说明：**  
如果跳过此步骤且文档已损坏，构造函数 `aw.Document(...)` 将抛出 `InvalidOperationException`。启用恢复模式可防止崩溃，并为您提供一个部分修复的 `Document` 对象，仍可继续使用。

## 步骤 2：使用指定的选项加载可能损坏的文档

将 `load_options` 实例传递给 `Document` 构造函数。加载器现在会自动应用恢复算法。

```python
# Step 2: Load the potentially corrupted document using the specified options
doc_path = "YOUR_DIRECTORY/Corrupted.docx"
doc = aw.Document(doc_path, load_options)
```

**提示：** 将 `YOUR_DIRECTORY` 替换为运行时可访问的绝对或相对路径。如果文件不存在，Aspose.Words 会在进入恢复逻辑之前抛出 `FileNotFoundError`。

## 步骤 3：验证已应用恢复模式

通过检查 `load_options.recovery_mode` 可以确认当前使用的模式。这在日志记录或后续管道的条件处理时非常有用。

```python
# Step 3: Confirm that the document was loaded with the chosen recovery mode
print("Document loaded with recovery mode:", load_options.recovery_mode)
```

**预期输出**

```
Document loaded with recovery mode: RecoveryMode.RECOVER
```

如果输出显示 `RECOVER`，则说明您已成功 **启用恢复模式**，文档现在可以进行进一步处理（例如文本提取、转换为 PDF，或保存修复后的副本）。

## 步骤 4（可选）：保存修复后的副本以供以后使用

加载完成后，您可能希望持久化已恢复的文档，这样就不必重复恢复步骤。

```python
# Optional: Save the repaired document
repaired_path = "YOUR_DIRECTORY/Corrupted_Repaired.docx"
doc.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

保存后会生成一个新的 `.docx`，Aspose.Words 将其视为有效文件，可在 Microsoft Word 中打开且不会出现警告。

## 常见问题与边缘情况处理

| 问题 | 答案 |
|------|------|
| **如果文档完全无法读取怎么办？** | 即使在 `RECOVER` 模式下，某些文件也无法修复。`Document` 对象仍会被创建，但可能只包含一个空白页。请检查 `doc.get_page_count()` 以验证内容。 |
| **加载后能切换到 `IGNORE_ERRORS` 吗？** | 不能。恢复模式必须在 `Document` 构造函数运行 **之前** 设置。如果需要不同的策略，请创建新的 `LoadOptions` 实例。 |
| **恢复模式会影响性能吗？** | 会有少量开销，因为库会尝试重构损坏的部分。对大多数文件（< 2 MB）影响可以忽略不计。 |
| **此方法是否与语言无关？** | 相同的概念在 .NET、Java 和 Node.js API 中也存在（`LoadOptions.RecoveryMode`）。代码语法会变化，但逻辑完全相同。 |

## 专业提示：记录详细的恢复信息

Aspose.Words 提供了 `LoadOptions.recovery_callback`，可接收每个恢复步骤的详细信息。将其挂钩后，可帮助您诊断特定文档为何失败。

```python
def recovery_logger(message):
    print("[Recovery] ", message)

load_options.recovery_callback = recovery_logger
```

现在每一次内部修复（例如 “Removed duplicate relationship”）都会打印到控制台。

## 完整可运行示例

将所有部分组合在一起，下面是一个可直接复制粘贴并立即运行的脚本：

```python
import aspose.words as aw

def enable_recovery_and_load(doc_path: str, save_repaired: bool = False):
    # Create load options and enable recovery mode
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # Optional: attach a simple logger
    load_options.recovery_callback = lambda msg: print("[Recovery] ", msg)

    # Load the document with recovery enabled
    doc = aw.Document(doc_path, load_options)

    # Verify the mode
    print("Document loaded with recovery mode:", load_options.recovery_mode)

    # Show basic info
    print("Page count:", doc.page_count)
    print("Word count:", doc.get_text().split())

    # Optionally save a repaired copy
    if save_repaired:
        repaired_path = doc_path.replace(".docx", "_repaired.docx")
        doc.save(repaired_path)
        print(f"Repaired document saved to {repaired_path}")

    return doc

if __name__ == "__main__":
    corrupted_path = "YOUR_DIRECTORY/Corrupted.docx"
    enable_recovery_and_load(corrupted_path, save_repaired=True)
```

运行脚本后会打印恢复模式、页数以及从修复文档中提取的单词列表。如果将 `save_repaired=True`，则会在原文件旁生成一个全新的干净文件。

## 结论

您现在已经掌握了如何在 Aspose.Words for Python 中 **启用恢复模式**，并可靠地 **恢复损坏的 Word 文档**。关键步骤如下：

1. 创建 `LoadOptions` 并将 `recovery_mode` 设置为 `RECOVER`。  
2. 使用该选项加载 `.docx`。  
3. 验证模式并可选地保存修复副本。

接下来，您可以进一步探索 **从恢复的文档中提取文本**、**转换为 PDF**，或 **为大型文档库实现批量恢复** 等主题。

---


## 接下来您应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您在项目中进一步使用 API 功能并探索替代实现方式。

- [Recover Corrupted DOCX – Complete Guide to Enable Recovery Mode & Get Page](/words/english/python-net/document-operations/recover-corrupted-docx-complete-guide-to-enable-recovery-mod/)
- [Recover Corrupted DOCX – Open & Load Word Document](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)
- [recover damaged docx with Aspose.Words – set recovery mode and load options](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}