---
category: general
date: 2026-03-21
description: 学习如何通过将 Word DOCX 转换为 TXT 来导出 LaTeX，并保留公式。一步一步的 C# 指南，教你从 Word 导出公式。
draft: false
keywords:
- how to export latex
- convert docx to txt
- export equations from word
- save docx as txt
- convert word equations latex
language: zh
og_description: 如何从 Word 导出 LaTeX？本教程展示了如何使用 C# 将 DOCX 转换为 TXT，同时保留公式为 LaTeX。
og_title: 如何从 Word 导出 LaTeX – 快速 DOCX 转 TXT 指南
tags:
- C#
- Aspose.Words
- LaTeX
- DOCX
- Text Export
title: 如何从 Word 导出 LaTeX —— 将 DOCX 转换为含公式的 TXT
url: /zh/net/programming-with-txtsaveoptions/how-to-export-latex-from-word-convert-docx-to-txt-with-equat/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何从 Word 导出 LaTeX – 将 DOCX 转换为带公式的 TXT

是否曾经想过 **如何导出 LaTeX** 从 Word 文档而无需手动复制每个公式？你并不是唯一的。大多数开发者在需要将公式从 *.docx* 中提取并输入到支持 LaTeX 的流水线时都会遇到障碍。  

好消息是？只需几行 C# 代码并使用正确的保存选项，你就可以 **convert docx to txt**，并让每个 Office Math 公式以干净的 LaTeX 形式呈现。在本指南中，我们将逐步演示具体操作，解释每个设置为何重要，并展示你可以在几秒钟内验证的最终结果。

## 本教程涵盖内容

我们先列出前置条件（只需 Aspose.Words for .NET 库）。随后进入三步流程：

1. 加载源 *.docx* 文件。  
2. 配置 `TxtSaveOptions` 以让 Office Math 导出为 LaTeX。  
3. 将文档保存为纯文本文件。

完成后，你将了解 **how to export latex**，熟悉 **export equations from word**，并拥有一段可在任何 C# 项目中直接使用的可复用代码片段。  

*为什么要在意？* 如果你生成科学报告、作业或任何后续需要使用 LaTeX 编译的内容，自动化导出可以节省大量复制粘贴的时间，并消除格式错误。

## 前置条件

- .NET 6.0 或更高版本（代码同样适用于 .NET Core 和 .NET Framework）。  
- Aspose.Words for .NET（免费试用版或正式授权版）。通过 NuGet 安装：

```bash
dotnet add package Aspose.Words
```

- 一个包含至少一个 Office Math 公式的 Word 文档（`input.docx`）。

> **专业提示：** 如果手头没有 DOCX，创建一个新 Word 文件，使用 *Insert → Equation* 插入公式，然后保存为 `input.docx`。

## 步骤 1：加载要导出的源文档

首先需要一个指向待转换文件的 `Document` 实例。`Document` 类抽象了整个 Word 文件，让我们能够访问段落、表格以及——最关键的——Office Math 对象。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Step 1: Load the source DOCX file
Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

> **为何重要：** 加载文件会在内存中创建文档的表示，保存引擎可以遍历它。没有这个对象，就没有可导出的内容，后续的选项也将失效。

## 步骤 2：配置文本保存选项，以 LaTeX 方式导出 Office Math

魔法就在 `TxtSaveOptions` 中。默认情况下，保存为纯文本会剔除所有非文本内容，包括公式。将 `OfficeMathExportMode` 设置为 `LaTeX`，即可让 Aspose 将每个 Office Math 节点转换为对应的 LaTeX 代码。

```csharp
// Step 2: Set up save options for LaTeX export
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    // This flag ensures every equation becomes LaTeX code
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};
```

> **内部原理是什么？** Aspose 解析 Office Math 的 XML，映射运算符到 LaTeX 命令，并将结果写入文本流。`OfficeMathExportMode` 枚举还提供 `Unicode` 和 `MathML` 选项，可根据下游工具链选择合适的格式。

## 步骤 3：使用配置好的选项将文档保存为纯文本文件

现在把转换后的内容写入磁盘。`.txt` 扩展名表明是纯文本格式，但由于我们已设置相应选项，文件中会在原公式位置混入常规文本和 LaTeX 代码片段。

