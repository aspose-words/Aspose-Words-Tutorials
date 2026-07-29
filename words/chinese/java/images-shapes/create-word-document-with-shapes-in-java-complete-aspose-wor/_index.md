---
category: general
date: 2026-07-29
description: 使用 Aspose.Words 在 Java 中创建 Word 文档。学习在 Word 中插入矩形形状、对形状进行分组，并快速将文档保存为
  docx。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
- add shapes to word
language: zh
lastmod: 2026-07-29
og_description: 使用 Aspose.Words 在 Java 中创建 Word 文档。插入矩形形状，在 Word 中对形状进行分组，并在几分钟内将文档保存为
  docx。
og_image_alt: Screenshot showing how to create word document with grouped shapes using
  Java
og_title: 使用形状创建 Word 文档 – Java Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  headline: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  name: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  steps:
  - name: '## Create Word Document with Shapes Using Aspose.Words'
    text: The first thing you need is an empty Word file to work with. Aspose.Words
      makes this a one‑liner.
  - name: '## Insert Rectangle Shape and Other Shapes'
    text: Now we’ll add a blue rectangle and a green ellipse. The rectangle demonstrates
      the **insert rectangle shape** keyword, while the ellipse shows that you can
      mix shape types freely.
  - name: '## Group Shapes in Word for Easy Manipulation'
    text: Having two separate objects is fine, but often you want to move them together.
      That’s where **group shapes in word** shines.
  - name: '## Save Document as DOCX and Verify Output'
    text: Finally, we persist the file. This step fulfills the **save document as
      docx** requirement.
  - name: '## Full Working Example and Common Pitfalls'
    text: Below is the complete, ready‑to‑run Java class. Copy‑paste it into your
      project, adjust the output folder, and hit *Run*.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: 使用 Java 创建带形状的 Word 文档 – 完整 Aspose.Words 指南
url: /zh/java/images-shapes/create-word-document-with-shapes-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Java 创建带形状的 Word 文档 – 完整 Aspose.Words 指南

有没有想过如何以编程方式 **create word document** 并添加自定义图形？你并不是唯一有此想法的人。无论是需要生成带高亮部分的报告，还是即时设计传单，掌握 Word 中的形状处理都能为你节省大量手工工作时间。

在本教程中，我们将一步步演示如何使用 Aspose.Words for Java **create word document**，**insert rectangle shape**，**group shapes in Word**，以及最终 **save document as docx**。完成后，你将拥有一个可以直接放入任何项目的完整可运行示例。

## 您将收获的内容

- 一个完全由 Java 代码生成的全新 Word 文件。  
- 页面上添加了两种不同的形状（矩形和椭圆）。  
- 这些形状通过 **group shapes in word** API 捆绑在一起，表现为单个对象。  
- 文件以标准 `.docx` 格式保存在磁盘上，可在 Microsoft Word 中顺利打开。  

无需外部工具，无需繁琐的 XML hack——只需干净、类型安全的 Java 代码和 Aspose.Words。

---

## 前置条件

在开始之前，请确保你已经具备：

1. **Java Development Kit (JDK) 8 或更高版本** – 代码针对 Java 8+。  
2. **Aspose.Words for Java** JAR（可从 Maven Central 仓库获取最新版本）。  
3. 一个普通的 IDE（IntelliJ IDEA、Eclipse，或甚至是简单的文本编辑器）。  

如果你已经准备好，太好了——让我们开始吧。

---

## 步骤实现

下面我们将整个过程拆分为若干小步骤。每一步都包含代码片段、简短说明以及官方文档中可能没有的小技巧。

### ## 使用 Aspose.Words 创建带形状的 Word 文档

首先，你需要一个空的 Word 文件作为工作基准。Aspose.Words 只需一行代码即可完成。

```java
// Step 1: Initialise a blank document and a DocumentBuilder
Document doc = new Document();                 // Represents the Word file
DocumentBuilder builder = new DocumentBuilder(doc);
```

**为什么这很重要：**  
`Document` 是所有内容的容器——文本、表格、图像和形状。`DocumentBuilder` 是友好的助手，帮助你在不与底层对象搏斗的情况下添加内容。可以把它想象成直接在页面上书写的笔。

> **专业提示：** 如果您打算使用模板（例如公司信头），请将 `new Document()` 替换为 `new Document("template.docx")`。

### ## 插入矩形形状及其他形状

现在我们将添加一个蓝色矩形和一个绿色椭圆。矩形演示 **insert rectangle shape** 关键字，椭圆则展示了可以自由混合不同形状类型。

```java
// Step 2: Insert a rectangle shape (100x50 points) and set its appearance
Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
rect.setLeft(50);                               // X‑coordinate in points
rect.setTop(50);                                // Y‑coordinate in points
rect.getFill().setColor(java.awt.Color.BLUE);  // Fill color

// Step 3: Insert an ellipse shape (80x80 points) and configure it
Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
ellipse.setLeft(180);
ellipse.setTop(30);
ellipse.getFill().setColor(java.awt.Color.GREEN);
```

