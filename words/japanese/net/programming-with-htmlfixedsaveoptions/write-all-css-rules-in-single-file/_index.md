---
title: すべての CSS ルールを 1 つのファイルに記述する
linktitle: すべての CSS ルールを 1 つのファイルに記述する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word 文書を HTML に変換する方法を学びます。すべての CSS ルールが 1 つのファイルにまとめられ、コードがよりクリーンになり、メンテナンスが容易になります。
weight: 10
url: /ja/net/programming-with-htmlfixedsaveoptions/write-all-css-rules-in-single-file/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# すべての CSS ルールを 1 つのファイルに記述する

## 導入

Word 文書を HTML に変換するときに、あちこちに散らばった CSS ルールの網に巻き込まれたことはありませんか? 心配しないでください! 今日は、すべての CSS ルールを 1 つのファイルに記述できる Aspose.Words for .NET の優れた機能について詳しく説明します。これにより、コードが整理されるだけでなく、作業がずっと簡単になります。シートベルトを締めて、よりクリーンで効率的な HTML 出力への旅を始めましょう!

## 前提条件

細かい点に入る前に、準備を整えましょう。始めるために必要なものは次のとおりです。

1.  Aspose.Words for .NET: Aspose.Words for .NETライブラリがインストールされていることを確認してください。まだインストールされていない場合は、[ここからダウンロード](https://releases.aspose.com/words/net/).
2. .NET 開発環境: マシンに .NET 開発環境をセットアップする必要があります。Visual Studio が一般的な選択肢です。
3. C# の基礎知識: C# プログラミングの基本的な理解が役立ちます。
4. Word 文書: 変換する Word 文書 (.docx) を用意します。

## 名前空間のインポート

まず最初に、C# プロジェクトに必要な名前空間をインポートしましょう。これにより、Aspose.Words の機能に簡単にアクセスできるようになります。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

では、プロセスをわかりやすいステップに分解してみましょう。各ステップでは、すべてがスムーズに実行されるように、プロセスの特定の部分をガイドします。

## ステップ1: ドキュメントディレクトリを設定する

まず、ドキュメント ディレクトリへのパスを定義する必要があります。これは、Word ドキュメントが保存される場所であり、変換された HTML が保存される場所です。

```csharp
//ドキュメントディレクトリへのアクセスパス
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## ステップ2: Word文書を読み込む

次に、HTMLに変換したいWord文書を読み込みます。これは、`Document` Aspose.Words ライブラリのクラス。

```csharp
// Word文書を読み込む
Document doc = new Document(dataDir + "Document.docx");
```

## ステップ3: HTML保存オプションを設定する

次に、HTML保存オプションを設定する必要があります。具体的には、すべてのCSSルールを1つのファイルに書き込む機能を有効にします。これは、`SaveFontFaceCssSeparately`財産に`false`.

```csharp
// 「すべての CSS ルールを 1 つのファイルに書き込む」機能を使用してバックアップ オプションを構成する
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions 
{ 
    SaveFontFaceCssSeparately = false 
};
```

## ステップ4: ドキュメントを固定HTMLに変換する

最後に、設定された保存オプションを使用して、ドキュメントを HTML ファイルとして保存します。この手順により、すべての CSS ルールが 1 つのファイルに書き込まれるようになります。

```csharp
//ドキュメントを固定HTMLに変換する
doc.Save(dataDir + "WorkingWithHtmlFixedSaveOptions.WriteAllCssRulesInSingleFile.html", saveOptions);
```

## 結論

これで完了です。わずか数行のコードで、すべての CSS ルールが 1 つのファイルに整理された状態で、Word 文書を HTML に変換できました。この方法により、CSS 管理が簡素化されるだけでなく、HTML 文書の保守性も向上します。次に Word 文書の変換を任されたときには、整理された状態を保つ方法を正確に把握できます。

## よくある質問

### HTML 出力に単一の CSS ファイルを使用する必要があるのはなぜですか?
単一の CSS ファイルを使用すると、スタイルの管理とメンテナンスが簡素化されます。HTML がよりクリーンで効率的になります。

### 必要に応じてフォント フェイスの CSS ルールを分離できますか?
はい、設定することで`SaveFontFaceCssSeparately`に`true`フォント フェイスの CSS ルールを別のファイルに分離できます。

### Aspose.Words for .NET は無料で使用できますか?
 Aspose.Wordsは無料トライアルを提供しており、[ここからダウンロード](https://releases.aspose.com/)継続して使用する場合は、ライセンスの購入を検討してください[ここ](https://purchase.aspose.com/buy).

### Aspose.Words for .NET は他にどのような形式に変換できますか?
Aspose.Words for .NET は、PDF、TXT、JPEG や PNG などの画像形式を含むさまざまな形式をサポートしています。

### Aspose.Words for .NET に関するその他のリソースはどこで見つかりますか?
チェックしてください[ドキュメント](https://reference.aspose.com/words/net/)包括的なガイドと API リファレンスについては、こちらをご覧ください。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
