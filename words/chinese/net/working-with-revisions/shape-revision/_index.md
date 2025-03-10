---
title: 形状修改
linktitle: 形状修改
second_title: Aspose.Words 文档处理 API
description: 通过本综合指南了解如何使用 Aspose.Words for .NET 处理 Word 文档中的形状修订。掌握跟踪更改、插入形状等。
weight: 10
url: /zh/net/working-with-revisions/shape-revision/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 形状修改

## 介绍

以编程方式编辑 Word 文档可能是一项艰巨的任务，尤其是在处理形状时。无论您是创建报告、设计模板还是简单地自动创建文档，跟踪和管理形状修订的能力都至关重要。Aspose.Words for .NET 提供了强大的 API，使此过程无缝且高效。在本教程中，我们将深入探讨修改 Word 文档中形状的具体细节，确保您拥有轻松管理文档的工具和知识。

## 先决条件

在深入研究代码之前，请确保您已准备好所需的一切：

-  Aspose.Words for .NET：确保已安装 Aspose.Words 库。您可以[点击下载](https://releases.aspose.com/words/net/).
- 开发环境：您应该设置一个开发环境，例如 Visual Studio。
- 对 C# 的基本理解：熟悉 C# 编程语言和面向对象编程的基本概念。
- Word 文档：要使用的 Word 文档，或者您可以在教程期间创建一个。

## 导入命名空间

首先，让我们导入必要的命名空间。这将为我们提供处理 Word 文档和形状所需的类和方法。

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
//文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 步骤 2：创建新文档

让我们创建一个新的 Word 文档，在其中插入和修改形状。

```csharp
Document doc = new Document();
```

## 步骤 3：插入内联形状

首先，我们将在不跟踪修订的情况下将内联形状插入到文档中。内联形状是与文本一起流动的形状。

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## 步骤 4：开始跟踪修订

要跟踪文档中的更改，我们需要启用修订跟踪。这对于识别对形状所做的修改至关重要。

```csharp
doc.StartTrackRevisions("John Doe");
```

## 步骤 5：插入另一个带修订的形状

现在已启用修订跟踪，让我们插入另一个形状。这次，任何更改都将被跟踪。

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## 步骤 6：检索和修改形状

我们可以检索文档中的所有形状并根据需要进行修改。在这里，我们将获取形状并删除第一个形状。

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## 步骤 7：保存文档

完成更改后，我们需要保存文档。这可确保所有修订和修改都已保存。

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## 步骤 8：处理形状移动修订

当形状移动时，Aspose.Words 会将其作为修订进行跟踪。这意味着该形状将有两个实例：一个位于其原始位置，一个位于其新位置。

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## 结论

就这样！您已经成功学会了如何使用 Aspose.Words for .NET 处理 Word 文档中的形状修订。无论您是管理文档模板、自动生成报告还是只是跟踪更改，这些技能都是无价的。通过遵循本分步指南，您不仅掌握了基础知识，还深入了解了更高级的文档处理技术。

## 常见问题解答

### 什么是 Aspose.Words for .NET？
Aspose.Words for .NET 是一个功能强大的库，允许开发人员使用 C# 以编程方式创建、修改和转换 Word 文档。

### 我可以跟踪对 Word 文档中其他元素所做的更改吗？
是的，Aspose.Words for .NET 支持跟踪各种元素的变化，包括文本、表格等。

### 如何免费试用 Aspose.Words for .NET？
您可以免费试用 Aspose.Words for .NET[这里](https://releases.aspose.com/).

### 是否可以通过编程来接受或拒绝修订？
是的，Aspose.Words for .NET 提供了以编程方式接受或拒绝修订的方法。

### 除了 C# 之外，我可以将 Aspose.Words for .NET 与其他 .NET 语言一起使用吗？
当然！Aspose.Words for .NET 可以与任何 .NET 语言一起使用，包括 VB.NET 和 F#。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
