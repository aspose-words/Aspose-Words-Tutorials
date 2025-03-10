---
title: 空白を含む番号を検出する
linktitle: 空白を含む番号を検出する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用してプレーンテキスト ドキュメント内の空白を含む番号を検出し、リストが正しく認識されるようにする方法を説明します。
weight: 10
url: /ja/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 空白を含む番号を検出する

## 導入

.NET 愛好家のための Aspose.Words! 今日は、プレーンテキスト ドキュメント内のリストを簡単に処理できる魅力的な機能を紹介します。テキスト ファイルの行の一部がリストであるはずなのに、Word ドキュメントに読み込んだときに正しく表示されないという経験をしたことはありませんか? 私たちには、空白文字を含む番号を検出するという巧妙なトリックがあります。このチュートリアルでは、`DetectNumberingWithWhitespaces` Aspose.Words for .NET のオプションを使用すると、数字とテキストの間に空白がある場合でも、リストが正しく認識されるようになります。

## 前提条件

始める前に、以下のものを用意してください。

-  Aspose.Words for .NET: ダウンロードはこちらから[Aspose リリース](https://releases.aspose.com/words/net/)ページ。
- 開発環境: Visual Studio またはその他の C# IDE。
- .NET Framework がマシンにインストールされています。
- C# の基礎知識: 基礎を理解すると、例を理解しやすくなります。

## 名前空間のインポート

コードに進む前に、プロジェクトに必要な名前空間がインポートされていることを確認してください。開始するための簡単なスニペットを次に示します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

プロセスをシンプルで管理しやすいステップに分解してみましょう。各ステップでは、必要なコードを説明し、何が起こっているかを説明します。

## ステップ1: ドキュメントディレクトリを定義する

まず最初に、ドキュメント ディレクトリへのパスを設定しましょう。ここに入力ファイルと出力ファイルが保存されます。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ステップ2: プレーンテキスト文書を作成する

次に、プレーンテキスト ドキュメントを文字列として作成します。このドキュメントには、リストとして解釈できる部分が含まれます。

```csharp
const string textDoc = "Full stop delimiters:\n" +
                       "1. First list item 1\n" +
                       "2. First list item 2\n" +
                       "3. First list item 3\n\n" +
                       "Right bracket delimiters:\n" +
                       "1) Second list item 1\n" +
                       "2) Second list item 2\n" +
                       "3) Second list item 3\n\n" +
                       "Bullet delimiters:\n" +
                       "• Third list item 1\n" +
                       "• Third list item 2\n" +
                       "• Third list item 3\n\n" +
                       "Whitespace delimiters:\n" +
                       "1 Fourth list item 1\n" +
                       "2 Fourth list item 2\n" +
                       "3 Fourth list item 3";
```

## ステップ3: LoadOptionsを構成する

空白を含む番号を検出するには、`DetectNumberingWithWhitespaces`オプション`true`で`TxtLoadOptions`物体。

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## ステップ4: ドキュメントを読み込む

さて、ドキュメントをロードしてみましょう。`TxtLoadOptions`パラメータとして。これにより、4 番目のリスト (空白を含む) が正しく検出されるようになります。

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## ステップ5: ドキュメントを保存する

最後に、指定したディレクトリにドキュメントを保存します。これにより、正しく検出されたリストを含む Word ドキュメントが出力されます。

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## 結論

これで完了です。わずか数行のコードで、Aspose.Words for .NET を使用してプレーンテキスト ドキュメント内の空白を含む番号を検出する技術を習得しました。この機能は、さまざまなテキスト形式を扱い、リストが Word ドキュメントで正確に表現されるようにする場合に非常に便利です。次に扱いにくいリストに遭遇したときには、何をすべきか正確にわかるでしょう。

## よくある質問

### 何ですか`DetectNumberingWithWhitespaces` in Aspose.Words for .NET?
`DetectNumberingWithWhitespaces`はオプションです`TxtLoadOptions`これにより、番号とリスト項目のテキストの間に空白がある場合でも、Aspose.Words はリストを認識できるようになります。

### この機能を箇条書きや括弧などの他の区切り文字にも使用できますか?
はい、Aspose.Wordsは箇条書きや括弧などの一般的な区切り文字を含むリストを自動的に検出します。`DetectNumberingWithWhitespaces`特に空白のあるリストに役立ちます。

### 使わないとどうなるのか`DetectNumberingWithWhitespaces`?
このオプションがないと、番号とテキストの間に空白があるリストはリストとして認識されず、項目が単純な段落として表示されてしまう可能性があります。

### この機能は他の Aspose 製品でも利用できますか?
この特定の機能は、Word ドキュメントの処理を処理するように設計された Aspose.Words for .NET 向けにカスタマイズされています。

### Aspose.Words for .NET の一時ライセンスを取得するにはどうすればよいですか?
臨時免許証は、[Aspose 一時ライセンス](https://purchase.aspose.com/temporary-license/)ページ。


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
