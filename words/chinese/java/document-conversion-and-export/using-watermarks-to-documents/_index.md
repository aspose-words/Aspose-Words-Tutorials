---
date: 2025-12-18
description: 了解如何使用 Aspose.Words for Java 为文档添加水印，包括图像水印示例、更改水印颜色、设置水印透明度以及删除文档水印。
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: 如何使用 Aspose.Words for Java 为文档添加水印
url: /zh/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words for Java 为文档添加水印

## Aspose.Words for Java 中向文档添加水印的介绍

在本教程中，您将学习 **如何使用 Aspose.Words for Java 为 Word 文档添加水印**。水印是一种快速标记文件为机密、草稿或已批准的方式，既可以是文字形式，也可以是图片形式。我们将演示如何设置库、创建文字和图片水印、定制水印外观（包括更改水印颜色和设置水印透明度），以及在不再需要时如何删除文档中的水印。

## 快速答疑
- **什么是水印？** 出现在文档主体内容后面的半透明覆盖层（文字或图片）。  
- **可以添加多个水印吗？** 可以——创建多个 `Shape` 对象并将它们分别添加到所需的章节。  
- **如何更改水印颜色？** 调整 `TextWatermarkOptions` 中的 `Color` 属性。  
- **有图片水印的示例吗？** 请参见下文的 “添加图片水印” 部分。  
- **删除水印需要许可证吗？** 生产环境使用时需要有效的 Aspose.Words 许可证。

## 设置 Aspose.Words for Java

在开始向文档添加水印之前，需要先设置 Aspose.Words for Java。请按以下步骤操作：

1. 从 [here](https://releases.aspose.com/words/java/) 下载 Aspose.Words for Java。  
2. 将 Aspose.Words for Java 库添加到您的 Java 项目中。  
3. 在 Java 代码中导入所需的类。

库配置完成后，让我们深入实际的水印创建过程。

## 添加文字水印

文字水印是想在文档中加入文字信息时的常见选择。下面演示如何使用 Aspose.Words for Java 添加文字水印：

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

**为何重要：** 通过调节 `setFontFamily`、`setFontSize` 和 `setColor`，您可以 **更改水印颜色** 以匹配品牌风格；而 `setSemitransparent(true)` 则可以 **设置水印透明度**，实现更柔和的效果。

## 添加图片水印

除了文字水印，您还可以向文档添加图片水印。下面是一个 **图片水印示例**，演示如何嵌入 PNG 徽标或印章：

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

您可以使用不同的图片或位置重复此代码块，以 **在同一文件中添加多个水印**。

## 定制水印

您可以通过调整外观和位置来自定义水印。对于文字水印，可更改字体、大小、颜色和布局；对于图片水印，可修改尺寸、旋转角度和对齐方式，正如前面的示例所示。

## 删除水印

如果需要 **删除文档中的水印**，下面的代码会遍历所有形状并删除被识别为水印的对象：

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## 常见使用场景与技巧

- **机密草稿：** 应用半透明文字水印，例如 “CONFIDENTIAL”。  
- **品牌化：** 使用包含公司徽标的图片水印。  
- **章节特定水印：** 循环 `doc.getSections()`，仅在选定的章节添加水印。  
- **性能技巧：** 在对多个文档应用相同水印时，复用同一个 `TextWatermarkOptions` 实例。

## 常见问题

### 如何更改文字水印的字体？

要更改文字水印的字体，请在 `TextWatermarkOptions` 中修改 `setFontFamily` 属性。例如：

```java
options.setFontFamily("Times New Roman");
```

### 能否在同一文档中添加多个水印？

可以，通过创建多个具有不同设置的 `Shape` 对象并将它们添加到文档中，实现多个水印的添加。

### 水印可以旋转吗？

可以，通过在 `Shape` 对象中设置 `setRotation` 属性来旋转水印。正值顺时针旋转，负值逆时针旋转。

### 如何使水印半透明？

在 `TextWatermarkOptions` 中将 `setSemitransparent` 属性设为 `true`，即可使水印半透明。

### 能否只在文档的特定章节添加水印？

可以，遍历章节并在需要的章节中添加水印，即可实现对特定章节的水印添加。

---

**最后更新：** 2025-12-18  
**测试环境：** Aspose.Words for Java 24.12  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}