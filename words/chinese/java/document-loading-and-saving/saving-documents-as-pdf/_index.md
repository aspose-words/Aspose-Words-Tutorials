---
"description": "学习如何使用 Aspose.Words for Java 将 Word 文档保存为 PDF。自定义字体、属性和图像质量。PDF 转换的全面指南。"
"linktitle": "将文档保存为 PDF"
"second_title": "Aspose.Words Java文档处理API"
"title": "在 Aspose.Words for Java 中将文档保存为 PDF"
"url": "/zh/java/document-loading-and-saving/saving-documents-as-pdf/"
"weight": 22
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中将文档保存为 PDF


## Aspose.Words for Java 文档保存为 PDF 简介

在本分步指南中，我们将探索如何使用 Aspose.Words for Java 将文档保存为 PDF。我们将涵盖 PDF 转换的各个方面，并提供代码示例以简化操作。

## 先决条件

在开始之前，请确保您已满足以下先决条件：

- 您的系统上安装了 Java 开发工具包 (JDK)。
- Aspose.Words for Java 库。您可以从 [这里](https://releases。aspose.com/words/java/).

## 将文档转换为 PDF

要将 Word 文档转换为 PDF，您可以使用以下代码片段：

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

代替 `"input.docx"` 您的 Word 文档的路径和 `"output.pdf"` 使用所需的输出 PDF 文件路径。

## 控制 PDF 保存选项

您可以使用以下方式控制各种 PDF 保存选项 `PdfSaveOptions` 类。例如，您可以按如下方式设置 PDF 文档的显示标题：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDisplayDocTitle(true);
doc.save("output.pdf", saveOptions);
```

## 在 PDF 中嵌入字体

要在生成的 PDF 中嵌入字体，请使用以下代码：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

## 自定义文档属性

您可以在生成的 PDF 中自定义文档属性。例如：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

## 导出文档结构

要导出文档结构，请设置 `exportDocumentStructure` 选择 `true`：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setExportDocumentStructure(true);
doc.save("output.pdf", saveOptions);
```

## 图像压缩

您可以使用以下代码控制图像压缩：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setImageCompression(PdfImageCompression.JPEG);
doc.save("output.pdf", saveOptions);
```

## 更新上次打印的属性

要更新 PDF 中的“上次打印”属性，请使用：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setUpdateLastPrintedProperty(true);
doc.save("output.pdf", saveOptions);
```

## 渲染 DML 3D 效果

对于 DML 3D 效果的高级渲染，请设置渲染模式：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDml3DEffectsRenderingMode(Dml3DEffectsRenderingMode.ADVANCED);
doc.save("output.pdf", saveOptions);
```

## 插值图像

您可以启用图像插值来提高图像质量：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setInterpolateImages(true);
doc.save("output.pdf", saveOptions);
```

## 结论

Aspose.Words for Java 提供全面的 Word 文档转换为 PDF 格式的功能，并具备灵活性和自定义选项。您可以控制 PDF 输出的各个方面，包括字体、文档属性、图像压缩等等。

## 常见问题解答

### 如何使用 Aspose.Words for Java 将 Word 文档转换为 PDF？

要将 Word 文档转换为 PDF，请使用以下代码：

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

代替 `"input.docx"` 您的 Word 文档的路径和 `"output.pdf"` 使用所需的输出 PDF 文件路径。

### 我可以在 Aspose.Words for Java 生成的 PDF 中嵌入字体吗？

是的，您可以通过设置 `setEmbedFullFonts` 选择 `true` 在 `PdfSaveOptions`。这里有一个例子：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

### 如何在生成的 PDF 中自定义文档属性？

您可以使用 `setCustomPropertiesExport` 选择 `PdfSaveOptions`。 例如：

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

### Aspose.Words for Java 中的图像压缩的目的是什么？

图像压缩允许您控制生成的 PDF 中图像的质量和大小。您可以使用以下方式设置图像压缩模式： `setImageCompression` 在 `PdfSaveOptions`。

### 如何更新 PDF 中的“上次打印”属性？

您可以通过设置来更新 PDF 中的“上次打印”属性 `setUpdateLastPrintedProperty` 到 `true` 在 `PdfSaveOptions`。这将反映 PDF 元数据中的最后打印日期。

### 如何在转换为 PDF 时提高图像质量？

为了提高图像质量，请通过设置启用图像插值 `setInterpolateImages` 到 `true` 在 `PdfSaveOptions`。这将使 PDF 中的图像更加流畅且质量更高。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}