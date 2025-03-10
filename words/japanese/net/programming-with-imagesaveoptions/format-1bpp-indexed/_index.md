---
title: フォーマット 1Bpp インデックス
linktitle: フォーマット 1Bpp インデックス
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word 文書を 1Bpp のインデックス付き画像に変換する方法を学びます。簡単な変換を行うには、ステップ バイ ステップ ガイドに従ってください。
weight: 10
url: /ja/net/programming-with-imagesaveoptions/format-1bpp-indexed/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# フォーマット 1Bpp インデックス

## 導入

数行のコードで Word 文書を白黒画像として保存する方法を考えたことはありませんか? いいえ、大丈夫です! 今日は、Aspose.Words for .NET を使用して、文書を 1Bpp インデックス画像に変換できる便利な小技を紹介します。この形式は、特定の種類のデジタル アーカイブ、印刷、またはスペースを節約する必要がある場合に最適です。各手順を分解して、簡単に行えるようにします。準備はできましたか? さあ、始めましょう!

## 前提条件

実際に作業を始める前に、準備しておくべきことがいくつかあります。

-  Aspose.Words for .NET: ライブラリがインストールされていることを確認してください。[ここからダウンロード](https://releases.aspose.com/words/net/).
- .NET 開発環境: Visual Studio は良い選択肢ですが、使い慣れた環境であればどれでも使用できます。
- C# の基本知識: 心配しないでください。簡単に説明しますが、C# に少し精通していると役立ちます。
- Word 文書: 変換するサンプルの Word 文書を用意します。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートする必要があります。これは、Aspose.Words から必要なクラスとメソッドにアクセスできるようにするため、非常に重要です。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ1: ドキュメントディレクトリを設定する

ドキュメント ディレクトリへのパスを指定する必要があります。これは Word ドキュメントが保存される場所であり、変換された画像が保存される場所です。

```csharp
//ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ステップ2: Word文書を読み込む

さて、Word文書をAspose.Wordsにロードしてみましょう。`Document`オブジェクト。このオブジェクトは Word ファイルを表し、それを操作できるようにします。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## ステップ3: 画像保存オプションを設定する

次に、`ImageSaveOptions`ここで魔法が起こります。1Bpp インデックス カラー モードで PNG 形式で画像を保存するように設定します。

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1),
    ImageColorMode = ImageColorMode.BlackAndWhite,
    PixelFormat = ImagePixelFormat.Format1bppIndexed
};
```

- SaveFormat.Png: ドキュメントを PNG 画像として保存することを指定します。
- PageSet(1): これは最初のページのみを変換することを示します。
- ImageColorMode.BlackAndWhite: 画像を白黒に設定します。
- ImagePixelFormat.Format1bppIndexed: 画像形式を 1Bpp インデックスに設定します。

## ステップ4: ドキュメントを画像として保存する

最後に、ドキュメントを画像として保存します。`Save`方法の`Document`物体。

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## 結論

これで完了です。わずか数行のコードで、Aspose.Words for .NET を使用して Word 文書を 1Bpp のインデックス付き画像に変換できました。この方法は、文書から高コントラストでスペース効率の高い画像を作成するのに非常に便利です。これで、これをプロジェクトやワークフローに簡単に統合できます。コーディングを楽しんでください。

## よくある質問

### 1Bpp インデックス画像とは何ですか?
1Bpp (1 ビット/ピクセル) インデックス画像は、各ピクセルが 0 または 1 の 1 ビットで表された白黒画像形式です。この形式は、スペース効率が非常に優れています。

### Word 文書の複数のページを一度に変換できますか?
はい、できます。`PageSet`の財産`ImageSaveOptions`複数のページまたはドキュメント全体を含めます。

### Aspose.Words for .NET を使用するにはライセンスが必要ですか?
はい、Aspose.Words for .NETの全機能を使用するにはライセンスが必要です。[一時ライセンスはこちら](https://purchase.aspose.com/temporary-license/).

### Word 文書を他のどのような画像形式に変換できますか?
 Aspose.WordsはJPEG、BMP、TIFFなどさまざまな画像形式をサポートしています。`SaveFormat`の`ImageSaveOptions`.

### Aspose.Words for .NET に関する詳細なドキュメントはどこで入手できますか?
詳細なドキュメントは[Aspose.Words for .NET ドキュメント ページ](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
