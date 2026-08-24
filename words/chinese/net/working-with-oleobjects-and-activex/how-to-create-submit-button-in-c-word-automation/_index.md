---
category: general
date: 2026-08-23
description: 在 C# Word 自动化中创建提交按钮。学习如何以编程方式添加 ActiveX 按钮，设置按钮名称、标题和文本。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create submit button
- set button text
- set button name
- add activex button
- set button caption
language: zh
lastmod: 2026-08-23
og_description: 在 C# Word 自动化中创建提交按钮。本指南展示如何使用 Aspose.Words 添加 ActiveX 按钮，并设置其名称、标题和文本。
og_image_alt: Screenshot of a Word document showing a created submit button
og_title: 在 C# Word 自动化中创建提交按钮
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  headline: How to create submit button in C# Word automation
  type: TechArticle
- description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  name: How to create submit button in C# Word automation
  steps:
  - name: Expected output
    text: 'Running the program creates `SubmitButton.docx`. When you open the file
      in Microsoft Word:'
  - name: Handling naming collisions
    text: 'If you run the routine multiple times on the same document, Word may auto‑rename
      duplicate controls. To guarantee uniqueness, you can prepend a GUID:'
  - name: Localizing the button caption
    text: 'For multilingual documents, store captions in a resource file and assign
      them at runtime:'
  - name: Responding to the button click
    text: 'The button itself does not contain click logic in C#. You typically attach
      a VBA macro:'
  type: HowTo
tags:
- C#
- Word automation
- ActiveX
- Aspose.Words
title: 如何在 C# Word 自动化中创建提交按钮
url: /zh/net/working-with-oleobjects-and-activex/how-to-create-submit-button-in-c-word-automation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# Word 自动化中创建提交按钮

如果您需要在 Word 文档中使用 C# **创建提交按钮**，本指南将带您完成整个过程。您将看到如何添加 ActiveX 按钮、分配程序化名称，并设置按钮标题，使其看起来像普通的 *Submit* 控件。

在 Word 中自动化表单控件可以取代手动布局工作，并确保数百份文档的一致性。在下面的步骤中，您还将学习如何 **设置按钮文本**、**设置按钮名称** 和 **设置按钮标题**——这些在按钮参与宏驱动工作流时至关重要。

## 前提条件

在开始之前，请确保您具备：

* 已安装 .NET 6.0（或更高版本）。
* 对 **Aspose.Words for .NET** 的引用（该库提供 `DocumentBuilder.InsertForms2OleControl`）。
* 对 C# 和 Word 的 ActiveX 表单控件有基本了解。

您可以通过 NuGet 安装 Aspose.Words：

```bash
dotnet add package Aspose.Words
```

> **技巧提示：** 使用最新的稳定版 Aspose.Words，以受益于针对 ActiveX 控件的错误修复和新功能。

## 解决方案概述

本教程分为三个清晰的步骤：

1. **添加 ActiveX 按钮** – 使用 `InsertForms2OleControl` 方法在文档中放置一个命令按钮。  
2. **设置按钮名称** – 使用 `Name` 属性分配唯一的程序化标识符。  
3. **设置按钮标题** – 通过 `Caption` 属性定义按钮上可见的文本（这也控制您在 UI 中看到的 **设置按钮文本**）。

通过本指南，您将拥有一个完整可用的 **创建提交按钮** 例程，可在任何 Word 自动化项目中重复使用。

## 步骤 1：向文档添加 ActiveX 按钮

