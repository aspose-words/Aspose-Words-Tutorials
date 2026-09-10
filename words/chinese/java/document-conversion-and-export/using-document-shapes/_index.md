---
date: 2025-12-14
description: 学习如何使用 Aspose.Words for Java **插入图像形状**。本指南向您展示如何添加形状、创建文本框形状、在表格中放置形状、设置形状的宽高比以及添加标注形状。
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: 在 Aspose.Words for Java 中使用文档形状
url: /zh/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words for Java **插入图像形状**

在本综合教程中，您将了解如何使用 Aspose.Words for Java 将 **插入图像形状** 对象插入 Word 文档。无论是构建报告、营销材料还是交互式表单，形状都可以让您添加标注、按钮、文本框、水印，甚至 SmartArt。我们将逐步演示每个步骤，解释为何使用特定形状，并提供可直接运行的代码片段。

## 快速答案
- **添加形状的主要方式是什么？** 使用 `DocumentBuilder.insertShape` 或创建 `Shape` 实例并将其添加到文档树中。  
- **我可以将图像作为形状插入吗？** 可以——调用 `builder.insertImage`，然后将返回的 `Shape` 像其他形状一样处理。  
- **如何保持形状的宽高比？** 根据需要设置 `shape.setAspectRatioLocked(true)` 或 `false`。  
- **可以对形状进行分组吗？** 当然——将它们包装在 `GroupShape` 中，并将该组作为单个节点插入。  
- **SmartArt 图表在 Aspose.Words 中可用吗？** 可以，您可以通过编程方式检测并更新 SmartArt 形状。

## 什么是 **插入图像形状**？
*图像形状* 是一种可视元素，用于在 Word 文档中容纳光栅或矢量图形。在 Aspose.Words 中，图像由 `Shape` 对象表示，您可以完全控制其大小、位置、旋转和环绕方式。

## 为什么在文档中使用形状？
- **视觉冲击力：** 形状能够吸引对关键信息的注意。  
- **交互性：** 按钮和标注可以链接到 URL 或书签。  
- **布局灵活性：** 使用绝对或相对坐标精确定位图形。  
- **自动化：** 在无需手动编辑的情况下生成复杂布局。

## 前提条件
- Java Development Kit (JDK 8 或更高版本)  
- Aspose.Words for Java 库（从官方网站下载）  
- 基本的 Java 及面向对象编程知识  

您可以在此下载库： [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## 如何 **添加形状** – 插入 GroupShape
`GroupShape` 允许您将多个形状视为一个单元。这对于一起移动或格式化多个元素非常有用。

```java
Document doc = new Document();
doc.ensureMinimum();

GroupShape groupShape = new GroupShape(doc);
Shape accentBorderShape = new Shape(doc, ShapeType.ACCENT_BORDER_CALLOUT_1);
accentBorderShape.setWidth(100.0);
accentBorderShape.setHeight(100.0);

groupShape.appendChild(accentBorderShape);

Shape actionButtonShape = new Shape(doc, ShapeType.ACTION_BUTTON_BEGINNING);
actionButtonShape.setLeft(100.0);
actionButtonShape.setWidth(100.0);
actionButtonShape.setHeight(200.0);

groupShape.appendChild(actionButtonShape);

groupShape.setWidth(200.0);
groupShape.setHeight(200.0);
groupShape.setCoordSize(new Dimension(200, 200));

DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertNode(groupShape);

doc.save("Your Directory Path" + "WorkingWithShapes.AddGroupShape.docx");
```

## 创建 **文本框形状**
文本框是一个可以容纳格式化文本的容器。您还可以旋转它以获得动态效果。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertShape(ShapeType.TEXT_BOX, RelativeHorizontalPosition.PAGE, 100.0,
    RelativeVerticalPosition.PAGE, 100.0, 50.0, 50.0, WrapType.NONE);

shape.setRotation(30.0);
builder.writeln();

shape = builder.insertShape(ShapeType.TEXT_BOX, 50.0, 50.0);
shape.setRotation(30.0);

OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);

