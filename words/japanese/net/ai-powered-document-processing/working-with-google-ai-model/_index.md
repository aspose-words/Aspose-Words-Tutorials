---
"description": "Aspose.Words for .NET と Google AI を使用してドキュメント処理を強化し、簡潔な要約を簡単に作成します。"
"linktitle": "Google AI モデルの操作"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "Google AI モデルの操作"
"url": "/ja/net/ai-powered-document-processing/working-with-google-ai-model/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Google AI モデルの操作

## 導入

この記事では、Aspose.WordsとGoogleのAIモデルを用いてドキュメントを要約する方法を段階的に解説します。長文のレポートを要約したい場合でも、複数のソースからインサイトを抽出したい場合でも、Aspose.Wordsがお手伝いします。

## 前提条件

実践的な部分に入る前に、成功するための準備を整えましょう。必要なものは以下のとおりです。

1. C# と .NET の基礎知識: プログラミングの概念を理解していると、例をよりよく理解できるようになります。
   
2. Aspose.Words for .NETライブラリ：この強力なライブラリを使用すると、Word文書をシームレスに作成および操作できます。 [ここからダウンロード](https://releases。aspose.com/words/net/).

3. Google AIモデルのAPIキー：AIモデルを利用するには、認証用のAPIキーが必要です。環境変数に安全に保存してください。

4. 開発環境: 動作する .NET 環境 (Visual Studio またはその他の IDE) が設定されていることを確認します。

5. サンプル ドキュメント: 要約をテストするには、サンプルの Word ドキュメント (例: 「Big document.docx」、「Document.docx」) が必要です。

基本を説明したので、コードを見ていきましょう。

## パッケージのインポート

Aspose.Words を操作して Google AI モデルを統合するには、必要な名前空間をインポートする必要があります。手順は以下のとおりです。

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

必要なパッケージがインポートされたので、ドキュメントを要約するプロセスを段階的に説明しましょう。

## ステップ1: ドキュメントディレクトリの設定

ドキュメントを処理する前に、ファイルの保存場所を指定する必要があります。この手順は、Aspose.Words がドキュメントにアクセスできるようにするために非常に重要です。

```csharp
// ドキュメントディレクトリ
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// ArtifactsDirディレクトリ
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

交換する `"YOUR_DOCUMENT_DIRECTORY"` そして `"YOUR_ARTIFACTS_DIRECTORY"` ドキュメントが保存されているシステム上の実際のパスを入力します。これがドキュメントの読み込みと保存の基準となります。

## ステップ2: ドキュメントの読み込み

次に、要約するドキュメントを読み込む必要があります。今回は、先ほど指定した2つのドキュメントを読み込みます。

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

その `Document` Aspose.Wordsのクラスを使うと、Wordファイルをメモリに読み込むことができます。ファイル名がディレクトリ内の実際のドキュメントと一致していることを確認してください。一致していないと、ファイルが見つからないというエラーが発生します。

## ステップ3: APIキーの取得

AIモデルを利用するには、APIキーを取得する必要があります。これはGoogle AIサービスへのアクセスパスとして機能します。

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

このコード行は、環境変数に保存したAPIキーを取得します。セキュリティ上の理由から、APIキーなどの機密情報はコードに含めないようにすることをお勧めします。

## ステップ4: AIモデルインスタンスの作成

さあ、AIモデルのインスタンスを作成しましょう。ここで使用するモデルを選択できます。この例では、GPT-4 Miniモデルを選択します。

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

この行は、ドキュメント要約に使用するAIモデルを設定します。 [ドキュメント](https://reference.aspose.com/words/net/) さまざまなモデルとその機能の詳細については、こちらをご覧ください。

## ステップ5: 1つのドキュメントを要約する

最初のドキュメントの要約に焦点を当てましょう。ここでは短い要約を選択できます。

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

このステップでは、 `Summarize` AIモデルインスタンスからメソッドを呼び出して、最初のドキュメントの要約を取得します。要約の長さは「short」に設定されていますが、必要に応じてカスタマイズできます。要約されたドキュメントは、アーティファクトディレクトリに保存されます。

## ステップ6: 複数の文書を要約する

複数のドキュメントを一度に要約したいですか? Aspose.Words ならこれも簡単です!

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

ここでは、 `Summarize` もう一度メソッドを実行しますが、今回はドキュメントの配列を使用します。これにより、両方のファイルのエッセンスをまとめた長いサマリーが生成されます。結果は前回と同様に、指定されたアーティファクトディレクトリに保存されます。

## 結論

これで完了です！Aspose.Words for .NETとGoogleのAIモデルを使用してドキュメントを要約する環境を構築できました。ドキュメントの読み込みから簡潔な要約の作成まで、これらの手順は大量のテキストを効率的に管理するための合理的なアプローチを提供します。

## よくある質問

### Aspose.Words とは何ですか?
Aspose.Words は、.NET を使用して Word 文書を作成、変更、変換するための強力なライブラリです。

### Google AI の API キーを取得するにはどうすればよいですか?
通常、Google Cloud にサインアップし、必要な API サービスを有効にすることで API キーを取得できます。

### 複数の文書を一度に要約できますか?
はい！示されているように、要約メソッドにドキュメントの配列を渡すことができます。

### どのような種類の要約を作成できますか?
ニーズに応じて、短い要約、中程度の要約、長い要約から選択できます。

### Aspose.Words のその他のリソースはどこで入手できますか?
チェックしてください [ドキュメント](https://reference.aspose.com/words/net/) さらなる例とガイダンスについては、こちらをご覧ください。



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}