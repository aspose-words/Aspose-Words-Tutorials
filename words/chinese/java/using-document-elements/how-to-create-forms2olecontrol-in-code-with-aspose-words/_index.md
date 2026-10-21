---
category: general
date: 2026-09-11
description: 学习如何使用 Aspose.Words DocumentBuilder 在代码中创建 forms2olecontrol。本分步指南涵盖 ActiveX
  命令按钮的插入、setOleClassName 的使用以及尺寸设置。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: zh
lastmod: 2026-09-11
og_description: 使用 Aspose.Words 在代码中创建 forms2olecontrol。按照本指南插入 ActiveX 命令按钮，设置其类名并调整大小。
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: 在代码中创建 forms2olecontrol – 完整的 Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: 如何在代码中使用 Aspose.Words 创建 forms2olecontrol
url: /zh/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在代码中使用 Aspose.Words 创建 forms2olecontrol

如果您需要 **在代码中创建 forms2olecontrol**，本指南将向您展示如何使用 Aspose.Words .NET API 完成此操作。无论是自动化需要 ActiveX 命令按钮的模板，还是仅想以编程方式丰富 Word 文档，下面的步骤都涵盖了从插入控件到配置外观的全部内容。

在本教程中，您将学习如何使用 **Aspose.Words DocumentBuilder** 插入 **ActiveX 命令按钮**，使用 **setOleClassName 方法** 设置其类名，并调整 **Forms2OleControl 大小**。无需外部工具——只需一个 .NET 开发环境和 Aspose.Words 库。

## 前置条件

在开始之前，请确保您具备以下条件：

* 已安装 .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.7+）
* 最近版本的 Aspose.Words for .NET NuGet 包
* 对 C# 基础以及 Word 文档中 ActiveX 控件概念的基本了解

如果缺少上述任意项，请使用以下命令安装 NuGet 包：

```bash
dotnet add package Aspose.Words
```

## 本教程涵盖的内容

* 创建 `DocumentBuilder` 实例
* 插入 `Forms2OleControl`（ActiveX 命令按钮的底层对象）
* 使用 `setOleClassName` 赋予正确的类名
* 通过 **Forms2OleControl 大小** 属性设置可视宽度和高度
* 保存文档并验证结果

完成本指南后，您将拥有一个包含可点击按钮的完整 Word 文件，您可以进一步自定义或绑定 VBA 宏。

---

## 如何在代码中创建 forms2olecontrol – 步骤详解

### 步骤 1：初始化 DocumentBuilder

`DocumentBuilder` 类是 Aspose.Words 中大多数文档生成任务的入口点。它提供了添加文本、图像、表格以及本教程重点的 OLE 控件的方法。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**为何重要：**  
`DocumentBuilder` 维护文档内部的当前光标位置。提前创建它，可确保后续插入（如 **ActiveX 命令按钮**）正好出现在您希望的位置。

### 步骤 2：插入 Forms2OleControl

`insertForms2OleControl` 方法返回一个 `Forms2OleControl` 对象。该对象代表 Word 将渲染为 ActiveX 按钮的 OLE 控件占位符。

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**为何重要：**  
如果不调用此方法，您将无法操作控件的属性。返回的 `Forms2OleControl` 让您可以完整访问 **setOleClassName 方法**、大小属性以及其他 OLE‑特定设置。

### 步骤 3：使用 setOleClassName 指定 ActiveX 类

Word 需要知道要渲染哪种类型的 ActiveX 控件。标准命令按钮的类名为 `"Forms.CommandButton.1"`。

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**为何重要：**  
`setOleClassName` 方法是通用 OLE 占位符与具体 **ActiveX 命令按钮** 之间的桥梁。使用错误的类名会导致对象为空白或在打开文档时出现运行时错误。

### 步骤 4：调整 Forms2OleControl 大小

按钮过小或过大都会显得不专业。您可以使用 `setWidth` 和 `setHeight` 控制其尺寸。

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**为何重要：**  
这些属性构成 **Forms2OleControl 大小**。它们影响按钮在 Word UI 中的显示效果，并确保任何关联的宏拥有足够的可点击区域。

### 步骤 5：保存文档并测试

配置完控件后，将文档保存到您选择的位置。

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

