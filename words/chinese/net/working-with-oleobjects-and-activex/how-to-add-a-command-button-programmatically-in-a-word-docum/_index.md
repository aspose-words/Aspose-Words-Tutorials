---
category: general
date: 2026-10-13
description: 学习如何使用 Aspose.Words 以编程方式添加命令按钮。本指南还展示了如何使用完整的 C# 代码创建 Word 文档按钮。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: zh
lastmod: 2026-10-13
og_description: 使用 Aspose.Words 以编程方式向 Word 文档添加命令按钮。请按照本完整教程使用 C# 创建 Word 文档按钮。
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: 在 Word 文档中以编程方式添加命令按钮——逐步指南
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 如何在 Word 文档中以编程方式添加命令按钮
url: /zh/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文档中以编程方式添加命令按钮  

如果您需要**以编程方式添加命令按钮**，Aspose.Words 提供了简洁的 API，允许您直接在 .docx 文件中嵌入 OLE 表单控件。本教程将逐步演示如何**创建 Word 文档按钮**，使其在 Microsoft Word 中打开时表现得像普通的表单按钮。  

您将学习如何设置开发环境、插入按钮、配置属性并验证结果。无需任何外部工具——只需一个 .NET 项目和 Aspose.Words for .NET 库。  

## 前提条件  

在开始之前，请确保您已拥有：  

* 已安装 .NET 6.0 SDK 或更高版本。  
* 最近版本的 Aspose.Words for .NET（示例使用 23.12，但任何 22.x+ 版本均可）。  
* 如 Visual Studio 2022 或 Visual Studio Code 等 IDE。  

该代码可在 Windows、macOS 和 Linux 上运行，因为 Aspose.Words 是跨平台的。  

## 步骤 1：设置项目并引用 Aspose.Words  

1. 创建一个新的控制台项目：  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. 添加 Aspose.Words NuGet 包：  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. 打开 **Program.cs** 并将其内容替换为下一步中展示的框架代码。  

以这种方式设置项目可确保编译器能够找到用于表单控件的 `Aspose.Words` 和 `Aspose.Words.Drawing.Forms` 命名空间。  

## 步骤 2：初始化空白文档和 DocumentBuilder  

`Document` 类表示整个 Word 文件，而 `DocumentBuilder` 提供了用于添加内容的流式 API。  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*此步骤的重要性* – 没有 `DocumentBuilder`，您无法在页面上精确定位按钮。该构建器还会遵循当前光标位置，便于以后插入多个控件。  

## 步骤 3：插入命令按钮 OLE 控件  

Aspose.Words 将命令按钮视为 `ControlType.CommandButton` 类型的 OLE 控件。您可以使用以点为单位（1 点 = 1/72 英寸）的 `RectangleF` 来定义其位置和大小。  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**关键点**  

* 矩形的原点 (X, Y) 相对于页面左上角。  
* 更改 `Width` 或 `Height` 会改变按钮的可视大小。  
* `InsertForms2OleControl` 返回一个 `Forms2OleControl` 对象，您可以进一步配置它。  

## 步骤 4：配置按钮的名称和标题  

**名称** 用于 Word 的宏引擎标识控件，而 **标题** 是用户看到的文本。  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

如果您计划稍后添加 VBA 宏，请使用描述性的名称，因为 Word 的宏记录器会引用此属性。  

## 步骤 5：（可选）保存文档并验证结果  

保存文件后，您可以在 Microsoft Word 中打开它，以确认按钮已出现并正常工作。  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

在 Word 中打开 *CommandButtonDemo.docx* 时，您应该会看到一个标有 **Submit** 的按钮，位置大约距左边距 1.4 英寸、距页面顶部 2.1 英寸。默认情况下点击按钮不会有任何动作，因为未附加宏，但该可视控件已完全可用。  

## 步骤 6：边缘情况和常见陷阱  

| Situation | What to watch for | Recommended fix |
|-----------|-------------------|-----------------|
| **按钮与现有文本重叠** | 矩形可能与段落相交，导致布局问题。 | 在调用 `builder.Writeln()` 后插入按钮，使光标移动到新行，或调整 `Y` 坐标。 |
| **文档打开时出现警告** | 某些 Word 版本会对缺少关联程序的 OLE 控件发出警告。 | 确保控件类型为 `CommandButton`；Word 将其视为标准表单元素，无需外部程序。 |
| **在无头环境的 Linux 上运行** | 无法启动 Word 来测试 UI，但文件仍然有效。 | 使用单元测试读取控件属性（`commandButton.Name`、`commandButton.Caption`），以验证其已正确设置。 |
| **需要多个按钮** | 重复使用相同的 `DocumentBuilder` 而不移动光标会导致按钮叠加在之前的按钮上。 | 在每次插入前调用 `builder.MoveToDocumentEnd()` 或调整矩形的 `Y` 值。 |

提前处理这些边缘情况可在将解决方案扩展到包含数十个控件的完整表单时节省时间。  

## 步骤 7：完整、可运行的示例  

下面是一个独立的程序，您可以复制、粘贴并直接运行（除 NuGet 还原外无需其他修改）。  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**预期输出**  

运行程序会打印类似以下的路径：  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

打开生成的 *CommandButtonDemo.docx* 会看到一个位于代码中定义坐标的 **Submit** 按钮。未出现其他 UI 元素，确认 **以编程方式添加命令按钮** 的工作流成功。  

## 结论  

现在，您已经了解如何使用 Aspose.Words **以编程方式向 Word 文档添加命令按钮**，以及如何 **创建 Word 文档按钮**，以后可以将其绑定到 VBA 宏或外部自动化工具。该过程包括初始化文档、插入 OLE `CommandButton` 控件、配置属性并保存文件。  

接下来您可以：  

* 通过重复步骤 3 并使用不同的 `ControlType` 值，添加更多控件（复选框、文本字段）。  
* 为按钮附加 VBA 宏，以执行保存表单或发送电子邮件等操作。  
* 通过遍历基于数据的字段定义集合，动态生成完整表单。  

尝试调整矩形坐标和按钮标题，以符合您的 UI 设计。祝编码愉快！  

## 接下来您应该学习什么？

以下教程涵盖与本指南技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能，并在自己的项目中探索替代实现方案。

- [使用 Aspose.Words for .NET 向 Word 文档添加组合框表单字段](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [使用 Aspose.Words for .NET 向 Word 文档添加复选框表单字段](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [使用 Aspose.Words 创建空白 Word 文档 – 步骤指南](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}