---
category: general
date: 2026-09-21
description: 学习如何使用 C# 生成文档模板、填充 Word 模板并替换 DOCX 文件中的占位符——一步一步的指南。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- generate document template
- populate word template
- how to replace placeholder
- fill docx template
- replace text docx
language: zh
lastmod: 2026-09-21
og_description: 在 C# 中通过填充 Word 模板、替换占位符并保存已填充的 DOCX 文件来生成文档模板。请遵循本完整指南。
og_image_alt: Screenshot of a C# program generating and filling a DOCX template
og_title: 在 C# 中生成文档模板 – 用数据填充 DOCX 文件
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to generate document template, populate word template and
    replace placeholders in a DOCX file using C# – step‑by‑step guide.
  headline: How to generate document template and fill it with data in C#
  type: TechArticle
tags:
- C#
- DOCX
- template processing
title: 如何在 C# 中生成文档模板并填充数据
url: /zh/net/find-and-replace-text/how-to-generate-document-template-and-fill-it-with-data-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中生成文档模板并填充数据

如果您需要 **生成文档模板** 文件，以便在发票、合同或报告中重复使用，本指南将准确展示操作方法。您将学习如何 **填充 word 模板** 的占位符，用真实值替换它们，最终以编程方式 **填充 docx 模板** 文件。

创建可重复使用的模板可以消除手动复制粘贴，并确保所有生成文档的一致性。以下步骤适用于任何包含类似 `{{Name}}` 简单占位符的 `.docx` 文件。

## 前置条件

* 已安装 .NET 6.0 SDK 或更高版本  
* Visual Studio 2022（或您喜欢的任何 IDE）  
* **Aspose.Words for .NET** NuGet 包——它提供示例中使用的 `Document` 类  

您可以使用以下命令添加该包：

```bash
dotnet add package Aspose.Words
```

## 第一步：准备 Word 模板

创建一个 Word 文档（`Template.docx`），其中包含动态数据应出现的位置占位符。常用约定是使用双大括号：

```
Dear {{Name}},

Your order #{{OrderId}} has been shipped on {{ShipDate}}.
```

将文件保存在代码可以引用的文件夹中，例如 `C:\Docs\Template.docx`。

## 第二步：加载模板文档

第一步编程操作是将模板加载到内存中。`Document` 构造函数读取文件并构建可供操作的对象模型。

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Load the template document from disk
        string templatePath = @"C:\Docs\Template.docx";
        Document doc = new Document(templatePath);
