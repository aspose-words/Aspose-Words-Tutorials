---
title: 追加 削除 コメント 返信
linktitle: 追加 削除 コメント 返信
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word 文書にコメントの返信を追加および削除する方法を学びます。このステップ バイ ステップ ガイドを使用して、文書の共同作業を強化します。
weight: 10
url: /ja/net/working-with-comments/add-remove-comment-reply/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 追加 削除 コメント 返信

## 導入

Word 文書でコメントとその返信を操作すると、文書のレビュー プロセスが大幅に強化されます。Aspose.Words for .NET を使用すると、これらのタスクを自動化して、ワークフローをより効率的かつ合理化できます。このチュートリアルでは、コメントの返信の追加と削除について説明し、この機能を習得するためのステップ バイ ステップ ガイドを提供します。

## 前提条件

コードに進む前に、次のものを用意してください。

-  Aspose.Words for .NET: ダウンロードしてインストールしてください。[ここ](https://releases.aspose.com/words/net/).
- 開発環境: Visual Studio または .NET をサポートするその他の IDE。
- C# の基礎知識: C# プログラミングに精通していることが必須です。

## 名前空間のインポート

まず、C# プロジェクトに必要な名前空間をインポートします。

```csharp
using System;
using Aspose.Words;
```

## ステップ1: Word文書を読み込む

まず、管理するコメントが含まれている Word 文書を読み込む必要があります。この例では、ディレクトリに「Comments.docx」という名前の文書があると想定しています。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Comments.docx");
```

## ステップ2: 最初のコメントにアクセスする

次に、ドキュメント内の最初のコメントにアクセスします。このコメントが返信の追加と削除の対象になります。

```csharp
Comment comment = (Comment)doc.GetChild(NodeType.Comment, 0, true);
```

## ステップ3: 既存の返信を削除する

コメントにすでに返信がある場合は、その返信を削除することもできます。コメントの最初の返信を削除する方法は次のとおりです。

```csharp
comment.RemoveReply(comment.Replies[0]);
```

## ステップ4: 新しい返信を追加する

それでは、コメントに新しい返信を追加してみましょう。投稿者の名前、イニシャル、返信の日時、返信テキストを指定できます。

```csharp
comment.AddReply("John Doe", "JD", new DateTime(2017, 9, 25, 12, 15, 0), "New reply");
```

## ステップ5: 更新したドキュメントを保存する

最後に、変更したドキュメントをディレクトリに保存します。

```csharp
doc.Save(dataDir + "WorkingWithComments.AddRemoveCommentReply.docx");
```

## 結論

Word ドキュメントのコメント返信をプログラムで管理すると、特に広範なレビューを扱う場合に、多くの時間と労力を節約できます。Aspose.Words for .NET を使用すると、このプロセスが簡単かつ効率的になります。このガイドで説明されている手順に従うことで、コメント返信を簡単に追加および削除でき、ドキュメントの共同作業エクスペリエンスが向上します。

## よくある質問

### 1 つのコメントに複数の返信を追加するにはどうすればよいですか?

 1つのコメントに複数の返信を追加するには、`AddReply`同じコメント オブジェクトに対してメソッドを複数回実行します。

### 各返信の作成者の詳細をカスタマイズできますか?

はい、返信の投稿者名、イニシャル、日時を、`AddReply`方法。

### コメントからすべての返信を一度に削除することは可能ですか?

すべての返信を削除するには、`Replies`コメントを収集し、それぞれを個別に削除します。

### ドキュメントの特定のセクションのコメントにアクセスできますか?

はい、ドキュメントのセクション間を移動し、各セクション内のコメントにアクセスするには、`GetChild`方法。

### Aspose.Words for .NET は他のコメント関連の機能もサポートしていますか?

はい、Aspose.Words for .NET は、新しいコメントの追加、コメント プロパティの設定など、さまざまなコメント関連機能に対する広範なサポートを提供します。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
