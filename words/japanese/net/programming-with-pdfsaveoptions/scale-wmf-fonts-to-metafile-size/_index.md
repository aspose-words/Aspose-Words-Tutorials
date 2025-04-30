---
"description": "Aspose.Words for .NET を使用して PDF に変換するときに、wmf フォントをメタファイル サイズにスケールして PDF サイズを縮小する手順ガイド。"
"linktitle": "WMFフォントをメタファイルサイズにスケールしてPDFサイズを縮小"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "WMFフォントをメタファイルサイズにスケールしてPDFサイズを縮小"
"url": "/ja/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# WMFフォントをメタファイルサイズにスケールしてPDFサイズを縮小

## 導入

PDFファイル、特にWMF（Windowsメタファイル）グラフィックを含むWord文書から生成されたPDFファイルを扱う場合、サイズ管理はドキュメント処理において非常に重要な要素となります。PDFのサイズを制御する方法の一つは、ドキュメント内でのWMFフォントのレンダリング方法を調整することです。このチュートリアルでは、Aspose.Words for .NETを使用してWMFフォントをメタファイルサイズに合わせてスケーリングすることで、PDFのサイズを縮小する方法を説明します。

## 前提条件

手順に進む前に、次のものを用意してください。

1. Aspose.Words for .NET: Aspose.Wordsライブラリがインストールされていることを確認してください。インストールされていない場合は、 [ここからダウンロード](https://releases。aspose.com/words/net/).
2. 開発環境: このチュートリアルでは、C# コードを記述および実行できる .NET 開発環境 (Visual Studio など) がセットアップされていることを前提としています。
3. .NET プログラミングの基本的な理解: .NET プログラミングの基本的な概念と C# 構文を理解していると役立ちます。
4. WMFグラフィックを含むWord文書：WMFグラフィックを含むWord文書が必要です。ご自身の文書を使用することも、テスト用に新規作成することもできます。

## 名前空間のインポート

まず、C#プロジェクトに必要な名前空間をインポートする必要があります。これにより、Aspose.Words の操作に必要なクラスとメソッドにアクセスできるようになります。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ1: Word文書を読み込む

まず、WMFグラフィックを含むWord文書を読み込みます。これは、 `Document` Aspose.Words のクラス。

```csharp
// ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";

// ドキュメントを読み込む
Document doc = new Document(dataDir + "WMF with text.docx");
```

ここ、 `dataDir` ドキュメントディレクトリパスのプレースホルダです。 `Document` クラスにWordファイルへのパスを渡すことで、ドキュメントがメモリに読み込まれ、その後の処理が可能になります。

## ステップ2: メタファイルレンダリングオプションを構成する

次に、メタファイルのレンダリングオプションを設定する必要があります。具体的には、 `ScaleWmfFontsToMetafileSize` 財産に `false`これは、WMF フォントをメタファイルのサイズに合わせて拡大縮小するかどうかを制御します。

```csharp
// MetafileRenderingOptionsの新しいインスタンスを作成する
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

その `MetafileRenderingOptions` クラスは、メタファイル（WMFなど）のレンダリング方法に関するオプションを提供します。 `ScaleWmfFontsToMetafileSize` に `false`、Aspose.Words にメタファイルのサイズに応じてフォントを拡大縮小しないように指示することになり、全体的な PDF サイズを削減するのに役立ちます。

## ステップ3: PDF保存オプションを設定する

次に、PDF保存オプションで、先ほど設定したメタファイルレンダリングオプションを使用するように設定します。これにより、Aspose.WordsはドキュメントをPDFとして保存する際にメタファイルをどのように処理するかを決定します。

```csharp
// PdfSaveOptionsの新しいインスタンスを作成する
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

その `PdfSaveOptions` クラスを使用すると、ドキュメントをPDFとして保存するためのさまざまな設定を指定できます。事前に設定した `MetafileRenderingOptions` に `MetafileRenderingOptions` の所有物 `PdfSaveOptions`、ドキュメントが希望するメタファイル レンダリング設定に従って保存されることを保証します。

## ステップ4: ドキュメントをPDFとして保存する

最後に、設定した保存オプションを使用してWord文書をPDFとして保存します。これにより、メタファイルレンダリングオプションを含むすべての設定が出力PDFに適用されます。


```csharp
// 文書をPDFとして保存する
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

このステップでは、 `Save` の方法 `Document` クラスはドキュメントをPDFファイルにエクスポートするために使用されます。PDFを保存するパスと、 `PdfSaveOptions` メタファイルのレンダリング設定が含まれます。

## 結論

WMFフォントをメタファイルサイズにスケーリングすることで、Word文書から生成されるPDFファイルのサイズを大幅に削減できます。この手法は、視覚的なコンテンツの品質を損なうことなく、文書の保存と配布を最適化するのに役立ちます。上記の手順に従うことで、PDFファイルの管理が容易になり、サイズも効率的になります。

## よくある質問

### WMF とは何ですか? また、PDF サイズにとってなぜ重要ですか?

WMF（Windowsメタファイル）は、Microsoft Windowsで使用されるグラフィック形式です。ベクターデータとビットマップデータの両方を格納できます。ベクターデータは拡大縮小や操作が可能なため、PDFファイルが不必要に大きくなるのを避けるには、適切に処理することが重要です。

### WMF フォントをメタファイル サイズにスケーリングすると、PDF にどのような影響がありますか?

WMF フォントをメタファイル サイズにスケーリングすると、ファイル サイズが大きくなる可能性のある高解像度フォントのレンダリングを回避することで、PDF 全体のサイズを削減できます。

### Aspose.Words で他のメタファイル形式を使用できますか?

はい、Aspose.Words は WMF に加えて EMF (拡張メタファイル) を含むさまざまなメタファイル形式をサポートしています。

### このテクニックはすべての種類の Word 文書に適用できますか?

はい、この手法は WMF グラフィックを含む任意の Word 文書に適用でき、生成される PDF のサイズを最適化するのに役立ちます。

### Aspose.Words の詳細情報はどこで入手できますか?

Aspose.Wordsの詳細については、 [Aspose.Words ドキュメント](https://reference.aspose.com/words/net/)ダウンロード、トライアル、サポートについては、 [Aspose.Words ダウンロードページ](https://releases.aspose.com/words/net/)、 [Aspose.Wordsを購入する](https://purchase.aspose.com/buy)、 [無料トライアル](https://releases.aspose.com/)、 [一時ライセンス](https://purchase.aspose.com/temporary-license/)、 そして [サポート](https://forum。aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}