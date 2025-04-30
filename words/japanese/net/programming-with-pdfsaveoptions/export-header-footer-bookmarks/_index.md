---
"description": "Aspose.Words for .NET を使用して、Word 文書からヘッダーとフッターのブックマークを PDF にエクスポートする方法をステップバイステップ ガイドで学習します。"
"linktitle": "Word文書のヘッダーとフッターのブックマークをPDF文書にエクスポートする"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "Word文書のヘッダーとフッターのブックマークをPDF文書にエクスポートする"
"url": "/ja/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word文書のヘッダーとフッターのブックマークをPDF文書にエクスポートする

## 導入

Word文書をPDFに変換することは、特に書式を維持したまま文書を共有したりアーカイブしたりしたい場合によく行われる作業です。これらの文書には、ヘッダーやフッターに重要なブックマークが含まれている場合があります。このチュートリアルでは、Aspose.Words for .NETを使用して、これらのブックマークをWord文書からPDFにエクスポートする手順を説明します。

## 前提条件

始める前に、次のものを用意しておいてください。

- Aspose.Words for .NET: Aspose.Words for .NET がインストールされている必要があります。こちらからダウンロードできます。 [ここ](https://releases。aspose.com/words/net/).
- 開発環境：開発環境を設定します。Visual Studio またはその他の .NET 互換 IDE を使用できます。
- C# の基礎知識: コード例を理解するには、C# プログラミングの知識が必要です。

## 名前空間のインポート

まず最初に、C#プロジェクトに必要な名前空間をインポートする必要があります。コードファイルの先頭に以下の行を追加してください。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

プロセスをわかりやすいステップに分解してみましょう。

## ステップ1: ドキュメントを初期化する

最初のステップはWord文書を読み込むことです。手順は以下のとおりです。

```csharp
// ドキュメント ディレクトリへのパス。
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

ここでは、 `PdfSaveOptions`。その `DefaultBookmarksOutlineLevel` プロパティはブックマークのアウトラインレベルを設定し、 `HeaderFooterBookmarksExportMode` プロパティにより、ヘッダーとフッター内のブックマークの最初の出現のみがエクスポートされます。

## ステップ3: ドキュメントをPDFとして保存する

最後に、設定したオプションを使用してドキュメントを PDF として保存します。

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

この手順では、設定したオプションを使用して、指定したパスにドキュメントを保存します。

## 結論

これで完了です！これらの手順に従うだけで、Aspose.Words for .NET を使用して、Word 文書のヘッダーとフッターにあるブックマークを PDF に簡単にエクスポートできます。この方法により、文書内の重要なナビゲーション情報が PDF 形式でも保持されるため、読者は文書内を簡単に移動できます。

## よくある質問

### Word 文書からすべてのブックマークを PDF にエクスポートできますか?

はい、できます。 `PdfSaveOptions`必要に応じて、すべてのブックマークを含めるように設定を調整できます。

### ドキュメント本体からもブックマークをエクスポートしたい場合はどうすればよいでしょうか?

設定できるのは `OutlでeOptions` in `PdfSaveOptions` ドキュメントの本文からブックマークを含めます。

### PDF 内のブックマーク レベルをカスタマイズすることは可能ですか?

もちろんです！ `DefaultBookmarksOutlineLevel` ブックマークに異なるアウトライン レベルを設定するプロパティ。

### ブックマークのないドキュメントをどのように処理すればよいですか?

ドキュメントにブックマークがない場合、PDFはブックマークのアウトラインなしで生成されます。PDFでブックマークが必要な場合は、ドキュメントにブックマークが含まれていることを確認してください。

### この方法は、DOCX や RTF などの他のドキュメント タイプにも使用できますか?

はい、Aspose.Words for .NET は、DOCX、RTF など、さまざまなドキュメント タイプをサポートしています。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}