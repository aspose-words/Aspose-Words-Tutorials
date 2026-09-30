---
category: general
date: 2026-02-21
description: Aspose.Words for .NET を使用して、Word を画像としてすばやく保存します。Word を PNG に変換し、各ページを個別の画像としてエクスポートし、ファイル名をカスタマイズする方法をご紹介します。
draft: false
keywords:
- save word as images
- convert word to png
- convert word document png
- save each page png
- image export single page
language: ja
og_description: Aspose.Words を使用して Word を画像として保存します。このガイドでは、Word 文書を PNG に変換し、各ページを個別のファイルとしてエクスポートし、名前をカスタマイズする方法を示します。
og_title: C#でWordを画像として保存 – 完全チュートリアル
tags:
- Aspose.Words
- C#
- Image Export
- Document Conversion
title: C#でWordを画像として保存する – ステップバイステップガイド
url: /ja/net/programming-with-imagesaveoptions/save-word-as-images-with-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#でWordを画像として保存 – ステップバイステップガイド

Word を画像として **保存** したいと思ったことはありませんか？どの API 呼び出しを使えばよいか分からないこともあるでしょう。これはあなただけの問題ではありません—ドキュメントページをウェブギャラリーに埋め込んだり、プレビュー用のサムネイルを生成したりしたい開発者は多く、この壁にぶつかります。朗報です。C# と Aspose.Words の数行のコードで、Word 文書を PNG に変換し、各ページを個別の画像としてエクスポートし、さらに各ファイルに意味のある名前を付けることができます—IDE を離れる必要はありません。

このチュートリアルでは、`.docx` ファイルの読み込みから `Page_1.png`、`Page_2.png` といったファイルが生成されるまでの全プロセスを順に解説します。途中で **convert word to png** のヒントを紹介し、**image export single page** モードについて説明し、**save each page png** を自分でループを書かずに実現する方法を示します。

## 必要なもの

- **.NET 6.0**（またはそれ以降のバージョン；API は .NET Framework 4.7+ でも同様に動作します）
- **Aspose.Words for .NET** NuGet パッケージ (`Aspose.Words`) – `dotnet add package Aspose.Words` で追加できます。
- C# の構文に関する基本的な理解（特別なことは不要で、通常の `using` 文が使えれば OK）
- 変換したい Word ファイル（`.docx` または `.doc`）。このガイドでは `YOUR_DIRECTORY/input.docx` にあると想定します。

> プロのコツ: Visual Studio を使用している場合、NuGet パッケージ マネージャー UI で Aspose.Words をワンクリックで追加できます。

## 手順 1: ソースドキュメントの読み込み

最初に行うのは、Word ファイルを `Document` オブジェクトに読み込むことです。このオブジェクトは、ページ、段落、画像など、ファイル全体のメモリ上の表現と考えてください。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

なぜこの方法で読み込むのでしょうか？`Document` は非表示セクションから複雑なテーブルまで全てを処理するため、ファイルを自分で解析する必要がありません。また、後続のエクスポート処理がレイアウト情報に完全にアクセスできるようになるため、後で **convert word document png** を行う際に重要です。

## 手順 2: PNG 用の Image Save Options を作成

次にエクスポートの動作を設定します。`ImageSaveOptions` を使用すると、出力形式（`SaveFormat.Png`）を選択し、ページごとに1枚の画像にするか、1枚の結合画像にするかをライブラリに指示できます。

```csharp
// Step 2: Create image save options for PNG format
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png);
```

`SaveFormat.Png` を設定するとロスレス品質が保証され、サムネイルや高解像度プレビューに最適です。JPEG が必要な場合は、`SaveFormat.Jpeg` に変更すれば OK です。

## 手順 3: 各エクスポートページの名前を決めるコールバックを定義

ここで **save each page png** の魔法が実行されます。`PageSavingCallback` を割り当てることで、Aspose.Words に各ページのファイル名の決定を任せます。コールバックはページインデックス（0 ベース）を受け取るので、1 を加えて人間にとって分かりやすい名前にします。

```csharp
// Step 3: Define a callback to give each exported page a meaningful file name
imageSaveOptions.PageSavingCallback = (sender, args) =>
{
    // Files will be named Page_1.png, Page_2.png, ...
    args.PageFileName = $"Page_{args.PageIndex + 1}.png";
};
```

手動ループではなくコールバックを使う理由は何でしょうか？ライブラリが内部でページングを処理するため、オフバイワンエラーを回避でき、メモリ使用量も最適化されます—特に大きなドキュメントで **image export single page** シナリオの場合、ヒープが膨張するのを防げます。

## 手順 4: 各ページを個別の PNG 画像としてエクスポート

ここで Aspose.Words に各ページを個別の画像として扱うよう指示します。`ImageExportMode.SinglePage` 設定はまさにそれを行い、ページごとに 1 つの PNG を生成します。

```csharp
// Step 4: Export each page as a separate PNG image
imageSaveOptions.ExportImagesAs = ImageExportMode.SinglePage;
```

