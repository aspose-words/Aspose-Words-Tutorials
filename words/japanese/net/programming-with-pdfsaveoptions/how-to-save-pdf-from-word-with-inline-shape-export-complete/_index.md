---
category: general
date: 2026-06-02
description: Aspose.Words を使用して DOCX から PDF を保存し、図形をインラインの span タグとしてエクスポートし、数ステップで
  Word を PDF に変換する方法。
draft: false
keywords:
- how to save pdf
- save docx as pdf
- convert word to pdf
- how to export shapes
- inline span tags
language: ja
og_description: Aspose.Words を使用して Word 文書から PDF を保存する方法、浮動形状をインラインの span タグとしてエクスポートし、クリーンな
  Word から PDF への変換結果を得る。
og_title: WordからPDFを保存する方法 – インラインシェイプエクスポートチュートリアル
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  headline: How to Save PDF from Word with Inline Shape Export – Complete Guide
  type: TechArticle
- description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  name: How to Save PDF from Word with Inline Shape Export – Complete Guide
  steps:
  - name: What if my document contains **SmartArt** or **Charts**?
    text: SmartArt and charts are treated as drawing objects. The `ExportFloatingShapesAsInlineTag`
      flag will still wrap them in `<span>` tags, but complex graphics may lose some
      fidelity. In those cases, consider exporting the chart as an image first (`Chart.ToImage()`)
      and then inserting it inline.
  - name: Can I **preserve hyperlinks** and **bookmarks**?
    text: Absolutely. Those elements are not affected by the `ExportFloatingShapesAsInlineTag`
      setting. Aspose.Words retains all hyperlink and bookmark information automatically.
  - name: How do I **change PDF compression** or **embed fonts**?
    text: '`PdfSaveOptions` offers many additional properties:'
  type: HowTo
tags:
- Aspose.Words
- C#
- PDF conversion
title: WordからインラインシェイプエクスポートでPDFを保存する方法 – 完全ガイド
url: /ja/net/programming-with-pdfsaveoptions/how-to-save-pdf-from-word-with-inline-shape-export-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word からインライン シェイプ エクスポートで PDF を保存する方法 – 完全ガイド

Word ファイルから **PDF を保存する方法** を、すべての浮動シェイプをきれいにフローに収めたまま知りたくありませんか？ あなただけではありません。多くのエンタープライズ アプリでは、画像がずれたり余計な描画オブジェクトが残ったりしないように *Word を PDF に変換* する必要があります。良いニュースは、Aspose.Words がそれを簡単にし、ライブラリに **シェイプをインライン `<span>` タグとしてエクスポート** させることができ、PDF が元の DOCX と同じように見えるということです。

このチュートリアルでは、DOCX の読み込み、`PdfSaveOptions` の調整、そして最終的にきれいな PDF を保存するまでの全プロセスを順に解説します。最後までで、**PDF の保存方法**、**docx を pdf に保存する方法**、そして *インライン span タグ* を使用した **シェイプのエクスポート方法** が分かります。

## 必要なもの

- **Aspose.Words for .NET**（執筆時点での最新バージョン 24.x）。  
- **.NET 6.0** 以上 – コードは .NET Framework 4.7.2 でも動作しますが、.NET 6 が最適です。  
- 少なくとも 1 つの浮動シェイプ（画像、テキスト ボックス、または図形）を含むシンプルな Word 文書。  
- お好みの IDE（Visual Studio、Rider、VS Code + C# 拡張機能）  

以上です—追加の NuGet パッケージは不要で、面倒な COM インターロップも必要ありません。準備はいいですか？さっそく始めましょう。

## ステップ 1: プロジェクトのセットアップと Aspose.Words の追加

まず、コンソール アプリを作成します（または既存のサービスにコードを統合します）。

```bash
dotnet new console -n WordToPdfDemo
cd WordToPdfDemo
dotnet add package Aspose.Words
```

> **Pro tip:** Visual Studio を使用している場合は、NuGet パッケージ マネージャー UI からパッケージを追加できます—*Aspose.Words* を検索してください。

## ステップ 2: ソース ドキュメントの読み込み

ライブラリの参照が設定されたので、DOCX を読み込むことができます。これは **PDF を保存する方法** の最初の具体的なステップで、ソースをメモリに取得することです。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Step 2: Load the source document
        // Replace YOUR_DIRECTORY with the actual path on your machine.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

**なぜ重要か:** ファイルを読み込むことで、パスが正しいことと Aspose が Word の構造を解析できることを検証します。ファイルに浮動シェイプが含まれている場合、それらは `Document` オブジェクトのノードツリーの一部になります。

## ステップ 3: PDF 保存オプションの設定 – シェイプをインライン タグとしてエクスポート

これが **シェイプのエクスポート方法** の核心です。デフォルトでは Aspose.Words は浮動シェイプを PDF 内の別個のオブジェクトとして描画し、レイアウトがずれることがあります。`ExportFloatingShapesAsInlineTag` を `true` に設定すると、エンジンは各シェイプをインライン `<span>` 要素でラップし、フローを保持します。

