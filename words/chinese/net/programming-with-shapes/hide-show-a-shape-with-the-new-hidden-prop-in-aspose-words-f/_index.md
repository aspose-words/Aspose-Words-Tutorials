---
category: general
date: 2026-10-20
description: 使用 Aspose.Words for C# 的新 `Hidden` 属性隐藏/显示形状。了解如何切换形状可见性、处理边缘情况并保存结果。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Hide/Show a Shape with the new `Hidden` prop
- Aspose.Words hide shape
- C# shape hidden property
- Word document shape visibility
- programmatically hide shape
language: zh
lastmod: 2026-10-20
og_description: 使用 Aspose.Words for C# 的新 `Hidden` 属性隐藏/显示形状。掌握形状可见性切换，避免常见陷阱。
og_image_alt: Screenshot of a Word document where a shape is hidden using the Hidden
  property
og_title: 使用 Aspose.Words（C#）中的新 `Hidden` 属性隐藏/显示形状
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
    C#. Learn how to toggle shape visibility, handle edge cases, and save the result.
  headline: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 使用 Aspose.Words for C# 中的新 `Hidden` 属性隐藏/显示形状
url: /zh/net/programming-with-shapes/hide-show-a-shape-with-the-new-hidden-prop-in-aspose-words-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for C# 中的新 `Hidden` 属性隐藏/显示形状

如果您需要在 Word 文档中 **使用新 `Hidden` 属性隐藏/显示形状**，本指南将向您展示如何使用 Aspose.Words for .NET 完成此操作。无论是生成报告、构建模板，还是清理导入的文档，程序化控制形状可见性都能帮您省去手动编辑的麻烦。

在本教程中，您将学习如何加载文档、定位形状、切换 `Hidden` 属性并保存修改后的文件。步骤还涵盖了常见的变体，例如处理多个形状以及处理内联与浮动图形。

## 前置条件

在开始之前，请确保您具备以下条件：

* 已安装 .NET 6.0（或更高版本）——Aspose.Words 支持 .NET Standard 2.0 和 .NET Core。  
* 拥有 **Aspose.Words for .NET** 的授权副本（免费试用版可用于探索）。  
* 使用 Visual Studio 2022 或 Visual Studio Code 等 IDE。  
* 一个包含至少一个形状（例如图片、SmartArt 或绘图画布）的 Word 文档（`input.docx`）。

## 步骤 1：加载 Word 文档

首先创建一个表示磁盘上 .docx 文件的 `Document` 对象。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*此步骤的重要性*：`Document` 是所有 Aspose.Words 操作的入口。将文件加载到内存后，您即可完整访问其节点树，包括形状。

## 步骤 2：获取目标形状

要切换可见性，必须获取形状节点的引用。下面的示例获取文档中的第一个形状，您可以根据名称、类型或索引自行调整逻辑。

```csharp
// Get the first Shape node in the document tree
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

if (shape == null)
{
    throw new InvalidOperationException("No shape was found in the document.");
}
```

*此步骤的重要性*：`GetChild` 与 `true` 参数一起执行深度搜索，确保即使形状嵌套在表格或页眉中也能被找到。对 `null` 的检查可防止在文档不包含形状时抛出 `NullReferenceException`。

## 步骤 3：使用 `Hidden` 属性隐藏形状

Aspose.Words 引入了 `Hidden` 属性，用于控制形状是否渲染或打印。将其设为 `true` 可隐藏形状；设为 `false` 则再次显示形状。

```csharp
// Hide the shape so it will not appear in the rendered document
shape.Hidden = true;
```

如果需要 **显示** 先前隐藏的形状，只需将其设为 `false`：

```csharp
// Show the shape again
shape.Hidden = false;
```

*此步骤的重要性*：`Hidden` 属性适用于浮动和内联形状，并与 Word 本机的 “Hidden” 格式相集成。此方法比删除形状更可靠，因为节点仍保留在文档树中，保持布局和引用不变。

## 步骤 4：保存修改后的文档

调整可见性后，将更改写回新文件（或根据需要覆盖原文件）。

