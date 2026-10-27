---
category: general
date: 2026-09-21
description: 使用 DocumentBuilder 编程创建 Word 文档，并学习如何保存 Word 文档按钮、插入命令按钮文字以及设置命令按钮标题。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: zh
lastmod: 2026-09-21
og_description: 使用 Aspose.Words 编程创建 Word 文档。了解如何保存 Word 文档按钮、插入命令按钮、设置命令按钮标题，以及使用
  DocumentBuilder 实现交互式表单。
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: 以编程方式创建Word文档并添加按钮
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: 以编程方式创建Word文档并插入按钮
url: /zh/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 编程创建 Word 文档并插入按钮

如果您需要**编程创建 Word 文档**，Aspose.Words 提供了流畅的 API，允许您添加诸如 CommandButton 的交互式控件。本教程还说明了**如何使用 DocumentBuilder**、**如何保存 Word 文档按钮**以及**如何设置命令按钮标题**，以便按钮在 .docx 文件中呈现出您期望的效果。

您将学习如何：

* 使用 `Document` 初始化空白文档。
* 使用 `DocumentBuilder` 编辑文档。
* 插入 **CommandButton**（`insert command button word`）。
* 设置按钮的名称和可见标题（`set command button caption`）。
* 将结果持久化到磁盘（`save word document button`）。

这些步骤面向使用 C# 的 .NET 开发者，基于最新的 Aspose.Words for .NET（v24.10）。除 Aspose.Words 外，无需其他 NuGet 包。

---

## 开始之前的准备

| 前置条件 | 原因 |
|--------------|--------|
| Visual Studio 2022（或任何 C# IDE） | 用于编译和运行示例代码。 |
| .NET 6.0 SDK 或更高版本 | 为示例提供运行时环境。 |
| Aspose.Words for .NET（v24.10 或更新版本） | 该库可让您**编程创建 Word 文档**并操作表单控件。 |
| 对 C# 和面向对象编程概念的基本了解 | 理解代码流程所必需。 |

您可以通过 NuGet 安装 Aspose.Words：

```bash
dotnet add package Aspose.Words
```

---

## 编程创建 Word 文档

第一步是实例化一个空的 `Document`。该对象在内存中表示整个 Word 文件。

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

以编程方式创建文档可为您提供一个干净的画布，您可以在其上添加段落、表格或交互式控件。  

---

## 如何使用 DocumentBuilder

`DocumentBuilder` 是编辑 `Document` 的主要类。它提供插入文本、图像和表单字段的方法。在本教程中，我们使用它来放置 CommandButton。

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

构建器维护一个内部光标，指向当前的插入位置。默认情况下，它位于第一个节的开头，这对于我们的示例非常合适。

---

## 插入 command button word

Aspose.Words 将 CommandButton 视为 ActiveX 控件。`InsertForms2OleControl` 方法创建一个通用的 OLE 控件，随后我们将其配置为按钮。

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

此时控件已存在于文档中，但在我们定义其类型之前，它没有可视化表现。

---

## 设置 command button caption

现在我们告诉 OLE 控件它应表现为 CommandButton，并为其设置一个友好的标签。

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

设置**命令按钮标题**至关重要，因为 Word 会在按钮表面显示该文本。如果省略 `SetCaption`，按钮将显示为通用标签。

---

## 保存 word document button

最后，将文档持久化到磁盘。`Save` 方法将整个 Word 包（包括新插入的按钮）写入 .docx 文件。

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

文件 `CommandButton.docx` 现在包含一个标记为 **Submit** 的完整功能按钮。当用户在 Microsoft Word 中打开该文件并点击按钮时，默认操作（您以后可以通过 VBA 绑定）将被触发。

---

## 完整工作示例

下面是完整的程序示例，您可以复制、粘贴并运行。它演示了从文档创建到保存按钮的完整工作流。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**预期结果**

* 一个名为 `CommandButton.docx` 的文件，位于您指定的路径。
* 在 Microsoft Word 中打开文件时，第一页会显示一个 **Submit** 按钮。
* 该按钮可以被选中、调整大小，或通过 Word 的 **Developer** 选项卡链接到宏。

---

## 常见问题及边缘情况处理

| 问题 | 答案 |
|----------|--------|
| *如果需要多个按钮怎么办？* | 重复步骤 3–6，使用不同的名称和标题。每个按钮必须具有唯一的 `SetName` 值。 |
| *我可以设置按钮大小吗？* | 可以。插入控件后，您可以通过 `OleFormat` 对象修改其 `Width` 和 `Height` 属性。 |
| *按钮能在所有 Word 版本上工作吗？* | ActiveX 控件在桌面版 Word（Windows）中受支持。它们在 Word Online 或 macOS 上不渲染。 |
| *如何添加点击处理程序？* | 您需要编写引用按钮名称（`btnSubmit`）的 VBA 代码。可以使用 `doc.VbaProject` 嵌入 VBA 宏。 |
| *如果需要在表格单元格内插入按钮怎么办？* | 在调用 `InsertForms2OleControl` 之前，将构建器光标移动到目标单元格（`builder.MoveTo(cell.FirstParagraph)`）。 |

---

## 专业技巧

* **专业提示：** 始终使用 `SetName` 设置有意义的名称。这简化了 VBA 自动化并使调试更容易。
* **注意：** 忘记调用 `SetControlType`。如果不调用，该 OLE 对象将显示为通用占位符，而不是可点击的按钮。
* **性能提示：** 如果在循环中生成大量文档，请复用同一个 `DocumentBuilder` 实例，并在每次插入前调用 `builder.MoveToDocumentEnd()`，以避免不必要的光标重置。

---

## 下一步

现在您已经了解如何**编程创建 Word 文档**、**插入 command button word**、**设置 command button caption**以及**保存 word document button**，可以探索更高级的场景：

* 添加用于用户输入的 **TextFormField** 控件。
* 将按钮与 **MacroButton** 字段结合，以直接执行 VBA。
* 使用 **DocumentBuilder.InsertImage** 在按钮上放置图标。
* 与 ASP.NET 集成，以生成 Word 表单 on

## 接下来应该学习什么？

以下教程涵盖与本指南紧密相关的主题，基于本教程展示的技术。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [创建新 Word 文档](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [使用 Aspose.Words for .NET 创建 Word 文档](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [使用 Aspose.Words 在 Word 文档中插入内联图像](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}