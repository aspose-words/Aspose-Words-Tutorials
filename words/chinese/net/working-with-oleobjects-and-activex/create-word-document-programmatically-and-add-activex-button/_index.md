---
category: general
date: 2026-08-10
description: 使用 Aspose.Words 编程创建 Word 文档，然后添加 ActiveX 控件按钮。几分钟内即可插入 ActiveX 命令按钮。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: zh
lastmod: 2026-08-10
og_description: 使用 Aspose.Words 编程创建 Word 文档，然后添加 ActiveX 控件按钮。快速学习如何插入 ActiveX 命令按钮。
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: 以编程方式创建 Word 文档 – 在 C# 中添加 ActiveX 按钮
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: 以编程方式创建 Word 文档并添加 ActiveX 按钮
url: /zh/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 以编程方式创建 Word 文档并添加 ActiveX 按钮

如果您需要 **以编程方式创建 Word 文档**，本指南将带您使用 Aspose.Words for .NET 完成整个过程。您还将学习如何 **向 Word 中添加 ActiveX 控件** 元素以及 **插入 ActiveX 命令按钮** 对象，示例为单文件、完整自包含。

通过代码生成 Word 文件可以省去手动打开 Microsoft Word 的步骤，让您自动生成报告、发票或基于数据的合同。完成本教程后，您将拥有一个可直接运行的 C# 控制台应用程序，能够生成包含交互式 ActiveX CommandButton 的 `.docx` 文件。

## 前置条件

在开始之前，请确保您具备以下条件：

* .NET 6.0 SDK 或更高版本（代码同样适用于 .NET Framework 4.6+）
* Visual Studio 2022 或任何支持 .NET 开发的 IDE
* 有效的 Aspose.Words for .NET 许可证（可使用免费评估密钥进行测试）
* 对 C# 语法以及 COM/ActiveX 控件概念有基本了解

> **专业提示**：如果您计划将生成的文档分发给未安装 Word 的用户，请将 ActiveX 控件的运行时文件与 `.docx` 一起嵌入，或提供宏启用的模板。

## 以编程方式创建 Word 文档 – 初始设置

首先，将 Aspose.Words NuGet 包添加到项目中：

```bash
dotnet add package Aspose.Words
```

然后创建一个新的控制台项目（如果尚未创建）：

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

打开生成的 `Program.cs` 文件——我们将在下面用完整的解决方案代码替换其内容。

## 步骤 1：导入命名空间并配置许可证

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*为什么重要*：导入 `Aspose.Words.Drawing` 可让您使用 `Forms2OleControl` 类，该类代表 Word 文档中的 ActiveX 控件。提前设置许可证可以避免生产环境中的运行时警告。

## 步骤 2：创建空白文档并实例化 DocumentBuilder

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` 对象是 `.docx` 文件的内存表示。`DocumentBuilder` 则像光标一样在文档中移动，以插入各种元素。

## 步骤 3：插入 ActiveX CommandButton 控件

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` 会创建一个 OLE 对象，Word 将其视为 ActiveX 控件。坐标系使用点（1 point = 1/72 英寸），这与 Word 的布局引擎保持一致。

## 步骤 4：设置按钮的标题及可选属性

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

设置 `Caption` 属性是为按钮添加标签的最常用方式。如果需要按钮执行 VBA 宏，可将宏名称赋给 `OnAction`。本教程侧重于可视化部分，宏集成将在 “后续步骤” 中介绍。

## 步骤 5：保存文档

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

运行程序后，您将在控制台看到一条信息，确认 `ActiveX_CommandButton.docx` 已写入磁盘。

### 完整源代码（可直接复制粘贴）

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

运行上述代码片段后，会生成一个包含可点击 **ActiveX command button** 的 Word 文件。用 Microsoft Word 打开该文件，切换到 **Design Mode**（开发者选项卡 → Design Mode），即可看到按钮正好出现在您放置的位置。

## 步骤 6：验证结果

1. 在 Microsoft Word 中打开 `ActiveX_CommandButton.docx`。
2. 若未看到 **Developer**（开发者）选项卡，请启用它（`File → Options → Customize Ribbon → 勾选 Developer`）。
3. 点击 **Design Mode**。按钮应显示标签 “Submit”。
4. 若您为按钮设置了 `OnAction` 宏，请在关闭 Design Mode 的情况下点击按钮，以触发宏。

如果按钮未显示，请确保 Word 的安全设置允许 ActiveX 控件（`File → Options → Trust Center → Trust Center Settings → ActiveX Settings`）。

## 常见问题与边缘情况

| Question | Answer |
|----------|--------|
| **Can I insert other ActiveX types?** | Yes. `Forms2OleControlType` enum includes `CheckBox`, `OptionButton`, `ComboBox`, etc. Replace `CommandButton` with the desired enum value |

## 接下来应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您在已有技巧的基础上进一步深入。每篇资源都提供完整的可运行代码示例，并配有逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}