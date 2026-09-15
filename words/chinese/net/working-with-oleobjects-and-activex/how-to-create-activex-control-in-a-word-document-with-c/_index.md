---
category: general
date: 2026-09-14
description: 使用 C# 在 Word 文档中创建 ActiveX 控件。学习如何插入 ActiveX、添加交互按钮，并以编程方式生成 .docx 文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: zh
lastmod: 2026-09-14
og_description: 使用 C# 在 Word 文档中创建 ActiveX 控件。请参考完整示例，了解如何插入 ActiveX、添加交互按钮并保存文件。
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: 使用 C# 在 Word 中创建 ActiveX 控件 – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: 如何使用 C# 在 Word 文档中创建 ActiveX 控件
url: /zh/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 C# 在 Word 文档中创建 ActiveX 控件

如果您需要在 Microsoft Word 文件中 **创建 ActiveX 控件**，本指南将向您展示一个完整、可直接运行的解决方案。您将看到如何插入 ActiveX CommandButton、设置其属性，并仅使用 C# 代码保存生成的 `.docx` 文件。

在 Word 文档中添加交互式按钮是常见需求，尤其是当您希望最终用户直接从文档 UI 触发宏或自定义逻辑时。下面的示例演示了 **如何插入 ActiveX**，无需依赖第三方工具，并且还涵盖了 **如何以编程方式创建 Word 文档**。

通过本教程，您将能够 **使用代码创建按钮**，自定义其标题，并生成一个可携带的 Word 文件，保留 ActiveX 控件。

## 前置条件

- .NET 6.0 或更高版本（Aspose.Words for .NET 库兼容 .NET Core 和 .NET Framework）
- 对 `Aspose.Words` NuGet 包的引用  
  ```bash
  dotnet add package Aspose.Words
  ```
- 基本的 C# 和面向对象编程知识

## 步骤 1：设置项目并导入命名空间

创建一个新的控制台项目（或将代码集成到任何现有的 C# 应用程序中）。导入所需的命名空间，以便编译器能够定位 Word 处理类。

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **此步骤重要原因** – `Aspose.Words` API 提供了 `Document`、`DocumentBuilder` 和 `Forms2OleControl` 类，使您能够在对象层面操作 Word 文件。如果没有这些引用，其余代码将无法编译。

## 步骤 2：创建新的 Word 文档和 DocumentBuilder

`Document` 对象表示整个 `.docx` 包，而 `DocumentBuilder` 提供了用于插入内容的流畅 API。

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **说明** – 实例化一个新的 `Document` 为您提供了一个干净的画布。构建器的光标位于第一节的开头，准备进行下一次插入。

## 步骤 3：插入 ActiveX CommandButton

使用 `InsertForms2OleControl` 在特定位置放置 ActiveX 控件。该方法需要控件类型，以及定义 X/Y 坐标和大小（以点为单位）的 `RectangleF`。

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **此方法有效的原因** – `OleControlType.CommandButton` 告诉 API 创建标准的 Windows CommandButton。矩形相对于页面左上角定位按钮，使您能够在需要的确切位置 **添加交互式按钮**。

## 步骤 4：配置按钮属性

现在设置按钮的可见文本（`Caption`）和内部名称（`Name`）。这些属性是用户看到的内容，也是 VBA 代码以后可以引用的对象。

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **实用技巧** – `Name` 必须在文档内唯一；否则，VBA 宏可能会引用错误的控件。

## 步骤 5：保存文档

最后，将文件写入磁盘。ActiveX 控件存储在 Word 包内部，因此保存的文件在 Microsoft Word 中打开时将保留完整功能。

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **结果** – 在 Word 中打开 `CommandButton.docx` 时，会显示一个标有 “Click Me” 的可点击 CommandButton。可以通过 Word UI（`Developer → Design Mode → Properties`）将该控件链接到宏。

## 完整源码列表

将所有步骤组合在一起即可得到一个可复制、粘贴并运行的完整独立程序。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### 预期输出

运行程序会打印一行确认信息：

```
Document saved to C:\Temp\CommandButton.docx
```

当您在 Microsoft Word 中打开生成的文件时，会看到一个位于指定坐标的 **CommandButton**。在设计模式下单击按钮会高亮显示；在运行模式下，它的行为与任何标准 ActiveX 按钮相同。

## 常见变体和边缘情况

| 场景 | 调整 |
|----------|------------|
| **不同的控件类型** | 将 `OleControlType.CommandButton` 替换为 `OleControlType.CheckBox`、`OleControlType.OptionButton` 等。 |
| **多个按钮** | 多次调用 `InsertForms2OleControl`，为每个新按钮更新 `RectangleF` 坐标。 |
| **动态尺寸** | 根据页面大小（`builder.PageSetup.PageWidth`）计算矩形尺寸。 |
| **保存到流** | 当需要从 Web API 返回文件时，使用 `document.Save(stream, SaveFormat.Docx)`。 |
| **Word 97‑2003 格式** | 将保存格式更改为 `SaveFormat.Doc`，以生成仍嵌入 ActiveX 控件的 `.doc` 文件。 |

> **专业提示**：始终在目标版本的 Word 上测试生成的文档，因为旧版本可能默认启用安全设置，导致 ActiveX 控件被禁用。

## 常见问题

**此方法在 .NET Core 上可用吗？**  
是的。Aspose.Words 库是跨平台的，完全兼容 .NET Core 和 .NET 5/6+。

**我可以通过代码为按钮分配宏吗？**  
API 并不直接嵌入 VBA 代码。文档生成后，在 Word 中打开，启用 Developer 选项卡，然后录制或编写引用 `btnClick` 的宏。

**如果按钮未出现怎么办？**  
检查 Word 中是否启用了 `Developer` 选项卡，并且文档未在 **受保护视图** 中打开。同时确认矩形坐标在页面边距范围内。

## 结论

现在，您已经了解了如何使用 C# 在 Word 文件中 **创建 ActiveX 控件**。本教程涵盖了 **如何插入 ActiveX**，演示了 **添加交互式按钮**，展示了 **从头创建 Word 文档**，并说明了 **使用代码创建按钮**，该按钮在保存后仍然存在。  

接下来，您可以探索更多的 ActiveX 类型，将按钮连接到 VBA 宏，或将逻辑嵌入更大的文档生成服务中。尝试不同的尺寸、位置和控件属性，以实现所需的用户体验。

---

## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方式。

- [创建新 Word 文档](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [在 Word 文档中创建 VBA 项目](/words/english/net/working-with-vba-macros/create-vba-project/)
- [在 Aspose.Words for .NET 中创建并样式化 Word 文档](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}