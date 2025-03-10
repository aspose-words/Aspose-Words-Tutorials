---
title: PDFをJpegとして保存
linktitle: PDFをJpegとして保存
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、PDF を JPEG に簡単に変換できます。例と FAQ を含む詳細なガイドに従ってください。開発者や愛好家に最適です。
weight: 10
url: /ja/net/basic-conversions/pdf-to-jpeg/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# PDFをJpegとして保存

## 導入

PDF ファイルを JPEG 画像に変換する必要がある状況に遭遇したことがありますか? 共有しやすくするため、プレゼンテーションに埋め込むため、または単に簡単にプレビューするためでしょうか? 幸運です! このチュートリアルでは、Aspose.Words for .NET の世界を詳しく調べて、PDF を JPEG として保存する方法を説明します。信じてください、思ったより簡単です。では、コーヒーを 1 杯飲み、ゆっくり座って、PDF を魅力的な JPEG に変換してみましょう!

## 前提条件

細かい点に入る前に、準備が整っていることを確認しましょう。必要なものは次のとおりです。

1. Aspose.Words for .NET: この強力なライブラリがインストールされていることを確認してください。インストールされていない場合はダウンロードできます。[ここ](https://releases.aspose.com/words/net/).
2. .NET Framework: マシンに .NET 環境が設定されていることを確認してください。
3. Visual Studio: 操作に慣れていれば、どのバージョンでも構いません。
4.  PDFファイル: 変換するPDFファイルを準備します。このチュートリアルでは、`Pdf Document.pdf`.

## 名前空間のインポート

まず最初に、必要な名前空間をインポートしましょう。この手順により、コードが Aspose.Words for .NET によって提供されるすべてのクラスとメソッドにアクセスできるようになります。

```csharp
using System;
using Aspose.Words;
```

さて、楽しい部分に移りましょう！プロセスをわかりやすいステップに分解します。

## ステップ1: プロジェクトを設定する

コードに取り組む前に、プロジェクトを設定する必要があります。手順は次のとおりです。

1. Visual Studio を開きます。まず、Visual Studio を起動し、新しい C# プロジェクトを作成します。
2.  Aspose.Wordsのインストール: NuGetパッケージマネージャーを使用してAspose.Words for .NETをインストールします。[ここ](https://releases.aspose.com/words/net/).

```shell
Install-Package Aspose.Words
```

3. ディレクトリの作成: PDF と結果の JPEG ファイルを保存するためのディレクトリを設定します。

## ステップ2: PDF文書を読み込む

プロジェクトの準備ができたので、PDF ドキュメントを読み込んでみましょう。ここで Aspose.Words が活躍します。

1. ディレクトリ パスの定義: ドキュメント ディレクトリへのパスを設定します。ここに PDF ファイルが保存されます。

    ```csharp
    string dataDir = "YOUR DOCUMENT DIRECTORY";
    ```

2.  PDFを読み込む:`Document` PDF を読み込むための Aspose.Words のクラス。

    ```csharp
    Document doc = new Document(dataDir + "Pdf Document.pdf");
    ```

## ステップ3: PDFをJPEGに変換する

PDF が読み込まれたら、変換を実行します。この手順は驚くほど簡単です。

1.  JPEGとして保存:`Save` PDF を JPEG 画像に変換する方法。

    ```csharp
    doc.Save(dataDir + "BaseConversions.PdfToJpeg.jpeg");
    ```

2. コードを実行する: プロジェクトを実行すると、PDF が新しい JPEG になります。

## 結論

これで完了です。Aspose.Words for .NET を使用して PDF を JPEG に変換するのは簡単です。わずか数行のコードでドキュメントを変換し、可能性の世界を広げることができます。ワークフローを合理化したい開発者でも、コードをいじるのが好きな人でも、Aspose.Words が役に立ちます。

## よくある質問

### 複数の PDF を一度に変換できますか?
もちろんです! PDF のディレクトリをループして、それぞれを JPEG に変換できます。

### Aspose.Words は他の画像形式をサポートしていますか?
はい、できます。PDF を PNG、BMP などとして保存できます。

### Aspose.Words は .NET Core と互換性がありますか?
確かにそうです。Aspose.Words は .NET Framework と .NET Core の両方をサポートしています。

### Aspose.Words を使用するにはライセンスが必要ですか?
無料トライアルをご利用ください[ここ](https://releases.aspose.com/)またはライセンスを購入する[ここ](https://purchase.aspose.com/buy).

### Aspose.Words に関するその他のチュートリアルはどこで見つかりますか?
チェックしてください[ドキュメント](https://reference.aspose.com/words/net/)豊富なチュートリアルとガイドをご覧ください。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
