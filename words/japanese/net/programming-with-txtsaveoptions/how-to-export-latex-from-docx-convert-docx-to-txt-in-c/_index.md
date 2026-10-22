---
category: general
date: 2026-02-18
description: Aspose.Words C# を使用して DOCX ファイルから LaTeX をエクスポートする方法。このガイドでは、DOCX を TXT
  に変換し、文書を TXT として保存し、LaTeX を迅速にエクスポートする手順を示します。
draft: false
keywords:
- how to export latex
- convert docx to txt
- save document as txt
- how to save txt
- save word as txt
language: ja
og_description: C#でDOCXファイルからLaTeXをエクスポートする方法。DOCXをTXTに変換し、文書をTXTとして保存し、Aspose.WordsでLaTeX出力を取得する方法を学びましょう。
og_title: DOCXからLaTeXへのエクスポート方法 – C#ガイド
tags:
- Aspose.Words
- C#
- LaTeX export
title: DOCXからLaTeXをエクスポートする方法 – C#でDOCXをTXTに変換
url: /ja/net/programming-with-txtsaveoptions/how-to-export-latex-from-docx-convert-docx-to-txt-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX から LaTeX をエクスポートする方法 – C# で DOCX を TXT に変換

Word 文書から **LaTeX をエクスポート** したいけれど、式を手作業でコピーするのは面倒だと思ったことはありませんか？あなただけではありません。多くの科学プロジェクトでは、.docx のソースに数十個もの Office Math 式が含まれており、論文やプレゼンテーション、静的サイト向けに LaTeX に変換する必要があります。朗報です！Aspose.Words for .NET を使えば **docx を txt に変換** でき、すべての式が自動的に LaTeX マークアップに変換されます。

このチュートリアルでは、**文書を txt として保存** する手順、エクスポーターを LaTeX 出力に設定する方法、そしてクリーンな `.txt` ファイルを取得して LaTeX パイプラインに直接流し込むまでを詳しく解説します。外部ツール不要、面倒な後処理不要、C# の数行だけです。

> **得られるもの:** `input.docx` を読み込み、すべての式を LaTeX にエクスポートし、`Math.txt` に書き出す完全な実行可能プログラム。最後には、改行を保持したり大容量ファイルを扱ったりするオプションの調整方法もマスターできます。

## 前提条件

- **Aspose.Words for .NET**（バージョン 23.10 以降）。NuGet から取得できます: `Install-Package Aspose.Words`。
- .NET 6+ ランタイム（コードは .NET Core、.NET Framework、.NET 5/6 でも動作します）。
- Office Math オブジェクトを含む Word 文書（`input.docx`）。
- C# と Visual Studio もしくはお好みの IDE に関する基本的な知識。

これらが揃っていれば、さっそく始めましょう。

## 手順 1: ソース文書を読み込む

まず最初に、ディスク上の .docx ファイルを表す `Document` オブジェクトを取得します。

```csharp
using Aspose.Words;

// Step 1: Load the source document
Document doc = new Document(@"C:\MyProjects\ExportLatexDemo\input.docx");
```

**ポイント:** Aspose.Words は Word ファイル全体の構造（段落、テーブル、式）を単一オブジェクトに抽象化します。一度だけ読み込むことで、I/O を繰り返さずに Office Math オブジェクトを正しく解析させることができます。

> **プロのコツ:** 開発中は絶対パスを使用して「ファイルが見つからない」エラーを防ぎ、本番環境では相対パスまたは設定項目に切り替えましょう。

## 手順 2: LaTeX エクスポート用に TXT 保存オプションを設定

既定ではプレーンテキストに保存すると、単純文字以外はすべて除去されます。式を LaTeX に変換しながら **docx を txt に変換** するようセーバーに指示する必要があります。

```csharp
// Step 2: Create TXT save options and set Office Math export mode to LaTeX
TxtSaveOptions txtSaveOptions = new TxtSaveOptions
{
    // This flag makes every OfficeMath object become LaTeX code.
    OfficeMathExportMode = TxtSaveOptions.OfficeMathExportMode.LaTeX,

    // Optional: keep line breaks as they appear in Word.
    PreserveLineBreaks = true
};
```

**ポイント:** `OfficeMathExportMode` が式のレンダリング方法を決定します。`LaTeX` 列挙値を指定すると、Aspose.Words は各 `OfficeMath` ノードを対応する LaTeX 構文（`\frac{a}{b}`、`\int` など）に変換します。これが無いと、`[Equation]` のようなプレースホルダーが出力されてしまいます。

## 手順 3: 文書をプレーンテキストとして保存

いよいよ出力ファイルを書き込みます。`Save` メソッドは先ほど設定したオプションを尊重します。

```csharp
// Step 3: Save the document as a plain‑text file using the configured options
doc.Save(@"C:\MyProjects\ExportLatexDemo\Math.txt", txtSaveOptions);
```

プログラムが完了したら `Math.txt` を開き、次のような内容が確認できるはずです。

