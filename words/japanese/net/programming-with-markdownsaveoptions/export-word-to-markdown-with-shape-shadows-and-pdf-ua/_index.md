---
category: general
date: 2026-03-28
description: C# で Aspose.Words を使用して、Word を Markdown にエクスポートし、シェイプに影を追加し、PDF/UA を保存する方法をステップバイステップで学ぶガイド。
draft: false
keywords:
- export word to markdown
- add shape shadow
- save pdf ua
- Aspose.Words markdown
- C# document conversion
language: ja
og_description: Aspose.Words を使用して C# で Word を Markdown にエクスポートし、シェイプに影を追加、PDF/UA
  を保存する方法。コードとヒント付きの完全チュートリアル。
og_title: Word を Markdown にエクスポート – シェイプの影を追加 & PDF/UA を保存
tags:
- Aspose.Words
- C#
- Markdown
- PDF/UA
title: シェイプの影とPDF/UA対応でWordをMarkdownにエクスポート
url: /ja/net/programming-with-markdownsaveoptions/export-word-to-markdown-with-shape-shadows-and-pdf-ua/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Shape の影付きで Word を Markdown にエクスポートし、PDF/UA で保存する方法

Word を **markdown にエクスポート** したいけど、かっこいい shape の影も残したまま PDF/UA の準拠も満たしたい、ということはありませんか？ 同じ悩みを抱える開発者は多いです。特にアクセシビリティ（PDF/UA）が必須の場合、ビジュアルの忠実性を保ちつつフォーマットを変換するのは壁にぶつかりがちです。

このガイドでは、**Word を markdown にエクスポート**、**shape に影を付け**、最後に **浮動 shape をインラインに強制して PDF/UA を保存** する完全な実行可能サンプルを順を追って解説します。使用するのは Aspose.Words for .NET で、堅牢なドキュメント変換の定番ライブラリです。外部スクリプトや自前パーサーは不要、今日からコンソールアプリに貼り付けられるシンプルな C# コードだけです。

> **プロのコツ:** まだ Aspose.Words をインストールしていない方は、最新の NuGet パッケージ (`Install-Package Aspose.Words`) を取得してください。 .NET 6+、.NET Framework 4.8、.NET Core でも動作します。

## 必要な環境

- **Visual Studio 2022**（または .NET 6+ に対応した任意の IDE）
- **Aspose.Words for .NET**（NuGet バージョン 23.8 以上）
- 少なくとも 1 つの shape（例: 四角形）を含むサンプル `input.docx`
- 基本的な C# の知識 – 文法はシンプルに保ちます

前提条件が整ったら、さっそく始めましょう。

![Diagram showing export word to markdown flow](export_word_to_markdown_diagram.png){alt="Word を markdown にエクスポートする例"}

## Step 1: 復元モードで Word 文書を読み込む  

何かを変更する前に、文書をメモリ上にロードする必要があります。**RecoveryMode.Recover** で読み込むと、フォント置換の警告を取得でき、ソースにインストールされていないフォントが使われている場合に便利です。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Saving;

// 1️⃣ Load the document while collecting warnings
var loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Recover,
    WarningCallback = new WarningInfoCollection()
};

Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*なぜ RecoveryMode か？*  
元ファイルが欠損フォントを参照していると、Aspose は自動で置換し警告を出します。その警告を取得しておくと、デバッグやコンプライアンスレポート作成時に役立ちます。

## Step 2: Shape に影を追加  

文書がロードできたので、shape の見た目を強化します。最初の `Shape` ノードを取得し、さりげないドロップシャドウを有効にします。

```csharp
// 2️⃣ Find the first shape and enable its shadow
Shape shape = (Shape)doc.GetChildNodes(NodeType.Shape, true)[0];
shape.ShadowFormat.Visible = true;
shape.ShadowFormat.BlurRadius = 4;   // soft edges
shape.ShadowFormat.Distance = 2;    // how far the shadow is from the shape
shape.ShadowFormat.Angle = 30;      // direction of the light source
```

*影を調整する理由*  
影を付けると奥行き感が出て、Word 上でもエクスポート後の markdown 画像（後で shape を画像に変換した場合）でも shape が際立ちます。ビジュアル属性が変換パイプラインを通過するかどうかの簡易テストにもなります。

## Step 3: 文書を Markdown（LaTeX 数式付き）にエクスポート  

Aspose.Words は Word ファイルをクリーンな markdown に変換できます。ここでは OfficeMath の数式を LaTeX 形式でエクスポートするよう指示します。LaTeX は科学文書の事実上の標準です。

```csharp
// 3️⃣ Configure markdown export options
var markdownOptions = new MarkdownSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,
    // Store all extracted images in a dedicated folder
    ResourceSavingCallback = (s, e) =>
    {
        string assetsFolder = "YOUR_DIRECTORY/assets";
        Directory.CreateDirectory(assetsFolder);
        e.FileName = Path.Combine(assetsFolder, e.FileName);
    }
};

// Save as markdown
doc.Save("YOUR_DIRECTORY/output.md", markdownOptions);
```

