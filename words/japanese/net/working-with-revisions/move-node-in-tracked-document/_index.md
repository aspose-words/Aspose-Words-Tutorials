---
"description": "Aspose.Words for .NET を使用して、追跡されたWord文書内のノードを移動する方法を、詳細なステップバイステップガイドで学習します。開発者に最適です。"
"linktitle": "追跡ドキュメント内のノードを移動"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "追跡ドキュメント内のノードを移動"
"url": "/ja/net/working-with-revisions/move-node-in-tracked-document/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 追跡ドキュメント内のノードを移動

## 導入

Aspose.Words を愛用する皆様、こんにちは！Word 文書内のノードを移動しながら変更履歴を追跡する必要があった経験があるなら、まさにうってつけの場所です。本日は、Aspose.Words for .NET を使ってこれを実現する方法を詳しく解説します。手順をステップバイステップで学ぶだけでなく、スムーズかつ効率的に文書を操作するためのヒントやコツもご紹介します。

## 前提条件

コードに取り掛かる前に、必要なものがすべて揃っていることを確認しましょう。

- Aspose.Words for .NET: ダウンロード [ここ](https://releases。aspose.com/words/net/).
- .NET 環境: 互換性のある .NET 開発環境が設定されていることを確認します。
- C# の基本知識: このチュートリアルでは、C# の基本を理解していることを前提としています。

すべてできましたか？素晴らしい！インポートする必要がある名前空間に進みましょう。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートする必要があります。これらは、Aspose.Words の操作とドキュメントノードの処理に不可欠です。

```csharp
using Aspose.Words;
using System;
```

では、プロセスを分かりやすいステップに分解してみましょう。各ステップを詳しく説明するので、各段階で何が起こっているのかをしっかりと理解できます。

## ステップ1: ドキュメントを初期化する

まず、新しいドキュメントを初期化し、 `DocumentBuilder` いくつかの段落を追加します。

```csharp
// ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// いくつかの段落を追加する
builder.Writeln("Paragraph 1");
builder.Writeln("Paragraph 2");
builder.Writeln("Paragraph 3");
builder.Writeln("Paragraph 4");
builder.Writeln("Paragraph 5");
builder.Writeln("Paragraph 6");

// 最初の段落数を確認する
Body body = doc.FirstSection.Body;
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## ステップ2: 変更履歴の追跡を開始する

次に、リビジョンの追跡を開始する必要があります。これは、ドキュメントに加えられた変更を確認できるため、非常に重要です。

```csharp
// リビジョンの追跡を開始する
doc.StartTrackRevisions("Author", new DateTime(2020, 12, 23, 14, 0, 0));
```

## ステップ3: ノードを移動する

さて、いよいよタスクの核心部分、つまりノードをある場所から別の場所へ移動します。3番目の段落を最初の段落の前に移動します。

```csharp
// 移動するノードとその終了範囲を定義する
Node node = body.Paragraphs[3];
Node endNode = body.Paragraphs[5].NextSibling;
Node referenceNode = body.Paragraphs[0];

// 定義された範囲内でノードを移動する
while (node != endNode)
{
    Node nextNode = node.NextSibling;
    body.InsertBefore(node, referenceNode);
    node = nextNode;
}
```

## ステップ4: 変更履歴の追跡を停止する

ノードを移動したら、リビジョンの追跡を停止する必要があります。

```csharp
// リビジョンの追跡を停止する
doc.StopTrackRevisions();
```

## ステップ5: ドキュメントを保存する

最後に、変更したドキュメントを指定されたディレクトリに保存します。

```csharp
// 変更したドキュメントを保存する
doc.Save(dataDir + "WorkingWithRevisions.MoveNodeInTrackedDocument.docx");

// 最終段落数を出力する
Console.WriteLine("Paragraph count: {0}", body.Paragraphs.Count);
```

## 結論

これで完了です！Aspose.Words for .NET を使って、追跡対象ドキュメント内のノードを移動できました。この強力なライブラリを使えば、Word ドキュメントをプログラムで簡単に操作できます。作成、編集、変更の追跡など、どんな作業でも Aspose.Words がサポートします。ぜひお試しください。コーディングを楽しんでください！

## よくある質問

### Aspose.Words for .NET とは何ですか?

Aspose.Words for .NET は、Word 文書をプログラムで操作するためのクラスライブラリです。開発者は、.NET アプリケーション内で Word 文書を作成、編集、変換、印刷できます。

### Aspose.Words を使用して Word 文書の変更履歴を追跡するにはどうすればよいですか?

改訂履歴を追跡するには、 `StartTrackRevisions` 方法 `Document` オブジェクト。これにより、ドキュメントに加えられた変更がすべて表示され、リビジョンの追跡が可能になります。

### Aspose.Words で複数のノードを移動できますか?

はい、複数のノードを反復処理して次のようなメソッドを使用することで移動できます。 `InsertBefまたはe` or `InsertAfter` 希望の場所に配置します。

### Aspose.Words でリビジョンの追跡を停止するにはどうすればよいですか?

使用 `StopTrackRevisions` 方法 `Document` リビジョンの追跡を停止するにはオブジェクトを使用します。

### Aspose.Words for .NET に関する詳細なドキュメントはどこで入手できますか?

詳細なドキュメントは以下をご覧ください [ここ](https://reference。aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}