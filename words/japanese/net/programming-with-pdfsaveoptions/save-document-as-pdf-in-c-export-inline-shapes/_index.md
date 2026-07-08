---
category: general
date: 2026-06-30
description: C#でdocxをPDFに変換し、インラインシェイプを処理しながら文書をPDFとして保存します。Wordを正しくPDFにエクスポートするためのステップバイステップガイドに従ってください。
draft: false
keywords:
- save document as pdf
- convert docx to pdf
- convert word to pdf
- save word as pdf
- how to export inline
language: ja
og_description: C# と Aspose.Words で文書を PDF として保存します。docx を PDF に変換し、浮動形状をインライン要素としてエクスポートする方法を学びましょう。
og_title: C#でドキュメントをPDFとして保存 – インラインシェイプのエクスポート
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Save document as PDF in C# while converting docx to PDF and handling
    inline shapes. Follow this step‑by‑step guide to export Word to PDF correctly.
  headline: Save Document as PDF in C# – Export Inline Shapes
  type: TechArticle
- description: Save document as PDF in C# while converting docx to PDF and handling
    inline shapes. Follow this step‑by‑step guide to export Word to PDF correctly.
  name: Save Document as PDF in C# – Export Inline Shapes
  steps:
  - name: '**.NET 6+** (or .NET Framework 4.6+).'
    text: '**.NET 6+** (or .NET Framework 4.6+).'
  - name: The **Aspose.Words for .NET** NuGet package (`Install-Package Aspose.Words`).
    text: The **Aspose.Words for .NET** NuGet package (`Install-Package Aspose.Words`).
  - name: A sample `input.docx` that contains at least one floating picture or text
      box.
    text: A sample `input.docx` that contains at least one floating picture or text
      box.
  type: HowTo
tags:
- C#
- PDF
- Aspose.Words
title: C#で文書をPDFとして保存 – インラインシェイプをエクスポート
url: /ja/net/programming-with-pdfsaveoptions/save-document-as-pdf-in-c-export-inline-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# でドキュメントを PDF として保存 – インライン シェイプのエクスポート

C# から直接 **save document as PDF**（ドキュメントを PDF として保存）し、浮動画像のレイアウトを失わない方法を考えたことはありませんか？ あなただけではありません。Word ファイルにテキストの上に浮かんでいる画像やテキスト ボックスが含まれていると、多くの開発者が問題に直面します—単に `doc.Save("output.pdf")` を呼び出すだけで、これらの要素が消えたり位置がずれたりします。  

このチュートリアルでは、浮動オブジェクトをインライン要素として保持しながら **convert docx to pdf**（docx を pdf に変換）する正確な手順を解説します。実質的に *how to export inline* シェイプへの回答となります。最後まで読むと、期待通りに **save word as pdf**（Word を PDF として保存）できる実行可能なコードスニペットが手に入ります。

## 学習できること

- Aspose.Words（または任意の互換ライブラリ）で `.docx` ファイルをロードする。  
- `PdfSaveOptions` を設定し、浮動シェイプをインラインに変換する。  
- 保存操作を実行して **convert word to pdf**（Word を PDF に変換）する。  
- フォントが見つからない、画像が大きいといった一般的な落とし穴に対処する。  

外部ツールや Word‑automation COM オブジェクトの手動操作は不要です—純粋なクリーン C# コードだけです。

## 前提条件

1. **.NET 6+**（または .NET Framework 4.6+）。  
2. **Aspose.Words for .NET** NuGet パッケージ（`Install-Package Aspose.Words`）。  
3. 少なくとも1つの浮動画像またはテキスト ボックスを含むサンプル `input.docx`。  

別の PDF ライブラリを使用している場合でも概念は同じです—`ExportFloatingShapesAsInlineTag` に似たプロパティを探してください。

## ステップ 1: ソース ドキュメントのロード – Save Document as PDF の基本  

