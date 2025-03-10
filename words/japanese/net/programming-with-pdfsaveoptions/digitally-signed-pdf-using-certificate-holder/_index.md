---
title: 証明書ホルダーを使用してPDFにデジタル署名を追加する
linktitle: 証明書ホルダーを使用してPDFにデジタル署名を追加する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、デジタル署名で PDF ファイルを保護します。このステップバイステップ ガイドに従って、PDF にデジタル署名を簡単に追加します。
weight: 10
url: /ja/net/programming-with-pdfsaveoptions/digitally-signed-pdf-using-certificate-holder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 証明書ホルダーを使用してPDFにデジタル署名を追加する

## 導入

PDF ドキュメントをデジタル署名で保護する方法を考えたことはありませんか? まさにその通りです! デジタル署名は手書きの署名の現代版であり、デジタル ドキュメントの信頼性と整合性を検証する方法を提供します。 このチュートリアルでは、Aspose.Words for .NET を使用して PDF にデジタル署名を追加する方法を説明します。 環境の設定からコードの実行まで、すべてをステップ バイ ステップで説明します。 このガイドを読み終えると、安全で信頼性の高いデジタル署名された PDF が完成します。

## 前提条件

始める前に、いくつか必要なものがあります:

1.  Aspose.Words for .NET: Aspose.Words for .NETがインストールされていることを確認してください。[Aspose ウェブサイト](https://releases.aspose.com/words/net/).
2. 証明書ファイル: PDF に署名するには、.pfx 証明書ファイルが必要です。証明書ファイルがない場合は、テスト用に自己署名証明書を作成できます。
3. Visual Studio: このチュートリアルでは、開発環境として Visual Studio を使用していることを前提としています。
4. C# の基礎知識: C# および .NET プログラミングに精通していることが必須です。

## 名前空間のインポート

まず、必要な名前空間をインポートしましょう。これらは、ドキュメントの操作やデジタル署名に必要なクラスやメソッドにアクセスするために不可欠です。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
```

プロセスをシンプルで管理しやすいステップに分解してみましょう。

## ステップ1: プロジェクトを設定する

Visual Studio で新しい C# プロジェクトを作成します。Aspose.Words for .NET への参照を追加します。これは、NuGet パッケージ マネージャーで「Aspose.Words」を検索してインストールすることで実行できます。

## ステップ2: ドキュメントを読み込むか作成する

署名する文書が必要です。既存の文書を読み込むか、新しい文書を作成することができます。このチュートリアルでは、新しい文書を作成し、サンプル テキストを追加します。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

//ドキュメントにテキストを追加します。
builder.Writeln("Test Signed PDF.");
```

## ステップ3: デジタル署名の詳細を指定する

次に、デジタル署名の詳細を設定します。.pfx 証明書ファイルへのパス、署名の理由、場所、署名日を指定する必要があります。

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    DigitalSignatureDetails = new PdfDigitalSignatureDetails(
        CertificateHolder.Create(dataDir + "morzal.pfx", "your_password"), "reason", "location",
        DateTime.Now)
};
```

交換する`"your_password"` .pfx ファイルのパスワードを入力します。

## ステップ4: 文書をデジタル署名されたPDFとして保存する

最後に、デジタル署名付きの PDF としてドキュメントを保存します。

```csharp
doc.Save(dataDir + "DigitallySignedPdfUsingCertificateHolder.pdf", saveOptions);
```

これで完了です。ドキュメントに署名が付けられ、PDF として保存されました。

## 結論

デジタル署名は、ドキュメントの整合性と信頼性を保証する強力なツールです。Aspose.Words for .NET を使用すると、PDF ファイルにデジタル署名を簡単に効率的に追加できます。このステップ バイ ステップ ガイドに従うことで、PDF ドキュメントを保護し、受信者に信頼性に関して安心感を与えることができます。コーディングをお楽しみください。

## よくある質問

### デジタル署名とは何ですか?
デジタル署名は、デジタル文書の信頼性と整合性を検証する署名の電子形式です。

### デジタル署名を追加するには証明書が必要ですか?
はい、PDF にデジタル署名を追加するには、.pfx 証明書ファイルが必要です。

### テスト用に自己署名証明書を作成できますか?
はい、テスト目的で自己署名証明書を作成できます。ただし、実稼働環境で使用する場合は、信頼できる証明機関から証明書を取得することをお勧めします。

### Aspose.Words for .NET は無料ですか?
 Aspose.Words for .NETは商用製品ですが、以下のサイトから無料試用版をダウンロードすることができます。[Aspose ウェブサイト](https://releases.aspose.com/).

### Aspose.Words for .NET を使用して他の種類のドキュメントに署名できますか?
はい、Aspose.Words for .NET は PDF だけでなく、さまざまな種類のドキュメントに署名するために使用できます。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
