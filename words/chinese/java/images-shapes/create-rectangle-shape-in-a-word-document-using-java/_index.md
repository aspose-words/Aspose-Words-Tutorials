---
category: general
date: 2026-11-15
description: 使用 Java 在 Word 中创建矩形形状，并学习如何向 Word 添加形状、设置形状尺寸以及高效保存 Word 文档。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: zh
lastmod: 2026-11-15
og_description: 使用 Java 在 Word 文档中创建矩形形状。学习向 Word 添加形状、设置形状尺寸，并在几分钟内保存 Word 文档。
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: 使用 Java 在 Word 中创建矩形形状 – 逐步指南
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: 使用 Java 在 Word 文档中创建矩形形状
url: /zh/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Java 在 Word 文档中创建矩形形状

如果您需要在 Word 文件中**创建矩形形状**，本指南将向您展示如何使用 Java 完成此操作。您将看到如何**向 Word 添加形状**、控制**设置形状尺寸**，以及最终**保存 Word 文档**，而无需离开 IDE。

在接下来的章节中，您将获得完整的可运行示例、每行代码的解释，以及针对常见问题（如尺寸问题和文档兼容性）的提示。无需外部引用——只需 Aspose.Words for Java 库。

## 您将学习的内容

* 如何初始化 `Document` 和 `DocumentBuilder`。
* 如何插入**组形状**并在其中放置矩形。
* 如何使用 `setWidth` 和 `setHeight` **定义形状大小**。
* 如何以 `.docx` 格式 **保存 Word 文档**。
* 针对不同页面尺寸和 DPI 设置的边缘情况处理。

### 前置条件

* Java 17 或更高版本（代码也可在 Java 8 上编译）。
* Aspose.Words for Java 23.10 或更新版本 – 可从 Maven Central 获取。
* 对 Java 语法和面向对象概念有基本了解。

> **专业提示：** 如果您计划以后添加更多形状（例如圆形或文本框），请将它们保存在同一个 `GroupShape` 中。这会使移动、旋转或格式化整个集合变得更加容易。

## 步骤 1：初始化文档和构建器

第一步是创建一个空白的 Word 文件，并创建一个允许您写入内容的 `DocumentBuilder`。

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*为什么这很重要：* `Document` 代表整个文件，而 `DocumentBuilder` 提供了插入文本、表格和**形状**的高级方法。没有构建器，您必须手动操作底层节点。

## 步骤 2：插入组形状以容纳多个形状

**组形状**充当容器；您可以添加多个形状，随后将它们视为单个对象（例如一起移动或旋转）。

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*为什么使用组形状？* 如果以后决定在矩形周围添加箭头、圆形或标签，组形状可以保持所有内容对齐。它还简化了**向 Word 添加形状**的工作流，因为每个新形状只需一次 `appendChild` 调用。

## 步骤 3：创建矩形形状

现在我们创建实际的矩形，它将位于组形状内部。`Shape` 构造函数需要所属的 `Document` 和您想要的形状类型。

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*为什么是矩形？* `ShapeType.RECTANGLE` 是用于突出显示章节、创建占位符或在 Word 中直接绘制简单 UI 原型的最常用基元。

## 步骤 4：定义矩形的尺寸

设置尺寸时，**设置形状尺寸**变得尤为重要。您可以使用 Aspose.Words 支持的任何计量单位；默认单位是点（1 pt = 1/72 英寸）。

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **注意：** 如果您更喜欢使用毫米，可以调用 `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));`，其中 `1.39 in ≈ 35 mm`。这展示了**定义形状大小**的灵活性。

## 步骤 5：将矩形添加到组形状

将矩形追加到先前创建的组形状后，它会出现在文档中。

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

此时矩形位于组形状的左上角。如果需要精确定位，可以稍后使用 `rectangle.setLeft(...)` 和 `rectangle.setTop(...)` 移动它。

## 步骤 6：(可选) 保存文档以查看结果

最后，将文档写入磁盘。这是**保存 Word 文档**的步骤，会生成一个 `.docx` 文件，您可以在 Microsoft Word、LibreOffice 或 Google Docs 中打开。

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

运行程序后会生成 `RectangleShapeDemo.docx`，其中包含一个位于组形状内的单个矩形。打开文件会看到一个纯白矩形——正是您定义的尺寸。

### 预期输出

* 一个名为 `RectangleShapeDemo.docx` 的 Word 文件。
* 在第一段落中，包含一个 100 pt × 50 pt 的矩形的组形状。
* 未添加任何文本，因此矩形出现在空白页上。

## 常见变体和边缘情况

| 情况 | 如何调整代码 |
|-----------|-----------------------|
| **不同页面尺寸**（例如 A4） | 在插入形状之前调用 `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);`。 |
| **更高的打印 DPI** | 将宽度/高度乘以所需的 DPI 系数，例如 `rectangle.setWidth(200 * 2);` 以实现双倍分辨率。 |
| **在矩形内部添加文字标签** | 创建类型为 `TEXT_BOX` 的 `Shape`，将其 `setWidth`/`setHeight` 设置为与矩形匹配，然后将其添加到同一 `GroupShape` 中。 |
| **旋转矩形** | 使用 `rectangle.setRotationAngle(45);` 将矩形顺时针旋转 45 度。 |
| **保存为 PDF 而非 DOCX** | 将 `document.save("output.docx");` 替换为 `document.save("output.pdf");` ——相同的 API 也适用于 PDF，且会保留矩形。 |

## 稳健实现的专业提示

1. **复用构建器** – 在插入组形状后，您可以继续添加段落或表格，而无需创建新的构建器实例。  
2. **释放资源** – 虽然 Java 的垃圾回收器会处理大多数对象，但显式调用 `document.close();`（如果使用流）可防止文件句柄泄漏。  
3. **验证尺寸** – 在调用 `setWidth`/`setHeight` 之前，确保数值为正；负值会抛出 `IllegalArgumentException`。  
4. **版本兼容性** – 代码适用于 Aspose.Words 23.x 及更高版本。早期版本可能需要使用 `Shape.setSize(width, height)` 而非单独的 setter。  

## 完整、可运行的示例

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **结果验证：** 在 Microsoft Word 中打开 `output/RectangleShapeDemo.docx`。您应该看到一个位于第一页顶部居中的指定尺寸矩形。如果矩形显得太小，请调整传递给 `setWidth` 和 `setHeight` 的数值。

## 结论

您现在已经掌握了如何使用 Java **创建矩形形状**，如何通过 `GroupShape` **向 Word 添加形状**，以及如何 **设置形状尺寸**、**定义形状大小**，并最终 **保存 Word 文档** 以便进一步分发。同样的模式适用于其他形状类型，帮助您以编程方式构建复杂图表。

### 接下来该做什么？

* 探索 **向 Word 添加形状**，通过插入圆形、箭头或文本框。  
* 将多个形状组合成单个 `GroupShape` 并应用变换（旋转、翻转）。  
* 生成嵌入图表的报告，然后 **保存 Word 文档** 为 PDF 以便共享。

随意尝试不同的尺寸、颜色和定位，以满足您的具体场景。祝编码愉快！

## 您接下来应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您在自己的项目中进一步掌握 API 功能并探索替代实现方式。每个资源都包含完整的可运行代码示例和分步解释。

- [创建 Word 文档 Java – 添加带阴影效果的矩形形状](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [在 Java Word 文档中创建矩形形状 – 完整分步指南](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [创建 Word 文档 Java – 隐藏形状并设置填充颜色](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}