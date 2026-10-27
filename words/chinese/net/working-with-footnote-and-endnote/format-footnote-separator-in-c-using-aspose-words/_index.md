---
category: general
date: 2026-08-10
description: 使用 Aspose.Words 在 C# 中格式化脚注分隔线，以自定义脚注和尾注线。几分钟内快速掌握 C# 脚注格式化。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: zh
lastmod: 2026-08-10
og_description: 使用 Aspose.Words 在 C# 中格式化脚注分隔符。遵循本教程，快速可靠地设置脚注和尾注分隔符的样式。
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: 在 C# 中格式化脚注分隔符 – 完整的 Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: 使用 Aspose.Words 在 C# 中格式化脚注分隔符
url: /zh/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words 在 C# 中格式化脚注分隔符

如果您需要在 Word 文档中 **格式化脚注分隔符**，本指南将展示如何使用 Aspose.Words for .NET 实现。您将看到一个完整、可运行的示例，演示如何更改分隔符段落的对齐方式和颜色，并学习如何将相同技术应用于尾注分隔符。

本教程涵盖了从加载源文件到保存修改后文档的每一步，您可以直接复制粘贴代码到自己的项目中，无需额外查找资料。

## 您需要的环境

在开始之前，请确保您具备以下条件：

* .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.6+）
* 有效的 Aspose.Words for .NET 许可证（免费试用可用于评估）
* 包含至少一个脚注或尾注的 Word 文件（例如 `Footnotes.docx`）
* Visual Studio 2022 或您喜欢的任何 C# IDE

准备好这些后，您即可专注于 **C# 脚注格式化** 的逻辑，而无需担心环境配置。

## 第一步：加载包含脚注和尾注的文档

首先创建一个指向源文件的 `Document` 对象。Aspose.Words 会将整个 DOCX 包读取到内存中，从而让您可以完整访问脚注和尾注节点。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*为什么这很重要*：加载文档是进行任何操作的前提。如果文件路径错误，Aspose.Words 会抛出 `FileNotFoundException`，因此请在继续之前确认路径无误。

## 第二步：获取分隔符和续页分隔符节点

脚注和尾注的分隔符存储在 `Footnotes` 和 `Endnotes` 集合中的特殊节点里。每个集合都提供 `Separator` 和 `ContinuationSeparator` 属性，返回 `Node` 引用。

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*为什么这很重要*：`Separator` 节点表示在正文与脚注块之间的视觉分隔线。获取该引用后，您可以修改其段落格式、字体，甚至完全替换该节点。

## 第三步：更改脚注分隔符的视觉样式

在大多数 Word 文档中，分隔符是包含破折号或星号的单个段落。下面的代码检查分隔符是否为 `Paragraph`，如果是，则将其居中并将文字颜色改为灰色。

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### 为续页分隔符设置样式（可选）

当脚注跨越多页时会出现续页分隔符。您可以以类似方式对其进行样式设置：

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*为什么这很重要*：对齐分隔符可以提升可读性，改变颜色则能将其与普通段落文字区分开来。您可以将 `ParagraphAlignment.Center` 替换为 `Left` 或 `Right`，以符合文档的设计规范。

## 第四步：保存修改后的文档

应用完所需样式后，将文档写回磁盘。您可以覆盖原文件，也可以生成新版本。

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

当您在 Microsoft Word 中打开 `Footnotes_Styled.docx` 时，脚注分隔符将居中显示且为灰色，正如代码所指定的那样。

## 高级变体

### 格式化尾注分隔符

如果文档同时使用了尾注，您可以对 `Endnotes` 集合使用相同的逻辑：

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### 使用自定义字符串作为分隔符

有时您希望分隔符是一串星号（`***`）。只需用新 `Run` 替换现有的 runs：

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### 处理没有分隔符节点的文档

极少数情况下文档可能省略了分隔符节点（例如作者手动删除了它）。此时 `document.Footnotes.Separator` 会返回 `null`，需要做好防护：

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## 常见陷阱及规避方法

| 陷阱 | 产生原因 | 解决方案 |
|------|----------|----------|
| **Separator 不是 `Paragraph`** | 某些 Word 模板使用 `Table` 或 `Shape` 作为分隔符。 | 在强制转换前使用 `is Paragraph` 检查节点类型。 |
| **`Runs` 集合为空** | 分隔符可能是一个空段落。 | 在访问 `Runs[0]` 前确认 `Runs.Count > 0`。 |
| **未应用许可证** | 未授权时，Aspose.Words 会插入水印并可能限制 API 使用。 | 在程序入口处调用 `License license = new License(); license.SetLicense("Aspose.Words.lic");`。 |
| **保存到只读文件夹** | `Save` 方法会抛出 `UnauthorizedAccessException`。 | 确保目标目录具有写入权限。 |

提前处理这些问题可避免运行时异常，确保 **修改脚注分隔符** 的过程顺畅。

## 完整、可运行的示例

下面是一个独立的控制台应用程序，演示了上述所有步骤。将代码复制到新的 .NET 控制台项目中，替换文件路径后运行即可。

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**预期结果**  

打开 `Footnotes_Styled.docx` 时：

* 脚注分隔线居中显示在正文下方。  
* 颜色为浅灰色，视觉上与普通段落区分明显。  
* 如果文档包含尾注，它们的分隔符也会居中并呈灰色（或石板灰）。

## 接下来您可以学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方式。

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Set Footnote And Endnote Position](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Working With Footnote And Endnote](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}