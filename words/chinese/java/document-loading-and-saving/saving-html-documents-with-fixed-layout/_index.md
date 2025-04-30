---
"description": "了解如何在 Aspose.Words for Java 中保存固定布局的 HTML 文档。按照我们的分步指南，实现无缝文档格式化。"
"linktitle": "保存具有固定布局的 HTML 文档"
"second_title": "Aspose.Words Java文档处理API"
"title": "在 Aspose.Words for Java 中保存具有固定布局的 HTML 文档"
"url": "/zh/java/document-loading-and-saving/saving-html-documents-with-fixed-layout/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中保存具有固定布局的 HTML 文档


## Aspose.Words for Java 中固定布局 HTML 文档保存简介

在本指南中，我们将引导您使用 Aspose.Words for Java 保存固定布局的 HTML 文档。通过分步说明和代码示例，您将学习如何无缝地实现这一点。现在就开始吧！

## 先决条件

在开始之前，请确保您已满足以下先决条件：

- Java开发环境搭建。
- Aspose.Words for Java 库已安装并配置。

## 步骤 1：加载文档

首先，我们需要加载要保存为 HTML 格式的文档。操作方法如下：

```java
Document doc = new Document("Your Directory Path" + "YourDocument.docx");
```

代替 `"YourDocument.docx"` 以及您的 Word 文档的路径。

## 步骤 2：配置 HTML 固定保存选项

要以固定布局保存文档，我们需要配置 `HtmlFixedSaveOptions` 类。我们将设置 `useTargetMachineFonts` 财产 `true` 确保在 HTML 输出中使用目标机器的字体：

```java
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions();
saveOptions.setUseTargetMachineFonts(true);
```

## 步骤 3：将文档保存为 HTML

现在，让我们使用之前配置的选项将文档保存为具有固定布局的 HTML：

```java
doc.save("Your Directory Path" + "FixedLayoutDocument.html", saveOptions);
```

代替 `"FixedLayoutDocument.html"` 使用您所需的 HTML 文件名称。

## 在 Aspose.Words for Java 中保存固定布局 HTML 文档的完整源代码

```java
        Document doc = new Document("Your Directory Path" + "Bullet points with alternative font.docx");
        HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions();
        {
            saveOptions.setUseTargetMachineFonts(true);
        }
        doc.save("Your Directory Path" + "WorkingWithHtmlFixedSaveOptions.UseFontFromTargetMachine.html", saveOptions);
    }
```

## 结论

在本教程中，我们学习了如何使用 Aspose.Words for Java 保存具有固定布局的 HTML 文档。通过遵循这些简单的步骤，您可以确保文档在不同平台上保持一致的视觉结构。

## 常见问题解答

### 如何在我的项目中设置 Aspose.Words for Java？

Aspose.Words for Java 的设置非常简单。您可以从以下链接下载该库： [这里](https://releases.aspose.com/words/java/) 并按照文档中提供的安装说明进行操作 [这里](https://reference。aspose.com/words/java/).

### 使用 Aspose.Words for Java 有任何许可要求吗？

是的，Aspose.Words for Java 需要有效的许可证才能在生产环境中使用。您可以从 Aspose 网站获取许可证。更多详细信息请参阅文档。

### 我可以进一步自定义 HTML 输出吗？

当然！Aspose.Words for Java 提供了丰富的选项，可根据您的特定需求定制 HTML 输出。您可以浏览文档，了解有关定制选项的详细信息。

### Aspose.Words for Java 是否与不同 Java 版本兼容？

是的，Aspose.Words for Java 与各种 Java 版本兼容。请确保您使用的 Aspose.Words for Java 版本与您的 Java 开发环境兼容。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}