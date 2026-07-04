---
category: general
date: 2026-04-21
description: 使用 Aspose.Words 快速保存 Office 数学 LaTeX —— 还可学习如何一次性保存 Word 纯文本并导出 Word
  公式的 LaTeX。
draft: false
keywords:
- save office math latex
- save word plain text
- export word equations latex
- convert word math latex
- convert word equations mathml
language: zh
og_description: 即时保存 Office 数学 LaTeX；学习导出 Word 方程的 LaTeX 并使用 Aspose.Words 在 C# 中转换
  Word 数学 LaTeX。
og_title: 保存 Office Math LaTeX – 将 Word 方程导出为 LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: 保存 Office Math LaTeX – 在 C# 中将 Word 方程导出为 LaTeX
url: /zh/net/programming-with-officemath/save-office-math-latex-export-word-equations-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# save office math latex – Export Word equations to LaTeX with Aspose.Words

是否曾经需要从 `.docx` 文件中 **save office math latex**，却不知从何入手？你并不孤单，好消息是解决方案相当直接。在本指南中，我们将逐步演示如何使用 Aspose.Words for .NET 导出 Word 方程的 LaTeX（甚至是 MathML），并展示如何 **save word plain text** 与数学公式一起保存。

我们会覆盖你可能会想了解的所有内容：为何选择 LaTeX 而非其他格式、如何配置 `TxtSaveOptions`，以及如果需要 **convert word math latex** 为其他表示形式时该怎么做。阅读完本篇，你将拥有一个可运行的代码片段，能够读取包含 Office Math 对象的 Word 文档，并生成一个干净的 `.txt` 文件，里面包含 LaTeX（或 MathML）方程。无需外部工具，无需手动复制粘贴——只需一段简洁的 C# 代码，随时可放入任意项目。

## Prerequisites

- **Aspose.Words for .NET**（v23.10 或更高）。NuGet 包名为 `Aspose.Words`。
- .NET 开发环境（Visual Studio、Rider，或带 C# 扩展的 VS Code）。
- 一个包含至少一个使用 Office Math 编辑器创建的方程的 Word 文件（`.docx`）。
- 对 C# 语法有基本了解——不需要高级技巧，只需常规的 `using` 语句。

如果这些条件都已满足，太好了——让我们开始吧。

## Step 1 – Set up **save office math latex** options

首先需要告诉 Aspose.Words 你希望如何呈现数学内容。`TxtSaveOptions` 类的 `OfficeMathExportMode` 属性接受三个值：`LaTeX`、`MathML` 或 `Text`。针对我们的主要目标，选择 `LaTeX`。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Configure TXT save options to export equations as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // This line makes the library output LaTeX for every Office Math object
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
    // You could also use OfficeMathExportMode.MathML or .Text here
};
```

**Why this matters:** 当你将 `OfficeMathExportMode` 设置为 `LaTeX` 时，每个方程都会被转换为其原始 LaTeX 源码。该源码随后可以使用任意 LaTeX 引擎编译，获得像素级完美排版，而无需重新手动输入公式。

> **Pro tip:** 如果你需要 **convert word equations mathml**，只需将枚举值改为 `OfficeMathExportMode.MathML`。其余代码保持不变。

## Step 2 – Load the Word document (the **save word plain text** scenario)

接下来，加载源 `.docx`。无论你只想提取纯文本，还是还想获取 LaTeX 方程，这一步都是相同的。

```csharp
// Load the document that contains Office Math objects
Document doc = new Document(@"C:\MyDocs\input.docx");

// Optional: verify that the document actually has equations
bool hasMath = doc.GetChildNodes(NodeType.OfficeMath, true).Count > 0;
if (!hasMath)
{
    Console.WriteLine("Warning: No Office Math objects found in the document.");
}
```

**What’s happening here?** `Document` 构造函数会将文件读取到内存中。使用 `GetChildNodes` 的快速检查可以帮助你捕获一个常见的边缘情况——尝试从不含方程的文件中导出 LaTeX。这个小小的防护措施可以避免后期出现空输出的困惑。

## Step 3 – **save office math latex** to a plain‑text file

现在终于可以写文件了。`Save` 方法会遵循我们之前配置的 `TxtSaveOptions`，因此生成的 `.txt` 将同时包含普通文本和每个方程的 LaTeX 片段。

```csharp
// Define the output path
string outputPath = @"C:\MyDocs\Equations.txt";

