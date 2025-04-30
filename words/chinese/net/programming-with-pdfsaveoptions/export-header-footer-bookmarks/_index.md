---
"description": "通过我们的分步指南了解如何使用 Aspose.Words for .NET 将 Word 文档的页眉和页脚书签导出为 PDF。"
"linktitle": "将 Word 文档页眉页脚书签导出为 PDF 文档"
"second_title": "Aspose.Words文档处理API"
"title": "将 Word 文档页眉页脚书签导出为 PDF 文档"
"url": "/zh/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 将 Word 文档页眉页脚书签导出为 PDF 文档

## 介绍

将 Word 文档转换为 PDF 是一项常见的任务，尤其是在您想要共享或存档文档并保留其格式时。有时，这些文档的页眉和页脚中包含重要的书签。在本教程中，我们将逐步介绍如何使用 Aspose.Words for .NET 将这些书签从 Word 文档导出为 PDF。

## 先决条件

在深入研究之前，请确保您具备以下条件：

- Aspose.Words for .NET：您需要安装 Aspose.Words for .NET。您可以从以下网址下载 [这里](https://releases。aspose.com/words/net/).
- 开发环境：设置您的开发环境。您可以使用 Visual Studio 或任何其他兼容 .NET 的 IDE。
- C# 基础知识：需要熟悉 C# 编程才能遵循代码示例。

## 导入命名空间

首先，你需要在 C# 项目中导入必要的命名空间。在代码文件的顶部添加以下几行：

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

让我们将这个过程分解为易于遵循的步骤。

## 步骤 1：初始化文档

第一步是加载Word文档。操作方法如下：

```csharp
// 文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

在此步骤中，您只需指定文档目录的路径并加载 Word 文档。

## 步骤 2：配置 PDF 保存选项

接下来，您需要配置 PDF 保存选项，以确保页眉和页脚中的书签正确导出。

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

在这里，我们正在设置 `PdfSaveOptions`。 这 `DefaultBookmarksOutlineLevel` 属性设置书签的大纲级别，以及 `HeaderFooterBookmarksExportMode` 属性确保仅导出页眉和页脚中第一次出现的书签。

## 步骤 3：将文档保存为 PDF

最后，使用配置的选项将您的文档保存为 PDF。

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

在此步骤中，您将使用已配置的选项将文档保存到指定路径。

## 结论

就这样！按照以下步骤，您可以使用 Aspose.Words for .NET 轻松地将 Word 文档页眉和页脚中的书签导出到 PDF。此方法可确保文档中重要的导航辅助信息以 PDF 格式保存，方便读者轻松浏览文档。

## 常见问题解答

### 我可以将 Word 文档中的所有书签导出为 PDF 吗？

是的，你可以。在 `PdfSaveOptions`，您可以根据需要调整设置以包含所有书签。

### 如果我也想从文档正文中导出书签怎么办？

您可以配置 `Outl在eOptions` in `PdfSaveOptions` 包括文档正文中的书签。

### 是否可以自定义 PDF 中的书签级别？

当然！您可以自定义 `DefaultBookmarksOutlineLevel` 属性为您的书签设置不同的大纲级别。

### 如何处理没有书签的文档？

如果您的文档没有书签，则生成的 PDF 将不包含任何书签轮廓。如果您需要在 PDF 中添加书签，请确保您的文档包含书签。

### 我可以将此方法用于其他文档类型（例如 DOCX 或 RTF）吗？

是的，Aspose.Words for .NET 支持各种文档类型，包括 DOCX、RTF 等。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}