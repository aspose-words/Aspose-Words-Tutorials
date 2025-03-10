---
title: Word 文档中的首选控件类型
linktitle: Word 文档中的首选控件类型
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 在 Word 文档中插入组合框表单字段。按照此分步指南进行无缝 HTML 内容集成。
weight: 10
url: /zh/net/programming-with-htmlloadoptions/preferred-control-type/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 文档中的首选控件类型

## 介绍

我们正在深入研究有关如何使用 Aspose.Words for .NET 中的 HTML 加载选项的精彩教程，特别是重点介绍在将组合框表单字段插入 Word 文档时设置首选控件类型。本分步指南将帮助您了解如何使用 Aspose.Words for .NET 有效地操作和呈现 Word 文档中的 HTML 内容。

## 先决条件

在我们进入代码之前，你需要做好以下几件事：

1.  Aspose.Words for .NET：确保已安装 Aspose.Words for .NET 库。您可以从[网站](https://releases.aspose.com/words/net/).
2. 开发环境：您应该设置一个开发环境，例如 Visual Studio。
3. C# 基础知识：要学习本教程，需要对 C# 编程有基本的了解。
4. HTML 内容：HTML 的基本知识很有帮助，因为我们将在此示例中处理 HTML 内容。

## 导入命名空间

首先，让我们导入必要的命名空间以开始：

```csharp
using System;
using System.IO;
using System.Text;
using Aspose.Words;
using Aspose.Words.Loading;
```

现在，让我们将示例分解为多个步骤，以确保清晰易懂。

## 步骤 1：设置 HTML 内容

首先，我们需要定义要插入 Word 文档的 HTML 内容。以下是我们将使用的 HTML 代码片段：

```csharp
const string html = @"
    <html>
        <select name='ComboBox' size='1'>
            <option value='val1'>item1</option>
            <option value='val2'></option>                        
        </select>
    </html>
";
```

此 HTML 包含一个带有两个选项的简单组合框。我们将此 HTML 加载到 Word 文档中并指定其呈现方式。

## 第 2 步：定义文档目录

接下来，指定 Word 文档的保存目录。这有助于组织文件并保持路径管理清晰。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替`"YOUR DOCUMENT DIRECTORY"`与您想要保存 Word 文档的实际路径。

## 步骤 3：配置 HTML 加载选项

在这里，我们配置 HTML 加载选项，特别关注`PreferredControlType`属性。这决定了组合框在 Word 文档中的呈现方式。

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { PreferredControlType = HtmlControlType.StructuredDocumentTag };
```

通过设置`PreferredControlType`到`HtmlControlType.StructuredDocumentTag`，我们确保组合框在 Word 文档中呈现为结构化文档标签 (SDT)。

## 步骤 4：将 HTML 内容加载到文档中

使用配置的加载选项，我们将 HTML 内容加载到新的 Word 文档中。

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

在这里，我们将 HTML 字符串转换为字节数组，并使用内存流将其加载到文档中。这确保了 Aspose.Words 能够正确解释和呈现 HTML 内容。

## 步骤 5：保存文档

最后将文档以DOCX格式保存到指定目录。

```csharp
doc.Save(dataDir + "WorkingWithHtmlLoadOptions.PreferredControlType.docx", SaveFormat.Docx);
```

这会将呈现的组合框控件连同 Word 文档一起保存在指定位置。

## 结论

就这样！我们已成功使用 Aspose.Words for .NET 通过利用 HTML 加载选项将组合框表单字段插入 Word 文档。本分步指南应可帮助您了解该过程并将其应用于您的项目。无论您是自动创建文档还是处理 HTML 内容，Aspose.Words for .NET 都提供了强大的工具来实现您的目标。

## 常见问题解答

### 什么是 Aspose.Words for .NET？
Aspose.Words for .NET 是一个强大的文档操作库，允许开发人员以编程方式创建、编辑、转换和呈现 Word 文档。

### 我可以将其他 HTML 控件类型与 Aspose.Words for .NET 一起使用吗？
是的，Aspose.Words for .NET 支持各种 HTML 控件类型。您可以自定义不同控件在 Word 文档中的呈现方式。

### 如何在 Aspose.Words for .NET 中处理复杂的 HTML 内容？
 Aspose.Words for .NET 为 HTML 提供全面支持，包括复杂元素。请确保配置`HtmlLoadOptions`以适当地处理您的特定 HTML 内容。

### 在哪里可以找到更多示例和文档？
您可以在[Aspose.Words for .NET 文档页面](https://reference.aspose.com/words/net/).

### Aspose.Words for .NET 有免费试用版吗？
是的，你可以从[Aspose 网站](https://releases.aspose.com/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
