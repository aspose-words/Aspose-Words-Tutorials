---
category: general
date: 2025-12-19
description: LaTeX方程式付きMarkdownガイド – Aspose.Words for C# を使用して、docx を Markdown に変換し、方程式を
  LaTeX にエクスポートし、画像をユニークな名前でフォルダーに保存する方法を学びましょう。
draft: false
keywords:
- markdown with latex equations
- convert docx to markdown
- save images to folder
- export equations to latex
- generate unique image names
language: ja
og_description: Markdown と LaTeX 方程式のチュートリアルでは、docx を Markdown に変換する方法、方程式を LaTeX
  にエクスポートする方法、保存された画像のためにユニークな画像名を生成する方法を示します。
og_title: LaTeX方程式付きMarkdown – 完全なC#変換ガイド
tags:
- Aspose.Words
- C#
- Markdown
- LaTeX
title: LaTeX方程式付きMarkdown：DOCXをMarkdownに変換し、画像をエクスポート
url: /ja/net/programming-with-markdownsaveoptions/markdown-with-latex-equations-convert-docx-to-markdown-and-e/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# markdown with latex equations: DOCX を Markdown に変換し画像をエクスポート

Word ファイルから **markdown with latex equations** を取得する方法が分からないことはありませんか？ あなただけではありません—多くの開発者が Office から静的サイトジェネレータへドキュメントを移行する際にこの問題に直面しています。  

このチュートリアルでは、Aspose.Words for .NET を使用して、**docx を markdown に変換**し、**数式を latex にエクスポート**し、**画像をフォルダーに保存**し、**ユニークな画像名を生成**するロジックを備えた、完全なエンドツーエンドのソリューションを順を追って解説します。  

最後まで実行すれば、手動でコピー＆ペーストする必要なく、クリーンな Markdown ファイル、LaTeX 対応の数式、整理された画像ディレクトリを生成する、すぐに実行可能な C# プログラムが手に入ります。

## 必要なもの

- .NET 6（または最近の .NET ランタイム）  
- Aspose.Words for .NET 23.10 以降（NuGet パッケージ `Aspose.Words`）  
- 通常のテキスト、Office Math オブジェクト、数枚の画像を含むサンプル `input.docx`  
- 好きな IDE（Visual Studio、Rider、または VS Code）  

以上です。余計なライブラリや面倒なコマンドラインツールは不要で、純粋に C# だけです。

## Step 1: ドキュメントを安全にロード（リカバリーモード）

多数の手で編集された可能性のあるファイルを扱う場合、破損は現実的なリスクです。Aspose.Words では *RecoveryMode* を有効にでき、ローダーが例外を投げる代わりに破損した部分を修復しようとします。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // Load the document with recovery mode – this handles possible corruption.
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx", loadOptions);
```

**この点が重要な理由:**  
ソースファイルに不要な XML ノードや壊れた画像ストリームが含まれている場合でも、リカバリーモードは使用可能な `Document` オブジェクトを返します。このステップを省くと、特に CI パイプラインでアップロードを完全に管理できない場合にハードクラッシュを引き起こす可能性があります。

> **プロのコツ:** バッチ処理時はロードを `try/catch` で囲み、`DocumentCorruptedException` を後で確認できるようにログに記録してください。

## Step 2: DOCX を LaTeX 数式付き Markdown に変換

ここからがチュートリアルの核心です：**markdown with latex equations** を実現します。Aspose.Words の `MarkdownSaveOptions` で `OfficeMathExportMode.LaTeX` を指定すると、各 Office Math オブジェクトが `$…$` または `$$…$$` で囲まれた LaTeX 文字列に変換されます。

```csharp
        // Export Office Math equations to LaTeX while saving as Markdown.
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        doc.Save(@"YOUR_DIRECTORY/output_math.md", markdownMathOptions);
```

生成される `output_math.md` は次のようになります:

```markdown
Here is an inline equation $E = mc^2$ inside a sentence.

And a displayed equation:

