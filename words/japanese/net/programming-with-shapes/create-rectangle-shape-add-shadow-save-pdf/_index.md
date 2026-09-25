---
category: general
date: 2026-02-24
description: C#でAspose.Wordsを使用して長方形のシェイプを作成し、シェイプに影を追加してドキュメントをPDFとして保存します。影の付け方とPDFの保存方法を数分で学びましょう。
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: ja
og_description: Aspose.Words を使用して C# で長方形シェイプを作成し、シェイプに影を追加してドキュメントを PDF として保存する
  – 完全なステップバイステップガイド。
og_title: 長方形を作成し、影を付けてPDFを保存
tags:
- Aspose.Words
- C#
- PDF generation
title: 長方形を作成し、影を付けてPDFを保存
url: /ja/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 長方形シェイプを作成し、影を付けてPDFとして保存

Word 文書で **create rectangle shape** が必要だったことはありませんか？ さらにきれいなドロップシャドウと PDF 出力も欲しい…そんな方は多いはずです。レポートや請求書生成プロジェクトでは、微妙な影といったビジュアルの磨きが「ただのファイル」から「プロフェッショナル品質の文書」へと差をつけます。

このチュートリアルでは、**Aspose.Words for .NET** を使って長方形シェイプを作成し、影を付け、最終的に **save document as PDF** する手順を詳しく解説します。最後まで読むと、影付き長方形を生成する C# コンソール アプリが完成し、影の調整やエクスポート オプションの変更方法も理解できます。

## 必要なもの

- .NET 6 SDK（または最近の .NET バージョン） – API は .NET Framework 4.x でも同様に動作します。  
- Aspose.Words for .NET NuGet パッケージ（`Aspose.Words`） – `dotnet add package Aspose.Words` でインストールします。  
- コード エディタ – Visual Studio、VS Code、Rider のいずれかで構いません。  

このサンプルでは追加のライセンス手順は不要です。無料評価モードで PDF 出力を確認できます。

## 手順 1: プロジェクトを作成し名前空間をインポート

まずはコンソール プロジェクトを作成し、必要なクラスをインポートします。

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*ポイント*: `Document` と `DocumentBuilder` がキャンバスを提供し、`Shape` と `ShadowFormat` が長方形の描画とスタイル設定を行います。事前にインポートしておくと、後のコードがすっきりします。

## 手順 2: **Create rectangle shape** を希望サイズで作成

空のドキュメントを作成し、長方形を挿入します。`InsertShape` メソッドはすぐにスタイル設定できる `Shape` オブジェクトを返します。

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*解説*: サイズはポイント単位（1 pt = 1/72 in）で指定します。レイアウトに合わせて数値を調整してください。影が際立つように、シェイプには淡いブルーの塗りを設定しています。

## 手順 3: **Add shadow to shape** – 影の細かい調整

影は単なる「オン/オフ」ではありません。色、ぼかし、距離、方向、透明度まで制御できます。多くのレポートでうまく機能する実用的な設定例を示します。

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*これらの値を変更する理由*:  
- **BlurRadius** – ぼかしを大きくすると夢幻的な効果に、小さくするとくっきりしたエッジになります。  
- **Direction** – 0° が右向き、90° が下向き、180° が左向きなど。ページレイアウトに合わせて回転させます。  
- **Transparency** – `0` で不透明な影、`0.5` で半透明など、好みの透明度に設定できます。

### 影の付け方 – 代替アプローチ

**multiple‑layer shadow**（例: 外側は濃い影、内側は薄い影）を実現したい場合は、別のシェイプを作成してオフセットし、異なる `ShadowFormat` を設定します。あるいは「ぼかしなし」外観が欲しいときは `BlurRadius = 0` にします。

## 手順 4: **Save document as PDF** – 最終エクスポート

長方形と影の設定が完了したら、PDF として書き出します。Aspose.Words が内部で変換を行うので、`Save` に目的のフォーマットを指定するだけです。

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*ヒント*: PDF の準拠レベル（PDF/A、PDF/X）やフォント埋め込みを制御したい場合は、以下のオーバーロードを使用します。

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

これが **how to save pdf** の要点です。

## 完全な実行可能サンプル

以下は `Program.cs` にそのまま貼り付けて使用できる完全プログラムです。フォルダーが存在すればそのままコンパイル・実行できます。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### 期待される結果

生成された `ShadowRectangle.pdf` を開くと、淡いブルーの長方形と、右下方向（45°）にオフセットされたソフトなグレーの影が1ページに表示されます。PDF は最新のリーダー（Adobe Acrobat、Edge、Chrome）で問題なく閲覧可能です。

![PDFで影付きの長方形シェイプを作成](/images/shadow-rectangle.png "Create rectangle shape with shadow in PDF")

*(画像の alt テキストは SEO 用の主要キーワードを含んでいます。)*

## よくある質問とエッジケースの対処法

**PDF で影が消えてしまう場合**  
Aspose.Words の最新バージョン（≥23.3）を使用してください。古いビルドでは一部の影プロパティが PDF 変換時に無視されるバグがありました。

**ブランドカラーに合わせて影の色を変えられるか**  
もちろん可能です。`System.Drawing.Color.Gray` を任意の `Color` に置き換えてください。例: `Color.FromArgb(128, 0, 0, 255)` で半透明の青にできます。

**他のシェイプ（楕円、星形など）に影を付けるには**  
`ShadowFormat` はすべての `Shape` オブジェクトで共通です。シェイプ作成後に `ShadowFormat` を取得し、プロパティを設定します。

**DPI やスケーリングの問題は？**  
PDF の描画はシェイプのポイントサイズを尊重します。印刷用に高解像度が必要な場合は、シェイプのサイズを大きくするか、`PdfSaveOptions.ImageResolution` を設定してください。

**PNG など他形式へのエクスポートは可能か**  
可能です。`document.Save("output.png", SaveFormat.Png)` とすれば影付きの画像が生成されます。

## プロのコツとベストプラクティス

- **Builder の再利用**: 複数シェイプを追加する場合は、`DocumentBuilder` インスタンスを1つだけ保持するとオーバーヘッドが減ります。  
- **バッチ保存**: ループで多数の PDF を生成する際は、`PdfSaveOptions` オブジェクトを使い回して不要な割り当てを防ぎます。  
- **テスト**: 保存後は必ず PDF を開き、影が期待通りに表示されているか確認してください。PDF ビューアによっては影の描画が若干異なることがありますが、Adobe Acrobat が最も信頼できる基準です。  
- **パフォーマンス**: 大規模文書では、`DocumentBuilder.InsertShape` の自動改ページを無効にするために `builder.PageSetup.DifferentFirstPageHeaderFooter = false` を設定すると効果的です（必要なければ）。

## 結論

Aspose.Words for .NET を使用して **create rectangle shape**、**add shadow to shape**、そして **save document as PDF** する方法をすべて解説しました。コードはコンパクトで概念も明確ですので、他のシェイプや影スタイル、エクスポート オプションを試すための土台として活用してください。

次のステップは、長方形を丸みを帯びた …  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}