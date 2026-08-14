---
category: general
date: 2026-03-01
description: Aspose.Words を使用して PDF に矩形をすばやく追加します。形状を PDF に挿入する方法、PDF にグラフィックを追加する方法、カスタム
  シャドウを付けてプログラムから PDF ドキュメントを作成する方法を学びましょう。
draft: false
keywords:
- add rectangle to pdf
- insert shape pdf
- add graphics to pdf
- create pdf document programmatically
- create pdf with shape
language: ja
og_description: Aspose.Words を使用して PDF に矩形を追加します。このチュートリアルでは、PDF にシェイプを挿入し、PDF にグラフィックを追加し、C#
  でプログラム的に PDF ドキュメントを作成する方法を示します。
og_title: Aspose.WordsでPDFに矩形を追加する – 完全ガイド
tags:
- pdf
- aspnet
- csharp
- graphics
title: Aspose.WordsでPDFに矩形を追加する – ステップバイステップガイド
url: /ja/python/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words で PDF に矩形を追加する – 完全ガイド

PDF に **矩形を追加** したいと思ったことはありませんか？どの API 呼び出しが必要か分からないこともあるでしょう。開発者はよく「PDF に図形を挿入して、ファイルサイズを軽く保つにはどうすればいいか」 と質問します。良いニュースは、Aspose.Words ならとても簡単です。このチュートリアルでは、PDF ドキュメントをプログラムで作成するところから、矩形に影を付けてスタイリングするまでの全工程を解説します。

さらにいくつかの便利情報も紹介します：**PDF にグラフィックを追加** する方法、**PDF に図形を挿入** する正確な手順、そして **形状付き PDF を作成** する実行可能なサンプルです。外部参照は不要で、すぐにコピー＆ペーストできる自己完結型のソリューションです。

## 前提条件

- .NET 6.0 以降 (Aspose.Words は .NET Standard 2.0+ に対応)
- 有効な Aspose.Words for .NET ライセンスまたは一時評価キー
- Visual Studio 2022（またはお好みの IDE）
- 基本的な C# の知識—特別なことは不要で、コンソールアプリを実行できれば OK

以上です。これらが揃っていれば、すぐに始められます。

## 手順 1: PDF ドキュメントをプログラムで作成する

**PDF に矩形を追加** したいときに最初に行うのは、空のドキュメントを作成することです。`Document` クラスは白紙のキャンバスと考えてください。後から追加するすべての要素はこの中に配置されます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – initialise a new empty document
        Document doc = new Document();

        // The rest of the steps follow...
```

なぜ空のドキュメントから始めるのでしょうか？それは、すべての要素を完全にコントロールでき、後で隠れたページヘッダーやフッターと格闘する必要がないからです。

## 手順 2: DocumentBuilder を初期化して shape PDF を挿入する

`DocumentBuilder` は描画用のブラシです。テキストや画像、そして私たちにとって重要な図形を配置する方法を知っています。これがなければ、低レベルのノードツリーを自分で操作しなければならず、ほとんどの開発者にとっては悪夢です。

```csharp
        // Step 2 – create a builder that will let us add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

まだページは追加していないことに注意してください。ビルダーは最初に何かを挿入したときに自動的にページを作成するため、コードがすっきりします。

## 手順 3: 矩形シェイプを挿入する – “PDF に矩形を追加” の核心

さあ、楽しいパートです：矩形の挿入です。`InsertShape` メソッドは多数の `ShapeType` をサポートしています。ここでは `ShapeType.Rectangle` を選び、サイズを 200 × 100 ポイントに設定します。

```csharp
        // Step 3 – insert a rectangle (200 × 100 points) into the document
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

この時点で PDF にはシンプルな矩形が含まれています。今すぐファイルを開くと、1 ページ目の左上隅に単純な箱が表示されます。これが **PDF にグラフィックを追加** するための基礎です。

## 手順 4: 矩形にスタイルを適用 – カスタムシャドウの追加

スタイルのない矩形は退屈です。PDF がレンダリングされたときに目立つよう、控えめなドロップシャドウを付けましょう。`ShadowFormat` オブジェクトはぼかし半径から不透明度まで全てを制御します。

```csharp
        // Step 4 – configure a custom shadow for the shape
        ShadowFormat shadow = rectangle.ShadowFormat;
        shadow.Visible = true;
        shadow.BlurRadius = 8.0;          // pixels
        shadow.Distance = 5.0;           // points from the shape
        shadow.Direction = 45.0;         // degrees clockwise
        shadow.Opacity = 0.6;            // 0‑1 range
        shadow.Color = Color.Black;
