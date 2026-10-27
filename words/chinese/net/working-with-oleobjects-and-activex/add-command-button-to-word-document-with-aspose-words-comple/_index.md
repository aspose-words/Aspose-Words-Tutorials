---
category: general
date: 2026-07-29
description: 使用 Aspose.Words 向 Word 文档添加命令按钮。了解如何设置 ActiveX 控件属性以及在几步简单操作中设置命令按钮的标题。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: zh
lastmod: 2026-07-29
og_description: 使用 Aspose.Words 向 Word 文档添加命令按钮。本教程快速演示如何设置 ActiveX 控件属性以及设置命令按钮的标题。
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: 向 Word 文档添加命令按钮 – Aspose.Words 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: 使用 Aspose.Words 向 Word 文档添加命令按钮 – 完整指南
url: /zh/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 向 Word 文档添加命令按钮 – 完整编程演练

是否曾需要 **向 Word 文档添加命令按钮**，却不确定该使用哪些 API 调用？你并不孤单；许多开发者在首次尝试在 DOCX 文件中嵌入交互控件时都会遇到这个难题。好消息是 Aspose.Words 让这一步骤出奇地简单。在本指南中，我们将逐步演示如何创建 CommandButton ActiveX 控件、**设置 ActiveX 控件属性**，以及**设置命令按钮标题**——全部使用可以直接复制粘贴的 C# 代码。

阅读完本教程后，你将拥有一个功能完整的 Word 文件，其中包含一个可点击的 “Submit” 按钮，能够直接在 Microsoft Word 中打开。无需外部 VBA 脚本，也不需要手动 UI 调整——纯粹的代码控制。

## 你将学到

* 如何创建空白 Word 文档并获取 `DocumentBuilder`。
* 使用 Aspose.Words **向 Word 文档添加命令按钮** 的确切方法调用。
* 如何 **设置 ActiveX 控件属性**，例如大小、位置和名称。
* 正确的 **设置命令按钮标题** 技巧，使按钮显示你想要的文字。
* 处理不同按钮类型、DPI 缩放以及 Word 版本兼容性的实用提示。

> **先决条件：** 已安装 Aspose.Words for .NET（NuGet 包 `Aspose.Words`）的 Visual Studio（或任意 C# IDE）。不需要事先了解 ActiveX。

---

## 第 1 步：设置项目并导入命名空间

在 **向 Word 文档添加命令按钮** 之前，需要一个引用 Aspose.Words 的 C# 项目。创建一个新的 .NET 控制台应用程序，然后添加 NuGet 包：

```bash
dotnet add package Aspose.Words
```

接下来在源码文件中引入所需的命名空间：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

这三个 `using` 指令让你能够访问 `Document`、`DocumentBuilder` 和 `Forms2OleControl` 类，从而实现 ActiveX 插入。

*小技巧：* 如果使用 Visual Studio，IDE 会在你键入类名时自动提示添加这些引用。

---

## 第 2 步：创建空白文档和 Builder

一个全新的 `Document` 对象代表一个空的 Word 文件。`DocumentBuilder` 则是我们的“笔”，可以绘制、插入文本，且关键是能够放置 ActiveX 控件。

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

此时文档仅是一个空白画布——想象成一张等待你的命令按钮的白纸。

---

## 第 3 步：插入 CommandButton ActiveX 控件

现在我们终于 **向 Word 文档添加命令按钮**。Aspose.Words 提供 `InsertForms2OleControl` 方法，接受控件类型和尺寸。我们使用 `Forms2OleControlType.CommandButton`，并设定宽度 150 点、高度 30 点的舒适尺寸。

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

该方法返回一个 `Forms2OleControl` 实例，接下来我们将在此基础上 **设置 ActiveX 控件属性**。

---

## 第 4 步：配置控件 – 名称、标题和位置

### 设置标题

标题是显示在按钮上的文字。要 **设置命令按钮标题**，只需给 `Caption` 属性赋值即可：

```csharp
commandButton.Caption = "Submit";
```