// Save the document as plain text, with LaTeX equations embedded
doc.Save(outputPath, txtOptions);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

打开 `Equations.txt` 时，你会看到类似下面的内容：

```
This is a sample paragraph.

\begin{equation}
E = mc^2
\end{equation}

Another paragraph follows.
```

LaTeX 块会自动被包裹在 `\begin{equation}` … `\end{equation}` 中，方便直接嵌入任何 LaTeX 文档。

## Step 4 – Alternative: **convert word equations mathml** instead of LaTeX

如果你的下游工具链更倾向于 MathML（例如在网页中使用 MathJax 渲染方程），只需更改导出模式：

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
doc.Save(@"C:\MyDocs\EquationsMathML.txt", txtOptions);
```

输出现在将包含 XML 风格的 MathML 标签，例如：

```xml
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>E</mi>
  <mo>=</mo>
  <mi>m</mi>
  <msup><mi>c</mi><mn>2</mn></msup>
</math>
```

这就是在不编写自定义解析器的情况下快速 **convert word equations mathml** 的方法。

## Step 5 – Bonus: **save word plain text** while keeping equations separate

有时你只想要文档的纯文本版本，且不希望其中嵌入任何 LaTeX 或 MathML。可以通过将导出模式切换为 `Text` 并执行第二次保存来实现：

```csharp
// Export pure plain text (no math markup)
txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
doc.Save(@"C:\MyDocs\PlainDocument.txt", txtOptions);
```

此时你将拥有并排的三个文件：

| File                         | Contents                               |
|------------------------------|----------------------------------------|
| `Equations.txt`              | Plain text **+** LaTeX equations       |
| `EquationsMathML.txt`        | Plain text **+** MathML equations       |
| `PlainDocument.txt`          | Pure text, equations stripped out      |

当你需要将纯文本送入搜索索引，同时又要保留原始数学公式用于学术出版时，这种模式非常实用。

## Full Working Example (Copy‑Paste Ready)

下面是完整的程序代码，可直接编译运行。它演示了 **save office math latex**、**export word equations latex**、**convert word math latex** 与 **save word plain text** 四项功能，全部集中在一个整洁的脚本中。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure TXT save options for LaTeX export
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        // 2️⃣ Load the source Word document
        string inputPath = @"C:\MyDocs\input.docx";
        Document doc = new Document(inputPath);

        // Quick sanity check for equations
        if (doc.GetChildNodes(NodeType.OfficeMath, true).Count == 0)
        {
            Console.WriteLine("No equations found – proceeding with plain‑text export only.");
        }

        // 3️⃣ Save with LaTeX equations embedded
        string latexPath = @"C:\MyDocs\Equations.txt";
        doc.Save(latexPath, txtOptions);
        Console.WriteLine($"LaTeX export saved to {latexPath}");

        // 4️⃣ Switch to MathML and save (optional)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
        string mathmlPath = @"C:\MyDocs\EquationsMathML.txt";
        doc.Save(mathmlPath, txtOptions);
        Console.WriteLine($"MathML export saved to {mathmlPath}");

        // 5️⃣ Finally, pure plain‑text export (no math markup)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
        string plainPath = @"C:\MyDocs\PlainDocument.txt";
        doc.Save(plainPath, txtOptions);
        Console.WriteLine($"Plain‑text export saved to {plainPath}");
    }
}
```

**Expected result:** 运行后，你将在 `C:\MyDocs` 中看到三个文本文件。打开 `Equations.txt` 可看到 LaTeX 块；`EquationsMathML.txt` 包含 MathML；`PlainDocument.txt` 则没有任何方程标记。

## Common Questions & Edge Cases

- **What if I only need LaTeX for a subset of equations?**  
  使用 `OfficeMath` 节点 API 遍历每个方程，手动通过 `MathConverter` 导出，并在需要的位置替换占位文本。此方法提供了细粒度控制，但会多几行代码。

- **Does this work with .NET Core / .NET 5+?**  
  完全支持。Aspose.Words 是跨平台的，只要运行时版本符合库的要求，代码即可在 Windows、Linux 与 macOS 上运行。

- **Can I change the LaTeX wrapper (`\begin{equation}`) to something else?**  
  可以。设置 `txtOptions.OfficeMathExportMode = OfficeMathExportMode.LaTeX` 后，修改 `txtOptions.MathExportSettings`（在新版中可用）即可自定义分隔符。

- **Performance concerns for huge documents?**  
  库会流式写入输出，内存占用保持在合理范围。不过

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}