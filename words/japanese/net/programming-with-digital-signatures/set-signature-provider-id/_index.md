---
title: Word 文書に署名プロバイダー ID を設定する
linktitle: Word 文書に署名プロバイダー ID を設定する
second_title: Aspose.Words ドキュメント処理 API
description: Aspose.Words for .NET を使用して、Word 文書に署名プロバイダー ID を安全に設定します。文書にデジタル署名するには、2,000 語の詳細なガイドに従ってください。
weight: 10
url: /ja/net/programming-with-digital-signatures/set-signature-provider-id/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word 文書に署名プロバイダー ID を設定する

## 導入

こんにちは。デジタル署名が必要な素晴らしい Word 文書をお持ちですね。ただし、署名は何でもいいわけではありません。特定の署名プロバイダー ID を設定する必要があります。法的文書、契約書、その他の書類を扱う場合、安全なデジタル署名を追加することは非常に重要です。このチュートリアルでは、Aspose.Words for .NET を使用して Word 文書に署名プロバイダー ID を設定するプロセス全体を説明します。準備はできましたか? 早速始めましょう。

## 前提条件

始める前に、以下のものを用意してください。

1. Aspose.Words for .NET ライブラリ: まだお持ちでない場合は、[ここからダウンロード](https://releases.aspose.com/words/net/).
2. 開発環境: Visual Studio または C# 互換の IDE。
3. Word文書:署名欄のある文書（`Signature line.docx`）。
4. デジタル証明書: A`.pfx`証明書ファイル（例：`morzal.pfx`）。
5. C# の基礎知識: 基本的な知識だけです。心配しないでください。私たちがお手伝いします!

さあ、アクションに飛び込みましょう！

## 名前空間のインポート

まず最初に、プロジェクトに必要な名前空間が含まれていることを確認します。これは、Aspose.Words ライブラリと関連クラスにアクセスするために不可欠です。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.DigitalSignatures;
```

さて、これをシンプルで理解しやすいステップに分解してみましょう。

## ステップ1: Word文書を読み込む

最初のステップは、署名行を含む Word 文書を読み込むことです。この文書は、指定された署名プロバイダー ID を持つデジタル署名を含むように変更されます。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Signature line.docx");
```

ここでは、ドキュメントが保存されているディレクトリを指定します。`"YOUR DOCUMENT DIRECTORY"`ドキュメントへの実際のパスを入力します。

## ステップ2: 署名欄にアクセスする

次に、文書内の署名欄にアクセスする必要があります。署名欄は、Word 文書に図形オブジェクトとして埋め込まれています。

```csharp
SignatureLine signatureLine = ((Shape)doc.FirstSection.Body.GetChild(NodeType.Shape, 0, true)).SignatureLine;
```

このコード行は、ドキュメントの最初のセクションの本文の最初の図形を取得し、それを`SignatureLine`物体。

## ステップ3: サインオプションを設定する

ここで、アクセスされた署名行のプロバイダー ID と署名行 ID を含む署名オプションを作成します。

```csharp
SignOptions signOptions = new SignOptions
{
    ProviderId = signatureLine.ProviderId,
    SignatureLineId = signatureLine.Id
};
```

これらのオプションは、ドキュメントに署名するときに、正しい署名プロバイダー ID が設定されていることを確認するために使用されます。

## ステップ4: 証明書を読み込む

文書にデジタル署名するには、証明書が必要です。`.pfx`ファイル：

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

交換する`"aw"`証明書ファイルにパスワードがある場合は、そのパスワードを入力します。

## ステップ5: 文書に署名する

最後に、`DigitalSignatureUtil.Sign`方法。

```csharp
DigitalSignatureUtil.Sign(dataDir + "Digitally signed.docx",
    dataDir + "SignDocuments.SetSignatureProviderId.docx", certHolder, signOptions);
```

これにより、文書に署名が付けられ、新しいファイルとして保存されます。`Digitally signed.docx`.

## 結論

これで完了です。Aspose.Words for .NET を使用して Word 文書に署名プロバイダー ID を設定することができました。このプロセスにより、文書が保護されるだけでなく、デジタル署名標準に準拠していることも保証されます。さあ、自分の文書で試してみてください。質問がありますか? 下記の FAQ を確認するか、[Aspose サポート フォーラム](https://forum.aspose.com/c/words/8).

## よくある質問

### 署名プロバイダー ID とは何ですか?

署名プロバイダー ID は、デジタル署名のプロバイダーを一意に識別し、信頼性とセキュリティを保証します。

### 署名には任意の .pfx ファイルを使用できますか?

はい、有効なデジタル証明書であれば可能です。保護されている場合は、正しいパスワードを入力してください。

### .pfx ファイルを取得するにはどうすればよいですか?

.pfx ファイルは証明機関 (CA) から取得するか、OpenSSL などのツールを使用して生成できます。

### 一度に複数の文書に署名できますか?

はい、複数のドキュメントをループして、それぞれに同じ署名プロセスを適用できます。

### 文書に署名欄がない場合はどうなりますか?

まず署名行を挿入する必要があります。Aspose.Words には、プログラムで署名行を追加するメソッドが用意されています。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
