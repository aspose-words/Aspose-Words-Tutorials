---
category: general
date: 2026-04-04
description: C# と Aspose.Words で長方形の図形を作成し、影を追加し、影にぼかしを適用し、影を透明にする方法をステップバイステップで学ぶガイド。
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: ja
og_description: Aspose.Words を使用して C# で矩形シェイプを作成します。影を追加し、影にぼかしを適用し、影を透明にする方法を簡潔なチュートリアルで学びましょう。
og_title: C#で矩形シェイプを作成し、影を追加する方法
tags:
- Aspose.Words
- C#
- Document Automation
title: C#で長方形シェイプを作成し、影を追加する方法
url: /ja/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で矩形シェイプを作成し、影を追加する方法

Word 文書で **矩形シェイプを作成** したいと思ったことはありませんか？しかし、さりげないドロップシャドウの付け方が分からない…という方は多いです。多くのレポートやブランディングのシーンでは、柔らかく半透明の影が付いたシンプルな矩形だけで、レイアウトが洗練された印象になります。

このチュートリアルでは、Aspose.Words を使って **ドキュメントの作成方法** を解説し、続いて **影の追加方法**、**影へのぼかしの適用**、さらには **影を透明にする** 方法を示します。最後まで読むと、数分で陰影の付いた矩形を含む *.docx* ファイルを生成する、すぐに実行できる C# スニペットが手に入ります。

## 必要なもの

- .NET 6 以降（API は .NET Framework 4.6+ でも動作します）
- Aspose.Words for .NET（この例では無料トライアルで動作します）
- コードエディタ – Visual Studio、VS Code、Rider、好きなもの
- 基本的な C# の知識 – 特別なことは不要、コンソールアプリを実行できれば OK

これらが揃っていれば、すぐに解決策に進みましょう。

## ステップ 1 – ドキュメントの作成方法とキャンバスの初期化

まず最初に、空の `Document` オブジェクトが必要です。これは、後で Aspose.Words が Word ファイルに変換する空白の紙と考えてください。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

`Document` をテンプレートから読み込むのではなくインスタンス化する理由は何でしょうか？ゼロから始めることで、隠れたスタイルやセクションが矩形に干渉することを防げます。また、ファイルサイズも極小に抑えられるため、ループで多数のドキュメントを生成する際の良い習慣となります。

## ステップ 2 – 矩形シェイプの作成（主要キーワードのコア）

ここで実際に **矩形シェイプを作成** します。`Shape` クラスは柔軟で、タイプ（Rectangle）、サイズ、周囲のテキストとの折り返し方法を指定できます。

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

オブジェクト初期化子構文を使用している点に注目してください。コードが簡潔になるだけでなく、後でプロパティの設定忘れを防げます。矩形は最初の段落内に配置され、次のステップでその段落を追加します。

## ステップ 3 – 影の追加方法と外観のカスタマイズ

影を追加するだけでなく、調整すべきプロパティがいくつかあります。ここで二次キーワードである **影へのぼかしの適用** と **影を透明にする** が活躍します。

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

数値に関する簡単な説明です。`BlurRadius` を 5 に設定するとやさしいフェザー効果が得られます。10 に上げるとより柔らかく、2 に下げるとくっきりしたエッジになります。`Transparency` の範囲は 0（不透明）から 1（完全に透明）です。ブランドのコントラスト要件に合わせて調整してください。

### プロのコツ

もしカラー影（例：企業のブルー）が必要な場合は、`Color.DarkGray` を `Color.FromArgb(80, 0, 120, 215)` に置き換えるだけです。最初の引数はアルファチャンネルで、低めに設定すると控えめな影になります。

## ステップ 4 – シェイプをドキュメントに挿入

矩形とその影の準備ができたら、ドキュメントの最初の段落に配置します。この手順により、シェイプがファイルの最上部に表示されます。

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

なぜ最初の段落なのか？ドキュメントが完全に空の場合でも安全に機能するデフォルトです。特定の位置（例：見出しの後）に挿入したい場合は、そのノードを取得してシェイプをそこに挿入します。

## ステップ 5 – ファイルを保存し結果を確認

最後に、ドキュメントをディスクに保存します。好きなパスを指定できますが、フォルダーが存在することを確認してください。

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

Microsoft Word で *ShadowRectangle.docx* を開くと、200 × 100 ポイントの矩形に、暗いグレーでややぼかされた 30 % 透明の影が右と下にそれぞれ 3 ポイントオフセットされているのが見えるはずです。この効果は控えめですが、平坦なレイアウトに奥行きを加えます。

![Aspose.Words で影付き矩形シェイプを作成](https://example.com/placeholder-image.png "Aspose.Words で影付き矩形シェイプを作成")

*画像の代替テキスト:* **Aspose.Words で影付き矩形シェイプを作成** – この画像は、影付き矩形が入った最終的なドキュメントを示しています。

## 一般的なバリエーションとエッジケース

### 影の色を動的に変更する

アプリケーションがテーマに対応している場合、設定ファイルから影の色を取得することができます。

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### シェイプをインライン以外にする

矩形をテキストの上に浮かせたい場合があります。その際は `WrapType` を `WrapType.Square` に変更し、`RelativeHorizontalPosition` を `RelativeHorizontalPosition.Margin` に設定すると、より細かい制御が可能です。

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### 複数ページの処理

各ページに矩形が必要な場合は、`doc.Sections` をループし、各セクションの最初の段落にクローンしたシェイプを追加します。影の設定も複製するために `rect.Clone(true)` を呼び出すことを忘れないでください。

## まとめ – 実現したこと

- Aspose.Words を使用して **矩形シェイプを作成** した
- **影の追加方法** を色、オフセット、ぼかし、透明度付きで実装
- **影へのぼかしの適用** と **影を透明にする** を実演
- すぐに開ける Word ファイルを保存

これらはほんの数行のコードで実現でき、洗練されたビジュアル調整が必ずしも重厚なグラフィックライブラリを必要としないことを示しています。

## 次にやること

- 他の `ShapeType`（Ellipse、Cloud など）を試して、影の挙動を確認する
- 矩形とテキストボックスを組み合わせて、ラベル付きコールアウトを作成する
- **ドキュメントの作成方法** のテンプレートにシェイプ用プレースホルダーを事前に用意し、プログラムで埋め込む方法を深掘りする

ブラー半径、色、透明度を自由に調整し、デザインに最適な影になるまで試してみてください。API は寛容で、コンソールアプリを再実行すれば変更がすぐに反映されます。

コーディングを楽しんでください。そして、あなたのドキュメントが常に奥行きを持つように！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}