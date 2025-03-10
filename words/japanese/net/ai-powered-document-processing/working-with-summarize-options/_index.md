---
title: 要約オプションの操作
linktitle: 要約オプションの操作
second_title: Aspose.Words ドキュメント処理 API
description: 迅速な洞察を得るために AI モデルを統合するステップバイステップ ガイドを使用して、Aspose.Words for .NET を使用して Word 文書を効果的に要約する方法を学びます。
weight: 10
url: /ja/net/ai-powered-document-processing/working-with-summarize-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 要約オプションの操作

## 導入

ドキュメント、特に大きなドキュメントを扱う場合、要点を要約すると便利です。干し草の山から針を探すように何ページものテキストを精査した経験があれば、要約の効率性に感謝するでしょう。このチュートリアルでは、Aspose.Words for .NET を活用してドキュメントを効果的に要約する方法について詳しく説明します。個人使用、職場でのプレゼンテーション、学術的な取り組みなど、どのような用途でも、このガイドではプロセスをステップごとに説明します。

## 前提条件

ドキュメント要約の作業を始める前に、次の前提条件が満たされていることを確認してください。

1.  Aspose.Words for .NET ライブラリ: Aspose.Words ライブラリをダウンロードしたことを確認してください。[ここ](https://releases.aspose.com/words/net/).
2. .NET 環境: システムには .NET 環境 (Visual Studio など) が設定されている必要があります。.NET を初めて使用する場合でも心配はいりません。非常に使いやすいです。
3. C# の基礎知識: C# プログラミングの知識があると役立ちます。コードでいくつかの手順を実行するので、基本を理解しておくとスムーズに作業できます。
4. AI モデルの API キー: 要約には生成言語モデルを活用するため、環境で設定できる API キーが必要です。

これらの前提条件をチェックしたら、準備完了です。

## パッケージのインポート

まず、プロジェクトに必要なパッケージを入手しましょう。Aspose.Words と、要約に使用する AI パッケージが必要です。手順は次のとおりです。

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

Visual Studio の NuGet パッケージ マネージャーを使用して、必要な NuGet パッケージを必ずインストールしてください。

環境の準備ができたので、Aspose.Words for .NET を使用してドキュメントを要約する手順を見ていきましょう。

## ステップ1: ドキュメントディレクトリの設定 

ドキュメントの処理を開始する前に、ディレクトリを設定することをお勧めします。この構成により、入力ファイルと出力ファイルを効率的に管理できます。

```csharp
//ドキュメントディレクトリ
string MyDir = "YOUR_DOCUMENT_DIRECTORY"; 
//ArtifactsDir ディレクトリ
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY"; 
```

必ず交換してください`"YOUR_DOCUMENT_DIRECTORY"`そして`"YOUR_ARTIFACTS_DIRECTORY"`ドキュメントが保存されているシステム上の実際のパスと、要約ファイルを保存する場所を指定します。

## ステップ2: ドキュメントの読み込み 

次に、要約したいドキュメントを読み込む必要があります。ここでテキストをプログラムに取り込みます。

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

ここでは2つのドキュメントを読み込んでいます。`Big document.docx`そして`Document.docx`指定したディレクトリにこれらのファイルが存在することを確認してください。

## ステップ3: AIモデルの設定 

次は、ドキュメントの要約に役立つ AI モデルを操作します。まず API キーを設定する必要があります。 

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

この例では、OpenAI の GPT-4 Mini を使用しています。これが適切に機能するには、環境変数に API キーが正しく設定されていることを確認してください。

## ステップ4: 1つのドキュメントを要約する

ここからが楽しい部分、要約です。まず、1 つのドキュメントを要約してみましょう。 

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

ここではAIモデルに要約を依頼しています`firstDoc`要約の長さが短い。要約されたドキュメントは、指定された成果物ディレクトリに保存されます。

## ステップ5: 複数のドキュメントを要約する

要約するドキュメントが複数ある場合はどうすればよいでしょうか? 心配はいりません! 次の手順では、その処理方法を説明します。

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

この場合、私たちは両方を要約しています`firstDoc`そして`secondDoc`また、要約の長さを長く指定しました。要約された出力により、すべての詳細を読み通さなくても主要なアイデアを把握できるようになります。

## 結論

これで完了です。Aspose.Words for .NET を使用して 1 つまたは 2 つのドキュメントを要約できました。ここで説明した手順は、より大規模なプロジェクトに適用したり、さまざまなドキュメント処理タスクを自動化したりすることもできます。要約により、ドキュメントの本質を保持しながら、時間と労力を大幅に節約できることを覚えておいてください。 

コードをいじってみたいと思いませんか？どうぞ！この技術の素晴らしいところは、自分のニーズに合わせて調整できることです。その他のリソースやドキュメントは、こちらでご覧いただけます。[Aspose.Words for .NET ドキュメント](https://reference.aspose.com/words/net/)何か問題が起こった場合は、[Aspose サポート フォーラム](https://forum.aspose.com/c/words/8/)クリックするだけです。

## よくある質問

### Aspose.Words とは何ですか?
Aspose.Words は、開発者が Microsoft Word をインストールしなくても Word 文書に対して操作を実行できる強力なライブラリです。

### Aspose を使用して PDF を要約できますか?
Aspose.Words は主に Word 文書を扱います。PDF を要約する場合は、Aspose.PDF を確認することをお勧めします。

### AI モデルを実行するにはインターネット接続が必要ですか?
はい。AI モデルにはアクティブなインターネット接続に依存する API 呼び出しが必要です。

### Aspose.Words の試用版はありますか?
もちろんです！無料トライアルはこちらからダウンロードできます[ここ](https://releases.aspose.com/).

### 問題が発生した場合はどうすればよいですか?
問題が発生した場合やご質問がある場合は、[サポートフォーラム](https://forum.aspose.com/c/words/8/)ガイダンスのため。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
