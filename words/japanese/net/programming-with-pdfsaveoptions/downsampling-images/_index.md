---
title: 画像のダウンサンプリングでPDF文書のサイズを縮小
linktitle: 画像のダウンサンプリングでPDF文書のサイズを縮小
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して画像をダウンサンプリングすることで、PDF ドキュメントのサイズを縮小します。PDF を最適化して、アップロードとダウンロードの時間を短縮します。
weight: 10
url: /ja/net/programming-with-pdfsaveoptions/downsampling-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 画像のダウンサンプリングでPDF文書のサイズを縮小

## 導入

PDF はデジタルの世界では欠かせないものであり、ドキュメントの共有から電子書籍の作成まで、あらゆる用途に使用されています。ただし、特に画像の多いコンテンツを扱う場合、そのサイズが障害になることがあります。ここで、画像のダウンサンプリングが役立ちます。PDF 内の画像の解像度を下げることで、品質をあまり損なうことなくファイル サイズを大幅に削減できます。このチュートリアルでは、Aspose.Words for .NET を使用してこれを実現する手順について説明します。

## 前提条件

コードに進む前に、必要なものがすべて揃っていることを確認しましょう。

1.  Aspose.Words for .NET: Aspose.Wordsライブラリがインストールされていることを確認してください。インストールされていない場合はダウンロードできます。[ここ](https://releases.aspose.com/words/net/).
2. 開発環境: Visual Studio などの任意の .NET 開発環境。
3. C# の基礎知識: C# プログラミングの基礎を理解しておくと役立ちます。
4. サンプル文書: Word文書(例:`Rendering.docx`) を画像とともに PDF に変換します。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートする必要があります。コード ファイルの先頭に以下を追加します。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

それでは、プロセスを管理しやすいステップに分解してみましょう。

## ステップ1: ドキュメントを読み込む

最初のステップは、Word 文書を読み込むことです。ここで、文書ディレクトリへのパスを指定します。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

このステップでは、指定されたディレクトリからWord文書を読み込みます。`"YOUR DOCUMENT DIRECTORY"`ドキュメントが配置されている実際のパスを入力します。

## ステップ2: ダウンサンプリングオプションを設定する

次に、ダウンサンプリング オプションを設定する必要があります。これには、画像の解像度と解像度しきい値の設定が含まれます。

```csharp
//ダウンサンプリングの最小しきい値を設定できます。
//この値により、入力ドキュメント内の 2 番目の画像がダウンサンプリングされなくなります。
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    DownsampleOptions = { Resolution = 36, ResolutionThreshold = 128 }
};
```

ここでは、新しいインスタンスを作成します`PdfSaveOptions`そして設定`Resolution`36DPIまで`ResolutionThreshold`128 DPI にダウンサンプリングされます。つまり、128 DPI を超える解像度の画像はすべて 36 DPI にダウンサンプリングされます。

## ステップ3: ドキュメントをPDFとして保存する

最後に、設定したオプションを使用してドキュメントを PDF として保存します。

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.DownsamplingImages.pdf", saveOptions);
```

この最後のステップでは、指定されたダウンサンプリング オプションを使用して、ドキュメントを同じディレクトリに PDF として保存します。

## 結論

これで完了です。Aspose.Words for .NET を使用して画像をダウンサンプリングすることで、PDF のサイズを縮小できました。これにより、PDF の管理が容易になるだけでなく、アップロードやダウンロードが高速化され、表示エクスペリエンスもスムーズになります。

## よくある質問

### ダウンサンプリングとは何ですか?
ダウンサンプリングは画像の解像度を下げるプロセスであり、画像を含むドキュメントのファイル サイズを縮小するのに役立ちます。

### ダウンサンプリングは画像の品質に影響しますか?
はい、ダウンサンプリングを行うと画質は低下します。ただし、影響は解像度の低下度合いによって異なります。ファイル サイズと画質はトレードオフの関係にあります。

### ダウンサンプリングする画像を選択できますか?
はい、設定することで`ResolutionThreshold`元の解像度に基づいて、どの画像をダウンサンプリングするかを制御できます。

### ダウンサンプリングに最適な解像度は何ですか?
理想的な解像度は、特定のニーズによって異なります。一般的に、Web 画像には 72 DPI が使用され、印刷品質にはより高い解像度が使用されます。

### Aspose.Words for .NET は無料ですか?
 Aspose.Words for .NETは商用製品ですが、無料試用版をダウンロードできます。[ここ](https://releases.aspose.com/)または申請する[一時ライセンス](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