$$
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
$$
```

**これが欲しい理由:**  
ほとんどの静的サイトジェネレータ（Hugo、Jekyll、MkDocs）は、MathJax や KaTeX プラグインを有効にすれば LaTeX デリミタをそのまま認識します。直接 LaTeX にエクスポートすることで、正規表現ハックが必要な後処理ステップを回避できます。

### エッジケース

- **複雑な数式:** 非常に深い入れ子構造でも正しくレンダリングされますが、`OutOfMemoryException` が発生した場合は `MathRenderer` のメモリ上限を増やす必要があります。  
- **混在コンテンツ:** 段落に通常テキストと数式が混在している場合、Aspose.Words は自動的に分割し、周囲の markdown を保持します。

## Step 3: 画像をフォルダーにユニークな名前で保存

Word 文書に画像が含まれている場合、markdown が参照できるように個別の画像ファイルとして保存したいでしょう。`MarkdownSaveOptions` の `ResourceSavingCallback` を使用すると、各画像の書き込み方法を完全に制御できます。

```csharp
        // Customize image handling during Markdown export.
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (resource, stream) =>
            {
                // Generate a unique file name for each image.
                string imageFileName = $"img_{Guid.NewGuid()}.png";
                string imagePath = Path.Combine(@"YOUR_DIRECTORY/Images", imageFileName);

                // Ensure the Images folder exists.
                Directory.CreateDirectory(Path.GetDirectoryName(imagePath)!);

                // Save the image to the file system.
                using var imageFile = File.Create(imagePath);
                resource.Save(imageFile);
            }
        };
        doc.Save(@"YOUR_DIRECTORY/output_images.md", markdownImageOptions);
```

**現在の markdown の例:**

```markdown
![Image description](Images/img_3f9c2a1e-7b5d-4c8f-9d6e-2b5c7a9e1f0a.png)
```

**なぜユニークな名前を生成するのか？**  
同じ画像が複数回出現する場合、元の名前を使用すると上書きが発生します。GUID ベースの名前にすれば、各ファイルが確実に一意となり、特に並列ジョブで変換を実行する際に便利です。

### ヒントと注意点

- **パフォーマンス:** 各画像に GUID を生成するコストはごくわずかですが、数千枚の画像を処理する場合は決定的ハッシュ（例：画像バイトの SHA‑256）に切り替えることができます。  
- **ファイル形式:** `resource.Save` は画像を元の形式で保存します。すべて PNG にしたい場合は、`resource.Save(imageFile);` を `resource.Save(imageFile, ImageSaveOptions.CreateSaveOptions(SaveFormat.Png));` に置き換えてください。

## Step 4: インラインシェイプ付き PDF をエクスポート（オプション）

場合によっては、法務レビュー用に同じ文書の PDF バージョンが必要になることがあります。`ExportFloatingShapesAsInlineTag` を設定すると、テキストボックスなどのフローティングオブジェクトが PDF 内でインラインタグとして保持され、レイアウトの忠実度が保たれます。

```csharp
        // Save the document as PDF, exporting floating shapes as inline tags.
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save(@"YOUR_DIRECTORY/output_shapes.pdf", pdfOptions);
    }
}
```

PDF 出力がワークフローに含まれない場合はこのステップを省略できます。省略しても何も壊れません。

## 完全動作例（全ステップ統合）

以下はコンソールアプリにコピペできる完全なプログラムです。`YOUR_DIRECTORY` を実際の絶対パスまたは相対パスに置き換えてください。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // 1️⃣ Load with recovery mode.
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx", loadOptions);

        // 2️⃣ Export markdown with LaTeX equations.
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        doc.Save(@"YOUR_DIRECTORY/output_math.md", markdownMathOptions);

        // 3️⃣ Save images to a folder, using unique GUID names.
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (resource, stream) =>
            {
                string imageFileName = $"img_{Guid.NewGuid()}.png";
                string imagePath = Path.Combine(@"YOUR_DIRECTORY/Images", imageFileName);
                Directory.CreateDirectory(Path.GetDirectoryName(imagePath)!);
                using var imageFile = File.Create(imagePath);
                resource.Save(imageFile);
            }
        };
        doc.Save(@"YOUR_DIRECTORY/output_images.md", markdownImageOptions);

        // 4️⃣ (Optional) Export PDF with inline shape tags.
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save(@"YOUR_DIRECTORY/output_shapes.pdf", pdfOptions);
    }
}
```

このプログラムを実行すると、3 つのファイルが生成されます:

| File | Purpose |
|------|---------|
| `output_math.md` | LaTeX 対応の数式を含む Markdown |
| `output_images.md` | ユニークな名前の PNG への画像リンクを含む Markdown |
| `output_shapes.pdf` | フローティングシェイプをインラインタグとして保持した PDF（オプション） |

## 結論

これで、**markdown with latex equations** パイプラインが完成しました。**docx を markdown に変換**し、**数式を latex にエクスポート**し、**画像をフォルダーに保存**しつつ、各画像に対して **ユニークな画像名を生成**します。このアプローチは完全に自己完結型で、最新の .NET プロジェクトで動作し、必要なのは Aspose.Words の NuGet パッケージだけです。

次は何をすべきか？ 生成した markdown を Hugo などの静的サイトジェネレータに組み込み、MathJax を有効にすれば、閉じたオフィス形式のドキュメントが美しいウェブ対応サイトへと変貌します。表が必要ですか？ Aspose.Words は `MarkdownSaveOptions.ExportTableAsHtml` もサポートしているので、複雑なレイアウトもそのまま保持できます。

If

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}