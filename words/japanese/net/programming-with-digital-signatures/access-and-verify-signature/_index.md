---
title: Word 文書の署名にアクセスして検証する
linktitle: Word 文書の署名にアクセスして検証する
second_title: Aspose.Words ドキュメント処理 API
description: この包括的なステップバイステップ ガイドを使用して、Aspose.Words for .NET を使用して Word 文書のデジタル署名にアクセスし、検証します。文書の信頼性を簡単に確保できます。
weight: 10
url: /ja/net/programming-with-digital-signatures/access-and-verify-signature/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 文書の署名にアクセスして検証する

## 導入

こんにちは、技術愛好家の皆さん！Word 文書のデジタル署名にアクセスして検証する必要があるのに、どこから始めればよいか分からないという状況に陥ったことはありませんか？そんなあなたに朗報です！今日は、Word 文書の取り扱いを簡単にする強力なライブラリである Aspose.Words for .NET の素晴らしい世界に飛び込みます。このガイドを読み終える頃には、Word 文書のデジタル署名を検証するプロになっていることでしょう。さあ、始めましょう！

## 前提条件

細かい詳細に入る前に、準備しておく必要のあるものがいくつかあります。

1. Visual Studio: マシンに Visual Studio がインストールされていることを確認してください。ここでコードを記述して実行します。
2.  Aspose.Words for .NET: Aspose.Words for .NETがインストールされている必要があります。ダウンロードできます。[ここ](https://releases.aspose.com/words/net/)無料トライアルをお忘れなく[ここ](https://releases.aspose.com/)まだ読んでいないなら！
3. デジタル署名された Word 文書: すでにデジタル署名された Word 文書を用意します。これが署名を検証するために使用するファイルです。

## 名前空間のインポート

まず最初に、必要な名前空間をインポートしましょう。これらの名前空間により、プロジェクトで Aspose.Words 機能を使用できるようになります。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.DigitalSignatures;
```

では、これを管理しやすいステップに分解してみましょう。各ステップでは、プロセスの特定の部分をガイドします。準備はいいですか? さあ、始めましょう!

## ステップ1: プロジェクトを設定する

デジタル署名を検証する前に、Visual Studio でプロジェクトを設定する必要があります。手順は次のとおりです。

### 新しいプロジェクトを作成する

1. Visual Studio を開きます。
2. 「新しいプロジェクトの作成」をクリックします。
3. 好みに応じて、コンソール アプリ (.NET Core) またはコンソール アプリ (.NET Framework) を選択します。
4. 「次へ」をクリックし、プロジェクトに名前を付けて、「作成」をクリックします。

### Aspose.Words for .NET をインストールする

1. ソリューション エクスプローラーで、プロジェクト名を右クリックし、[NuGet パッケージの管理] を選択します。
2. NuGet パッケージ マネージャーで、Aspose.Words を検索します。
3. 「インストール」をクリックしてプロジェクトに追加します。

## ステップ2: デジタル署名されたWord文書を読み込む

プロジェクトが設定されたので、デジタル署名された Word 文書を読み込みます。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Digitally signed.docx");
```

交換する`"YOUR DOCUMENT DIRECTORY"`ドキュメントディレクトリへの実際のパスを入力します。このコードスニペットは新しい`Document`オブジェクトを作成し、署名された Word 文書を読み込みます。

## ステップ3: デジタル署名にアクセスする

ドキュメントが読み込まれたら、デジタル署名にアクセスします。

```csharp
foreach (DigitalSignature signature in doc.DigitalSignatures)
{
    Console.WriteLine("* Signature Found *");
    Console.WriteLine("Is valid: " + signature.IsValid);
    Console.WriteLine("Reason for signing: " + signature.Comments); 
    Console.WriteLine("Time of signing: " + signature.SignTime);
    Console.WriteLine("Subject name: " + signature.CertificateHolder.Certificate.SubjectName.Name);
    Console.WriteLine("Issuer name: " + signature.CertificateHolder.Certificate.IssuerName.Name);
    Console.WriteLine();
}
```

このコードは、ドキュメント内の各デジタル署名をループし、署名に関するさまざまな詳細を出力します。各部分の動作を詳しく見てみましょう。

1. 署名が見つかりました: 署名が見つかったことを示します。
2. 有効: 署名が有効かどうかを確認します。
3. 署名の理由: 署名の理由がある場合はそれを表示します。
4. 署名時刻: 文書が署名されたときのタイムスタンプを表示します。
5. サブジェクト名: 証明書からサブジェクト名を取得します。
6. 発行者名: 証明書から発行者名を取得します。

## ステップ4: コードを実行する

すべての設定が完了したら、コードを実行して結果を確認します。


1. プログラムを実行するには、F5 キーを押すか、Visual Studio の [スタート] ボタンをクリックします。
2. ドキュメントがデジタル署名されている場合は、コンソールに署名の詳細が表示されます。

## ステップ5: 潜在的なエラーを処理する

発生する可能性のあるエラーを常に処理しておくことは良い考えです。コードに基本的なエラー処理を追加してみましょう。

```csharp
try
{
    //ドキュメント ディレクトリへのパス。
    string dataDir = "YOUR DOCUMENT DIRECTORY";
    Document doc = new Document(dataDir + "Digitally signed.docx");

    foreach (DigitalSignature signature in doc.DigitalSignatures)
    {
        Console.WriteLine("* Signature Found *");
        Console.WriteLine("Is valid: " + signature.IsValid);
        Console.WriteLine("Reason for signing: " + signature.Comments); 
        Console.WriteLine("Time of signing: " + signature.SignTime);
        Console.WriteLine("Subject name: " + signature.CertificateHolder.Certificate.SubjectName.Name);
        Console.WriteLine("Issuer name: " + signature.CertificateHolder.Certificate.IssuerName.Name);
        Console.WriteLine();
    }
}
catch (Exception ex)
{
    Console.WriteLine("An error occurred: " + ex.Message);
}
```

これにより、発生する可能性のある例外がすべてキャッチされ、エラー メッセージが出力されます。

## 結論

これで完了です。Aspose.Words for .NET を使用して、Word 文書内のデジタル署名にアクセスし、検証することができました。思ったほど難しくありませんよね? これらの手順に従うと、Word 文書内のデジタル署名を自信を持って処理し、その信頼性と整合性を確保できます。コーディングを楽しんでください!

## よくある質問

### Aspose.Words for .NET を使用して Word 文書にデジタル署名を追加できますか?

はい、Aspose.Words for .NET を使用して Word 文書にデジタル署名を追加できます。ライブラリには、デジタル署名の追加と検証の両方のための包括的な機能が備わっています。

### Aspose.Words for .NET はどのような種類のデジタル署名を検証できますか?

Aspose.Words for .NET は、X.509 証明書を使用する DOCX ファイル内のデジタル署名を検証できます。

### Aspose.Words for .NET は Microsoft Word のすべてのバージョンと互換性がありますか?

Aspose.Words for .NET は、DOC、DOCX、RTF など、Microsoft Word ドキュメントのすべてのバージョンをサポートします。

### Aspose.Words for .NET の一時ライセンスを取得するにはどうすればよいですか?

 Aspose.Words for .NETの一時ライセンスは以下から入手できます。[ここ](https://purchase.aspose.com/temporary-license/)これにより、ライブラリのすべての機能を制限なく試すことができます。

### Aspose.Words for .NET に関する詳細なドキュメントはどこで入手できますか?

 Aspose.Words for .NETの詳細なドキュメントは以下をご覧ください。[ここ](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
