---
title: Word 文書に目次を挿入する
linktitle: Word 文書に目次を挿入する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して Word に目次を挿入する方法を学びます。シームレスなドキュメント ナビゲーションを実現するには、ステップ バイ ステップ ガイドに従ってください。
weight: 10
url: /ja/net/add-content-using-documentbuilder/insert-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 文書に目次を挿入する

## 導入
このチュートリアルでは、Aspose.Words for .NET を使用して、Word 文書に目次 (TOC) を効率的に追加する方法を学習します。この機能は、長い文書を整理してナビゲートし、読みやすさを向上させ、文書のセクションの概要をすばやく提供するために不可欠です。

## 前提条件

始める前に、次のものがあることを確認してください。

- C# および .NET フレームワークの基本的な理解。
- マシンに Visual Studio がインストールされています。
-  Aspose.Words for .NETライブラリ。まだインストールしていない場合は、ここからダウンロードできます。[ここ](https://releases.aspose.com/words/net/).

## 名前空間のインポート

まず、C# プロジェクトに必要な名前空間をインポートします。

```csharp
using Aspose.Words;
using Aspose.Words.Builder;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

プロセスを明確なステップに分解してみましょう。

## ステップ 1: Aspose.Words ドキュメントと DocumentBuilder を初期化する

まず、新しいAspose.Wordsを初期化します。`Document`オブジェクトと`DocumentBuilder`一緒に働く：

```csharp
// DocumentとDocumentBuilderを初期化する
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## ステップ2: 目次を挿入する

次に、`InsertTableOfContents`方法：

```csharp
//目次を挿入
builder.InsertTableOfContents("\\o \"1-3\" \\h \\z \\u");
```

## ステップ3: 新しいページでドキュメントコンテンツを開始する

適切な書式設定を確実に行うには、実際のドキュメント コンテンツを新しいページで開始します。

```csharp
//改ページを挿入する
builder.InsertBreak(BreakType.PageBreak);
```

## ステップ4: 見出しを使って文書を構造化する

適切な見出しスタイルを使用してドキュメントのコンテンツを整理します。

```csharp
//見出しスタイルを設定する
builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 1.1");
builder.Writeln("Heading 1.2");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 2");
builder.Writeln("Heading 3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading3;
builder.Writeln("Heading 3.1.1");
builder.Writeln("Heading 3.1.2");
builder.Writeln("Heading 3.1.3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.2");
builder.Writeln("Heading 3.3");
```

## ステップ5: 目次を更新して入力する

ドキュメントの構造を反映するように目次を更新します。

```csharp
//目次フィールドを更新する
doc.UpdateFields();
```

## ステップ6: ドキュメントを保存する

最後に、ドキュメントを指定されたディレクトリに保存します。

```csharp
//文書を保存する
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
doc.Save(dataDir + "InsertTableOfContentsUsingAsposeWords.docx");
```

## 結論

Aspose.Words for .NET を使用して目次を追加するのは簡単で、ドキュメントの使いやすさが大幅に向上します。これらの手順に従うことで、複雑なドキュメントを効率的に整理し、ナビゲートすることができます。

## よくある質問

### 目次の外観をカスタマイズできますか?
はい、Aspose.Words for .NET API を使用して目次の外観と動作をカスタマイズできます。

### Aspose.Words はフィールドの自動更新をサポートしていますか?
はい、Aspose.Words では、ドキュメントの変更に基づいて目次などのフィールドを動的に更新できます。

### 1 つのドキュメントに複数の目次を生成できますか?
Aspose.Words は、単一のドキュメント内で異なる設定を持つ複数の目次を生成することをサポートしています。

### Aspose.Words はさまざまなバージョンの Microsoft Word と互換性がありますか?
はい、Aspose.Words はさまざまなバージョンの Microsoft Word 形式との互換性を保証します。

### Aspose.Words に関する詳細なヘルプとサポートはどこで見つかりますか?
さらに詳しいサポートについては、[Aspose.Words フォーラム](https://forum.aspose.com/c/words/8)または、[公式文書](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
