---
category: general
date: 2025-12-29
description: Aspose.Words C# を使用して Word 文書に矩形シェイプを作成します。シェイプの透明度の設定、影の色の設定方法を学び、Word
  文書を簡単に保存できます。
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: ja
og_description: Aspose.Words C# を使用して Word 文書に矩形シェイプを作成します。このガイドでは、シェイプの透明度の設定、影の色の設定、そして
  Word 文書の保存方法を示します。
og_title: Wordで長方形シェイプを作成 – 完全なAspose.Wordsチュートリアル
tags:
- Aspose.Words
- C#
- Word Automation
title: Aspose.WordsでWordに長方形の図形を作成する – ステップバイステップガイド
url: /ja/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word で長方形シェイプを作成 – 完全 Aspose.Words チュートリアル

Word 文書で **長方形シェイプを作成** したいけど、どこから始めればいいか分からないことはありませんか？レポートや請求書の自動生成でこの壁にぶつかる開発者は多いです。このガイドでは、長方形シェイプの作成、シェイプの透明度設定、影の色設定、そして最終的に Aspose.Words for .NET を使用して **Word 文書を保存** する手順を詳しく解説します。

最初の Document オブジェクトからディスク上の最終的な `.docx` ファイルまでを網羅するので、最後には **プログラムで Word 文書を作成** できるようになります。外部参照は不要で、プロジェクトにコピペできる自己完結型のソリューションです。

## 前提条件

- .NET 6.0 以降（コードは .NET Framework 4.7+ でも動作します）
- Aspose.Words for .NET NuGet パッケージ（`Install-Package Aspose.Words`）
- C# の基本的な構文に慣れていること
- お好みの IDE（Visual Studio、Rider、VS Code など）

> **プロのコツ:** Aspose.Words の無料トライアルを使用している場合、出力ファイルに透かしが追加されます。本番環境では有効なライセンスが必要です。

## 手順 1: Document と Builder の初期化

まず、空の Word 文書とコンテンツ挿入用の `DocumentBuilder` を作成します。Builder はページ上に描画する仮想ペンのようなものです。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **なぜ重要か:** `DocumentBuilder` がないと、低レベルのノードツリーを直接操作しなければならず、エラーが起きやすく可読性も低くなります。

## 手順 2: 長方形シェイプの作成

ここで実際に **長方形シェイプを作成** します。`InsertShape` メソッドは `ShapeType` 列挙体、幅、高さ（ポイント単位）を受け取ります。返される `Shape` オブジェクトで後から視覚プロパティを調整できます。

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

この時点で、長方形は現在の段落に固定された黒い実体のボックスです。必要に応じて移動、サイズ変更、回転も可能です。

![create rectangle shape with shadow](/images/rectangle-shadow.png "Word 文書内に灰色の影が付いた長方形シェイプが表示されています")

*画像代替テキスト: Word 文書内に影付きの長方形シェイプを作成*

## 手順 3: シェイプの透明度設定

透明度はシェイプの塗りの「透け具合」を表します。Aspose.Words の `Transparency` プロパティは `0.0`（不透明）から `1.0`（完全透明）までの範囲です。ここでは **シェイプの透明度を 40 %** に設定し、下のテキストが読みやすいようにします。

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **エッジケース:** 完全に見えないシェイプにしたいが影は残したい場合は、`Transparency` を `1.0` に設定し、アウトラインをゼロ以外にします。

## 手順 4: 影の設定

さりげないドロップシャドウで奥行きを加えます。**影の色**を中間のグレーに設定し、ぼかし半径と水平・垂直オフセットを数ポイント調整します。

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **なぜ重要か:** 影が鋭すぎたり暗すぎると、印刷時のアーティファクトのように見えてしまいます。`Blur` と `Transparency` を調整して自然な見た目にしましょう。

## 手順 5: Word 文書の保存

最後に **Word 文書をディスクに保存** します。`Save` メソッドは拡張子から自動的にファイル形式を判別します。`.docx` は最新の OpenXML 形式です。

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

フォルダーが存在しない場合、Aspose.Words は `ArgumentException` をスローします。パスが有効か確認するか、事前にディレクトリを作成してください。

## 完全動作サンプル

以下はすべての手順をまとめた、すぐに実行できるプログラムです。新しいコンソールプロジェクトに貼り付けて **F5** を押すだけです。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### 期待される結果

`ShadowRectangle.docx` を Microsoft Word で開くと、薄いグレーの長方形に柔らかく少しずれた影が付いており、透明度は 40 % で表示されます。シェイプは空白ページ上に配置され、追加コンテンツを入れる準備ができています。

## よくある質問とバリエーション

**別のシェイプが必要な場合は？**  
`ShapeType.Rectangle` を他の列挙値（`Ellipse`、`Triangle`、`Star` など）に置き換えるだけです。残りのコードは同じです。

**アウトラインの色を変更できますか？**  
はい。`rectangleShape.StrokeColor = System.Drawing.Color.Blue;` のように設定し、必要に応じて `rectangleShape.StrokeWeight = 1.5;` も指定できます。

**ページ上の特定位置にシェイプを配置したい場合は？**  
`rectangleShape.WrapType = WrapType.None;` とし、`rectangleShape.Left` と `rectangleShape.Top`（単位はポイント）を調整します。

**長方形の中にテキストを入れられますか？**  
もちろん可能です。シェイプ作成後に `rectangleShape.AppendChild(new Paragraph(document))` を呼び、`Run` にテキストを追加します。リッチな書式が必要なら `rectangleShape.TextBox` プロパティを設定。

## プロのコツと落とし穴

- **早めにライセンスを適用:** ライセンスを忘れると、Aspose.Words が最初のページに透かしを挿入します。テスト時に混乱の元です。
- **パフォーマンスのコツ:** ループで多数の文書を生成する場合、単一の `Document` インスタンスを再利用し、各保存後に `document.RemoveAllChildren();` を呼んで GC 圧力を抑えます。
- **影の見え方:** 低解像度ディスプレイでは微細な影が見えにくいことがあります。デバッグ時は `Blur` や `OffsetX/Y` を大きめに設定し、最終的に調整してください。

## 次のステップ

**長方形シェイプの作成**、**シェイプの透明度設定**、**影の色設定**、**Word 文書の保存** ができたら、以下の拡張を検討してください。

- 複数のシェイプを追加し、グループ化する。
- テーブルセル内に長方形を挿入してレポートレイアウトを作る。
- `DocumentBuilder.InsertHtml` と組み合わせて HTML スタイルのコンテンツを重ねる。
- `Glow` や `Reflection` などの他のビジュアルエフェクトを試し、より UI ライクな文書を作成する。

実験し、失敗し、そして改善する――プログラムによる文書生成は、デザインとコードが出会う遊び場です。

---

*コーディングを楽しんでください！問題があれば下のコメントで教えてください。一緒にトラブルシュートします。*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}