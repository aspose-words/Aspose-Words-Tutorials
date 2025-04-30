---
"description": "Aspose.Words for .NET を使用して、Word ファイルにカスタム ドキュメント プロパティを追加する方法を学びます。ステップバイステップのガイドに従って、メタデータを追加することでドキュメントを強化しましょう。"
"linktitle": "カスタムドキュメントプロパティを追加する"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "カスタムドキュメントプロパティを追加する"
"url": "/ja/net/programming-with-document-properties/add-custom-document-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# カスタムドキュメントプロパティを追加する

## 導入

こんにちは！Aspose.Words for .NET の世界に飛び込んで、Word ファイルにカスタム ドキュメント プロパティを追加する方法を知りたいですか？まさにその通りです！カスタム プロパティは、組み込みプロパティではカバーされていない追加のメタデータを保存するのに非常に便利です。ドキュメントの承認、リビジョン番号の追加、特定の日付の挿入など、カスタム プロパティを使えば様々なことができます。このチュートリアルでは、Aspose.Words for .NET を使用してこれらのプロパティをシームレスに追加する手順を詳しく説明します。準備はできましたか？さあ、始めましょう！

## 前提条件

コードに進む前に、必要なものがすべて揃っていることを確認しましょう。

1. Aspose.Words for .NET ライブラリ: Aspose.Words for .NET ライブラリがインストールされていることを確認してください。ダウンロードできます。 [ここ](https://releases。aspose.com/words/net/).
2. 開発環境: Visual Studio のような IDE。
3. C# の基本知識: このチュートリアルでは、C# と .NET の基本的な知識があることを前提としています。
4. サンプル文書:サンプルのWord文書を用意し、 `Properties.docx`これを変更します。

## 名前空間のインポート

コーディングを始める前に、必要な名前空間をインポートする必要があります。これは、コードがAspose.Wordsが提供するすべての機能にアクセスできるようにするために重要なステップです。

```csharp
using System;
using Aspose.Words;
```

## ステップ1: ドキュメントパスの設定

まず最初に、ドキュメントへのパスを設定する必要があります。ここで、ドキュメントの場所を指定します。 `Properties.docx` ファイル。

```csharp
// ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

このスニペットでは、 `"YOUR DOCUMENT DIRECTORY"` ドキュメントへの実際のパスを入力します。この手順は、プログラムがWordファイルを見つけて開くために非常に重要です。

## ステップ2: カスタムドキュメントプロパティにアクセスする

次に、Word文書のカスタムドキュメントプロパティにアクセスしてみましょう。ここにすべてのカスタムメタデータが保存されます。

```csharp
CustomDocumentProperties customDocumentProperties = doc.CustomDocumentProperties;
```

これを行うことで、次の手順で操作するカスタム プロパティ コレクションを処理できるようになります。

## ステップ3: 既存のプロパティを確認する

新しいプロパティを追加する前に、特定のプロパティが既に存在するかどうかを確認することをお勧めします。これにより、不要な重複を回避できます。

```csharp
if (customDocumentProperties["Authorized"] != null) return;
```

この行は、プロパティ「Authorized」が既に存在するかどうかを確認します。存在する場合、重複するプロパティの追加を防ぐため、プログラムはメソッドを早期に終了します。

## ステップ4: ブールプロパティの追加

ここで、最初のカスタム プロパティ（ドキュメントが承認されているかどうかを示すブール値）を追加しましょう。

```csharp
customDocumentProperties.Add("Authorized", true);
```

この行は、「Authorized」という名前のカスタムプロパティを次の値で追加します。 `true`. シンプルでわかりやすい！

## ステップ5: 文字列プロパティの追加

次に、ドキュメントを承認したユーザーを指定するための別のカスタム プロパティを追加します。

```csharp
customDocumentProperties.Add("Authorized By", "John Smith");
```

ここでは、「Authorized By」というプロパティに「John Smith」という値を追加しています。「John Smith」は任意の名前に置き換えてください。

## ステップ6: 日付プロパティの追加

承認日を保存するプロパティを追加しましょう。これにより、ドキュメントがいつ承認されたかを追跡しやすくなります。

```csharp
customDocumentProperties.Add("Authorized Date", DateTime.Today);
```

このスニペットは、現在の日付を値として持つ「Authorized Date」というプロパティを追加します。 `DateTime.Today` プロパティは今日の日付を自動的に取得します。

## ステップ7: リビジョン番号の追加

ドキュメントのリビジョン番号を追跡するためのプロパティを追加することもできます。これはバージョン管理に特に便利です。

```csharp
customDocumentProperties.Add("Authorized Revision", doc.BuiltInDocumentProperties.RevisionNumber);
```

ここでは、「承認済みリビジョン」というプロパティを追加し、ドキュメントの現在のリビジョン番号を割り当てています。

## ステップ8: 数値プロパティの追加

最後に、承認金額を格納する数値プロパティを追加しましょう。これは予算額から取引金額まで、あらゆる数値に対応します。

```csharp
customDocumentProperties.Add("Authorized Amount", 123.45);
```

この行は、「承認金額」という名前のプロパティを次の値で追加します。 `123.45`繰り返しになりますが、この数字は必要に応じて任意の数字に置き換えてください。

## 結論

これで完了です！Aspose.Words for .NET を使用して、Word 文書にカスタム ドキュメント プロパティを追加できました。これらのプロパティは、ニーズに応じた追加メタデータの保存に非常に役立ちます。承認の詳細、リビジョン番号、特定の金額などを追跡する場合でも、カスタム プロパティは柔軟なソリューションを提供します。

Aspose.Words for .NET をマスターするには、練習が鍵です。様々なプロパティを試してみて、ドキュメントをどう強化できるか試してみてください。コーディングを楽しみましょう！

## よくある質問

### カスタム ドキュメント プロパティとは何ですか?
カスタム ドキュメント プロパティは、組み込みプロパティでカバーされていない追加情報を保存するために Word ドキュメントに追加できるメタデータです。

### 文字列や数値以外のプロパティを追加できますか?
はい、ブール値、日付、さらにはカスタム オブジェクトなど、さまざまな種類のプロパティを追加できます。

### Word 文書でこれらのプロパティにアクセスするにはどうすればよいでしょうか?
カスタム プロパティは、Aspose.Words を使用してプログラムでアクセスすることも、ドキュメント プロパティを通じて Word で直接表示することもできます。

### カスタムプロパティを編集または削除することは可能ですか?
はい、Aspose.Words が提供する同様の方法を使用して、カスタム プロパティを簡単に編集または削除できます。

### ドキュメントのフィルタリングにカスタム プロパティを使用できますか?
もちろんです！カスタム プロパティは、特定のメタデータに基づいてドキュメントを分類およびフィルタリングするのに最適です。



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}