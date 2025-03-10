---
title: フェンスコード
linktitle: フェンスコード
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、囲まれたコードと情報文字列を Word 文書に追加する方法を学びます。ステップ バイ ステップ ガイドが含まれています。文書の書式設定スキルを強化します。
weight: 10
url: /ja/net/working-with-markdown/fenced-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# フェンスコード

## 導入

こんにちは、プログラマーの皆さん! 今日は、Aspose.Words for .NET の世界に飛び込んで、Word 文書にフェンス コードや情報文字列を含むフェンス コードを追加する技術を習得します。Word 文書をキャンバスに見立てて、アーティストであるあなたが熟練した開発者のような精密さで絵を描こうとしているところを想像してください。Aspose.Words を使用すると、構造化されフォーマットされたコード ブロックを使用してプログラムで文書を拡張し、専門性と明瞭さを備えた技術文書を作成できます。

## 前提条件

チュートリアルに進む前に、必要なものがすべて揃っていることを確認しましょう。

- C# の基礎知識: C# の一般的な理解は、概念を素早く理解するのに役立ちます。
-  Aspose.Words for .NET: Aspose.Words for .NET がインストールされている必要があります。まだインストールしていない場合は、入手してください。[ここ](https://releases.aspose.com/words/net/).
- 開発環境: Visual Studio または使い慣れたその他の C# IDE。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートする必要があります。これは、プロジェクトを開始する前にすべてのツールを集めるようなものです。

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

それでは、プロセスを段階的に説明してみましょう。

## ステップ1: プロジェクトの設定

Word 文書に美しくフォーマットされたコード ブロックを作成するには、まず Visual Studio で新しいプロジェクトを設定する必要があります。

1. 新しいプロジェクトを作成する: Visual Studio を開き、新しい C# コンソール アプリケーションを作成します。
2. Aspose.Words 参照の追加: NuGet パッケージ マネージャーを使用して Aspose.Words をインストールします。これを行うには、ソリューション エクスプローラーでプロジェクトを右クリックし、[NuGet パッケージの管理] を選択して、Aspose.Words を検索します。

## ステップ2: DocumentBuilderを初期化する

プロジェクトがセットアップされたので、Word 文書にコンテンツを追加するための主なツールとなる DocumentBuilder を初期化しましょう。

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## ステップ3: フェンスコードのスタイルを作成する

フェンスコードを追加するには、まずスタイルを作成する必要があります。これは、コードブロックのテーマを設定するものと考えてください。

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## ステップ4: ドキュメントにフェンスコードを追加する

スタイルの準備ができたので、フェンスで囲まれたコード ブロックをドキュメントに追加できます。

```csharp
builder.ParagraphFormat.Style = fencedCode;
builder.Writeln("This is a fenced code block");
```

## ステップ5: 情報文字列を含むフェンスコードのスタイルを作成する

場合によっては、プログラミング言語を指定したり、コード ブロックに追加情報を追加したりする必要があるかもしれません。そのためのスタイルを作成しましょう。

```csharp
Style fencedCodeWithInfo = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode.C#");
fencedCodeWithInfo.Font.Name = "Courier New";
fencedCodeWithInfo.Font.Size = 10;
fencedCodeWithInfo.ParagraphFormat.LeftIndent = 20;
fencedCodeWithInfo.ParagraphFormat.RightIndent = 20;
fencedCodeWithInfo.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## ステップ6: 情報文字列を含むフェンスコードをドキュメントに追加する

ここで、C# コードであることを示す情報文字列を含むフェンス付きコード ブロックを追加しましょう。

```csharp
builder.ParagraphFormat.Style = fencedCodeWithInfo;
builder.Writeln("This is a fenced code block with info string - C#");
```

## 結論

おめでとうございます! Aspose.Words for .NET を使用して、フェンス コード ブロックと情報文字列を含むフェンス コードを Word ドキュメントに追加しました。これは氷山の一角にすぎません。Aspose.Words を使用すると、ドキュメント処理を自動化し、新たなレベルにまで強化できます。探索を続け、コーディングを楽しんでください!

## よくある質問

### Aspose.Words for .NET とは何ですか?
Aspose.Words for .NET は、開発者がプログラムで Word 文書を作成、操作、変換できるようにする強力なライブラリです。

### Aspose.Words を他のプログラミング言語で使用できますか?
Aspose.Words は主に .NET 言語をサポートしていますが、Java、Python、その他の言語用のバージョンも用意されています。

### Aspose.Words は無料で使用できますか?
 Aspose.Wordsは商用製品ですが、無料試用版をダウンロードできます。[ここ](https://releases.aspose.com/)その特徴を探ります。

### Aspose.Words のサポートを受けるにはどうすればよいですか?
 Asposeコミュニティと開発者からサポートを受けることができます[ここ](https://forum.aspose.com/c/words/8).

### Aspose.Words には他にどのような機能がありますか?
Aspose.Words は、ドキュメント変換、テンプレートベースのドキュメント生成、レポート作成など、幅広い機能を提供します。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
