---
title: ビルダーでドキュメントを挿入
linktitle: ビルダーでドキュメントを挿入
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して 2 つの Word 文書を結合する方法を学びます。DocumentBuilder を使用して文書を挿入し、書式を保持するためのステップバイステップ ガイドです。
weight: 10
url: /ja/net/join-and-append-documents/insert-document-with-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ビルダーでドキュメントを挿入

## 導入

つの Word 文書があり、それを 1 つに結合したいとします。「プログラムでこれを行う簡単な方法はないだろうか?」とお考えかもしれません。もちろんあります! 今日は、Aspose.Words for .NET ライブラリを使用して、1 つの文書を別の文書に挿入するプロセスについて説明します。この方法は、特に大きな文書を扱っている場合やプロセスを自動化する必要がある場合に非常に便利です。早速始めましょう!

## 前提条件

始める前に、必要なものがすべて揃っていることを確認しましょう。

1.  Aspose.Words for .NET: まだダウンロードしていない場合は、こちらからダウンロードできます。[ここ](https://releases.aspose.com/words/net/).
2. 開発環境: Visual Studio またはその他の適切な IDE がインストールされていることを確認してください。
3. C# の基本知識: C# に少しでも精通していると、大いに役立ちます。

## 名前空間のインポート

まず最初に、Aspose.Words ライブラリの機能にアクセスするために必要な名前空間をインポートする必要があります。手順は次のとおりです。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

前提条件が整ったので、プロセスを段階的に説明しましょう。

## ステップ1: ドキュメントディレクトリの設定

コーディングを始める前に、ドキュメント ディレクトリへのパスを設定する必要があります。ここにソース ドキュメントと宛先ドキュメントが保存されます。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する`"YOUR DOCUMENT DIRECTORY"`ドキュメントが保存されている実際のパスを入力します。これにより、プログラムがファイルを簡単に見つけられるようになります。

## ステップ2: ソースドキュメントと宛先ドキュメントの読み込み

次に、作業するドキュメントを読み込む必要があります。この例では、ソース ドキュメントと宛先ドキュメントがあります。

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

ここでは、`Document`ドキュメントを読み込むには、Aspose.Words ライブラリのクラスを使用します。ファイル名がディレクトリ内のファイル名と一致していることを確認してください。

## ステップ 3: DocumentBuilder オブジェクトの作成

の`DocumentBuilder`クラスは、Aspose.Words ライブラリの強力なツールです。これにより、ドキュメントをナビゲートしたり操作したりすることができます。

```csharp
DocumentBuilder builder = new DocumentBuilder(dstDoc);
```

このステップでは、`DocumentBuilder`宛先ドキュメントのオブジェクト。これにより、ドキュメントにコンテンツを挿入できるようになります。

## ステップ4: 文書の末尾に移動する

ソース ドキュメントを挿入する前に、ビルダー カーソルを宛先ドキュメントの末尾に移動する必要があります。

```csharp
builder.MoveToDocumentEnd();
```

これにより、ソース ドキュメントが宛先ドキュメントの最後に挿入されるようになります。

## ステップ5: ページ区切りの挿入

整理するために、ソース ドキュメントを挿入する前に改ページを追加しましょう。これにより、ソース ドキュメントの内容が新しいページで開始されます。

```csharp
builder.InsertBreak(BreakType.PageBreak);
```

ページ区切りにより、ソース ドキュメントのコンテンツが新しいページで開始され、結合されたドキュメントがプロフェッショナルな外観になります。

## ステップ6: ソースドキュメントの挿入

ここで、実際にソース ドキュメントを宛先ドキュメントに挿入するという、興味深い部分が始まります。

```csharp
builder.InsertDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

使用方法`InsertDocument`この方法では、ソース文書全体を宛先文書に挿入することができます。`ImportFormatMode.KeepSourceFormatting`ソース ドキュメントの書式が保持されることを保証します。

## ステップ7: 結合した文書を保存する

最後に、結合したドキュメントを保存します。これにより、ソース ドキュメントと宛先ドキュメントが 1 つのファイルに結合されます。

```csharp
builder.Document.Save(dataDir + "JoinAndAppendDocuments.InsertDocumentWithBuilder.docx");
```

ドキュメントを保存すると、2 つのドキュメントを結合するプロセスが完了します。これで新しいドキュメントの準備が整い、指定したディレクトリに保存されます。

## 結論

これで完了です。Aspose.Words for .NET を使用して、あるドキュメントを別のドキュメントに挿入できました。この方法は効率的であるだけでなく、両方のドキュメントの書式設定が保持されるため、シームレスな結合が保証されます。1 回限りのプロジェクトで作業している場合でも、ドキュメント処理を自動化する必要がある場合でも、Aspose.Words for .NET が役立ちます。

## よくある質問

### Aspose.Words for .NET とは何ですか?  
Aspose.Words for .NET は、開発者がプログラムによって Word 文書を作成、編集、変換、操作できるようにする強力なライブラリです。

### ソースドキュメントの書式を維持できますか?  
はい、使用することで`ImportFormatMode.KeepSourceFormatting`、ソース ドキュメントの書式設定は、宛先ドキュメントに挿入されたときに保持されます。

### Aspose.Words for .NET を使用するにはライセンスが必要ですか?  
はい、Aspose.Words for .NETの全機能を使用するにはライセンスが必要です。[一時ライセンス](https://purchase.aspose.com/temporary-license/)評価のため。

### このプロセスを自動化できますか?  
もちろんです! 説明した方法は、より大規模なアプリケーションに組み込んで、ドキュメント処理タスクを自動化できます。

### より多くのリソースとサポートはどこで見つかりますか?  
詳細については、[ドキュメント](https://reference.aspose.com/words/net/) 、または[サポートフォーラム](https://forum.aspose.com/c/words/8)援助をお願いします。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
