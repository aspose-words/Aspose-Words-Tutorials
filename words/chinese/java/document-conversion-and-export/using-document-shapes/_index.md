---
"description": "解锁 Aspose.Words for Java 中文档形状的强大功能。通过分步示例学习如何创建视觉效果引人入胜的文档。"
"linktitle": "使用文档形状"
"second_title": "Aspose.Words Java文档处理API"
"title": "在 Aspose.Words for Java 中使用文档形状"
"url": "/zh/java/document-conversion-and-export/using-document-shapes/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用文档形状


## Aspose.Words for Java 文档形状使用简介

在本指南中，我们将深入探讨 Aspose.Words for Java 中的文档形状。形状是创建视觉吸引力和交互性文档的关键元素。无论您需要添加标注、按钮、图像还是水印，Aspose.Words for Java 都能提供高效的工具。让我们通过源代码示例逐步探索如何使用这些形状。

## 文档形状入门

在开始编写代码之前，我们先来设置一下环境。确保你的项目已集成 Aspose.Words for Java。如果你还没有安装，可以从 Aspose 网站下载。 [下载 Aspose.Words for Java](https://releases.aspose.com/words/java/)

## 向文档添加形状

### 插入 GroupShape

一个 `GroupShape` 允许您将多个形状组合在一起。以下是如何创建和插入 `GroupShape`：

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

要插入文本框形状，您可以使用 `insertShape` 方法如下例所示：

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

您可以控制是否锁定形状的纵横比。以下是解锁形状纵横比的方法：

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### 将形状放置在表格单元格中

如果您需要在表格单元格内放置形状，则可以使用以下代码实现：

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
watermark.isLayoutInCell(true); // 如果要将形状放入单元格中，则在表格单元格外面显示该形状。
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

在本指南中，我们探索了 Aspose.Words for Java 中文档形状的奥秘。您学习了如何向文档中添加各种形状、操作其属性以及如何使用 SmartArt 形状。掌握这些知识后，您就可以轻松创建外观精美、交互性强的文档。

## 常见问题解答

### 什么是 Aspose.Words for Java？

Aspose.Words for Java 是一个 Java 库，允许开发人员以编程方式创建、修改和转换 Word 文档。它提供了丰富的功能和工具，可用于处理各种格式的文档。

### 如何下载适用于 Java 的 Aspose.Words？

您可以通过以下链接从 Aspose 网站下载 Aspose.Words for Java： [下载 Aspose.Words for Java](https://releases.aspose.com/words/java/)

### 使用文档形状有什么好处？

文档形状可为您的文档增添视觉元素和交互性，使其更具吸引力，信息量更大。您可以使用形状创建标注、按钮、图像、水印等，从而提升整体用户体验。

### 我可以自定义形状的外观吗？

是的，您可以通过调整形状的属性（例如大小、位置、旋转和填充颜色）来自定义形状的外观。Aspose.Words for Java 提供了丰富的形状自定义选项。

### Aspose.Words for Java 是否与 SmartArt 兼容？

是的，Aspose.Words for Java 支持 SmartArt 形状，允许您在文档中处理复杂的图表和图形。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}