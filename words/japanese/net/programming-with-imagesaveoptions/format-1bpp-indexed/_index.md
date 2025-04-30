---
"description": "Aspose.Words for .NET を使用して、Word 文書を 1Bpp のインデックス付き画像に変換する方法を学びましょう。ステップバイステップのガイドに従って簡単に変換できます。"
"linktitle": "フォーマット 1Bpp インデックス"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "フォーマット 1Bpp インデックス"
"url": "/ja/net/programming-with-imagesaveoptions/format-1bpp-indexed/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# フォーマット 1Bpp インデックス

## 導入

たった数行のコードでWord文書を白黒画像として保存したいと思ったことはありませんか？ まさにその通りです！今日は、Aspose.Words for .NETを使って、文書を1Bppのインデックス付き画像に変換するちょっとしたコツをご紹介します。この形式は、特定の種類のデジタルアーカイブ、印刷、あるいは容量を節約したい場合に最適です。各ステップを丁寧に解説するので、とても簡単です。準備はできましたか？ さあ、始めましょう！

## 前提条件

作業を始める前に、準備しておくべきことがいくつかあります。

- Aspose.Words for .NET: ライブラリがインストールされていることを確認してください。 [ここからダウンロード](https://releases。aspose.com/words/net/).
- .NET 開発環境: Visual Studio は良い選択肢ですが、使い慣れた環境であればどれでも使用できます。
- C# の基本知識: 心配しないでください。簡単に説明しますが、C# に少し精通していると役立ちます。
- Word 文書: 変換するサンプルの Word 文書を用意しておきます。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートする必要があります。これは、Aspose.Words から必要なクラスやメソッドにアクセスできるようにするために非常に重要です。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ1: ドキュメントディレクトリを設定する

ドキュメントディレクトリへのパスを指定する必要があります。これはWord文書が保存されている場所であり、変換された画像も保存される場所です。

```csharp
// ドキュメントディレクトリへのパス
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ステップ2: Word文書を読み込む

さて、Word文書をAspose.Wordsにロードしてみましょう。 `Document` オブジェクト。このオブジェクトは Word ファイルを表し、これを操作することができます。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## ステップ3: 画像保存オプションを設定する

次に、 `ImageSaveOptions`魔法が起こるのはここです。画像を1BppインデックスカラーモードでPNG形式で保存するように設定します。

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
- ImagePixelFormat.Format1bppIndexed: 画像フォーマットを 1Bpp インデックスに設定します。

## ステップ4: ドキュメントを画像として保存する

最後に、ドキュメントを画像として保存します。 `Save` の方法 `Document` 物体。

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## 結論

これで完了です！わずか数行のコードで、Aspose.Words for .NET を使ってWord文書を1bppのインデックス付き画像に変換できました。この方法は、文書から高コントラストで省スペースな画像を作成するのに非常に便利です。これで、プロジェクトやワークフローに簡単に統合できます。コーディングを楽しんでください！

## よくある質問

### 1Bpp インデックス画像とは何ですか?
1Bpp (1 ビット/ピクセル) インデックス画像は、各ピクセルが 0 または 1 の 1 ビットで表された白黒画像形式です。この形式は、スペース効率が非常に優れています。

### Word 文書の複数のページを一度に変換できますか?
はい、できます。 `PageSet` の財産 `ImageSaveOptions` 複数のページまたはドキュメント全体を含めます。

### Aspose.Words for .NET を使用するにはライセンスが必要ですか?
はい、Aspose.Words for .NETの全機能を使用するにはライセンスが必要です。 [仮免許証はこちら](https://purchase。aspose.com/temporary-license/).

### Word 文書を他のどのような画像形式に変換できますか?
Aspose.WordsはJPEG、BMP、TIFFなど様々な画像形式をサポートしています。 `SaveFormat` の中で `ImageSaveOptions`。

### Aspose.Words for .NET に関する詳細なドキュメントはどこで入手できますか?
詳細なドキュメントは [Aspose.Words for .NET ドキュメント ページ](https://reference。aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}