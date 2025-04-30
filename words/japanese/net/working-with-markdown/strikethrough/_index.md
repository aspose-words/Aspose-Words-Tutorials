---
"description": "Aspose.Words for .NET を使用してテキストに取り消し線を適用する方法を、ステップバイステップガイドで学習しましょう。ドキュメント処理スキルを向上させましょう。"
"linktitle": "取り消し線"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "取り消し線"
"url": "/ja/net/working-with-markdown/strikethrough/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 取り消し線

## 導入

Aspose.Words for .NET を使ってテキストに取り消し線を適用する方法を詳しく説明したガイドへようこそ。ドキュメント処理スキルを向上させ、テキストに個性的なタッチを加えたいとお考えなら、まさにうってつけのガイドです。さあ、始めましょう！

## 前提条件

始める前に、次のものを用意してください。

- Aspose.Words for .NET: ダウンロード [ここ](https://releases。aspose.com/words/net/).
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

その `DocumentBuilder` クラスは、Aspose.Words の強力なツールであり、ドキュメントにコンテンツを簡単に追加できます。

```csharp
// DocumentBuilder を初期化します。
DocumentBuilder builder = new DocumentBuilder();
```

## ステップ2: 取り消し線プロパティを設定する

それでは、テキストに取り消し線プロパティを適用してみましょう。これは、 `StrikeThrough` の財産 `Font` 反対する `true`。

```csharp
// テキストに取り消し線を付けます。
builder.Font.StrikeThrough = true;
```

## ステップ3：取り消し線付きのテキストを書く

取り消し線プロパティを設定したら、テキストを追加できます。 `Writeln` メソッドはドキュメントにテキストを追加します。

```csharp
// 取り消し線付きのテキストを書き込みます。
builder.Writeln("This text will be StrikeThrough");
```

## 結論

これで完了です！Aspose.Words for .NET を使って、テキストに取り消し線書式を追加できました。この強力なライブラリは、ドキュメント処理とカスタマイズの可能性を無限に広げます。レポート、レター、その他あらゆる種類のドキュメントを作成する場合でも、これらの機能をマスターすれば、生産性と出力品質が間違いなく向上します。

## よくある質問

### Aspose.Words for .NET とは何ですか?
Aspose.Words for .NET は、開発者がプログラムによって Word 文書を作成、操作、変換できるようにする強力なドキュメント処理ライブラリです。

### Aspose.Words for .NET を商用プロジェクトで使用できますか?
はい、Aspose.Words for .NETは商用プロジェクトでもご利用いただけます。購入オプションについては、 [購入ページ](https://purchase。aspose.com/buy).

### Aspose.Words for .NET の無料試用版はありますか?
はい、無料トライアルをダウンロードできます [ここ](https://releases。aspose.com/).

### Aspose.Words for .NET のサポートを受けるにはどうすればよいですか?
Asposeコミュニティと専門家からのサポートを受けることができます。 [サポートフォーラム](https://forum。aspose.com/c/words/8).

### Aspose.Words for .NET を使用して他のテキスト書式設定オプションを適用できますか?
もちろんです! Aspose.Words for .NET は、太字、斜体、下線など、幅広いテキスト書式設定オプションをサポートしています。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}