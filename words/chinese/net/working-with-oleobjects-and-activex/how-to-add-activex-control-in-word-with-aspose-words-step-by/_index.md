---
category: general
date: 2026-08-07
description: 学习如何使用 C# 在 Word 文档中添加 ActiveX 控件。包括将宏关联到按钮以及添加可点击按钮的 Word 示例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: zh
lastmod: 2026-08-07
og_description: 如何使用 Aspose.Words 在 Word 文档中添加 ActiveX 控件。请按照本指南插入按钮、将宏关联到按钮，并添加可点击的按钮文字。
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: 如何在 Word 中添加 ActiveX 控件 – 完整 C# 教程
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: 如何在 Word 中使用 Aspose.Words 添加 ActiveX 控件 – 步骤指南
url: /zh/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中使用 Aspose.Words 添加 ActiveX 控件

如果您需要 **如何添加 ActiveX 控件** 在 Microsoft Word 文件中以编程方式实现，本教程将展示使用 Aspose.Words for .NET 的完整步骤。您将看到如何插入命令按钮、设置其标题，以及 **将宏关联到按钮**，使控件在用户点击时作出响应。完成后，您将拥有一个宏启用的 `.docm` 文件，其中包含一个功能完整的按钮。

在构建交互式模板（如贷款申请、员工入职表单或自动化报告）时，添加 ActiveX 按钮是常见需求。本指南逐行讲解代码，说明 **为什么** 每一步都很重要，并覆盖可能遇到的典型陷阱。

## 前提条件

在开始之前，请确保您具备：

* 已安装 .NET 6（或 .NET Core 3.1 / .NET Framework 4.8）。
* 有效的 Aspose.Words for .NET 许可证或临时评估密钥。
* Visual Studio 2022（或任何支持 C# 的 IDE）。
* 对 Word 宏（VBA）有基本了解（如果您计划编写按钮触发的宏）。

> **专业提示：** 运行示例时，请将输出保存到您拥有写入权限的文件夹，否则 `doc.Save` 将抛出异常。

## 使用 Aspose.Words 在 Word 文档中添加 ActiveX 控件的方法

解决方案的核心是一个简短的 C# 程序，它创建新文档、插入 ActiveX **CommandButton** 控件，并将文件保存为宏启用文档（`.docm`）。代码完整，可直接复制粘贴使用。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### 为什么每行代码都很重要

| 行 | 目的 |
|------|---------|
| `Document doc = new Document();` | 在内存中实例化一个全新的 Word 包。 |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | 提供流式 API 用于插入内容，包括 ActiveX 控件。 |
| `InsertForms2OleControl` | 唯一的 Aspose.Words 方法用于创建 ActiveX 控件；您需要指定控件类型（`CommandButton`）及其几何尺寸。 |
| `commandButton.Caption = "Click Me";` | 设置 **添加可点击按钮文字**，即最终用户看到的标签。若未设置标题，按钮将显示为空白。 |
| `commandButton.OnAction = "MyMacro";` | **将宏关联到按钮** —— 告诉 Word 在点击控件时运行哪个 VBA 宏。 |
| `doc.Save("CommandButton.docm");` | 将文档持久化为宏启用文件；普通的 `.docx` 会剥离控件和宏。 |

> **注意：** 坐标（左、上）以点为单位（1 pt ≈ 1/72 in）。根据需要调整，以将按钮放置在页面的合适位置。

## 如何将宏关联到按钮

`OnAction` 属性将按钮链接到名为 `MyMacro` 的 VBA 宏。您仍需在 Word 文件中创建该宏，可以手动完成，也可以通过编程方式注入 VBA 代码（Aspose.Words 不会写入 VBA 代码）。以下是可通过 Word 的 **Developer → Visual Basic** 编辑器添加的最小宏示例：

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

当用户打开 `CommandButton.docm` 并点击按钮时，Word 将执行 `MyMacro` 并显示消息框。如果宏安全性设置为 **Disable all macros without notification**，按钮将显示为禁用状态。建议用户为该文档启用宏，或使用受信任的证书对宏进行签名。

### 关联宏时的常见陷阱

* **宏安全设置** – 若文档在安全策略严格的机器上打开，宏可能被阻止。提供降低安全级别或签名宏的说明。
* **命名冲突** – 宏名称必须在文档的 VBA 项目中唯一，否则 Word 会抛出 “duplicate procedure name” 错误。
* **64‑bit 与 32‑bit Word** – ActiveX 控件工作方式相同，但 VBA 编辑器可能根据 Office 版本显示不同的警告信息。

## 向 Word 表单添加可点击按钮文字

`Caption` 属性决定用户在按钮上看到的文字。您可以进一步自定义：

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

如果需要根据用户输入动态更改标题，稍后可以通过 Word 对象模型访问该控件：

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### 边缘情况：长标题

Word 会截断超出按钮宽度的标题。为避免裁剪，可在 `InsertForms2OleControl` 中增大宽度参数，或缩短文本。建议使用不同语言（如德语或日语）进行测试，因为字符宽度会有所差异。

## 为表单自动化添加命令按钮文字

除了可视标题外，**添加命令按钮文字** 概念还涵盖控件的编程名称。Aspose.Words 未公开 ActiveX 控件的直接 `Name` 属性，但您可以设置 `AltText` 字段，Word 会将其视为控件的标识符：

```csharp
commandButton.AltText = "SubmitButton";
```

随后在 VBA 中，您可以通过其 `AltText` 值引用该按钮：

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

当您拥有多个按钮并需要在代码中区分它们时，此技巧非常有用。

## 完整工作示例

下面是完整的程序，您可以将其编译并作为控制台应用运行。示例包含可选样式、宏关联以及描述每一步的注释块。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**预期结果：** 在 Microsoft Word 中打开 `SubmitForm.docm` 时，会显示一个蓝色边框、标签为 *Submit Form* 的按钮。点击该按钮会触发 VBA 宏 `SubmitMacro`（前提是您已将宏添加到文档中）。该按钮可使用相同的 `Forms2OleControl` 对象进一步移动、调整大小或更改样式。

## 测试解决方案

1. 构建并运行 C# 控制台应用。
2. 在 Word 中打开生成的 `SubmitForm.docm`。
3. 如有提示，启用宏。
4. 点击 *Submit Form* 按钮 – 您应看到 `SubmitMacro` 中定义的消息框。

如果按钮出现但没有响应，请再次确认宏名称完全匹配（`SubmitMacro`），并确保宏安全设置未阻止执行。

## 常见问题

| 问题 | 答案 |
|----------|--------|
| *我可以添加多个 ActiveX 按钮吗？* | 可以。多次调用 `InsertForms2OleControl` 并使用不同坐标。使用不同的 `OnAction` 和 `AltText` 值来区分它们。 |
| *ActiveX 控件在 Word Online 中可见吗？* | 不可。 |

## 接下来应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并探索在项目中的替代实现方式。

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Add a New Section to Word Document | Aspose.Words for .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}