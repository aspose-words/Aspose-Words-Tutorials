---
category: general
date: 2026-10-20
description: 使用 C# 在 Word 文档中设置占位符文本。了解如何使用 Aspose.Words for .NET 快速添加控件并设置占位符。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- how to add control
- how to set placeholder
- generate word c#
language: zh
lastmod: 2026-10-20
og_description: 使用 C# 在 Word 文档中设置占位符文本。本教程展示如何添加控件、设置占位符以及以编程方式生成 Word 文件。
og_image_alt: Screenshot of a Word document showing placeholder text created with
  C# code
og_title: 使用 C# 在 Word 文档中设置占位符文本 – 分步指南
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Set placeholder text in a Word document using C#. Learn how to add
    control and set placeholder quickly with Aspose.Words for .NET.
  headline: Set placeholder text in a Word document using C#
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, and .NET
      6+. The same code runs unchanged.
    question: Does this work with .NET Core?
  - answer: Use `sdt.SetText("Default value")` after creating the SDT. The placeholder
      disappears once a value is set.
    question: Can I set a default value in addition to the placeholder?
  - answer: 'Load the document, locate the SDT by its `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag,
      true)`) and read `sdt.GetText()`. ## Conclusion You now know how to **set placeholder
      text** in a Word document using C#. By creating a plain‑text `StructuredDocumentTag`,
      assigning a title and place'
    question: What if I need to retrieve the entered value later?
  type: FAQPage
tags:
- C#
- Aspose.Words
- Word automation
- Content control
title: 使用 C# 在 Word 文档中设置占位符文本
url: /zh/net/programming-with-sdt/set-placeholder-text-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 文档中使用 C# 设置占位符文本

如果您需要在使用 C# 生成的 Microsoft Word 文件中**设置占位符文本**，本指南将手把手教您如何实现。您将看到一个简洁的端到端解决方案，添加内容控件、定义占位符并保存文档——全部使用 Aspose.Words for .NET。

许多开发者都会好奇**如何向 Word 文档添加控件**或**如何在不手动打开 Word 的情况下设置占位符**。本教程解答这些问题，并演示一种干净的方式来**生成 Word C#**文件，使其准备好接受用户输入。

## 您将完成的目标

完成本教程后，您将能够：

* 以编程方式创建一个空白的 Word 文档。
* 插入一个纯文本的 Structured Document Tag（SDT），即内容控件的技术名称。
* 为 SDT 分配有意义的标题和占位符文本。
* 将生成的 `.docx` 文件保存到磁盘。

无需额外工具，只需 Aspose.Words 库和 .NET 6（或更高）开发环境。

## 前置条件

* 已安装 .NET 6 SDK 或更高版本。  
* Visual Studio 2022（或任何支持 .NET 的 IDE）。  
* Aspose.Words for .NET NuGet 包（`Install-Package Aspose.Words`）。  

> **专业提示：** 如果您只是进行测试，可使用 Aspose.Words 的免费评估版；它会添加水印，但功能与正式授权版相同。

## 第一步：设置项目并导入命名空间

创建一个新的控制台项目并添加所需的 `using` 指令。这些指令会把核心的 Aspose.Words 类和 markup 命名空间引入作用域。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // The complete solution starts here.
        }
    }
}
```

*此步骤的重要性：* 导入 `Aspose.Words.Markup` 可让您访问 `StructuredDocumentTag`、`SdtType` 和 `MarkupLevel`——这些对象是实现**添加控件**和**设置占位符**所必需的。

## 第二步：创建空白文档并实例化 DocumentBuilder

`Document` 代表整个 Word 文件，而 `DocumentBuilder` 提供了一个方便的光标，用于插入元素。

```csharp
// Step 2: Initialize a new empty document.
Document doc = new Document();

// DocumentBuilder starts at the beginning of the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*此步骤的重要性：* 从一个干净的文档开始，可确保您设置的占位符正好出现在预期位置，不会受到已有内容的干扰。

## 第三步：创建内容控件（Structured Document Tag）

在这里我们创建一个纯文本 SDT，给它一个标题，并设置用户在控件为空时看到的占位符文本。

```csharp
// Step 3: Build a plain‑text Structured Document Tag (SDT).
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,                     // Parent document
    SdtType.PlainText,       // Control type – plain text box
    MarkupLevel.Inline);     // Inline placement (behaves like a word)

