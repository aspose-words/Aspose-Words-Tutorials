---
"description": "Aspose.Words for .NET の Word 文書の細分性の比較機能について学習します。この機能を使用すると、文書を文字ごとに比較し、変更内容を報告できます。"
"linktitle": "Word文書の比較粒度"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "Word文書の比較粒度"
"url": "/ja/net/compare-documents/comparison-granularity/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word文書の比較粒度

ここでは、Aspose.Words for .NET の Word 文書の粒度比較機能を使用する以下の C# ソース コードを説明するステップ バイ ステップ ガイドを示します。

## ステップ1：導入

Aspose.Words for .NET の「比較粒度」機能を使用すると、文字レベルでドキュメントを比較できます。つまり、各文字が比較され、それに応じて変更内容がレポートされます。

## ステップ2: 環境の設定

始める前に、Aspose.Words for .NET を使用するための開発環境をセットアップする必要があります。Aspose.Words ライブラリがインストールされていること、そしてコードを埋め込むための適切な C# プロジェクトがあることを確認してください。

## ステップ3: 必要なアセンブリを追加する

Aspose.Words for .NET の粒度比較機能を使用するには、必要なアセンブリをプロジェクトに追加する必要があります。プロジェクトに Aspose.Words への適切な参照があることを確認してください。

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## ステップ4: ドキュメントの作成

このステップでは、DocumentBuilderクラスを使用して2つのドキュメントを作成します。これらのドキュメントは比較に使用されます。

```csharp
// ドキュメントAを作成します。
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// ドキュメントBを作成します。
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## ステップ5: 比較オプションの設定

このステップでは、比較オプションを設定して比較の粒度を指定します。ここでは文字レベルの粒度を使用します。

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## ステップ6: ドキュメントの比較

それでは、DocumentクラスのCompareメソッドを使ってドキュメントを比較してみましょう。変更はドキュメントAに保存されます。

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

その `Compare` このメソッドは、ドキュメント A とドキュメント B を比較し、変更をドキュメント A に保存します。参照用として、作成者の名前と比較の日付を指定できます。

## 結論

この記事では、Aspose.Words for .NET の「粒度比較」機能について解説しました。この機能を使うと、文字レベルでドキュメントを比較し、変更点をレポートできます。この知識は、プロジェクトで詳細なドキュメント比較を行う際に役立ちます。

### Aspose.Words for .NET を使用した比較粒度のサンプル ソース コード

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## 結論

このチュートリアルでは、Aspose.Words for .NET の比較粒度機能について説明しました。この機能を使用すると、ドキュメントを比較する際の詳細レベルを指定できます。粒度レベルを選択することにより、特定の要件に応じて、文字レベル、単語レベル、ブロックレベルなど、詳細な比較を実行できます。Aspose.Words for .NET は柔軟かつ強力なドキュメント比較機能を提供し、粒度が異なるドキュメント間の差異を容易に特定できます。

### よくある質問

#### Q: Aspose.Words for .NET で比較の粒度を使用する目的は何ですか?

A: Aspose.Words for .NET の比較粒度を使用すると、ドキュメントを比較する際の詳細レベルを指定できます。この機能を使用すると、文字レベル、単語レベル、さらにはブロックレベルなど、さまざまなレベルでドキュメントを比較できます。粒度レベルごとに、比較結果の詳細レベルが異なります。

#### Q: Aspose.Words for .NET で比較の粒度を使用するにはどうすればよいですか?

A: Aspose.Words for .NET で比較の粒度を使用するには、次の手順に従います。
1. Aspose.Words ライブラリを使用して開発環境をセットアップします。
2. Aspose.Words を参照して、必要なアセンブリをプロジェクトに追加します。
3. 比較したい文書を、 `DocumentBuilder` クラス。
4. 比較オプションを設定するには、 `CompareOptions` オブジェクトと設定 `Granularity` 希望するレベルにプロパティを設定します（例： `Granularity.CharLevel` （文字レベルの比較用）。
5. 使用 `Compare` 一方の文書にメソッドを渡し、もう一方の文書と `CompareOptions` オブジェクトをパラメータとして渡します。このメソッドは、指定された粒度に基づいてドキュメントを比較し、最初のドキュメントの変更を保存します。

#### Q: Aspose.Words for .NET で使用できる比較粒度レベルは何ですか?

A: Aspose.Words for .NET では、次の 3 つのレベルの比較粒度が提供されます。
- `Granularity.CharLevel`: 文書を文字レベルで比較します。
- `Granularity.WordLevel`: 文書を単語レベルで比較します。
- `Granularity.BlockLevel`: ブロック レベルでドキュメントを比較します。

#### Q: 文字レベルの粒度で比較結果をどのように解釈すればよいですか?

A: 文字レベルの粒度では、比較対象の文書内の各文字の差異が分析されます。比較結果には、追加、削除、変更など、個々の文字レベルでの変更が表示されます。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}