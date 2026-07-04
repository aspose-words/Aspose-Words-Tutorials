---
category: general
date: 2026-04-21
description: Aspose.Words を使用して Office の数式 LaTeX をすばやく保存する – また、Word のプレーンテキストの保存方法と、Word
  の数式を一括で LaTeX にエクスポートする方法も学べます。
draft: false
keywords:
- save office math latex
- save word plain text
- export word equations latex
- convert word math latex
- convert word equations mathml
language: ja
og_description: Officeの数式LaTeXをすぐに保存；Wordの数式をLaTeXにエクスポートし、C# の Aspose.Words で Word
  の数式 LaTeX に変換する方法を学ぶ。
og_title: Office Math LaTeX を保存 – Word の数式を LaTeX にエクスポート
tags:
- Aspose.Words
- C#
- LaTeX
title: Office Math LaTeX を保存 – C# で Word の数式を LaTeX にエクスポート
url: /ja/net/programming-with-officemath/save-office-math-latex-export-word-equations-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# save office math latex – Aspose.Words を使用して Word 方程式を LaTeX にエクスポート

Ever needed to **save office math latex** from a `.docx` file but weren’t sure where to start? You’re not alone, and the good news is the solution is pretty straightforward. In this guide we’ll walk through the exact steps to export Word equations latex (and even MathML) using Aspose.Words for .NET, all while showing you how to **save word plain text** alongside the math.

`.docx` ファイルから **save office math latex** を取得したいが、どこから始めればよいか分からないことはありませんか？ あなたは一人ではありませんし、解決策はかなりシンプルです。このガイドでは、Aspose.Words for .NET を使用して Word 方程式の LaTeX（場合によっては MathML）をエクスポートする正確な手順を説明し、数式と一緒に **save word plain text** を取得する方法も示します。

We’ll cover everything you might wonder about: why you’d choose LaTeX over other formats, how to configure the `TxtSaveOptions`, and what to do if you need to **convert word math latex** to another representation. By the end you’ll have a runnable snippet that takes a Word document with Office Math objects and drops a clean `.txt` file containing LaTeX (or MathML) equations. No external tools, no manual copy‑pasting—just clean C# code you can drop into any project.

## 前提条件

- **Aspose.Words for .NET** (v23.10 以降)。NuGet パッケージは `Aspose.Words` です。
- .NET 開発環境 (Visual Studio、Rider、または C# 拡張機能付き VS Code)。
- Office Math エディタで作成された少なくとも 1 つの方程式を含む Word ファイル（`.docx`）。
- C# の基本構文に慣れていること—特別なことは不要で、通常の `using` 文だけです。

If you already have those boxes checked, great—let’s dive in.

## Step 1 – **save office math latex** オプションの設定

The first thing you need to do is tell Aspose.Words how you want the mathematical content to be rendered. The `TxtSaveOptions` class has an `OfficeMathExportMode` property that accepts three values: `LaTeX`, `MathML`, or `Text`. For our primary goal we’ll pick `LaTeX`.

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

**Why this matters:** When you set `OfficeMathExportMode` to `LaTeX`, each equation is transformed into its raw LaTeX source. That source can later be compiled with any LaTeX engine, giving you pixel‑perfect typesetting without the need to re‑type the formulas.

> **Pro tip:** If you ever need to **convert word equations mathml**, just swap the enum value to `OfficeMathExportMode.MathML`. The rest of the code stays the same.

## Step 2 – Load the Word document (the **save word plain text** scenario)

Next, we load the source `.docx`. This step is identical whether you’re only interested in plain‑text extraction or you also want the equations in LaTeX.

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

**What’s happening here?** The `Document` constructor reads the file into memory. The quick check with `GetChildNodes` helps you catch a common edge case—trying to export LaTeX from a file that contains no equations. It’s a tiny safeguard that saves you a puzzling empty output later.

## Step 3 – **save office math latex** をプレーンテキストファイルに保存

Now we finally write the file. The `Save` method respects the `TxtSaveOptions` we configured earlier, so the resulting `.txt` will contain both regular text and LaTeX snippets for each equation.

```csharp
// Define the output path
string outputPath = @"C:\MyDocs\Equations.txt";

// Save the document as plain text, with LaTeX equations embedded
doc.Save(outputPath, txtOptions);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

When you open `Equations.txt` you’ll see something like:

```
This is a sample paragraph.

\begin{equation}
E = mc^2
\end{equation}

Another paragraph follows.
```

The LaTeX blocks are wrapped in `\begin{equation}` … `\end{equation}` automatically, which makes them ready for inclusion in any LaTeX document.

## Step 4 – Alternative: LaTeX の代わりに **convert word equations mathml** を使用

If your downstream toolchain prefers MathML (for example, a web page that renders equations with MathJax), just change the export mode:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
doc.Save(@"C:\MyDocs\EquationsMathML.txt", txtOptions);
```

The output will now contain XML‑style MathML tags, like:

```xml
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>E</mi>
  <mo>=</mo>
  <mi>m</mi>
  <msup><mi>c</mi><mn>2</mn></msup>
</math>
```

That’s the quick way to **convert word equations mathml** without writing a custom parser.

## Step 5 – Bonus: **save word plain text** を取得しつつ数式を別に保持

Sometimes you want a clean text version of the document *without* any LaTeX or MathML embedded. You can achieve that by switching the export mode to `Text` and running a second save pass:

```csharp
// Export pure plain text (no math markup)
txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
doc.Save(@"C:\MyDocs\PlainDocument.txt", txtOptions);
```

Now you have three files side‑by‑side:

| ファイル                         | 内容                               |
|--------------------------------|------------------------------------|
| `Equations.txt`                | プレーンテキスト **+** LaTeX 方程式 |
| `EquationsMathML.txt`          | プレーンテキスト **+** MathML 方程式 |
| `PlainDocument.txt`            | 純粋なテキスト、数式は除去         |

This pattern is handy when you need to feed the plain text into a search index while still preserving the original math for academic publishing.

## 完全動作例（コピー＆ペースト可能）

Below is the complete program you can compile and run as is. It demonstrates **save office math latex**, **export word equations latex**, **convert word math latex**, and **save word plain text**—all in one tidy script.

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

**Expected result:** After running, you’ll find three text files in `C:\MyDocs`. Open `Equations.txt` and you’ll see LaTeX blocks; `EquationsMathML.txt` will contain MathML; `PlainDocument.txt` will be free of any equation markup.

## よくある質問とエッジケース

- **What if I only need LaTeX for a subset of equations?**  
  Use the `OfficeMath` node API to iterate over each equation, export it manually with `MathConverter`, and replace the placeholder text where you want. That approach gives you fine‑grained control but adds a few extra lines of code.

- **Does this work with .NET Core / .NET 5+?**  
  Absolutely. Aspose.Words is cross‑platform, so the same code runs on Windows, Linux, and macOS as long as the runtime version matches the library’s requirements.

- **Can I change the LaTeX wrapper (`\begin{equation}`) to something else?**  
  Yes. Set `txtOptions.OfficeMathExportMode = OfficeMathExportMode.LaTeX` and then modify `txtOptions.MathExportSettings` (available in newer releases) to customize delimiters.

- **Performance concerns for huge documents?**  
  The library streams the output, so memory usage stays modest. However

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}