在 Microsoft Word 中打开 `ActiveXButton.docx`。您应该会看到一个标记为 “CommandButton1” 的按钮（默认标题）。点击它不会执行任何操作，除非您添加 VBA 宏，但控件本身已完全可用。

**预期输出：**  

![Word 文档中插入的 ActiveX 命令按钮](/images/activeX-button.png "显示通过代码插入的全新 ActiveX 命令按钮的 Word 文档截图")

*图片的 alt 文本包含主要关键词，以提升可访问性和 SEO。*

---

## 理解 ActiveX Forms2OleControl 类

`Forms2OleControl` 类封装了 Word 用于 ActiveX 元素的底层 OLE 基础设施。它继承自 `Shape`，因此您也可以对其应用常规形状格式（例如边框、旋转）等。

* **ActiveX 命令按钮** – 最常见的使用场景；可通过 Word 开发者工具将其绑定到宏。
* **setOleClassName 方法** – 决定 Word 加载的 COM 类；其他有效值包括 `"Forms.TextBox.1"` 和 `"Forms.ComboBox.1"`。
* **Forms2OleControl 大小** – 通过 `SetWidth`/`SetHeight` 控制。这些方法接受点数（1 pt = 1/72 in）。

### 使用 Forms2OleControl 与内容控件的对比

如果您只需要简单的数据输入（例如普通文本字段），Word 内置的内容控件更轻量。只有在需要完整的 ActiveX 功能（如事件处理或自定义 VBA 交互）时才使用 `Forms2OleControl`。

---

## 设置其他属性（可选）

虽然核心步骤已经足以 **在代码中创建 forms2olecontrol**，但您通常还想微调按钮的外观或行为。

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**为何重要：**  
`SetOleData` 允许您直接向 OLE 流写入任意属性值。这是自定义 **ActiveX 命令按钮** 而无需使用 VBA 的最灵活方式。

---

## 常见问题与排查

| 症状 | 可能原因 | 解决办法 |
|--------|--------------|-----|
| 按钮显示为灰色方框 | `setOleClassName` 传入的类名不正确 | 确认字符串完全为 `"Forms.CommandButton.1"`（区分大小写） |
| 大小未变化 | 在插入控件之前设置了 Width/Height | 始终在 `InsertForms2OleControl` **之后** 调用 `SetWidth`/`SetHeight` |
| 打开文档时报 “OLE object not found” 错误 | 缺少 Aspose.Words 许可证（评估版可能限制 OLE） | 应用有效许可证或使用完整 OLE 支持的免费试用版 |
| 按钮标题仍为 “CommandButton1” | 未使用 `SetOleData` 或宏未读取该属性 | 使用 VBA 宏读取 `"Caption"` 属性，或通过 Word UI 设置标题 |

---

## 完整可运行示例

下面是一个完整的控制台应用程序示例，您可以复制、粘贴并运行。它演示了本教程中涉及的所有内容。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**各部分说明**

* **Using 指令** – 引入 Aspose.Words 命名空间，以便使用 `Document`、`DocumentBuilder` 和 `Forms2OleControl`。
* **文档创建** – 实例化一个空的 Word 文件。
* **InsertForms2OleControl** – 将 OLE 控件放置在 Builder 当前光标位置。
* **SetOleClassName** – 告诉 Word 该控件是 **ActiveX 命令按钮**。
* **SetWidth / SetHeight** – 调整 **Forms2OleControl 大小**，使外观更专业。
* **SetOleData（可选）** – 演示如何写入额外属性，如按钮标题。
* **Save** – 将最终的 `.docx` 文件写入磁盘。

运行程序（`dotnet run`），然后打开 `ActiveXButton.docx`。您应该会看到一个可以后续链接到宏的按钮。

---

## 结论

现在，您已经掌握了使用 Aspose.Words **在代码中创建 forms2olecontrol** 的完整流程，从初始化 `DocumentBuilder` 到使用 `setOleClassName` 配置 **ActiveX 命令按钮**，并控制其 **Forms2OleControl 大小**。此方法让您能够自动化复杂的 Word 文档，嵌入交互式 UI 元素，并将所有逻辑保留在代码层面。

## 接下来您应该学习什么？

以下教程涵盖了与本指南密切相关的主题，帮助您进一步掌握 API 功能并探索在项目中实现的替代方案。每篇资源均提供完整的可运行代码示例和逐步解释。

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}