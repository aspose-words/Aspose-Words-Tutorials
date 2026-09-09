---
category: general
date: 2026-02-13
description: "DOCX を markdown に変換する際に改行を保持します。  \nWord を markdown として保存する方法、空の段落をエクスポートする方法、そして書式をそのまま保つ方法を学びましょう。"
draft: false
keywords:
- preserve line breaks
- convert docx to markdown
- save word as markdown
- how to export empty
- how to preserve breaks
language: ja
og_description: DOCX を markdown に変換する際に改行を保持します。このガイドでは、Word を markdown として保存し、空の段落を正しくエクスポートする方法を示します。
og_title: '改行を保持: DOCX を Markdown に変換'
tags:
- Aspose.Words
- C#
- Markdown
title: '改行を保持: DOCX を Markdown に変換'
url: /ja/net/programming-with-markdownsaveoptions/preserve-line-breaks-convert-docx-to-markdown/
---

output with all translations.

Let's write.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 行間の保持: DOCX を Markdown に変換する

DOCX ファイルを Markdown に変換するときに **行間を保持** したくなったことはありませんか？ これはよくある問題で、綺麗な Word 文書がテキストの塊になり、意図した空白行が消えてしまいます。 良いニュースは、いくつかのシンプルな設定で空の段落を含むすべての改行を保持できることです。

このチュートリアルでは **Word を Markdown として保存** する全工程を解説します。 ソース文書の読み込みから正しいエクスポートモードの設定まで網羅します。 最後まで読めば、*空の段落をエクスポートする方法*、*複雑なレイアウトで改行を保持する方法* が分かり、コピー＆ペーストできる完全なコードサンプルも手に入ります。 途中で「ドキュメントを参照してください」的な行き止まりはありません。

## 学べること

- 読みやすさや下流ツールのために行間を保持する重要性。  
- Aspose.Words for .NET を使って **DOCX を markdown に変換** する方法。  
- 空の段落処理を制御する `MarkdownSaveOptions` の設定項目。  
- 表、リスト、コードブロックなどのエッジケースに対する実践的なヒント。  
- 今日から任意の C# プロジェクトに組み込める、完全に動作するサンプル。

### 前提条件

- .NET 6+（または .NET Framework 4.7.2+）がインストールされていること。  
- **Aspose.Words for .NET** のライセンス（デモ用の無料トライアルで可）。  
- C# と Markdown の概念に基本的に慣れていること。  

これらが揃っていれば、さっそく始めましょう。

![Preserve line breaks diagram](preserve-line-breaks.png "Diagram illustrating how empty paragraphs become line breaks in Markdown")

## 行間の保持 – なぜ重要か

Word 文書に意図的に空白行（セクション間の視覚的区切り）を入れている場合、変換時にそれらが削除されがちです。 Markdown は単一の改行を同一段落の続きとみなすため、空行は明示的に表現しなければなりません。 **行間を保持** しないと、出力が窮屈に見え、静的サイトジェネレータなどの下流パーサーがセクションを意図せず結合してしまうことがあります。

改行を保持することは見た目だけでなく、脚注の配置やカスタムスタイリング、さらには SEO フレンドリーな見出し抽出といった、段落境界に依存するツールにも役立ちます。 要するに、忠実な変換は作者の意図を尊重することです。

## Aspose.Words で DOCX を Markdown に変換する

Aspose.Words は変換プロセスを細かく制御できるライブラリです。 キーとなるクラスは `MarkdownSaveOptions` で、空の段落をどのようにエクスポートするかを決められます。 以下では `EmptyParagraphExportMode` を `EmptyLine` に設定し、空の Word 段落を空の Markdown 行に変換します。

### 手順実装

### 1️⃣ ソース文書の読み込み

まず、`.docx` ファイルをライブラリに渡します。 `Document` コンストラクタがスタイル、画像、レイアウト情報の解析をすべて行います。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Adjust the path to match your environment
string inputPath  = @"C:\Docs\MyReport.docx";
Document doc = new Document(inputPath);
```

> **なぜ重要か:** 文書を早めに読み込むことで内部構造にアクセスでき、空の段落が実際に存在するかどうかを検出してオプションを調整できます（例: 空段落の有無を判定）。

### 2️⃣ Markdown 保存オプションの設定

ここで **「空の段落をエクスポートする方法」** に答えます。 `EmptyParagraphExportMode` 列挙体は 3 つの選択肢を提供します。

| モード | Markdown の結果 |
|------|--------------------|
| `EmptyLine` | 空行（`\n\n`）を挿入 |
| `PreserveLineBreaks` | 各改行をハードブレーク（`  \n`）に変換 |
| `None` | 空の段落を完全に除外 |

ほとんどのシナリオで、視覚的な隙間だけが欲しい場合は `EmptyLine` が最適です。

```csharp
MarkdownSaveOptions mdOpts = new MarkdownSaveOptions
{
    // Export empty paragraphs as a single empty line.
    // This is the most intuitive way to keep visual spacing.
    EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine,

    // Optional: keep original line breaks inside paragraphs.
    // Uncomment if you need finer control.
    // PreserveLineBreaks = true
};
```

> **プロのコツ:** 手動改行（Word の Shift + Enter）も保持したい場合は `PreserveLineBreaks = true` を設定します。これにより、空段落とソフトブレークの両方が往復変換で残ります。

### 3️⃣ 文書を Markdown として保存

最後に出力ファイルを書き出します。 任意のフォルダーを指定できますが、拡張子は必ず `.md` にしてください。

```csharp
string outputPath = @"C:\Docs\MyReport.md";
doc.Save(outputPath, mdOpts);
Console.WriteLine($"✅ Conversion complete! Markdown saved to {outputPath}");
```

これでパイプラインは完了です。 プログラムを実行し、生成された `.md` ファイルを開くと、元の Word ファイルにあった空行がそのまま Markdown に反映されているはずです。

### 完全動作サンプル

すべてをまとめた、すぐにコンパイルできるコンソールアプリの例です。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source DOCX
        string inputPath = @"C:\Docs\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Set up Markdown options to preserve empty paragraphs
        MarkdownSaveOptions mdOpts = new MarkdownSaveOptions
        {
            EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine,
            // PreserveLineBreaks = true   // Uncomment if you need soft line breaks
        };

        // 3️⃣ Save as Markdown
        string outputPath = @"C:\Docs\WithEmptyParas.md";
        doc.Save(outputPath, mdOpts);

        Console.WriteLine($"✅ Document converted! Check: {outputPath}");
    }
}
```

