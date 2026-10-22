---
category: general
date: 2026-07-19
description: 使用 Aspose.Words C# 创建 Word 文档，并学习如何添加 ActiveX 命令按钮、设置按钮大小以及以编程方式插入按钮。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: zh
lastmod: 2026-07-19
og_description: 使用 Aspose.Words C# 创建 Word 文档，并在几秒钟内嵌入 ActiveX 命令按钮。按照分步指南轻松设置按钮大小并插入按钮。
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: 使用 ActiveX 按钮创建 Word 文档 – C# 教程
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: 使用 ActiveX 按钮创建 Word 文档 – C# 指南
url: /zh/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建带 ActiveX 按钮的 Word 文档 – 完整 C# 指南

是否曾想过如何 **create word document** 并在其中包含一个可工作的 ActiveX 按钮？也许你正在自动生成报告，需要在文件内部放置一个可点击的 “Approve” 控件。在本教程中，我们将一步步演示——使用 Aspose.Words for .NET 添加 ActiveX 命令按钮、设置其大小，并将其插入到所需位置。

如果你曾经自问 *how to add activex* 控件而不想手动打开 Word，那么你来对地方了。结束时，你将拥有一个可运行的示例、每一步的清晰解释以及处理常见陷阱的技巧。

## 你将学到的内容

- 如何在 C# 项目中设置 Aspose.Words  
- **create word document** 并嵌入 ActiveX 命令按钮的完整代码  
- **set button size** 的方法以及如何自定义按钮的标题和名称  
- 正确的 **insert command button** 方法以及 **how to insert button** 到文档任意位置的技巧  
- 边缘案例考虑（Word 版本、平台限制、安全警告）

### 前置条件

- .NET 6.0 或更高（代码同样适用于 .NET Framework 4.7+）。  
- 有效的 Aspose.Words for .NET 许可证（或免费评估密钥）。  
- Visual Studio 2022（或任何你喜欢的 IDE）。  
- 基本的 C# 与面向对象编程知识。

不需要其他第三方库。

---

## 第 1 步：创建 Word 文档 – 项目设置

在我们能够 **insert command button** 之前，需要先准备一个空的 Word 文件。本步骤还展示了使用 Aspose.Words 的经典 “create word document” 模式。

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why this matters:** `Document` 代表整个 .docx 文件，而 `DocumentBuilder` 负责跟踪当前光标位置。所有后续的插入（包括我们的 ActiveX 控件）都相对于该 builder 进行。

---

## 第 2 步：如何添加 ActiveX – 构建 CommandButton 控件

文档已创建，现在来解决 **how to add activex** 的部分。Aspose.Words 提供 `Forms2OleControl` 类来处理 ActiveX 对象。下面我们将创建一个命令按钮并配置其属性，包括 **set button size** 的需求。

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **Pro tip:** 大小以点为单位（1 point = 1/72 英寸）。根据布局调整数值；对于典型的工具栏按钮，120 × 30 的尺寸效果不错。

---

## 第 3 步：插入命令按钮 – **Insert Command Button** 的核心

控件准备就绪后，我们现在将 **insert command button** 插入到文档中 builder 当前所在的位置。你可以在调用此方法前将 builder 移动到任意位置（例如段落之后）。

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

如果需要在特定书签处 **how to insert button**，只需先移动 builder：

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **What happens behind the scenes?** Aspose.Words 会将必要的 OLE 对象流写入 .docx 包中，Word 能够在无需额外宏的情况下渲染该按钮。

---

## 第 4 步：保存文档 – 完成 **Create Word Document** 循环

最后一步非常直接：将文件持久化到磁盘。这完成了 **create word document**、嵌入 ActiveX 并保存的完整过程。

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

在 Microsoft Word（仅限 Windows）中打开生成的文件。你应该会看到一个标有 “Click Me” 的可点击按钮。点击后会触发 CommandButton 的默认动作——除非你附加 VBA 代码，否则不会有实际行为，但控件已完全可用。

> **Expected output:** 一个包含单页的 .docx 文件，按钮居中于插入点，尺寸为 120 × 30 pt，标题为 “Click Me”。  
> ![ActiveX button inserted into a Word document](placeholder-image.png)  
> *Image alt text:* **ActiveX button inserted into a Word document using C#** (matches `og_image_alt`).

---

## 第 5 步：边缘情况、安全性与最佳实践

### 平台限制
- ActiveX 控件仅在 Windows 版 Word 中运行。如果你的受众包括 macOS 或 Word Online 用户，按钮将显示为静态图片。  
- 某些企业环境出于安全考虑会禁用 ActiveX；此时可能需要对文档进行签名或提醒用户启用内容。

### VBA 交互（可选）
如果希望按钮执行宏，需要在保存后向文档添加 VBA 项目。Aspose.Words 不会自动生成 VBA 代码，但你可以使用 `Document.VbaProject` API 将其注入。

### 命名冲突
务必为每个控件分配唯一的 `Name`。重复使用相同名称会导致 Word 在解析控件时出现运行时错误。

### 性能提示
插入大量控件时，复用同一个 `DocumentBuilder` 实例并避免在循环中调用 `doc.Save`。一次性批量插入后再统一保存。

---

## 完整工作示例

将所有内容整合在一起，下面是一个完整的、可直接复制粘贴的程序：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

运行程序，打开保存的文件，你将看到按钮正好位于 builder 所在的位置。

---

## 结论

我们已经 **created word document** 从零开始，学习了通过配置 `Forms2OleControl` 来 **how to add activex**，掌握了 **set button size** 属性，并演示了正确的 **insert command button** 与 **how to insert button** 在文件任意位置的使用方式。

通过这段代码示例，你现在拥有了构建更丰富 Word 自动化的坚实基础——无论是创建带交互表单的模板、生成需要用户确认的合同，还是在报告中随意添加几个实用控件。

### 接下来可以做什么？

- **Style the button** – 更改字体、颜色或添加图片背景。  
- **Attach VBA macros** – 让按钮执行计算或启动外部程序。  
- **Combine with other controls** – 复选框、列表框，甚至嵌入的 Excel 工作表。  

尽情尝试吧，如果遇到问题，欢迎在下方留言。祝编码愉快，享受使用 Aspose.Words 自动化 Word 的过程！

## 接下来应该学习什么？

以下教程与本指南的技术紧密相关，帮助你进一步掌握 API 功能并探索在项目中的其他实现方式。

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}