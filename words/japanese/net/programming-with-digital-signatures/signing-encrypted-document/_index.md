---
"description": "Aspose.Words for .NET を使用して暗号化されたWord文書に署名する方法を、詳細なステップバイステップガイドで学びましょう。開発者に最適です。"
"linktitle": "暗号化されたWord文書への署名"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "暗号化されたWord文書への署名"
"url": "/ja/net/programming-with-digital-signatures/signing-encrypted-document/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 暗号化されたWord文書への署名

## 導入

暗号化されたWord文書に署名する方法をご存知ですか？今日は、Aspose.Words for .NETを使ってその手順を解説します。シートベルトを締めて、詳細で魅力的、そして楽しいチュートリアルに備えましょう！

## 前提条件

コードに進む前に、必要なものがすべて揃っていることを確認しましょう。

1. Aspose.Words for .NET: ダウンロードしてインストールする [ここ](https://releases。aspose.com/words/net/).
2. Visual Studio: インストールされていることを確認してください。
3. 有効な証明書: .pfx 証明書ファイルが必要です。
4. C# の基本知識: 基本を理解すると、このチュートリアルがよりスムーズになります。

## 名前空間のインポート

まず、必要な名前空間をインポートしましょう。これらはAspose.Wordsの機能にアクセスするために不可欠です。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.DigitalSignatures;
```

それでは、プロセスをシンプルで管理しやすいステップに分解してみましょう。

## ステップ1: プロジェクトの設定

まず最初に、Visual Studioプロジェクトをセットアップします。Visual Studioを開き、新しいC#コンソールアプリケーションを作成します。「SignEncryptedWordDoc」など、わかりやすい名前を付けます。

## ステップ2: Aspose.Wordsをプロジェクトに追加する

次に、Aspose.Wordsをプロジェクトに追加する必要があります。これにはいくつかの方法がありますが、NuGetを使用するのが最も簡単です。 

1. [ツール] > [NuGet パッケージ マネージャー] > [パッケージ マネージャー コンソール] から NuGet パッケージ マネージャー コンソールを開きます。
2. 次のコマンドを実行します。

```powershell
Install-Package Aspose.Words
```

## ステップ3: ドキュメントディレクトリの準備

Word文書と証明書を保存するためのディレクトリが必要です。作成してみましょう。

1. コンピュータにディレクトリを作成します。ここでは「DocumentDirectory」と名付けます。
2. Word 文書 (例: 「Document.docx」) と .pfx 証明書 (例: 「morzal.pfx」) をこのディレクトリに配置します。

## ステップ4: コードを書く

では、コードを見てみましょう。 `Program.cs` ファイルを開いて、ドキュメントディレクトリへのパスを設定し、 `SignOptions` 復号パスワードを使用します。

```csharp
// ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENTS DIRECTORY";
SignOptions signOptions = new SignOptions { DecryptionPassword = "decryptionPassword" };
```

## ステップ5: 証明書の読み込み

次に、証明書をロードします。 `CertificateHolder` クラス。これには、.pfx ファイルへのパスと証明書のパスワードが必要です。

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

## ステップ6：文書に署名する

最後に、 `DigitalSignatureUtil.Sign` 暗号化されたWord文書に署名する方法です。この方法では、入力ファイル、出力ファイル、証明書所有者、および署名オプションが必要です。

```csharp
DigitalSignatureUtil.Sign(
    dataDir + "Document.docx",
    dataDir + "DigitallySignedDocument.docx",
    certHolder,
    signOptions);
```

## ステップ7: コードの実行

ファイルを保存してプロジェクトを実行してください。すべてが正しく設定されていれば、指定したディレクトリに署名済みの文書が表示されます。

## 結論

これで完了です！Aspose.Words for .NET を使って暗号化されたWord文書に署名できました。この強力なライブラリを使えば、暗号化されたファイルでもデジタル署名が簡単に行えます。コーディングを楽しみましょう！

## よくある質問

### 別の種類の証明書を使用できますか?
はい、Aspose.Words は、正しい形式である限り、さまざまな種類の証明書をサポートします。

### 一度に複数の文書に署名することは可能ですか?
もちろんです！ドキュメントのコレクションをループして、プログラムでそれぞれに署名することができます。

### 復号パスワードを忘れてしまったらどうすればいいですか？
残念ながら、復号化パスワードがないと文書に署名することはできません。

### 文書に可視署名を追加できますか?
はい、Aspose.Words では目に見えるデジタル署名も追加できます。

### 署名を検証する方法はありますか?
はい、使えます `DigitalSignatureUtil.Verify` 署名を検証する方法。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}