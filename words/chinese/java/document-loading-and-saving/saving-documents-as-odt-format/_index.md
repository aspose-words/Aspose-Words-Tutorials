---
"description": "了解如何使用 Aspose.Words for Java 将文档保存为 ODT 格式。确保与开源办公套件兼容。"
"linktitle": "将文档保存为 ODT 格式"
"second_title": "Aspose.Words Java文档处理API"
"title": "在 Aspose.Words for Java 中将文档保存为 ODT 格式"
"url": "/zh/java/document-loading-and-saving/saving-documents-as-odt-format/"
"weight": 19
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中将文档保存为 ODT 格式


## 在 Aspose.Words for Java 中将文档保存为 ODT 格式的简介

在本文中，我们将探讨如何使用 Aspose.Words for Java 将文档保存为 ODT（开放文档文本）格式。ODT 是一种流行的开放标准文档格式，被各种办公套件（包括 OpenOffice 和 LibreOffice）所采用。将文档保存为 ODT 格式，可以确保与这些软件包兼容。

## 先决条件

在开始之前，请确保您已满足以下先决条件：

1. Java 开发环境：确保您的系统上安装了 Java 开发工具包 (JDK)。

2. Aspose.Words for Java：下载并安装 Aspose.Words for Java 库。您可以找到下载链接 [这里](https://releases。aspose.com/words/java/).

3. 示例文档：有一个要转换为 ODT 格式的示例 Word 文档（例如“Document.docx”）。

## 步骤 1：加载文档

首先，让我们使用 Aspose.Words for Java 加载 Word 文档：

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
```

这里， `"Your Directory Path"` 应该指向您的文档所在的目录。

## 步骤 2：指定 ODT 保存选项

要将文档保存为 ODT 格式，我们需要指定 ODT 保存选项。此外，我们还可以设置文档的测量单位。Open Office 使用厘米，而 MS Office 使用英寸。我们将其设置为英寸：

```java
OdtSaveOptions saveOptions = new OdtSaveOptions();
saveOptions.setMeasureUnit(OdtSaveMeasureUnit.INCHES);
```

## 步骤3：保存文档

现在，是时候将文档保存为 ODT 格式了：

```java
doc.save("Your Directory Path" + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

这里， `"Your Directory Path"` 应该指向您想要保存转换后的 ODT 文件的目录。

## 在 Aspose.Words for Java 中将文档保存为 ODT 格式的完整源代码

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
// Open Office 在指定长度、宽度和其他可测量格式时使用厘米
// 和文档中的内容属性，而 MS Office 使用英寸。
OdtSaveOptions saveOptions = new OdtSaveOptions(); { saveOptions.setMeasureUnit(OdtSaveMeasureUnit.INCHES); }
doc.save("Your Directory Path" + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

## 结论

在本文中，我们学习了如何使用 Aspose.Words for Java 将文档保存为 ODT 格式。当您需要确保与 OpenOffice 和 LibreOffice 等开源办公套件兼容时，此功能尤其有用。

## 常见问题解答

### 如何下载适用于 Java 的 Aspose.Words？

您可以从 Aspose 网站下载 Aspose.Words for Java。访问 [此链接](https://releases.aspose.com/words/java/) 访问下载页面。

### 将文档保存为 ODT 格式有什么好处？

以 ODT 格式保存文档可确保与 OpenOffice 和 LibreOffice 等开源办公套件兼容，从而使这些软件包的用户更轻松地访问和编辑您的文档。

### 以 ODT 格式保存时是否需要指定测量单位？

是的，指定测量单位是个好习惯。Open Office 默认使用厘米，因此将其设置为英寸可以确保格式一致。

### 我可以批量将多个文档转换为 ODT 格式吗？

是的，您可以使用 Aspose.Words for Java 通过遍历文档文件并应用转换过程自动将多个文档转换为 ODT 格式。

### Aspose.Words for Java 是否与最新的 Java 版本兼容？

Aspose.Words for Java 会定期更新以支持最新的 Java 版本，从而确保兼容性和性能提升。请务必查看文档中的系统要求以获取最新信息。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}