最初に行うべきことは、Word ファイルをメモリに読み込むことです。ここから **save document as pdf** プロセスが実際に開始されます。

```csharp
using Aspose.Words;

// Step 1: Load the source DOCX file
string inputPath = @"C:\MyDocs\input.docx";
Document doc = new Document(inputPath);
```

*Why this matters*: ドキュメントのロードは、ファイルが存在することを検証し、すべてのパーツ（スタイル、画像、ヘッダー）を解析します。ロードに失敗すると、後続の PDF 変換は実行されないため、ここでエラーを捕捉することでデバッグ時間を大幅に削減できます。

## ステップ 2: PDF 保存オプションの設定 – How to Export Inline Shapes  

ここで、ライブラリに浮動シェイプの扱い方を指示します。重要なフラグは `ExportFloatingShapesAsInlineTag` です。これを `true` に設定すると、すべての浮動画像やテキスト ボックスが **inline**（インライン）として描画され、通常の段落ランと同様になります。

```csharp
// Step 2: Prepare PDF save options
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    // true → inline (text‑flow); false → keep as block‑level floating objects
    ExportFloatingShapesAsInlineTag = true,

    // Optional: improve compatibility with older PDF viewers
    Compliance = PdfCompliance.PdfA1b
};
```

*Why this matters*: デフォルトでは、Aspose.Words は浮動シェイプを元の位置に保持するため、生成された PDF で切り取られたり消失したりする可能性があります。インラインエクスポートを有効にすると、シェイプがテキストフローの一部となり、すべての PDF リーダーで視覚的忠実度が保たれます。

## ステップ 3: ドキュメントを PDF として保存 – Convert Word to PDF  

ドキュメントがロードされ、オプションが設定されたら、最終ステップは実際に **save document as pdf** を行うワンライナーです。

```csharp
// Step 3: Save the document as a PDF file
string outputPath = @"C:\MyDocs\FloatingShapes.pdf";
doc.Save(outputPath, pdfOptions);
```

これで完了です！`doc.Save` 呼び出しは、元の Word レイアウトを鏡像する PDF を生成し、浮動画像がテキスト内にきれいに配置されます。

## 完全な動作例  

すべてをまとめると、以下のような単体のコンソール アプリがあります。コピー＆ペースト、コンパイル、実行できます：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToPdfInlineExport
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\MyDocs\input.docx";
            string outputPath = @"C:\MyDocs\FloatingShapes.pdf";

            // Load the DOCX file
            Document doc = new Document(inputPath);

            // Configure PDF options to export floating shapes as inline
            PdfSaveOptions pdfOptions = new PdfSaveOptions
            {
                ExportFloatingShapesAsInlineTag = true,
                Compliance = PdfCompliance.PdfA1b // optional, ensures PDF/A‑1b compliance
            };

            // Save as PDF
            doc.Save(outputPath, pdfOptions);

            Console.WriteLine($"Document successfully saved as PDF: {outputPath}");
        }
    }
}
```

**期待される出力**（コンソール）:

```
Document successfully saved as PDF: C:\MyDocs\FloatingShapes.pdf
```

`FloatingShapes.pdf` を任意のビューアで開くと、以前は浮動していた画像が段落内にきちんと埋め込まれていることが確認できます。

## なぜ浮動シェイプをインラインとしてエクスポートするのか？

Word では浮動シェイプは、ページ上の任意の位置に画像を配置できるため便利です。しかし、PDF は *ページ指向* のフォーマットであり、Word のような「浮動」の概念はありません。変換エンジンがそれらをブロックレベルオブジェクトのままにすると、次のような問題が起こります：

- 他のコンテンツと重なる。  
- ページ余白で切り取られる。  
- 古い PDF リーダーで完全に消える。  

それらを **inline** 要素に変換することで、PDF が読み順を尊重し、スクリーンリーダーが文書を正しく解釈できるようになります—アクセシビリティ遵守に重要です。

## Docx から PDF へ変換する際の一般的な落とし穴

| 問題 | 症状 | 対策 |
|------|------|------|
| フォントが見つからない | テキストが “□” と表示されたり、Arial にフォールバックしたりする | `PdfSaveOptions.FontEmbeddingMode = FontEmbeddingMode.Always` でフォントを埋め込む。 |
| 大きな画像がメモリ使用量を増大させる | 大きな DOCX で Out‑of‑memory 例外が発生する | 変換前に画像を縮小するか、`PdfSaveOptions.ImageCompression = PdfImageCompression.Jpeg;` を設定する。 |
| インラインエクスポートが適用されない | PDF で浮動シェイプが依然として浮いたままになる | 最新の Aspose.Words バージョンを使用しているか確認してください。古いリリースではプロパティ名が変更されています。 |
| パスエラー | `FileNotFoundException` | `Path.Combine` を使用し、ディレクトリが存在することを確認（`Directory.CreateDirectory`）。 |

## 上級: 特定のシェイプだけをインラインでエクスポート

場合によっては、*選択的* にインライン変換したいことがあります—すべてではなく特定の画像だけです。保存前にドキュメントノードを走査することで実現できます：

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.WrapType == WrapType.Inline)
        continue; // already inline

    // Example condition: only convert pictures larger than 300px
    if (shape.HasImage && shape.Width > 300)
        shape.WrapType = WrapType.Inline;
}
```