```csharp
        // Step 3: Configure PDF save options to export floating shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            // Optional: keep the original page size
            PageMode = PdfPageMode.UseTrimBox
        };
        Console.WriteLine("PDF save options configured – shapes will be inline.");
```

**なぜこのフラグを有効にするのか？** テキストの上に浮かんでいる署名ボックスを含む契約書を想像してください。この設定なしで PDF に変換すると、ボックスが別のページに表示されることがあります。インライン `<span>` タグはシェイプを周囲の段落に固定し、忠実なビジュアルレプリカを生成します。

## ステップ 4: ドキュメントを PDF として保存

最後に、先ほど作成したオプションを使って `doc.Save` を呼び出します。これが実際に **docx を pdf に保存** する瞬間です。

```csharp
        // Step 4: Save the document as a PDF using the configured options
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved successfully to: {outputPath}");
    }
}
```

プログラムを実行（`dotnet run`）し、`output.pdf` を確認してください。浮動シェイプがインラインで描画され、Word に表示された通りになるはずです。

## ステップ 5: 結果の検証 – 簡易チェックリスト

1. **すべてのテキストが存在する** – 欠落した段落はありません。  
2. **浮動シェイプが正しい位置に表示される** – これらはテキストフローの一部になっています。  
3. **PDF のサイズが妥当である** – インラインタグでエクスポートすると、別々の画像ストリームに比べてファイルサイズの肥大化が通常抑えられます。  

何か問題がある場合は、ソース DOCX が本当に *浮動* シェイプを使用しているか確認してください（右クリック → レイアウト → “テキストに合わせてインライン” と “四角形/テキストの背後”）。変換前にシェイプを “インライン” に切り替えても動作しますが、インラインタグオプションを使うと元のファイルを編集せずに制御できます。

## エッジケースとよくある質問

### ドキュメントに **SmartArt** や **チャート** が含まれている場合は？

SmartArt とチャートは描画オブジェクトとして扱われます。`ExportFloatingShapesAsInlineTag` フラグはそれらを `<span>` タグでラップしますが、複雑なグラフィックは一部の忠実度が失われる可能性があります。そのような場合は、まずチャートを画像としてエクスポート（`Chart.ToImage()`）し、インラインで挿入することを検討してください。

### ハイパーリンクやブックマークを **保持** できますか？

もちろんです。これらの要素は `ExportFloatingShapesAsInlineTag` 設定の影響を受けません。Aspose.Words はすべてのハイパーリンクとブックマーク情報を自動的に保持します。

### PDF の圧縮を **変更** したり **フォントを埋め込む** 方法は？

`PdfSaveOptions` には多くの追加プロパティがあります：

```csharp
pdfOpts.JpegQuality = 90;               // Adjust image compression
pdfOpts.FontEmbeddingMode = FontEmbeddingMode.EmbedAll; // Embed all used fonts
```

下流の要件（例: PDF/A 準拠）に応じてこれらの設定を自由に調整してください。

## 完全動作例（コピー＆ペースト可能）

以下は `Program.cs` にコピーできる完全なプログラムです。`YOUR_DIRECTORY` を実際のフォルダー パスに置き換えてください。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source DOCX (contains floating shapes)
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded.");

        // Configure PDF save options – export shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            PageMode = PdfPageMode.UseTrimBox,
            // Optional tweaks
            JpegQuality = 90,
            FontEmbeddingMode = FontEmbeddingMode.EmbedAll
        };
        Console.WriteLine("PDF options set – shapes will be inline.");

        // Save as PDF
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved to {outputPath}");
    }
}
```

**Expected output in the console:**

```
Document loaded.
PDF options set – shapes will be inline.
PDF saved to C:\MyDocs\output.pdf
```

`output.pdf` を開くと、元のレイアウトが表示され、すべての浮動シェイプがテキストフロー内にきれいに配置されていることがわかります。

## 結論

Word 文書から **PDF を保存する方法** を取り上げ、浮動シェイプがインライン `<span>` タグになることを保証しました。DOCX を読み込み、`PdfSaveOptions` を設定し、`doc.Save` を呼び出すことで、レイアウトの予期せぬ変化なしに **docx を pdf に保存** し、**word を pdf に変換** できるようになります。

次のステップは？このアプローチを **PDF/A** 準拠と組み合わせてアーカイブに使用したり、シンプルな `foreach` ループで DOCX フォルダーをバッチ処理したりしてみてください。また、Aspose.Words の `DocumentVisitor` API を利用して **カスタムレンダリング**（例: ウォーターマークの追加）を検討することもできます。

シェイプの取り扱い、フォント埋め込み、パフォーマンス調整に関する質問があれば、下にコメントを残してください。ハッピーコーディング！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法に基づく密接に関連したトピックを取り上げています。各リソースには、完全な動作コード例とステップバイステップの解説が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Aspose.Words for Java を使用したドキュメントの PDF 保存方法](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Aspose.Words for Java で Word を PDF に変換](/words/english/java/document-converting/exporting-documents-to-pdf/)
- [aspose word to pdf – Java で DOCX を PDF に変換](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}