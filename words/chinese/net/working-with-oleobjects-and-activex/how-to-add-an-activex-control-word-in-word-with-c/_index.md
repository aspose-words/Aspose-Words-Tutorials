---
category: general
date: 2026-09-30
description: 使用 C# 向 Word 文档添加 ActiveX 控件。学习如何插入 ActiveX 按钮、添加命令按钮并使其可点击。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: zh
lastmod: 2026-09-30
og_description: 使用 C# 向 Word 文档添加 ActiveX 控件。请按照本完整指南插入 ActiveX 按钮、添加命令按钮，并使其可点击。
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: 向 Word 文档添加 ActiveX 控件 – 步骤详解 C# 指南
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: 如何使用 C# 在 Word 中添加 ActiveX 控件
url: /zh/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 C# 在 Word 中添加 ActiveX 控件词

如果您需要在 Microsoft Word 文件中嵌入 **ActiveX 控件词**，本指南将向您展示具体的操作步骤。您将看到一个完整的可运行示例，演示如何插入可点击按钮、保存文档，并使用最新的 Aspose.Words for .NET。

添加 ActiveX 控件词可以让您创建交互式表单、自定义对话框或类似原生 Word 控件的简单 UI 元素。无论是构建需要用户交互的合同模板，还是需要“运行”按钮的报告，下面的步骤都涵盖了您所需的全部内容。

## 前置条件

* .NET 6.0 SDK 或更高版本（代码同样适用于 .NET Framework 4.8）
* Visual Studio 2022（或任何支持 C# 的 IDE）
* 已安装 Aspose.Words for .NET（`dotnet add package Aspose.Words`）
* 对 C# 和 Word 文档结构有基本了解

> **专业提示：** `InsertForms2OleControl` 方法仅适用于传统的 “Forms 2.0” 控件，这些是 Word 用于表单字段的 ActiveX 控件。如果您针对更新的 Office 版本，该控件在桌面客户端仍能正确渲染。

## 步骤 1：设置项目并导入命名空间

创建一个新的控制台项目并添加所需的 `using` 语句。这样可以确保编译器能够找到 `Document`、`DocumentBuilder` 和 `OleControlType` 类。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

`Aspose.Words` 命名空间提供用于 Word 处理的高级 API，而 `Aspose.Words.Drawing` 包含用于指定 ActiveX 控件类型的 `OleControlType` 枚举。

## 步骤 2：加载源 Word 文档

您必须以要修改的 Word 文件为起点。以下代码从您指定的文件夹加载 `input.docx`。

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

如果文件不存在，Aspose.Words 会抛出 `FileNotFoundException`。如果需要优雅的错误处理，请将调用包装在 `try/catch` 块中。

## 步骤 3：创建 DocumentBuilder 以编辑文档

`DocumentBuilder` 是用于插入文本、图像和控件的核心工具。它维护一个光标，指向下一个元素将要放置的位置。

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

默认情况下，构建器的光标位于第一个节的开头。如果您希望按钮出现在其他位置，可以使用 `MoveToDocumentEnd()` 或 `MoveToParagraph(index)` 等方法移动光标。

## 步骤 4：插入 ActiveX CommandButton 控件

现在进入教程的核心：插入一个显示为可点击按钮的 **ActiveX 控件词**。`InsertForms2OleControl` 方法接受两个参数——控件类型和控件的标题（或名称）。

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **为什么使用 `OleControlType.CommandButton`？**  
  它告诉 Word 创建一个经典的 Forms 2.0 命令按钮，该按钮显示标题，并且以后可以连接到宏或 VBA 脚本。

* **标题有什么作用？**  
  字符串 `"ClickMe"` 成为按钮的可见文字。您可以将其更改为任何适合您 UI 的内容。

### 在特定位置插入按钮

如果您需要在特定段落之后插入按钮，请先移动构建器：

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## 步骤 5：保存修改后的文档

插入控件后，将更改持久化到新文件（或覆盖原文件）。

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

当您在桌面版 Word 中打开 `output.docx` 时，会看到标有 **ClickMe**（或 **Submit**，取决于您使用的标题）的按钮。默认情况下，在设计模式下点击按钮不会有任何操作；您可以稍后通过 Word 的 “Developer” 选项卡为其分配宏。

## 完整、可运行的示例

下面是一个独立的程序，演示完整的工作流。将其复制到新控制台应用的 `Program.cs` 中并运行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### 预期输出

* 控制台打印包含输出路径的成功信息。
* 打开 `output.docx` 时，会在构建器插入的位置显示一个 **ClickMe** 按钮。
* 可以选中、调整大小，或通过 Word 的 **Developer → Design Mode** 为按钮分配宏。

## 常见问题与边缘情况处理

| 问题 | 答案 |
|----------|--------|
| **如何在页眉/页脚中插入 ActiveX 按钮？** | 在调用 `InsertForms2OleControl` 之前，使用 `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` 将构建器移动到页眉/页脚。 |
| **如果需要复选框而不是按钮怎么办？** | 使用 `OleControlType.CheckBox` 并提供类似 `"Agree"` 的标题。 |
| **按钮在 Word Online 中能工作吗？** | 不能。Word Online 不支持传统的 Forms 2.0 ActiveX 控件。该按钮仅在桌面客户端渲染。 |
| **可以通过代码设置按钮的大小吗？** | 插入后，可通过 `builder.CurrentParagraph.Runs[0].GetShape()` 获取 `Shape` 对象并调整 `Width`/`Height`。 |
| **有没有办法从代码分配宏？** | Aspose.Words 不提供宏编辑功能。您必须在 Word 中手动附加宏，或使用 Office Interop API。 |

## 生产环境使用提示

* **避免硬编码路径** —— 使用 `Path.Combine` 并结合配置文件。
* **释放 `Document`** —— 如果处理大文件，请将其放在 `using` 语句块中，以便及时释放内存。
* **验证输出** —— 通过遍历 `doc.GetChildNodes(NodeType.Shape, true)`，在程序中检查文档是否包含 `OleControl` 类型的形状。
* **安全提示** —— ActiveX 控件可能在客户端机器上运行代码。仅向受信任的用户分发文档，并考虑使用数字签名。

## 结论

现在，您已经了解如何使用 C# 向 Word 文档添加 **ActiveX 控件词**。通过加载文档、创建 `DocumentBuilder`、使用 `InsertForms2OleControl` 插入命令按钮并保存文件，您可以实现交互式 Word 表单的自动化创建。尝试其他 `OleControlType` 值，将控件放置在页眉或表格中，并结合宏以获得更丰富的用户体验。

---

*下一步*：探索 **如何插入其他类型的 ActiveX** 控件，学习 **如何通过 VBA 添加命令按钮** 事件处理程序，并阅读关于 **插入 ActiveX 按钮** 的跨平台兼容性最佳实践。

## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步学习。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [Embedding OLE Objects and ActiveX Controls in Word Documents](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}