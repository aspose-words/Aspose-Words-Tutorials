---
title: Word 文書にブックマークされたテキストを追加する
linktitle: Word 文書にブックマークされたテキストを追加する
second_title: Aspose.Words ドキュメント処理 API
description: このステップバイステップ ガイドでは、Aspose.Words for .NET を使用して Word 文書にブックマークされたテキストを追加する方法を学習します。開発者に最適です。
weight: 10
url: /ja/net/programming-with-bookmarks/append-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 文書にブックマークされたテキストを追加する

## 導入

こんにちは! Word 文書のブックマークされたセクションからテキストを追加しようとして、難しいと感じたことはありませんか? 大丈夫です! このチュートリアルでは、Aspose.Words for .NET を使用してそのプロセスを順を追って説明します。 簡単な手順に分解して、簡単に理解できるようにします。 早速、ブックマークされたテキストをプロのように追加してみましょう!

## 前提条件

始める前に、必要なものがすべて揃っていることを確認しましょう。

-  Aspose.Words for .NET: インストールされていることを確認してください。インストールされていない場合は、[ここからダウンロード](https://releases.aspose.com/words/net/).
- 開発環境: Visual Studio などの任意の .NET 開発環境。
- C# の基礎知識: 基本的な C# プログラミングの概念を理解しておくと役立ちます。
- ブックマーク付きの Word 文書: テキストを追加するために使用するブックマークが設定された Word 文書。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートしましょう。これにより、必要なツールがすべて手元に揃います。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

例を詳細な手順に分解してみましょう。

## ステップ1: ドキュメントを読み込み、変数を初期化する

さて、まずは Word 文書を読み込んで、必要な変数を初期化しましょう。

```csharp
//ソースドキュメントと宛先ドキュメントを読み込みます。
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

//ドキュメントインポーターを初期化します。
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

//ソース ドキュメント内のブックマークを見つけます。
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## ステップ2: 開始段落と終了段落を特定する

次に、ブックマークの開始と終了の段落を見つけます。この境界内でテキストを処理する必要があるため、これは非常に重要です。

```csharp
//これはブックマークの始まりを含む段落です。
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

//これはブックマークの終わりを含む段落です。
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## ステップ3: 段落の親を検証する

開始段落と終了段落の親が同じであることを確認する必要があります。これは、物事をわかりやすくするための単純なシナリオです。

```csharp
//かなり単純なシナリオに限定します。
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## ステップ4: 停止するノードを特定する

次に、テキストのコピーを停止するノードを決定する必要があります。これは、終了段落の直後のノードになります。

```csharp
//開始段落から終了段落まで（終了段落も含む）すべての段落をコピーしたいのですが、
//したがって、停止するノードは最後の段落の 1 つ後になります。
Node endNode = endPara.NextSibling;
```

## ステップ5: ブックマークしたテキストを宛先ドキュメントに追加する

最後に、開始段落から終了段落の後のノードまでのノードをループし、それらを宛先ドキュメントに追加します。

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    //これは現在のノードのコピーを作成し、それをコンテキストにインポート（有効にする）します。
    //インポートとは、スタイルとリスト識別子を正しく調整することを意味します。
    Node newNode = importer.ImportNode(curNode, true);

    //インポートしたノードを宛先ドキュメントに追加します。
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

//追加したテキストを含む宛先ドキュメントを保存します。
dstDoc.Save("appended_document.docx");
```

## 結論

これで完了です。Aspose.Words for .NET を使用して、Word 文書内のブックマークされたセクションからテキストを正常に追加できました。この強力なツールにより、文書の操作が簡単になり、さらにもう 1 つの秘策が身につきました。コーディングを楽しんでください。

## よくある質問

### 複数のブックマークからテキストを一度に追加できますか?
はい、ブックマークごとにこのプロセスを繰り返し、それに応じてテキストを追加できます。

### 開始段落と終了段落の親が異なる場合はどうなりますか?
現在の例では、同じ親を持つことを前提としています。親が異なる場合は、より複雑な処理が必要です。

### 追加されたテキストの元の書式を維持できますか?
絶対に！`ImportFormatMode.KeepSourceFormatting`元の書式が保持されます。

### 宛先ドキュメント内の特定の位置にテキストを追加することは可能ですか?
はい、宛先ドキュメント内の目的のノードに移動することで、任意の位置にテキストを追加できます。

### ブックマークのテキストを新しいセクションに追加する必要がある場合はどうすればよいですか?
宛先ドキュメントに新しいセクションを作成し、そこにテキストを追加できます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
