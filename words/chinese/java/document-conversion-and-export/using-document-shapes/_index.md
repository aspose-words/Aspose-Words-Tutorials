---
title: 在 Aspose.Words for Java 中使用文档形状
linktitle: 使用文档形状
second_title: Aspose.Words Java 文档处理 API
description: 解锁 Aspose.Words for Java 中文档形状的强大功能。通过分步示例学习如何创建具有视觉吸引力的文档。
weight: 14
url: /zh/java/document-conversion-and-export/using-document-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用文档形状


## Aspose.Words for Java 中使用文档形状的简介

在本综合指南中，我们将深入研究 Aspose.Words for Java 中的文档形状世界。形状是创建具有视觉吸引力和交互性的文档时必不可少的元素。无论您需要添加标注、按钮、图像还是水印，Aspose.Words for Java 都提供了高效完成这些操作的工具。让我们通过源代码示例逐步探索如何使用这些形状。

## 开始使用文档形状

在开始编写代码之前，让我们先设置环境。确保已将 Aspose.Words for Java 集成到项目中。如果尚未集成，可以从 Aspose 网站下载[下载 Aspose.Words for Java](https://releases.aspose.com/words/java/)

## 向文档添加形状

### 插入 GroupShape

一个`GroupShape`允许您将多个形状组合在一起。以下是创建和插入`GroupShape`：

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

### 插入文本框形状

要插入文本框形状，您可以使用`insertShape`方法如下例所示：

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

## 操作形状属性

### 管理宽高比

您可以控制是否锁定形状的纵横比。以下是如何解锁形状的纵横比：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### 将形状放置在表格单元格中

如果您需要在表格单元格内放置形状，可以使用以下代码实现：

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
watermark.isLayoutInCell(true); //如果要将其放入单元格中，则在表格单元格外部显示该形状。
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

您可以使用以下代码检测文档中的 SmartArt 形状：

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### 更新 SmartArt 绘图

要更新文档中的 SmartArt 绘图，请使用以下代码：

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## 结论

在本指南中，我们探索了 Aspose.Words for Java 中的文档形状世界。您已经学习了如何向文档添加各种形状、操作其属性以及如何使用 SmartArt 形状。有了这些知识，您可以轻松创建具有视觉吸引力和交互性的文档。

## 常见问题解答

### 什么是 Aspose.Words for Java？

Aspose.Words for Java 是一个 Java 库，允许开发人员以编程方式创建、修改和转换 Word 文档。它提供了广泛的功能和工具来处理各种格式的文档。

### 如何下载适用于 Java 的 Aspose.Words？

您可以通过以下链接从 Aspose 网站下载 Aspose.Words for Java：[下载 Aspose.Words for Java](https://releases.aspose.com/words/java/)

### 使用文档形状有哪些好处？

文档形状可为您的文档添加视觉元素和交互性，使其更具吸引力和信息量。借助形状，您可以创建标注、按钮、图像、水印等，从而增强整体用户体验。

### 我可以自定义形状的外观吗？

是的，您可以通过调整形状的属性（例如大小、位置、旋转和填充颜色）来自定义形状的外观。 Aspose.Words for Java 提供了广泛的形状自定义选项。

### Aspose.Words for Java 与 SmartArt 兼容吗？

是的，Aspose.Words for Java 支持 SmartArt 形状，允许您处理文档中的复杂图表和图形。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
