---
title: 置換時にドキュメントを挿入
linktitle: 置換時にドキュメントを挿入
second_title: Aspose.Words ドキュメント処理 API
description: 詳細なステップバイステップ ガイドを使用して、Aspose.Words for .NET を使用して 1 つの Word 文書を別の Word 文書にシームレスに挿入する方法を学びます。ドキュメント処理を効率化したい開発者に最適です。
weight: 10
url: /ja/net/clone-and-combine-documents/insert-document-at-replace/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 置換時にドキュメントを挿入

## 導入

ドキュメント マエストロの皆さん、こんにちは。Word ドキュメントを別のドキュメントにシームレスに挿入する方法を模索しながら、コードにどっぷりつかってしまったことはありませんか? 心配はいりません。今日は、その作業を簡単にするために Aspose.Words for .NET の世界に飛び込みます。この強力なライブラリを使用して、検索と置換操作中に特定のポイントにドキュメントを挿入する方法について、詳細なステップ バイ ステップ ガイドで説明します。Aspose.Words の達人になる準備はできましたか? さあ、始めましょう!

## 前提条件

コードに進む前に、準備しておくべきことがいくつかあります。

-  Visual Studio: お使いのマシンにVisual Studioがインストールされていることを確認してください。まだインストールされていない場合は、こちらからダウンロードできます。[ここ](https://visualstudio.microsoft.com/).
-  Aspose.Words for .NET: Aspose.Wordsライブラリが必要です。[Aspose ウェブサイト](https://releases.aspose.com/words/net/).
- C# の基本知識: C# と .NET の基本的な理解があれば、このチュートリアルを理解するのに役立ちます。

さて、準備が整ったので、実際にコードに取り組んでみましょう。

## 名前空間のインポート

まず最初に、Aspose.Words を操作するために必要な名前空間をインポートする必要があります。これは、プロジェクトを開始する前にすべてのツールを集めるようなものです。C# ファイルの先頭に次の using ディレクティブを追加します。

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

前提条件が整ったので、プロセスを細かいステップに分解してみましょう。各ステップは重要であり、目標に近づくのに役立ちます。

## ステップ1: ドキュメントディレクトリの設定

まず、ドキュメントが保存されているディレクトリを指定する必要があります。これは、大きなパフォーマンスの前にステージを設定するようなものです。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する`"YOUR DOCUMENT DIRECTORY"`ディレクトリへのパスを入力します。ここにドキュメントが保存されます。

## ステップ2: メインドキュメントを読み込む

次に、別のドキュメントを挿入するメイン ドキュメントを読み込みます。これは、すべてのアクションが発生するメイン ステージと考えてください。

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

このコードは、指定されたディレクトリからメイン ドキュメントを読み込みます。

## ステップ3: 検索と置換のオプションを設定する

ドキュメントを挿入する特定の場所を見つけるには、検索と置換機能を使用します。これは、地図を使用して新しい追加項目の正確な場所を見つけるのに似ています。

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

カスタム コールバック ハンドラーは、魔法が起こる場所です。このハンドラーは、検索と置換の操作中にドキュメントの挿入がどのように実行されるかを定義します。

```csharp
private class InsertDocumentAtReplaceHandler : IReplacingCallback
{
    ReplaceAction IReplacingCallback.Replacing(ReplacingArgs args)
    {
        Document subDoc = new Document(dataDir + "Document insertion 2.docx");

        //一致するテキストを含む段落の後にドキュメントを挿入します。
        Paragraph para = (Paragraph)args.MatchNode.ParentNode;
        InsertDocument(para, subDoc);

        //一致するテキストを含む段落を削除します。
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
    //挿入先が段落か表か確認する
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;

        //ソースドキュメントからノードをインポートするためのNodeImporterを作成する
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        //ソースドキュメントのセクション内のすべてのブロックレベルノードをループします。
        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        {
            foreach (Node srcNode in srcSection.Body)
            {
                //セクションの最後の空の段落をスキップする
                if (srcNode.NodeType == NodeType.Paragraph)
                {
                    Paragraph para = (Paragraph)srcNode;
                    if (para.IsEndOfSection && !para.HasChildNodes)
                        continue;
                }

                //ノードをインポートして宛先に挿入する
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

これで完了です。Aspose.Words for .NET を使用して 1 つのドキュメントを別のドキュメントに挿入するための包括的なガイドです。これらの手順に従うことで、ドキュメントのアセンブリと操作のタスクを簡単に自動化できます。ドキュメント管理システムを構築する場合でも、ドキュメント処理ワークフローを合理化する必要がある場合でも、Aspose.Words は信頼できる相棒です。

## よくある質問

### Aspose.Words for .NET とは何ですか?
Aspose.Words for .NET は、Word 文書をプログラムで操作するための強力なライブラリです。Word 文書を簡単に作成、変更、変換、処理できます。

### 一度に複数のドキュメントを挿入できますか?
はい、ドキュメントのコレクションを反復処理することで、複数の挿入を処理するようにコールバック ハンドラーを変更できます。

### 無料トライアルはありますか？
もちろんです！無料トライアルはこちらからダウンロードできます[ここ](https://releases.aspose.com/).

### Aspose.Words のサポートを受けるにはどうすればよいですか?
サポートを受けるには、[Aspose.Words フォーラム](https://forum.aspose.com/c/words/8).

### 挿入したドキュメントの書式を維持できますか?
はい、`NodeImporter`クラスを使用すると、あるドキュメントから別のドキュメントにノードをインポートするときに書式設定をどのように処理するかを指定できます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
