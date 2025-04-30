---
"description": "この包括的なステップバイステップのチュートリアルでは、Aspose.Words for .NET を使用して差し込み印刷フィールドにドキュメントを挿入する方法を学習します。"
"linktitle": "差し込み印刷で文書を挿入"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "差し込み印刷で文書を挿入"
"url": "/ja/net/clone-and-combine-documents/insert-document-at-mail-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 差し込み印刷で文書を挿入

## 導入

Aspose.Words for .NET によるドキュメント自動化の世界へようこそ！差し込み印刷処理中に、メイン文書内の特定のフィールドにドキュメントを動的に挿入したいと思ったことはありませんか？まさにその通りです。このチュートリアルでは、Aspose.Words for .NET を使用して差し込み印刷フィールドにドキュメントを挿入するプロセスをステップバイステップで解説します。まるでパズルを組み立て、ピースが一つ一つぴったりと収まるように。さあ、早速始めましょう！

## 前提条件

始める前に、次のものを用意してください。

1. Aspose.Words for .NET: 次のようなことが可能です [最新バージョンはこちらからダウンロードしてください](https://releases.aspose.com/words/net/)ライセンスを購入する必要がある場合は、 [ここ](https://purchase.aspose.com/buy)または、 [一時ライセンス](https://purchase.aspose.com/temporary-license/) または、 [無料トライアル](https://releases。aspose.com/).
2. 開発環境: Visual Studio またはその他の C# IDE。
3. C# の基本知識: C# プログラミングに精通していれば、このチュートリアルは簡単に理解できます。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートする必要があります。これらはプロジェクトの構成要素のようなものです。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

プロセスを管理しやすいステップに分解してみましょう。各ステップは前のステップを基盤として構築され、完全なソリューションへと導きます。

## ステップ1: ディレクトリの設定

ドキュメントの挿入を始める前に、ドキュメントディレクトリへのパスを定義する必要があります。ここにドキュメントが保存されます。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ステップ2: メインドキュメントの読み込み

次に、メイン文書を読み込みます。この文書には、他の文書を挿入するための差し込みフィールドが含まれています。

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## ステップ3: フィールドマージコールバックの設定

マージ処理を実行するには、コールバック関数を設定する必要があります。この関数は、指定されたマージフィールドにドキュメントを挿入する役割を担います。

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## ステップ4: 差し込み印刷を実行する

いよいよ差し込み印刷を実行します。ここで魔法が起こります。差し込み印刷フィールドと、そのフィールドに挿入する文書を指定します。

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## ステップ5: ドキュメントを保存する

差し込み印刷が完了したら、変更した文書を保存します。この新しい文書には、挿入したコンテンツが希望の場所に正確に配置されます。

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## ステップ6: コールバックハンドラの作成

コールバックハンドラは、差し込みフィールドに対して特別な処理を行うクラスです。フィールド値で指定されたドキュメントを読み込み、現在の差し込みフィールドに挿入します。

```csharp
private class InsertDocumentAtMailMergeHandler : IFieldMergingCallback
{
    void IFieldMergingCallback.FieldMerging(FieldMergingArgs args)
    {
        if (args.DocumentFieldName == "Document_1")
        {
            DocumentBuilder builder = new DocumentBuilder(args.Document);
            builder.MoveToMergeField(args.DocumentFieldName);

            Document subDoc = new Document((string)args.FieldValue);
            InsertDocument(builder.CurrentParagraph, subDoc);

            if (!builder.CurrentParagraph.HasChildNodes)
                builder.CurrentParagraph.Remove();

            args.Text = null;
        }
    }
}
```

## ステップ7: ドキュメントの挿入

このメソッドは、指定されたドキュメントを現在の段落または表のセルに挿入します。

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        foreach (Node srcNode in srcSection.Body)
        {
            if (srcNode.NodeType == NodeType.Paragraph)
            {
                Paragraph para = (Paragraph)srcNode;
                if (para.IsEndOfSection && !para.HasChildNodes)
                    continue;
            }

            Node newNode = importer.ImportNode(srcNode, true);
            destinationParent.InsertAfter(newNode, insertionDestination);
            insertionDestination = newNode;
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}
```

## 結論

これで完了です！Aspose.Words for .NET を使って、差し込み印刷時に特定のフィールドにドキュメントを挿入することができました。この強力な機能は、特に大量のドキュメントを扱う際に、時間と労力を大幅に節約できます。まるで、面倒な作業をすべて引き受けてくれるパーソナルアシスタントがいるかのようです。さあ、ぜひ試してみてください。コーディングを楽しんでください！

## よくある質問

### 異なるマージフィールドに複数のドキュメントを挿入できますか?
はい、できます。適切な差し込みフィールドと対応するドキュメントパスを指定するだけです。 `MailMerge.Execute` 方法。

### 挿入されたドキュメントをメインドキュメントとは異なる形式でフォーマットすることは可能ですか?
もちろんです！ `ImportFormatMode` パラメータの `NodeImporter` 書式を制御します。

### マージフィールド名が動的な場合はどうなりますか?
動的なマージ フィールド名をコールバック ハンドラーにパラメーターとして渡すことで、動的なマージ フィールド名を処理できます。

### この方法は異なるファイル形式でも使用できますか?
はい、Aspose.Words は DOCX、PDF などさまざまなファイル形式をサポートしています。

### ドキュメント挿入プロセス中にエラーが発生した場合、どうすれば処理できますか?
発生する可能性のある例外を管理するには、コールバック ハンドラーにエラー処理を実装します。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}