sdt.Title = "CustomerName";                 // Logical name for the control
sdt.PlaceholderName = "Enter name here";    // Text shown when empty
```

*此步骤的重要性：* `Title` 属性让您以后可以引用该控件（例如进行数据绑定）。`PlaceholderName` 正是您想要显示的**设置占位符文本**，用于引导最终用户。

## 第四步：在当前光标位置插入控件

使用 `DocumentBuilder`，将在构建器当前所在位置插入 SDT。

```csharp
// Step 4: Insert the SDT into the document.
builder.InsertNode(sdt);
```

*此步骤的重要性：* 插入节点会将控件附加到文档的 DOM 中。如果需要添加多个占位符，只需移动构建器的光标并重复此步骤。

## 第五步：保存文档

最后，将文档写入磁盘。将 `YOUR_DIRECTORY` 替换为您机器上的实际路径。

```csharp
// Step 5: Save the .docx file.
string outputPath = @"C:\Temp\SDT.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

当您在 Microsoft Word 中打开 `SDT.docx` 时，会看到一个灰色阴影的行内文本框，显示 **Enter name here**。单击文本框后占位符会消失，用户即可输入客户名称。

### 预期输出

| 文件位置 | 内容预览 |
|----------|----------|
| `C:\Temp\SDT.docx` | 行内占位符 **Enter name here** 位于标题为 *CustomerName* 的纯文本内容控件内部。 |

## 边缘情况与变体

| 情形 | 推荐的调整 |
|------|------------|
| **Multiple placeholders**（多个占位符） | 创建额外的 `StructuredDocumentTag` 对象，使用不同的 `Title` 和 `PlaceholderName` 值，然后在需要的位置插入。 |
| **Rich‑text placeholder**（富文本占位符） | 使用 `SdtType.RichText` 替代 `PlainText`，以允许在占位符内部使用格式。 |
| **Block‑level control**（块级控件） | 将 `MarkupLevel.Inline` 改为 `MarkupLevel.Block`，使控件表现为完整段落。 |
| **Placeholder not visible**（占位符不可见） | 确认 Word 中的视图设置未隐藏内容控件（`文件 → 选项 → 高级 → 显示内容控件`）。 |
| **Saving to a stream**（保存到流） | 如需通过 HTTP 发送文件，可调用 `doc.Save(stream, SaveFormat.Docx)`。 |

## 完整可运行示例

下面是完整的程序代码，您可以直接复制、粘贴并运行。它将上述所有步骤整合在单个 `Main` 方法中。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Position a builder at the start of the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Define a plain‑text content control (SDT) with placeholder text.
            StructuredDocumentTag sdt = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Inline);

            sdt.Title = "CustomerName";                 // Logical identifier
            sdt.PlaceholderName = "Enter name here";    // The placeholder you see in Word

            // 4️⃣ Insert the SDT into the document.
            builder.InsertNode(sdt);

            // 5️⃣ Save the document to disk.
            string outputPath = @"C:\Temp\SDT.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document successfully saved to {outputPath}");
        }
    }
}
```

运行程序，打开生成的文件，即可看到已准备好的占位符文本，等待用户输入。

## 常见问题解答

**问：这在 .NET Core 上能工作吗？**  
答：可以。Aspose.Words for .NET 与 .NET Core、.NET 5 以及 .NET 6+ 兼容，代码无需修改即可运行。

**问：我可以在占位符之外设置默认值吗？**  
答：可以在创建 SDT 后调用 `sdt.SetText("Default value")`。一旦设置了值，占位符会自动消失。

**问：以后如何获取用户输入的值？**  
答：加载文档后，使用 `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` 按 `Title` 定位 SDT，然后读取 `sdt.GetText()`。

## 结论

现在，您已经掌握了如何使用 C# 在 Word 文档中**设置占位符文本**。通过创建纯文本 `StructuredDocumentTag`、分配标题和占位符、使用 `DocumentBuilder` 插入控件并保存文件，您即可**添加控件**并**生成 Word C#**文件。

接下来，您可以进一步探索：

* 添加富文本或下拉列表控件（`SdtType.RichText`、`SdtType.DropDownList`）。  
* 从数据库批量填充多个占位符。  
* 使用 Aspose.Words 将生成的 `.docx` 转换为 PDF。

尝试不同的控件类型和占位符样式，以满足您的应用需求。祝编码愉快！

## 接下来您可以学习什么？

以下教程与本指南紧密相关，帮助您进一步掌握 API 功能并探索其他实现方式：

- [在 Aspose.Words 中设置占位符文本 – 完整 C# 指南](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [使用代码创建 Word 文档 – 添加内容控件和占位符](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [如何添加内容控件并使用 Aspose 创建 Word 文档 – 完整教程](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}