```csharp
// Step 3: Export the document to a TXT file with LaTeX equations
doc.Save(@"YOUR_DIRECTORY\Equations.txt", txtSaveOptions);
```

### 预期输出

在任意编辑器中打开 `Equations.txt`，你应该看到类似如下内容：

```
This is a sample paragraph.

Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
\]
```

如果 LaTeX 正好如上所示，说明你已经成功 **save docx as txt**，且保留了所有公式。

## 常见变体与边缘情况

### 批量转换多个文件

如果需要处理一个文件夹中的多个 DOCX 文件，可将上述三步包装在 `foreach` 循环中：

```csharp
string[] files = Directory.GetFiles(@"YOUR_DIRECTORY", "*.docx");
foreach (var file in files)
{
    Document d = new Document(file);
    d.Save(Path.ChangeExtension(file, ".txt"), txtSaveOptions);
}
```

### 处理非公式内容

`TxtSaveOptions` 还能控制换行、编码以及是否保留隐藏文本。例如，强制使用 UTF‑8：

```csharp
txtSaveOptions.Encoding = Encoding.UTF8;
```

### 导出到其他基于文本的格式

如果更倾向于 Markdown 而非原始 TXT，只需更改文件扩展名并可选地微调选项：

```csharp
doc.Save(@"YOUR_DIRECTORY\Equations.md", txtSaveOptions);
```

LaTeX 块保持不变，Markdown 处理器（如 Pandoc）随后即可渲染它们。

## 完整可运行示例

下面是完整的程序代码，可直接复制粘贴到控制台应用中。它包含所有必要的 `using` 语句、错误处理以及解释每行作用的注释。

```csharp
using System;
using System.IO;
using System.Text;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToLatexExport
{
    class Program
    {
        static void Main(string[] args)
        {
            // Adjust these paths to match your environment
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\Equations.txt";

            try
            {
                // 1️⃣ Load the Word document
                Document doc = new Document(inputPath);

                // 2️⃣ Prepare save options – this is where we tell Aspose to export equations as LaTeX
                TxtSaveOptions saveOptions = new TxtSaveOptions
                {
                    OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                    Encoding = Encoding.UTF8          // Ensure Unicode characters survive
                };

                // 3️⃣ Perform the export
                doc.Save(outputPath, saveOptions);

                Console.WriteLine($"✅ Success! LaTeX‑rich text file created at: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Oops – something went wrong: {ex.Message}");
            }
        }
    }
}
```

运行程序，打开生成的 `Equations.txt`，你将看到每个公式都已渲染为 LaTeX——可以直接喂给 LaTeX 编译器或科学出版工作流。

## 常见问答

**此方法适用于旧版本的 Aspose.Words 吗？**  
是的。`OfficeMathExportMode` 属性自 19.8 版本起即已存在。如果你使用的版本更旧，请升级到至少该版本。

**如果我的 DOCX 包含图片怎么办？**  
纯文本导出会按设计丢弃图片。如果需要同时保留图片和 LaTeX，考虑导出为 HTML（`HtmlSaveOptions`），然后后处理 HTML 以提取 LaTeX 块。

**能直接导出为 `.tex` 文件吗？**  
Aspose 并未提供原生的 `.tex` 写入器，但导出后你可以将 `.txt` 重命名为 `.tex`——LaTeX 代码本身是相同的。只需手动添加文档结构（前言、`\begin{document}` 等）即可。

## 结论

现在你已经掌握了 **how to export latex**，通过 **convert docx to txt** 并保持所有公式完整的技巧。三步 C# 代码——加载、配置、保存——涵盖了 **export equations from word** 的核心，且同样适用于批量处理或其他输出格式的场景。  

准备好迎接下一个挑战了吗？尝试对多语言文档执行 **save docx as txt**，或使用 `pdflatex` 等工具将这些 LaTeX 片段转换为 PDF。将 Aspose.Words 与稳健的 LaTeX 工作流相结合，可能性无限。

---

![Diagram showing the flow: DOCX → Aspose.Words → TXT with LaTeX equations](https://example.com/flow-diagram.png "how to export latex flow diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}