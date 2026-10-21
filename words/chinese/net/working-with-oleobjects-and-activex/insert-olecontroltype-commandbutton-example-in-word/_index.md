---
category: general
date: 2026-08-17
description: 使用 Aspose.Words 在 Word 中插入 OleControlType.CommandButton 示例。了解如何以编程方式向
  Word 文档添加表单控件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: zh
lastmod: 2026-08-17
og_description: 在 Word 中使用 Aspose.Words 插入 OleControlType.CommandButton 示例。请按照本指南向
  Word 文档添加表单控件。
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: 在 Word 中插入 OleControlType.CommandButton 示例
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: 在 Word 中插入 OleControlType.CommandButton 示例
url: /zh/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中插入 OleControlType.CommandButton 示例

如果您需要在 Word 文件中 **insert OleControlType.CommandButton example**，本指南将向您展示如何操作。您将学习使用 Aspose.Words **how to add form controls to a Word document**，并提供完整可运行的 C# 程序。

ActiveX 按钮等表单控件可以帮助您构建交互式 Word 模板——适用于合同、问卷或内部工具。以下步骤涵盖了从项目设置到验证保存的 `.docx` 文件中按钮是否正确显示的全部内容。

## 前置条件

- .NET 6.0 SDK 或更高版本已安装  
- Visual Studio 2022（或任何 C# IDE）  
- Aspose.Words for .NET 许可证或免费临时许可证  
- 对 C# 和 Word 文件概念有基本了解  

> **技巧提示：** 如果您使用的是免费试用版，请将许可证文件放在可执行文件所在的同一文件夹中，并在 `Main` 开始时加载它。

## 步骤 1：创建新控制台项目并添加 Aspose.Words

在终端中运行以下命令：

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

此命令会创建一个干净的项目并获取最新的 Aspose.Words 包，其中提供了实现 **insert OleControlType.CommandButton example** 所需的 `Document`、`DocumentBuilder` 和 `InsertForms2OleControl` API。

## 步骤 2：编写完整程序

创建或替换 `Program.cs` 为以下代码。它包含所有必需的 `using` 指令、许可证加载以及原始示例中展示的四步工作流。

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### 每行代码的意义

* **License loading** – 确保您不会受到评估限制的约束。  
* **`Document doc = new Document();`** – 创建用于存放所有 Word 内容的容器；这是 **insert OleControlType.CommandButton example** 的基础。  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – 提供流式 API，用于添加文本、图像和控件。  
* **`InsertForms2OleControl`** – 实现 **how to add form controls to a Word document** 的核心方法。`OleControlType.CommandButton` 枚举值指示 Aspose.Words 创建 ActiveX 按钮。  
* **`new Rectangle(100, 100, 80, 30)`** – 将按钮定位在距左、上边距各 100 点的位置，宽度为 80 点，高度为 30 点。根据布局需要可调整这些数值。  
* **`doc.Save`** – 将 .docx 文件写入磁盘；文件中现在包含嵌入的按钮。  

## 步骤 3：构建并运行程序

在项目文件夹中执行以下命令：

```bash
dotnet run
```

您应该会看到控制台输出信息：

```
Document saved to ActiveXButton.docx
```

在 Microsoft Word 中打开 `ActiveXButton.docx`。您会看到一个标记为 **ClickMe** 的按钮，大致位于页面中部。点击该按钮会触发默认的 ActiveX 行为（除非您附加宏，否则通常不执行任何操作）。

![insert olecontroltype.commandbutton example](/images/activex-button.png "ActiveX CommandButton inserted into a Word document")

*图片替代文字:* insert olecontroltype.commandbutton example – 在 Word 文档中显示的 ActiveX CommandButton。

## 步骤 4：自定义按钮（可选）

基本的 **insert OleControlType.CommandButton example** 会创建一个默认按钮。您可以通过编辑底层 OLE 对象来修改其标题、字体，甚至附加宏。下面提供一种在插入后更改按钮标题的简洁方法：

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **注意：** 直接操作 OLE 属性需要了解底层 COM 接口。对于大多数场景，默认标题已足够。

## 步骤 5：常见问题及规避方法

| 问题 | 产生原因 | 解决方案 |
|-------|----------------|-----|
| 按钮未在 Word 中显示 | 文档已保存为 `.docx`，但在会剥离 OLE 控件的查看器中打开（例如 Google Docs）。 | 在 Microsoft Word 或具有编辑权限的 Word Online 中打开文件。 |
| 运行时错误 `ArgumentOutOfRangeException` | `Rectangle` 坐标超出页面边距。 | 使用页面尺寸范围内的数值（例如 A4 为 0‑500）。 |
| 许可证异常 | 试用许可证在 30 天后过期。 | 加载有效的许可证文件或向 Aspose 请求延长试用。 |

## 步骤 6：此示例在更大自动化项目中的作用

当您需要大规模 **how to add form controls to Word document**（例如生成数百个合同模板）时，可将插入逻辑封装为可重用的方法：

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

随后，您可以在处理数据行的循环中调用 `AddCommandButton`，确保每个生成的文档都包含唯一命名的按钮（例如 `Approve_001`、`Approve_002`）。

## 结论

现在您已经拥有完整的 **insert OleControlType.CommandButton example**，演示了使用 Aspose.Words for .NET **how to add form controls to a Word document**。本教程涵盖了项目设置、完整源代码、定制技巧以及常见故障排除步骤。

接下来您可以探索：

- 添加其他控件类型，例如 **CheckBox** 或 **ComboBox**（`OleControlType.CheckBox`、`OleControlType.ComboBox`）。  
- 将按钮绑定到 VBA 宏，以实现更丰富的交互性。  
- 从同一文档生成 PDF，同时保留表单字段。

尝试不同的尺寸、位置和控件名称，以适应您的具体使用场景。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [在 Word 文档中插入组合框表单字段](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [在 Word 文档中插入复选框表单字段](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [在 Word 文档中插入文本输入表单字段](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}