```csharp
// Save the document with the updated shape visibility
doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");
```

*此步骤的重要性*：`Save` 将内存中的节点树序列化为 Word 可打开的 .docx 包。隐藏标记会被持久化，使用 Microsoft Word 打开文件时会根据 `Hidden` 设置显示或隐藏形状。

## 完整、可运行的示例

将所有步骤组合在一起，即可得到一个可复制、编译并运行的独立程序。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShowShapeExample
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape in the document
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found. Exiting.");
            return;
        }

        // 3. Toggle the Hidden property
        // Hide the shape
        shape.Hidden = true;
        // To show the shape again, uncomment the following line:
        // shape.Hidden = false;

        // 4. Save the modified document
        doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");

        Console.WriteLine("Document saved. Shape hidden = " + shape.Hidden);
    }
}
```

运行程序时的 **预期输出**：

```
Document saved. Shape hidden = True
```

在 Microsoft Word 中打开 `ShapeHidden.docx` 时，文档将不显示目标形状。如果在保存前将 `shape.Hidden = false;`，形状将重新出现。

## 处理多个形状

上述示例适用于单个形状。实际文档往往包含大量图形。使用循环可以隐藏或显示满足条件的所有形状（例如特定名称或类型）。

```csharp
// Hide every picture shape in the document
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Image)
    {
        s.Hidden = true; // hide picture
    }
}
doc.Save("YOUR_DIRECTORY/AllPicturesHidden.docx");
```

*提示*：通过 `ShapeType` 进行过滤，可避免意外隐藏文本框或 SmartArt 等装饰元素。

## 边缘情况与最佳实践

| 情况 | 推荐处理方式 |
|-----------|----------------------|
| **形状位于页眉/页脚中** | 首先获取页眉/页脚节点，然后在该子文档上调用 `GetChild(NodeType.Shape, …)`。 |
| **文档不包含任何形状** | 在 `GetChild` 后始终检查 `null`，或使用 `doc.GetChildNodes(NodeType.Shape, true).Count` 进行验证。 |
| **需要在不同 Word 版本间保留隐藏标记** | `Hidden` 属性存储在形状的 XML 中为 `<w:hidden/>`，该标记在 Word 2007 及以后版本均受支持。 |
| **大文档的性能** | 只调用一次 `doc.GetChildNodes(NodeType.Shape, true)` 并复用返回的集合，而不是重复调用 `GetChild`。 |

## 专业技巧：将 `Hidden` 与 `WrapType` 结合使用

当形状被隐藏时，Word 仍会保留其占用的空间，除非您同时更改其环绕行为。将 `WrapType = WrapType.None` 可移除占位区域。

```csharp
shape.Hidden = true;
shape.WrapType = WrapType.None;
```

这样布局会像形状从未存在一样收缩，对于生成整洁报告非常有用。

## 结论

现在，您已经掌握了使用 Aspose.Words for C# **通过新 `Hidden` 属性隐藏/显示形状** 的方法。该解决方案涵盖了加载文档、定位形状、切换 `Hidden` 属性以及持久化更改。通过遵循最佳实践——检查 `null`、处理多个形状以及调整环绕设置——您可以在任何 Word 自动化场景中可靠地控制形状可见性。

准备好进一步探索了吗？可以考虑以下后续步骤：

* 基于自定义元数据 **隐藏/显示多个形状**（使用 “程序化隐藏形状” 技术）。  
* 将 `Hidden` 与 **条件内容** 结合，使用 Aspose.Words 字段实现动态报告生成。  
* **探索其他节点属性**，例如图表对象的 `Visible` 或段落级别的 `IsDeleted` 控制。

祝编码愉快，尽情享受 Aspose.Words 为 Word 文档形状可见性提供的细粒度控制吧！

## 接下来您应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方式，每篇资源均提供完整的可运行代码示例和逐步说明。

- [如何在 Word 中使用 C# 隐藏形状 – 步骤指南](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/)
- [How to Hide Shape in Word with C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/)
- [Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}