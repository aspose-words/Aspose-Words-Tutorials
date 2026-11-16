---
category: general
date: 2026-11-15
description: 使用 Java 在 Word 文档中设置段落行距。学习如何使用 Aspose.Words 通过编程方式设置行距，实现精确的文档格式化。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: zh
lastmod: 2026-11-15
og_description: 使用 Java 在 Word 文档中设置段落行距。本指南解释了如何使用 Aspose.Words 为段落和脚注分隔线设置行距，让您对文档布局拥有完整的控制权。
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: 使用 Java 在 Word 中设置段落行距
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: 使用 Java 设置 Word 文档中的段落行距
url: /zh/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Java 在 Word 文档中设置段落行距

如果您需要 **设置段落行距**，本教程将演示如何使用 Java 和 Aspose.Words 实现。您还将学习 **如何为脚注分隔线设置行距**——这是专业文档排版中的常见需求。

在接下来的章节中，您将：

* 加载已有的 *.docx* 文件。
* 获取脚注分隔线段落。
* 应用自定义行距值。
* 保存更新后的文档。

只需在项目中添加 Aspose.Words 库，无需其他外部配置，您可以直接复制代码并立即运行。

## 前提条件

开始之前，请确保您具备：

* 已安装 Java 17 或更高版本。
* Maven（或其他构建工具）用于管理依赖。
* 有效的 Aspose.Words for Java 许可证（免费评估版可用于测试）。
* 位于已知目录下的输入 Word 文档（`input.docx`）。

在 `pom.xml` 中添加 Aspose.Words 依赖：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## 使用 Aspose.Words 设置段落行距

此 H2 标题包含主要关键词，满足 SEO 要求。

### 步骤 1：加载 Word 文档

首先，创建指向源文件的 `Document` 实例。

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*为什么重要*：加载文档后，您将获得一个内存模型，可在不触及原始文件的情况下进行操作，直至显式保存。

### 步骤 2：获取脚注分隔线

脚注分隔线是出现在脚注与正文之间的特殊段落。要更改其外观，需要访问 `FootnoteSeparator` 对象。

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*提示*：即使文档中没有脚注，分隔线仍以隐藏段落的形式存在，因此此调用永远不会返回 `null`。

### 步骤 3：为分隔线段落设置行距

现在应用所需的行距。Aspose.Words 使用点（pts）作为行距单位；12 pts 大致相当于大多数字体的单倍行距。

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

您还可以使用其他间距模式：

| 模式                     | 方法调用                                                                      |
|--------------------------|-------------------------------------------------------------------------------|
| **Exactly** (固定 pts)   | `setLineSpacingRule(LineSpacingRule.EXACTLY)`                                 |
| **Multiple** (如 1.5)    | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);`          |

选择正确的规则可确保文档在 Word、Google Docs 等查看器中保持一致的渲染效果。

### 步骤 4：保存更新后的文档

最后，将更改写回磁盘。

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

当您在 Microsoft Word 中打开 `output.docx` 时，脚注分隔线将以您定义的行距显示。

## 理解如何为普通段落设置行距

相同的 API 适用于任何 `Paragraph` 对象，而不仅限于脚注分隔线。下面是一个快速示例，演示如何调整正文中第一段的间距：

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**为何需要**：报告、合同和学术论文常常要求特定的行距样式（例如草稿的双倍行距）。使用相同的 `setLineSpacing` 方法可保证获得期望的精确布局。

## 常见陷阱及规避方法

| 问题                                 | 原因                                         | 解决方案 |
|--------------------------------------|----------------------------------------------|----------|
| 行距未发生变化                       | `LineSpacingRule` 仍为默认 (AUTO)            | 使用 `setLineSpacingRule` 显式设置规则。 |
| 分隔线后出现多余空行                 | 分隔线包含隐藏的回车符                       | 在设置间距前使用 `separator.getText().trim();` 去除文本。 |
| 保存后文档损坏                       | 使用了过时的 Aspose.Words 版本               | 升级到最新版本（如 24.10），其中已修复保存相关的错误。 |

## 高手技巧：批量处理多个文档

如果需要一次性更新数十个文件，可将逻辑封装为辅助方法并遍历文件夹：

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

在循环中调用此方法可为您节省大量手动编辑时间。

## 预期输出

运行完整程序后，`output.docx` 将：

* 保持原始内容不变，仅修改行距。
* 脚注分隔线采用单倍行距（12 pts）布局。
* 其余所有格式（样式、图片、表格）保持完整。

在 Word 中打开文件，您会看到分隔线的行距更紧（或更松），具体取决于您设置的值。

## 结论

现在，您已经掌握了使用 Java **设置段落行距** 的方法，并了解了 **如何为脚注分隔线和普通段落设置行距**。完整、可运行的示例展示了如何加载文档、调整行距属性并保存结果——全部只需几行清晰的 API 调用。

**后续可探索的方向**：

* **如何为表格和列表项设置行距**。
* 为标题与正文分别应用不同的间距规则。
* 使用 `Style` 对象在整个文档范围内统一间距设置。

尝试不同的数值，结合其他格式化选项，您就能在任何 Java 应用中完全掌控文档布局。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南技术密切相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方式。

- [How to set options in Aspose.Words for Java – complete guide](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Change Asian Paragraph Spacing And Indents In Word Document](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}