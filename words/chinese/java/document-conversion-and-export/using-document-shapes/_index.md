---
date: 2026-02-16
description: 学习如何使用 Aspose.Words for Java 创建文本框、添加水印文字、对多个形状进行分组、设置形状的宽高比以及将形状放置在表格单元格中。
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: 如何在 Aspose.Words for Java 中创建文本框并使用文档形状
url: /zh/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用文档形状

## Aspose.Words for Java 中使用文档形状简介

在本综合指南中，**您将学习如何创建文本框**对象以及其他强大的形状。形状可让您在 Word 文档中添加注释、按钮、水印、SmartArt 等，使文档在视觉上更具吸引力和交互性。我们将通过实际示例，演示从插入一个简单的文本框到对多个形状进行分组、设置宽高比以及将形状放置在表格单元格内的完整过程。

## 快速答案
- **添加文本框的主要方式是什么？** 使用 `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`。
- **我可以将形状分组吗？** 可以 – 创建 `GroupShape` 并追加子形状。
- **如何锁定或解锁形状的宽高比？** 调用 `shape.setAspectRatioLocked(true/false)`。
- **可以使用形状添加水印吗？** 完全可以 – 插入 `Shape` 并使用 `TEXT_PLAIN_TEXT` 设置填充/描边。
- **SmartArt 图表在 Aspose.Words 中可用吗？** 可用 – 使用 `shape.hasSmartArt()` 检测，并通过 `shape.updateSmartArtDrawing()` 更新。

## 什么是文本框，为什么要创建文本框形状？

文本框是一个容器，可容纳格式化文本、图像或其他形状。使用 **创建文本框** 在自动化过程中，您可以在页面任意位置放置漂浮内容，非常适合注释、标注或装饰元素，而不会影响文档的主流布局。

## 如何添加形状

在编写代码之前，请确保项目中已引用 Aspose.Words for Java。如果尚未添加，请从官方网站下载库：

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### 向文档添加形状

## 如何对多个形状进行分组

`GroupShape` 允许您将多个独立形状视为一个整体，便于一起移动或旋转。

### 插入 GroupShape

下面是一个完整示例，创建一个组，添加两种不同的形状，并将该组插入文档。

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

## 如何创建文本框（create text box）

### 插入文本框形状

`insertShape` 方法使添加文本框变得简洁。以下示例展示了两种定位和旋转文本框的方式。

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

## 如何设置形状宽高比

### 管理宽高比

有时您需要形状在拉伸时不保持原始比例。下面的代码片段演示了如何解锁图像形状的宽高比。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## 如何将形状放置在表格单元格中

### 在表格单元格内放置形状

下面是一步步的示例，先创建表格，然后插入一个相对于页面定位的水印形状，该形状也可以放置在单元格内。

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

## 使用 SmartArt 形状

### 检测 SmartArt 形状

您可以使用 `hasSmartArt()` 方法在文档中编程式地查找 SmartArt 对象。

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### 更新 SmartArt 绘图

定位到 SmartArt 形状后，可通过 `updateSmartArtDrawing()` 刷新其内部绘图数据。

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## 结论

在本指南中，我们介绍了如何 **创建文本框** 对象、对多个形状进行分组、调整宽高比、在表格单元格内嵌入形状、添加水印以及使用 Aspose.Words for Java 操作 SmartArt 图表。这些技术使您能够以编程方式构建内容丰富、交互性强的 Word 文档。

## 常见问题

### 什么是 Aspose.Words for Java？

Aspose.Words for Java 是一个 Java 库，允许开发者以编程方式创建、修改和转换 Word 文档。它提供了丰富的功能和工具，支持多种文档格式的操作。

### 如何下载 Aspose.Words for Java？

您可以通过以下链接从 Aspose 官方网站下载 Aspose.Words for Java：  
[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### 使用文档形状有哪些好处？

文档形状为文档添加视觉元素和交互性，使其更具吸引力和信息量。通过形状，您可以创建标注、按钮、图像、水印等，提升整体用户体验。

### 我可以自定义形状的外观吗？

可以，您可以通过调整大小、位置、旋转和填充颜色等属性来自定义形状的外观。Aspose.Words for Java 提供了丰富的形状定制选项。

### Aspose.Words for Java 是否兼容 SmartArt？

兼容，Aspose.Words for Java 支持 SmartArt 形状，您可以在文档中处理复杂的图表和图形。

## Frequently Asked Questions

**Q: Can I combine a text box with an image inside the same shape?**  
A: Yes. Insert an image into the text box shape using `builder.insertImage()` after creating the shape, then adjust its layout as needed.

**Q: How do I ensure a watermark appears behind all document content?**  
A: Set the shape’s `WrapType` to `NONE` and adjust its `RelativeHorizontalPosition` and `RelativeVerticalPosition` to `PAGE`. This positions the watermark behind the main flow.

**Q: Is it possible to animate a grouped shape in Word?**  
A: While Aspose.Words can create and group shapes, animation features are not supported because they rely on Word’s UI capabilities.

**Q: What version of Aspose.Words is required for SmartArt support?**  
A: SmartArt detection and updating are available starting from Aspose.Words 20.9 for Java and later.

**Q: Does the library handle large documents with many shapes efficiently?**  
A: Yes. Use `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` or higher to improve performance on documents with many shapes.

---

**Last Updated:** 2026-02-16  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}