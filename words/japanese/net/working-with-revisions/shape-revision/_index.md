---
"description": "この包括的なガイドでは、Aspose.Words for .NET を使用して Word 文書内の図形の修正を処理する方法を学びます。変更の追跡、図形の挿入などをマスターしましょう。"
"linktitle": "形状修正"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "形状修正"
"url": "/ja/net/working-with-revisions/shape-revision/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 形状修正

## 導入

Word文書をプログラムで編集するのは、特に図形を扱うとなると大変な作業になりがちです。レポートの作成、テンプレートのデザイン、あるいは単に文書作成を自動化する場合でも、図形の修正履歴を追跡・管理する機能は不可欠です。Aspose.Words for .NETは、このプロセスをシームレスかつ効率的にする強力なAPIを提供します。このチュートリアルでは、Word文書内の図形の修正方法を詳しく説明し、文書管理を容易にするためのツールと知識を習得できるようにします。

## 前提条件

コードに進む前に、必要なものがすべて揃っていることを確認しましょう。

- Aspose.Words for .NET: Aspose.Wordsライブラリがインストールされていることを確認してください。 [ここからダウンロード](https://releases。aspose.com/words/net/).
- 開発環境: Visual Studio などの開発環境をセットアップする必要があります。
- C# の基本的な理解: C# プログラミング言語とオブジェクト指向プログラミングの基本概念に精通していること。
- Word 文書: 作業に使用する Word 文書、またはチュートリアル中に作成することもできます。

## 名前空間のインポート

まず、必要な名前空間をインポートしましょう。これにより、Word文書や図形の処理に必要なクラスとメソッドにアクセスできるようになります。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## ステップ1: ドキュメントディレクトリの設定

図形の操作を始める前に、ドキュメントディレクトリへのパスを定義する必要があります。ここに変更したドキュメントを保存します。

```csharp
// ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ステップ2: 新しいドキュメントを作成する

図形を挿入して修正する新しい Word 文書を作成しましょう。

```csharp
Document doc = new Document();
```

## ステップ3: インライン図形の挿入

まず、変更履歴を残さずにドキュメントにインライン図形を挿入します。インライン図形とは、テキストに合わせて配置する図形です。

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## ステップ4: 変更履歴の追跡を開始する

ドキュメントの変更を追跡するには、リビジョン追跡を有効にする必要があります。これは、図形に加えられた変更を識別するために不可欠です。

```csharp
doc.StartTrackRevisions("John Doe");
```

## ステップ5: 修正を加えた別の図形を挿入する

リビジョン管理が有効になったので、別の図形を挿入してみましょう。今度は、すべての変更が追跡されます。

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## ステップ6: 図形の取得と変更

ドキュメント内のすべての図形を取得し、必要に応じて修正することができます。ここでは、図形を取得し、最初の図形を削除します。

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## ステップ7: ドキュメントを保存する

変更を加えたら、ドキュメントを保存する必要があります。これにより、すべての修正内容が保存されます。

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## ステップ8: 図形移動の修正の処理

図形が移動すると、Aspose.Words はそれをリビジョンとして記録します。つまり、図形のインスタンスが 2 つ存在することになります。1 つは元の場所、もう 1 つは新しい場所にあります。

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## 結論

これで完了です！Aspose.Words for .NET を使用して、Word 文書内の図形の修正を処理する方法を習得できました。ドキュメントテンプレートの管理、レポートの自動化、あるいは単に変更履歴を管理するなど、これらのスキルは非常に役立ちます。このステップバイステップガイドに従うことで、基本を習得するだけでなく、より高度なドキュメント処理テクニックについても理解を深めることができます。

## よくある質問

### Aspose.Words for .NET とは何ですか?
Aspose.Words for .NET は、開発者が C# を使用してプログラム的に Word 文書を作成、変更、変換できるようにする強力なライブラリです。

### Word 文書内の他の要素に加えられた変更を追跡できますか?
はい、Aspose.Words for .NET は、テキスト、表など、さまざまな要素に対する変更の追跡をサポートしています。

### Aspose.Words for .NET の無料試用版を入手するにはどうすればいいですか?
Aspose.Words for .NETの無料トライアルを入手できます [ここ](https://releases。aspose.com/).

### プログラムで修正を承認または拒否することは可能ですか?
はい、Aspose.Words for .NET には、プログラムによって変更を承認または拒否するメソッドが用意されています。

### Aspose.Words for .NET を C# 以外の他の .NET 言語で使用できますか?
もちろんです! Aspose.Words for .NET は、VB.NET や F# を含むあらゆる .NET 言語で使用できます。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}