`WrapType` を調整した後、同じ `doc.Save` 呼び出しを実行します。これにより **how to export inline** の動作を細かく制御できます。

## プロのコツとベストプラクティス  

- **Pro tip:** アーカイブに PDF/A が必要な場合は `pdfOptions.Compliance = PdfCompliance.PdfA1b` を設定してください。  
- **Watch out for:** 隠れたセクション（`SectionBreakContinuous`）が浮動シェイプを隠す可能性があります。保存前に `doc.UpdatePageLayout()` を実行してください。  
- **Performance tip:** バッチで多数のファイルを変換する場合は、`PdfSaveOptions` のインスタンスを再利用すると、割り当てオーバーヘッドが削減されます。  
- **Testing:** 生成された PDF は必ず少なくとも2つのビューア（Adobe Reader、Edge）で開き、レイアウトの一貫性を確認してください。  

## ビジュアル概要  

![Save document as PDF フローチャート（ロード → 設定 → 保存 手順）](https://example.com/flowchart.png "Save document as PDF フローチャート")

*Alt text:* **Save document as PDF flowchart** – DOCX のロード、インラインエクスポートの設定、PDF への保存という3ステッププロセスを示しています。

## 結論  

これで、C# で **save document as PDF** を行い、浮動オブジェクトを正しく処理する堅牢で本番対応の手法が手に入りました。`ExportFloatingShapesAsInlineTag` を設定することで、すべての画像、チャート、テキスト ボックスがテキストフローの一部となり、素朴な **convert word to pdf** 手法でよく起こる問題を排除できます。  

試してみてください：複数の浮動画像を含む複雑なレポートを変換し、選択的インラインロジックで一部のシェイプを元の位置に残す実験を行ってみましょう。次に **convert docx to pdf** が必要になるときは、すべてのビジュアル要素を正確に保持する方法が分かっています。  

問題が発生したり、便利なショートカットを見つけた場合は遠慮なくコメントしてください。コーディングを楽しんで！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words で docx を pdf に保存 – 完全な C# ガイド](/words/english/net/basic-conversions/save-docx-as-pdf-with-aspose-words-complete-c-guide/)
- [Aspose.Words で Word を PDF に保存 – 完全な C# ガイド](/words/english/net/basic-conversions/save-word-as-pdf-with-aspose-words-complete-c-guide/)
- [Aspose.Words を使用した C# での word を pdf に変換 – ガイド](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}