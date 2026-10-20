---
category: general
date: 2026-10-20
description: 使用 Aspose.Words 编程创建 Word 文档并添加命令按钮。学习插入 ActiveX 控件并设置按钮标题。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: zh
lastmod: 2026-10-20
og_description: 以编程方式创建 Word 文档并嵌入 ActiveX 命令按钮。本教程说明如何使用 Aspose.Words 插入该控件并设置其按钮文字。
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: 以编程方式创建 Word 文档 – 添加 ActiveX 按钮
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: 使用 ActiveX 按钮以编程方式创建 Word 文档
url: /zh/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 ActiveX 按钮以编程方式创建 Word 文档

使用 Aspose.Words 以编程方式创建 Word 文档，然后添加一个用户可以点击的命令按钮。本指南将带您完成插入 ActiveX 控件、配置其属性以及将结果保存为 **.docx** 文件的步骤。

您将看到一个完整的可运行示例，您可以将其复制到控制台应用程序中。教程结束时，您能够生成包含完整功能命令按钮的 Word 文件，并且了解如何在 C# 代码中 **add command button**、**add activex control**、**insert activex button** 和 **set button caption**，而无需离开代码。

## 前置条件

* .NET 6.0 SDK 或更高版本已安装  
* Visual Studio 2022（或任何兼容 C# 的 IDE）  
* Aspose.Words for .NET 许可证文件（免费试用版可用于本示例）  
* 对 C# 和 .NET 项目系统有基本了解  

除 **Aspose.Words** 外无需额外的 NuGet 包，因为 ActiveX 支持已内置于该库中。

## 步骤 1：设置项目并添加 Aspose.Words

1. 打开终端或 Visual Studio 并创建一个新的控制台项目：

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. 添加 Aspose.Words 包：

   ```bash
   dotnet add package Aspose.Words
   ```

3. （可选）如果您有许可证文件，请将其放在项目根目录，并在 `Program.cs` 开头添加以下代码行，以避免评估水印：

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## 步骤 2：以编程方式创建 Word 文档 – 初始化文档

第一步是 **以编程方式创建 Word 文档**。您可以通过实例化 `Document` 对象和 `DocumentBuilder`（用于编辑文档内容）来实现。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` 表示整个文件，而 `DocumentBuilder` 维护一个光标，您可以将其移动到文档中的任意位置。这种分离保持了 API 的简洁，并使您以后能够 **add activex control** 而无需手动管理底层结构。

## 步骤 3：添加命令按钮 – 插入 ActiveX 控件

现在，您将通过插入类型为 `OleControlType.CommandButton` 的 ActiveX 控件来 **add command button**。`InsertForms2OleControl` 方法需要控件类型、位置（`Point`）和大小（`Size`）。

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

上述调用会 **insert activex button** 到文档中您指定的精确坐标。坐标以点为单位（1 pt ≈ 1/72 in）。如果需要将按钮放在特定段落上，请先移动 builder 的光标：

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## 步骤 4：设置按钮标题 – 自定义命令按钮文本

没有标签的按钮会让人困惑，因此您将 **set button caption** 为有意义的文字。`Caption` 属性定义按钮上显示的文本，而 `Name` 为控件提供程序化标识符。

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

如果您随后将文档导出为宏启用格式（`.docm`），`OnClick` 的值必须与 VBA 宏名称匹配。对于普通的 `.docx`，该属性会被保存但不会执行，这在大多数自动化场景中是可以接受的。

## 步骤 5：保存包含 ActiveX 按钮的文档

配置完控件后，您可以 **save the document**。选择一个您有写入权限的目录，并使用 `.docx` 扩展名以获得最大兼容性。

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

当您在 Microsoft Word 中打开生成的文件时，会看到一个标有 **Submit** 的按钮，位于您指定的坐标处。点击桌面客户端中的按钮将尝试运行 `SubmitForm` 宏（如果存在）。

## 步骤 6：验证结果并排查常见问题

1. 在 Microsoft Word 中打开 `ActiveXCommandButton.docx`。  
2. 切换到 **Design Mode**（开发者选项卡 → **Design Mode**），以查看按钮的边框。  
3. 如果按钮未出现，请检查已启用 **Developer** 选项卡，并确认您的 Word 版本支持 ActiveX 控件。  
4. 对于宏启用文件（`.docm`），确保 `OnClick` 中的宏名称与 VBA 例程匹配；否则 Word 将显示安全警告。

### 小贴士

ActiveX 控件仅适用于 Windows。如果需要跨平台交互，请考虑使用 **Content Controls**（`RichTextContentControl`）来替代 ActiveX 按钮。

## 完整源代码

下面是完整的可直接运行的程序。将其复制到 `Program.cs` 并执行 `dotnet run`。



## 接下来应该学习什么？

以下教程涵盖与本指南演示的技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在自己的项目中探索替代实现方案。

- [使用 ActiveX 按钮创建 Word 文档 – C# 指南](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [使用 Aspose.Words 向 Word 文档添加命令按钮 – 完整指南](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [使用 Aspose.Words 创建 Word 文档按钮 – 完整代码示例](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}