```
Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{0}^{\infty} e^{-x} \,dx = 1
\]
```

これが **txt を保存する方法** です。すべての Office Math ブロックが正しい LaTeX になっています。

## 完全動作サンプル

以下はコンソールアプリにそのまま貼り付けて動作させられる、完成形プログラムです。

```csharp
using System;
using Aspose.Words;

namespace ExportLatexDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Verify input arguments
            if (args.Length < 2)
            {
                Console.WriteLine("Usage: ExportLatexDemo <input.docx> <output.txt>");
                return;
            }

            string inputPath = args[0];
            string outputPath = args[1];

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Configure save options for LaTeX export
            TxtSaveOptions options = new TxtSaveOptions
            {
                OfficeMathExportMode = TxtSaveOptions.OfficeMathExportMode.LaTeX,
                PreserveLineBreaks = true,
                // Optional: set encoding if you need UTF‑8 (default is UTF‑8)
                Encoding = System.Text.Encoding.UTF8
            };

            // 3️⃣ Save as plain‑text (this is where we **convert docx to txt**)
            doc.Save(outputPath, options);

            Console.WriteLine($"✅ Successfully exported LaTeX to \"{outputPath}\"");
        }
    }
}
```

### 実行手順

```bash
dotnet run --project ExportLatexDemo.csproj "C:\Docs\input.docx" "C:\Docs\Math.txt"
```

コンソールにエクスポート完了のメッセージが表示され、`Math.txt` を任意のエディタで開くことができます。

## エッジケースとよくある質問

### 1. 文書に式と同時に画像が含まれている場合は？

`TxtSaveOptions` クラスはテキストコンテンツのみを扱います。画像はプレーンテキストでは表現できないため無視されます。画像付きの混合出力（例: Markdown に埋め込んだ base64 画像）が必要な場合は、代わりに `SaveFormat.Markdown` を使用し、画像変換を別途処理してください。

### 2. カスタム記号が LaTeX で正しく表示されないのはなぜ？

Aspose.Words は多くの Office Math 記号を LaTeX にマッピングしますが、まれに Unicode の特殊記号は文字そのものとして出力されます。そのようなケースでは、簡単な置換処理で対処できます。例:

```csharp
string txt = File.ReadAllText(outputPath);
txt = txt.Replace("ℵ", @"\aleph");
File.WriteAllText(outputPath, txt);
```

### 3. 数百 MB の大容量文書で OutOfMemoryException が発生する。対策は？

- `LoadOptions` に `LoadFormat.Docx` と `MemoryOptimization.MemorySaving` を設定して読み込み時のメモリ使用を抑える。
- 文書をセクション単位で分割し、各セクションを個別にエクスポートして結果を結合する。

```csharp
LoadOptions loadOptions = new LoadOptions { MemoryOptimization = MemoryOptimization.MemorySaving };
Document largeDoc = new Document(inputPath, loadOptions);
```

### 4. LaTeX の前後に付く `$` デリミタを除去したい？

`OfficeMathExportMode` を `TxtSaveOptions.OfficeMathExportMode.LaTeX` に設定したまま、出力後にデリミタを手動で除去すれば OK です。簡単な正規表現で一括削除できます。

```csharp
txt = Regex.Replace(txt, @"\$(.*?)\$", "$1"); // removes inline $…$
```

## 実践的なポイント（E‑E‑A‑T）

- **バージョンに注意:** LaTeX エクスポーターは Aspose.Words 22.5 で導入されました。古いバージョンを使用している場合、`OfficeMathExportMode` プロパティは存在しません。
- **テスト:** 生成された LaTeX は必ずコンパイラ（`pdflatex`、`xelatex` など）で検証してから、パイプラインに流し込みましょう。
- **パフォーマンス:** 式だけが必要な場合は `Document.GetChildNodes(NodeType.OfficeMath, true)` を使って直接抽出し、全文テキスト変換をスキップできます。

## 結論

C# を使って **DOCX から LaTeX をエクスポート** する方法が分かりましたね。`TxtSaveOptions` を設定すれば **docx を txt に変換** でき、**文書を txt として保存** するとすべての式がクリーンな LaTeX マークアップとして出力されます。上記のコードは引数解析、エンコーディング、いくつかの便利なエッジケース対策も含んでいるので、任意の自動化スクリプトにそのまま組み込めます。

次のステップは？このエクスポーターを静的サイトジェネレータと組み合わせてドキュメントサイトを自動構築したり、CI パイプラインでコミットごとに PDF を生成したりしてみましょう。他のエクスポート形式（例: LaTeX を保持したまま Markdown に変換）に興味がある場合は、Aspose.Words の `SaveFormat.Markdown` オプションもチェックしてください。

Happy coding, and may your equations always render flawlessly! 

![Diagram showing the flow from DOCX → Aspose.Words → LaTeX TXT export](https://example.com/images/how-to-export-latex-flow.png "how to export latex flow diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}