---
"description": "Aspose.Words for .NET を使えば、ブックマークされたテキストを Word 文書間で簡単にコピーできます。このステップバイステップガイドでその方法を学びましょう。"
"linktitle": "Word文書内のブックマークされたテキストをコピーする"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "Word文書内のブックマークされたテキストをコピーする"
"url": "/ja/net/programming-with-bookmarks/copy-bookmarked-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word文書内のブックマークされたテキストをコピーする

## 導入

あるWord文書から別のWord文書に特定のセクションをコピーしたいと思ったことはありませんか？そんな時、ぜひご活用ください！このチュートリアルでは、Aspose.Words for .NETを使って、ブックマークされたテキストをあるWord文書から別のWord文書にコピーする方法を詳しく説明します。動的なレポートを作成する場合でも、ドキュメント生成を自動化する場合でも、このガイドがプロセスを簡素化します。

## 前提条件

始める前に、次のものを用意しておいてください。

- Aspose.Words for .NET ライブラリ: ダウンロードはこちらから [ここ](https://releases。aspose.com/words/net/).
- 開発環境: Visual Studio またはその他の .NET 開発環境。
- C# の基礎知識: C# プログラミングと .NET フレームワークに精通していること。

## 名前空間のインポート

まず、プロジェクトに必要な名前空間がインポートされていることを確認します。

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## ステップ1: ソースドキュメントを読み込む

まず最初に、コピーしたいブックマークされたテキストを含むソース ドキュメントを読み込む必要があります。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

ここ、 `dataDir` ドキュメントディレクトリへのパスであり、 `Bookmarks.docx` ソースドキュメントです。

## ステップ2: ブックマークを特定する

次に、ソース ドキュメントからコピーするブックマークを特定します。

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

交換する `"MyBookmark1"` ブックマークの実際の名前を入力します。

## ステップ3: 宛先ドキュメントを作成する

次に、ブックマークしたテキストをコピーする新しいドキュメントを作成します。

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## ステップ4: ブックマークしたコンテンツをインポートする

スタイルと書式設定が保持されるようにするには、 `NodeImporter` ブックマークされたコンテンツをソース ドキュメントから宛先ドキュメントにインポートします。

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## ステップ5: AppendBookmarkedTextメソッドを定義する

ここで魔法が起こります。ブックマークされたテキストのコピーを処理するメソッドを定義します。

```csharp
private void AppendBookmarkedText(NodeImporter importer, Bookmark srcBookmark, CompositeNode dstNode)
{
    Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
    Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

    if (startPara == null || endPara == null)
        throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");

    if (startPara.ParentNode != endPara.ParentNode)
        throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");

    Node endNode = endPara.NextSibling;

    for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
    {
        Node newNode = importer.ImportNode(curNode, true);
        dstNode.AppendChild(newNode);
    }
}
```

## ステップ6: 宛先ドキュメントを保存する

最後に、コピー先のドキュメントを保存して、コピーした内容を確認します。

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## 結論

これで完了です！Aspose.Words for .NET を使って、ブックマークされたテキストをある Word 文書から別の Word 文書にコピーできました。この方法は、文書操作タスクを自動化するのに非常に効果的で、ワークフローをより効率的かつ合理化します。

## よくある質問

### 複数のブックマークを一度にコピーできますか?
はい、複数のブックマークを反復処理し、同じ方法を使用してそれぞれをコピーできます。

### ブックマークが見つからない場合はどうなりますか?
その `Range.Bookmarks` 財産は返還される `null`したがって、例外を回避するためにこのケースを処理するようにしてください。

### 元のブックマークの書式を保持できますか?
絶対に！ `ImportFormatMode.KeepSourceFormatting` 元の書式が保持されます。

### ブックマークしたテキストのサイズに制限はありますか?
特定の制限はありませんが、ドキュメントが非常に大きい場合はパフォーマンスが異なる場合があります。

### 異なる Word 文書形式間でテキストをコピーできますか?
はい、Aspose.Words はさまざまな Word 形式をサポートしており、このメソッドはこれらの形式で機能します。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}