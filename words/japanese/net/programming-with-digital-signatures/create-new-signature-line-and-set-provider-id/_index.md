---
"description": "Aspose.Words for .NET を使用して、Word 文書に新しい署名欄を作成し、プロバイダー ID を設定する方法を学びます。ステップバイステップ ガイド。"
"linktitle": "新しい署名欄を作成し、プロバイダー ID を設定する"
"second_title": "Aspose.Words ドキュメント処理 API"
"title": "新しい署名欄を作成し、プロバイダー ID を設定する"
"url": "/ja/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 新しい署名欄を作成し、プロバイダー ID を設定する

## 導入

テクノロジーに詳しい皆さん、こんにちは！Word文書にプログラムで署名欄を追加する方法を考えたことはありませんか？今日は、Aspose.Words for .NETを使って、まさにその方法を詳しく解説します。このガイドでは、Word文書に新しい署名欄を作成し、プロバイダーIDを設定する手順を一つ一つ丁寧に解説します。文書処理の自動化を目指す場合でも、ワークフローの効率化を目指す場合でも、このチュートリアルがきっとお役に立ちます。

## 前提条件

作業を始める前に、必要なものがすべて揃っていることを確認しましょう。

1. Aspose.Words for .NET: まだダウンロードしていない場合はダウンロードしてください [ここ](https://releases。aspose.com/words/net/).
2. 開発環境: Visual Studio またはその他の C# 開発環境。
3. .NET Framework: .NET Framework がインストールされていることを確認してください。
4. PFX証明書：文書に署名するには、PFX証明書が必要です。信頼できる証明機関から取得できます。

## 名前空間のインポート

まず最初に、C# プロジェクトに必要な名前空間をインポートしましょう。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

では、本題に入りましょう。新しい署名欄を作成し、プロバイダーIDを設定する手順を、それぞれ詳しく説明します。

## ステップ1：新しいドキュメントを作成する

まず、新しいWord文書を作成します。これが署名欄のキャンバスになります。

```csharp
// ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

このスニペットでは、新しい `Document` そして `DocumentBuilder`。その `DocumentBuilder` ドキュメントに要素を追加するのに役立ちます。

## ステップ2: 署名行のオプションを定義する

次に、署名欄のオプションを定義します。署名者の名前、役職、メールアドレス、その他の詳細が含まれます。

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

これらのオプションにより、署名行がパーソナライズされ、明確かつプロフェッショナルなものになります。

## ステップ3: 署名欄を挿入する

オプションを設定すると、文書に署名行を挿入できるようになります。

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

ここでは、 `InsertSignatureLine` メソッドは署名行を追加し、それに一意のプロバイダー ID を割り当てます。

## ステップ4: ドキュメントを保存する

署名欄を挿入したら、文書を保存しましょう。

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

これにより、新しく追加された署名行を含むドキュメントが保存されます。

## ステップ5: 署名オプションを設定する

次に、ドキュメントに署名するためのオプションを設定します。これには、署名行ID、プロバイダーID、コメント、署名時刻が含まれます。

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

これらのオプションにより、ドキュメントが正しい詳細で署名されることが保証されます。

## ステップ6: 証明書所有者を作成する

ドキュメントに署名するには、PFX証明書を使用します。そのための証明書ホルダーを作成しましょう。

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

必ず交換してください `"morzal.pfx"` 実際の証明書ファイルと `"aw"` 証明書のパスワードを入力します。

## ステップ7：文書に署名する

最後に、デジタル署名ユーティリティを使用してドキュメントに署名します。

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

これにより、ドキュメントが署名され、新しいファイルとして保存されます。

## 結論

これで完了です！Aspose.Words for .NET を使って、Word 文書に新しい署名欄を作成し、プロバイダー ID を設定できました。この強力なライブラリを使えば、文書処理タスクの管理と自動化が驚くほど簡単になります。ぜひお試しいただき、ワークフローを効率化できるかどうかご確認ください。

## よくある質問

### 署名行の外観をカスタマイズできますか?
もちろんです！様々なオプションを調整できます `SignatureLineOptions` お客様のニーズに合わせて。

### PFX 証明書を持っていない場合はどうなりますか?
信頼できる証明機関から証明書を取得する必要があります。これは、文書にデジタル署名するために不可欠です。

### 文書に複数の署名行を追加できますか?
はい、さまざまなオプションで挿入プロセスを繰り返すことで、必要な数の署名行を追加できます。

### Aspose.Words for .NET は .NET Core と互換性がありますか?
はい、Aspose.Words for .NET は .NET Core をサポートしており、さまざまな開発環境に柔軟に対応できます。

### デジタル署名はどの程度安全ですか?
有効で信頼できる証明書を使用している限り、Aspose.Words で作成されたデジタル署名は非常に安全です。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}