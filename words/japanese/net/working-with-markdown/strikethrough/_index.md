---
title: 取り消し線
linktitle: 取り消し線
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用してテキストに取り消し線書式を適用する方法をステップバイステップ ガイドで学習します。ドキュメント処理スキルを強化します。
weight: 10
url: /ja/net/working-with-markdown/strikethrough/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 取り消し線

## 導入

Aspose.Words for .NET を使用してテキストに取り消し線書式を適用する方法について詳しく説明したガイドへようこそ。ドキュメント処理スキルを強化し、テキストに独自のタッチを追加したい場合は、ここが最適な場所です。さっそく始めましょう。

## 前提条件

始める前に、以下のものを用意してください。

-  Aspose.Words for .NET: ダウンロード[ここ](https://releases.aspose.com/words/net/).
- .NET Framework: システムに .NET Framework がインストールされていることを確認してください。
- 開発環境: Visual Studio のような IDE。
- C# の基礎知識: C# プログラミングに精通している必要があります。

## 名前空間のインポート

まず、必要な名前空間をインポートする必要があります。これらは、Aspose.Words ライブラリとその機能にアクセスするために不可欠です。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ1: DocumentBuilderを初期化する

の`DocumentBuilder`クラスは、Aspose.Words の強力なツールであり、ドキュメントにコンテンツを簡単に追加できます。

```csharp
// DocumentBuilder を初期化します。
DocumentBuilder builder = new DocumentBuilder();
```

## ステップ2: 取り消し線プロパティを設定する

さて、テキストに取り消し線プロパティを適用してみましょう。これは、`StrikeThrough`の財産`Font`反対する`true`.

```csharp
//テキストに取り消し線を付けます。
builder.Font.StrikeThrough = true;
```

## ステップ3: 取り消し線付きのテキストを書く

取り消し線プロパティを設定したら、テキストを追加できます。`Writeln`メソッドはテキストをドキュメントに追加します。

```csharp
//取り消し線付きのテキストを書き込みます。
builder.Writeln("This text will be StrikeThrough");
```

## 結論

これで完了です。Aspose.Words for .NET を使用して、テキストに取り消し線の書式設定を正常に追加できました。この強力なライブラリにより、ドキュメントの処理とカスタマイズの可能性が広がります。レポート、レター、その他の種類のドキュメントを作成する場合でも、これらの機能を習得すれば、生産性と出力の品質が間違いなく向上します。

## よくある質問

### Aspose.Words for .NET とは何ですか?
Aspose.Words for .NET は、開発者がプログラムで Word ドキュメントを作成、操作、変換できるようにする強力なドキュメント処理ライブラリです。

### Aspose.Words for .NET を商用プロジェクトで使用できますか?
はい、Aspose.Words for .NETは商用プロジェクトでもご利用いただけます。購入オプションについては、[購入ページ](https://purchase.aspose.com/buy).

### Aspose.Words for .NET の無料試用版はありますか?
はい、無料トライアルをダウンロードできます[ここ](https://releases.aspose.com/).

### Aspose.Words for .NET のサポートを受けるにはどうすればよいですか?
Asposeコミュニティと専門家からのサポートを受けることができます。[サポートフォーラム](https://forum.aspose.com/c/words/8).

### Aspose.Words for .NET を使用して他のテキスト書式設定オプションを適用できますか?
もちろんです! Aspose.Words for .NET は、太字、斜体、下線など、幅広いテキスト書式設定オプションをサポートしています。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
