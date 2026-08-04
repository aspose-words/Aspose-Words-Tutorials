---
category: general
date: 2026-08-04
description: 使用 C# 编程方式创建 Word 文档。学习如何仅通过几步使用 Aspose.Words 编程添加命令按钮。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: zh
lastmod: 2026-08-04
og_description: 使用 Aspose.Words 编程创建 Word 文档。本指南展示了如何以编程方式添加命令按钮、配置它并保存文件。
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: 程序化创建 Word 文档 – 完整 C# 教程
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 以编程方式创建Word文档——逐步指南
url: /zh/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 以编程方式创建 Word 文档 – 完整 C# 教程

如果您需要 **以编程方式创建 word document**，本指南将向您展示如何使用 Aspose.Words for .NET 完成此操作。只需几行 C# 代码，您即可生成一个空的 `.docx` 文件，**以编程方式添加 command button** 控件，设置其属性，并保存结果。  

下面的步骤涵盖了从项目设置到处理边缘情况的全部内容，您可以直接将代码复制到自己的应用程序中运行，无需任何修改。

## 您将实现的目标

* 在内存中完整初始化一个新的 Word 文档。  
* **以编程方式添加 command button** OLE 控件，任意位置和尺寸。  
* 配置按钮的标题、内部名称以及其他 OLE 属性。  
* 将生成的文档保存到磁盘或流中，以便后续处理。

### 前提条件

* .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.6+）。  
* 有效的 Aspose.Words for .NET 许可证（或免费试用版）。  
* 对 C# 和 Visual Studio（或您选择的任何 IDE）有基本了解。  

> **专业提示：** 如果在没有许可证的情况下运行示例，Aspose.Words 会在首页添加一个小的评估水印。

## Step 1: 设置项目并导入所需命名空间

创建一个新的 Console App（或集成到现有服务中），并添加 Aspose.Words NuGet 包：

```bash
dotnet add package Aspose.Words
```

然后在 `.cs` 文件的顶部引入必要的命名空间：

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

这些导入让您可以使用 `Document`、`DocumentBuilder`、`Forms2OleControl` 以及用于定位的 `RectangleF` 结构。

## Step 2: 初始化一个全新的 Word 文档

在任何 **create word document programmatically** 工作流中，第一步都是实例化一个 `Document` 对象。该对象仅存在于内存中，直到您显式保存它。

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` 类似于光标，跟踪下一个元素将放置的位置。使用它可以让代码更简洁，并且与直接在 Word 中输入的方式相吻合。

## Step 3: 插入 command button OLE 控件

Aspose.Words 提供 `InsertForms2OleControl` 方法来嵌入 OLE 对象，例如 command button、复选框或组合框。该方法需要三个参数：

1. `ControlType` 枚举值（此处为 `CommandButton`）。  
2. 定义控件 X‑Y 位置以及宽高的 `RectangleF`（单位为点，72 pt = 1 inch）。  
3. 可选的额外 OLE 属性（基础按钮不需要）。

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **工作原理说明：** `InsertForms2OleControl` 在文档中创建一个 OLE 容器并返回一个 `Forms2OleControl` 包装器。该包装器让您能够在不处理底层 COM 互操作的情况下操作实际的 OLE 对象（即按钮本身）。

## Step 4: 配置按钮的标题和内部名称

插入后，通常需要为按钮设置用户可见的标签以及宏或加载项后续引用的内部标识符。

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

* `Caption` 是按钮在 Word UI 中显示的文字。  
* `Name` 是 VBA 或外部自动化脚本使用的程序化标识符。

### 可选：为按钮分配宏

如果您计划在按钮被点击时运行 VBA 宏，可以附加宏名称：

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **边缘情况：** 当目标文档在没有该宏的机器上打开时，Word 会显示安全警告。请务必对宏进行签名或告知用户所需的设置。

## Step 5: 保存文档

您可以将文件写入磁盘、`MemoryStream`，或直接写入 Web API 的响应对象。对于控制台演示，最简单的方式是保存到本地文件夹：

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

生成的 `.docx` 在 Microsoft Word 中打开后，会出现一个功能性的 command button，显示文字 “Click Me”。点击按钮将触发分配的宏（如果有），否则仅显示默认消息。

## 完整工作示例

将以下程序复制到 `Program.cs` 并运行。它演示了完整的 **create word document programmatically** 流程，包括错误处理。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**预期结果：** 在 Word 中打开 `CommandButton.docx` 时，会看到一个标记为 “Click Me” 的按钮。将鼠标悬停在按钮上会在属性窗格中显示名称 `cmdClickMe`。

## 常见问题与故障排除

| Question | Answer |
|----------|--------|
| *我可以将按钮添加到已有文档吗？* | 可以。使用 `new Document("Existing.docx")` 加载文件，然后使用相同的 `InsertForms2OleControl` 调用。 |
| *`RectangleF` 使用什么单位？* | 点（1 inch = 72 pt）。根据需要调整数值以精确定位按钮。 |
| *按钮在 Mac 版 Word 上能工作吗？* | OLE 控件仅在 Windows 版 Word 上受支持。Mac 上按钮会显示为静态图片。 |
| *生产环境需要许可证吗？* | 商业许可证可去除评估水印并解锁全部功能。 |
| *插入后如何修改按钮大小？* | 修改 `commandButton.Width` 和 `commandButton.Height`，或使用新的 `RectangleF` 重新插入。 |

## 扩展方案

既然您已经掌握了 **programmatically add command button** 控件的使用方法，可以进一步探索以下相关主题：

* **插入其他表单控件** – 使用 `ControlType.CheckBox`、`ControlType.OptionButton` 等（涉及二级关键词 *Aspose.Words InsertForms2OleControl*）。  
* **使用动态数据填充文档** – 将数据库中的数据合并到表格或邮件合并字段中。  
* **导出为 PDF** – 添加按钮后，调用 `doc.Save("output.pdf", SaveFormat.Pdf)` 生成 PDF 版本（关联 *C# Word automation*）。  

## 结论

现在，您已经拥有一个完整、可投入生产的模式，能够使用 Aspose.Words for .NET **create word document programmatically** 并 **programmatically add command button**。本教程涵盖了项目设置、文档初始化、OLE 按钮插入、属性配置以及文件保存。欢迎根据需要改写代码，以插入其他表单控件、附加宏，或将逻辑集成到 Web 服务或后台任务中。

祝编码愉快，尽情享受 Word 文档自动化的乐趣！

## 接下来您可以学习什么？

以下教程紧密围绕本指南展示的技术，帮助您进一步掌握 API 的其他功能，并在项目中探索替代实现方案，每篇资源均提供完整可运行的代码示例和逐步说明。

- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}