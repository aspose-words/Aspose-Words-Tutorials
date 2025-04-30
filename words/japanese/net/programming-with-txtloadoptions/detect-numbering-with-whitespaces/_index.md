---
"description": "Aspose.Words for .NET を使用してプレーンテキスト ドキュメント内の空白を含む番号を検出し、リストが正しく認識されることを確認する方法について説明します。"
"linktitle": "空白を含む番号の検出"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "空白を含む番号の検出"
"url": "/ja/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 空白を含む番号の検出

## 導入

.NET愛好家のためのAspose.Words！本日は、プレーンテキスト文書内のリスト処理を非常に簡単にする魅力的な機能をご紹介します。テキストファイルで、リストとして扱うべき行があるのに、Word文書に読み込むと見た目がおかしくなってしまうという経験はありませんか？そんな時に役立つ便利な機能があります。それは、空白文字を含む番号の検出です。このチュートリアルでは、 `DetectNumberingWithWhitespaces` Aspose.Words for .NET のオプションを使用すると、数字とテキストの間に空白があっても、リストが正しく認識されます。

## 前提条件

始める前に、次のものを用意してください。

- Aspose.Words for .NET: ダウンロードはこちらから [Aspose リリース](https://releases.aspose.com/words/net/) ページ。
- 開発環境: Visual Studio またはその他の C# IDE。
- .NET Framework がマシンにインストールされています。
- C# の基本知識: 基本を理解すると、例を理解するのに役立ちます。

## 名前空間のインポート

コードに進む前に、プロジェクトに必要な名前空間がインポートされていることを確認してください。簡単なコード例を以下に示します。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

プロセスをシンプルで扱いやすいステップに分解してみましょう。各ステップでは、必要なコードと、何が起こっているかを説明します。

## ステップ1: ドキュメントディレクトリを定義する

まず最初に、ドキュメントディレクトリへのパスを設定しましょう。ここに入力ファイルと出力ファイルが保存されます。

```csharp
// ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ステップ2: プレーンテキスト文書を作成する

次に、文字列としてプレーンテキスト文書を作成します。この文書には、リストとして解釈できる部分が含まれます。

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

空白を含む番号を検出するには、 `DetectNumberingWithWhitespaces` オプション `true` で `TxtLoadOptions` 物体。

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## ステップ4: ドキュメントを読み込む

さて、ドキュメントをロードしてみましょう。 `TxtLoadOptions` パラメータとして指定します。これにより、4番目のリスト（空白を含む）が正しく検出されます。

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## ステップ5: ドキュメントを保存する

最後に、指定したディレクトリにドキュメントを保存します。これにより、正しく検出されたリストを含むWord文書が出力されます。

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## 結論

これで完了です！わずか数行のコードで、Aspose.Words for .NET を使ってプレーンテキスト文書内の空白を含む番号を検出する技術を習得できました。この機能は、様々なテキスト形式を扱う際に非常に便利で、Word 文書内でリストが正確に表示されるようにすることができます。これで、次に扱いにくいリストに遭遇した時、どうすればいいのかが正確に分かるでしょう。

## よくある質問

### 何ですか `DetectNumberingWithWhitespaces` Aspose.Words for .NET では?
`DetectNumberingWithWhitespaces` はオプションです `TxtLoadOptions` これにより、番号とリスト項目のテキストの間に空白があっても、Aspose.Words がリストを認識できるようになります。

### この機能を箇条書きや括弧などの他の区切り文字にも使用できますか?
はい、Aspose.Wordsは箇条書きや括弧などの一般的な区切り文字を含むリストを自動的に検出します。 `DetectNumberingWithWhitespaces` 特に空白のあるリストに役立ちます。

### 使わないとどうなるのか `DetectNumberingWithWhitespaces`？
このオプションを指定しないと、番号とテキストの間に空白があるリストはリストとして認識されず、項目が単純な段落として表示されてしまう可能性があります。

### この機能は他の Aspose 製品でも利用できますか?
この特定の機能は、Word ドキュメントの処理に対応するように設計された Aspose.Words for .NET 向けにカスタマイズされています。

### Aspose.Words for .NET の一時ライセンスを取得するにはどうすればよいですか?
臨時免許証は、 [Aspose 一時ライセンス](https://purchase.aspose.com/temporary-license/) ページ。




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}