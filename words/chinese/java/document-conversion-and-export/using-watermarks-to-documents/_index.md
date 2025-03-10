---
title: 在 Aspose.Words for Java 中将水印应用于文档
linktitle: 使用水印到文档
second_title: Aspose.Words Java 文档处理 API
description: 了解如何在 Aspose.Words for Java 中向文档添加水印。自定义文本和图像水印，使文档看起来更专业。
weight: 15
url: /zh/java/document-conversion-and-export/using-watermarks-to-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中将水印应用于文档


## Aspose.Words for Java 中向文档添加水印的简介

在本教程中，我们将探索如何使用 Aspose.Words for Java API 向文档添加水印。水印是一种有用的方法，可以用文本或图形标记文档以指示其状态、机密性或其他相关信息。我们将在本指南中介绍文本和图像水印。

## 设置 Aspose.Words for Java

在开始向文档添加水印之前，我们需要设置 Aspose.Words for Java。请按照以下步骤开始：

1. 从以下网址下载 Aspose.Words for Java[这里](https://releases.aspose.com/words/java/).
2. 将 Aspose.Words for Java 库添加到您的 Java 项目。
3. 在 Java 代码中导入必要的类。

现在我们已经设置好了库，让我们继续添加水印。

## 添加文本水印

当您想在文档中添加文本信息时，文本水印是一种常见的选择。以下是使用 Aspose.Words for Java 添加文本水印的方法：

```java
//创建 Document 实例
Document doc = new Document("Document.docx");

//定义 TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

//设置水印文本和选项
doc.getWatermark().setText("Test", options);

//保存带水印的文档
doc.save("DocumentWithWatermark.docx");
```

## 添加图片水印

除了文本水印外，您还可以在文档中添加图像水印。添加图像水印的方法如下：

```java
//创建 Document 实例
Document doc = new Document("Document.docx");

//加载水印图片
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

//设置水印大小和位置
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

//为文档添加水印
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

//保存带水印的文档
doc.save("DocumentWithImageWatermark.docx");
```

## 自定义水印

您可以通过调整水印的外观和位置来自定义水印。对于文本水印，您可以更改字体、大小、颜色和布局。对于图像水印，您可以修改其大小和位置，如前面的示例所示。

## 删除水印

要从文档中删除水印，可以使用以下代码：

```java
//创建 Document 实例
Document doc = new Document("DocumentWithWatermark.docx");

//删除水印
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

//保存文档时不添加水印
doc.save("DocumentWithoutWatermark.docx");
```


## 结论

在本教程中，我们学习了如何使用 Aspose.Words for Java 向文档添加水印。无论您需要添加文本还是图像水印，Aspose.Words 都提供了自定义和高效管理水印的工具。您还可以在不再需要水印时将其删除，确保您的文档干净且专业。

## 常见问题解答

### 如何更改文本水印的字体？

要更改文本水印的字体，请修改`setFontFamily`财产在`TextWatermarkOptions`。 例如：

```java
options.setFontFamily("Times New Roman");
```

### 我可以在单个文档中添加多个水印吗？

是的，您可以通过创建多个`Shape`具有不同设置的对象并将它们添加到文档中。

### 可以旋转水印吗？

是的，您可以通过设置`setRotation`财产在`Shape`对象。正值表示顺时针旋转水印，负值表示逆时针旋转水印。

### 如何使水印变得半透明？

要使水印半透明，请设置`setSemitransparent`财产`true`在`TextWatermarkOptions`.

### 我可以在文档的特定部分添加水印吗？

是的，您可以通过遍历各个部分并将水印添加到所需部分来将水印添加到文档的特定部分。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
