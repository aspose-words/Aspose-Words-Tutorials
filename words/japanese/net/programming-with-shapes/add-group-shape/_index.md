---
title: グループシェイプを追加
linktitle: グループシェイプを追加
second_title: Aspose.Words ドキュメント処理 API
description: この包括的なステップバイステップのチュートリアルでは、Aspose.Words for .NET を使用して Word 文書にグループ図形を追加する方法を学習します。
weight: 10
url: /ja/net/programming-with-shapes/add-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# グループシェイプを追加

## 導入

豊富なビジュアル要素を含む複雑なドキュメントの作成は、特にグループ図形を扱う場合には困難な作業になることがあります。しかし、心配はいりません。Aspose.Words for .NET は、このプロセスを簡素化し、非常に簡単にします。このチュートリアルでは、Word ドキュメントにグループ図形を追加する手順を説明します。準備はできましたか? さあ、始めましょう!

## 前提条件

始める前に、以下のものを用意してください。

1.  Aspose.Words for .NET: ダウンロードはこちらから[Aspose リリース ページ](https://releases.aspose.com/words/net/).
2. 開発環境: Visual Studio または .NET と互換性のあるその他の IDE。
3. C# の基本的な理解: C# プログラミングに精通していると有利です。

## 名前空間のインポート

まず、プロジェクトに必要な名前空間をインポートする必要があります。これらの名前空間は、Aspose.Words を使用して Word 文書を操作するために必要なクラスとメソッドへのアクセスを提供します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## ステップ1: ドキュメントを初期化する

まず最初に、新しい Word 文書を初期化しましょう。これは、グループ図形を追加する空白のキャンバスを作成するものと考えてください。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

ここ、`EnsureMinimum()`ドキュメントに必要な最小限のノード セットを追加します。

## ステップ2: GroupShapeオブジェクトを作成する

次に、`GroupShape`オブジェクト。このオブジェクトは他の図形のコンテナとして機能し、それらをグループ化することができます。

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## ステップ3: GroupShapeに図形を追加する

さて、個々の図形を追加してみましょう`GroupShape`コンテナー。アクセントの境界線の図形から始めて、アクション ボタンの図形を追加します。

### アクセントの境界線シェイプを追加する

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

このコードスニペットは、幅と高さが100単位のアクセントボーダーシェイプを作成し、それを`GroupShape`.

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

ここでは、アクションボタンの形状を作成し、配置して、`GroupShape`.

## ステップ4: GroupShapeの寸法を定義する

図形がグループ内にうまく収まるようにするには、図形の寸法を設定する必要があります。`GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

これは幅と高さを定義します`GroupShape`200 単位として、それに応じて座標サイズを設定します。

## ステップ5: GroupShapeをドキュメントに挿入する

さて、`GroupShape`文書に`DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder`ドキュメントに図形などのノードを簡単に追加できます。

## ステップ6: ドキュメントを保存する

最後に、指定したディレクトリにドキュメントを保存します。

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

これで完了です。グループ図形を含むドキュメントが完成しました。

## 結論

Word 文書にグループ図形を追加するのは、複雑なプロセスである必要はありません。Aspose.Words for .NET を使用すると、図形を簡単に作成および操作して、文書の見た目と機能性を向上させることができます。このチュートリアルで説明されている手順に従えば、すぐにプロになれます。

## よくある質問

### GroupShape に 2 つ以上の図形を追加できますか?
はい、必要な数だけ図形を追加できます。`GroupShape` . 使用するだけです`AppendChild`各形状に応じたメソッド。

### GroupShape 内の図形にスタイルを設定することは可能ですか?
もちろんです！各シェイプは、`Shape`クラス。

### ドキュメント内で GroupShape を配置するにはどうすればよいですか?
配置することができます`GroupShape`設定することで`Left`そして`Top`プロパティ。

### GroupShape 内の図形にテキストを追加できますか?
はい、図形にテキストを追加するには、`AppendChild`追加する方法`Paragraph`含む`Run`テキストを含むノード。

### ユーザー入力に基づいて図形を動的にグループ化することは可能ですか?
はい、プロパティとメソッドを適切に調整することで、ユーザー入力に基づいて図形を動的に作成およびグループ化できます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
