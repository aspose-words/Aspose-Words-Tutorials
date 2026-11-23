---
category: general
date: 2026-11-22
description: 学习如何使用 C# 在 Word 中插入 Forms2Ole 控件。本分步指南涵盖 DocumentBuilder、命令按钮的放置以及 .docx
  的保存。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: zh
lastmod: 2026-11-22
og_description: 使用 C# 在 Word 中插入 Forms2Ole 控件。请按照本指南使用 Aspose.Words 和 DocumentBuilder
  添加命令按钮。
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: 使用 C# 在 Word 中插入 Forms2Ole 控件 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: 如何使用 C# 和 Aspose.Words 在 Word 中插入 Forms2Ole 控件
url: /zh/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中使用 C# 和 Aspose.Words 插入 Forms2Ole 控件

如果您需要 **在 Word 中插入 Forms2Ole 控件**，本教程将向您展示如何使用 C# 完成此操作。无论是构建可填写的模板还是自动化表单创建，下面的方案都可以让您以编程方式添加命令按钮。

您将学习如何创建空白文档，使用 `DocumentBuilder` 放置控件，并将结果保存为 `.docx`。指南还涵盖了常见的陷阱，例如坐标系以及与旧版 Word 的兼容性。

## 前置条件

在开始之前，请确保您具备：

* .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.6+）
* Aspose.Words for .NET（NuGet 包 `Aspose.Words`）
* 对 C# 和 Word 对象模型的基本了解
* Visual Studio 或 VS Code 等 IDE

## 第 1 步：设置项目并导入命名空间

创建一个新的控制台应用程序并添加 Aspose.Words 包：

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

在 `Program.cs` 中导入所需的命名空间：

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **小贴士：** 使用最新的 Aspose.Words 版本以获得对 `Forms2OleControl` API 的完整支持。

## 第 2 步：创建空白文档并初始化 DocumentBuilder

`Document` 类代表 Word 文件，而 `DocumentBuilder` 提供插入内容的方法。

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` 的工作方式类似光标；在此行之后，您可以在文档的任意位置放置元素。

## 第 3 步：定义按钮的位置和大小

Word 使用点（pt）作为坐标单位（1 pt ≈ 1/72 英寸）。`System.Drawing` 中的 `Rectangle` 结构描述控件的边界。

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` 将控件放置在当前页面的左上角。
* 调整 `x` 和 `y` 可将按钮移动到其他位置（例如 `new Rectangle(150, 200, 100, 30)`）。

## 第 4 步：插入 Forms2Ole 命令按钮

现在使用 `InsertForms2OleControl` 添加控件。该方法需要控件类型、名称以及上面定义的边界。

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

返回的 `Forms2OleControl` 对象允许您修改属性，例如 `Enabled`、`Visible`，甚至以后再附加宏名称。

### 为什么使用 Forms2Ole？

* **向后兼容** – Forms2Ole 控件在 Word 97‑2003（`.doc`）和更新的 `.docx` 文件中均可工作。
* **宏支持** – 它们可以触发 VBA 宏，非常适合交互式模板。
* **精确定位** – 与内容控件不同，您可以控制确切坐标。

## 第 5 步：保存文档

最后，将文件写入磁盘。请选择您拥有写入权限的文件夹。

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

在 Microsoft Word 中打开 `output.docx`。您会看到第一页左上角有一个标记为 **ClickMe** 的按钮。该按钮在 Word 中点击后不会执行任何操作，除非您分配了宏，但控件已完全可用。

## 处理常见边缘情况

| 情况 | 解决办法 |
|-----------|-------------------|
| **按钮显示在页面之外** | 确认 `Rectangle` 坐标在页面边距范围内。使用 `builder.PageSetup.PageWidth` 和 `PageHeight` 计算安全边界。 |
| **在旧版 Word 中控件不可见** | 将文档保存为 `.doc`（`doc.Save("output.doc", SaveFormat.Doc)`），以确保 Word 97‑2003 对 Forms2Ole 的兼容性。 |
| **需要更改按钮文字** | 插入后，设置 `commandButton.Caption = "Submit";`。 |
| **分配宏** | 设置 `commandButton.MacroName = "MyMacro"`；宏必须存在于文档的 VBA 项目中。 |
| **多个按钮** | 对不同的 `Rectangle` 值和唯一名称重复第 4 步。 |

## 完整可运行示例

将所有内容组合在一起，下面是一个可直接复制、粘贴并运行的独立程序：

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**预期输出：** 运行程序后，`output.docx` 在 Word 中打开，页面左上角出现一个标记为 *Click Me!* 的可点击按钮。

## 结论

现在，您已经掌握了使用 C# 和 Aspose.Words **在 Word 中插入 Forms2Ole 控件** 的方法。该过程包括创建 `Document`、定位 `Rectangle`，以及通过 `DocumentBuilder` 调用 `InsertForms2OleControl`。借助完整的代码示例和边缘情况指南，您可以将命令按钮集成到任何自动化的 Word 工作流中。

### 后续步骤

* 探索其他 `ControlType` 值，如 `CheckBox` 或 `OptionButton`。
* 将 Forms2Ole 控件与 VBA 宏结合，实现交互式表单。
* 使用 `DocumentBuilder.MoveTo` 将按钮放置在特定段落或表格中。
* 查阅 Aspose.Words 的 **Forms2Ole** 文档，了解高级属性设置。

祝编码愉快，尽情使用 C# 和 Aspose.Words 构建更丰富的 Word 文档！

## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方式，每个资源都提供完整的可运行代码示例和逐步解释。

- [How to insert OLE command button in a Word document using C#](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [how to add activex control in Word with Aspose.Words – step‑by‑step guide](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}