すべてのページを1枚の大きな画像に結合したい場合は、`ImageExportMode.MultiplePages` に切り替えてください。ただし、ほとんどのウェブギャラリーのユースケースでは、シングルページモードの方が整理しやすいです。

## 手順 5: ドキュメントを保存 – コールバックがファイルを生成

最後に `doc.Save` を呼び出し、出力パス（ここで指定した名前はコールバックが上書きするため無視されます）と設定したオプションを渡します。

```csharp
// Step 5: Save the document – the callback will generate one PNG per page
doc.Save("YOUR_DIRECTORY/output.png", imageSaveOptions);
```

この行が実行された後、`YOUR_DIRECTORY` に一連のファイルが作成されます：

```
Page_1.png
Page_2.png
Page_3.png
...
```

各 PNG は対応する Word ページのビジュアル（ヘッダー、フッター、埋め込み画像を含む）に相当します。

### 期待される出力

- **File format:** PNG（ロスレス、24 ビットカラー）
- **Resolution:** デフォルトで 96 dpi（`imageSaveOptions.Resolution` で調整可能）
- **Naming:** `Page_{n}.png`（`{n}` は 1 から開始）
- **Location:** 別のパスを指定しない限り、元のドキュメントと同じフォルダーに保存されます。

## 完全な動作例

すべてをまとめると、以下がコピー＆ペーストで使える完全なプログラムです：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Set up PNG export options
        ImageSaveOptions pngOptions = new ImageSaveOptions(SaveFormat.Png)
        {
            // Export each page as its own image
            ExportImagesAs = ImageExportMode.SinglePage,

            // Optional: increase resolution for sharper output (e.g., 300 dpi)
            // Resolution = 300
        };

        // Callback to name each PNG file
        pngOptions.PageSavingCallback = (sender, args) =>
        {
            args.PageFileName = $"Page_{args.PageIndex + 1}.png";
        };

        // Save – the callback creates Page_1.png, Page_2.png, …
        doc.Save("YOUR_DIRECTORY/output.png", pngOptions);

        Console.WriteLine("Conversion complete! Check YOUR_DIRECTORY for the PNG files.");
    }
}
```

このプログラムを実行すると、すぐに使える画像セットが得られます—プレビューサムネイル、メール添付、またはラスタ画像を期待する機械学習パイプラインへの入力に最適です。

## エッジケースと一般的なバリエーション

### 大きなドキュメント（> 500 ページ）

非常に大きなファイルを扱う場合、デフォルトのラスタライズ DPI が高すぎるとメモリ制限に達することがあります。`pngOptions.Resolution` を下げる（例: 72 dpi）か、`pngOptions.UsePdfRenderer = true` を有効にして PDF レンダラにページングを任せることで対策できます。

### カスタム命名スキーム

別の命名規則が必要な場合は、コールバックを以下のように調整してください：

```csharp
args.PageFileName = $"Chapter_{args.SectionIndex + 1}_Page_{args.PageIndex + 1}.png";
```

`SectionIndex` は、Word 文書が論理的なセクションに分割されている場合に便利です。

### 他のフォーマットへのエクスポート

下流システムが JPEG や TIFF を好む場合は、`SaveFormat.Png` を `SaveFormat.Jpeg` または `SaveFormat.Tiff` に変更してください。パイプラインの残りは同じです。

### 埋め込み画像の取り扱い

Aspose.Words は埋め込み画像、チャート、SmartArt を自動的にラスタライズします。ただし、元のベクタ資産だけが必要な場合は、`doc.GetChildNodes(NodeType.Shape, true)` で個別に抽出し、各 `Shape` を個別の画像として保存できます。

## よくある質問

**Q: この方法は `.doc` ファイルでも動作しますか？**  
A: はい、問題ありません。Aspose.Words は `.doc` と `.docx` の両方をサポートしています。`Document` コンストラクタに旧形式のファイルを指定すれば OK です。

**Q: PNG の背景色を制御できますか？**  
A: はい—`pngOptions.BackgroundColor` に `System.Drawing.Color.White`（または任意の `Color`）を設定します。

**Q: PNG の代わりに PDF が必要な場合は？**  
A: `ImageSaveOptions` を `PdfSaveOptions` に置き換え、`doc.Save("output.pdf", pdfOptions);` を呼び出します。ワークフローの残りは同じです。

## 結論

これで C# を使って **save word as images** するための堅実なエンドツーエンドソリューションが手に入りました。ドキュメントを読み込み、`ImageSaveOptions` を設定し、`PageSavingCallback` を活用し、`doc.Save` を呼び出すだけで、**convert word to png**、**save each page png**、そして **image export single page** の動作を制御できます—数行のコードで実現できます。

次のステップは？印刷品質のプレビュー用に DPI 設定を上げてみる、あるいはこの手法をオンデマンドで PNG を配信する Web API と組み合わせるなどです。また、画像を WebP に変換すればさらにファイルサイズを小さくできます—`SaveFormat` を変更し、圧縮オプションを調整するだけです。

コーディングを楽しんでください。問題があれば遠慮なくコメントを残してください！ 🚀

![save word as images example](placeholder.png "save word as images example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}