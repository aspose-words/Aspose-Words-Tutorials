---
title: ハイフネーションコールバック
linktitle: ハイフネーションコールバック
second_title: Aspose.Words ドキュメント処理 API
description: この包括的なステップバイステップ ガイドを使用して、Aspose.Words for .NET でハイフネーション コールバックを実装し、ドキュメントの書式設定を強化する方法を学習します。
weight: 10
url: /ja/net/working-with-hyphenation/hyphenation-callback/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ハイフネーションコールバック


## 導入

こんにちは。特にハイフネーションが必要な言語を扱うときに、テキストの書式設定の複雑さに巻き込まれたことはありませんか? あなただけではありません。ハイフネーションは、適切なテキスト レイアウトに不可欠ですが、少々面倒なこともあります。しかし、どうでしょう? Aspose.Words for .NET が役に立ちます。この強力なライブラリを使用すると、コールバック メカニズムによるハイフネーションの処理を含め、テキストの書式設定をシームレスに管理できます。興味が湧きましたか? Aspose.Words for .NET を使用してハイフネーション コールバックを実装する方法の詳細を詳しく見ていきましょう。

## 前提条件

コードに取り掛かる前に、必要なものがすべて揃っていることを確認しましょう。

1. Aspose.Words for .NET: ライブラリがあることを確認してください。[ここからダウンロード](https://releases.aspose.com/words/net/).
2. IDE: Visual Studio のような開発環境。
3. C# の基礎知識: C# と .NET フレームワークの理解。
4. ハイフネーション辞書: 使用する予定の言語のハイフネーション辞書。
5.  Asposeライセンス: 有効なAsposeライセンス。[一時ライセンス](https://purchase.aspose.com/temporary-license/)持っていない場合は。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートしましょう。これにより、コードは Aspose.Words から必要なすべてのクラスとメソッドにアクセスできるようになります。

```csharp
using Aspose.Words;
using System;
using System.IO;
```

## ステップ1: ハイフネーションコールバックを登録する

まず、ハイフネーション コールバックを登録する必要があります。ここで、Aspose.Words にカスタム ハイフネーション ロジックを使用するように指示します。

```csharp
try
{
    //ハイフネーションコールバックを登録します。
    Hyphenation.Callback = new CustomHyphenationCallback();
}
catch (Exception e)
{
    Console.WriteLine($"Error registering hyphenation callback: {e.Message}");
}
```

ここでは、カスタムコールバックのインスタンスを作成し、それを`Hyphenation.Callback`.

## ステップ2: ドキュメントパスを定義する

次に、ドキュメントが保存されるディレクトリを定義する必要があります。このパスからドキュメントを読み込み、保存するため、これは非常に重要です。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する`"YOUR DOCUMENT DIRECTORY"`ドキュメントへの実際のパスを入力します。

## ステップ3: ドキュメントを読み込む

それでは、ハイフネーションが必要なドキュメントを読み込んでみましょう。

```csharp
Document document = new Document(dataDir + "German text.docx");
```

ここではドイツ語のテキスト文書を読み込んでいます。`"German text.docx"`ドキュメントのファイル名に置き換えます。

## ステップ4: ドキュメントを保存する

ドキュメントを読み込んだ後、そのプロセスでハイフネーション コールバックを適用して新しいファイルに保存します。

```csharp
document.Save(dataDir + "TreatmentByCesureWithRecall.pdf");
```

この行は、ハイフネーションを適用した PDF としてドキュメントを保存します。

## ステップ5: ハイフネーション辞書の例外処理

場合によっては、ハイフネーション辞書が見つからないという問題が発生することがあります。その場合は対処しましょう。

```csharp
catch (Exception e) when (e.Message.StartsWith("Missing hyphenation dictionary"))
{
    Console.WriteLine(e.Message);
}
finally
{
    Hyphenation.Callback = null;
}
```

このブロックでは、辞書の不足に関連する特定の例外をキャッチし、メッセージを出力します。

## ステップ6: カスタムハイフネーションコールバッククラスを実装する

さて、実装してみましょう`CustomHyphenationCallback`ハイフネーション辞書の要求を処理するクラス。

```csharp
public class CustomHyphenationCallback : IHyphenationCallback
{
    public void RequestDictionary(string language)
    {
        string dictionaryFolder = MyDir;
        string dictionaryFullFileName;
        switch (language)
        {
            case "en-US":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_en_US.dic");
                break;
            case "de-CH":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_de_CH.dic");
                break;
            default:
                throw new Exception($"Missing hyphenation dictionary for {language}.");
        }
        //要求された言語の辞書を登録します。
        Hyphenation.RegisterDictionary(language, dictionaryFullFileName);
    }
}
```

このクラスでは、`RequestDictionary`このメソッドはハイフネーション辞書が必要なときに呼び出されます。言語をチェックし、適切な辞書を登録します。

## 結論

これで完了です。Aspose.Words for .NET でハイフネーション コールバックを実装する方法を学習しました。これらの手順に従うことで、言語に関係なく、ドキュメントが美しくフォーマットされることを保証できます。英語、ドイツ語、またはその他の言語を扱う場合でも、この方法を使用すると、ハイフネーションを簡単に処理できます。

## よくある質問

### Aspose.Words for .NET とは何ですか?
Aspose.Words for .NET は、開発者がプログラムによってドキュメントを作成、変更、変換できるようにする強力なドキュメント操作ライブラリです。

### ドキュメントの書式設定においてハイフネーションが重要なのはなぜですか?
ハイフネーションにより、適切な場所で単語が区切られるため、テキストのレイアウトが改善され、より読みやすく視覚的に魅力的なドキュメントが実現します。

### Aspose.Words を無料で使用できますか?
 Aspose.Wordsは無料トライアルを提供しています。[ここ](https://releases.aspose.com/).

### ハイフネーション辞書を入手するにはどうすればよいですか?
さまざまなオンライン リソースからハイフネーション辞書をダウンロードしたり、必要に応じて独自の辞書を作成したりできます。

### ハイフネーション辞書がない場合はどうなりますか?
辞書がない場合は、`RequestDictionary`メソッドは例外をスローします。これを処理してユーザーに通知したり、フォールバックを提供したりできます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
