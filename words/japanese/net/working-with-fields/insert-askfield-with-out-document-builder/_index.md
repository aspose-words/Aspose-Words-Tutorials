---
"description": "Aspose.Words for .NETでドキュメントビルダーを使用せずにASKフィールドを挿入する方法を学びましょう。このガイドに従って、Word文書を動的に強化しましょう。"
"linktitle": "ドキュメントビルダーなしでASKFieldを挿入する"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "ドキュメントビルダーなしでASKFieldを挿入する"
"url": "/ja/net/working-with-fields/insert-askfield-with-out-document-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# ドキュメントビルダーなしでASKFieldを挿入する

## 導入

Aspose.Words for .NET を使ったドキュメント自動化をマスターしたいですか？まさにうってつけの場所です！今日は、ドキュメントビルダーを使わずに ASK フィールドを挿入する方法をご紹介します。これは、ユーザーに特定の入力を求めるプロンプトを表示したい場合に便利な機能で、Word ドキュメントをよりインタラクティブでダイナミックなものにすることができます。さあ、早速使ってみて、ドキュメントをもっとスマートにしましょう！

## 前提条件

コードに取り掛かる前に、すべてがセットアップされていることを確認しましょう。

1. Aspose.Words for .NET: このライブラリがインストールされていることを確認してください。まだインストールされていない場合は、こちらからダウンロードできます。 [ここ](https://releases。aspose.com/words/net/).
2. 開発環境: Visual Studio などの適切な IDE。
3. .NET Framework: .NET Framework がインストールされていることを確認します。

素晴らしい！準備が整ったので、必要な名前空間をインポートすることから始めましょう。

## 名前空間のインポート

まず最初に、Aspose.Words for .NET のすべての機能にアクセスするには、Aspose.Words 名前空間をインポートする必要があります。手順は以下のとおりです。

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

## ステップ1：新しいドキュメントを作成する

ASKフィールドを挿入する前に、作業対象となるドキュメントが必要です。新しいドキュメントを作成する方法は次のとおりです。

```csharp
// ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// ドキュメントの作成。
Document doc = new Document();
```

このコード スニペットは、ASK フィールドを追加する新しい Word 文書を設定します。

## ステップ2: 段落ノードにアクセスする

Word文書では、コンテンツはノードに編成されています。ASKフィールドを挿入する最初の段落ノードにアクセスする必要があります。

```csharp
Paragraph para = (Paragraph)doc.GetChild(NodeType.Paragraph, 0, true);
```

このコード行は、ドキュメントの最初の段落を取得し、ASK フィールドの挿入の準備を整えます。

## ステップ3: ASKフィールドを挿入する

さて、いよいよメインイベント、ASKフィールドの挿入です。このフィールドは、ドキュメントを開いた際にユーザーに入力を求めるプロンプトを表示します。

```csharp
// ASK フィールドを挿入します。
FieldAsk field = (FieldAsk)para.AppendField(FieldType.FieldAsk, false);
```

ここで、段落にASKフィールドを追加します。簡単ですよね？

## ステップ4: ASKフィールドを設定する

ASKフィールドの動作を定義するために、いくつかのプロパティを設定する必要があります。ブックマーク名、プロンプトテキスト、デフォルトの応答、差し込み印刷の動作を設定しましょう。

```csharp
field.BookmarkName = "Test1";
field.PromptText = "Please enter your response:";
field.DefaultResponse = "Default response";
field.PromptOnceOnMailMerge = true;
```

- BookmarkName: ASK フィールドの一意の識別子。
- PromptText: ユーザーに入力を促すテキスト。
- DefaultResponse: ユーザーが変更できる事前に入力された応答。
- PromptOnceOnMailMerge: 差し込み印刷中にプロンプトが 1 回だけ表示されるかどうかを決定します。

## ステップ5: フィールドを更新する

ASK フィールドを設定したら、すべての設定が正しく適用されていることを確認するために更新する必要があります。

```csharp
field.Update();
```

このコマンドは、ASK フィールドが準備され、ドキュメント内に適切に設定されていることを確認します。

## ステップ6: ドキュメントを保存する

最後に、指定したディレクトリにドキュメントを保存します。

```csharp
doc.Save(dataDir + "InsertionChampASKSansDocumentBuilder.docx");
```

この行は、挿入されたASKフィールドを含むドキュメントを保存します。これで、ドキュメントに動的なASKフィールドが追加されました。

## 結論

おめでとうございます！Aspose.Words for .NET を使って、Document Builder を使わずに Word 文書に ASK フィールドを追加しました。この機能により、ドキュメントに対するユーザーインタラクションが大幅に向上し、より柔軟で使いやすくすることができます。様々なフィールドやプロパティを試して、Aspose.Words の潜在能力を最大限に引き出しましょう。コーディングを楽しみましょう！

## よくある質問

### Aspose.Words の ASK フィールドとは何ですか?
Aspose.Words の ASK フィールドは、ドキュメントを開いたときにユーザーに特定の入力を求めるフィールドであり、動的なデータ入力を可能にします。

### 1 つのドキュメントで複数の ASK フィールドを使用できますか?
はい、ドキュメントに複数の ASK フィールドを挿入し、それぞれに固有のプロンプトと応答を設定できます。

### の目的は何ですか？ `PromptOnceOnMailMerge` 財産？
その `PromptOnceOnMailMerge` プロパティは、差し込み印刷操作中に ASK プロンプトが 1 回だけ表示されるか、毎回表示されるかを決定します。

### ASK フィールドのプロパティを設定した後、更新する必要がありますか?
はい、ASK フィールドを更新すると、すべてのプロパティが正しく適用され、フィールドが期待どおりに機能することが保証されます。

### プロンプトテキストとデフォルトの応答をカスタマイズできますか?
もちろんです！カスタムプロンプトテキストとデフォルトの応答を設定して、ASK フィールドを特定のニーズに合わせてカスタマイズできます。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}