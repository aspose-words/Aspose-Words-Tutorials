---
title: Word 文書の行のブックマークを解読する
linktitle: Word 文書の行のブックマークを解読する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用すると、Word 文書内の絡まった行ブックマークを簡単に解くことができます。このガイドでは、よりクリーンで安全なブックマーク管理のプロセスを順を追って説明します。
weight: 10
url: /ja/net/programming-with-bookmarks/untangle-row-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 文書の行のブックマークを解読する

## 導入

Word 文書内の行をブックマークで削除すると、隣接する行のブックマークが台無しになってしまうという状況に遭遇したことはありませんか? これは、特に複雑な表を扱う場合には、非常にイライラさせられるものです。ありがたいことに、Aspose.Words for .NET は、行のブックマークを解くという強力なソリューションを提供します。 

このガイドでは、Aspose.Words for .NET を使用して Word 文書内の行ブックマークを整理するプロセスについて説明します。コードをわかりやすい手順に分解し、各関数の目的を説明します。これにより、面倒なブックマークの問題に自信を持って対処できるようになります。

## 前提条件

始める前に、いくつか必要なものがあります:

1.  Aspose.Words for .NET: この商用ライブラリは、Word文書をプログラムで操作するための機能を提供します。2. 無料試用版は以下からダウンロードできます。[ダウンロードリンク](https://releases.aspose.com/words/net/)またはライセンスを購入する[買う](https://purchase.aspose.com/buy).
3. C# 開発環境: Visual Studio またはその他の C# IDE は完全に動作します。
4. 行ブックマーク付きの Word 文書: デモンストレーションのために、「Table column bookmarks.docx」というサンプル文書を使用します。

## 名前空間のインポート

最初のステップでは、必要な名前空間を C# プロジェクトにインポートします。これらの名前空間は、Aspose.Words for .NET から使用するクラスと機能へのアクセスを提供します。

```csharp
using Aspose.Words;
using System;
```

## ステップ1: Word文書を読み込む

まず、絡み合った行のブックマークを含むWord文書を読み込みます。`Document`クラスは Aspose.Words でドキュメント操作を処理します。ドキュメントを読み込む方法は次のとおりです。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; //ドキュメントの場所に置き換えます
Document doc = new Document(dataDir + "Table column bookmarks.docx");
```

交換を忘れないでください`"YOUR DOCUMENT DIRECTORY"`「Table column bookmarks.docx」ファイルへの実際のパスを入力します。

## ステップ2: 行のブックマークを解く

ここで魔法が起こるのです！`Untangle`関数は行のブックマークを解く処理を行います。その機能を詳しく見てみましょう。

```csharp
private void Untangle(Document doc)
{
   foreach (Bookmark bookmark in doc.Range.Bookmarks)
   {
	   //ブックマークとブックマーク終了の両方の親行を取得します
	   Row row1 = (Row)bookmark.BookmarkStart.GetAncestor(typeof(Row));
	   Row row2 = (Row)bookmark.BookmarkEnd.GetAncestor(typeof(Row));

	   //行が有効で隣接しているかどうかを確認する
	   if (row1 != null && row2 != null && row1.NextSibling == row2)
		   //ブックマークの終了を最上行の最後のセルの最後の段落に移動する
		   row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd);
   }
}
```

コードが何をするのかを段階的に説明します。

ドキュメント内のすべてのブックマークを反復処理するには、`foreach`ループ。
各ブックマークについて、ブックマークの開始行（`bookmark.BookmarkStart`) とブックマークの終了 (`bookmark.BookmarkEnd` ）を使用して`GetAncestor`方法。
次に、両方の行が見つかるかどうかを確認します（`row1 != null`そして`row2 != null`) であり、隣接する行である場合 (`row1.NextSibling == row2`)。これにより、隣接する行にまたがるブックマークのみが変更されます。
条件が満たされた場合、ブックマーク終了ノードを最上行の最後のセルの最後の段落の末尾に移動します（`row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd)`) 効果的にそれらを解きほぐします。

## ステップ3: ブックマークで行を削除する

ブックマークが解かれたので、ブックマーク名を使って安全に行を削除できます。`DeleteRowByBookmark`関数はこのタスクを処理します:

```csharp
private void DeleteRowByBookmark(Document doc, string bookmarkName)
{
   Bookmark bookmark = doc.Range.Bookmarks[bookmarkName];

   Row row = (Row)bookmark?.BookmarkStart.GetAncestor(typeof(Row));
   row?.Remove();
}
```

この機能の詳細は次のとおりです。

ブックマーク名（`bookmarkName`) を入力します。
対応するブックマークオブジェクトを取得するには、`doc.Range.Bookmarks[bookmarkName]`.
次にブックマーク開始の親行を取得します。`GetAncestor` （`Untangle`関数）。
最後に、ブックマークと行が存在するかどうかを確認します（`bookmark != null`そして

## ステップ4: もつれが解けたことを確認する

一方、`Untangle`関数は他のブックマークの安全性を確保する必要があるため、常に検証することをお勧めします。 解凍プロセスによって誤って別のブックマークの末尾が削除されていないかどうかを確認する方法は次のとおりです。

```csharp
if (doc.Range.Bookmarks["ROW1"].BookmarkEnd == null)
   throw new Exception("Wrong, the end of the bookmark was deleted.");
```

このコード スニペットは、「ROW2」ブックマークの行を削除した後、「ROW1」という名前のブックマークの末尾がまだ存在するかどうかを確認します。null の場合、例外がスローされ、アンタングル プロセスに問題があることが示されます。 

## ステップ5: ドキュメントを保存する

最後に、ブックマークを解いて行を削除した後、`Save`方法：

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

これにより、もつれが解かれたブックマークと削除された行を含むドキュメントが、新しいファイル名「WorkingWithBookmarks.UntangleRowBookmarks.docx」で保存されます。 

## 結論

これらの手順に従い、`Untangle`関数を使用すると、Aspose.Words for .NETを使用してWord文書内の行のブックマークを効果的に整理できます。これにより、ブックマークで行を削除しても、隣接する行の他のブックマークに予期しない影響が生じないことが保証されます。プレースホルダーを次のように置き換えることを忘れないでください。`"YOUR DOCUMENT DIRECTORY"`実際のパスとファイル名を入力します。

## よくある質問

### Aspose.Words for .NET は無料ですか?

 Aspose.Words for .NETは商用ライブラリで、無料トライアルもご利用いただけます。こちらからダウンロードできます。[ダウンロードリンク](https://releases.aspose.com/words/net/).

### Word で行のブックマークを手動で解除できますか?

技術的には可能ですが、Word でブックマークを手動で解除するのは面倒で、エラーが発生しやすくなります。Aspose.Words for .NET はこのプロセスを自動化し、時間と労力を節約します。

### もし、`Untangle` function encounters an error?

コードには、アンタングル処理によって誤って別のブックマークの末尾が削除された場合に例外をスローする例外ハンドラーが含まれています。このエラー処理は、特定のニーズに合わせてカスタマイズできます。

### このコードを使用して、隣接していない行にまたがるブックマークを解くことはできますか?

現在、コードは隣接する行にまたがるブックマークを解くことに重点を置いています。隣接しない行を処理するようにコードを変更するには、それらのシナリオを識別して処理するための追加のロジックが必要になります。

### このアプローチの使用には何か制限がありますか?

このアプローチでは、ブックマークが表のセル内で適切に定義されていることを前提としています。ブックマークがセルの外側または予期しない場所に配置されている場合、解除プロセスが意図したとおりに機能しない可能性があります。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