第一步是 **添加 activex 按钮** 到 Word 文件。Aspose.Words 为此提供了 `Forms2OleControlType.CommandButton` 枚举。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load or create a new document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a CommandButton ActiveX control at the cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton);
```

**此步骤的重要性：**  
ActiveX 控件是唯一能够执行 VBA 宏或与外部代码交互的 Word 表单元素。添加控件后会创建一个占位符，后续步骤可以对其进行配置。

> **特殊情况：** 如果文档中已经存在同名控件，Word 会自动为新控件重命名（例如 `CommandButton1`）。在下一步显式设置名称可避免此类冲突。

## 步骤 2：设置按钮名称

在需要从 VBA 或 C# 代码的其他部分引用控件时，可靠的 **设置按钮名称** 至关重要。`Name` 属性为按钮提供了程序化标识符。

```csharp
// Assign a unique programmatic name
commandBtn.Name = "btnSubmit";
```

**为什么要设置名称：**  
打开文档时，VBA 可以通过 `ActiveDocument.InlineShapes("btnSubmit")` 获取按钮。像 `btnSubmit` 这样的有意义的名称在检查文档 XML 时也能明确意图。

> **技巧提示：** 保持名称简短、字母数字组合，并以字母开头，以兼容 VBA 命名规则。

## 步骤 3：设置按钮标题（可见文本）

用户在按钮上看到的文本由 **设置按钮标题** 属性控制。在 Word 的 UI 中，这显示为按钮的标签，也就是您想要显示的 **设置按钮文本**。

```csharp
// Define the text shown on the button
commandBtn.Caption = "Submit";
```

**标题为何重要：**  
标题是面向用户的标签。之后更改它不会影响按钮的名称，因此您可以在不破坏依赖 `btnSubmit` 的代码的情况下本地化 UI。

> **常见问题：** *我可以同时设置 Caption 和 Value 吗？*  
> 对于 `CommandButton`，`Caption` 控制标签，而 `Value` 未使用。如果需要隐藏值，请改为存储在自定义文档属性中。

## 完整工作示例

将三个步骤组合在一起，可得到一个完整的例程，您可以将其放入任何控制台或 Windows 应用程序中：

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
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert the ActiveX command button
        Forms2OleControl commandBtn = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton);

        // 3. Set a meaningful name for later reference
        commandBtn.Name = "btnSubmit";

        // 4. Set the visible caption (this is the button text)
        commandBtn.Caption = "Submit";

        // Optional: position the button (in points)
        commandBtn.Left = 100;   // distance from left margin
        commandBtn.Top = 200;    // distance from top margin
        commandBtn.Width = 80;
        commandBtn.Height = 30;

        // Save the document
        doc.Save("SubmitButton.docx");
        Console.WriteLine("Document with submit button created successfully.");
    }
}
```

### 预期输出

运行程序会生成 `SubmitButton.docx`。在 Microsoft Word 中打开该文件时：

* 在指定位置出现一个 **Submit** 按钮。
* 按钮的名称为 `btnSubmit`（可通过 *Developer → Design Mode → Properties* 检查）。
* 在设计模式下单击按钮会显示标题 *Submit*。

您现在拥有一个可重复使用的构建块，可用于任何基于表单的 Word 解决方案。

## 其他注意事项

### 处理命名冲突

如果在同一文档上多次运行例程，Word 可能会自动重命名重复的控件。为确保唯一性，您可以在前面添加 GUID：

```csharp
commandBtn.Name = $"btnSubmit_{Guid.NewGuid():N}";
```

### 本地化按钮标题

对于多语言文档，可将标题存储在资源文件中，并在运行时分配：

```csharp
commandBtn.Caption = Resources.SubmitButtonLabel;
```

### 响应按钮点击

按钮本身在 C# 中不包含点击逻辑。通常会附加一个 VBA 宏：

```vba
Sub btnSubmit_Click()
    MsgBox "Form submitted!"
End Sub
```

因为您已 **设置按钮名称** 为 `btnSubmit`，宏名称会自动遵循 `<Name>_Click` 约定。

## 故障排除 FAQ

| Question | Answer |
|----------|--------|
| **为什么按钮显示为空白？** | 确保已设置 `Caption` 属性；如果未设置，按钮将不显示文字。 |
| **我可以使用其他 ActiveX 控件吗？** | 可以。将 `Forms2OleControlType.CommandButton` 替换为 `CheckBox`、`OptionButton` 等，但属性会有所不同。 |
| **这与 .NET Core 兼容吗？** | Aspose.Words for .NET 支持 .NET 6+，因此相同的代码可在 .NET Core 和 .NET Framework 上运行。 |
| **如果文档已经有按钮怎么办？** | 使用唯一的 `Name`（例如追加 GUID）以避免冲突。 |

## 结论

您现在了解如何使用 C# 在 Word 文档中以编程方式 **创建提交按钮**。通过遵循这三个步骤——**添加 activex 按钮**、**设置按钮名称** 和 **设置按钮标题**，您可以可靠地为任何自动化表单解决方案 **设置按钮文本**、**设置按钮名称** 和 **设置按钮标题**。

接下来您可以探索：

* 添加响应 **提交按钮** 点击的 VBA 宏。
* 通过底层 XML 使用自定义字体或颜色对按钮进行样式设置。
* 在循环中生成多个按钮以实现动态表单。

随意尝试不同的标题、名称和位置，以适应您的具体工作流。祝您自动化愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方式。每个资源都包含完整的可运行代码示例和逐步解释。

- [使用 Aspose.Words for .NET 在 Word 文档中创建组形状](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words for .NET 在 Word 中创建折线图](/words/english/net/working-with-charts/create-chart-using-shape/)
- [使用 Aspose.Words 创建带页眉页脚的 Word 文档](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}