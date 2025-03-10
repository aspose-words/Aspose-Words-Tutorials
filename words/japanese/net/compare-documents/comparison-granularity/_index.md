---
title: Word 文書の比較の粒度
linktitle: Word 文書の比較の粒度
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET の Word 文書機能で、文書を文字ごとに比較し、変更を報告できる詳細度の比較について学習します。
weight: 10
url: /ja/net/compare-documents/comparison-granularity/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 文書の比較の粒度

ここでは、Aspose.Words for .NET の Word 文書の粒度比較機能を使用する以下の C# ソース コードを説明するステップ バイ ステップ ガイドを示します。

## ステップ1: はじめに

Aspose.Words for .NET の詳細な比較機能を使用すると、文字レベルでドキュメントを比較できます。つまり、各文字が比較され、それに応じて変更が報告されます。

## ステップ2: 環境の設定

開始する前に、Aspose.Words for .NET を使用するための開発環境を設定する必要があります。Aspose.Words ライブラリがインストールされており、コードを埋め込むための適切な C# プロジェクトがあることを確認してください。

## ステップ3: 必要なアセンブリを追加する

Aspose.Words for .NET の粒度比較機能を使用するには、必要なアセンブリをプロジェクトに追加する必要があります。プロジェクトに Aspose.Words への適切な参照があることを確認してください。

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## ステップ4: ドキュメントの作成

このステップでは、DocumentBuilder クラスを使用して 2 つのドキュメントを作成します。これらのドキュメントは比較に使用されます。

```csharp
//ドキュメントAを作成します。
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

//ドキュメントBを作成します。
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## ステップ5: 比較オプションの設定

この手順では、比較の粒度を指定するために比較オプションを構成します。ここでは、文字レベルの粒度を使用します。

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## ステップ6: ドキュメントの比較

次に、Document クラスの Compare メソッドを使用してドキュメントを比較します。変更はドキュメント A に保存されます。

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

の`Compare`メソッドは、ドキュメント A とドキュメント B を比較し、変更をドキュメント A に保存します。参照用に、作成者の名前と比較の日付を指定できます。

## 結論

この記事では、Aspose.Words for .NET の粒度比較機能について説明しました。この機能を使用すると、文字レベルでドキュメントを比較し、変更を報告できます。この知識を使用して、プロジェクトで詳細なドキュメント比較を実行できます。

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

このチュートリアルでは、Aspose.Words for .NET の比較粒度機能について説明しました。この機能を使用すると、ドキュメントを比較する際の詳細レベルを指定できます。異なる粒度レベルを選択することで、特定の要件に応じて、文字、単語、またはブロック レベルで詳細な比較を実行できます。Aspose.Words for .NET は柔軟で強力なドキュメント比較機能を提供し、さまざまな粒度レベルのドキュメントの違いを簡単に識別できます。

### よくある質問

#### Q: Aspose.Words for .NET で比較の粒度を使用する目的は何ですか?

A: Aspose.Words for .NET の比較の粒度により、ドキュメントを比較する際の詳細レベルを指定できます。この機能を使用すると、文字レベル、単語レベル、ブロック レベルなど、さまざまなレベルでドキュメントを比較できます。粒度レベルごとに、比較結果の詳細レベルが異なります。

#### Q: Aspose.Words for .NET で比較の粒度を使用するにはどうすればよいですか?

A: Aspose.Words for .NET で比較の粒度を使用するには、次の手順に従います。
1. Aspose.Words ライブラリを使用して開発環境をセットアップします。
2. Aspose.Words を参照して、必要なアセンブリをプロジェクトに追加します。
3. 比較したい文書を`DocumentBuilder`クラス。
4. 比較オプションを設定するには、`CompareOptions`オブジェクトと設定`Granularity`物件を希望のレベルまで引き上げる（例：`Granularity.CharLevel`文字レベルの比較用)。
5. 使用`Compare`一方の文書にメソッドを適用し、もう一方の文書と`CompareOptions`オブジェクトをパラメータとして渡します。このメソッドは、指定された粒度に基づいてドキュメントを比較し、最初のドキュメントの変更を保存します。

#### Q: Aspose.Words for .NET で利用可能な比較の粒度レベルは何ですか?

A: Aspose.Words for .NET では、比較の粒度を 3 つのレベルで提供します。
- `Granularity.CharLevel`: 文書を文字レベルで比較します。
- `Granularity.WordLevel`: 単語レベルで文書を比較します。
- `Granularity.BlockLevel`: ブロックレベルでドキュメントを比較します。

#### Q: 文字レベルの粒度で比較結果をどのように解釈すればよいですか?

A: 文字レベルの粒度では、比較する文書内の各文字の相違点が分析されます。比較結果には、追加、削除、変更など、個々の文字レベルでの変更が表示されます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