doc.save("Your Directory Path" + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## 设置 **形状宽高比**
有时您需要形状自由拉伸，有时又想保持其原始比例。控制宽高比非常简单。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## 将 **形状放入表格**
在表格单元格中嵌形状对于报告布局非常方便。下面的示例创建一个表格，然后插入一个跨整页的水印样式形状。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();
builder.getRowFormat().setHeight(100.0);
builder.getRowFormat().setHeightRule(HeightRule.EXACTLY);

for (int i = 0; i < 31; i++) {
    if (i != 0 && i % 7 == 0)
        builder.endRow();

    builder.insertCell();
    builder.write("Cell contents");
}

builder.endTable();

Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.isLayoutInCell(true); // Display the shape outside of the table cell if it will be placed into a cell.
watermark.setWidth(300.0);
watermark.setHeight(70.0);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setRotation(-40);
watermark.setFillColor(Color.GRAY);
watermark.setStrokeColor(Color.GRAY);
watermark.getTextPath().setText("watermarkText");
watermark.getTextPath().setFontFamily("Arial");
watermark.setName("WaterMark_{Guid.NewGuid()}");
watermark.setWrapType(WrapType.NONE);

Run run = (Run) doc.getChildNodes(NodeType.RUN, true).get(doc.getChildNodes(NodeType.RUN, true).getCount() - 1);
builder.moveTo(run);
builder.insertNode(watermark);

doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010);
doc.save("Your Directory Path" + "WorkingWithShapes.LayoutInCell.docx");
```

## 添加 **标注形状**
标注形状非常适合突出显示注释或警告。虽然上面的代码已经演示了 `ACCENT_BORDER_CALLOUT_1`，您可以将 `ShapeType` 替换为任何标注变体以符合您的设计需求。

## 使用 SmartArt 形状

### 检测 SmartArt 形状
可以通过编程方式识别 SmartArt 图表，从而根据需要处理或替换它们。

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### 更新 SmartArt 绘图
检测到后，您可以刷新 SmartArt 图形以反映任何数据更改。

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## 常见问题与技巧
- **形状未显示：** 确保使用 `builder.insertNode` 将形状插入到目标节点之后。  
- **意外旋转：** 请记住旋转是围绕形状中心进行的；如有需要，调整 `setLeft`/`setTop`。  
- **宽高比被锁定：** 默认情况下，许多形状会锁定宽高比；调用 `setAspectRatioLocked(false)` 可自由拉伸。  
- **SmartArt 检测失败：** 请确认您使用的 Aspose.Words 版本支持 SmartArt（v24+）。

## 常见问题

**问：什么是 Aspose.Words for Java？**  
**答：** Aspose.Words for Java 是一个 Java 库，允许开发者以编程方式创建、修改和转换 Word 文档。它提供了广泛的功能和工具，用于处理各种格式的文档。

**问：如何下载 Aspose.Words for Java？**  
**答：** 您可以通过以下链接从 Aspose 官方网站下载 Aspose.Words for Java： [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**问：使用文档形状有哪些好处？**  
**答：** 文档形状为您的文档添加视觉元素和交互性，使其更具吸引力和信息性。通过形状，您可以创建标注、按钮、图像、水印等，提升整体用户体验。

**问：我可以自定义形状的外观吗？**  
**答：** 是的，您可以通过调整大小、位置、旋转和填充颜色等属性来自定义形状的外观。Aspose.Words for Java 提供了丰富的形状自定义选项。

**问：Aspose.Words for Java 是否兼容 SmartArt？**  
**答：** 是的，Aspose.Words for Java 支持 SmartArt 形状，您可以在文档中处理复杂的图表和图形。

---

**最后更新：** 2025-12-14  
**测试环境：** Aspose.Words for Java 24.12 (latest)  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}