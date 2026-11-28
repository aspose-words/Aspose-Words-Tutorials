---
category: general
date: 2026-11-18
description: 使用 C# 创建一个空白 Word 文档并插入 ActiveX 按钮。学习如何添加控件、设置按钮标题以及保存文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: zh
lastmod: 2026-11-18
og_description: 使用 C# 创建一个空白的 Word 文档并插入 ActiveX 按钮。按照本完整教程添加控件、设置按钮标题并保存结果。
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: 创建空白 Word 文档并插入 ActiveX 按钮——逐步指南
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: 创建空白 Word 文档并插入 ActiveX 按钮
url: /zh/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建一个空白 Word 文档并插入 ActiveX 按钮

如果您需要 **创建一个空白 Word 文档** 并在其中放置交互式 ActiveX 按钮，本指南将向您展示如何使用 Aspose.Words for .NET 完成此操作。您将看到完整代码，了解每行代码为何重要，并学习如何 **设置按钮标题** 使控件看起来已准备好供用户交互。

除了主要目标外，我们还将介绍 **如何插入 ActiveX**、**如何向 Word 文件添加控件** 的步骤，以及带有自定义标题的 **插入 ActiveX 按钮** 的细节。完成后，您将拥有一个可重复使用的模式，适用于任何需要嵌入 UI 元素的文档自动化场景。

## 您将学习

* 如何以编程方式 **创建一个空白 Word 文档**。  
* 插入 **ActiveX 按钮** 并配置其属性所需的确切 API 调用。  
* 如何 **设置按钮标题** 使控件显示所需的文本。  
* 关于将文件保存到您选择的位置以及处理常见陷阱的提示。

### 前提条件

* .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.6+）。  
* 已安装 Aspose.Words for .NET（`Install-Package Aspose.Words`）。  
* 具备 C# 和 Visual Studio 或任何 .NET 兼容 IDE 的基本熟悉度。

---

## 使用 Aspose.Words 创建空白 Word 文档

第一步是实例化一个空的 `Document` 对象。该对象表示一个 Word 文件，直到我们添加内容之前，它不包含任何内容。

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*为什么这很重要*：空的 `Document` 为您提供了一个干净的画布。您以后可以添加段落、表格或控件，而无需担心已有的格式。

---

## 初始化 DocumentBuilder 以操作文档

`DocumentBuilder` 是一个帮助类，允许您在当前光标位置插入内容。它会自动跟踪您在文档中的位置。

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*为什么这很重要*：如果没有 `DocumentBuilder`，您需要手动操作低层节点树。该构建器简化了文本、图像和 ActiveX 控件的插入。

---

## 如何插入 ActiveX 按钮（insert activex button）

现在我们使用 `InsertForms2OleControl` 来嵌入 ActiveX 控件。该方法需要三个参数：

1. 控件的类型（`OleControlType.CommandButton`）。  
2. 控件的内部名称（供 VBA 或宏代码使用）。  
3. 一个定义页面上位置和大小的 `RectangleF`。

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*为什么这很重要*：这是 **如何插入 activex** 到 Word 文档的核心。矩形的坐标以点为单位（1 点 = 1/72 英寸）。根据需要调整它们以定位按钮。

### 提示

如果您需要按钮出现在特定页面，请先移动 builder 的光标：

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## 如何设置按钮标题（set button caption）

控件放置后，您可以修改其属性。最显眼的属性是 `Caption`，它决定按钮上显示的文字。

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*为什么这很重要*：用户看到的是标题，而不是内部名称。更改它使按钮在最终文档中具有意义。

---

## 保存包含按钮的文档

最后，将文档写入磁盘。您可以选择任何受支持的格式（`.docx`、`.pdf` 等）。这里我们保存为 Word 文档。

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*为什么这很重要*：持久化文件后，您可以在 Microsoft Word 中打开并测试按钮。打开文档时，按钮将显示标题 “Press”。

### 预期结果

在 Word 中打开 `with_button.docx` 会显示一个空白页，页面上有一个标有 **Press** 的矩形按钮。默认情况下点击按钮不会有任何动作，因为未附加 VBA 宏，但该控件是完全可用的，稍后可以连接到代码。

---

## 如何向特定段落添加控件（how to add control）

有时您希望按钮位于特定段落中，例如在一些说明文字之后。使用 `MoveTo` 将 builder 定位到插入控件之前的位置。

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*为什么这很重要*：此模式演示了 **how to add control** 的上下文使用，确保文档布局保持逻辑。

---

## 常见陷阱及避免方法

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| 按钮显示在页面之外 | 矩形坐标超出页面边距 | 使用 `builder.PageSetup` 获取页面尺寸并计算安全的 `RectangleF`。 |
| 标题未显示 | `Caption` 在控件完全初始化之前设置 | 在 `InsertForms2OleControl` 调用之后 **设置** `Caption`，如第 4 步所示。 |
| 文档保存时没有按钮 | 插入后 Builder 的光标被移动且未提交更改 | 保持 Builder 在同一页面，或在保存前调用 `builder.Document.UpdatePageLayout()`。 |

---

## 完整、可运行的示例

下面是完整的程序，您可以复制、粘贴并运行。它创建一个空白 Word 文件，插入 ActiveX 按钮，设置其标题，并保存结果。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**输出**：运行程序后，在 Microsoft Word 中打开 `C:\Temp\with_button.docx`。您将看到一页，显示文本 “Below is an ActiveX button created programmatically:” 并随后出现一个标有 **Press** 的按钮。

---

## 结论

您现在已经了解如何使用 Aspose.Words for .NET **创建空白 Word 文档**、**插入 ActiveX 按钮**、**设置按钮标题**，以及 **保存** 结果。通过更改 `OleControlType`，相同的模式可以扩展到其他 ActiveX 控件（复选框、列表框等）。  

接下来，您可以探索使用 VBA 的 **how to insert ActiveX button** 事件，或将 **how to add control** 添加到已经包含内容的现有文档。这两个主题都直接基于此处介绍的概念。

祝编码愉快，随意尝试不同的尺寸、位置和标题，以满足您应用程序的 UI 需求！

## 接下来您应该学习什么？

以下教程涵盖与本指南技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在自己的项目中探索替代实现方法。

- [如何使用 C# 创建带有 ActiveX 命令按钮的 Word 文档](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [如何在 Word 文档中使用 Aspose.Words 添加 ActiveX 按钮](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}