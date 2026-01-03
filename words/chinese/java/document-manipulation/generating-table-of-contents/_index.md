---
date: 2026-01-03
description: 了解如何在使用 Aspose.Words for Java 插入目录时调整页码。自定义目录样式，轻松创建文档。
linktitle: Generating Table of Contents
second_title: Aspose.Words Java Document Processing API
title: 使用 Aspose.Words for Java 调整页码并生成目录
url: /zh/java/document-manipulation/generating-table-of-contents/
weight: 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 调整页码并在 Aspose.Words for Java 中生成目录

在本教程中，您将学习如何 **调整页码** 并 **插入目录**（TOC），使用 Aspose.Words for Java。结构良好的目录可以让长文档更易于导航，微调页码对齐可以为读者提供专业的阅读体验。我们将演示如何创建文档、定制目录样式以及调整制表位，使页码恰好出现在您希望的位置。

## 快速答案
- **“调整页码”是什么意思？** 修改目录中对齐页码的制表位。  
- **我可以自动插入目录吗？** 可以——使用 `FieldToc` 类。  
- **运行代码需要许可证吗？** 开发阶段可使用免费试用版；生产环境需要许可证。  
- **支持哪个 Aspose 版本？** 示例适用于最新的 Aspose.Words for Java 发行版。  
- **可以自定义目录样式吗？** 当然——您可以更改字体、粗体等属性。

## Aspose.Words 中的目录是什么？
目录是一种字段，它会扫描文档中的标题样式（例如 Heading 1、Heading 2），并生成带有页码的条目列表。Aspose.Words 允许您以编程方式插入此字段，并完全控制其外观。

## 为什么要在目录中调整页码？
调整制表位可以让您精确控制页码出现的位置，这对于以下需求至关重要：

- 保持整洁的列对齐布局。  
- 符合公司样式指南。  
- 提升打印和电子文档的可读性。

## 前置条件
- 已在项目中添加 Aspose.Words for Java（Maven/Gradle）。  
- 具备基本的 Java 语法知识。  

## 步骤指南

### 步骤 1：创建新文档
首先，实例化一个空的 `Document` 对象，用于保存您的内容和目录。

```java
Document doc = new Document();
```

### 步骤 2：定制目录样式
您可以更改每个目录级别的外观。本示例将一级目录条目设为粗体，这是常见的格式需求。

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

### 步骤 3：向文档添加内容
插入标题（例如 `Heading1`、`Heading2`）和普通段落。目录字段稍后会自动捕获这些标题。（为简洁起见，代码已省略——重点在于目录生成。）

### 步骤 4：插入目录字段
将目录放置在您希望的位置——通常在文档开头。

```java
// Insert a TOC field at the desired location in your document.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

### 步骤 5：保存文档
将文档持久化到磁盘。您可以选择任意受支持的格式，如 DOCX、PDF 或 HTML。

```java
doc.save("your_output_path_here");
```

## 定制目录中的制表位（调整页码）
如果默认的制表位未能满足您的对齐需求，您可以遍历所有目录段落并修改其制表位位置。

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Get the first tab used in this paragraph, which aligns the page numbers.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Remove the old tab.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Insert a new tab at a modified position (e.g., 50 units to the left).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

现在，目录条目的页码会精确显示在您想要的位置，使文档更显专业。

## 常见问题与技巧
- **目录中缺少标题：** 确保您的标题使用内置样式（`Heading1`、`Heading2` 等），或将自定义样式映射到目录级别。  
- **制表位未生效：** 核实段落实际属于目录样式（`TOC_1`‑`TOC_9`）。  
- **大文档性能问题：** 在插入目录后调用 `doc.updateFields()`，一次性刷新所有条目。

## 常见问答

**问：如何更改目录条目的格式？**  
答：使用 `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`（其中 *X* 为级别 1‑9），并修改其字体、颜色或段落设置。

**问：如何为目录添加更多级别？**  
答：调整 `FieldToc` 开关 `\o "1-3"`（例如）以包含更多标题级别，然后更新相应的 `TOC_X` 样式。

**问：可以为特定目录条目单独设置制表位吗？**  
答：可以——如 “定制目录中的制表位” 部分所示，遍历段落并逐一修改制表位。

**问：能在 PDF 输出中生成目录吗？**  
答：完全可以。目录生成后，将文档保存为 PDF（`doc.save("output.pdf")`），字段会自动渲染。

**问：是否需要手动调用 `updateFields()`？**  
答：插入 `FieldToc` 时，Aspose.Words 会在保存时自动更新，但手动调用 `doc.updateFields()` 可在调试时立即看到效果。

## 结论
您已经学习了如何使用 Aspose.Words for Java **调整页码**、**插入目录**，以及 **定制目录样式**。这些技巧帮助您创建结构清晰、易于导航且符合专业出版标准的文档。

---  

**最后更新：** 2026-01-03  
**测试环境：** Aspose.Words for Java（最新发行版）  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}