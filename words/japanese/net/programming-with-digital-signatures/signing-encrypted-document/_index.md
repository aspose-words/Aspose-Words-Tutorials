---
title: 暗号化された Word 文書に署名する
linktitle: 暗号化された Word 文書に署名する
second_title: Aspose.Words ドキュメント処理 API
description: この詳細なステップバイステップ ガイドでは、Aspose.Words for .NET を使用して暗号化された Word 文書に署名する方法を学習します。開発者に最適です。
weight: 10
url: /ja/net/programming-with-digital-signatures/signing-encrypted-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 暗号化された Word 文書に署名する

## 導入

暗号化された Word 文書に署名する方法を考えたことはありませんか? 今日は、Aspose.Words for .NET を使用してこのプロセスについて説明します。シートベルトを締めて、詳細で魅力的で楽しいチュートリアルの準備をしましょう。

## 前提条件

コードに進む前に、必要なものがすべて揃っていることを確認しましょう。

1.  Aspose.Words for .NET: ダウンロードしてインストールする[ここ](https://releases.aspose.com/words/net/).
2. Visual Studio: インストールされていることを確認してください。
3. 有効な証明書: .pfx 証明書ファイルが必要です。
4. C# の基本知識: 基本を理解すると、このチュートリアルがよりスムーズになります。

## 名前空間のインポート

まず、必要な名前空間をインポートしましょう。これらは Aspose.Words の機能にアクセスするために重要です。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.DigitalSignatures;
```

それでは、プロセスをシンプルで管理しやすいステップに分解してみましょう。

## ステップ1: プロジェクトの設定

まず最初に、Visual Studio プロジェクトをセットアップします。Visual Studio を開き、新しい C# コンソール アプリケーションを作成します。「SignEncryptedWordDoc」のようなわかりやすい名前を付けます。

## ステップ 2: プロジェクトに Aspose.Words を追加する

次に、Aspose.Words をプロジェクトに追加する必要があります。これを行うにはいくつかの方法がありますが、NuGet を使用するのが最も簡単です。 

1. [ツール] > [NuGet パッケージ マネージャー] > [パッケージ マネージャー コンソール] から NuGet パッケージ マネージャー コンソールを開きます。
2. 次のコマンドを実行します。

```powershell
Install-Package Aspose.Words
```

## ステップ3: ドキュメントディレクトリの準備

Word 文書と証明書を保存するためのディレクトリが必要になります。作成してみましょう。

1. コンピュータにディレクトリを作成します。簡単にするために、「DocumentDirectory」という名前を付けます。
2. Word 文書 (例: 「Document.docx」) と .pfx 証明書 (例: 「morzal.pfx」) をこのディレクトリに配置します。

## ステップ4: コードを書く

さて、コードを見てみましょう。`Program.cs`ファイルを開いて、ドキュメントディレクトリへのパスを設定し、`SignOptions`復号化パスワードを使用します。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENTS DIRECTORY";
SignOptions signOptions = new SignOptions { DecryptionPassword = "decryptionPassword" };
```

## ステップ5: 証明書の読み込み

次に、`CertificateHolder`クラス。これには、.pfx ファイルへのパスと証明書のパスワードが必要です。

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## ステップ6: 文書に署名する

最後に、`DigitalSignatureUtil.Sign`暗号化された Word 文書に署名する方法。この方法では、入力ファイル、出力ファイル、証明書所有者、および署名オプションが必要です。

```csharp
DigitalSignatureUtil.Sign(
    dataDir + "Document.docx",
    dataDir + "DigitallySignedDocument.docx",
    certHolder,
    signOptions);
```

## ステップ7: コードの実行

ファイルを保存してプロジェクトを実行します。すべてが正しく設定されていれば、指定したディレクトリに署名されたドキュメントが表示されます。

## 結論

これで完了です。Aspose.Words for .NET を使用して暗号化された Word 文書に正常に署名できました。この強力なライブラリを使用すると、暗号化されたファイルでもデジタル署名が簡単になります。コーディングをお楽しみください。

## よくある質問

### 別の種類の証明書を使用できますか?
はい、Aspose.Words は、正しい形式であればさまざまな種類の証明書をサポートします。

### 一度に複数の文書に署名することは可能ですか?
もちろんです! ドキュメントのコレクションをループし、それぞれにプログラムで署名することができます。

### 復号パスワードを忘れてしまったらどうすればいいですか？
残念ながら、復号化パスワードがないと文書に署名することはできません。

### 文書に目に見える署名を追加できますか?
はい、Aspose.Words では目に見えるデジタル署名も追加できます。

### 署名を検証する方法はありますか?
はい、`DigitalSignatureUtil.Verify`署名を検証する方法。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
