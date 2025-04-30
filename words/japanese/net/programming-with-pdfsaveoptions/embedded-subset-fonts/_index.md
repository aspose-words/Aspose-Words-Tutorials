---
"description": "Aspose.Words for .NET を使って必要なフォントサブセットのみを埋め込むことで、PDF ファイルのサイズを縮小できます。ステップバイステップのガイドに従って、PDF を効率的に最適化しましょう。"
"linktitle": "PDF文書にサブセットフォントを埋め込む"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "PDF文書にサブセットフォントを埋め込む"
"url": "/ja/net/programming-with-pdfsaveoptions/embedded-subset-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# PDF文書にサブセットフォントを埋め込む

## 導入

似たような内容のPDFファイルでも、ファイルサイズが他のファイルよりもかなり大きいことに気づいたことはありませんか？その原因は多くの場合、フォントにあります。PDFにフォントを埋め込むと、どのデバイスでも同じ表示になりますが、ファイルサイズが肥大化してしまうこともあります。幸いなことに、Aspose.Words for .NETには、必要なフォントのサブセットだけを埋め込む便利な機能があり、PDFをスリムで効率的な状態に保つことができます。このチュートリアルでは、その手順をステップバイステップで説明します。

## 前提条件

始める前に、次のものを用意してください。

- Aspose.Words for .NET: ダウンロードできます [ここ](https://releases。aspose.com/words/net/).
- .NET 環境: 動作する .NET 開発環境があることを確認します。
- C# の基本知識: C# プログラミングの知識があると、理解しやすくなります。

## 名前空間のインポート

Aspose.Words for .NETを使用するには、プロジェクトに必要な名前空間をインポートする必要があります。以下のコードをC#ファイルの先頭に追加してください。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ1：ドキュメントを読み込む

まず、PDFに変換したいWord文書を読み込む必要があります。これは、 `Document` Aspose.Words によって提供されるクラス。

```csharp
// ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

このコードスニペットは、次の場所にあるドキュメントを読み込みます。 `dataDir`必ず交換してください `"YOUR DOCUMENT DIRECTORY"` ドキュメントへの実際のパスを入力します。

## ステップ2: PDF保存オプションを設定する

次に、 `PdfSaveOptions` 必要なフォントサブセットのみが埋め込まれるようにします。 `EmbedFullFonts` に `false`、ドキュメントで使用されているグリフのみを埋め込むように Aspose.Words に指示します。

```csharp
// 出力 PDF には、ドキュメント内のフォントのサブセットが含まれます。
// PDF フォントには、ドキュメントで使用されているグリフのみが含まれます。
PdfSaveOptions saveOptions = new PdfSaveOptions { EmbedFullFonts = false };
```

この小さいながらも重要なステップは、PDF ファイルのサイズを大幅に削減するのに役立ちます。

## ステップ3: ドキュメントをPDFとして保存する

最後に、ドキュメントをPDFとして保存します。 `Save` 設定された方法を適用する `PdfSaveOptions`。

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf", saveOptions);
```

このコードは、次の名前のPDFファイルを生成します。 `WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf` 必要なフォント サブセットのみが埋め込まれた、指定されたディレクトリに保存されます。

## 結論

これで完了です！これらの簡単な手順に従うだけで、Aspose.Words for .NET を使用して必要なフォントサブセットのみを埋め込むことで、PDFファイルのサイズを効率的に削減できます。これにより、ストレージ容量を節約できるだけでなく、特にフォントを多く使用するドキュメントの読み込み時間とパフォーマンスが向上します。

## よくある質問

### PDF にフォントのサブセットのみを埋め込む必要があるのはなぜですか?
必要なフォント サブセットのみを埋め込むと、ドキュメントの外観や読みやすさを損なうことなく、PDF ファイルのサイズを大幅に削減できます。

### 必要に応じて、完全なフォントの埋め込みに戻すことはできますか?
はい、できます。 `EmbedFullFonts` 財産に `true` の中で `PdfSaveOptions`。

### Aspose.Words for .NET は他の PDF 最適化機能もサポートしていますか?
もちろんです! Aspose.Words for .NET には、画像の圧縮や未使用オブジェクトの削除など、PDF を最適化するためのさまざまなオプションが用意されています。

### Aspose.Words for .NET を使用してサブセット埋め込むことができるフォントの種類は何ですか?
Aspose.Words for .NET は、ドキュメントで使用されるすべての TrueType フォントのサブセット埋め込みをサポートします。

### PDF に埋め込まれているフォントを確認するにはどうすればよいですか?
Adobe Acrobat Reader で PDF を開き、「フォント」タブのプロパティをチェックして埋め込まれたフォントを確認できます。



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}