*期待できる出力*  
- 標準的な markdown 構文の `output.md` ファイル  
- 影を付けた shape を含むすべての埋め込み画像が `assets/` 配下に保存される  
- 数式は `$…$` の LaTeX ブロックとして出力され、MathJax や KaTeX でレンダリング可能

## Step 4: 同じ文書を PDF/UA で保存  

PDF/UA（PDF/Universal Accessibility）は PDF が ISO 14289‑1 に準拠していることを保証します。さらに浮動 shape をインラインタグとして保存するよう強制し、アクセシビリティタグ付けを簡素化します。

```csharp
// 4️⃣ Set up PDF/UA compliance and inline floating shapes
var pdfOptions = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfUAX2,
    ExportFloatingShapesAsInlineTag = true
};

// Save the PDF/UA file
doc.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*PDF/UA が必要な理由*  
利用者にスクリーンリーダーを使用するユーザーがいる、あるいは法的なアクセシビリティ基準を満たす必要がある場合、PDF/UA が最適です。`ExportFloatingShapesAsInlineTag` フラグにより、浮動オブジェクトが論理的な読順を乱すことを防げます。

## Step 5: フォント置換警告を確認  

変換処理が終わったら、**Step 1** で取得したフォント関連の警告を出力しておくとベストプラクティスです。

```csharp
// 5️⃣ List font‑substitution warnings (if any)
var warnings = (WarningInfoCollection)loadOptions.WarningCallback;
foreach (var warning in warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"⚠️ {warning.Description}");
}
```

「*Font 'Calibri' was substituted with 'Arial'*」のようなメッセージが出た場合、どのフォントが欠損していたかが一目で分かります。置換フォントを埋め込むか、欠損フォントを同梱するか判断できます。

## 完全動作サンプル  

すべてをまとめた、コンソールプロジェクトにコピペできる完全プログラムです。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load with recovery mode and capture warnings
        var loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.Recover,
            WarningCallback = new WarningInfoCollection()
        };
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Add a shadow to the first shape
        Shape shape = (Shape)doc.GetChildNodes(NodeType.Shape, true)[0];
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.BlurRadius = 4;
        shape.ShadowFormat.Distance = 2;
        shape.ShadowFormat.Angle = 30;

        // Export to Markdown with LaTeX math and custom assets folder
        var markdownOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            ResourceSavingCallback = (s, e) =>
            {
                string assetsFolder = "YOUR_DIRECTORY/assets";
                Directory.CreateDirectory(assetsFolder);
                e.FileName = Path.Combine(assetsFolder, e.FileName);
            }
        };
        doc.Save("YOUR_DIRECTORY/output.md", markdownOptions);

        // Save as PDF/UA, forcing floating shapes inline
        var pdfOptions = new PdfSaveOptions
        {
            Compliance = PdfCompliance.PdfUAX2,
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // Print any font‑substitution warnings
        var warnings = (WarningInfoCollection)loadOptions.WarningCallback;
        foreach (var warning in warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ {warning.Description}");
        }
    }
}
```

### 期待される結果  

- `output.md` にはクリーンな markdown、LaTeX でエンコードされた数式、`![Shape](assets/shape0.png)` のような画像リンクが含まれる  
- `output.pdf` は PDF/UA 準拠のファイルで、Adobe Acrobat のアクセシビリティチェッカーを通過する  
- コンソール出力にフォント置換警告が一覧表示され、欠損フォントの管理が容易になる

## よくある質問とエッジケース  

**文書に複数の shape がある場合は？**  
`doc.GetChildNodes(NodeType.Shape, true)` をループし、各要素に対して影設定を適用してください。  

**影の色を変えられますか？**  
はい、保存前に `shape.ShadowFormat.Color = Color.Gray;` などで設定できます。  

**Web 配備時に assets フォルダのパスを変更する必要がありますか？**  
必須です。相対パスを使用するか、`ResourceSavingCallback` で CDN URL を設定して画像配信を最適化してください。  

**markdown エクスポートで Word 固有の機能は失われますか？**  
トラック変更、コメント、複雑な SmartArt などは markdown には変換されません。必要なら PDF/UA 版をバックアップとして保持してください。

## 結論  

Aspose.Words を使って **Word を markdown にエクスポート**、**shape に影を付け**、そして **PDF/UA で保存** する方法を学びました。フルコード例は、フォント警告の処理、リソース管理、アクセシビリティ遵守を一つのシンプルなスクリプトで実現する、実務レベルのワークフローを示しています。

次のステップは？ 影のパラメータを変えてみる、`MarkdownSaveOptions`（例: `ExportImagesAsBase64`）を試す、あるいはこのパイプラインを ASP.NET Core API に組み込んでユーザーがアップロードした Word ファイルをリアルタイムで変換する、などです。さらに他の出力形式に興味がある場合は、Aspose の **HTML**、**EPUB**、**TIFF** エクスポートオプションもチェックしてください。どれも似たようなパターンで利用できます。

Happy coding, and may your documents always render exactly as you intended!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}