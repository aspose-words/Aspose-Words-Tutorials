---
title: ページ保存コールバック
linktitle: ページ保存コールバック
second_title: Aspose.Words ドキュメント処理 API
description: 詳細なステップバイステップ ガイドに従って、Aspose.Words for .NET を使用して Word 文書の各ページを個別の PNG 画像として保存する方法を学習します。
weight: 10
url: /ja/net/programming-with-imagesaveoptions/page-saving-callback/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ページ保存コールバック

## 導入

こんにちは! Word 文書の各ページを個別の画像として保存したいと思ったことはありませんか? 大きなレポートを簡単に理解できるビジュアルに分割したい場合や、プレビュー用のサムネイルを作成する必要がある場合もあります。理由が何であれ、Aspose.Words for .NET を使用すると、この作業が簡単になります。このガイドでは、ページ保存コールバックを設定して、文書の各ページを個別の PNG 画像として保存する手順を説明します。早速始めましょう!

## 前提条件

始める前に、以下のものを用意してください。

1.  Aspose.Words for .NET: まだダウンロードしていない場合は、こちらからダウンロードしてインストールしてください。[ここ](https://releases.aspose.com/words/net/).
2. Visual Studio: どのバージョンでも動作するはずですが、このガイドでは Visual Studio 2019 を使用します。
3. C# の基礎知識: この手順を実行するには、C# の基本的な理解が必要です。

## 名前空間のインポート

まず、必要な名前空間をインポートする必要があります。これにより、毎回完全な名前空間を入力しなくても、必要なクラスとメソッドにアクセスできるようになります。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## ステップ1: ドキュメントディレクトリを設定する

さて、まずはドキュメント ディレクトリへのパスを定義するところから始めましょう。これは、入力 Word ドキュメントが保存される場所であり、出力画像が保存される場所です。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## ステップ2: ドキュメントを読み込む

次に、処理するドキュメントを読み込みます。ドキュメント (「Rendering.docx」) が指定されたディレクトリにあることを確認してください。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## ステップ3: 画像保存オプションを設定する

画像を保存するためのオプションを設定する必要があります。この場合、ページを PNG ファイルとして保存します。

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

ここ、`PageSet`保存するページの範囲を指定し、`PageSavingCallback`カスタム コールバック クラスを指します。

## ステップ4: ページ保存コールバックを実装する

ここで、各ページの保存方法を処理するコールバック クラスを実装しましょう。

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

このクラスは、`IPageSavingCallback`インターフェース、そして`PageSaving`メソッドでは、保存された各ページの命名パターンを定義します。

## ステップ5: ドキュメントを画像として保存する

最後に、設定されたオプションを使用してドキュメントを保存します。

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## 結論

これで完了です。Aspose.Words for .NET を使用して、Word 文書の各ページを個別の PNG 画像として保存するためのページ保存コールバックを正常に設定できました。この手法は、ページ プレビューの作成からレポートの個別のページ画像の生成まで、さまざまなアプリケーションで非常に役立ちます。 

楽しいコーディングを！

## よくある質問

### PNG以外の形式でページを保存できますか?  
はい、JPEG、BMP、TIFFなどのさまざまな形式でページを保存できます。`SaveFormat`で`ImageSaveOptions`.

### 特定のページだけを保存したい場合はどうすればいいでしょうか?  
保存したいページを指定するには、`PageSet`パラメータ`ImageSaveOptions`.

### 画質をカスタマイズすることは可能ですか？  
もちろんです！次のようなプロパティを設定できます`ImageSaveOptions.JpegQuality`出力画像の品質を制御します。

### 大きな文書を効率的に処理するにはどうすればよいでしょうか?  
大きなドキュメントの場合は、メモリ使用量を効率的に管理するために、ページをバッチで処理することを検討してください。

### Aspose.Words for .NET の詳細情報はどこで入手できますか?  
チェックしてください[ドキュメント](https://reference.aspose.com/words/net/)包括的なガイドと例については、こちらをご覧ください。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
