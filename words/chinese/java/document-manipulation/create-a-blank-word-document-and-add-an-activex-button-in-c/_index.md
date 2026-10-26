---
category: general
date: 2026-10-23
description: 使用 C# 创建空白 Word 文档，并学习如何使用 Aspose.Words 插入 ActiveX 控件，包括按钮。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: zh
lastmod: 2026-10-23
og_description: 使用 C# 创建空白 Word 文档，并学习如何使用 Aspose.Words 插入 ActiveX 控件，包括按钮。
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: 在 C# 中创建空白 Word 文档并添加 ActiveX 按钮
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: 在 C# 中创建空白 Word 文档并添加 ActiveX 按钮
url: /zh/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中创建空白 Word 文档并添加 ActiveX 按钮

如果你需要 **以编程方式创建空白 Word 文档**，本指南将一步步演示。你将看到一个完整、可运行的示例，创建新文档、插入 ActiveX CommandButton，并保存文件——全部使用 Aspose.Words for .NET。

处理 Word 文件时往往不仅仅是纯文本。添加 **ActiveX 按钮** 可以嵌入交互功能，适用于宏启用的模板或仅限 Windows 的解决方案。教程结束后，你将能够插入任意 ActiveX 控件，但我们重点演示最常见的场景：一个 **word document activex button** 用于提交表单。

## 前置条件

开始之前，请确保你拥有：

* .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.7+）
* Visual Studio 2022（或任意 C# IDE）
* **Aspose.Words for .NET** NuGet 包  
  ```bash
  dotnet add package Aspose.Words
  ```
* 对 C# 语法有基本了解

> **专业提示：** Aspose.Words 是商业库，但提供免费临时许可证用于测试。尽早安装许可证可避免评估水印。

## 第一步：使用 Aspose.Words 创建空白 Word 文档

第一步是实例化一个 `Document` 对象。它在内存中表示一个空的 `.docx` 文件。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` 初始时没有章节、页面或内容。它是你在 **create blank word document** 场景下需要的干净画布，例如从头生成报告。

## 第二步：获取 DocumentBuilder 以编辑文档

`DocumentBuilder` 提供了便捷的 API 用于添加文本、图像和控件。我们将使用它来定位 ActiveX 控件。

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

构建器会自动添加默认章节和第一页，因而可以立即插入对象。

## 第三步：向文档插入 ActiveX 控件的方法

Aspose.Words 暴露了 `InsertForms2OleControl` 用于嵌入 OLE/ActiveX 对象。该方法需要控件类型、宽度和高度（单位为点）。下面我们插入一个 **CommandButton**——在传统 Word 模板中常见的表单按钮。

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **为什么可行：** `Forms2OleControlType.COMMANDBUTTON` 告诉 Word 创建一个按钮，当文档在支持 ActiveX 的 Windows 环境中打开时，可响应点击事件。

## 第四步：创建 ActiveX 控件并设置属性

现在为按钮指定程序化名称和可见标题。这正是 **create activex control** 时开发者常忽略的部分。

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` 是你将在 VBA 宏中引用的标识符（`ActiveDocument.InlineShapes("btnSubmit")`）。
* `Caption` 是按钮本身显示的标签。

## 第五步：保存带有 ActiveX 按钮的 Word 文档

最后，将文档写入磁盘。文件扩展名必须为 `.docx`（如果以后要添加宏，则使用 `.docm`）。示例保存到占位文件夹——请替换为自己的路径。

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

在 Windows 版 Microsoft Word 中打开生成的文件时，你会看到一个可用的 **word document activex button**，可以绑定到 VBA 代码。

## 完整工作示例

下面是可以直接复制到新控制台项目中的完整程序。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**运行程序时的预期输出**

```
Document saved to C:\Temp\ActiveXButton.docx
```

打开生成的 `ActiveXButton.docx`，你会在首页顶部看到标记为 **Submit** 的按钮。

## 边缘情况与常见陷阱

| 情况 | 需要注意的点 | 建议 |
|-----------|-------------------|----------------|
| 在 macOS 或 Linux 上运行 | ActiveX 是仅限 Windows 的技术，按钮会显示为占位符。 | 仅在面向 Windows 的模板中使用本教程。 |
| 文档在 Word Online 中打开 | 浏览器视图不支持 ActiveX 控件。 | 提供备用 UI，或指示用户在桌面客户端中打开文件。 |
| 需要宏启用的文件 | `.docx` 文件无法存储 VBA 代码。 | 保存为 `.docm`（`document.Save("MyFile.docm", SaveFormat.Docm)`），并单独添加宏。 |
| 控件尺寸不匹配 | 宽度/高度的单位是点（1 pt ≈ 1/72 in）。 | 调整数值以获得所需的视觉大小。 |

## 常见问题

**如何插入除按钮之外的 ActiveX 控件？**  
使用相同的 `InsertForms2OleControl` 方法，只需传入不同的 `Forms2OleControlType` 枚举值，例如 `COMBOBOX` 或 `LISTBOX`。

**能否更改按钮的字体或颜色？**  
ActiveX 按钮的外观由宿主应用（Word）和底层 Windows 主题决定。可以在文档打开后通过 VBA 修改 `ForeColor`、`BackColor` 等属性。

**有没有办法直接在 C# 中添加点击事件处理程序？**  
没有。点击事件必须由 VBA 或 Word 加载项处理，因为按钮在 Word 进程内部运行，而不是你的 .NET 应用程序。

## 结论

现在你已经掌握了如何使用 Aspose.Words for .NET **以编程方式创建空白 Word 文档** 并嵌入 **ActiveX 按钮**。本教程涵盖的步骤：

1. 实例化 `Document`。
2. 使用 `DocumentBuilder` 操作文件。
3. 调用 `InsertForms2OleControl` 实现 **how to insert activex** 控件。
4. 配置控件属性（**create activex control**）。
5. 保存文件，得到一个可供 VBA 集成的 **word document activex button**。

接下来，你可以尝试添加其他类型的控件、编写 VBA 宏，或在保留按钮（作为静态图像）的情况下将文档转换为 PDF。尽情实验不同的尺寸、标题和名称吧。

## 接下来你应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助你进一步掌握 API 功能并探索在项目中的替代实现方式。

- [How to add ActiveX button in a Word document with Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}