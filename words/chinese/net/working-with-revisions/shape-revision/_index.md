---
"description": "通过这份全面的指南，学习如何使用 Aspose.Words for .NET 处理 Word 文档中的形状修订。掌握跟踪更改、插入形状等操作。"
"linktitle": "形状修改"
"second_title": "Aspose.Words文档处理API"
"title": "形状修改"
"url": "/zh/net/working-with-revisions/shape-revision/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 形状修改

## 介绍

以编程方式编辑 Word 文档可能是一项艰巨的任务，尤其是在处理形状方面。无论您是创建报告、设计模板，还是仅仅自动化文档创建，跟踪和管理形状修订的能力都至关重要。Aspose.Words for .NET 提供了强大的 API，使这一过程无缝且高效。在本教程中，我们将深入探讨在 Word 文档中修改形状的具体细节，确保您拥有轻松管理文档的工具和知识。

## 先决条件

在深入研究代码之前，请确保您拥有所需的一切：

- Aspose.Words for .NET：请确保您已安装 Aspose.Words 库。您可以 [点击此处下载](https://releases。aspose.com/words/net/).
- 开发环境：您应该设置一个开发环境，例如 Visual Studio。
- C# 基本理解：熟悉 C# 编程语言和面向对象编程的基本概念。
- Word 文档：要使用的 Word 文档，或者您可以在教程期间创建一个。

## 导入命名空间

首先，我们导入必要的命名空间。这些命名空间将使我们能够访问处理 Word 文档和形状所需的类和方法。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## 步骤 1：设置文档目录

在开始处理形状之前，我们需要定义文档目录的路径。我们将在这里保存修改后的文档。

```csharp
// 文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 步骤2：创建新文档

让我们创建一个新的 Word 文档，在其中插入和修改形状。

```csharp
Document doc = new Document();
```

## 步骤 3：插入内联形状

首先，我们将在文档中插入一个不跟踪修订的内联形状。内联形状是指与文本一起流动的形状。

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## 步骤 4：开始跟踪修订

为了追踪文档中的更改，我们需要启用修订跟踪。这对于识别形状的修改至关重要。

```csharp
doc.StartTrackRevisions("John Doe");
```

## 步骤5：插入另一个带有修订的形状

现在已启用修订跟踪，让我们插入另一个形状。这次，所有更改都将被跟踪。

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## 步骤 6：检索和修改形状

我们可以检索文档中的所有形状，并根据需要进行修改。在这里，我们将获取所有形状并删除第一个形状。

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## 步骤7：保存文档

完成更改后，我们需要保存文档。这确保所有修订和修改都已保存。

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## 步骤8：处理形状移动修订

当形状移动时，Aspose.Words 会将其作为修订进行跟踪。这意味着该形状将有两个实例：一个在原始位置，一个在新位置。

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## 结论

就这样！您已经成功学会了如何使用 Aspose.Words for .NET 处理 Word 文档中的形状修订。无论您是管理文档模板、自动化报告，还是仅仅跟踪更改，这些技能都弥足珍贵。通过遵循本分步指南，您不仅掌握了基础知识，还深入了解了更高级的文档处理技巧。

## 常见问题解答

### 什么是 Aspose.Words for .NET？
Aspose.Words for .NET 是一个功能强大的库，允许开发人员使用 C# 以编程方式创建、修改和转换 Word 文档。

### 我可以跟踪对 Word 文档中其他元素所做的更改吗？
是的，Aspose.Words for .NET 支持跟踪各种元素的变化，包括文本、表格等。

### 如何免费试用 Aspose.Words for .NET？
您可以免费试用 Aspose.Words for .NET [这里](https://releases。aspose.com/).

### 是否可以通过编程接受或拒绝修订？
是的，Aspose.Words for .NET 提供了以编程方式接受或拒绝修订的方法。

### 除了 C# 之外，我可以将 Aspose.Words for .NET 与其他 .NET 语言一起使用吗？
当然！Aspose.Words for .NET 可以与任何 .NET 语言一起使用，包括 VB.NET 和 F#。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}