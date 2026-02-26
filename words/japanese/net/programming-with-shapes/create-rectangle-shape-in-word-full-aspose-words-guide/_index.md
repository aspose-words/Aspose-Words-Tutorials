---
category: general
date: 2026-02-26
description: Aspose.Words を使用して Word に長方形の図形を作成し、図形の追加方法、影の適用方法、透明度の設定方法を数分で学びましょう。
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: ja
og_description: Aspose.Words を使用して Word に長方形の図形を作成します。図形の追加、影の適用、透明度の設定をすばやく学びましょう。
og_title: Wordで長方形シェイプを作成 – 完全なAspose.Wordsガイド
tags:
- Aspose.Words
- C#
- Word Automation
title: Wordで長方形シェイプを作成 – 完全なAspose.Wordsガイド
url: /ja/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wordで矩形シェイプを作成 – 完全な Aspose.Words ガイド

Word ドキュメントに **矩形シェイプを作成** したいけど、どこから始めればいいか分からないことはありませんか？レポートや請求書の自動生成でこの壁にぶつかる開発者は多いです。このチュートリアルでは、**Word にシェイプを追加**し、さりげない影を適用し、シェイプの透明度を制御する方法を、Aspose.Words for .NET を使った完全な実行可能サンプルで解説します。

このガイドを読み終えると、洗練された影付きのクリーンな矩形が入った `.docx` ファイルが手に入ります。ブランディングや注釈、ドキュメントを少しだけプロフェッショナルに見せるのに最適です。外部ツールは不要、C# の数行で完了します。

## 必要なもの

- **Aspose.Words for .NET**（2026 年初頭時点の最新バージョン）。NuGet から取得できます（`Install-Package Aspose.Words`）。
- .NET 開発環境（Visual Studio、Rider、または C# 拡張機能付き VS Code）。
- C# の基本的な構文に慣れていること—特別な知識は不要、通常の `using` 文とオブジェクト生成ができれば OK です。

これらが揃っていれば、さっそく始めましょう。

## 矩形シェイプの作成 – 基本手順

以下が完全なソースコードです。新しいコンソールプロジェクトに貼り付け、**F5** キーで実行すると、指定したフォルダーに `ShadowDemo.docx` が生成されます。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### なぜこのコードが機能するのか

- **`Document`** はエントリーポイントで、Word ファイル全体を表します。
- **`Shape`** に `ShapeType.Rectangle` を指定することで、Aspose に矩形の描画オブジェクトを作成させます。
- **`Width`** と **`Height`** を設定するとシェイプのサイズが決まります。設定しないと極小のプレースホルダーになります。
- **`Shadow`** オブジェクトで、ぼかし、距離、方向、色、透明度、拡散といった視覚的要素を細かく調整できます。これが *apply shadow to shape* の核心です。
- 最後に **`AppendChild`** でシェイプを文書の最初の段落に挿入します。テーブルやヘッダーを扱わずに *add shape to Word* する最もシンプルな方法です。

`ShadowDemo.docx` を開くと、文書内にグレーの矩形が配置され、影が右下方向へ 45° の角度で伸びているのが確認できます。影は塊ではなく、ぼかし半径によってエッジが柔らかくなり、透明度が自然なドロップシャドウのように見えます。

![矩形シェイプの例](image.png "Aspose.Words を使用して Word に影付き矩形シェイプを作成")

*(上の画像はコードスニペットの最終結果を示しています。)*

## Word 文書へのシェイプ追加 – 配置オプション

この例では **最初の段落** にシェイプを入れていますが、実務では次のような場所に配置したいことがあります。

- 特定の **セクション** や **ヘッダー/フッター** にシェイプを挿入する。
- **テーブルセル** 内に配置して、表データと整列させる。
- **テキストラッピング** オプション（例：`WrapType.Square`）を使用し、周囲のテキストが矩形の周りを回り込むようにする。

以下は、カスタムスタイルの新しい段落にシェイプを入れる簡易バリエーションです。

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*プロのコツ:* シェイプのプロパティを設定した **後** にシェイプを追加してください。逆に追加してから設定すると、`UpdateLayout` を呼び出さないと見た目が更新されません。

## シェイプに影を適用 – ルックの微調整

