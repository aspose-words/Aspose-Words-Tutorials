---
category: general
date: 2026-10-20
description: 如何在 Aspose.Words for Java 中对形状进行分组——学习如何插入矩形形状、将它们分组并保存文档的完整指南。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: zh
lastmod: 2026-10-20
og_description: 如何在 Aspose.Words for Java 中对形状进行分组。本教程展示了如何插入矩形形状、对其进行分组并导出结果。
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: 如何在 Aspose.Words for Java 中对形状进行分组——一步一步的指南
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: 如何在 Aspose.Words for Java 中对形状进行分组
url: /zh/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words for Java 中对形状进行分组

如果您需要在使用 Aspose.Words for Java 的 Word 文档中**如何对形状进行分组**，本指南将展示完整的工作流程。您将学习如何**插入矩形形状**，添加第二个矩形，将这两个形状分组，最后保存文件——全部使用清晰、可运行的代码。

对形状进行分组在您想要将多个绘图作为一个单元移动、旋转或设置样式时非常有用。无论是构建报表模板、图表还是自定义传单，掌握形状分组都能为您节省时间并保持布局一致。

在本教程中，您将：

* 创建一个新的 `Document` 和一个 `DocumentBuilder`。
* **如何插入矩形** 形状并设置精确尺寸。
* 将矩形放入 `GroupShape` 中进行分组。
* 保存文档并验证结果。

> **先决条件** – 您必须在项目中添加 Aspose.Words for Java（v23.12 或更高）。Maven 用户可以在下面加入相应的依赖。

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## 您需要的环境

| 项目 | 原因 |
|------|--------|
| Java 17+ | 现代语言特性和更好的性能 |
| Aspose.Words for Java | 提供 `DocumentBuilder`、`Shape` 和 `GroupShape` API |
| IDE（IntelliJ IDEA、Eclipse、VS Code 等） | 用于编译和运行示例 |
| 对文件夹的写入权限 | 文档将保存到磁盘 |

---

## 如何插入矩形形状

第一步是创建一个 `Document` 和一个 `DocumentBuilder`。构建器提供诸如 `insertShape` 的方法来放置绘图对象。

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **为什么这很重要** – 使用 `insertShape` 是在 Aspose.Words 中**如何插入矩形**对象的标准方式。它会自动将形状添加到文档的当前段落，无需您手动处理底层 OpenXML。

---

## 调整矩形位置（可选）

如果第二个矩形需要相对于第一个矩形的自定义位置，您可以修改其 `left` 和 `top` 属性。此步骤是可选的，但在精确的图表布局中常常必需。

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **小贴士**：所有度量均以点为单位（1 pt ≈ 1/72 in）。如果需要 UI 计算的像素值，可使用 `convertPointsToPixels`。

---

## 如何对形状进行分组

现在矩形已经存在，您可以将它们放入 `GroupShape` 中。分组使两个矩形表现为单个对象——移动、旋转或格式化该组都会影响两个形状。

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **为什么分组有效** – `GroupShape` 继承自 `Shape`，因此您可以像对待其他绘图对象一样对待该组。当调用 `appendChild` 时，形状会从原位置移除并成为组的子对象。

---

## 保存包含分组形状的文档

最后，将文档写入磁盘。文件中将只包含一个包含两个矩形的 `GroupShape`。

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### 预期结果

在 Microsoft Word 中打开 `GroupShape.docx`：

* 您会看到两个并排放置的矩形（蓝色和绿色）。
* 选中任意一个矩形时会选中整个组——拖动时两者一起移动。
* 该组有一条细红色边框，表明已应用 `GroupShape` 的属性。

如果右键单击该组并选择 **Group → Ungroup**，矩形将恢复为独立形状，演示了分组操作是可逆的。

---

## 常见变体和边缘情况

| 情况 | 处理方法 |
|-----------|------------------|
| **超过两个形状** | 插入每个形状，然后全部追加到同一个 `GroupShape`。 |
| **不同的形状类型**（例如椭圆、图片） | 使用 `builder.insertShape(ShapeType.ELLIPSE, …)` 或 `builder.insertImage(...)` 再追加。 |
| **缩放组** | 调用 `group.setWidth(newWidth)` 或 `group.setHeight(newHeight)`；子形状按比例缩放。 |
| **旋转组** | `group.setRotationAngle(45);` 将整个集合围绕中心旋转。 |
| **保留原始位置** | 在分组前存储每个形状的 `left`/`top`，如有需要在取消分组后恢复。 |

---

## 完整、可运行的示例

下面是完整的 Java 类，您可以直接复制粘贴到 IDE 中使用。它包含所有导入、错误处理以及为清晰起见添加的注释。

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

运行程序，打开生成的 `GroupShape.docx`，您将看到如描述的那样分组的矩形。

---

## 结论

您现在已经掌握了在 Aspose.Words for Java 中**如何对形状进行分组**的完整流程，从创建文档、插入矩形形状、调整位置，到最终使用 `GroupShape` 进行分组。这一技术让您能够将多个绘图视为单一实体，简化布局调整并保持视觉一致性。

**后续步骤**

* 探索**如何插入矩形**形状的不同填充模式或边框。
* 将**插入矩形形状**与文本框结合，创建带标签的图表。
* 试验旋转或缩放组，以生成更复杂的图形。

欢迎根据其他形状类型、更大的组或动态文档生成场景自行调整代码。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，每个资源都提供完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [在 Java 中插入矩形形状 – 分组与定位形状](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [在 Java 中插入组形状 – 完整指南](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [在 Aspose.Words 中为形状设置阴影 – 完整指南](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}