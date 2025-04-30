---
"description": "Aspose.Words for .NET を使用して、Word 文書内の図形の境界ポイントを正確に取得する方法を学びます。この詳細なガイドで、正確な図形操作を習得しましょう。"
"linktitle": "実際の形状境界ポイントを取得する"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "実際の形状境界ポイントを取得する"
"url": "/ja/net/programming-with-shapes/get-actual-shape-bounds-points/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 実際の形状境界ポイントを取得する

## 導入

Word文書で図形を操作しようとした際に、正確な寸法が分からず戸惑ったことはありませんか？図形の正確な境界を知ることは、様々な文書編集や書式設定の作業において非常に重要です。詳細なレポート、魅力的なニュースレター、洗練されたチラシなどを作成する場合でも、図形の寸法を理解することで、完璧なデザインを実現できます。このガイドでは、Aspose.Words for .NETを使用して、図形の実際の境界をポイント単位で取得する方法を詳しく説明します。完璧な図形を作成する準備はできましたか？さあ、始めましょう！

## 前提条件

本題に入る前に、必要なものがすべて揃っていることを確認しましょう。

1. Aspose.Words for .NET: Aspose.Words for .NETライブラリがインストールされていることを確認してください。インストールされていない場合はダウンロードできます。 [ここ](https://releases。aspose.com/words/net/).
2. 開発環境: Visual Studio などの開発環境をセットアップする必要があります。
3. C# の基本知識: このガイドでは、C# プログラミングの基本を理解していることを前提としています。

## 名前空間のインポート

まず、必要な名前空間をインポートしましょう。これは、Aspose.Words for .NET が提供するクラスとメソッドにアクセスできるようになるため、非常に重要です。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## ステップ1：新しいドキュメントを作成する

まず、新しいドキュメントを作成する必要があります。このドキュメントは、図形を挿入したり操作したりするためのキャンバスになります。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

ここでは、 `Document` クラスと `DocumentBuilder` ドキュメントにコンテンツを挿入するのに役立ちます。

## ステップ2: 画像シェイプを挿入する

次に、ドキュメントに画像を挿入しましょう。この画像は図形として機能し、後でその境界を取得します。

```csharp
Shape shape = builder.InsertImage("YOUR DOCUMENT DIRECTORY/Transparent background logo.png");
```

交換する `"YOUR DOCUMENT DIRECTORY/Transparent background logo.png"` 画像ファイルへのパスを指定します。この行は、画像を図形としてドキュメントに挿入します。

## ステップ3: アスペクト比のロックを解除する

この例では、図形のアスペクト比をロック解除します。この手順はオプションですが、図形のサイズを変更する場合は便利です。

```csharp
shape.AspectRatioLocked = false;
```

アスペクト比のロックを解除すると、元の比率を維持せずに図形のサイズを自由に変更できます。

## ステップ4: 図形の境界を取得する

いよいよ、図形の実際の境界をポイント単位で取得する、エキサイティングな部分です。この情報は、正確な配置とレイアウトに不可欠な場合があります。

```csharp
Console.Write("\nGets the actual bounds of the shape in points: ");
Console.WriteLine(shape.GetShapeRenderer().BoundsInPoints);
```

その `GetShapeRenderer` メソッドは図形のレンダラーを提供し、 `BoundsInPoints` 正確な寸法を教えてくれます。

## 結論

これで完了です！Aspose.Words for .NET を使って、図形の実際の境界をポイント単位で取得できました。この知識があれば、図形を正確に操作・配置できるようになり、ドキュメントを思い描いた通りの見た目に仕上げることができます。複雑なレイアウトをデザインする場合でも、単に要素を微調整する場合でも、図形の境界を理解することは大きな変化をもたらします。

## よくある質問

### 図形の境界を知ることはなぜ重要なのでしょうか?
境界を把握しておくと、ドキュメント内の図形の正確な配置と整列に役立ち、プロフェッショナルな外観が保証されます。

### 画像以外の種類の図形も使用できますか?
もちろんです！長方形、円、カスタム描画など、あらゆる形状を使用できます。

### 画像がドキュメントに表示されない場合はどうすればよいですか?
ファイルパスが正しく、画像がその場所に存在することを確認してください。入力ミスやディレクトリ参照の誤りがないか再度確認してください。

### 図形のアスペクト比を維持するにはどうすればよいでしょうか?
セット `shape.AspectRatioLocked = true;` サイズ変更時に元の比率を維持するため。

### ポイント以外の単位で境界を取得することは可能ですか?
はい、適切な変換係数を使用して、ポイントをインチやセンチメートルなどの他の単位に変換できます。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}