---
category: general
date: 2026-09-08
description: 如何在 C# 中插入 ActiveX 控件时保存 docx。请按照本分步指南以编程方式添加命令按钮。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save docx
- insert activex control
- add activex button
- create word document programmatically
- how to add command button
language: zh
lastmod: 2026-09-08
og_description: 如何在 C# 中插入 ActiveX 控件时保存 docx。本教程将逐步演示以编程方式创建 Word 文档、添加命令按钮并持久化文件。
og_image_alt: How to save docx with an ActiveX command button displayed in the document
og_title: 如何在 C# 中保存 docx 并嵌入 ActiveX 按钮
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: How to save docx while inserting an ActiveX control in C#. Follow this
    step‑by‑step guide to add a command button programmatically.
  headline: How to save docx and insert an ActiveX button with C#
  type: TechArticle
tags:
- C#
- Word automation
- ActiveX
- Docx
title: 如何使用 C# 保存 docx 并插入 ActiveX 按钮
url: /zh/net/working-with-oleobjects-and-activex/how-to-save-docx-and-insert-an-activex-button-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 C# 保存 docx 并插入 ActiveX 按钮

如果您需要以编程方式创建 Word 文档并随后保存带有交互按钮的 docx，本指南将向您展示如何实现。您将学习插入 ActiveX 控件、添加 ActiveX 按钮，并使用 C# 和 Aspose.Words 库保存生成的 .docx 文件。

本教程涵盖了 **create word document programmatically**（以编程方式创建 Word 文档）的所有必要步骤，嵌入 **command button**（命令按钮），并将文件持久化到磁盘。无需先前的 COM 对象经验，但您应具备基本的 C# 知识并已安装 Visual Studio。

## 前提条件

* .NET 6.0 SDK 或更高版本  
* Visual Studio 2022（或任何 C# IDE）  
* Aspose.Words for .NET NuGet 包（`Install-Package Aspose.Words`）  
* 了解 C# 项目结构  

这些项目确保代码能够编译并在无需额外配置的情况下运行。

## 步骤 1：设置新的 C# 控制台项目

创建一个将承载 Word 自动化逻辑的控制台应用程序。

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

上述命令会创建一个名为 **WordActiveXDemo** 的文件夹，添加 Aspose.Words 引用，并为编译准备项目。

## 步骤 2：以编程方式创建 Word 文档

打开生成的 `Program.cs` 文件并添加所需的 `using` 指令。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;   // not used directly but required for some overloads
```

现在实例化一个空的 `Document` 对象。该对象表示内存中的整个 Word 文件。

```csharp
// Step 2: Create a new blank document
Document document = new Document();
```

`Document` 类是所有 Word 处理操作的入口点。此时文档不包含任何页面，但当您添加内容时，Aspose.Words 会自动创建默认节。

## 步骤 3：插入 ActiveX 控件 – 添加 activex 按钮

**Forms2OleControl** 对象允许您在 Word 段落中嵌入 ActiveX 控件。以下代码插入一个宽度为 150 pt、高度为 30 pt 的 **CommandButton**。

```csharp
// Step 3: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX CommandButton control with the desired size
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

`InsertForms2OleControl` 创建控件并返回一个强类型的 `Forms2OleControl` 实例，您可以进一步配置它。该方法会自动添加一个新段落来容纳控件，因此您无需手动管理段落对象。

## 步骤 4：配置命令按钮 – 如何添加命令按钮属性

设置按钮的 **Name** 和 **Caption** 属性，以便在运行时能够识别并在 UI 中友好显示。

```csharp
// Step 4: Set the control's name and caption
commandButton.Name = "cmdSubmit";
commandButton.Caption = "Submit";
```

`Name` 属性在您稍后通过 VBA 或 Word 宏处理按钮点击事件时非常有用。`Caption` 是最终用户在按钮表面看到的文本。

### 小技巧
如果您计划从 C# 自动化处理点击事件，请嵌入引用 `cmdSubmit` 的 VBA 宏。文档打开时，Word 会提示用户启用宏，这是一种针对 ActiveX 控件的标准安全行为。

## 步骤 5：如何保存 docx

控件就位后，将文档持久化为 .docx 文件。`Save` 方法会根据文件扩展名自动选择相应的格式。

```csharp
// Step 5: Save the document containing the CommandButton
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

保存文件完成了 **how to save docx** 工作流。生成的文件可在 Microsoft Word 中打开，ActiveX 按钮将出现在首页。点击按钮时，除非附加了宏，否则 Word 将显示占位消息。

## 步骤 6：运行程序并验证结果

编译并执行控制台应用程序：

```bash
dotnet run
```

程序完成后，在 Microsoft Word 中打开 `C:\Temp\CommandButton.docx`：

* 文档包含单页，在顶部附近有一个 **Submit** 按钮。  
* 将鼠标悬停在按钮上会显示名称为 `cmdSubmit` 的工具提示。  
* 内容未丢失，文件大小与标准空白 .docx 相当。

如果按钮未出现，请确认以下事项：

1. Word 的 **Trust Center** 设置允许 ActiveX 控件。  
2. 文件已使用 `.docx` 扩展名保存（而非 `.doc`）。  

## 边缘情况和常见变体

| 情况 | 推荐的调整 |
|-----------|------------------------|
| 需要不同的按钮尺寸 | 在 `InsertForms2OleControl` 中更改宽度和高度参数。 |
| 希望按钮位于特定页面 | 在添加页面后使用 `builder.MoveToDocumentEnd();`，或在控件前插入分页符。 |
| 必须支持没有 Aspose.Words 的环境 | 使用 Open XML SDK 插入 `w:object` 元素，但代码会变得相当复杂。 |
| 需要宏启用的文档 | 使用 `.docm` 扩展名保存（`document.Save("MyDoc.docm");`），并嵌入处理 `cmdSubmit_Click` 的 VBA 模块。 |

## 完整源代码

下面是完整的、独立的程序，您可以复制到 `Program.cs` 中并直接运行（除输出路径外无需修改）。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document document = new Document();

            // Initialize a DocumentBuilder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control with the desired size
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Set the control's name and caption
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // Save the document containing the CommandButton
            string outputPath = @"C:\Temp\CommandButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### 控制台的预期输出

```
Document saved to C:\Temp\CommandButton.docx
```

在 Word 中打开文件会显示标有 **Submit** 的按钮。点击按钮会触发默认的 ActiveX 行为（弹出消息框提示未附加宏）。

## 结论

本教程演示了在嵌入 **ActiveX control**（特别是 **add activex button**）作为命令按钮的同时，**how to save docx** 的方法。您现在了解了如何 **create word document programmatically**、配置按钮属性，并将文件持久化供最终用户交互使用。

接下来您可以探索：

- 添加 VBA 宏以处理 `cmdSubmit_Click`。  
- 插入其他 ActiveX 控件，如复选框或组合框。  
- 生成包含多个交互元素的多页文档。  

尝试不同的控件类型和布局选项，构建丰富的交互式 Word 模板，以简化您的业务流程。

## 接下来您应该学习什么？

以下教程涵盖与本指南紧密相关的主题，基于所示技术进行扩展。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方法。

- [Aspose.Words – 将 docx 保存为 txt 并导出 Word 方程为 LaTeX – 完整指南](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [如何恢复 docx – 针对损坏 Word 文件的 C# 指南](/words/english/net/programming-with-loadoptions/how-to-recover-docx-c-guide-for-corrupted-word-files/)
- [如何将 Word 保存为 Markdown – 完整 C# 指南](/words/english/net/programming-with-markdownsaveoptions/how-to-save-word-as-markdown-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}