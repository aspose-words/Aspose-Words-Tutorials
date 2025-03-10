---
title: 新しい署名欄を作成し、プロバイダー ID を設定する
linktitle: 新しい署名欄を作成し、プロバイダー ID を設定する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word 文書に新しい署名欄を作成し、プロバイダー ID を設定する方法を学習します。ステップ バイ ステップ ガイド。
weight: 10
url: /ja/net/programming-with-digital-signatures/create-new-signature-line-and-set-provider-id/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 新しい署名欄を作成し、プロバイダー ID を設定する

## 導入

こんにちは、技術愛好家の皆さん! Word 文書にプログラムで署名欄を追加する方法を考えたことはありませんか? 今日は、Aspose.Words for .NET を使用してその方法について詳しく説明します。このガイドでは、すべての手順を順を追って説明し、Word 文書に新しい署名欄を作成し、プロバイダー ID を設定するのが簡単になるようにします。文書処理を自動化する場合でも、ワークフローを合理化する場合でも、このチュートリアルが役立ちます。

## 前提条件

作業を始める前に、必要なものがすべて揃っていることを確認しましょう。

1.  Aspose.Words for .NET: まだダウンロードしていない場合はダウンロードしてください[ここ](https://releases.aspose.com/words/net/).
2. 開発環境: Visual Studio またはその他の C# 開発環境。
3. .NET Framework: .NET Framework がインストールされていることを確認してください。
4. PFX 証明書: ドキュメントに署名するには、PFX 証明書が必要です。信頼できる証明機関から取得できます。

## 名前空間のインポート

まず最初に、C# プロジェクトに必要な名前空間をインポートしましょう。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

さて、本題に入りましょう。新しい署名行を作成し、プロバイダー ID を設定するための各手順を詳しく説明します。

## ステップ1: 新しいドキュメントを作成する

まず、新しい Word 文書を作成する必要があります。これが署名行のキャンバスになります。

```csharp
//ドキュメント ディレクトリへのパス。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

このスニペットでは、新しい`Document`そして`DocumentBuilder` 。`DocumentBuilder`ドキュメントに要素を追加するのに役立ちます。

## ステップ2: 署名行オプションを定義する

次に、署名行のオプションを定義します。これには、署名者の名前、役職、電子メール、その他の詳細が含まれます。

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

ここでは、`InsertSignatureLine`メソッドは署名行を追加し、それに一意のプロバイダー ID を割り当てます。

## ステップ4: ドキュメントを保存する

署名欄を挿入したら、文書を保存しましょう。

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

これにより、新しく追加された署名行を含むドキュメントが保存されます。

## ステップ5: 署名オプションを設定する

次に、ドキュメントに署名するためのオプションを設定する必要があります。これには、署名行 ID、プロバイダー ID、コメント、署名時刻が含まれます。

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

ドキュメントに署名するには、PFX 証明書を使用します。そのための証明書ホルダーを作成しましょう。

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

必ず交換してください`"morzal.pfx"`実際の証明書ファイルと`"aw"`証明書のパスワードを入力します。

## ステップ7: 文書に署名する

最後に、デジタル署名ユーティリティを使用してドキュメントに署名します。

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

これにより、ドキュメントが署名され、新しいファイルとして保存されます。

## 結論

これで完了です。Aspose.Words for .NET を使用して、Word 文書に新しい署名欄を作成し、プロバイダー ID を設定できました。この強力なライブラリを使用すると、文書処理タスクの管理と自動化が非常に簡単になります。ぜひ試して、ワークフローを効率化できるかどうかを確認してください。

## よくある質問

### 署名行の外観をカスタマイズできますか?
もちろんです！さまざまなオプションを調整できます`SignatureLineOptions`お客様のニーズに合わせて。

### PFX 証明書を持っていない場合はどうなりますか?
信頼できる証明機関から証明書を取得する必要があります。これは、ドキュメントにデジタル署名するために不可欠です。

### 文書に複数の署名行を追加できますか?
はい、さまざまなオプションで挿入プロセスを繰り返すことで、必要な数の署名行を追加できます。

### Aspose.Words for .NET は .NET Core と互換性がありますか?
はい、Aspose.Words for .NET は .NET Core をサポートしているため、さまざまな開発環境に柔軟に対応できます。

### デジタル署名はどれくらい安全ですか?
Aspose.Words で作成されたデジタル署名は、有効で信頼できる証明書を使用している限り、非常に安全です。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
