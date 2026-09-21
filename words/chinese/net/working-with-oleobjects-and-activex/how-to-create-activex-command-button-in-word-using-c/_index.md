---
category: general
date: 2026-09-21
description: 学习如何使用 Aspose.Words 和 C# 在 Word 文档中创建 ActiveX 命令按钮。一步步指南涵盖插入、定位和保存。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: zh
lastmod: 2026-09-21
og_description: 使用 C# 和 Aspose.Words 在 Word 文档中创建 ActiveX 命令按钮。请按照本完整教程，程序化地插入、定位并保存按钮。
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: 使用 C# 在 Word 中创建 ActiveX 命令按钮 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: 如何使用 C# 在 Word 中创建 ActiveX 命令按钮
url: /zh/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中使用 C# 创建 ActiveX 命令按钮

如果您需要在 Word 文件中 **创建 ActiveX 命令按钮**，本指南将展示完整步骤。借助 Aspose.Words for .NET，您可以完全通过 C# 代码添加、定位并配置按钮。

以编程方式插入 ActiveX 按钮可消除手动 UI 操作，并实现表单、报告或交互式模板的自动化文档生成。在本教程中，您将学习如何使用 **DocumentBuilder**、**InsertForms2OleControl** 方法以及相关属性来实现功能完整的按钮。

## 您需要准备的环境

在开始之前，请确保您具备以下条件：

* .NET 6.0 SDK 或更高版本（代码同样适用于 .NET Framework 4.7+）
* Aspose.Words for .NET（NuGet 包 `Aspose.Words`）
* Visual Studio 2022、VS Code 或其他 IDE
* 基本的 C# 与 Word 文档概念

无需额外安装 Office，因为 Aspose.Words 可独立于 Microsoft Word 工作。

## 第 1 步：创建 C# 项目

新建一个控制台项目并添加 Aspose.Words 包。

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

`Aspose.Words` 库提供了 **DocumentBuilder** 类，供我们操作文档使用。

## 第 2 步：初始化文档和 Builder

下面的代码块创建一个空白文档并实例化 `DocumentBuilder`。该对象是所有 Word 处理操作的入口。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**为什么重要：** `DocumentBuilder` 维护当前光标位置，后续的任何插入都会精确出现在光标所在位置。

## 第 3 步：插入 ActiveX 命令按钮

**InsertForms2OleControl** 方法会创建指定类型的 ActiveX 控件。这里我们请求创建 `CommandButton`，并以点为单位指定大小（200 × 30 pt）。

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**说明：**  
* `OleControlType.CommandButton` 告诉 Aspose.Words 创建按钮而非其他控件类型。  
* 该方法返回一个 `Forms2OleControl` 对象，提供定位和属性字段。

## 第 4 步：定位按钮并设置属性

插入后，您可以将按钮移动到页面任意位置，并为其指定编程名称和可见标题。

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**小技巧：** 坐标系起点位于页面左上角。调整 `Left` 和 `Top` 可使按钮与其他表单字段对齐。

## 第 5 步：保存文档

最后，将文档写入磁盘。文件中将包含 ActiveX 按钮，打开后即可在 Microsoft Word 中交互使用。

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

在 Word 中打开 `ActiveXCommandButton.docx` 时，您会看到位于指定位置的 **Submit** 按钮。点击该按钮会触发默认的命令按钮行为（后续可通过 VBA 或 Word 加载项自定义）。

## 完整可运行示例

将所有代码片段组合在一起，即可得到一个可直接复制、粘贴并运行的独立程序。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**预期输出：** 控制台打印 *“Document created successfully.”*，并在文件夹中生成 `ActiveXCommandButton.docx`。在 Microsoft Word 中打开该文件，可看到一个可点击的 **Submit** 按钮，左边距 100 pt、顶部 150 pt。

## 常见问题及解决方案

| 问题 | 产生原因 | 解决办法 |
|------|----------|----------|
| 按钮显示在页面之外 | `Left`/`Top` 值超出页面尺寸 | 使用 `doc.FirstSection.PageSetup.PageWidth` 与 `PageHeight` 计算安全坐标 |
| Word 中看不到按钮 | 文档保存为会剥离 ActiveX 控件的格式（如 `.txt`） | 始终保存为 `.docx` 或 `.doc` |
| 运行时出现 `ArgumentOutOfRangeException` | 宽度或高度设为零或负数 | 确保传递给 `InsertForms2OleControl` 的尺寸参数为正数 |

## 扩展方案

您可以通过设置 `Enabled`、`Visible` 等属性进一步自定义按钮，或通过 VBA 绑定宏。**Forms2OleControl** 类同样支持插入其他 ActiveX 控件，如复选框 (`OleControlType.CheckBox`) 或下拉框 (`OleControlType.ComboBox`)。

如果需要在循环中生成多个按钮，可将插入逻辑封装为辅助方法：

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## 结论

现在，您已经掌握了使用 C# 和 Aspose.Words 在 Word 文档中 **创建 ActiveX 命令按钮** 的全部步骤。教程涵盖了项目搭建、使用 `InsertForms2OleControl` 插入按钮、定位以及保存最终文件。基于此，您可以自动化复杂表单、嵌入交互式控件，并将 Word 文档集成到更大的 .NET 解决方案中。

接下来，您可以进一步探索 **Aspose.Words ActiveX** 表单字段、**C# DocumentBuilder** 高级样式，或以编程方式在 Word 中添加 **ActiveX 控件**（如复选框和下拉列表）。尝试不同的坐标和尺寸，以满足您的特定布局需求。祝编码愉快！

## 接下来您应该学习什么？

以下教程与本指南紧密相关，帮助您进一步掌握相关技术。每个资源都提供完整的可运行代码示例和逐步解释，助您在项目中灵活运用 API 并探索替代实现方案。

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}