**内部原理是什么？**  
每次调用 `insertShape` 都会创建一个 `Shape` 对象，并自动将其添加到当前段落。`setLeft`/`setTop` 方法相对于页面边距定位形状，单位为点（1 pt = 1/72 in）。通过调整这些数值，你可以将形状放置在任意位置。

> **常见问题：** *我可以添加图片而不是纯色填充吗？*  
> 完全可以——只需使用 `shape.getFill().setImage("path/to/image.png")` 将填充颜色替换为图片。

### ## 在 Word 中对形状进行分组以便轻松操作

单独的两个对象可以工作，但通常你希望它们一起移动。这时 **group shapes in word** 就派上用场了。

```java
// Step 4: Create a GroupShape container and add the two shapes
GroupShape group = builder.insertGroupShape(); // Starts an empty group
group.appendChild(rect);
group.appendChild(ellipse);

// Step 5: Reposition the whole group as a single entity
group.setLeft(100);
group.setTop(150);
```

**为什么要分组？**  
当形状被分组后，任何变换——移动、旋转、缩放——都会作用于整个集合。这与在 Word UI 中手动选中多个形状后点击 *Group* 的行为一致。它还能简化后续代码，因为你只需调整一个对象，而不是多个。

> **特殊情况：** 如果以后需要取消分组，调用 `group.getParentNode().removeChild(group)` 并单独重新插入子形状即可。

### ## 将文档保存为 DOCX 并验证输出

最后，我们将文件持久化。这一步满足 **save document as docx** 的需求。

```java
// Step 6: Write the document to disk as a .docx file
String outputPath = "output/GroupShapeExample.docx";
doc.save(outputPath, SaveFormat.DOCX);
System.out.println("Document saved successfully to " + outputPath);
```

**预期结果：**  
在 Microsoft Word 中打开生成的 `GroupShapeExample.docx`。你会看到一个蓝色矩形和一个绿色椭圆已被整齐分组。拖动该组时，两者会一起移动，正如 UI 中的表现。

> **提示：** 如果需要 PDF 版本，使用 `SaveFormat.PDF`；相同代码无需修改即可工作。

### ## 完整工作示例及常见陷阱

下面是完整的、可直接运行的 Java 类。复制粘贴到项目中，调整输出文件夹路径，然后点击 *Run*。

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle shape and set its position and fill color
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rect.setLeft(50);
        rect.setTop(50);
        rect.getFill().setColor(java.awt.Color.BLUE);

        // Step 3: Insert a second ellipse shape and configure its position and fill color
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
        ellipse.setLeft(180);
        ellipse.setTop(30);
        ellipse.getFill().setColor(java.awt.Color.GREEN);

        // Step 4: Group the two shapes together using the new GroupShape API
        GroupShape group = builder.insertGroupShape();
        group.appendChild(rect);
        group.appendChild(ellipse);

        // Step 5: Optionally reposition the entire group as a single object
        group.setLeft(100);
        group.setTop(150);

        // Step 6: Save the document containing the grouped shapes
        String outPath = "output/GroupShapeExample.docx";
        doc.save(outPath, SaveFormat.DOCX);
        System.out.println("Document saved successfully to " + outPath);
    }
}
```

#### 常见陷阱及避免方法

| 问题 | 产生原因 | 解决方案 |
|-------|----------------|-----|
| **`NullPointerException` on `builder`** | 忘记在创建 `Document` 后实例化 `DocumentBuilder`。 | 确保在插入任何形状之前运行 `new DocumentBuilder(doc)`。 |
| **Shapes appear off‑page** | 使用像素值而非点，或未考虑页边距。 | 记住 Aspose.Words 使用点作为单位；72 pt = 1 in。相应调整 `setLeft`/`setTop`。 |
| **Group disappears after save** | 在保存组之后才向组中添加形状。 | 始终在调用 `doc.save()` 之前完成分组。 |
| **File not found on save** | 输出目录不存在。 | 通过代码创建目录（`new File("output").mkdirs();`）或使用已有路径。 |

---

## 结论

我们已经从零 **create word document**，**add shapes to word**，**insert rectangle shape**，**group shapes in word**，并最终 **save document as docx**——全部只用了几行 Java 代码。Aspose.Words 的强大之处在于其清晰的对象模型；你可以把 Word 文件当作画布，用形状在其上绘制，然后导出到任何需要的格式。

想更进一步？尝试将矩形换成星形，在形状内部使用 `Shape.getTextBox()` 添加文字，或尝试旋转（`shape.setRotationAngle(45)`）。API 功能丰富，可能性几乎无限。

对更高级的场景有疑问——比如将形状链接到书签或导出带嵌入字体的 PDF？在下方留言，我们一起深入探讨。祝编码愉快！

## 接下来您应该学习什么？

以下教程与本指南紧密相关，帮助你进一步掌握 API 功能并探索在项目中的替代实现方式。

- [创建 Word 文档 Java – 添加带阴影效果的矩形形状](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [在 Word 文档中使用 Aspose.Words for .NET 创建组形状](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words 在 Word 中创建矩形形状 – 步骤指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}