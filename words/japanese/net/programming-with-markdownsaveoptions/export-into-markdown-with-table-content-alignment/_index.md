---
"description": "Aspose.Words for .NET を使用して、整列した表を含むWord文書をMarkdown形式にエクスポートする方法を学びましょう。完璧なMarkdown表を作成するには、ステップバイステップガイドに従ってください。"
"linktitle": "表のコンテンツの位置揃えでMarkdownにエクスポート"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "表のコンテンツの位置揃えでMarkdownにエクスポート"
"url": "/ja/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 表のコンテンツの位置揃えでMarkdownにエクスポート

## 導入

こんにちは！Word文書をMarkdown形式にエクスポートする際に、表が完璧に整列した状態でエクスポートしたいと思ったことはありませんか？ドキュメント作成に携わる開発者の方にも、Markdownを愛用している方にも、このガイドはきっとお役に立ちます。Aspose.Words for .NETを使って、この作業を実現する方法について詳しく解説します。Wordの表をMarkdown形式に整列させたいですか？さあ、始めましょう！

## 前提条件

コードに進む前に、準備しておく必要があるものがいくつかあります。

1. Aspose.Words for .NET ライブラリ: Aspose.Words for .NET ライブラリがインストールされていることを確認してください。以下のリンクからダウンロードできます。 [Aspose リリースページ](https://releases。aspose.com/words/net/).
2. 開発環境：開発環境を設定します。Visual Studio は .NET 開発でよく使用されます。
3. C# の基礎知識: この言語でコードを記述するため、C# を理解することは不可欠です。
4. サンプル Word 文書: テストに使用できる Word 文書を用意します。

## 名前空間のインポート

コーディングを始める前に、必要な名前空間をインポートしましょう。これにより、使用するAspose.Wordsのクラスとメソッドにアクセスできるようになります。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ1: DocumentとDocumentBuilderを初期化する

まず最初に、新しいWord文書を作成し、 `DocumentBuilder` オブジェクトを使用してドキュメントの構築を開始します。

```csharp
// ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";

// 新しいドキュメントを作成します。
Document doc = new Document();

// DocumentBuilder を初期化します。
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ステップ2: セルを挿入してコンテンツを配置する

次に、ドキュメントにセルをいくつか挿入し、配置を設定します。これは、Markdownエクスポートで正しい配置が維持されるようにするために重要です。

```csharp
// セルを挿入し、右揃えに設定します。
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// 別のセルを挿入し、配置を中央に設定します。
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## ステップ3: Markdownエクスポートの表コンテンツの配置を設定する

さて、設定してみましょう `MarkdownSaveOptions` エクスポートされたMarkdownファイル内の表の内容の配置を制御します。どのように機能するかを確認するために、異なる配置設定でドキュメントを保存してみましょう。

```csharp
// MarkdownSaveOptions オブジェクトを作成します。
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// ドキュメントを左揃えで保存します。
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// 配置を右に変更して保存します。
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// 配置を中央に変更して保存します。
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## ステップ4: 表のコンテンツの自動配置を使用する

その `Auto` 配置オプションは、対応する表の列の最初の段落の配置を取得します。これは、1つの表に複数の配置が混在している場合に便利です。

```csharp
// 配置を自動に設定します。
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// ドキュメントを自動配置して保存します。
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## 結論

これで完了です！Aspose.Words for .NET を使えば、表を揃えたWord文書をMarkdown形式にエクスポートするのは、一度やり方を覚えてしまえば簡単です。この強力なライブラリを使えば、表の書式設定や配置を簡単に制御でき、Markdown文書を思い通りの見た目に仕上げることができます。コーディングを楽しんでください！

## よくある質問

### Aspose.Words for .NET とは何ですか?
Aspose.Words for .NET は、開発者がプログラムによって Word 文書を作成、変更、変換、エクスポートできるようにする強力なライブラリです。

### 同じ表内の異なる列に異なる配置を設定できますか?
はい、 `Auto` 配置オプションを使用すると、各列の最初の段落に基づいて異なる配置を設定できます。

### Aspose.Words for .NET を使用するにはライセンスが必要ですか?
はい、Aspose.Words for .NETの全機能を使用するにはライセンスが必要です。 [一時ライセンス](https://purchase.aspose.com/temporary-license/) 評価のため。

### Aspose.Words を使用して他のドキュメント要素を Markdown にエクスポートすることは可能ですか?
はい、Aspose.Words は、見出し、リスト、画像などのさまざまな要素を Markdown 形式にエクスポートすることをサポートしています。

### 問題が発生した場合、どこでサポートを受けることができますか?
サポートを受けるには [Aspose.Words サポートフォーラム](https://forum。aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}