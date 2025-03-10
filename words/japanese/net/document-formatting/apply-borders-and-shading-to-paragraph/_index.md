---
title: Word 文書の段落に罫線と網かけを適用する
linktitle: Word 文書の段落に罫線と網かけを適用する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word 文書の段落に境界線と網掛けを適用します。ステップ バイ ステップ ガイドに従って、文書の書式設定を強化します。
weight: 10
url: /ja/net/document-formatting/apply-borders-and-shading-to-paragraph/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 文書の段落に罫線と網かけを適用する

## 導入

こんにちは。Word 文書に派手な境界線や網掛けを加えて目立たせる方法を考えたことはありませんか? まさにその通りです! 今日は、段落を華やかにするために Aspose.Words for .NET の世界に飛び込んでみましょう。ほんの数行のコードで、プロのデザイナーの作品のように洗練された文書を作成できると想像してみてください。準備はできましたか? さあ、始めましょう!

## 前提条件

袖をまくってコーディングに取り掛かる前に、必要なものがすべて揃っていることを確認しましょう。簡単なチェックリストを以下に示します。

-  Aspose.Words for .NET: このライブラリをインストールする必要があります。[Aspose ウェブサイト](https://releases.aspose.com/words/net/).
- 開発環境: Visual Studio または .NET をサポートするその他の IDE。
- C# の基本知識: コード スニペットを理解して調整するのに十分です。
- 有効なライセンス:[一時ライセンス](https://purchase.aspose.com/temporary-license/)または購入したもの[アポーズ](https://purchase.aspose.com/buy).

## 名前空間のインポート

コードに進む前に、プロジェクトに必要な名前空間がインポートされていることを確認する必要があります。これにより、Aspose.Words のすべての優れた機能にアクセスできるようになります。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System.Drawing;
```

それでは、プロセスを細かいステップに分解してみましょう。各ステップには見出しと詳細な説明があります。準備はいいですか? さあ、始めましょう!

## ステップ1: ドキュメントディレクトリを設定する

まず最初に、美しくフォーマットされたドキュメントを保存する場所が必要です。ドキュメント ディレクトリへのパスを設定しましょう。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

このディレクトリは最終的な文書が保存される場所です。`"YOUR DOCUMENT DIRECTORY"`マシン上の実際のパスを使用します。

## ステップ2: 新しいドキュメントとDocumentBuilderを作成する

次に、新しいドキュメントを作成し、`DocumentBuilder`オブジェクト。`DocumentBuilder`ドキュメントを操作できる魔法の杖です。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

の`Document`オブジェクトはWord文書全体を表し、`DocumentBuilder`コンテンツの追加とフォーマットに役立ちます。

## ステップ3: 段落の境界線を定義する

次に、段落にスタイリッシュな境界線を追加してみましょう。テキストからの距離を定義し、さまざまな境界線のスタイルを設定します。

```csharp
BorderCollection borders = builder.ParagraphFormat.Borders;
borders.DistanceFromText = 20;
borders[BorderType.Left].LineStyle = LineStyle.Double;
borders[BorderType.Right].LineStyle = LineStyle.Double;
borders[BorderType.Top].LineStyle = LineStyle.Double;
borders[BorderType.Bottom].LineStyle = LineStyle.Double;
```

ここでは、テキストと境界線の間の距離を 20 ポイントに設定しています。すべての辺 (左、右、上、下) の境界線は二重線に設定されています。素敵だと思いませんか?

## ステップ4: 段落に網掛けを適用する

境界線は素晴らしいですが、陰影を付けてさらにレベルアップさせましょう。段落を目立たせるために、色を混ぜた斜めの十字のパターンを使用します。

```csharp
Shading shading = builder.ParagraphFormat.Shading;
shading.Texture = TextureIndex.TextureDiagonalCross;
shading.BackgroundPatternColor = System.Drawing.Color.LightCoral;
shading.ForegroundPatternColor = System.Drawing.Color.LightSalmon;
```

このステップでは、背景色にライトコーラル、前景色にライトサーモンを使用した斜めの十字のテクスチャを適用しました。段落にデザイナーの服を着せたような感じです。

## ステップ5: 段落にテキストを追加する

テキストのない段落とは何でしょうか? サンプル文を追加して、書式設定の実際の動作を確認してみましょう。

```csharp
builder.Write("I'm a formatted paragraph with double border and nice shading.");
```

この行は、ドキュメントにテキストを挿入します。シンプルですが、スタイリッシュなフレームと影付きの背景で囲まれています。

## ステップ6: ドキュメントを保存する

最後に、作業内容を保存します。ドキュメントを、わかりやすい名前で指定したディレクトリに保存しましょう。

```csharp
doc.Save(dataDir + "DocumentFormatting.ApplyBordersAndShadingToParagraph.doc");
```

これにより、ドキュメントは次のような名前で保存されます。`DocumentFormatting.ApplyBordersAndShadingToParagraph.doc`先ほど指定したディレクトリにあります。

## 結論

これで完了です。わずか数行のコードで、単純な段落を視覚的に魅力的なコンテンツに変換できました。Aspose.Words for .NET を使用すると、ドキュメントにプロフェッショナルな書式設定を簡単に追加できます。レポート、手紙、その他のドキュメントを作成する場合でも、これらのトリックは優れた印象を与えるのに役立ちます。さあ、試してみて、ドキュメントが生き生きと動くのを見てください。

## よくある質問

### 境界線ごとに異なる線のスタイルを使用できますか?  
もちろんです！Aspose.Words for .NETでは、各境界線を個別にカスタマイズできます。`LineStyle`ガイドに示されているように、各境界線の種類ごとに。

### 他にどのようなシェーディングテクスチャが利用できますか?  
使用できるテクスチャは、無地、横縞、縦縞などいくつかあります。[Aspose ドキュメント](https://reference.aspose.com/words/net/)完全なリストについてはこちらをご覧ください。

### 境界線の色を変更するにはどうすればよいですか?  
境界線の色は、`Color`各境界線のプロパティを設定します。たとえば、`borders[BorderType.Left].Color = Color.Red;`.

### テキストの特定の部分に境界線や網掛けを適用することは可能ですか?  
はい、特定のテキスト部分に境界線や網掛けを適用することができます。`Run`オブジェクト内の`DocumentBuilder`.

### 複数の段落に対してこのプロセスを自動化できますか?  
もちろんです! 段落をループして、同じ境界線と網掛け設定をプログラムで適用できます。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
