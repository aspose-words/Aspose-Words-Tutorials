---
title: プロパティを列挙する
linktitle: プロパティを列挙する
second_title: Aspose.Words ドキュメント処理 API
description: このステップバイステップ ガイドでは、Aspose.Words for .NET を使用して Word 文書内のプロパティを列挙する方法を学習します。あらゆるスキル レベルの開発者に最適です。
weight: 10
url: /ja/net/programming-with-document-properties/enumerate-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# プロパティを列挙する

## 導入

Word 文書をプログラムで操作したいとお考えですか? Aspose.Words for .NET は、まさにそれを実現するのに役立つ強力なツールです。今日は、Aspose.Words for .NET を使用して Word 文書のプロパティを列挙する方法について説明します。初心者でも経験者でも、このガイドでは会話形式でわかりやすく段階的に説明します。

## 前提条件

チュートリアルに進む前に、始めるために必要なものがいくつかあります。

-  Aspose.Words for .NET: 次のようなことができます[ここからダウンロード](https://releases.aspose.com/words/net/).
- 開発環境: Visual Studio が推奨されますが、任意の C# IDE を使用できます。
- C# の基礎知識: C# の基礎を理解しておくと、理解しやすくなります。

さあ、早速始めましょう！

## ステップ1: プロジェクトの設定

まず最初に、Visual Studio でプロジェクトを設定する必要があります。

1. 新しいプロジェクトを作成する: Visual Studio を開き、新しいコンソール アプリケーション プロジェクトを作成します。
2. Aspose.Words for .NET をインストールします。NuGet パッケージ マネージャーを使用して Aspose.Words for .NET をインストールします。ソリューション エクスプローラーでプロジェクトを右クリックし、[NuGet パッケージの管理] を選択して、「Aspose.Words」を検索します。パッケージをインストールします。

## ステップ2: 名前空間をインポートする

Aspose.Words を使用するには、必要な名前空間をインポートする必要があります。Program.cs ファイルの先頭に次のコードを追加します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Properties;
```

## ステップ3: ドキュメントを読み込む

次に、作業する Word 文書を読み込みます。この例では、プロジェクト ディレクトリにある「Properties.docx」という名前の文書を使用します。

1. ドキュメント パスの定義: ドキュメントへのパスを指定します。
2. ドキュメントを読み込む: Aspose.Wordsを使用する`Document`ドキュメントを読み込むクラス。

コードは次のとおりです:

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

## ステップ4: ドキュメント名を表示する

ドキュメントが読み込まれたら、その名前を表示したい場合があります。Aspose.Words には、このためのプロパティが用意されています。

```csharp
Console.WriteLine("1. Document name: {0}", doc.OriginalFileName);
```

## ステップ5: 組み込みプロパティを列挙する

組み込みプロパティは、Microsoft Word によって事前定義されたメタデータ プロパティです。これには、タイトル、作成者などが含まれます。

1. 組み込みプロパティにアクセスする:`BuiltInDocumentProperties`コレクション。
2. プロパティをループ: プロパティを反復処理し、その名前と値を表示します。

コードは次のとおりです:

```csharp
Console.WriteLine("2. Built-in Properties");

foreach (DocumentProperty prop in doc.BuiltInDocumentProperties)
    Console.WriteLine("{0} : {1}", prop.Name, prop.Value);
```

## ステップ6: カスタムプロパティを列挙する

カスタム プロパティは、ユーザー定義のメタデータ プロパティです。ドキュメントに追加したい任意のプロパティを設定できます。

1. カスタムプロパティにアクセスするには、`CustomDocumentProperties`コレクション。
2. プロパティをループ: プロパティを反復処理し、その名前と値を表示します。

コードは次のとおりです:

```csharp
Console.WriteLine("3. Custom Properties");

foreach (DocumentProperty prop in doc.CustomDocumentProperties)
    Console.WriteLine("{0} : {1}", prop.Name, prop.Value);
```

## 結論

これで完了です。Aspose.Words for .NET を使用して、Word ドキュメントの組み込みプロパティとカスタム プロパティの両方を正常に列挙できました。これは、Aspose.Words で実行できることのほんの一部にすぎません。ドキュメント生成を自動化する場合でも、複雑なドキュメントを操作する場合でも、Aspose.Words は作業を楽にする豊富な機能を提供します。

## よくある質問

### ドキュメントに新しいプロパティを追加できますか?
はい、新しいカスタムプロパティを追加するには、`CustomDocumentProperties`コレクション。

### Aspose.Words は無料で使用できますか?
 Aspose.Wordsは、[無料トライアル](https://releases.aspose.com/)異なる[購入オプション](https://purchase.aspose.com/buy).

### Aspose.Words のサポートを受けるにはどうすればよいですか?
 Asposeコミュニティからサポートを受けることができます[ここ](https://forum.aspose.com/c/words/8).

### Aspose.Words を他の .NET 言語で使用できますか?
はい、Aspose.Words は VB.NET を含む複数の .NET 言語をサポートしています。

### もっと多くの例はどこで見つかりますか?
チェックしてください[Aspose.Words for .NET ドキュメント](https://reference.aspose.com/words/net/)より多くの例と詳細な情報については、こちらをご覧ください。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
