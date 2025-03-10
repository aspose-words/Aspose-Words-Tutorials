---
title: 在气球中显示修订
linktitle: 在气球中显示修订
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 在气泡框中显示修订。本详细指南将引导您完成每个步骤，确保您的文档更改清晰且井然有序。
weight: 10
url: /zh/net/working-with-revisions/show-revisions-in-balloons/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在气球中显示修订

## 介绍

跟踪 Word 文档中的更改对于协作和编辑至关重要。Aspose.Words for .NET 提供强大的工具来管理这些修订，确保清晰度和易于审查。本指南将帮助您在气泡框中显示修订，让您更轻松地查看所做的更改以及更改者。

## 先决条件

在开始之前，请确保您已准备好以下内容：

-  Aspose.Words for .NET 库。您可以下载它[这里](https://releases.aspose.com/words/net/).
- 有效的 Aspose 许可证。如果没有，您可以获取[临时执照](https://purchase.aspose.com/temporary-license/).
- Visual Studio 或任何其他支持 .NET 开发的 IDE。
- 对 C# 和 .NET 框架有基本的了解。

## 导入命名空间

首先，让我们在 C# 项目中导入必要的命名空间。这些命名空间对于访问 Aspose.Words 功能至关重要。

```csharp
using Aspose.Words;
using Aspose.Words.Layout;
using Aspose.Words.RevisionOptions;
```

让我们将这个过程分解为简单且易于遵循的步骤。

## 步骤 1：加载文档

首先，我们需要加载包含修订内容的文档。请确保文档路径正确。

```csharp
//文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Revisions.docx");
```

## 步骤 2：配置修订选项

接下来，我们将配置修订选项，以内联显示插入修订，并在气球中删除和格式化修订。这样可以更轻松地区分不同类型的修订。

```csharp
//渲染以内联方式插入修订，在气球中删除和格式化修订。
doc.LayoutOptions.RevisionOptions.ShowInBalloons = ShowInBalloons.FormatAndDelete;
doc.LayoutOptions.RevisionOptions.MeasurementUnit = MeasurementUnits.Inches;
```

## 步骤 3：设置修订栏位置

为了使文档更具可读性，我们可以设置修订栏的位置。在此示例中，我们将其放置在页面的右侧。

```csharp
//在页面右侧呈现修订栏。
doc.LayoutOptions.RevisionOptions.RevisionBarsPosition = HorizontalAlignment.Right;
```

## 步骤 4：保存文档

最后，我们将文档保存为 PDF。这样我们就能以所需的格式查看修订内容。

```csharp
doc.Save(dataDir + "WorkingWithRevisions.ShowRevisionsInBalloons.pdf");
```

## 结论

就这样！按照这些简单的步骤，您可以使用 Aspose.Words for .NET 轻松地在气泡框中显示修订。这使得审阅和协作文档变得轻而易举，确保所有更改都清晰可见且井然有序。祝您编码愉快！

## 常见问题解答

### 我可以自定义修订栏的颜色吗？
是的，Aspose.Words 允许您自定义修订栏的颜色以满足您的喜好。

### 是否可以在气球中仅显示特定类型的修订？
当然可以。您可以配置 Aspose.Words 以在提示框中仅显示某些类型的修订，例如删除或格式更改。

### 如何获取 Aspose.Words 的临时许可证？
您可以获得临时驾照[这里](https://purchase.aspose.com/temporary-license/).

### 我可以将 Aspose.Words for .NET 与其他编程语言一起使用吗？
Aspose.Words 主要为 .NET 设计，但您可以将其与任何 .NET 支持的语言一起使用，包括 VB.NET 和 C++/CLI。

### Aspose.Words 除了 Word 之外还支持其他文档格式吗？
是的，Aspose.Words 支持各种文档格式，包括 PDF、HTML、EPUB 等。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
