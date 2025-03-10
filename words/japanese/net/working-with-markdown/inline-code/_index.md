---
title: インラインコード
linktitle: インラインコード
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word 文書にインライン コード スタイルを適用する方法を学びます。このチュートリアルでは、コード フォーマット用の単一および複数のバックティックについて説明します。
weight: 10
url: /ja/net/working-with-markdown/inline-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# インラインコード

## 導入

Word ドキュメントをプログラムで生成または操作する場合、テキストをコードに似せてフォーマットする必要があるかもしれません。ドキュメント用でもレポートのコード スニペット用でも、Aspose.Words for .NET はテキスト スタイルを処理するための堅牢な方法を提供します。このチュートリアルでは、Aspose.Words を使用してテキストにインライン コード スタイルを適用する方法に焦点を当てます。単一または複数のバックティックのカスタム スタイルを定義して使用し、ドキュメント内でコード セグメントをはっきりと目立たせる方法を説明します。

## 前提条件

始める前に、以下のものを用意してください。

1.  Aspose.Words for .NET ライブラリ: .NET 環境に Aspose.Words がインストールされていることを確認してください。ダウンロードは、[Aspose.Words for .NET リリース ページ](https://releases.aspose.com/words/net/).

2. .NET プログラミングの基礎知識: このガイドでは、C# および .NET プログラミングの基礎を理解していることを前提としています。

3. 開発環境: C# コードを記述して実行できる Visual Studio などの .NET 開発環境をセットアップする必要があります。

## 名前空間のインポート

プロジェクトで Aspose.Words を使い始めるには、必要な名前空間をインポートする必要があります。手順は次のとおりです。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

プロセスを明確なステップに分解してみましょう。

## ステップ 1: ドキュメントと DocumentBuilder を初期化する

まず、新しいドキュメントを作成し、`DocumentBuilder`インスタンス。`DocumentBuilder`このクラスは、Word 文書にコンテンツを追加して書式設定するのに役立ちます。

```csharp
//新しいドキュメントで DocumentBuilder を初期化します。
DocumentBuilder builder = new DocumentBuilder();
```

## ステップ2: バックティック1つでインラインコードスタイルを追加する

このステップでは、単一のバックティックを使用してインライン コードのスタイルを定義します。このスタイルは、テキストをインライン コードのように見えるようにフォーマットします。

### スタイルを定義する

```csharp
// つのバックティックを使用して、インライン コードの新しい文字スタイルを定義します。
Style inlineCode1BackTicks = builder.Document.Styles.Add(StyleType.Character, "InlineCode");
inlineCode1BackTicks.Font.Name = "Courier New"; //コード用の典型的なフォント。
inlineCode1BackTicks.Font.Size = 10.5; //インライン コードのフォント サイズ。
inlineCode1BackTicks.Font.Color = System.Drawing.Color.Blue; //コードテキストの色。
inlineCode1BackTicks.Font.Bold = true; //コードテキストを太字にします。
```

### スタイルを適用する

これで、このスタイルをドキュメント内のテキストに適用できます。

```csharp
// DocumentBuilder を使用して、インライン コード スタイルでテキストを挿入します。
builder.Font.Style = inlineCode1BackTicks;
builder.Writeln("Text with InlineCode style with 1 backtick");
```

## ステップ3: 3つのバックティックでインラインコードスタイルを追加する

次に、複数行のコード ブロックで通常使用される、3 つのバックティックを含むインライン コードのスタイルを定義します。

### スタイルを定義する

```csharp
// 3 つのバックティックを含むインライン コードの新しい文字スタイルを定義します。
Style inlineCode3BackTicks = builder.Document.Styles.Add(StyleType.Character, "InlineCode.3");
inlineCode3BackTicks.Font.Name = "Courier New"; //コードに一貫したフォントを使用します。
inlineCode3BackTicks.Font.Size = 10.5; //コード ブロックのフォント サイズ。
inlineCode3BackTicks.Font.Color = System.Drawing.Color.Green; //視認性を高めるために色を変えました。
inlineCode3BackTicks.Font.Bold = true; //強調する場合は太字にします。
```

### スタイルを適用する

このスタイルをテキストに適用すると、複数行のコード ブロックとしてフォーマットされます。

```csharp
//コード ブロックにスタイルを適用します。
builder.Font.Style = inlineCode3BackTicks;
builder.Writeln("Text with InlineCode style with 3 backticks");
```

## 結論

Aspose.Words for .NET を使用して Word 文書内のテキストをインライン コードとして書式設定するのは、手順がわかれば簡単です。1 つまたは複数のバックティックを使用してカスタム スタイルを定義して適用することで、コード スニペットを目立たせることができます。この方法は、技術文書やコードの読みやすさが重要な文書に特に役立ちます。

さまざまなスタイルや書式設定オプションを自由に試して、ニーズに最適なものを見つけてください。Aspose.Words は柔軟性に富んでいるため、ドキュメントの外観を自由にカスタマイズできます。

## よくある質問

### インライン コード スタイルに異なるフォントを使用できますか?
はい、ニーズに合ったフォントであればどれでも使用できます。「Courier New」などのフォントは、等幅フォントであるため、通常はコードに使用されます。

### インライン コード テキストの色を変更するにはどうすればよいですか?
色を変更するには、`Font.Color`スタイルのプロパティは`System.Drawing.Color`.

### 同じテキストに複数のスタイルを適用できますか?
Aspose.Words では、一度に適用できるスタイルは 1 つだけです。スタイルを組み合わせる必要がある場合は、必要な書式設定をすべて組み込んだ新しいスタイルを作成することを検討してください。

### ドキュメント内の既存のテキストにスタイルを適用するにはどうすればよいですか?
既存のテキストにスタイルを適用するには、まずテキストを選択し、`Font.Style`財産。

### Aspose.Words を他のドキュメント形式で使用できますか?
Aspose.Words は Word 文書専用に設計されています。他の形式の場合は、別のライブラリを使用するか、文書を互換性のある形式に変換する必要があります。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
