---
date: 2026-02-19
description: 学习如何使用 Aspose.Words for Java 创建带水印的文档，并添加图像水印，以实现专业外观的文档。
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: 使用 Aspose.Words for Java 创建带水印的文档
url: /zh/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for Java 创建带水印的文档

在本教程中，您将使用 Aspose.Words for Java API **创建带水印的文档**。水印（无论是文字还是图片）可帮助您将文件标记为机密、草稿或已批准，并且可以以编程方式应用到任何 Word 文档。我们将逐步演示如何设置库、添加文字和图片水印、定制其外观，以及在不再需要时删除水印。

## 快速答案
- **水印的作用是什么？** 它在每页上覆盖文字或图片，以传达状态或品牌信息。  
- **哪个库在 Java 中添加水印？** Aspose.Words for Java 提供内置的水印支持。  
- **我可以添加图片水印吗？** 可以——使用 `Shape` 类并采用 `add image watermark java` 方法。  
- **水印可以半透明吗？** 可以通过 `setSemitransparent` 为文字水印控制不透明度。  
- **需要许可证吗？** 免费试用可用于测试；生产环境需要商业许可证。

## 什么是水印，为什么要使用它？

水印是一种淡淡的覆盖层——文字或图形——添加到文档的每一页。它常用于表示 **机密**、**草稿状态** 或 **品牌标识**，而不会改变文档的实际内容。以编程方式添加水印可确保在大量文件中保持一致性，并且比手动编辑更省时。

## 设置 Aspose.Words for Java

在开始添加水印之前，请确保库已在项目中就绪：

1. 从 [here](https://releases.aspose.com/words/java/) 下载 Aspose.Words for Java。  
2. 将下载的 JAR（或 Maven/Gradle 依赖）添加到项目的类路径中。  
3. 在 Java 源文件中导入所需的类：

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

库准备就绪后，让我们深入实际的水印代码。

## 如何添加文字水印

文字水印非常适合将文档标记为 “CONFIDENTIAL” 或 “DRAFT”。下面的代码片段展示了使用 `TextWatermarkOptions` **创建带水印的文档** 的简洁方式。

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

### 定制文字水印
- **字体族和大小** – 更改 `setFontFamily` 和 `setFontSize`。  
- **颜色** – 使用任意 `java.awt.Color`。  
- **布局** – 选择 `HORIZONTAL`、`DIAGONAL` 等。  
- **透明度** – 通过 `setSemitransparent(true)` 调整为更淡的外观。

## 如何添加图片水印（add image watermark java）

图片水印非常适合徽标或自定义图形。下面是 **add image watermark java** 示例，将 PNG 插入到每页的中心位置。

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

### 图片水印技巧
- **缩放** 使用 `setWidth` / `setHeight` 使其适配页面。  
- **位置** 可通过 `RelativeHorizontalPosition` / `RelativeVerticalPosition` 将其居中或对齐到任意边距。  
- **透明度** 可在加载前通过调整 PNG 的 alpha 通道实现。

## 如何删除水印

当文档不再需要水印时，可以通过编程方式将其删除。下面的代码遍历所有形状，删除名称中包含 “Watermark” 的对象。

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

## 常见问题与故障排除

- **保存后水印消失** – 确保在设置水印后调用 `doc.save()`。  
- **图片未显示** – 检查图片路径是否正确，且文件格式受支持（PNG、JPEG、BMP）。  
- **透明度未生效** – `setSemitransparent(true)` 仅对文字水印有效；对图片需在加载前编辑 PNG 的 alpha 通道。  
- **多节文档** – 如果文档包含多个节，需要在每个节的 body 中添加水印，或使用 `doc.getWatermark().setText(...)` 全局应用。

## 常见问答

**Q: 如何更改文字水印的字体？**  
A: 在 `TextWatermarkOptions` 中修改 `setFontFamily` 属性，例如 `options.setFontFamily("Times New Roman");`。

**Q: 能否在同一文档中添加多个水印？**  
A: 可以。为图片创建多个 `Shape` 对象，或对每个水印使用不同的选项调用 `doc.getWatermark().setText(...)`。

**Q: 水印可以旋转吗？**  
A: 对于图片水印，可在 `Shape` 对象上使用 `watermark.setRotation(angle)` 设置旋转角度。对于文字水印，使用 `setLayout` 属性（例如 `WatermarkLayout.DIAGONAL`）。

**Q: 如何使水印半透明？**  
A: 在 `TextWatermarkOptions` 中调用 `options.setSemitransparent(true)`。对于图片，在加载前调整图像的透明度。

**Q: 能否仅对文档的特定章节添加水印？**  
A: 可以。遍历 `doc.getSections()`，仅在需要的章节中添加水印。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**最后更新：** 2026-02-19  
**测试环境：** Aspose.Words for Java 24.12（最新）  
**作者：** Aspose