---
"description": "通过这份全面的指南，学习如何使用 Aspose.Words for .NET 设置单元格布局。非常适合希望自定义 Word 文档的开发人员。"
"linktitle": "单元格布局"
"second_title": "Aspose.Words文档处理API"
"title": "单元格布局"
"url": "/zh/net/programming-with-shapes/layout-in-cell/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 单元格布局

## 介绍

如果您曾经想通过编程方式微调 Word 文档中表格单元格的布局，那么您来对地方了。今天，我们将深入探讨如何使用 Aspose.Words for .NET 设置单元格布局。我们将通过一个实际示例，逐步讲解，以便您轻松上手。

## 先决条件

在我们进入代码之前，让我们确保您拥有所需的一切：

1. Aspose.Words for .NET：请确保您已安装 Aspose.Words for .NET 库。如果没有，您可以 [点击此处下载](https://releases。aspose.com/words/net/).
2. 开发环境：您需要一个使用 .NET 搭建的开发环境。如果您需要推荐，Visual Studio 是一个不错的选择。
3. C# 基础知识：虽然我会解释每个步骤，但对 C# 的基本了解将帮助您更轻松地跟进。
4. 文档目录：准备一个用于保存文档的目录路径。我们将其称为 `YOUR DOCUMENT DIRECTORY`。

## 导入命名空间

首先，请确保在项目中导入必要的命名空间：

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

让我们将这个过程分解为易于管理的步骤。

## 步骤 1：创建新文档

首先，我们将创建一个新的 Word 文档并初始化 `DocumentBuilder` 对象来帮助我们构建内容。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 步骤 2：创建表格并设置行格式

我们将开始构建一个表格并指定行的高度和高度规则。

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## 步骤 3：插入单元格并填充内容

接下来，我们循环将单元格插入表格。每插入 7 个单元格，我们就结束该行并创建一个新行。

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## 步骤 4：添加水印形状

现在，让我们在文档中添加水印。我们将创建一个 `Shape` 对象并设置其属性。

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // 如果要将形状放入单元格中，则在表格单元格外面显示该形状。
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## 步骤5：自定义水印外观

我们将通过设置水印的颜色和文本属性来进一步定制水印的外观。

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## 步骤 6：将水印插入文档

我们将找到文档中的最后一次运行并在该位置插入水印。

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## 步骤 7：针对 Word 2010 优化文档

为了确保兼容性，我们将针对 Word 2010 优化文档。

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## 步骤8：保存文档

最后，我们将文档保存到指定的目录。

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## 结论

就这样！您已经成功使用 Aspose.Words for .NET 创建了一个具有自定义表格布局的 Word 文档，并添加了水印。本教程旨在提供清晰的分步指南，帮助您理解整个过程的每个部分。掌握这些技能后，您现在可以通过编程方式创建更复杂、更个性化的 Word 文档。

## 常见问题解答

### 我可以对水印文本使用不同的字体吗？
是的，您可以通过设置 `watermark.TextPath.FontFamily` 属性为您想要的字体。

### 如何调整水印的位置？
您可以修改 `RelativeHorizontalPosition`， `RelativeVerticalPosition`， `HorizontalAlignment`， 和 `VerticalAlignment` 属性来调整水印的位置。

### 可以使用图像代替文本作为水印吗？
当然！你可以创建一个 `Shape` 与类型 `ShapeType.Image` 并使用 `ImageData.SetImage` 方法。

### 我可以创建具有不同行高的表格吗？
是的，您可以通过更改 `RowFormat.Height` 属性，然后再将单元格插入到该行。

### 如何从文档中去除水印？
您可以通过在文档的形状集合中找到水印并调用 `Remove` 方法。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}