```

**为什么重要：** 每次加载文件都会创建一个干净的副本，从而保证原始模板在后续运行中保持未被修改。

## 第三步：用实际数据替换占位符

Aspose.Words 提供了简洁的 `Range.Replace` 方法，可扫描文档中的特定字符串并进行替换。将调用封装在辅助方法中，以保持主流程整洁。

```csharp
        // Helper to replace a single placeholder
        void ReplacePlaceholder(string placeholder, string value)
        {
            // The placeholder includes the curly braces exactly as they appear in the template
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());
        }

        // Populate the template with real values
        ReplacePlaceholder("{{Name}}", "John Doe");
        ReplacePlaceholder("{{OrderId}}", "A12345");
        ReplacePlaceholder("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));
```

**工作原理：** `Range.Replace` 会遍历每个段落、表格单元格、页眉和页脚，确保所有出现的标记都被更新。这是 **如何替换占位符** 文本在 DOCX 文件中最可靠的方式。

### 处理多个出现和缺失的标记

* 如果占位符出现多次，`Replace` 会自动更新所有实例。  
* 如果占位符不存在，方法仅不执行任何操作——不会抛出异常。  
* 对于大型文档，可通过在所有替换完成之前禁用 `doc.UpdateFields()` 来提升性能。

## 第四步：保存填充后的文档

所有占位符替换完毕后，将结果写入新文件。将输出文件与原模板分离，可保留原始模板以供后续使用。

```csharp
        // Save the filled document to a new file
        string outputPath = @"C:\Docs\FilledTemplate.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**结果：** `FilledTemplate.docx` 现在包含了个性化的内容：

```
Dear John Doe,

Your order #A12345 has been shipped on September 21, 2026.
```

## 第五步：验证输出（可选）

如果您想通过编程方式确认替换是否成功，可以重新读取保存的文件并搜索预期的值：

```csharp
        Document verifyDoc = new Document(outputPath);
        bool nameReplaced = verifyDoc.Range.Text.Contains("John Doe");
        Console.WriteLine($"Name replacement successful: {nameReplaced}");
```

运行验证步骤时，如果占位符被正确替换，将打印 `true`。

## 常见陷阱与最佳实践提示

| 问题 | 产生原因 | 推荐解决方案 |
|-------|----------------|-----------------|
| **占位符包含多余空格** | `"{{ Name }}"` 与 `"{{Name}}"` 不匹配。 | 保持占位符标记没有空格，或在替换前两端进行 trim。 |
| **Word 添加隐藏格式** | Word 可能将占位符拆分到多个 run 中，导致 `Replace` 未能匹配。 | 使用 `Document.Range.Replace` 并将 `FindReplaceOptions` 的 `MatchCase = false` 与 `FindWholeWordsOnly = false` 设置。 |
| **大型文档导致性能下降** | 逐个替换标记会每次触发完整文档扫描。 | 在保存之前一次性批量替换，针对每个标记调用 `Range.Replace`。 |
| **保存到只读文件夹** | `doc.Save` 抛出 `UnauthorizedAccessException`。 | 确保目标目录具有写入权限，或选择用户可写路径（例如 `%TEMP%`）。 |

## 完整工作示例

下面是完整的、独立的程序示例，您可以复制、粘贴并运行。

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Paths – adjust to your environment
        string templatePath = @"C:\Docs\Template.docx";
        string outputPath   = @"C:\Docs\FilledTemplate.docx";

        // 1️⃣ Load the template document
        Document doc = new Document(templatePath);

        // 2️⃣ Replace placeholders
        void Replace(string placeholder, string value) =>
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());

        Replace("{{Name}}", "John Doe");
        Replace("{{OrderId}}", "A12345");
        Replace("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));

        // 3️⃣ Save the filled document
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");

        // 4️⃣ (Optional) Verify replacement
        Document verify = new Document(outputPath);
        Console.WriteLine($"Verification – name found: {verify.Range.Text.Contains("John Doe")}");
    }
}
```

**预期的控制台输出**

```
Document saved to C:\Docs\FilledTemplate.docx
Verification – name found: True
```

在 Microsoft Word 中打开 `FilledTemplate.docx`，即可看到个性化的文本。

## 结论

您现在已经了解如何 **生成文档模板**、**填充 word 模板**，以及通过 **如何替换占位符** 将真实数据写入 **填充 docx 模板** 文件。只要遵循最佳实践提示，此方法即可处理任意数量的占位符，并在大型文档中保持良好扩展性。

### 接下来做什么？

* **动态表格：** 使用 `DocumentBuilder` 根据集合插入行。  
* **条件章节：** 使用 `IF` 域隐藏或显示模板的部分内容。  
* **PDF 导出：** 调用 `doc.Save("output.pdf")` 生成填充文档的 PDF 版本。  

尝试这些变体，构建面向发票、合同或任何可重复报告的全功能文档生成引擎。

---


## 接下来应该学习什么？

以下教程涵盖与本指南技术密切相关的主题，帮助您进一步学习。每个资源都包含完整的代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [Word 文档 - 查找并替换文本](/words/english/net/find-and-replace-text/)
- [生成 Word 文档](/words/english/java/word-processing/generate-word-document/)
- [恢复损坏的 DOCX – 打开并加载 Word 文档](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}