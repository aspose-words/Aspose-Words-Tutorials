---
title: チェックDrawingMLテキスト効果
linktitle: チェックDrawingMLテキスト効果
second_title: Aspose.Words ドキュメント処理 API
description: 詳細なステップバイステップ ガイドを使用して、Aspose.Words for .NET を使用して Word 文書で DrawingML テキスト効果を確認する方法を学びます。文書を簡単に強化できます。
weight: 10
url: /ja/net/working-with-fonts/check-drawingml-text-effect/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# チェックDrawingMLテキスト効果

## 導入

Aspose.Words for .NET の操作に関する詳細なチュートリアルへようこそ。今日は、DrawingML テキスト効果の魅力的な世界に飛び込みます。Word 文書に影、反射、3D 効果を追加したい場合、このガイドでは、Aspose.Words for .NET を使用して文書内のこれらのテキスト効果を確認する方法を説明します。さあ、始めましょう。

## 前提条件

チュートリアルに進む前に、いくつかの前提条件を満たす必要があります。

-  Aspose.Words for .NET ライブラリ: Aspose.Words for .NET ライブラリがインストールされていることを確認してください。[Aspose リリース ページ](https://releases.aspose.com/words/net/).
- 開発環境: Visual Studio などの開発環境をセットアップする必要があります。
- C# の基礎知識: C# プログラミングに関するある程度の知識があると役立ちます。

## 名前空間のインポート

まず、必要な名前空間をインポートする必要があります。これらの名前空間により、Word 文書を操作し、DrawingML テキスト効果をチェックするために必要なクラスとメソッドにアクセスできるようになります。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## DrawingML テキスト効果をチェックするためのステップバイステップガイド

ここで、プロセスを複数のステップに分割して、わかりやすく説明します。

## ステップ1: ドキュメントを読み込む

最初のステップは、DrawingML テキスト効果を確認する Word 文書を読み込むことです。 

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "DrawingML text effects.docx");
```

このコード スニペットは、指定されたディレクトリから「DrawingML text effects.docx」という名前のドキュメントを読み込みます。

## ステップ2: 実行コレクションにアクセスする

次に、ドキュメントの最初の段落にある実行のコレクションにアクセスする必要があります。実行とは、同じ書式のテキストの部分です。

```csharp
RunCollection runs = doc.FirstSection.Body.FirstParagraph.Runs;
```

このコード行は、ドキュメントの最初のセクションの最初の段落から実行を取得します。

## ステップ3: 最初の実行のフォントを取得する

ここで、runs コレクションの最初の run のフォント プロパティを取得します。これにより、テキストに適用されたさまざまな DrawingML テキスト効果を確認できます。

```csharp
Font runFont = runs[0].Font;
```

## ステップ4: DrawingMLテキスト効果を確認する

最後に、影、3D 効果、反射、アウトライン、塗りつぶしなどのさまざまな DrawingML テキスト効果を確認できます。

```csharp
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Shadow));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Effect3D));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Reflection));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Outline));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Fill));
```

これらのコード行は次のように出力されます`true`または`false`各特定の DrawingML テキスト効果が実行のフォントに適用されているかどうかによって異なります。

## 結論

おめでとうございます! Aspose.Words for .NET を使用して Word 文書内の DrawingML テキスト効果を確認する方法を学習しました。この強力な機能により、高度なテキスト書式をプログラムで検出および操作できるようになり、文書処理タスクをより細かく制御できるようになります。


## よくある質問

### DrawingML テキスト効果とは何ですか?
DrawingML テキスト効果は、影、3D 効果、反射、アウトライン、塗りつぶしなど、Word 文書の高度なテキスト書式設定オプションです。

### Aspose.Words for .NET を使用して DrawingML テキスト効果を適用できますか?
はい、Aspose.Words for .NET を使用すると、DrawingML テキスト効果をプログラムで確認して適用できます。

### Aspose.Words for .NET を使用するにはライセンスが必要ですか?
はい、Aspose.Words for .NETの全機能を使用するにはライセンスが必要です。[一時ライセンス](https://purchase.aspose.com/temporary-license/)評価のため。

### Aspose.Words for .NET の無料試用版はありますか?
はい、ダウンロードできます[無料トライアル](https://releases.aspose.com/)購入前に Aspose.Words for .NET を試用できます。

### Aspose.Words for .NET に関する詳細なドキュメントはどこで入手できますか?
詳細なドキュメントは[Aspose.Words for .NET ドキュメント ページ](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
