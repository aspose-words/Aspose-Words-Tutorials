---
title: WMF フォントをメタファイル サイズにスケールして PDF サイズを縮小する
linktitle: WMF フォントをメタファイル サイズにスケールして PDF サイズを縮小する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して PDF に変換するときに、wmf フォントをメタファイル サイズにスケールして PDF サイズを縮小する手順ガイド。
weight: 10
url: /ja/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# WMF フォントをメタファイル サイズにスケールして PDF サイズを縮小する

## 導入

PDF ファイル、特に WMF (Windows メタファイル) グラフィックを含む Word 文書から生成された PDF ファイルを扱う場合、サイズ管理は文書処理の重要な側面になります。PDF サイズを制御する 1 つの方法は、文書内での WMF フォントのレンダリング方法を調整することです。このチュートリアルでは、Aspose.Words for .NET を使用して WMF フォントをメタファイル サイズにスケーリングすることで PDF サイズを縮小する方法について説明します。

## 前提条件

手順に進む前に、以下のものを用意してください。

1. Aspose.Words for .NET: Aspose.Wordsライブラリがインストールされていることを確認してください。インストールされていない場合は、[ここからダウンロード](https://releases.aspose.com/words/net/).
2. 開発環境: このチュートリアルでは、C# コードを記述して実行できる .NET 開発環境 (Visual Studio など) が設定されていることを前提としています。
3. .NET プログラミングの基本的な理解: 基本的な .NET プログラミングの概念と C# 構文を理解していると役立ちます。
4. WMF グラフィックを含む Word 文書: WMF グラフィックを含む Word 文書が必要です。独自の文書を使用することも、テスト用に文書を作成することもできます。

## 名前空間のインポート

まず、C# プロジェクトに必要な名前空間をインポートする必要があります。これにより、Aspose.Words の操作に必要なクラスとメソッドにアクセスできるようになります。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ1: Word文書を読み込む

まず、WMFグラフィックを含むWord文書を読み込みます。これは、`Document` Aspose.Words のクラス。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";

//ドキュメントを読み込む
Document doc = new Document(dataDir + "WMF with text.docx");
```

ここ、`dataDir`ドキュメントディレクトリパスのプレースホルダです。`Document`クラスに Word ファイルへのパスを渡すことで、ドキュメントがメモリに読み込まれ、さらに処理できるようになります。

## ステップ2: メタファイルレンダリングオプションを構成する

次に、メタファイルのレンダリングオプションを設定する必要があります。具体的には、`ScaleWmfFontsToMetafileSize`財産に`false`これは、WMF フォントがメタファイルのサイズに合わせて拡大縮小されるかどうかを制御します。

```csharp
// MetafileRenderingOptionsの新しいインスタンスを作成する
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

の`MetafileRenderingOptions`クラスは、メタファイル（WMFなど）のレンダリング方法のオプションを提供します。設定により`ScaleWmfFontsToMetafileSize`に`false`すると、Aspose.Words にメタファイルのサイズに応じてフォントを拡大縮小しないように指示することになり、全体的な PDF サイズを削減するのに役立ちます。

## ステップ3: PDF保存オプションを設定する

ここで、設定したメタファイル レンダリング オプションを使用するように PDF 保存オプションを構成します。これにより、ドキュメントを PDF として保存するときにメタファイルを処理する方法が Aspose.Words に指示されます。

```csharp
// PdfSaveOptionsの新しいインスタンスを作成する
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

の`PdfSaveOptions`クラスを使用すると、ドキュメントをPDFとして保存するためのさまざまな設定を指定できます。以前に設定した`MetafileRenderingOptions`に`MetafileRenderingOptions`の所有物`PdfSaveOptions`、ドキュメントが希望するメタファイル レンダリング設定に従って保存されていることを確認します。

## ステップ4: ドキュメントをPDFとして保存する

最後に、設定した保存オプションを使用して Word 文書を PDF として保存します。これにより、メタファイル レンダリング オプションを含むすべての設定が出力 PDF に適用されます。


```csharp
//文書をPDFとして保存する
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

このステップでは、`Save`方法の`Document`クラスは、ドキュメントをPDFファイルにエクスポートするために使用されます。PDFが保存されるパスと、`PdfSaveOptions`メタファイルのレンダリング設定が含まれます。

## 結論

WMF フォントをメタファイル サイズにスケーリングすると、Word 文書から生成される PDF ファイルのサイズを大幅に削減できます。この手法は、視覚コンテンツの品質を損なうことなく、文書の保存と配布を最適化するのに役立ちます。上記の手順に従うと、PDF ファイルの管理が容易になり、サイズが効率的になります。

## よくある質問

### WMF とは何ですか? また、PDF サイズにとってなぜ重要ですか?

WMF (Windows メタファイル) は、Microsoft Windows で使用されるグラフィック形式です。ベクター データとビットマップ データの両方を含めることができます。ベクター データは拡大縮小や操作が可能なため、PDF ファイルが不必要に大きくなるのを避けるために適切に処理することが重要です。

### WMF フォントをメタファイル サイズにスケーリングすると、PDF にどのような影響がありますか?

WMF フォントをメタファイル サイズにスケーリングすると、ファイル サイズが増加する可能性のある高解像度フォントのレンダリングを回避することで、PDF 全体のサイズを削減できます。

### Aspose.Words で他のメタファイル形式を使用できますか?

はい、Aspose.Words は WMF に加えて EMF (拡張メタファイル) を含むさまざまなメタファイル形式をサポートしています。

### この手法はすべての種類の Word 文書に適用できますか?

はい、この手法は WMF グラフィックを含む任意の Word 文書に適用でき、生成される PDF のサイズを最適化するのに役立ちます。

### Aspose.Words の詳細情報はどこで入手できますか?

 Aspose.Wordsの詳細については、[Aspose.Words ドキュメント](https://reference.aspose.com/words/net/)ダウンロード、トライアル、サポートについては、[Aspose.Words ダウンロード ページ](https://releases.aspose.com/words/net/), [Aspose.Words を購入する](https://purchase.aspose.com/buy), [無料トライアル](https://releases.aspose.com/), [一時ライセンス](https://purchase.aspose.com/temporary-license/) 、 そして[サポート](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
