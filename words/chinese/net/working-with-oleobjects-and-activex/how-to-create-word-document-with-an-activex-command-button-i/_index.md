---
category: general
date: 2026-09-05
description: 使用 Aspose.Words C# 创建 Word 文档，并学习如何插入 ActiveX 命令按钮、设置按钮大小以及添加交互式按钮功能。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: zh
lastmod: 2026-09-05
og_description: 在 C# 中创建 Word 文档并插入 ActiveX 命令按钮。本教程展示如何设置按钮大小以及添加交互式按钮功能。
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: 在 C# 中创建带 ActiveX 命令按钮的 Word 文档 – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: 如何在 C# 中创建带有 ActiveX 命令按钮的 Word 文档
url: /zh/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中使用 ActiveX 命令按钮创建 Word 文档

如果您需要 **以编程方式创建 Word 文档** 并嵌入可点击的 UI 元素，本指南将一步步演示。使用 Aspose.Words for .NET，您可以 **创建 Word 文档**、**添加命令按钮**，并控制其外观——全部无需打开 Microsoft Word。

您将学习 **如何插入 ActiveX** 控件、**设置按钮大小**，以及让按钮表现得像交互式 UI 组件。无需 COM 或 VBA 经验，只需一个 .NET 开发环境和 Aspose.Words 库。

## 您将实现的目标

完成本教程后，您将能够：

* **使用 C# 从头创建 Word 文档**。
* **插入 ActiveX 命令按钮**（经典的 “Click Me” 控件）。
* **精确设置按钮的大小和位置**。
* 可选地添加简单的 **交互式按钮** 逻辑（例如宏占位符）。
* 将文件保存为 `.docx`，可在 Microsoft Word 或任何兼容的查看器中打开。

### 前置条件

| 要求 | 原因 |
|------|------|
| .NET 6.0 或更高版本 | 为 C# 代码提供运行时环境。 |
| Aspose.Words for .NET（最新版本） | 提供示例中使用的 `Document`、`DocumentBuilder` 和 `Forms2OleControl` API。 |
| Visual Studio 2022（或任意 C# IDE） | 便于编译和运行示例。 |
| 基础 C# 知识 | 需要理解代码流程。 |

> **专业提示：** 如果使用 Aspose.Words 的试用版，请务必在运行代码前设置许可证，以避免出现评估水印。

## 创建 Word 文档的整体工作流

该过程包括四个逻辑步骤：

1. **初始化新文档** 并创建 `DocumentBuilder` 进行编辑。  
2. 使用 `InsertForms2OleControl` **插入 ActiveX 命令按钮**。  
3. **配置按钮**——标题、大小和位置。  
4. **保存** 文档到磁盘。

下面的各节将分别解释每一步。

![带有 ActiveX 按钮的 Word 文档](/images/activex-button.png "包含使用 C# 创建的 ActiveX 命令按钮的 Word 文档截图")

## 如何插入 ActiveX 命令按钮

**插入 ActiveX** 的部分从 `InsertForms2OleControl` 方法开始。该方法创建一个基于 COM 的控件，Word 将其视为 ActiveX 对象。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**工作原理说明：** `OleControlType.CommandButton` 告诉 Aspose.Words 创建经典的 VB 风格按钮。大小和位置使用点（1 point = 1/72 英寸）表示，能够精确控制布局。

## 如何添加命令按钮并设置按钮大小

控件插入后，您可以调整其视觉属性。**添加命令按钮** 步骤还涵盖 **设置按钮大小**。

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**说明：**  

* `Caption` 是按钮上显示的标签。  
* `Width` 和 `Height` 让您在首次插入后 **设置按钮大小**——当大小取决于运行时数据时非常有用。  
* `Left` 和 `Top` 在不重新创建文档的情况下重新定位控件。

> **常见陷阱：** 使用像素而非点会导致按钮显示过小或过大。若从屏幕测量开始，请始终将像素值转换为点（`px * 72 / DPI`）。

## 如何添加交互式按钮（可选）

ActiveX 按钮可以在点击时执行宏，但从 C# 嵌入 VBA 代码超出纯 Aspose.Words 工作流的范围。相反，您可以添加一个占位属性，Word 会将其识别为宏名称。

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

当用户在 Word 中打开生成的 `.docx` 时，点击按钮将尝试运行 `MyMacroName`。如果该宏不存在，Word 会提示用户创建它。

**使用场景：** 对于企业表单，宏负责填充字段时，C# 代码只需放置按钮；宏逻辑则位于文档的 VBA 项目中。

## 保存文档并验证结果

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**预期输出：** 在 Microsoft Word 中打开 `CommandButton.docx`，会看到一个标有 **Click Me** 的按钮，左边距 100 pts、上边距 120 pts。按钮尺寸为 **200 pts × 80 pts**。点击按钮会触发宏占位符（如果存在）。

## 完整可运行示例

下面是将所有步骤整合在一起的完整可运行程序。将其复制到新的 Console App 项目中，添加 Aspose.Words NuGet 包后运行。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

运行程序后，打开生成的文件，即可看到已准备好的 **交互式按钮**，可进一步自定义。

## 常见问题

| 问题 | 回答 |
|------|------|
| **这在 .NET Core 上可用吗？** | 可以。Aspose.Words 支持 .NET Standard，代码同样适用于 .NET 5/6/7。 |
| **我可以使用其他 ActiveX 控件（例如 CheckBox）吗？** | 当然。将 `OleControlType.CommandButton` 替换为 `OleControlType.CheckBox`、`OleControlType.OptionButton` 等即可。 |
| **如果在横向页面上需要更大的按钮怎么办？** | 按比例调整 `Width`、`Height`、`Left` 和 `Top` 属性。请记住，无论页面方向如何，点的单位保持不变。 |
| **按钮可点击是否必须配合宏？** | 不需要。按钮本身就是完整的 UI 元素，宏仅在点击时提供自定义行为。 |

## 结论

现在，您已经掌握了使用 Aspose.Words **创建 Word 文档**、**添加命令按钮**、**设置按钮大小**，以及可选地将按钮链接到宏以实现 **交互式按钮** 行为的完整流程。这种方法可帮助您自动化表单创建、生成动态报告，或直接从 C# 构建基于 Word 的 UI 原型。

接下来，您可以探索：

* **如何为调查表单插入 ActiveX 复选框**。  
* **如何使用 `DocumentBuilder` 在按钮周围添加富文本内容**。  
* **如何在保持按钮功能的同时保护文档**。  

欢迎尝试不同的控件类型、尺寸和宏名称，以满足您的具体场景。祝编码愉快！


## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方式。

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}