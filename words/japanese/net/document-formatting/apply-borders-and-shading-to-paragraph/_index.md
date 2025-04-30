---
"description": "Aspose.Words for .NET を使って、Word 文書の段落に罫線と網掛けを適用しましょう。ステップバイステップのガイドに従って、文書の書式設定を強化しましょう。"
"linktitle": "Word文書の段落に罫線と網掛けを適用する"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "Word文書の段落に罫線と網掛けを適用する"
"url": "/ja/net/document-formatting/apply-borders-and-shading-to-paragraph/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word文書の段落に罫線と網掛けを適用する

## 導入

こんにちは。Word文書に素敵な罫線や網掛けを加えて、目立たせたいと思ったことはありませんか？まさにうってつけの場所です！今日は、Aspose.Words for .NET を使って段落を華やかに演出する方法をご紹介します。たった数行のコードで、プロのデザイナーが手がけたような洗練された文書が完成するのを想像してみてください。準備はいいですか？さあ、始めましょう！

## 前提条件

さあ、袖をまくってコーディングに取り掛かる前に、必要なものがすべて揃っているか確認しましょう。簡単なチェックリストはこちらです。

- Aspose.Words for .NET: このライブラリをインストールする必要があります。ダウンロードは以下から行えます。 [Aspose ウェブサイト](https://releases。aspose.com/words/net/).
- 開発環境: Visual Studio または .NET をサポートするその他の IDE。
- C# の基本知識: コード スニペットを理解して調整できる程度の知識。
- 有効なライセンス： [一時ライセンス](https://purchase.aspose.com/temporary-license/) または購入したもの [アポーズ](https://purchase。aspose.com/buy).

## 名前空間のインポート

コードに進む前に、プロジェクトに必要な名前空間がインポートされていることを確認する必要があります。これにより、Aspose.Words の優れた機能をすべて利用できるようになります。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System.Drawing;
```

それでは、プロセスを簡単なステップに分解してみましょう。各ステップには見出しと詳細な説明が付いています。準備はいいですか？さあ、始めましょう！

## ステップ1: ドキュメントディレクトリを設定する

まず最初に、美しくフォーマットされたドキュメントを保存する場所が必要です。ドキュメントディレクトリへのパスを設定しましょう。

```csharp
// ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

このディレクトリに最終的な文書が保存されます。 `"YOUR DOCUMENT DIRECTORY"` マシン上の実際のパスを入力します。

## ステップ2: 新しいドキュメントとドキュメントビルダーを作成する

次に、新しいドキュメントを作成し、 `DocumentBuilder` オブジェクト。 `DocumentBuilder` ドキュメントを操作できる魔法の杖です。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

その `Document` オブジェクトはWord文書全体を表し、 `DocumentBuilder` コンテンツの追加とフォーマットに役立ちます。

## ステップ3: 段落の境界線を定義する

それでは、段落にスタイリッシュな枠線を追加してみましょう。テキストからの距離を定義し、さまざまな枠線のスタイルを設定します。

```csharp
BorderCollection borders = builder.ParagraphFormat.Borders;
borders.DistanceFromText = 20;
borders[BorderType.Left].LineStyle = LineStyle.Double;
borders[BorderType.Right].LineStyle = LineStyle.Double;
borders[BorderType.Top].LineStyle = LineStyle.Double;
borders[BorderType.Bottom].LineStyle = LineStyle.Double;
```

ここでは、テキストと枠線の間の距離を20ポイントに設定しています。すべての辺（左、右、上、下）の枠線は二重線になっています。素敵だと思いませんか？

## ステップ4：段落に網掛けを適用する

ボーダーは素晴らしいですが、陰影を付けてさらにワンランク上の効果を加えてみましょう。段落を際立たせるために、複数の色をブレンドした斜めの十字模様を使用します。

```csharp
Shading shading = builder.ParagraphFormat.Shading;
shading.Texture = TextureIndex.TextureDiagonalCross;
shading.BackgroundPatternColor = System.Drawing.Color.LightCoral;
shading.ForegroundPatternColor = System.Drawing.Color.LightSalmon;
```

このステップでは、背景色にライトコーラル、前景色にライトサーモンを使用した斜めの十字のテクスチャを適用しました。まるで段落にデザイナーの服を着せたような仕上がりです！

## ステップ5: 段落にテキストを追加する

テキストのない段落とは何でしょうか? サンプル文を追加して、書式設定の実際の動作を確認してみましょう。

```csharp
builder.Write("I'm a formatted paragraph with double border and nice shading.");
```

この行はテキストをドキュメントに挿入します。シンプルですが、スタイリッシュなフレームと影付きの背景で囲まれています。

## ステップ6: ドキュメントを保存する

最後に、作業内容を保存します。ドキュメントを、わかりやすい名前を付けて指定したディレクトリに保存しましょう。

```csharp
doc.Save(dataDir + "DocumentFormatting.ApplyBordersAndShadingToParagraph.doc");
```

これにより、ドキュメントは次のように保存されます。 `DocumentFormatting.ApplyBordersAndShadingToParagraph.doc` 先ほど指定したディレクトリにあります。

## 結論

これで完成です！たった数行のコードで、シンプルな段落が視覚的に魅力的なコンテンツに生まれ変わりました。Aspose.Words for .NETを使えば、驚くほど簡単にプロフェッショナルな書式設定をドキュメントに追加できます。レポート、手紙、その他あらゆる文書を作成する際に、これらのテクニックを活用すれば、素晴らしい印象を与えることができます。さあ、ぜひお試しください。あなたのドキュメントが生き生きと動き出すのを実感してください！

## よくある質問

### 境界線ごとに異なる線のスタイルを使用できますか?  
もちろんです！Aspose.Words for .NETでは、それぞれの境界線を個別にカスタマイズできます。 `LineStyle` ガイドに示されているように、各境界線の種類ごとに。

### 他にどのようなシェーディング テクスチャが利用できますか?  
使用できるテクスチャは、無地、横縞、縦縞など、いくつかあります。 [Aspose ドキュメント](https://reference.aspose.com/words/net/) 完全なリストについてはこちらをご覧ください。

### 境界線の色を変更するにはどうすればよいですか?  
境界線の色は、 `Color` 各境界線のプロパティを設定します。例えば、 `borders[BorderType。Left].Color = Color.Red;`.

### テキストの特定の部分に境界線や網掛けを適用することは可能ですか?  
はい、特定のテキスト部分に枠線や網掛けを適用することができます。 `Run` オブジェクト内の `DocumentBuilder`。

### このプロセスを複数の段落に対して自動化できますか?  
もちろんです！段落をループして、同じ境界線と網掛け設定をプログラムで適用できます。



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}