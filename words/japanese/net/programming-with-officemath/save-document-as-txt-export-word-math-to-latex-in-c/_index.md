---
category: general
date: 2026-04-24
description: Aspose.Words を使用してドキュメントを txt として保存し、Word を LaTeX に変換します。Word の数式を LaTeX
  にすばやくエクスポートする方法を学びましょう。
draft: false
keywords:
- save document as txt
- convert word to latex
- convert word equations to latex
- export word math latex
language: ja
og_description: C# を使用して文書を txt として保存し、Word の数式を LaTeX に変換します。コード付きのステップバイステップ完全ガイド。
og_title: 文書をTXTとして保存 – Wordの数式をLaTeXへエクスポート
tags:
- Aspose.Words
- C#
- LaTeX
title: 文書をTXTとして保存 – C#でWordの数式をLaTeXにエクスポート
url: /ja/net/programming-with-officemath/save-document-as-txt-export-word-math-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ドキュメントをTXTとして保存 – C#でWordの数式をLaTeXにエクスポート

高度な数式をそのまま残したまま、**save document as txt**したいことはありませんか？ あなただけではありません。Word の組み込み「プレーンテキストとして保存」は Office Math をすべて破棄し、読めない文字化けになってしまいます。 もし数式を保持しつつ、きれいな LaTeX に変換できたらどうでしょうか？

このチュートリアルでは、Aspose.Words for .NET を使用して **Word を LaTeX 対応テキスト** に変換する正確な手順を解説します。 最終的に、すべての数式が正しい LaTeX マークアップとして表現された `.txt` ファイルが手に入ります。 論文や Markdown ファイルにそのまま貼り付けられます。 外部コンバータは不要、手動でコピー＆ペーストする必要もありません—C# の数行で完了します。

## What You’ll Learn

- Aspose.Words で `.docx` ファイルを読み込む方法
- `TxtSaveOptions` を構成して Office Math を LaTeX としてエクスポートする方法
- 任意のエディタで開けるプレーンテキストファイルとして保存する手順
- インライン数式とディスプレイ数式のエッジケース処理、複数ドキュメントを一括処理するための簡単なヒント

### Prerequisites

- .NET 6.0 以降（.NET Framework 4.6+ でも動作します）
- Aspose.Words for .NET NuGet パッケージ（`Install-Package Aspose.Words`）
- 少なくとも 1 つの数式（Office Math オブジェクト）を含む Word ドキュメント

---

## Step 1: Install Aspose.Words and Set Up the Project

まず、ライブラリをプロジェクトに追加します。ソリューションフォルダーでターミナルを開き、次のコマンドを実行してください。

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Visual Studio の NuGet パッケージマネージャ UI でも同様に「Aspose.Words」を検索してインストールできます。

次に新しいコンソールアプリを作成するか、既存プロジェクトにコードを貼り付けます。必要な `using` ディレクティブは以下の通りです。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

これにより `Document` クラスと `TxtSaveOptions` 型がスコープに入ります。

## Step 2: Load the Source Document

Aspose.Words に数式が埋め込まれた Word ファイルの場所を指定します。`YOUR_DIRECTORY/input.docx` を実際のパスに置き換えてください。

```csharp
// Load the source .docx file
Document doc = new Document(@"C:\MyDocs\input.docx");
```

> **Why this matters:** ドキュメントを読み込むことで、Aspose.Words は内部の Office Math オブジェクトへフルアクセスできるようになります。単純なテキストエクスポートでは取得できない情報です。

## Step 3: Configure TxtSaveOptions for LaTeX Export

`TxtSaveOptions` オブジェクトで魔法が起きます。`OfficeMathExportMode` を `LaTeX` に設定するだけで、すべての数式が LaTeX 形式に変換されます。

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

> **What if you need MathML instead?** `OfficeMathExportMode` を `MathML` に変更してください。同じ API が複数の出力形式をサポートしています。

## Step 4: Save the Document as Plain‑Text

いよいよファイルを書き出します。生成される `Math.txt` には通常のテキストに加えて、各数式の LaTeX フラグメントが含まれます。

```csharp
// Save the document as a .txt file with LaTeX equations
doc.Save(@"C:\MyDocs\Math.txt", txtOptions);
Console.WriteLine("Document saved as txt with LaTeX equations.");
```

プログラムを実行すると、次のような内容のファイルが作成されます。

```
This is a simple paragraph.

Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{0}^{\infty} e^{-x} \, dx = 1
\]
```

インライン数式は `$…$` で囲まれ、ディスプレイ数式は `\[` と `\]` でラップされていることに注目してください。これは標準的な LaTeX の慣例で、Aspose.Words が自動的に行ってくれます。

## Step 5: Verify the Output (Optional)

LaTeX が正しく生成されているか確認したい場合は、`.txt` を `pdflatex` などの LaTeX コンパイラや Overleaf のようなオンラインレンダラに渡してみてください。エラーなくコンパイルでき、数式が Word と同じように表示されれば成功です。

```bash
pdflatex Math.txt
```

「Undefined control sequence」エラーが出た場合は、埋め込む先の LaTeX 文書のプリアンブルに必要なパッケージ（例: `amsmath`）が含まれているか確認してください。

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

Aspose.Words は Word 内のレイアウトに基づいて自動的に数式タイプを判別します。特定のスタイルに強制したい場合は、出力後に後処理を行うことができます。

```csharp
string txt = File.ReadAllText(@"C:\MyDocs\Math.txt");
txt = txt.Replace("$", "\\(").Replace("$", "\\)"); // forces inline math delimiters
File.WriteAllText(@"C:\MyDocs\Math_fixed.txt", txt);
```

### Exporting to Other Formats

LaTeX が目的でない場合は、エクスポートモードを切り替えるだけです。

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML; // for MathML
```

HTML に埋め込んで MathML を使用したい場合は、`HtmlSaveOptions` を利用してください。

---

## Full Working Example

以下はそのまま実行可能な完全サンプルです。`.NET` コンソールプロジェクトの `Program.cs` にコピー＆ペーストしてください。

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

プログラムを実行（`dotnet run`）し、`Math.txt` を開くと、Word の内容が LaTeX 数式とともにそのまま表示されます。

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

You now know how to **save document as txt** while preserving every equation as clean LaTeX markup. This approach lets you **convert Word to LaTeX** without third‑party tools, and it scales from a single file to whole folders. Next, you might explore **convert word equations to LaTeX** for batch processing, or dive into **export word math latex** for HTML or Markdown pipelines.

Feel free to experiment—swap `OfficeMathExportMode` for MathML, tweak line‑break handling, or integrate this snippet into a larger document‑generation workflow. Happy coding, and may your equations always render perfectly!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}