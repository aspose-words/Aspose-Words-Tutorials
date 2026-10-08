---
category: general
date: 2026-10-07
description: 学习如何使用 Aspose.Words C# 在 Word 文档中插入 OLE 命令按钮。一步步指南，涵盖 DocumentBuilder、属性以及文件保存。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: zh
lastmod: 2026-10-07
og_description: 使用 C# 在 Word 文档中插入 OLE 命令按钮。请按照本简明教程添加、配置并保存带有 Aspose.Words 的功能性 CommandButton。
og_image_alt: Insert OLE command button example in Word document
og_title: 使用 C# 在 Word 中插入 OLE 命令按钮 – 完整的 Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: 如何使用 C# 在 Word 文档中插入 OLE 命令按钮
url: /zh/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 C# 在 Word 文档中插入 OLE 命令按钮

如果您需要 **在 Word 文件中以编程方式插入 OLE 命令按钮**，本指南将向您展示如何使用 Aspose.Words for .NET 完成此操作。无论是构建带填表的报告，还是自动化需要用户交互的模板，下面的步骤都提供了完整、可运行的解决方案。

您将学习如何创建空白文档，使用 `DocumentBuilder` 放置 `Forms2OleControl`，设置按钮的标题和名称，最后保存为 `.docx`。除了 Aspose.Words 库外，无需任何外部工具。

## 前置条件

开始之前，请确保您具备以下条件：

* .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.7+）
* 有效的 Aspose.Words for .NET 许可证或免费评估密钥
* Visual Studio 2022（或您喜欢的任何 C# IDE）
* 对 C# 语法和 Word OLE 概念有基本了解

> **专业提示：** 如果使用免费评估版，生成的文档会包含一个小水印。正式授权版会自动去除该水印。

## 第一步：安装 Aspose.Words

通过 NuGet 将 Aspose.Words 包添加到项目中：

```bash
dotnet add package Aspose.Words
```

该包包含 `Aspose.Words.Drawing` 和 `Aspose.Words.Drawing.Ole` 命名空间，这些是使用 OLE 控件所必需的。

## 第二步：使用 DocumentBuilder 插入 OLE 命令按钮

本教程的核心是 `InsertForms2OleControl` 方法。它会在指定位置和尺寸创建一个 **Forms2 OLE CommandButton**。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### 为什么这样可行

* `DocumentBuilder` 是以编程方式构建 Word 文档的主要 API。  
* `InsertForms2OleControl` 告诉 Aspose.Words 嵌入 **Forms2 OLE 控件**，这是一种支持命令按钮、复选框等的旧版 Word 表单技术。  
* `OleControlType.CommandButton` 枚举值指定插入的控件类型为 **命令按钮**——正是您在 **插入 OLE 命令按钮** 时所需要的类型。  
* `Rectangle` 决定了可视化位置。您可以根据布局调整 X/Y 坐标或宽高。

## 第三步：保存文档

配置完按钮后，将文档写入磁盘。您可以选择 Aspose.Words 支持的任意格式（`.docx`、`.pdf`、`.odt` 等）。本教程中我们将保存为 Word 文档。

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

当您在 Microsoft Word 中打开 `CommandButton.docx` 时，会看到一个标有 **Click Me** 的可点击按钮。在 Word 中点击它会触发默认的 “运行宏” 对话框，因为该按钮是 OLE 表单控件；如果需要，您以后可以为其附加宏或 VBA 代码。

## 第四步：验证结果（预期输出）

打开生成的文件：

1. 按您指定的坐标（大约距页面左侧和顶部 1.4 英寸）出现按钮。  
2. 标题显示为 **Click Me**。  
3. 名称属性 (`cmdSubmit`) 可在 Word 的 **开发工具 → 属性** 面板中看到，这在需要从 VBA 引用控件时非常有用。

![在 Word 文档中插入 OLE 命令按钮示例](insert-ole-button.png)

*图片替代文字*：**在 Word 文档中插入 OLE 命令按钮示例**（包含主要关键词以提升可访问性和 SEO）。

## 边缘情况与常见问题

### 1. 如果按钮没有出现在我预期的位置怎么办？

* Word 使用的是点（point），而不是像素。请将屏幕像素转换为点（`points = pixels * 72 / DPI`）。  
* 确保矩形不与页面边距相交；否则 Word 可能会移动控件。

### 2. 能否将按钮插入到已有文档中？

可以。使用 `new Document("Existing.docx")` 加载文档，然后使用相同的 `DocumentBuilder` 流程。只需在调用 `InsertForms2OleControl` 之前移动构建器光标（例如 `builder.MoveToDocumentEnd()`、`builder.MoveToBookmark("myBookmark")` 等）。

### 3. 如何为按钮附加宏？

Aspose.Words 本身不生成 VBA 代码，但您可以在文档生成后嵌入宏：

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. 在 Linux 上的 .NET Core 能否使用此功能？

OLE 控件是 Windows 特有的功能，因为它依赖 COM。在 Linux 上仍会插入按钮，但会以静态图片形式显示，无法交互。若需跨平台交互式表单，建议使用内容控件（`StructuredDocumentTag`）代替。

### 5. 如果需要不同尺寸或多个按钮怎么办？

创建具有不同坐标的 `Rectangle` 对象并重复调用 `InsertForms2OleControl`。每个按钮都可以拥有独立的 `Caption` 和 `Name`。

## 完整工作示例

下面是可直接复制到控制台应用程序中的完整程序示例，包含所有必要的 `using` 指令、错误处理和注释。

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

运行程序，打开生成的 `CommandButton.docx`，即可看到已准备好的 **Click Me** 按钮，供后续自定义使用。

## 结论

现在，您已经掌握了使用 C# 和 Aspose.Words **插入 OLE 命令按钮** 到 Word 文档的完整方法。本教程涵盖了：

* 安装 Aspose.Words 包  
* 使用 `DocumentBuilder.InsertForms2OleControl` 与 `OleControlType.CommandButton`  
* 设置按钮属性（`Caption`、`Name`）  
* 保存并验证输出  

接下来，您可以进一步探索 **Aspose.Words OLE 控件** 用于复选框、下拉框，或嵌入整个 Excel 工作表的相关主题。也可以在更大的模板中尝试 **Word OLE 命令按钮** 自动化，或将 OLE 控件替换为现代 **内容控件** 以获得更好的跨平台支持。

欢迎根据实际需求调整矩形数值、添加多个按钮或附加 VBA 宏。祝编码愉快！

## 接下来您可以学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中实现替代方案。

- [Insert Ole Object In Word Document](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Insert Ole Object In Word Document As Icon](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Insert Ole Object In Word With Ole Package](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}