你可以将 `"Submit"` 换成任意文字——“保存”、 “导出”、 “启动”等，Word 会显示对应的文本。

### 为控件命名

为控件指定有意义的名称，便于后续引用（例如在自动化 Word 宏时）。我们设置 `Name` 属性：

```csharp
commandButton.Name = "btnSubmit";
```

### 页面定位

Word 使用点（1/72 英寸）进行布局。通过调整 `Left` 和 `Top` 属性即可将按钮放置在所需位置：

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

如果需要相对于段落对齐按钮，可以先移动 Builder 的光标，再插入控件；坐标将相对于该位置。

*边缘情况：* 在高 DPI 显示器上，Word 中的视觉大小可能略有差异。为保持按钮在不同设备上的实际尺寸一致，可根据目标 DPI（Word 通常为 96 DPI）计算点数。

---

## 第 5 步：保存文档

按钮配置完成后，保存文件只需一行代码：

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

生成的 `CommandButton.docx` 包含一个功能完整的 ActiveX 按钮。用 Microsoft Word 打开它，你会看到一个位于指定坐标的 “Submit” 按钮。

### 预期结果

1. Word 文档打开后只有一页。
2. 在你指定的坐标出现一个标有 **Submit** 的矩形按钮。
3. 右键点击按钮并选择 **Properties**，即可看到名称 `btnSubmit` 以及你设置的其他属性。

---

## 第 6 步：高级变体与常见陷阱

### 插入其他 ActiveX 类型

`InsertForms2OleControl` 方法并不限于命令按钮。你可以嵌入复选框、单选按钮，甚至自定义 ActiveX 对象：

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

同样的 **设置 ActiveX 控件属性** 方式适用，只需更换枚举类型即可。

### 兼容不同 Word 版本

旧版 Word（2007 之前）使用二进制 `.doc` 格式，ActiveX 控件的存储方式不同。Aspose.Words 在保存为 `.doc` 时会自动转换控件，但某些属性（如精确定位）可能会出现偏移。如果面向旧版格式，请在对应的 Word 版本中进行测试。

### 安全设置

在安全策略严格的机器上，Word 可能会禁用 ActiveX 控件。为避免出现 “Security Warning” 对话框，可考虑：

* 使用受信任的证书对文档签名。
* 指导用户在该文件所在位置启用 ActiveX 内容。
* 若安全性是主要顾虑，可改用无宏的替代方案（例如普通内容控件）。

---

## 第 7 步：完整可运行示例

下面是完整的、可直接运行的程序示例，囊括了前面讨论的所有步骤。将其复制到 `Program.cs`，如有需要调整输出路径，然后点击 **Run**。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**代码功能概述：**

* 从空白文档开始。
* 插入命令按钮，**设置 ActiveX 控件属性**，并 **设置命令按钮标题**。
* 添加一段简短说明文字。
* 将文件保存为 `CommandButton.docx`。

运行程序，打开生成的文件，你会看到按钮位于说明文字下方。

---

## 结论

我们已经演示了如何使用 Aspose.Words **向 Word 文档添加命令按钮**、**设置 ActiveX 控件属性**，以及 **设置命令按钮标题**——全部通过简洁、可投入生产的 C# 代码实现。该方法具备可扩展性：只需更换控件类型、调整尺寸，或在数据源上循环，即可自动嵌入大量按钮。

想进一步探索？可以尝试：

* 将按钮绑定到触发数据导出的宏。
* 使用 `Picture` 属性在按钮内部添加图像或自定义图标。
* 构建包含多个 ActiveX 控件（文本框、下拉框等）的完整表单。

动手实验是掌握 Word 自动化的最佳途径。如果遇到问题，请检查 DPI 计算和 Word 安全设置。祝编码愉快，愿你的文档更加交互丰富！

## 接下来你应该学习什么？

以下教程与本指南紧密相关，帮助你进一步掌握 API 功能并探索在项目中的替代实现方式，每篇都附有完整可运行的代码示例和逐步解释。

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}