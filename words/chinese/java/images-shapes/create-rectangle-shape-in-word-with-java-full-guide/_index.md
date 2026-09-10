---
category: general
date: 2026-02-10
description: 使用 Aspose.Words for Java 在 Word 文档中创建矩形形状。了解如何设置阴影颜色、如何添加阴影，以及如何以编程方式创建
  Word 文档。
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: zh
og_description: 使用 Aspose.Words for Java 在 Word 文档中创建矩形形状。按照本分步教程设置阴影颜色、添加阴影并创建 Word
  文档。
og_title: 使用 Java 在 Word 中创建矩形形状 – 完整指南
tags:
- Aspose.Words
- Java
- Document Automation
title: 使用 Java 在 Word 中创建矩形形状 – 完整指南
url: /zh/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 Java 创建矩形形状 – 完整指南

是否曾需要在 Word 文档中 **创建矩形形状**，却不知从何入手？你并不孤单——许多开发者在首次尝试以编程方式绘制 Word 图形时都会遇到这个难题。好消息是？使用 Aspose.Words for Java，你可以在页面上放置一个矩形，给它添加漂亮的阴影，并在几秒钟内保存文件。在本教程中，我们将逐步演示 **如何添加阴影**、**设置阴影颜色**，以及 **从头创建 Word 文档** 的完整过程。

我们将覆盖所有必需内容：所需的库、每一行代码、为何某些设置重要，以及官方文档中可能找不到的一些技巧。结束时，你将拥有一个可直接运行的示例，它会创建一个带柔和灰色阴影的矩形形状，并保存为 *Shadow.docx*。

## 前置条件 – 开始之前你需要准备的东西

在深入代码之前，请确保你具备以下条件：

| 要求 | 原因 |
|------|------|
| Java Development Kit (JDK) 8 或更高版本 | Aspose.Words 可在任何现代 JDK 上运行。 |
| Maven 或 Gradle（可选） | 简化添加 Aspose.Words 依赖。 |
| Aspose.Words for Java 许可证（或免费试用） | 该库为商业产品；试用版可用于测试。 |
| IDE（IntelliJ IDEA、Eclipse、VS Code 等） | 帮助你快速运行和调试示例。 |

如果你已经有一个 Java 项目，只需添加 Maven 坐标：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

不需要其他繁琐的设置——一个普通的 `public static void main` 方法即可。

![创建矩形形状示例](https://example.com/rectangle-shadow.png "在 Word 中创建带阴影的矩形形状")

*图片说明：创建矩形形状示例，展示一个带灰色阴影的青色矩形。*

## 第一步 – 创建一个新的 Word 文档

我们首先要做的是生成一个空白文档。可以把它想象成打开一个全新的 Word 文件，随后在其上绘制。

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

为什么要从空的 `Document` 开始？因为 Aspose.Words 将 `Document` 类视为后续所有操作的画布——添加段落、表格或形状。如果跳过这一步，一旦尝试插入任何内容就会抛出 `NullPointerException`。

## 第二步 – 设置 DocumentBuilder

`DocumentBuilder` 就是你的“笔”，用于向 `Document` 写入内容。它是推荐的添加内容方式，因为它会自动管理光标位置。

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

你可能会问：“为什么不直接操作 Document？”答案是：builder 抽象掉了诸如章节处理等底层细节，使代码更简洁、更不易出错。

## 第三步 – 插入矩形形状

下面进入有趣的部分——**如何创建形状**。我们将插入一个 100 × 50 点的矩形，并使用青色填充，以便能够清晰看到它。

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

几点说明：

* `ShapeType.RECTANGLE` 告诉 Aspose 我们需要一个矩形；你也可以换成 `OVAL`、`LINE` 等。
* 尺寸使用点（1 pt ≈ 1/72 英寸）表示。根据你的布局需求自行调整。
* 若不设置填充颜色，形状在白页上将不可见——因此使用青色。

## 第四步 – 添加阴影并 **设置阴影颜色**

这一步回答 **如何添加阴影** 的核心问题。`ShadowFormat` 对象控制阴影的所有视觉属性，包括颜色、模糊半径等。

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

为什么使用这些特定的值？

* **可见性** – 若不调用 `setVisible(true)`，其余设置将被忽略。
* **颜色** – 灰色是中性选择，适用于浅色和深色背景。你可以将 `java.awt.Color.GRAY` 替换为任意 `java.awt.Color`。
* **模糊半径** – `5.0` 产生柔和的羽化效果；更大的数值会让阴影更散。
* **OffsetX/Y** – 偏移量将阴影向右下移动，模拟光源来自左上方。
* **透明度** – 半透明阴影在页面上更自然，尤其是打印时。

如果想要更锐利的效果，可将模糊半径降至 `0` 并增大偏移量。鼓励自行实验——阴影高度依赖视觉感受，合适的设置取决于文档的整体设计。

## 第五步 – 保存文档

最后，将所有内容持久化为 `.docx` 文件。你可以自行决定保存路径，只需确保目录已存在。

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

当你在 Microsoft Word 中打开 *Shadow.docx* 时，会看到一个青色矩形，右下方偏移 4 pt，带有细微的灰色阴影。这就是完整的 **创建 Word 文档** 工作流。

### 预期结果

| 元素 | 外观 |
|------|------|
| 矩形 | 青色填充，大小 100 × 50 pt |
| 阴影 | 灰色，30 % 透明，5 pt 模糊，偏移 (4, 4) |
| 文件 | `Shadow.docx` 存储在你指定的路径下 |

如果形状未出现，请检查填充颜色是否与页面背景相同，并确认阴影已设为可见。

## 专业技巧与常见陷阱

* **技巧**：如果想为形状添加边框，可使用 `rectangle.setStrokeColor(java.awt.Color.BLACK);`。这在打印页上能让矩形更突出。
* **注意**：将文件保存到只读文件夹会抛出 `IOException`。请选择可写位置或调整文件权限。
* **特殊情况**：若需要透明填充（无颜色），可调用 `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);`。形状仍会投射阴影，可用于水印式图形。
* **性能提示**：在循环中添加数百个形状会增加内存占用。所有形状插入完毕后，仅调用一次 `document.save`。

## 完整可运行示例

下面是完整的程序代码，你可以直接复制粘贴到名为 `ShadowDemo` 的 Java 类中。只要类路径中包含 Aspose.Words JAR，即可编译运行。

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

运行程序，打开生成的 *Shadow.docx*，即可看到如描述的矩形及其阴影。

## 如果需要更多形状怎么办？

你可能会想，“能否 **多次创建矩形形状** 或使用其他形状？”答案是肯定的。只需在插入代码外层套上循环，并使用 `builder.moveTo` 或 `builder.insertParagraph` 调整坐标。相同的阴影设置可以抽取为辅助方法复用：

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

在每次插入形状后调用 `applyStandardShadow(rectangle);`，即可保持代码 DRY（Don’t Repeat Yourself）。

## 后续步骤 – 超越基础

既然已经掌握 **如何添加阴影**，可以进一步探索以下相关主题：

* **如何为文本运行设置阴影颜色** – 为标题增添细腻的立体感。
* **使用表格和图片创建 Word 文档** – 将形状与其他内容组合。
* **如何创建形状动画**，利用 Word 内置的...

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}