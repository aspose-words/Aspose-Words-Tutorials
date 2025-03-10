---
title: PDF 文書内の画像圧縮
linktitle: PDF 文書内の画像圧縮
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して PDF ドキュメント内の画像を圧縮する方法を学びます。ファイル サイズと品質を最適化するには、このガイドに従ってください。
weight: 10
url: /ja/net/programming-with-pdfsaveoptions/image-compression/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# PDF 文書内の画像圧縮

## 導入

今日のデジタル時代では、ドキュメント サイズの管理はパフォーマンスとストレージ効率の両方にとって重要です。大きなレポートを扱う場合でも、複雑なプレゼンテーションを扱う場合でも、品質を犠牲にすることなくファイル サイズを縮小することが不可欠です。PDF ドキュメントでの画像圧縮は、この目標を達成するための重要な手法です。Aspose.Words for .NET を使用している場合は、ラッキーです。このチュートリアルでは、Aspose.Words for .NET を使用して PDF ドキュメントで画像を圧縮するプロセスについて説明します。さまざまな圧縮オプションと、それらを効果的に適用して PDF の品質とサイズの両方を最適化する方法について説明します。

## 前提条件

チュートリアルに進む前に、次の前提条件が満たされていることを確認してください。

1. Aspose.Words for .NET: Aspose.Words for .NETがインストールされている必要があります。[Aspose ウェブサイト](https://releases.aspose.com/words/net/).

2. C# の基礎知識: C# プログラミングの知識があると、このチュートリアルで提供されるコード例を理解するのに役立ちます。

3. 開発環境: Visual Studio などの .NET 開発環境が設定されていることを確認します。

4. サンプル ドキュメント: 画像圧縮をテストするためのサンプル Word ドキュメント (例: 「Rendering.docx」) を用意します。

5. Aspose ライセンス: Aspose.Words for .NET のライセンス版を使用している場合は、ライセンスが適切に設定されていることを確認してください。一時ライセンスが必要な場合は、以下から取得できます。[Aspose の一時ライセンス ページ](https://purchase.aspose.com/temporary-license/).

## 名前空間のインポート

Aspose.Words for .NET を使用して PDF ドキュメントで画像圧縮を開始するには、必要な名前空間をインポートする必要があります。手順は次のとおりです。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

これらの名前空間は、Word 文書を操作し、さまざまなオプションを使用して PDF として保存するために必要なコア機能へのアクセスを提供します。

## ステップ1: ドキュメントディレクトリを設定する

コーディングを始める前に、ドキュメント ディレクトリへのパスを定義します。これにより、ファイルを簡単に見つけて保存できるようになります。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

交換する`"YOUR DOCUMENT DIRECTORY"`サンプル ドキュメントが保存されているパスに置き換えます。

## ステップ2: Word文書を読み込む

次に、Word文書を`Aspose.Words.Document`オブジェクト。これにより、プログラムでドキュメントを操作できるようになります。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

ここ、`"Rendering.docx"`はサンプル Word 文書の名前です。このファイルが指定されたディレクトリにあることを確認してください。

## ステップ3: 基本的な画像圧縮を構成する

作成する`PdfSaveOptions`オブジェクトを使用して、画像圧縮を含むPDF保存オプションを設定します。`ImageCompression`財産に`PdfImageCompression.Jpeg`画像に JPEG 圧縮を使用します。

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
	// JPEGを使用して画像を圧縮する
    ImageCompression = PdfImageCompression.Jpeg,
	//オプション: PDF 内のフォーム フィールドを保持する
    PreserveFormFields = true
};
```

## ステップ4: 基本圧縮でドキュメントを保存する

設定された画像圧縮オプションを使用して、Word 文書を PDF として保存します。これにより、PDF 内の画像に JPEG 圧縮が適用されます。

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression.pdf", saveOptions);
```

この例では、出力PDFの名前は`"WorkingWithPdfSaveOptions.PdfImageCompression.pdf"`必要に応じてファイル名を調整します。

## ステップ5: PDF/A準拠の高度な圧縮を構成する

さらに圧縮率を高めるために、特にPDF/A規格に準拠する必要がある場合は、追加のオプションを設定できます。`Compliance`財産に`PdfCompliance.PdfA2u`調整して`JpegQuality`財産。

```csharp
PdfSaveOptions saveOptionsA2U = new PdfSaveOptions
{
	//コンプライアンスを PDF/A-2u に設定
    Compliance = PdfCompliance.PdfA2u,
	//JPEG圧縮を使用する
    ImageCompression = PdfImageCompression.Jpeg,
	//JPEG品質を調整して圧縮レベルを制御する
    JpegQuality = 100 
};
```

## ステップ6: 高度な圧縮でドキュメントを保存する

高度な圧縮設定を使用して、Word 文書を PDF として保存します。この構成により、PDF は PDF/A 標準に準拠し、高品質の JPEG 圧縮が使用されます。

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression_A2u.pdf", saveOptionsA2U);
```

ここで、出力PDFの名前は`"WorkingWithPdfSaveOptions.PdfImageCompression_A2u.pdf"`好みに応じてファイル名を変更します。

## 結論

画像を圧縮して PDF ドキュメントのサイズを縮小することは、ドキュメントのパフォーマンスとストレージを最適化するための重要なステップです。Aspose.Words for .NET には、画像圧縮を効果的に制御するための強力なツールが用意されています。このチュートリアルで説明する手順に従うことで、PDF ドキュメントを高品質かつコンパクトにすることができます。基本的な圧縮でも高度な圧縮でも、Aspose.Words はニーズを満たす柔軟性を提供します。


## よくある質問

### PDF での画像圧縮とは何ですか?
画像圧縮は、画像の品質を下げることで PDF ドキュメントのファイル サイズを縮小し、ストレージとパフォーマンスの最適化に役立ちます。

### Aspose.Words for .NET は画像圧縮をどのように処理しますか?
Aspose.Words for .NETは、`PdfSaveOptions`クラスでは、JPEG 圧縮を含むさまざまな画像圧縮オプションを設定できます。

### Aspose.Words for .NET を使用して PDF/A 標準に準拠できますか?
はい、Aspose.Words は PDF/A 準拠をサポートしており、アーカイブおよび長期保存の標準を満たす形式でドキュメントを保存できます。

### JPEG 品質は PDF ファイル サイズにどのような影響を与えますか?
JPEG 品質設定を高くすると画像品質は向上しますが、ファイル サイズが大きくなります。一方、品質設定を低くするとファイル サイズは小さくなりますが、画像の鮮明さに影響する可能性があります。

### Aspose.Words for .NET の詳細情報はどこで入手できますか?
 Aspose.Words for .NETの詳細については、[ドキュメント](https://reference.aspose.com/words/net/), [サポート](https://forum.aspose.com/c/words/8) 、 そして[ダウンロード](https://releases.aspose.com/words/net/)ページ。

### Aspose.Words for .NET で画像を圧縮するためのサンプル ソース コード

```csharp

//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");

PdfSaveOptions saveOptions = new PdfSaveOptions
{
	ImageCompression = PdfImageCompression.Jpeg, PreserveFormFields = true
};

doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression.pdf", saveOptions);

PdfSaveOptions saveOptionsA2U = new PdfSaveOptions
{
	Compliance = PdfCompliance.PdfA2u,
	ImageCompression = PdfImageCompression.Jpeg,
	JpegQuality = 100, //ファイル サイズを縮小するには、50% の品質で JPEG 圧縮を使用します。
};



doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression_A2u.pdf", saveOptionsA2U);
	
```
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
