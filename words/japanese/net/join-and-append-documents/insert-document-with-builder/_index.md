---
"description": "Aspose.Words for .NET を使用して 2 つの Word 文書を結合する方法を学びます。DocumentBuilder を使用して文書を挿入し、書式設定を保持する手順をステップバイステップで説明します。"
"linktitle": "ビルダーでドキュメントを挿入"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "ビルダーでドキュメントを挿入"
"url": "/ja/net/join-and-append-documents/insert-document-with-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ビルダーでドキュメントを挿入

## 導入

2つのWord文書があり、それを1つに結合したいとします。「プログラムで簡単にできる方法はないかな？」とお考えかもしれません。もちろんです！今日は、Aspose.Words for .NETライブラリを使って、ある文書を別の文書に挿入する手順を解説します。この方法は非常に便利で、特に大きな文書を扱う場合や、処理を自動化する必要がある場合に便利です。早速始めましょう！

## 前提条件

始める前に、必要なものがすべて揃っていることを確認しましょう。

1. Aspose.Words for .NET: まだダウンロードしていない場合は、こちらからダウンロードできます。 [ここ](https://releases。aspose.com/words/net/).
2. 開発環境: Visual Studio またはその他の適切な IDE がインストールされていることを確認してください。
3. C# の基本知識: C# に少しでも精通していると、大いに役立ちます。

## 名前空間のインポート

まず最初に、Aspose.Words ライブラリの機能にアクセスするために必要な名前空間をインポートする必要があります。手順は以下のとおりです。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

前提条件が整ったので、プロセスを段階的に説明しましょう。

## ステップ1: ドキュメントディレクトリの設定

コーディングを始める前に、ドキュメントディレクトリへのパスを設定する必要があります。ここにソースドキュメントとターゲットドキュメントが保存されます。

```csharp
// ドキュメントディレクトリへのパス 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する `"YOUR DOCUMENT DIRECTORY"` ドキュメントが保存されている実際のパスを入力してください。これにより、プログラムがファイルを簡単に見つけられるようになります。

## ステップ2: ソースドキュメントとターゲットドキュメントの読み込み

次に、作業対象となるドキュメントを読み込む必要があります。この例では、ソースドキュメントと宛先ドキュメントがあります。

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

ここでは、 `Document` ドキュメントを読み込むには、Aspose.Wordsライブラリのクラスを使用します。ファイル名がディレクトリ内のファイル名と一致していることを確認してください。

## ステップ3: DocumentBuilderオブジェクトの作成

その `DocumentBuilder` クラスはAspose.Wordsライブラリの強力なツールです。これにより、ドキュメント内を移動したり操作したりすることができます。

```csharp
DocumentBuilder builder = new DocumentBuilder(dstDoc);
```

このステップでは、 `DocumentBuilder` 対象ドキュメントのオブジェクト。これにより、ドキュメントにコンテンツを挿入できるようになります。

## ステップ4: 文書の末尾に移動する

ソース ドキュメントを挿入する前に、ビルダー カーソルを宛先ドキュメントの末尾に移動する必要があります。

```csharp
builder.MoveToDocumentEnd();
```

これにより、ソース ドキュメントが宛先ドキュメントの末尾に挿入されるようになります。

## ステップ5: ページ区切りの挿入

見た目をすっきりさせるために、ソース文書を挿入する前に改ページを追加しましょう。これにより、ソース文書の内容が新しいページから開始されます。

```csharp
builder.InsertBreak(BreakType.PageBreak);
```

ページ区切りにより、ソース ドキュメントのコンテンツが新しいページで開始され、結合されたドキュメントがプロフェッショナルな外観になります。

## ステップ6: ソースドキュメントの挿入

次は、実際にソース ドキュメントを宛先ドキュメントに挿入する、楽しい部分です。

```csharp
builder.InsertDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

使用して `InsertDocument` この方法を使用すると、ソース文書全体を目的の文書に挿入できます。 `ImportFormatMode.KeepSourceFormatting` ソース ドキュメントの書式が保持されます。

## ステップ7: 結合した文書を保存する

最後に、結合した文書を保存しましょう。これにより、結合元文書と結合先文書が1つのファイルに結合されます。

```csharp
builder.Document.Save(dataDir + "JoinAndAppendDocuments.InsertDocumentWithBuilder.docx");
```

ドキュメントを保存すると、2つのドキュメントの結合プロセスが完了します。これで新しいドキュメントが完成し、指定のディレクトリに保存されました。

## 結論

これで完了です！Aspose.Words for .NET を使って、あるドキュメントを別のドキュメントに挿入できました。この方法は効率的であるだけでなく、両方のドキュメントの書式設定も維持されるため、シームレスな結合が保証されます。単発のプロジェクトでも、ドキュメント処理を自動化する必要がある場合でも、Aspose.Words for .NET がきっと役に立ちます。

## よくある質問

### Aspose.Words for .NET とは何ですか?  
Aspose.Words for .NET は、開発者が Word 文書をプログラムで作成、編集、変換、操作できるようにする強力なライブラリです。

### ソースドキュメントの書式を維持できますか?  
はい、使用することで `ImportFormatMode.KeepSourceFormatting`、ソース ドキュメントの書式は、宛先ドキュメントに挿入されたときに保持されます。

### Aspose.Words for .NET を使用するにはライセンスが必要ですか?  
はい、Aspose.Words for .NETの全機能を使用するにはライセンスが必要です。 [一時ライセンス](https://purchase.aspose.com/temporary-license/) 評価のため。

### このプロセスを自動化できますか?  
もちろんです！ここで説明した方法は、より大規模なアプリケーションに組み込んで、ドキュメント処理タスクを自動化することができます。

### さらにリソースやサポートはどこで見つかりますか?  
詳細については、 [ドキュメント](https://reference.aspose.com/words/net/)、または [サポートフォーラム](https://forum.aspose.com/c/words/8) 援助をお願いします。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}