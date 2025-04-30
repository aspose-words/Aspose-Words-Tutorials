---
"description": "この包括的なステップバイステップのチュートリアルでは、Aspose.Words for .NET を使用して Word 文書にグループ図形を追加する方法を学習します。"
"linktitle": "グループ図形を追加"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "グループ図形を追加"
"url": "/ja/net/programming-with-shapes/add-group-shape/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# グループ図形を追加

## 導入

豊富なビジュアル要素を含む複雑なドキュメントの作成は、時に困難な作業になることがあります。特にグループ図形を扱う場合はなおさらです。でもご安心ください！Aspose.Words for .NET はこのプロセスを簡素化し、驚くほど簡単にできます。このチュートリアルでは、Word ドキュメントにグループ図形を追加する手順を詳しく説明します。準備はできましたか？さあ、始めましょう！

## 前提条件

始める前に、以下のものを用意してください。

1. Aspose.Words for .NET: ダウンロードはこちらから [Aspose リリースページ](https://releases。aspose.com/words/net/).
2. 開発環境: Visual Studio または .NET と互換性のあるその他の IDE。
3. C# の基本的な理解: C# プログラミングに精通していると有利です。

## 名前空間のインポート

まず、プロジェクトに必要な名前空間をインポートする必要があります。これらの名前空間は、Aspose.Words で Word 文書を操作するために必要なクラスとメソッドへのアクセスを提供します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## ステップ1: ドキュメントを初期化する

まずは、新しいWord文書を初期化しましょう。これは、グループ図形を追加するための空白のキャンバスを作成するようなものです。

```csharp
// ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

ここ、 `EnsureMinimum()` ドキュメントに必要な最小限のノード セットを追加します。

## ステップ2: GroupShapeオブジェクトを作成する

次に、 `GroupShape` オブジェクト。このオブジェクトは他の図形のコンテナとして機能し、それらをグループ化することができます。

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## ステップ3: GroupShapeに図形を追加する

さて、個々の図形を追加してみましょう `GroupShape` コンテナです。まずアクセントの境界線の図形を追加し、次にアクションボタンの図形を追加します。

### アクセントボーダーシェイプの追加

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

このコードスニペットは、幅と高さが100単位のアクセントボーダーシェイプを作成し、それを `GroupShape`。

### アクションボタンの形状を追加する

```csharp
Shape actionButtonShape = new Shape(doc, ShapeType.ActionButtonBeginning)
{
    Left = 100,
    Width = 100,
    Height = 200
};
groupShape.AppendChild(actionButtonShape);
```

ここでは、アクションボタンの形状を作成し、配置して、 `GroupShape`。

## ステップ4: GroupShapeの寸法を定義する

図形がグループ内にうまく収まるようにするには、図形の寸法を設定する必要があります。 `GroupShape`。

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

これは、 `GroupShape` 200 単位として、それに応じて座標サイズを設定します。

## ステップ5: GroupShapeをドキュメントに挿入する

さて、 `GroupShape` 文書に `DocumentBuilder`。

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder` 図形を含むノードをドキュメントに簡単に追加できます。

## ステップ6: ドキュメントを保存する

最後に、ドキュメントを指定したディレクトリに保存します。

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

これで完了です。グループ図形を含むドキュメントが完成しました。

## 結論

Word文書にグループ図形を追加するのは、必ずしも複雑な作業ではありません。Aspose.Words for .NETを使えば、図形を簡単に作成・操作できるため、文書の見た目と機能性をより魅力的にすることができます。このチュートリアルの手順に従えば、すぐにプロ並みの使いこなせるようになります！

## よくある質問

### GroupShape に 2 つ以上の図形を追加できますか?
はい、必要なだけ図形を追加できます。 `GroupShape`使用するだけです `AppendChild` 各図形に対するメソッド。

### GroupShape 内の図形にスタイルを設定することは可能ですか?
もちろんです！各図形は、 `Shape` クラス。

### ドキュメント内で GroupShape を配置するにはどうすればよいですか?
配置することができます `GroupShape` 設定することで `Left` そして `Top` プロパティ。

### GroupShape 内の図形にテキストを追加できますか?
はい、図形にテキストを追加できます。 `AppendChild` 追加する方法 `Paragraph` 含む `Run` テキストを含むノード。

### ユーザー入力に基づいて図形を動的にグループ化することは可能ですか?
はい、プロパティとメソッドを適切に調整することで、ユーザー入力に基づいて図形を動的に作成およびグループ化できます。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}