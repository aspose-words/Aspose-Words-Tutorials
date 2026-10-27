---
category: general
date: 2026-10-26
description: 学习如何使用 C# 创建 Word 文档并以编程方式添加 ActiveX 按钮。本分步指南涵盖插入命令按钮、在设计时隐藏它以及保存文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: zh
lastmod: 2026-10-26
og_description: 使用 C# 创建 Word 文档并以编程方式添加 ActiveX 按钮。按照本完整教程嵌入仅在运行时出现的命令按钮。
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: 使用 ActiveX 命令按钮在 C# 中创建 Word 文档 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: 如何在 C# 中创建带 ActiveX 命令按钮的 Word 文档
url: /zh/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中使用 ActiveX 命令按钮创建 Word 文档

如果您需要 **create Word document C#**（创建包含交互按钮的 Word 文档），本指南将精确演示如何操作。阅读前两句话后，您将了解整体思路，随后步骤会逐行带您编写所需代码。

您将学习如何添加 ActiveX 按钮、在设计阶段隐藏它，并仅在用户打开文件时显示。教程还涵盖了常见的陷阱，如安全警告和版本兼容性，帮助您交付可靠的文档。

## 前置条件

在开始之前，请确保您具备：

* 已安装 .NET 6.0 或更高版本  
* 拥有 **Aspose.Words for .NET** 的授权副本（免费试用版可用于实验）  
* 对 C# 和 Visual Studio（任何支持 .NET 的 IDE）有基本了解  

除 `Aspose.Words` 之外，无需额外的 NuGet 包。

## 步骤 1：创建 Word 文档 C# 并初始化 DocumentBuilder

第一步是实例化一个 `Document` 对象和一个 `DocumentBuilder`。`Document` 代表整个 .docx 文件，而 `DocumentBuilder` 提供流式方法来添加内容。

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**为什么重要：** 没有 `DocumentBuilder`，您必须手动操作 OpenXML DOM，这既容易出错又难以阅读。Builder 抽象了这些细节，并保证生成的 Word 文件结构良好。

## 步骤 2：如何添加 ActiveX 按钮 – 插入 CommandButton 控件

现在我们在特定位置插入一个 **CommandButton ActiveX 控件**。矩形定义了按钮在点（X、Y）坐标以及宽度和高度。

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**为什么重要：** `InsertForms2OleControl` 是 Aspose.Words 唯一能够创建真正 ActiveX OLE 对象的方法。`Forms2OleControlType.CommandButton` 枚举值告诉 Word 嵌入一个可点击的按钮，而不是普通的 OLE 容器。

## 步骤 3：以编程方式添加命令按钮 – 在运行时之前隐藏

Word 默认将任何插入的形状设为可见。为了在设计模板时保持按钮不可见，需要对刚创建的形状设置 `Hidden` 属性。

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**为什么重要：** 将 `Hidden = true` 可以防止按钮在设计视图中占据空间。文档在 Word 中打开时，运行时环境会自动显示该控件，保持预期的用户体验。

## 步骤 4：保存文件 – 创建带命令按钮的 Word 文档

最后，将文档写入磁盘。选择应用程序有写入权限的路径，并使用 `.docx` 扩展名以确保现代兼容性。

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**为什么重要：** 使用 `.docx` 保存可确保嵌入的 ActiveX 控件符合 Office Open XML 标准，Word 2007 及以后版本均受支持。如果需要兼容旧版 `.doc`，请更改扩展名并使用 `SaveFormat.Doc`。

## 完整工作示例

将所有代码组合在一起，下面是可以直接复制、粘贴并运行的完整程序：

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**预期输出：** 运行程序后，在 Microsoft Word 中打开 `C:\Temp\ActiveX.docx`。您会看到一个空白文档；在设计模式下按钮不可见。按 **Alt + F9** 切换域代码，然后点击按钮区域——Word 将渲染 ActiveX 控件，您可以与之交互（例如双击查看属性）。

## 边缘情况和最佳实践提示

| 情况 | 需要注意的点 | 推荐的解决方案 |
|-----------|-------------------|-----------------|
| **用户禁用 ActiveX** | Word 可能显示安全警告或阻止控件。 | 指导最终用户在信任中心启用 “ActiveX 控件”，或提供已签名的宏替代方案。 |
| **文档在 Word Online 中打开** | Word Online 不支持 ActiveX，按钮会被省略。 | 如需云端兼容，可使用回退超链接或内容控件。 |
| **不同 DPI 设置** | 矩形尺寸在高 DPI 显示器上可能显得更大或更小。 | 使用 `GraphicsUnit.Point`（默认）并在常见 DPI（96 dpi、120 dpi）下进行测试。 |
| **多个按钮** | `GetChildNodes(NodeType.Shape, true)[0]` 只会检索到第一个形状。 | 遍历 `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)`，对每个新增的形状都设置 `Hidden`。 |
| **旧版 .doc 格式** | 保存为 `.doc` 时部分 ActiveX 属性会丢失。 | 除非有严格的旧版需求，否则建议使用 `.docx`。 |

**专业提示：** 插入按钮后，您可以通过 Word UI 将宏分配给其 `OnAction` 属性，从而在不编写额外 C# 代码的情况下定义自定义点击行为。

## 常见问题

* **这在 .NET Core 上能工作吗？**  
  可以。Aspose.Words for .NET 完全兼容 .NET 5、.NET 6 及更高版本。只需引用相同的 NuGet 包。

* **生成文档后我可以更改按钮的标题吗？**  
  `InsertForms2OleControl` 中设置的标题是设计时的默认文本。用户可以在 Word 中编辑它，您也可以通过 `Shape.OleFormat` API 访问 OLE 对象属性来编程修改标题。

* **如果需要不同尺寸的按钮怎么办？**  
  调整 `RectangleF` 的数值。前两个参数是 X、Y 坐标，后两个参数是宽度和高度，单位为点（1 pt = 1/72 英寸）。

## 结论

现在您已经掌握了如何 **create Word document C#** 并使用 Aspose.Words **以编程方式添加 command button**。本教程涵盖了文档初始化、插入 ActiveX 按钮、在运行时之前隐藏以及保存最终文件。凭借这些构建块，您可以在任何生成的 Word 模板中嵌入交互式控件。

接下来，您可以进一步了解 **how to add ActiveX button** 的事件处理、使用 VBA 为 **create command button word** 添加样式，以及 **programmatically add command button** 到已有文档的技巧。将此模式扩展到复选框、下拉框或自定义 OLE 对象的步骤相同——只需更改 `Forms2OleControlType` 枚举值。

开始实验吧：更改标题、调整位置，或将多个控件串联起来。练习得越多，您就越能熟练地从 C# 交付丰富、交互式的 Word 文档。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您在已有技巧的基础上进一步提升。每个资源都提供完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [如何在 Word 文档中以编程方式添加命令按钮](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [如何在 Word 文档中使用 Aspose.Words 添加 ActiveX 按钮](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [使用 ActiveX 按钮创建 Word 文档 – C# 指南](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}