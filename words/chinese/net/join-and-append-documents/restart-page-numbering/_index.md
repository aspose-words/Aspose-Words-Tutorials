---
"description": "了解如何使用 Aspose.Words for .NET 在合并和附加 Word 文档时重新开始页码编号。"
"linktitle": "重新开始页码"
"second_title": "Aspose.Words文档处理API"
"title": "重新开始页码"
"url": "/zh/net/join-and-append-documents/restart-page-numbering/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 重新开始页码

## 介绍

您是否曾为创建一份内容清晰、章节分明、且每页都从1页开始的文档而苦恼？想象一下，一份报告的各个章节都是从头开始的，或者一份冗长的提案，其中包含执行摘要和详细附录的独立章节。Aspose.Words for .NET 是一款功能强大的文档处理库，可以帮助您轻松实现这些目标。本指南将揭开重新开始页码编号的秘密，让您轻松制作出专业水准的文档。

## 先决条件

在踏上这段旅程之前，请确保您已准备好以下物品：

1. Aspose.Words for .NET：从官方网站下载该库 [下载链接](https://releases.aspose.com/words/net/)。您可以探索免费试用 [免费试用链接](https://releases.aspose.com/) 或购买许可证 [购买链接](https://purchase.aspose.com/buy) 根据您的需要。
2. C# 开发环境：Visual Studio 或任何支持 .NET 开发的环境都可以完美运行。
3. 示例文档：找到您想要试验的 Word 文档。

## 导入基本命名空间

为了与 Aspose.Words 对象和功能进行交互，我们需要导入必要的命名空间。操作方法如下：

```csharp
using Aspose.Words;
using Aspose.Words.Settings;
```

此代码片段导入 `Aspose.Words` 命名空间，用于访问核心文档操作类。此外，我们导入 `Aspose.Words.Settings` 命名空间，提供自定义文档行为的选项。


现在，让我们深入了解在文档中重新开始页码的实际步骤：

## 步骤 1：加载源文档和目标文档：

定义字符串变量 `dataDir` 用于存储文档目录的路径。请将“您的文档目录”替换为实际位置。

创建两个 `Document` 使用的对象 `Aspose.Words.Document` 构造函数。第一个（`srcDoc`) 将保存包含要附加内容的源文档。第二个 (`dstDoc`表示我们将在其中集成源内容并重新开始页码的目标文档。

```csharp
string dataDir = @"C:\MyDocuments\"; // 替换为您的实际目录
Document srcDoc = new Document(dataDir + "source.docx");
Document dstDoc = new Document(dataDir + "destination.docx");
```

## 第 2 步：设置分节符：

访问 `FirstSection` 源文档的属性（`srcDoc`）来操作初始部分。此部分的页码将重新开始。

利用 `PageSetup` 该部分的属性来配置其布局行为。

设置 `SectionStart` 的财产 `PageSetup` 到 `SectionStart.NewPage`。这可确保在将源内容附加到目标文档之前创建一个新页面。

```csharp
srcDoc.FirstSection.PageSetup.SectionStart = SectionStart.NewPage;
```

## 步骤 3：启用重新开始页码：

在同一 `PageSetup` 源文档第一节的对象，设置 `RestartPageNumbering` 财产 `true`。这个关键的步骤指示 Aspose.Words 为附加的内容重新启动页码编排。

```csharp
srcDoc.FirstSection.PageSetup.RestartPageNumbering = true;
```

## 步骤4：附加源文档：

现在源文档已准备好所需的分页符和编号配置，是时候将其集成到目标文档中了。

雇用 `AppendDocument` 目标文档的方法（`dstDoc`) 无缝添加源内容。

通过源文档（`srcDoc`）和一个 `ImportFormatMode.KeepSourceFormatting` 此方法的参数。此参数在附加时保留源文档的原始格式。

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## 步骤5：保存最终文档：

最后，利用 `Save` 目标文档的方法（`dstDoc`) 以重新开始页码的方式存储合并后的文档。为保存的文档指定合适的文件名和位置。

```csharp
dstDoc.Save(dataDir + "final_document.docx");
```

## 结论

总而言之，掌握 Aspose.Words for .NET 中的分页符和页码功能，可以帮助您创建精美且结构良好的文档。通过实施本指南中概述的技术，您可以将内容与重新开始的页码无缝集成，从而确保呈现专业且易于阅读的演示文稿。请记住，Aspose.Words 提供了丰富的附加文档操作功能。

## 常见问题解答

### 我可以在某一节的中间重新开始页码吗？

遗憾的是，Aspose.Words for .NET 不支持在单个部分内重新开始页码编号。不过，您可以通过在所需位置创建新部分并设置来实现类似的效果。 `RestartPageNumbering` 到 `true` 该部分。

### 如何在重启后自定义起始页码？

虽然提供的代码从 1 开始编号，但您可以自定义它。利用 `PageNumber` 的财产 `HeaderFooter` 新节中的对象。设置此属性可让您定义起始页码。

### 源文档中现有的页码会发生什么情况？

源文档中现有的页码不受影响。只有目标文档中附加的内容才会重新开始编号。

### 我可以应用不同的数字格式（例如罗马数字）吗？

当然！Aspose.Words 提供对页码格式的全面控制。探索 `NumberStyle` 的财产 `HeaderFooter` 对象可从各种编号样式中进行选择，如罗马数字、字母或自定义格式。

### 我可以在哪里找到更多资源或帮助？

Aspose 提供了全面的文档门户 [文档链接](https://reference.aspose.com/words/net/) 深入探讨页码功能和其他 Aspose.Words 功能。此外，他们活跃的论坛 [支持链接](https://forum.aspose.com/c/words/8) 是一个与开发者社区联系并寻求特定挑战帮助的绝佳平台。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}