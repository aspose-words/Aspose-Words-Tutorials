---
"description": "了解如何使用 Aspose.Words for .NET 修改 Word 中的结构化文档标签。逐步更新文本、下拉菜单和图像。"
"linktitle": "修改内容控件"
"second_title": "Aspose.Words文档处理API"
"title": "修改内容控件"
"url": "/zh/net/programming-with-sdt/modify-content-controls/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 修改内容控件

## 介绍

如果您曾经使用过 Word 文档，并且需要使用 Aspose.Words for .NET 修改结构化内容控件（例如纯文本、下拉列表或图片），那么您来对地方了！结构化文档标签 (SDT) 是功能强大的工具，可使文档自动化更轻松、更灵活。在本教程中，我们将深入探讨如何修改这些 SDT 以满足您的需求。无论您是更新文本、更改下拉列表选项还是替换图片，本指南都将逐步指导您完成整个过程。

## 先决条件

在我们深入讨论修改内容控件的细节之前，请确保您具备以下条件：

1. 已安装 Aspose.Words for .NET：确保您已安装 Aspose.Words 库。如果没有，您可以 [点击此处下载](https://releases。aspose.com/words/net/).

2. C# 基础知识：本教程假设您熟悉基本的 C# 编程概念。

3. .NET 开发环境：您应该有一个像 Visual Studio 这样的 IDE 来运行 .NET 应用程序。

4. 示例文档：我们将使用包含各种 SDT 类型的 Word 示例文档。您可以使用示例中的文档，也可以创建自己的文档。

5. 访问 Aspose 文档：有关更多详细信息，请查看 [Aspose.Words 文档](https://reference。aspose.com/words/net/).

## 导入命名空间

要开始使用 Aspose.Words，您需要将相关的命名空间导入到您的 C# 项目中。操作方法如下：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

这些命名空间将使您能够访问操作 Word 文档中的结构化文档标签所需的类和方法。

## 步骤 1：设置文档路径

在进行任何更改之前，您需要指定文档的路径。替换 `"YOUR DOCUMENT DIRECTORY"` 使用您的文档存储的实际路径。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## 步骤 2：循环遍历结构化文档标签

要修改 SDT，首先需要循环遍历文档中的所有 SDT。这可以通过使用 `GetChildNodes` 获取所有类型的节点的方法 `StructuredDocumentTag`。

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // 根据类型修改 SDT
}
```

## 步骤3：修改纯文本SDT

如果 SDT 是纯文本类型，则可以替换其内容。首先清除现有内容，然后添加新文本。

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

解释：这里， `RemoveAllChildren()` 清除 SDT 的现有内容。然后我们创建一个新的 `Paragraph` 和 `Run` 对象来插入新文本。

## 步骤 4：修改下拉列表 SDT

对于下拉列表 SDT，您可以通过访问 `ListItems` 集合。在这里，我们选择列表中的第三项。

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

说明：此代码片段从下拉列表中选择索引 2 处的项目（第三项）。请根据您的需求调整索引。

## 步骤5：修改图片SDT

要更新图片 SDT 中的图像，您可以用新图像替换现有图像。

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

说明：此代码检查形状是否包含图像，然后用位于的新图像替换它 `ImagesDir`。

## 步骤6：保存修改后的文档

完成所有必要的更改后，请使用新名称保存修改后的文档，以保持原始文档的完整性。

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

说明：这将使用新文件名保存文档，以便您可以轻松地将其与原始文档区分开来。

## 结论

了解相关步骤后，使用 Aspose.Words for .NET 修改 Word 文档中的内容控件非常简单。无论您是更新文本、更改下拉菜单选项还是交换图像，Aspose.Words 都提供了强大的 API 来完成这些任务。通过学习本教程，您可以有效地管理和自定义文档的结构化内容控件，从而使您的文档更具动态性，并更符合您的需求。

## 常见问题解答

1. 什么是结构化文档标签 (SDT)？

SDT 是 Word 文档中的元素，有助于管理和格式化文档内容，如文本框、下拉列表或图片。

2. 如何向 SDT 添加新的下拉项？

要添加新项目，请使用 `ListItems` 属性并附加新的 `SdtListItem` 到收藏夹。

3. 我可以使用 Aspose.Words 从文档中删除 SDT 吗？

是的，您可以通过访问文档的节点并删除所需的 SDT 来删除 SDT。

4. 如何处理嵌套在其他元素中的 SDT？

使用 `GetChildNodes` 具有适当参数的方法来访问嵌套的 SDT。

5. 如果我需要修改的SDT在文档中不可见，我该怎么办？

确保 SDT 未被隐藏或受保护。请检查文档设置，并确保您的代码正确定位了 SDT 类型。


### 使用 Aspose.Words for .NET 修改内容控件的示例源代码 

```csharp
// 文档目录的路径 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

就是这样！您已成功使用 Aspose.Words for .NET 修改了 Word 文档中不同类型的内容控件。

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}