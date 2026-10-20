---
category: general
date: 2026-09-18
description: 使用 Aspose.Words 创建空白文档并向 Word 插入形状——了解如何添加三角形形状及更多。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: zh
lastmod: 2026-09-18
og_description: 使用 Aspose.Words 在 Word 中创建空白文档，并学习如何插入三角形形状、组合形状以及其他图形。请遵循本完整指南。
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: 创建空白文档并向 Word 添加形状——一步一步指南
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: 如何创建空白文档并向 Word 添加形状
url: /zh/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何创建空白文档并向 Word 添加形状

如果您需要 **创建空白文档** 并随后使用图形丰富它，本指南将一步步演示具体操作。我们将从零开始创建 Word 文件并 **向 Word 添加形状**，包括 **如何插入三角形** 形状，使用 Aspose.Words for Java。

完成本教程后，您将得到一个可直接使用的 *.docx* 文件，其中包含一个包含三角形的组合形状。步骤涵盖从项目设置到保存最终 **create word document** 的全部过程。除 Aspose.Words 外，无需任何外部工具。

## 前置条件

在开始之前，请确保您具备：

* 已安装 Java 17 或更高版本  
* 用于依赖管理的 Maven 或 Gradle  
* Aspose.Words for Java 许可证（免费评估版可用于本演示）  

如果您使用其他构建系统，请相应调整依赖语法。该代码可在任何支持 Java 的平台上运行。

## 使用 Aspose.Words 创建空白文档

第一步是在内存中 **创建空白文档**。Aspose.Words 提供了 `Document` 类，用于表示一个没有任何内容的 Word 文件。

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

`new Document()` 构造函数会生成一个空的 *.docx* 结构，您可以随后向其中添加段落、表格或图形。由于文档是空白的，您可以完全控制后续添加的每个元素。

## 向 Word 添加形状 – 插入组合形状

组合形状允许您将多个图形视为一个整体。这在需要一起移动或缩放多个形状时非常有用。

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` 是添加内容的主要 API。`insertGroupShape` 调用会创建一个 300 × 300 点（约 4 × 4 英寸）的容器。此调用后，光标会定位在 *组内部*，准备插入更多形状。

### 为什么使用组合形状？

对相关图形进行分组可以保持对齐，并且更容易统一设置格式。如果以后决定移动三角形，整个组会一起移动，从而保持布局不变。

## 如何在组内插入三角形形状

接下来我们说明 **如何插入三角形** 形状。三角形是内置的 `ShapeType` 值之一。

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

`moveTo` 调用确保构建器的插入点位于组的第一个段落。随后 `insertShape` 会添加一个 60 × 60 点的三角形。由于光标位于组内部，三角形会成为该组合形状的子对象。

**插入三角形形状** 小贴士：

* 大小以点为单位；72 点等于一英寸。根据布局需要调整尺寸。  
* 如需不同方向，可使用 `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` 在组内对齐形状。  
* 除非使用 `shape.getFillColor()` 或 `shape.getStrokeColor()` 覆盖，否则三角形会继承组的填充和线条样式。

## 保存文档 – create word document

构建完图形后，您需要保存文件。这一步完成 **create word document** 操作。

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` 将内存中的表示写入磁盘，生成标准的 Word 文档。您可以在 Microsoft Word、LibreOffice 或任何支持 OOXML 格式的查看器中打开 `ExtendedGroup.docx`。文件将显示一个包含三角形的组合形状，正如代码所构建的那样。

## 完整可运行示例

将所有代码片段组合在一起，下面是完整的程序，您可以复制、编译并运行：

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### 预期结果

打开 `ExtendedGroup.docx` 后，您会看到页面中心有一个单独的组合形状。组内部默认位置出现一个小三角形。该三角形可以作为组的一部分被选中并移动，证明 **add shapes to word** 已成功实现。

## 常见问题与边缘情况

| 问题 | 答案 |
|----------|--------|
| *我可以在组内添加多个形状吗？* | 可以。在插入三角形后，保持光标在组内，再次调用 `builder.insertShape` 并使用不同的 `ShapeType` 即可。 |
| *如果我需要三角形是红色的怎么办？* | 获取 `insertShape` 返回的 `Shape`，然后调用 `shape.getFillColor().setColor(Color.RED)`。 |
| *这能用于旧的 .doc 文件吗？* | Aspose.Words 会按您指定的格式保存。使用 `doc.save("file.doc", SaveFormat.DOC)` 可创建传统的 Word 文档。 |
| *如何更改组合的边框？* | 使用 `group.getStrokeColor().setColor(Color.BLUE)` 并调用 `group.setLineWeight(2.0)` 来自定义轮廓。 |
| *有没有办法旋转三角形？* | 调用 `shape.getRotation()` 并设置角度（单位：度）。 |

## 专业技巧

* **复用 builder** – 为每个形状创建新的 `DocumentBuilder` 会增加开销。整个文档只保留一个 builder。  
* **单位转换** – 若使用毫米，可将其转换为点（`points = mm * 2.83465`）。  
* **性能优化** – 对于大型文档，所有形状添加完毕后仅调用一次 `doc.updatePageLayout()`。

## 结论

现在您已经掌握了 **创建空白文档**、**向 Word 添加形状**，以及使用 Aspose.Words for Java **插入三角形** 形状的完整流程。完整示例展示了从空文件到保存 **create word document**、其中包含组合三角形的全流程。

接下来，您可以探索更多 `ShapeType` 值，应用自定义样式，或组合多个组来构建复杂图表。尝试不同的尺寸、颜色和位置，以精通 Java 中的 Word 自动化。

--- 

*准备好自动化您的下一份报告了吗？克隆示例代码，调整尺寸，并将代码集成到您自己的应用中吧。*


## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您在已有技巧的基础上进一步提升。每篇资源都提供完整可运行的代码示例和逐步解释，帮助您掌握更多 API 功能并探索在项目中的替代实现方式。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}