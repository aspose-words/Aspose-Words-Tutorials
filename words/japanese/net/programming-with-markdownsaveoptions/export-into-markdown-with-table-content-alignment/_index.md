---
title: 表のコンテンツの位置合わせをしながら Markdown にエクスポートする
linktitle: 表のコンテンツの位置合わせをしながら Markdown にエクスポートする
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、整列したテーブルを含む Word 文書を Markdown にエクスポートする方法を学びます。完璧な Markdown テーブルを作成するには、ステップバイステップのガイドに従ってください。
weight: 10
url: /ja/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 表のコンテンツの位置合わせをしながら Markdown にエクスポートする

## 導入

こんにちは! Word 文書を、完璧に整列した表とともに Markdown 形式にエクスポートする方法を考えたことはありませんか? ドキュメント作成に取り組んでいる開発者でも、Markdown を愛用している人でも、このガイドは役に立ちます。これを実現するために Aspose.Words for .NET を使用する方法について詳しく説明します。Word の表を、整列した Markdown 表に変換する準備はできましたか? さあ、始めましょう!

## 前提条件

コードに進む前に、準備しておく必要があるものがいくつかあります。

1.  Aspose.Words for .NET ライブラリ: Aspose.Words for .NET ライブラリがインストールされていることを確認してください。[Aspose リリース ページ](https://releases.aspose.com/words/net/).
2. 開発環境: 開発環境を設定します。Visual Studio は .NET 開発によく使用されます。
3. C# の基礎知識: この言語でコードを記述するため、C# を理解することは不可欠です。
4. サンプル Word 文書: テストに使用できる Word 文書を用意します。

## 名前空間のインポート

コーディングを始める前に、必要な名前空間をインポートしましょう。これにより、使用する Aspose.Words のクラスとメソッドにアクセスできるようになります。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ 1: Document と DocumentBuilder を初期化する

まず最初に、新しいWord文書を作成し、`DocumentBuilder`ドキュメントの構築を開始するためのオブジェクト。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";

//新しいドキュメントを作成します。
Document doc = new Document();

// DocumentBuilder を初期化します。
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ステップ2: セルを挿入してコンテンツを揃える

次に、ドキュメントにセルをいくつか挿入し、配置を設定します。これは、Markdown エクスポートで正しい配置が維持されるようにするために重要です。

```csharp
//セルを挿入し、右揃えに設定します。
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

//別のセルを挿入し、配置を中央に設定します。
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## ステップ3: Markdownエクスポートの表コンテンツの配置を設定する

さて、設定をしましょう`MarkdownSaveOptions`エクスポートされた Markdown ファイル内の表の内容の配置を制御します。どのように機能するかを確認するために、さまざまな配置設定でドキュメントを保存してみます。

```csharp
// MarkdownSaveOptions オブジェクトを作成します。
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

//ドキュメントを左揃えで保存します。
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

//配置を右に変更して保存します。
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

//配置を中央に変更して保存します。
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## ステップ4: 表のコンテンツの自動配置を使用する

の`Auto`配置オプションは、対応する表の列の最初の段落から配置を取得します。これは、1 つの表に複数の配置が混在している場合に便利です。

```csharp
//配置を自動に設定します。
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

//自動配置でドキュメントを保存します。
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## 結論

これで完了です。Aspose.Words for .NET を使用して、整列した表を含む Word 文書を Markdown にエクスポートするのは、やり方がわかれば簡単です。この強力なライブラリを使用すると、表の書式設定と配置を簡単に制御できるため、Markdown 文書が希望どおりに表示されるようになります。コーディングを楽しんでください。

## よくある質問

### Aspose.Words for .NET とは何ですか?
Aspose.Words for .NET は、開発者がプログラムによって Word 文書を作成、変更、変換、エクスポートできるようにする強力なライブラリです。

### 同じ表内の異なる列に異なる配置を設定できますか?
はい、`Auto`配置オプションを使用すると、各列の最初の段落に基づいて異なる配置を設定できます。

### Aspose.Words for .NET を使用するにはライセンスが必要ですか?
はい、Aspose.Words for .NETの全機能を使用するにはライセンスが必要です。[一時ライセンス](https://purchase.aspose.com/temporary-license/)評価のため。

### Aspose.Words を使用して他のドキュメント要素を Markdown にエクスポートすることは可能ですか?
はい、Aspose.Words は、見出し、リスト、画像などのさまざまな要素を Markdown 形式にエクスポートすることをサポートしています。

### 問題が発生した場合、どこでサポートを受けることができますか?
サポートを受けるには[Aspose.Words サポート フォーラム](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
