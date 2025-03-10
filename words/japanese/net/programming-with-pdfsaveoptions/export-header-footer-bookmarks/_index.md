---
title: Word 文書のヘッダー フッター ブックマークを PDF 文書にエクスポートする
linktitle: Word 文書のヘッダー フッター ブックマークを PDF 文書にエクスポートする
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word 文書からヘッダーとフッターのブックマークを PDF にエクスポートする方法をステップバイステップ ガイドで学習します。
weight: 10
url: /ja/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 文書のヘッダー フッター ブックマークを PDF 文書にエクスポートする

## 導入

Word 文書を PDF に変換することは、特に文書の書式設定を保持したまま共有またはアーカイブする場合によく行われるタスクです。これらの文書には、ヘッダーとフッター内に重要なブックマークが含まれている場合があります。このチュートリアルでは、Aspose.Words for .NET を使用して、これらのブックマークを Word 文書から PDF にエクスポートするプロセスについて説明します。

## 前提条件

始める前に、以下のものを用意しておいてください。

- Aspose.Words for .NET: Aspose.Words for .NET がインストールされている必要があります。ダウンロードはこちらから行えます。[ここ](https://releases.aspose.com/words/net/).
- 開発環境: 開発環境を設定します。Visual Studio またはその他の .NET 互換 IDE を使用できます。
- C# の基礎知識: コード例に従うには、C# プログラミングの知識が必要です。

## 名前空間のインポート

まず最初に、C# プロジェクトに必要な名前空間をインポートする必要があります。コード ファイルの先頭に次の行を追加します。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

プロセスをわかりやすいステップに分解してみましょう。

## ステップ1: ドキュメントを初期化する

最初のステップは、Word 文書を読み込むことです。手順は次のとおりです。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

この手順では、ドキュメント ディレクトリへのパスを指定して、Word ドキュメントを読み込むだけです。

## ステップ2: PDF保存オプションを設定する

次に、ヘッダーとフッターのブックマークが正しくエクスポートされるように、PDF 保存オプションを構成する必要があります。

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

ここでは、`PdfSaveOptions` 。`DefaultBookmarksOutlineLevel`プロパティはブックマークのアウトラインレベルを設定し、`HeaderFooterBookmarksExportMode`プロパティにより、ヘッダーとフッター内のブックマークの最初の出現のみがエクスポートされます。

## ステップ3: ドキュメントをPDFとして保存する

最後に、設定したオプションを使用してドキュメントを PDF として保存します。

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

この手順では、設定したオプションを使用して、指定したパスにドキュメントを保存します。

## 結論

これで完了です。これらの手順に従うと、Aspose.Words for .NET を使用して、Word 文書のヘッダーとフッターからブックマークを PDF に簡単にエクスポートできます。この方法により、文書内の重要なナビゲーション補助が PDF 形式で保持され、読者が文書内を簡単に移動できるようになります。

## よくある質問

### Word 文書からすべてのブックマークを PDF にエクスポートできますか?

はい、できます。`PdfSaveOptions`必要に応じて、すべてのブックマークを含めるように設定を調整できます。

### ドキュメントの本文からもブックマークをエクスポートしたい場合はどうすればよいでしょうか?

設定できるのは`OutlineOptions`で`PdfSaveOptions`ドキュメントの本文からブックマークを追加します。

### PDF 内のブックマーク レベルをカスタマイズすることは可能ですか?

もちろんです！`DefaultBookmarksOutlineLevel`ブックマークに異なるアウトライン レベルを設定するプロパティ。

### ブックマークのないドキュメントをどのように処理すればよいですか?

ドキュメントにブックマークがない場合、PDF はブックマークのアウトラインなしで生成されます。PDF でブックマークが必要な場合は、ドキュメントにブックマークが含まれていることを確認してください。

### この方法は、DOCX や RTF などの他のドキュメント タイプにも使用できますか?

はい、Aspose.Words for .NET は、DOCX、RTF など、さまざまなドキュメント タイプをサポートしています。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
