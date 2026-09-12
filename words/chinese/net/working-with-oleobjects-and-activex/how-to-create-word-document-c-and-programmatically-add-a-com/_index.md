---
category: general
date: 2026-09-11
description: 学习如何使用 C# 创建 Word 文档，并通过 Aspose.Words 以几步简单的方式编程添加命令按钮。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: zh
lastmod: 2026-09-11
og_description: 使用 C# 创建 Word 文档，并通过 Aspose.Words 编程方式添加命令按钮。请参阅本完整指南获取可行的解决方案。
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: 使用 C# 创建 Word 文档 – 以编程方式添加命令按钮
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: 如何使用 C# 创建 Word 文档并以编程方式添加命令按钮
url: /zh/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 C# 创建 Word 文档并以编程方式添加命令按钮

如果您需要 **创建 word document c#** 并嵌入交互式按钮，本指南将一步步展示如何实现。借助 Aspose.Words，您只需几行代码即可以编程方式添加 CommandButton，省去在 Word 中手动操作 UI 的麻烦。

在本教程中，您将学习：

* 使用 C# 初始化一个空白 Word 文件。
* 插入 ActiveX **CommandButton** 控件。
* 设置按钮的属性，如名称和标题。
* 保存文档，使按钮在 Microsoft Word 中打开时可见。

无需除 Aspose.Words for .NET 库之外的外部工具，步骤适用于 .NET 6+ 或 .NET Framework 4.6.2 及更高版本。

## 前置条件

在开始之前，请确保您具备以下条件：

| Requirement | Reason |
|------------|--------|
| .NET 6 SDK（或 .NET Framework 4.6.2+） | 为 C# 项目提供运行时。 |
| Visual Studio 2022（或任意 C# IDE） | 便于编写、构建和运行代码。 |
| Aspose.Words for .NET NuGet 包 | 提供示例中使用的 `Document`、`DocumentBuilder` 和 `Forms2OleControl` 类。 |
| 基本的 C# 语法知识 | 让您无需额外学习即可跟随代码。 |

您可以通过 NuGet 控制台添加 Aspose.Words 包：

```powershell
Install-Package Aspose.Words
```

## 步骤 1：创建新的 C# 控制台项目

创建一个控制台应用程序，用于生成 Word 文件。打开终端并运行：

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

生成的 `Program.cs` 文件将承载后续步骤中的代码。

## 步骤 2：创建空白文档并实例化 DocumentBuilder

首先实例化一个 `Document` 对象，它代表一个空的 `.docx` 文件；随后创建一个 `DocumentBuilder`，用于编辑文档内容。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**为什么重要：**  
`Document` 是所有 Word 元素（段落、表格、控件）的容器。`DocumentBuilder` 提供流式 API，可在当前光标位置插入对象，而无需直接操作底层节点集合。

## 步骤 3：插入 ActiveX CommandButton 控件

Aspose.Words 通过 `InsertForms2OleControl` 方法支持插入传统的 ActiveX 控件。该方法需要指定控件类型以及以点为单位的尺寸。

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**内部工作原理：**  
Word 将 ActiveX 控件视为 OLE（对象链接与嵌入）对象。`Forms2OleControl` 类封装 OLE 数据，并公开 `Name`、`Caption` 等属性。

## 步骤 4：配置按钮的名称和标题

控件放置后，您可以自定义其运行时属性。为按钮设置有意义的 `Name` 有助于后续定位，而 `Caption` 决定按钮上显示的文字。

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**小技巧：**  
如果您计划使用 VBA 处理按钮的点击事件，`Name` 将成为宏名称，例如 `Sub btnSubmit_Click()`。

## 步骤 5：将文档保存到磁盘

最后，将文档写入 `.docx` 文件。请选择您拥有写入权限的文件夹；示例使用相对路径，解析后指向项目的输出目录。

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

运行程序后会生成 `CommandButton.docx`。在 Microsoft Word 中打开该文件，即可看到可点击的 **Submit** 按钮：

![Word document with a Submit command button](/images/command-button.png "Screenshot of a Word document containing a Submit command button created with C#")

*Image alt text (og_image_alt):* `Screenshot of a Word document containing a Submit command button created with C#`

## 验证结果

1. 启动 Word 并打开 `CommandButton.docx`。  
2. 您应在文档正文中看到标有 **Submit** 的按钮。  
3. 将鼠标悬停在按钮上，可在 **属性** 面板（开发者选项卡 → 属性）中看到名称 `btnSubmit`。  

如果按钮未出现，请确保 Word 中已启用 **开发者** 选项卡（文件 → 选项 → 自定义功能区 → 勾选 *开发者*）。禁用该选项卡时，ActiveX 控件会被隐藏。

## 常见变体与边缘情况处理

| Situation | Recommended adjustment |
|-----------|------------------------|
| **不同的按钮尺寸** | 修改 `InsertForms2OleControl` 中的宽度和高度参数。例如，`150, 40` 可生成更大的按钮。 |
| **多个按钮** | 多次调用 `InsertForms2OleControl`，并在调用之间移动构建器光标（`builder.Writeln();`）。 |
| **不使用 ActiveX 的按钮** | 使用 `InsertFormField` 添加传统表单字段（如复选框），以兼容会阻止 ActiveX 的旧版 Word。 |
| **跨平台使用** | ActiveX 控件仅在 Windows 版 Word 上工作。对于 Mac 或基于 Web 的查看器，可考虑插入样式化的超链接来模拟按钮。 |
| **安全警告** | 打开包含 ActiveX 控件的文档时，Word 可能弹出安全提示。使用受信任证书对文档签名可降低此阻力。 |

## 完整可运行示例

下面是完整的程序代码，可直接复制粘贴到 `Program.cs` 中。添加 Aspose.Words NuGet 包后，无需修改即可编译运行。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**控制台预期输出：**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

打开生成的文件即可看到已准备好的 **Submit** 按钮。

## 结论

现在您已经掌握了如何 **create word document c#** 并使用 Aspose.Words **以编程方式添加 command button** 控件。整个过程归结为：初始化 `Document`、插入 `Forms2OleControl`、配置属性并保存文件。接下来您可以：

* 通过更改 `ControlType` 添加更多控件（如复选框、文本框）。  
* 为按钮附加 VBA 宏，实现自定义逻辑。  
* 将此技术与 Aspose.Words 的其他功能（如邮件合并或模板填充）结合使用。

尝试不同的尺寸、标题和多个按钮，以满足您的自动化场景。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖了与本指南技术密切相关的主题，提供完整的代码示例和逐步解释，帮助您掌握更多 API 功能并探索在项目中的替代实现方式。

- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}