---
category: general
date: 2026-09-05
description: 学习如何创建组形状的 docx、插入 ActiveX 命令按钮，并使用完整的 C# 示例将 Markdown 加载到 Word 文档中。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: zh
lastmod: 2026-09-05
og_description: 使用 C# 创建分组形状的 docx，插入 ActiveX 命令按钮，并将 Markdown 加载到 Word 文档中。请按照本分步教程操作。
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: 创建组形状 docx 并嵌入 ActiveX 控件 – C# 指南
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: 如何在 C# 中创建组形状 docx 并添加交互式控件
url: /zh/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中创建组形状 docx 并添加交互式控件

如果您需要以编程方式 **创建 group shape docx** 文件，本指南将一步步展示具体做法。您还将看到如何 **插入 ActiveX 命令按钮** 控件以及 **将 Markdown 加载到 Word 文档** 中而不丢失下划线格式。教程结束时，您将拥有一个完整功能的 `.docx`，它结合了矢量图形、交互式 UI 元素和基于 Markdown 的内容。

本教程假设您已经具备基本的 C# 开发环境，并已安装 Aspose.Words for .NET 库。无需任何外部工具——所有操作都在标准的 .NET 控制台或桌面应用程序中完成。

## 前置条件

- .NET 6.0 SDK 或更高版本（代码同样适用于 .NET Framework 4.7+）
- Aspose.Words for .NET（NuGet 包 `Aspose.Words`）
- 有效的 X.509 证书（`.pfx`），如果您想测试签名步骤
- 一张图片文件（例如 `logo.png`）和一个 Markdown 文件（`sample.md`），放置在已知文件夹中

> **专业提示：** 将所有输入文件放在同一个 *resources* 文件夹中，以简化相对路径的使用。

## 步骤 1：设置项目并导入命名空间

创建一个新的控制台项目并添加所需的 `using` 指令。此代码块还演示了如何引用后续将使用的 Aspose.Words 类。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

`using` 语句让您可以直接访问 `Document`、`DocumentBuilder`、`GroupShape`、`Forms2OleControl` 等在本教程中使用的类型。

## 步骤 2：**创建 group shape docx** – 添加包含子元素的组形状

*组形状* 允许您将多个绘图对象视为一个单元进行处理。这对于一起移动或缩放相关图形非常有用。

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**为什么使用组形状？**  
将矩形和椭圆分组后，用户在 Word 中拖动时它们会保持对齐。并且后续操作（如统一设置边框或以编程方式移动整个图形）也会更简便。

## 步骤 3：插入纯文本内容控件（用于用户输入的占位符）

内容控件为最终用户提供一个结构化的文本输入区域。占位符文本在用户开始输入后会消失。

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

`PlaceholderName` 属性决定 Word 显示的浅灰色提示。用户可以用自己的文本替换它，底层 XML 仍保持良好结构。

## 步骤 4：**插入 ActiveX 命令按钮** – 为文档添加交互式 UI

ActiveX 控件仍然在现代 Word 文件中受支持，可触发宏或外部自动化。下面我们添加一个 *command button* 并设置其标题。

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**何时使用 ActiveX 按钮？**  
如果文档在依赖 VBA 宏的企业环境中分发，ActiveX 按钮可以启动宏或外部应用程序。若需纯 HTML 交互，建议改用带 *Office.js* 的 *content controls*。

## 步骤 5：插入隐藏图片（例如徽标），用于品牌或后续脚本访问

隐藏形状不会在打印文档中显示，但会保留在 XML 中，便于以后通过代码检索。

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## 步骤 6：**将 markdown 加载到 Word 文档**，同时保留下划线格式

Aspose.Words 可以直接导入 Markdown。启用 `ImportUnderlineFormatting` 可确保 markdown 下划线（`<u>` 或 `__text__`）转换为 Word 的下划线样式，而不是普通文本。

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**边缘情况：** 如果 markdown 文件包含表格，它们会自动转换为 Word 表格。若需要自定义表格样式，可在插入后使用 `DocumentBuilder` 进行设置。

## 步骤 7：使用 XAdES‑EPES 对文档签名（可选安全步骤）

数字签名保证文档完整性。下面的代码使用 XAdES‑EPES 配置对 **create group shape docx** 文件进行签名。

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **安全提示：** 将证书密码从源代码管理中剔除。生产环境请使用环境变量或安全保管库。

## 完整可运行示例

将所有步骤组合在一起即可得到一个独立的程序。将文件保存为 `Program.cs` 并在命令行运行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

运行程序后会生成 `CompleteGroupShape.docx`，其中包含：

- 一个组合的矩形 + 椭圆（**create group shape docx** 的核心）
- 带占位符文本的纯文本内容控件
- 标题为 “Click Me” 的 **insert ActiveX command button**
- 一个隐藏的徽标图片
- 保留下划线的 Markdown 内容
- （如果提供证书）XAdES‑EPES 数字签名

## 常见问题与故障排除

| 问题 | 答案 |
|---|---|
| **ActiveX 按钮在 macOS Word 上能工作吗？** | macOS Word 不支持 ActiveX 控件。按钮会显示为静态图片。跨平台交互请使用带 Office.js 的内容控件。 |
| **如果 markdown 文件包含自定义 CSS 会怎样？** | Aspose.Words 会忽略 CSS，只处理标准 markdown 语法。需要手动将 CSS 样式转换为 Word 样式。 |
| **我可以以后向同一组中添加更多形状吗？** | 可以。通过名称或索引获取 `GroupShape`，然后调用 `AppendChild(newShape)`。修改后记得重新保存文档。 |
| **如何更改签名算法？** | 在调用 `Sign` 之前设置 `signature.SignatureAlgorithm`。默认是 SHA‑256，满足大多数合规要求。 |
| **隐藏图片在 Word UI 中可见吗？** | 不可见，但可以通过在 Word 选项中启用 *显示隐藏文本* 来显示。这对存储元数据而不影响布局很有用。 |

## 后续步骤

既然您已经能够 **create group shape docx**、**insert ActiveX command button**，以及 **load markdown into a Word document**，可以进一步探索：

- **嵌入 VBA 宏**，响应 ActiveX 按钮的点击事件。  
- **为 markdown 生成的段落应用自定义样式**。  
- **使用 `doc.Save("output.pdf", SaveFormat.Pdf)` 将同一文档导出为 PDF**。  
- **批量处理**：将多个 markdown 文件自动合并为单一报告。

这些扩展让您能够构建完整的文档流水线，结合丰富图形、交互控件和基于 markdown 的创作——全部使用 C# 实现。

---

*祝编码愉快！如果您觉得本教程

## 接下来该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方案。每个资源都提供完整的可运行代码示例和逐步解释。

- [使用 Aspose.Words for .NET 在 Word 文档中创建组形状](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 C# 在 Word 中创建矩形形状 – 步骤指南](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [从 Word 创建 Markdown – 完整 C# 指南](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}