---
category: general
date: 2026-08-04
description: 使用 Aspose.Words 创建空白 Word 文档并插入命令按钮。学习在 C# 中设置按钮大小并添加可点击的按钮。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: zh
lastmod: 2026-08-04
og_description: 使用 Aspose.Words 创建空白 Word 文档并插入命令按钮。本指南展示如何设置按钮大小、添加可点击按钮以及保存文件。
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: 创建空白 Word 文档并添加命令按钮 – 完整 C# 教程
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 使用命令按钮创建空白 Word 文档——逐步指南
url: /zh/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用命令按钮创建空白 Word 文档 – 分步指南

如果您需要 **创建空白 Word 文档** 并在其中包含交互式按钮，本教程将向您展示如何使用 Aspose.Words for .NET 完成此操作。您将学习 **插入命令按钮**、调整其外观以及使其可点击——只需几行 C# 代码。

本指南涵盖从项目设置到保存最终文件的全部步骤，您可以将完整的解决方案直接复制粘贴到自己的应用程序中。过程中我们还会解释如何 **添加可点击按钮**、**设置按钮大小**，以及以编程方式 **创建命令按钮**。

## 前置条件

在开始之前，请确保您拥有：

* 已安装 .NET 6.0 SDK 或更高版本。
* Visual Studio 2022（或任何支持 .NET 的 IDE）。
* Aspose.Words for .NET NuGet 包（`Aspose.Words` 版本 23.12 或更新）。
* 对 C# 和面向对象编程的基本了解。

不需要额外的 Office 互操作程序集，因为 Aspose.Words 完全独立于 Microsoft Word 工作。

## 第 1 步：设置 .NET 项目

创建一个控制台应用程序来承载 Word 自动化代码。

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

此命令会创建一个名为 `WordButtonDemo` 的新文件夹，其中包含可直接运行的 `Program.cs`，并添加 Aspose.Words 库。

## 第 2 步：创建空白 Word 文档

首个操作是 **创建空白 Word 文档**。Aspose.Words 提供的 `Document` 类可以直接表示一个空的 Word 文件。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

创建空白文档后，您将拥有一个干净的画布，可在其上添加段落、表格，或在本例中添加 OLE 命令按钮。

## 第 3 步：初始化 DocumentBuilder

`DocumentBuilder` 是用于向文档插入内容的辅助类。您需要将其绑定到刚才创建的文档。

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

构建器会维护当前光标位置，后续的任何插入操作都会恰好发生在您希望的位置。

## 第 4 步：插入命令按钮

现在我们 **插入命令按钮**（一个 OLE `Forms2OleControl`）到文档中。`InsertForms2OleControl` 方法需要三个参数：

1. OLE 控件的 ProgID —— 标准按钮使用 `"CommandButton"`。
2. 定义 **设置按钮大小** 与位置的 `Rectangle`。
3. 按钮上显示的标题文字。

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

当文档在 Word 中打开时，按钮的行为与任何本地表单控件相同——您可以点击它，Word 将触发关联的宏（如果存在）。这满足了 **添加可点击按钮** 的需求。

### 为什么使用 Forms2OleControl？

`Forms2OleControl` 将 OLE 对象直接嵌入 DOCX 文件，保留控件属性而无需 Word Interop 程序集。这是实现 **创建命令按钮**、在各版本 Word 中均能可靠工作的最佳方式。

## 第 5 步：自定义按钮（可选）

您可能希望更精确地 **设置按钮大小**，或修改字体、背景颜色等其他属性。Aspose.Words 公开底层 OLE 对象，允许进一步微调。

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

如果需要不同的尺寸，只需在第 4 步的 `Rectangle` 中调整数值。坐标单位为点（1 pt = 1/72 英寸），因此 `120` 大约等于 1.67 英寸宽。

## 第 6 步：保存文档

最后，将文档写入磁盘。生成的文件即为包含完整功能命令按钮的 **空白 Word 文档**。

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

在 Microsoft Word 中打开 `CommandButtonDemo.docx` 时，您会看到一个标有 “Click Me” 的按钮。点击该按钮将显示默认宏对话框，除非您自行附加了自定义宏。

## 完整源代码

下面是可以直接复制到 `Program.cs` 的完整程序。它包含上述所有步骤，且无需任何修改即可编译运行。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### 预期结果

运行程序后会生成 `CommandButtonDemo.docx`。在 Word 中打开该文件会看到：

* 单页上有一个标记为 **Click Me** 的按钮。
* 按钮遵循 **设置按钮大小**（120 × 30 点）的设定。
* 点击按钮会触发 Word 的默认命令按钮行为，证明 **添加可点击按钮** 操作已成功。

## 常见问题与边缘情况

| 问题 | 答案 |
|----------|--------|
| **这能在 .doc 文件中使用吗？** | 可以。将 `doc.Save("file.doc")` 中的文件扩展名改为 `.doc` 即可。OLE 控件同样会存储在旧的二进制格式中。 |
| **如果需要多个按钮怎么办？** | 多次调用 `InsertForms2OleControl`，并为每个新按钮调整 `Rectangle`，以避免重叠。 |
| **可以给按钮附加宏吗？** | 按钮本身不包含宏代码。您需要手动或通过 `Document` 对象的 `Modules` 集合向文档添加 VBA 宏。 |
| **按钮在导出为 PDF 时可见吗？** | 使用 Aspose.Words 将 DOCX 导出为 PDF 时，按钮会被渲染为静态图像，而非交互式控件。 |
| **支持哪些 Word 版本？** | OLE 命令按钮在 Word 2007 及更高版本均可工作，因为它遵循标准的 Forms2.0 规范。 |

## 结论

现在，您已经掌握了如何使用 Aspose.Words for .NET **创建空白 Word 文档**、**插入命令按钮**、**添加可点击按钮**以及**设置按钮大小**。完整示例演示了 **创建命令按钮** 的完整工作流，为您进一步开展高级 Word 自动化任务奠定了坚实基础。

## 后续步骤

* 通过更改 `InsertForms2OleControl` 中的 ProgID，探索其他 OLE 控件（如 `CheckBox`、`ListBox`）。
* 将按钮与 VBA 宏结合，在用户点击时执行自定义操作。
* 使用 Aspose.Words 的 `DocumentBuilder` 在插入按钮前添加表格、图片或脚注等额外内容。
* 试验不同的 **设置按钮大小** 值，以匹配文档的布局需求。

祝编码愉快，尽情构建带有交互控件的丰富 Word 文档！

## 接下来您应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中尝试替代实现方式。每篇资源都提供完整的可运行代码示例和逐步解释。

- [使用 Aspose.Words for .NET 在 Word 文档中创建组合形状](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words for .NET 创建带阴影矩形形状的空白 Word 文档 – 分步指南](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [使用 Aspose.Words for .NET 创建 Word 文档](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}