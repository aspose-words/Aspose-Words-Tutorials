---
title: Jpeg ページ範囲を取得
linktitle: Jpeg ページ範囲を取得
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word 文書の特定のページをカスタム設定で JPEG に変換します。明るさ、コントラスト、解像度を段階的に調整する方法を学びます。
weight: 10
url: /ja/net/programming-with-imagesaveoptions/get-jpeg-page-range/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jpeg ページ範囲を取得

## 導入

Word 文書を画像に変換すると、サムネイルを作成したり、オンラインで文書をプレビューしたり、よりアクセスしやすい形式でコンテンツを共有したりする場合に非常に便利です。Aspose.Words for .NET を使用すると、明るさ、コントラスト、解像度などのさまざまな設定をカスタマイズしながら、Word 文書の特定のページを JPEG 形式に簡単に変換できます。これをステップごとに実現する方法を詳しく見ていきましょう。

## 前提条件

始める前に、いくつかの準備が必要です:

-  Aspose.Words for .NET: Aspose.Words for .NETがインストールされていることを確認してください。[ここからダウンロード](https://releases.aspose.com/words/net/).
- 開発環境: Visual Studio のような C# 開発環境。
- サンプル ドキュメント: 作業に使用する Word ドキュメント。このチュートリアルでは任意の .docx ファイルを使用できます。
- 基本的な C# の知識: C# プログラミングに精通していること。

準備ができたら、始めましょう!

## 名前空間のインポート

Aspose.Words for .NET を使用するには、コードの先頭に必要な名前空間をインポートする必要があります。これにより、ドキュメント操作に必要なすべてのクラスとメソッドにアクセスできるようになります。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ1: ドキュメントを読み込む

まず、変換したいWord文書を読み込む必要があります。文書の名前が`Rendering.docx`プレースホルダで指定されたディレクトリにあります`YOUR DOCUMENT DIRECTORY`.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

このコードはドキュメントへのパスを初期化し、Aspose.Wordsに読み込みます。`Document`物体。

## ステップ2: ImageSaveOptionsを設定する

次に、`ImageSaveOptions` JPEG の生成方法を指定します。これには、ページ範囲、画像の明るさ、コントラスト、解像度の設定が含まれます。

```csharp
ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Jpeg);
options.PageSet = new PageSet(0); //最初のページのみ変換する
options.ImageBrightness = 0.3f;   //明るさを設定する
options.ImageContrast = 0.7f;     //コントラストを設定する
options.HorizontalResolution = 72f; //解像度を設定する
```

## ステップ3: ドキュメントをJPEGとして保存する

最後に、定義した設定を使用してドキュメントを JPEG ファイルとして保存します。

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.GetJpegPageRange.jpeg", options);
```

このコードは、`Rendering.docx`指定された明るさ、コントラスト、解像度の設定を持つ JPEG 画像として。

## 結論

これで完了です。Aspose.Words for .NET を使用して、Word 文書の特定のページをカスタマイズされた設定で JPEG 画像に変換できました。このプロセスは、Web サイト用の画像を準備する場合や、ドキュメントのプレビューを作成する場合など、さまざまなニーズに合わせてカスタマイズできます。

## よくある質問

### 複数のページを一度に変換できますか?
はい、ページの範囲を指定するには、`PageSet`不動産の`ImageSaveOptions`.

### 画質を調整するにはどうすればよいですか?
 JPEGの品質は、`JpegQuality`不動産の`ImageSaveOptions`.

### 他の画像形式で保存できますか?
はい、Aspose.WordsはPNG、BMP、TIFFなどのさまざまな画像形式をサポートしています。`SaveFormat`で`ImageSaveOptions`それに応じて。

### 保存する前に画像をプレビューする方法はありますか?
Aspose.Words には組み込みのプレビュー機能がないため、プレビュー メカニズムを別途実装する必要があります。

### Aspose.Words の一時ライセンスを取得するにはどうすればよいですか?
リクエストすることができます[一時ライセンスはこちら](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
