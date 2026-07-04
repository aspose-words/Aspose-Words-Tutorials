---
category: general
date: 2026-04-24
description: 将文档保存为 txt 并使用 Aspose.Words 将 Word 转换为 LaTeX。了解如何快速将 Word 数学公式导出为 LaTeX。
draft: false
keywords:
- save document as txt
- convert word to latex
- convert word equations to latex
- export word math latex
language: zh
og_description: 使用 C# 将文档保存为 txt 并将 Word 方程转换为 LaTeX。完整的逐步指南和代码。
og_title: 将文档另存为 TXT – 导出 Word 数学为 LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: 将文档保存为 TXT – 在 C# 中导出 Word 数学为 LaTeX
url: /zh/net/programming-with-officemath/save-document-as-txt-export-word-math-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 保存文档为 TXT – 将 Word 数学公式导出为 LaTeX（C#）

有没有需要 **save document as txt** 并且保留精美公式的情况？你并不是唯一的。Word 内置的“另存为纯文本”会丢弃 Office Math，导致得到不可读的乱码。如果可以保留这些公式，并以干净的 LaTeX 形式输出呢？

在本教程中，我们将逐步演示如何使用 Aspose.Words for .NET 将 Word 转换为可直接使用 LaTeX 的文本。完成后，你将得到一个 `.txt` 文件，其中每个公式都以正确的 LaTeX 标记表示，随时可以粘贴到论文或 markdown 文件中。无需外部转换器，也不需要手动复制粘贴——只需几行 C# 代码。

## 你将学到

- 如何使用 Aspose.Words 加载 `.docx` 文件。
- 配置 `TxtSaveOptions` 以将 Office Math 导出为 LaTeX。
- 将结果保存为普通文本文件，能够在任何编辑器中打开。
- 处理内联与显示公式的边缘情况，并提供批量处理多个文档的快速技巧。

### 前提条件

- .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.6+）。
- Aspose.Words for .NET NuGet 包（`Install-Package Aspose.Words`）。
- 包含至少一个公式（Office Math 对象）的 Word 文档。

---

## Step 1: Install Aspose.Words and Set Up the Project

首先，将库添加到项目中。在解决方案文件夹的终端运行：

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** 如果使用 Visual Studio，NuGet 包管理器 UI 同样方便——搜索 “Aspose.Words” 并点击 Install。

现在创建一个新的控制台应用（或将代码放入已有项目）。你需要的 `using` 指令如下：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

这些指令将 `Document` 类和 `TxtSaveOptions` 类型引入作用域。

## Step 2: Load the Source Document

我们需要让 Aspose.Words 指向包含公式的 Word 文件。将 `YOUR_DIRECTORY/input.docx` 替换为你机器上的实际路径。

```csharp
// Load the source .docx file
Document doc = new Document(@"C:\MyDocs\input.docx");
```

> **Why this matters:** 加载文档后，Aspose.Words 能完整访问内部的 Office Math 对象，而这些对象在普通文本导出时是不可见的。

## Step 3: Configure TxtSaveOptions for LaTeX Export

魔法发生在 `TxtSaveOptions` 对象中。将 `OfficeMathExportMode` 设置为 `LaTeX`，即可将每个公式转换为对应的 LaTeX 表达式。

```csharp
// Configure save options to export Office Math as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // Export all Office Math objects as LaTeX code
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: keep line breaks similar to the original layout
    PreserveTableLayout = true
};
```

> **What if you need MathML instead?** 将 `OfficeMathExportMode` 改为 `MathML`。同一 API 支持多种输出格式。

## Step 4: Save the Document as Plain‑Text

现在将文件写出。生成的 `Math.txt` 将包含普通文本以及每个公式的 LaTeX 片段。

```csharp
// Save the document as a .txt file with LaTeX equations
doc.Save(@"C:\MyDocs\Math.txt", txtOptions);
Console.WriteLine("Document saved as txt with LaTeX equations.");
```

运行程序后会得到类似下面的文件：