```

なぜシャドウを付けるのでしょうか？見た目の向上だけでなく、重なったグラフィックを区別するのに役立ちます。これは、より複雑なレポートで **PDF にグラフィックを追加** する際に必要になることがあります。

## 手順 5: ファイルを保存 – “形状付き PDF を作成” ワークフローの完了

最後の行で全てをディスクに書き込みます。Aspose.Words は自動的に適切な PDF バージョンを選択し、必要なリソースを埋め込みます。

```csharp
        // Step 5 – save the document as a PDF file
        doc.Save(@"C:\Temp\ShapeWithShadow.pdf");
    }
}
```

`ShapeWithShadow.pdf` を開くと、ページ上にきれいな影付き矩形が表示されます。これが **PDF ドキュメントをプログラムで作成** する一連の流れで、コードは 30 行未満です。

## 完全動作例 – 最初から最後まで形状付き PDF を作成する

以下は新しいコンソールアプリプロジェクトにコピー＆ペーストできる完全なプログラムです。すべての `using` 文、`Main` メソッド、そして将来の参照用に簡単なコメントヘッダーが含まれています。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectanglePdfDemo
{
    /// <summary>
    /// Demonstrates how to add a rectangle to PDF, configure a shadow,
    /// and save the result using Aspose.Words for .NET.
    /// </summary>
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty PDF document
            Document doc = new Document();

            // 2️⃣ Initialise a DocumentBuilder – the tool that lets us add content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a rectangle shape (200 × 100 points) – this is the core of "add rectangle to pdf"
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

            // 4️⃣ Apply a custom shadow – makes the graphic stand out
            ShadowFormat shadow = rect.ShadowFormat;
            shadow.Visible = true;
            shadow.BlurRadius = 8.0;   // pixels
            shadow.Distance = 5.0;    // points
            shadow.Direction = 45.0;  // degrees
            shadow.Opacity = 0.6;     // semi‑transparent
            shadow.Color = Color.Black;

            // 5️⃣ Save the document – the final step in creating a PDF with shape
            string outputPath = @"C:\Temp\ShapeWithShadow.pdf";
            doc.Save(outputPath);

            Console.WriteLine($"PDF saved successfully to {outputPath}");
        }
    }
}
```

**期待結果:** 1 ページの PDF で、200 × 100 ポイントの矩形が左上付近に配置され、柔らかな 45 度の影が付いています。任意の PDF ビューアでファイルを開いて確認してください。

## よくある質問とエッジケース

### 他の形状タイプでも動作しますか？

もちろんです。`ShapeType.Rectangle` を `ShapeType.Ellipse`、`ShapeType.Triangle`、または Aspose.Words がサポートする 150 以上のオプションのいずれかに置き換えてください。同じ `ShadowFormat` プロパティが適用されます。

### 特定のページに矩形を配置したい場合は？

図形を挿入した後、`InsertShape` を呼び出す前にビルダーの `CurrentPage` プロパティを調整することで、別のページに移動できます。例:

```csharp
builder.MoveToPage(3);
Shape rectOnPage3 = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

### 矩形の塗りつぶし色を変更できますか？

はい、`FillColor` プロパティを使用します:

```csharp
rect.FillColor = Color.LightBlue;
```

### ファイルサイズへの影響は？

シンプルな形状と影を追加しても数キロバイト程度しか増えません。多数のグラフィックを重ねる場合は、画像を圧縮するか、ベクターベースの形状を使用して PDF を軽量に保つことを検討してください。

### 本番環境でライセンスは必要ですか？

Aspose.Words は評価モードでも動作しますが、出力 PDF には透かしが入ります。制限なく使用し、透かしを除去するにはライセンスを購入してください。

## ヒントとコツ（プロレベル）

- **バッチ挿入:** 数十個の矩形が必要な場合、座標コレクションをループし同じ `DocumentBuilder` を再利用すれば、パフォーマンスは線形のままです。
- **レイヤリング:** 矩形をテキストと同行させたい場合は `rect.WrapType = WrapType.Inline` を、テキストを回り込ませたい場合は `WrapType.Square` を設定してください。
- **PDF/A 準拠:** アーカイブ向け PDF が必要な場合は、保存前に `doc.CompatibilityOptions.OptimizeForPdfA = true;` を呼び出します。

## ビジュアルサマリー

![PDF に矩形を追加した例](https://example.com/rectangle-shadow.png "PDF に矩形を追加した例")

この画像は最終的な PDF レイアウトを示しています。控えめな影付きのシンプルな矩形で、コードが生成するものと同じです。

## 結論

これで、Aspose.Words を使用して **PDF に矩形を追加** する方法、**PDF に図形を挿入** する方法、そしてカスタムスタイルで **PDF にグラフィックを追加** する方法が分かりました。すべて **PDF ドキュメントをプログラムで作成** し、**形状付き PDF を作成** するサンプルで完了です。次は矩形をロゴに置き換えたり、複数の形状を組み合わせて簡単な図を作成してみてください。テキストの折り返しや回転、形状内へのハイパーリンク埋め込みなども試せます。API は豊富で、C# だけで静的な PDF をインタラクティブでグラフィック豊富なレポートに変換できます。

自由に試してみてください。問題があれば下にコメントを残してください。コーディングを楽しんで！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}