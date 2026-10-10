---
category: general
date: 2026-10-10
description: 使用 Aspose.Words 在 C# 中设置按钮文本并添加 ActiveX 按钮。了解如何插入按钮、创建按钮控件以及在 Word 文档中自定义标题。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: zh
lastmod: 2026-10-10
og_description: 使用 Aspose.Words 在 C# 中设置按钮文本并添加 ActiveX 按钮。请按照本分步指南插入按钮、创建按钮控件并自定义其标题。
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: 在 C# 中设置按钮文本并添加 ActiveX 按钮 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: 在 C# 中设置按钮文本并添加 ActiveX 按钮
url: /zh/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中设置按钮文本并添加 ActiveX 按钮

如果您需要在 Word 文档中的 ActiveX 按钮上 **设置按钮文本**，本指南将手把手教您完成。教程结束后，您将能够 **插入按钮**、创建 **按钮控件**，并仅用几行 C# 代码自定义其标题。

在 Word 中使用 ActiveX 控件是实现交互式表单的常见做法——无论是构建合同模板、调查问卷，还是内部工具。示例使用 Aspose.Words for .NET，这个库可以在未安装 Microsoft Office 的情况下操作 Word 文件。

## 前置条件

开始之前，请确保您已具备：

* .NET 6.0 SDK 或更高版本  
* Visual Studio 2022（或任何支持 C# 的 IDE）  
* Aspose.Words for .NET 许可证（免费评估版可用于学习）  

同时需要引用 `Aspose.Words` NuGet 包：

```bash
dotnet add package Aspose.Words
```

## 如何将按钮插入 Word 文档

第一步是创建一个新的 `Document` 和 `DocumentBuilder`。`DocumentBuilder` 是添加内容（包括 ActiveX 控件）的入口。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**为何重要：** `Document` 代表整个 .docx 文件，而 `DocumentBuilder` 提供 `InsertParagraph`、`InsertFormField` 等高级方法。使用全新文档可以确保按钮出现在您期望的位置。

## 使用 Forms2OleControl 创建按钮控件

接下来创建实际的按钮控件。`Forms2OleControl` 是 Aspose.Words 用于所有 ActiveX 对象的类，`COMMANDBUTTON` 类型在 Word 中呈现为可点击的按钮。

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**说明：**  
* `InsertForms2OleControl` 会在您提供的精确坐标处放置控件。  
* 大小以点为单位（1 point = 1/72 英寸）。根据布局需要调整这些数值。

## 添加 ActiveX 控件并赋予唯一名称

每个 ActiveX 对象都应拥有唯一名称，以便后续引用（例如在 VBA 中处理事件时）。

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**提示：** 名称中避免使用空格或特殊字符；Word 将名称视为内部表单模型中的标识符。

## 在 ActiveX 按钮上设置按钮文本（标题）

这正是 **set button text** 关键字发挥作用的地方。`Caption` 属性定义用户在按钮上看到的标签。

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

您可以在保存文档前随时更改标题。如果以后需要本地化 UI，只需再次调用 `SetCaption` 并传入不同的字符串即可。

## 保存文档并验证结果

最后，将文档写入磁盘。使用 Microsoft Word 打开文件即可看到带有自定义标题的按钮。

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**预期输出：** 在 Word 中打开 *ActiveXButton.docx* 时，您会看到一个位于指定坐标、标题为 **Click Me** 的按钮。点击按钮将触发默认的 Word 命令按钮行为（后续可通过 VBA 自定义）。

![Set button text example](https://example.com/activex-button.png){alt="设置按钮文本示例"}

## 添加 ActiveX 按钮并处理事件（可选）

如果需要按钮执行自定义操作，可以添加响应 `Click` 事件的 VBA 宏。宏可以通过编程方式注入，但这超出本教程范围。关键是按钮已经存在且标题已设置——随时可以进行任意事件处理。

## 常见陷阱及规避方法

| 问题 | 产生原因 | 解决方案 |
|------|----------|----------|
| 按钮位置错位 | 坐标使用的是点而非像素 | 将像素值转换为点 (`points = pixels * 72 / DPI`) |
| 保存后标题未改变 | `SetCaption` 在 `Save` 之后调用 | 始终在调用 `doc.Save` **之前** 设置标题 |
| 在旧版 Word 中控件不可见 | 某些旧版 Word 缺少完整的 ActiveX 支持 | 在目标 Word 版本上测试；必要时使用 `CheckBox` 或 `DropDownList` 作为备选 |
| 输出中出现许可证警告 | 评估许可证已过期 | 通过 `License license = new License(); license.SetLicense("Aspose.Words.lic");` 应用有效许可证 |

## 完整可运行示例

下面是完整程序代码，您可以直接复制、粘贴并运行。它包含所有必需的 `using` 指令，演示了从文档创建到保存的完整工作流。

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
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

使用 `dotnet run` 运行程序。执行完毕后，打开 *ActiveXButton.docx*，确认按钮标题为 **Click Me**。

## 本教程要点回顾

* 您学习了如何使用 Aspose.Words 在 ActiveX 按钮上 **set button text**。  
* 您掌握了 **如何插入按钮**、**创建按钮控件**、以及 **向 Word 文档添加 ActiveX 控件** 的完整步骤。  
* 您现在拥有一段可复用的代码片段，可在任何基于表单的 Word 自动化项目中进行适配。

## 后续步骤

* 探索其他 `Forms2OleControlType` 值，如 `CHECKBOX` 或 `LISTBOX`，以构建更丰富的表单。  
* 将按钮与 VBA 宏结合，实现计算或数据校验等自定义功能。  
* 使用 Aspose.Words 的 `FormField` API 在文档填写后读取用户输入。

欢迎随意实验尺寸、位置和标题，以满足您的设计需求。如遇问题，Aspose.Words 文档提供了对本教程中使用的每个类的详细参考。

祝编码愉快！


## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并探索在项目中的替代实现方式。每篇资源均提供完整可运行的代码示例和逐步解释。

- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}