---
"description": "通过我们详细的分步指南，了解如何在 Aspose.Words for .NET 中不使用 DocumentBuilder 插入 FieldIncludeText。"
"linktitle": "不使用文档生成器插入 FieldIncludeText"
"second_title": "Aspose.Words文档处理API"
"title": "插入字段包含文本（无需文档生成器）"
"url": "/zh/net/working-with-fields/insert-field-include-text-without-document-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 插入字段包含文本（无需文档生成器）

## 介绍

在文档自动化和操作领域，Aspose.Words for .NET 是一款强大的工具。今天，我们将深入讲解如何在不使用 DocumentBuilder 的情况下插入 FieldIncludeText 的详细指南。本教程将逐步指导您完成整个过程，确保您理解代码的每个部分及其用途。

## 先决条件

在深入研究代码之前，请确保您拥有所需的一切：

1. Aspose.Words for .NET：请确保您已安装最新版本。您可以从 [这里](https://releases。aspose.com/words/net/).
2. .NET 开发环境：任何与 .NET 兼容的 IDE，如 Visual Studio。
3. C# 基础知识：熟悉 C# 编程将帮助您跟上进度。

## 导入命名空间

首先，我们需要导入必要的命名空间。这些命名空间提供对操作 Word 文档所需的类和方法的访问。

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

现在，我们将示例分解为多个步骤。每个步骤都会进行详细解释，以确保清晰易懂。

## 步骤 1：设置目录路径

第一步是定义文档目录的路径。这是存储和访问Word文档的地方。

```csharp
// 文档目录的路径。
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## 步骤 2：创建文档和段落

接下来，我们创建一个新文档，并在其中创建一个段落。该段落将包含 FieldIncludeText 字段。

```csharp
// 创建文档和段落。
Document doc = new Document();
Paragraph para = new Paragraph(doc);
```

## 步骤3：插入FieldIncludeText字段

现在，我们将 FieldIncludeText 字段插入到段落中。此字段允许您包含来自其他文档的文本。

```csharp
// 插入 FieldIncludeText 字段。
FieldIncludeText fieldIncludeText = (FieldIncludeText)para.AppendField(FieldType.FieldIncludeText, false);
```

## 步骤 4：设置字段属性

我们需要指定 FieldIncludeText 字段的属性。这包括设置书签名称和源文档的完整路径。

```csharp
fieldIncludeText.BookmarkName = "bookmark";
fieldIncludeText.SourceFullName = dataDir + "IncludeText.docx";
```

## 步骤 5：将段落附加到文档

设置好字段后，我们将段落附加到文档的第一部分正文。

```csharp
doc.FirstSection.Body.AppendChild(para);
```

## 步骤 6：更新字段

在保存文档之前，我们需要更新 FieldIncludeText 以确保它从源文档中提取正确的内容。

```csharp
fieldIncludeText.Update();
```

## 步骤 7：保存文档

最后我们将文档保存到指定的目录。

```csharp
doc.Save(dataDir + "InsertionFieldFieldIncludeTextWithoutDocumentBuilder.docx");
```

## 结论

就这样！按照以下步骤，您无需使用 Aspose.Words for .NET 中的 DocumentBuilder，即可轻松插入 FieldIncludeText。这种方法提供了一种简化的方法，可以将一个文档的内容包含到另一个文档中，从而使您的文档自动化任务更加简单。

## 常见问题解答

### 什么是 Aspose.Words for .NET？  
Aspose.Words for .NET 是一个功能强大的库，用于在 .NET 应用程序中处理 Word 文档。它允许以编程方式创建、编辑和转换文档。

### 为什么要使用FieldIncludeText？  
FieldIncludeText 可用于将一个文档的内容动态地包含到另一个文档中，从而使文档更加模块化和易于维护。

### 我可以使用此方法来包含其他文件格式的文本吗？  
FieldIncludeText 专门用于 Word 文档。对于其他格式，您可能需要 Aspose.Words 提供的其他方法或类。

### Aspose.Words for .NET 是否与 .NET Core 兼容？  
是的，Aspose.Words for .NET 支持 .NET Framework、.NET Core 和 .NET 5/6。

### 如何免费试用 Aspose.Words for .NET？  
您可以从 [这里](https://releases。aspose.com/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}