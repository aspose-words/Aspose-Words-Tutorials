---
"description": "Aspose.Words for .NET を使って、Word 文書を別の Word 文書にシームレスに挿入する方法を、詳細なステップバイステップガイドで学習できます。ドキュメント処理の効率化を目指す開発者に最適です。"
"linktitle": "置換時にドキュメントを挿入"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "置換時にドキュメントを挿入"
"url": "/ja/net/clone-and-combine-documents/insert-document-at-replace/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 置換時にドキュメントを挿入

## 導入

ドキュメントマエストロの皆さん、こんにちは！Word文書を別のWord文書にシームレスに挿入する方法を模索しながら、コードにどっぷりと浸かった経験はありませんか？ご安心ください。今日は、そんな作業を簡単にするAspose.Words for .NETの世界をご紹介します。この強力なライブラリを使って、検索と置換操作中に特定の位置にドキュメントを挿入する方法を、ステップバイステップで詳しく解説します。Aspose.Wordsの達人になる準備はできましたか？さあ、始めましょう！

## 前提条件

コードに進む前に、準備しておく必要のあるものがいくつかあります。

- Visual Studio: お使いのマシンにVisual Studioがインストールされていることを確認してください。まだインストールされていない場合は、こちらからダウンロードできます。 [ここ](https://visualstudio。microsoft.com/).
- Aspose.Words for .NET: Aspose.Wordsライブラリが必要です。 [Aspose ウェブサイト](https://releases。aspose.com/words/net/).
- C# の基本知識: C# と .NET の基本的な理解があれば、このチュートリアルを理解するのに役立ちます。

さて、準備が整ったので、実際にコードに取り組んでみましょう。

## 名前空間のインポート

まず最初に、Aspose.Words を使用するために必要な名前空間をインポートする必要があります。これは、プロジェクトを開始する前に必要なツールをすべて揃えるようなものです。C# ファイルの先頭に以下の using ディレクティブを追加してください。

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

前提条件が整ったので、プロセスを簡単なステップに分解してみましょう。それぞれのステップは重要であり、目標達成に近づくためのものです。

## ステップ1: ドキュメントディレクトリの設定

まず、ドキュメントを保存するディレクトリを指定する必要があります。これは、大きなパフォーマンスの前に舞台を設定するようなものです。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する `"YOUR DOCUMENT DIRECTORY"` ディレクトリへのパスを入力します。ドキュメントはここに保存されます。

## ステップ2: メインドキュメントを読み込む

次に、別のドキュメントを挿入するメインドキュメントを読み込みます。これは、すべてのアクションが発生するメインステージと考えてください。

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

このコードは、指定されたディレクトリからメイン ドキュメントを読み込みます。

## ステップ3: 検索と置換のオプションを設定する

ドキュメントを挿入したい場所を特定するには、検索と置換機能を使います。これは、地図を使って新しい追加項目の正確な場所を探すようなものです。

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

ここでは、方向を後向きに設定し、次に定義するカスタム コールバック ハンドラーを指定しています。

## ステップ4: 置換操作を実行する

ここで、メイン ドキュメントに特定のプレースホルダー テキストを検索して何も置き換えないように指示し、カスタム コールバックを使用して別のドキュメントを挿入します。

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

このコードは検索と置換の操作を実行し、更新されたドキュメントを保存します。

## ステップ5: カスタム置換コールバックハンドラーを作成する

魔法が起こるのは、カスタムコールバックハンドラです。このハンドラは、検索と置換操作中にドキュメントの挿入がどのように実行されるかを定義します。

```csharp
private class InsertDocumentAtReplaceHandler : IReplacingCallback
{
    ReplaceAction IReplacingCallback.Replacing(ReplacingArgs args)
    {
        Document subDoc = new Document(dataDir + "Document insertion 2.docx");

        // 一致するテキストを含む段落の後にドキュメントを挿入します。
        Paragraph para = (Paragraph)args.MatchNode.ParentNode;
        InsertDocument(para, subDoc);

        // 一致するテキストを含む段落を削除します。
        para.Remove();
        return ReplaceAction.Skip;
    }
}
```

ここでは、挿入するドキュメントを読み込み、挿入を実行するためのヘルパー メソッドを呼び出します。

## ステップ6: ドキュメント挿入メソッドを定義する

パズルの最後のピースは、指定された場所にドキュメントを実際に挿入するメソッドです。

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    // 挿入先が段落か表かを確認します
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;

        // ソースドキュメントからノードをインポートするためのNodeImporterを作成する
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        // ソースドキュメントのセクション内のすべてのブロックレベルノードをループします
        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        {
            foreach (Node srcNode in srcSection.Body)
            {
                // セクションの最後の空の段落をスキップする
                if (srcNode.NodeType == NodeType.Paragraph)
                {
                    Paragraph para = (Paragraph)srcNode;
                    if (para.IsEndOfSection && !para.HasChildNodes)
                        continue;
                }

                // ノードをインポートして宛先に挿入する
                Node newNode = importer.ImportNode(srcNode, true);
                destinationParent.InsertAfter(newNode, insertionDestination);
                insertionDestination = newNode;
            }
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}

```

このメソッドは、挿入するドキュメントからノードをインポートし、メイン ドキュメント内の適切な場所に配置します。

## 結論

これで完了です！Aspose.Words for .NET を使用してドキュメントを別のドキュメントに挿入するための包括的なガイドです。これらの手順に従うことで、ドキュメントの組み立てと操作タスクを簡単に自動化できます。ドキュメント管理システムを構築する場合でも、ドキュメント処理ワークフローを効率化する必要がある場合でも、Aspose.Words は頼りになる相棒です。

## よくある質問

### Aspose.Words for .NET とは何ですか?
Aspose.Words for .NET は、Word 文書をプログラムで操作するための強力なライブラリです。Word 文書を簡単に作成、変更、変換、処理できます。

### 一度に複数のドキュメントを挿入できますか?
はい、ドキュメントのコレクションを反復処理して複数の挿入を処理するようにコールバック ハンドラーを変更できます。

### 無料トライアルはありますか？
もちろんです！無料トライアルはこちらからダウンロードできます。 [ここ](https://releases。aspose.com/).

### Aspose.Words のサポートを受けるにはどうすればよいですか?
サポートを受けるには、 [Aspose.Words フォーラム](https://forum。aspose.com/c/words/8).

### 挿入したドキュメントの書式を維持できますか?
はい、 `NodeImporter` クラスを使用すると、あるドキュメントから別のドキュメントにノードをインポートするときに書式設定をどのように処理するかを指定できます。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}