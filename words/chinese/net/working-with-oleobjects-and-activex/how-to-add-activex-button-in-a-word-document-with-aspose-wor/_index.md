---
category: general
date: 2026-08-14
description: 如何使用 Aspose.Words 在 Word 文档中添加 ActiveX 按钮——学习创建空白 Word 文档并以编程方式插入 ActiveX
  按钮。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: zh
lastmod: 2026-08-14
og_description: 如何使用 Aspose.Words 在 Word 文档中添加 ActiveX 按钮。本教程展示了如何创建空白 Word 文档、插入
  ActiveX 按钮并保存结果。
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: 如何在 Word 中添加 ActiveX 按钮——Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: 如何使用 Aspose.Words 在 Word 文档中添加 ActiveX 按钮
url: /zh/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文档中使用 Aspose.Words 添加 ActiveX 按钮

如果您需要在生成的 Word 文件中 **how to add ActiveX** 控件，本指南将向您展示具体步骤。您将学习如何以编程方式 **insert ActiveX button**，从 **create empty Word document** 开始，直至保存的文件可在 Microsoft Word 中打开。

添加一个运行 VBA 代码或触发宏的按钮是自动化报告生成器、表单模板或交互式合同的常见需求。使用 Aspose.Words for .NET 可以在不启动 Office 的情况下构建文档，使过程快速且适合服务器环境。

## 前提条件

* .NET 6.0（或更高）SDK 已安装。
* Visual Studio 2022 或任何兼容 C# 的 IDE。
* Aspose.Words for .NET NuGet 包（`Aspose.Words` 版本 24.9 或更高）。  
  安装方法如下：  
  ```bash
  dotnet add package Aspose.Words
  ```
* 如果您计划测试 ActiveX 按钮，需要 Windows 环境，因为 ActiveX 控件需要 Windows 版 Microsoft Word。

## 步骤 1：创建空的 Word 文档

第一步是 **create empty Word document** 到内存中。Aspose.Words 提供了 `Document` 类来实现此目的。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` 表示整个 .docx 文件。此时文档尚未包含任何页面，但您可以立即开始添加内容。

## 步骤 2：初始化 DocumentBuilder

`DocumentBuilder` 是一个帮助类，允许您向文档插入文本、图像和其他对象。它作用于您刚创建的 `Document` 实例。

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

构建器维护光标位置；在此行之后插入的任何内容都会出现在第一页的起始位置。

## 步骤 3：插入 ActiveX CommandButton 控件

Aspose.Words 提供了 `InsertForms2OleControl` 方法，用于添加包括 ActiveX 在内的传统表单控件。该方法需要指定控件类型以及其尺寸（以磅为单位）。

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

返回的 `Forms2OleControl` 对象允许您配置属性，例如控件的名称和标题。

## 步骤 4：配置按钮属性

设置有意义的 `Name` 可以让您在后续的 VBA 代码中引用该控件。`Caption` 是用户在按钮上看到的文本。

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **技巧提示：** 保持名称简短且仅含字母和数字；Word 会拒绝包含空格或特殊字符的名称。

## 步骤 5：保存文档

最后，将文档写入磁盘。使用 `.docx` 扩展名保存现代 Word 文件；ActiveX 按钮在 `.doc` 文件中同样有效，但 `.docx` 是新项目的首选格式。

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

当您在 Microsoft Word 中打开 `ActiveXButton.docx` 时，会看到一个可点击的 **Submit** 按钮。如果启用宏，您可以将 VBA 代码附加到 `btnSubmit_Click`，使其在用户点击按钮时执行。

## 完整、可运行的示例

将所有代码组合在一起即可得到一个独立的程序，您可以复制、粘贴并运行它。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**预期输出** – 运行程序后，控制台会打印保存位置，打开生成的 Word 文件时，会在第一页顶部看到标有 **Submit** 的按钮。

## 处理常见问题和边缘情况

### 按钮在所有 Word 版本中都能工作吗？

ActiveX 控件仅在 Windows 桌面版 Word 中受支持。它们在 Word Online、macOS 版 Word 或移动客户端中无法呈现。如果需要跨平台交互，建议改用内容控件或基于 HTML 的解决方案。

### 如果需要不同的尺寸或位置怎么办？

`InsertForms2OleControl` 将控件放置在当前构建器光标位置。要移动它，可在插入前使用 `builder.MoveTo` 调整光标，或在创建后修改控件的 `Left` 和 `Top` 属性：

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### 我可以添加其他类型的 ActiveX 吗？

可以。`Forms2OleControlType` 枚举包含 `CheckBox`、`OptionButton`、`ListBox` 等。将 `CommandButton` 替换为所需的枚举值，并相应地调整属性。

### 按钮要执行操作是否需要宏？

按钮本身不会执行任何操作，除非您附加 VBA 代码。在 Word 中，按 **Alt+F11** 打开 VBA 编辑器，定位 `btnSubmit_Click` 并编写所需逻辑。如果使用 **SaveFormat.Doc**（旧版 `.doc`）格式，生成的文档会保留 VBA 项目，但 `.docx` 文件无法存储 VBA 宏。如果需要嵌入 VBA，请使用 `.doc` 格式。

## 结论

现在，您已经了解如何使用 Aspose.Words **how to add ActiveX** 控件到 Word 文件。通过遵循 **create empty Word document**、初始化 `DocumentBuilder`、**insert ActiveX button**、配置属性并保存文件的步骤，您可以直接从 .NET 代码生成交互式 Word 模板。

接下来，探索相关主题，例如 **insert ActiveX button** 事件处理、为表格或图像添加 **create word document aspose**，以及为企业部署保护启用宏的文档。尝试不同的控件类型和布局选项，以根据您的应用需求定制用户体验。

祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}