```
This is a simple paragraph.

Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{0}^{\infty} e^{-x} \, dx = 1
\]
```

请注意，内联公式使用 `$…$` 包裹，而显示公式则使用 `\[` 和 `\]`。这符合标准 LaTeX 约定，Aspose.Words 会自动完成。

## Step 5: Verify the Output (Optional)

如果想再次确认 LaTeX 的有效性，可以将 `.txt` 输入到 `pdflatex` 等 LaTeX 编译器，或使用 Overleaf 等在线渲染器。文本应当能够无错误编译，公式会与 Word 中的显示完全一致。

```bash
pdflatex Math.txt
```

如果出现 “Undefined control sequence” 错误，请确保在将文本嵌入更大的 LaTeX 文档时，在导言区加入所需的宏包（例如 `amsmath`）。

## Handling Common Variations

### Converting Multiple Files in a Folder

```csharp
string[] files = Directory.GetFiles(@"C:\MyDocs\", "*.docx");
foreach (var file in files)
{
    Document d = new Document(file);
    d.Save(Path.ChangeExtension(file, ".txt"), txtOptions);
}
Console.WriteLine("Batch conversion complete.");
```

### Dealing with Inline vs. Display Equations

Aspose.Words 会根据 Word 中的布局自动检测公式类型。如果需要强制使用特定样式，可以对输出进行后处理：

```csharp
string txt = File.ReadAllText(@"C:\MyDocs\Math.txt");
txt = txt.Replace("$", "\\(").Replace("$", "\\)"); // forces inline math delimiters
File.WriteAllText(@"C:\MyDocs\Math_fixed.txt", txt);
```

### Exporting to Other Formats

如果 LaTeX 不是你的目标，只需切换导出模式：

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML; // for MathML
```

或者如果更喜欢在 HTML 中嵌入 MathML，可以使用 `HtmlSaveOptions`。

---

## Full Working Example

下面是完整的、可直接运行的示例程序。将其复制粘贴到 .NET 控制台项目的 `Program.cs` 中。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToLatexTxt
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source document
            Document doc = new Document(@"C:\MyDocs\input.docx");

            // 2️⃣ Set up save options to export Office Math as LaTeX
            TxtSaveOptions saveOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                PreserveTableLayout = true
            };

            // 3️⃣ Save as plain‑text with LaTeX equations
            string outputPath = @"C:\MyDocs\Math.txt";
            doc.Save(outputPath, saveOptions);

            Console.WriteLine($"✅ Saved document as txt at: {outputPath}");
            Console.WriteLine("Open the file to see LaTeX‑formatted equations.");
        }
    }
}
```

运行程序（`dotnet run`），打开 `Math.txt`，即可看到 Word 内容与 LaTeX 公式完整保留。

---

## Frequently Asked Questions

**Q: Does this work with older .doc files?**  
A: Yes—Aspose.Words can open legacy `.doc` files, but complex equations may be stored as images. In that case the exporter falls back to a placeholder comment.

**Q: What if an equation contains custom symbols?**  
A: Aspose.Words maps most Office Math symbols to standard LaTeX commands. For truly custom symbols you might need to manually edit the generated LaTeX.

**Q: Is the output UTF‑8 encoded?**  
A: By default, `TxtSaveOptions` writes UTF‑8, which is safe for most languages and symbols.

---

## Conclusion

你现在已经掌握了如何 **save document as txt**，同时将每个公式保留为干净的 LaTeX 标记。此方法让你能够 **convert Word to LaTeX** 而无需第三方工具，并且可以从单个文件扩展到整个文件夹。接下来，你可以探索 **convert word equations to LaTeX** 的批量处理，或深入了解 **export word math latex** 在 HTML 或 Markdown 流程中的应用。

欢迎随意实验——将 `OfficeMathExportMode` 换成 MathML，调整换行处理，或将此代码片段集成到更大的文档生成工作流中。祝编码愉快，愿你的公式始终完美渲染！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}