影は文書の美観を大きく変えます。`Shadow` クラスが提供する主なプロパティは次の通りです。

| プロパティ      | 制御内容                                           | 典型的な値 |
|----------------|---------------------------------------------------|------------|
| `BlurRadius`   | 影のエッジの柔らかさ                               | 2.0 – 10.0 |
| `Distance`     | シェイプから影がどれだけ離れるか                     | 1.0 – 8.0  |
| `Direction`    | 角度（度） (0 = 左, 90 = 上)                        | 0 – 360    |
| `Color`        | 影の色 (`System.Drawing.Color` で指定)            | Gray, Black, カスタム |
| `Transparency` | 不透明度 (0 = 完全不透明, 1 = 完全透明)            | 0.0 – 0.5  |
| `Spread`       | ぼかしが適用される前の影の拡がり                     | 0.0 – 1.0  |

**控えめでプロフェッショナルな外観** を求めるなら、`BlurRadius` を 4‑6、`Transparency` を 0.2 前後に設定すると良いでしょう。**ドラマチックな効果** を狙う場合は、`Distance` を 6、`Direction` を 135°、`Transparency` を 0.05 程度に下げます。

## シェイプの透明度と影の拡散を設定

透明度は影だけでなく、矩形自体にも適用できます。

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

半透明の塗りつぶしに柔らかな影を組み合わせると、ダッシュボードやデザインモックアップに最適なモダンな UI 感覚が得られます。

### 注意すべきエッジケース

1. **古い Word バージョン**（2007 以前）は一部の影プロパティに対応していません。`.doc` ファイルを対象にする場合は、`BlurRadius` を 0 にするなど簡素化を検討してください。
2. **高 DPI ディスプレイ** では影の描画が若干異なることがあります。視覚的忠実度が重要な場合は、対象環境でテストしてください。
3. **シェイプが重なる場合** – Aspose はシェイプが追加された順に影を描画します。不要な被りを防ぐため、背面から前面へと順に挿入してください。

## 結果の保存と検証

`Document.Save` メソッドはファイル拡張子から出力形式を自動判別します。**`.docx`** ファイルの場合は Open XML 形式で保存され、ほとんどの最新 Word プロセッサが対応しています。同じビジュアルを保った **PDF** が必要な場合は、拡張子を変更するだけです。

```csharp
document.Save("ShadowDemo.pdf");
```

生成された `ShadowDemo.docx`（または `ShadowDemo.pdf`）を開くと、**影付き矩形** がきれいに表示されます。これで *create rectangle shape* と *apply shadow to shape* が Aspose.Words で正しく実行されたことが確認できます。

## よくある質問

**Q: 楕円など別のシェイプは使えますか？**  
A: もちろんです。`ShapeType.Rectangle` を `ShapeType.Ellipse`（または他の `ShapeType` 列挙値）に置き換えるだけです。影のプロパティはそのまま使用できます。

**Q: 矩形をクリック可能にしたい場合は？**  
A: シェイプにハイパーリンクを割り当てられます。

```csharp
rectangleShape.Href = "https://example.com";
```

**Q: .NET 6 以降でも動作しますか？**  
A: はい。Aspose.Words 23.11 以降は .NET 6、.NET 7、.NET 8 を完全にサポートしています。適切な NuGet パッケージを参照してください。

**Q: ブランドカラーに合わせて影の色を変更したいです。**  
A: 任意の `System.Drawing.Color` を使用できます。

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## まとめ

Word 文書に **矩形シェイプを作成**し、**シェイプを Word に追加**、**シェイプに影を適用**、そして **シェイプの透明度を設定**するために必要なすべてを網羅しました。ページ上部にある完全な実行可能コードと、各項目の解説で、サイズや色、影のパラメータを自由に調整できる自信がついたはずです。

次のステップに挑戦してみませんか？

- 複数のシェイプを重ねてバッジ効果を作る。
- 文書内容に応じて動的にサイズを算出する（例：テーブル列幅から幅を計算）。
- 影を保持したまま PDF や HTML へエクスポートする。

質問や問題があればコメントで教えてください。また、あなた独自の「影付き矩形」バリエーションもぜひシェアしてください。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}