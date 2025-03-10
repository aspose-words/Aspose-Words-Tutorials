---
title: ドキュメントビルダーなしでASKFieldを挿入する
linktitle: ドキュメントビルダーなしでASKFieldを挿入する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET で Document Builder を使用せずに ASK フィールドを挿入する方法を学びます。このガイドに従って、Word ドキュメントを動的に強化します。
weight: 10
url: /ja/net/working-with-fields/insert-askfield-with-out-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ドキュメントビルダーなしでASKFieldを挿入する

## 導入

Aspose.Words for .NET でドキュメントの自動化をマスターしたいですか? まさにうってつけの場所です! 今日は、ドキュメント ビルダーを使用せずに ASK フィールドを挿入する方法について説明します。これは、ドキュメントでユーザーに特定の入力を促し、Word ドキュメントをよりインタラクティブかつダイナミックにしたい場合に便利な機能です。それでは、ドキュメントをもっとスマートにしてみましょう!

## 前提条件

コードに手をつける前に、すべてがセットアップされていることを確認しましょう。

1.  Aspose.Words for .NET: このライブラリがインストールされていることを確認してください。インストールされていない場合は、ここからダウンロードできます。[ここ](https://releases.aspose.com/words/net/).
2. 開発環境: Visual Studio などの適切な IDE。
3. .NET Framework: .NET Framework がインストールされていることを確認します。

素晴らしい! これで準備はすべて整いました。まずは必要な名前空間をインポートしましょう。

## 名前空間のインポート

まず最初に、Aspose.Words for .NET のすべての機能にアクセスするには、Aspose.Words 名前空間をインポートする必要があります。手順は次のとおりです。

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

## ステップ1: 新しいドキュメントを作成する

ASK フィールドを挿入する前に、作業するドキュメントが必要です。新しいドキュメントを作成する方法は次のとおりです。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENTS DIRECTORY";

//ドキュメントの作成。
Document doc = new Document();
```

このコード スニペットは、ASK フィールドを追加する新しい Word 文書を設定します。

## ステップ2: 段落ノードにアクセスする

Word 文書では、コンテンツはノードに編成されます。ASK フィールドを挿入する最初の段落ノードにアクセスする必要があります。

```csharp
Paragraph para = (Paragraph)doc.GetChild(NodeType.Paragraph, 0, true);
```

このコード行は、ドキュメントの最初の段落を取得し、ASK フィールドの挿入の準備を整えます。

## ステップ3: ASKフィールドを挿入する

さて、メインイベントである ASK フィールドの挿入に移りましょう。このフィールドは、ドキュメントを開いたときにユーザーに入力を促します。

```csharp
// ASK フィールドを挿入します。
FieldAsk field = (FieldAsk)para.AppendField(FieldType.FieldAsk, false);
```

ここでは、段落に ASK フィールドを追加します。簡単ですよね?

## ステップ4: ASKフィールドを構成する

ASK フィールドの動作を定義するには、いくつかのプロパティを設定する必要があります。ブックマーク名、プロンプト テキスト、既定の応答、および差し込み印刷の動作を構成しましょう。

```csharp
field.BookmarkName = "Test1";
field.PromptText = "Please enter your response:";
field.DefaultResponse = "Default response";
field.PromptOnceOnMailMerge = true;
```

- BookmarkName: ASK フィールドの一意の識別子。
- PromptText: ユーザーに入力を促すテキスト。
- DefaultResponse: ユーザーが変更できる事前に入力された応答。
- PromptOnceOnMailMerge: メールの差し込み印刷中にプロンプトが 1 回だけ表示されるかどうかを決定します。

## ステップ5: フィールドを更新する

ASK フィールドを設定したら、すべての設定が正しく適用されていることを確認するために更新する必要があります。

```csharp
field.Update();
```

このコマンドは、ASK フィールドが準備され、ドキュメント内で適切に設定されていることを確認します。

## ステップ6: ドキュメントを保存する

最後に、指定したディレクトリにドキュメントを保存しましょう。

```csharp
doc.Save(dataDir + "InsertionChampASKSansDocumentBuilder.docx");
```

この行は、挿入された ASK フィールドを含むドキュメントを保存します。これで、ドキュメントに動的な ASK フィールドが装備されました。

## 結論

おめでとうございます! ドキュメント ビルダーを使用せずに Aspose.Words for .NET を使用して、Word ドキュメントに ASK フィールドを追加しました。この機能により、ドキュメントに対するユーザー インタラクションが大幅に強化され、より柔軟でユーザー フレンドリなものになります。さまざまなフィールドとプロパティを試して、Aspose.Words の可能性を最大限に引き出してください。コーディングをお楽しみください!

## よくある質問

### Aspose.Words の ASK フィールドとは何ですか?
Aspose.Words の ASK フィールドは、ドキュメントを開いたときにユーザーに特定の入力を求めるフィールドであり、動的なデータ入力を可能にします。

### 1 つのドキュメントで複数の ASK フィールドを使用できますか?
はい、ドキュメントに複数の ASK フィールドを挿入し、それぞれに固有のプロンプトと応答を含めることができます。

### の目的は何ですか？`PromptOnceOnMailMerge` property?
の`PromptOnceOnMailMerge`プロパティは、メールの差し込み印刷操作中に ASK プロンプトが 1 回だけ表示されるか、毎回表示されるかを決定します。

### プロパティを設定した後、ASK フィールドを更新する必要がありますか?
はい、ASK フィールドを更新すると、すべてのプロパティが正しく適用され、フィールドが期待どおりに機能することが保証されます。

### プロンプトテキストとデフォルトの応答をカスタマイズできますか?
もちろんです! カスタムプロンプトテキストとデフォルトの応答を設定して、ASK フィールドを特定のニーズに合わせてカスタマイズできます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