**期待される出力:** 任意のエディタで `WithEmptyParas.md` を開くと、`input.docx` の空行がすべて空行として Markdown に現れ、設計した視覚的区切りが保持されます。

## Word を Markdown として保存 – 応用シナリオ

### 表とリストの取り扱い

Word の表は自動的に Markdown の表に変換されますが、空の行は扱いが難しいことがあります。 表の行が空セルだけの場合、Aspose.Words はそれを空の段落として扱います。 `EmptyParagraphExportMode` は依然として適用されるため、**表の外側** に空行が入りますが、表内部には入りません。 表内部で視覚的な隙間を保ちたい場合は、セルにノンブレークスペース（`&nbsp;`）を挿入してください。

```csharp
// Example: Adding a placeholder to an empty cell
Table table = doc.GetChild(NodeType.Table, 0, true) as Table;
Cell emptyCell = table.Rows[2].Cells[1];
emptyCell.AppendChild(new Paragraph(doc));
emptyCell.FirstParagraph.AppendChild(new Run(doc, "\u00A0")); // non‑breaking space
```

### コードブロックと整形済みテキスト

DOCX に整形済みコードが含まれている場合、Aspose.Words は自動的に三つのバッククオートで囲みます。 コードブロック内部の空行は `EmptyParagraphExportMode` に関係なく自動的に保持されます。 ただし、空行が欠落していると感じたら、元の Word 段落スタイルが「No Spacing」になっているか確認してください。 これにより、ライブラリは各行を別々の段落として扱います。

### `PreserveLineBreaks` を使うべきケース

時には空の段落ではなくハードブレーク（`  `）だけが必要になることがあります。 たとえば詩や住所ブロックは単一の改行に依存します。 オプションを次のように切り替えてください。

```csharp
mdOpts.PreserveLineBreaks = true;   // Turns soft breaks into Markdown hard breaks
mdOpts.EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.None; // optional
```

これで Word の `Shift+Enter` が Markdown では `  \n` に変換され、真に空の段落は（`EmptyLine` を同時に有効にしない限り）削除されます。

## 空の段落を正しくエクスポートする方法

簡潔な答え: `EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine` を設定すること。 詳細な説明は以下の通りです。

- **EmptyParagraphExportMode** は、テキスト（Run）がまったくない段落に対してシリアライザが何をすべきかを指示します。  
- **EmptyLine** は二重改行を挿入し、Markdown が段落区切りとして解釈します。  
- 他のモードは段落を縮める（`None`）か、改行をハードブレークとして扱う（`PreserveLineBreaks`）だけです。

この設定を忘れると、デフォルトは `None` となり、すべての空行が消えてしまいます。 それが今回解決したい問題です。

## 複雑文書で改行を保持する方法

複雑な文書は見出し、画像、脚注が混在します。 以下のチェックリストで改行が失われないように確認してください。

| チェック項目 | なぜ重要か |
|----------------|----------------|
| **空段落の検証** | `doc.GetChildNodes(NodeType.Paragraph, true)` を使って変換前に空段落数をカウント |
| **詩用に `PreserveLineBreaks` を有効化** | 単一改行の保持を保証 |
| **画像キャプションの確認** | キャプションは別段落なので同じエクスポートモードが必要 |
| **変換後の差分テスト** | `doc.GetText()` で抽出した元テキストと Markdown 出力を比較 |
| **Markdown ビューアでテスト** | ビューアによっては複数空行の扱いが異なるため、視覚結果を確認 |

### 検証サンプルコード

```csharp
// Count empty paragraphs before saving
int emptyCount = 0;
NodeCollection paragraphs = doc.GetChildNodes(NodeType.Paragraph, true);
foreach (Paragraph p in paragraphs)
{
    if (p.GetText().Trim().Length == 0)
        emptyCount++;
}
Console.WriteLine($"Document contains {emptyCount} empty paragraph(s).");
```

保存ステップの前にこのコードを実行すれば、期待通りの改行数が保持されるか自信を持って確認できます。

## よくある落とし穴 & プロのコツ

- **落とし穴:**

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}