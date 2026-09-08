---
category: general
date: 2026-09-08
description: C#でデジタル署名のdocxワークフローを使用してWord文書に署名し、pfx証明書を読み込み、XAdES署名を作成する方法。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to sign word
- digital signature docx
- load pfx certificate
- digitally sign word
- create xades signature
language: ja
lastmod: 2026-09-08
og_description: デジタル署名 docx フローを使用して Word 文書に署名し、pfx 証明書をロードし、C# で XAdES 署名を作成する方法。完全な例をご覧ください。
og_image_alt: Screenshot showing a Word document signed with XAdES EPES digital signature
og_title: C#でXAdES EPESを使用してWord文書に署名する方法 – ステップバイステップガイド
schemas:
- author: GroupDocs
  dateModified: '2026-09-08'
  description: How to sign word documents using a digital signature docx workflow,
    load pfx certificate, and create XAdES signature in C#.
  headline: How to sign word documents with XAdES EPES in C#
  type: TechArticle
tags:
- digital-signature
- C#
- Word
- XAdES
title: C#でXAdES EPESを使用してWord文書に署名する方法
url: /ja/net/programming-with-digital-signatures/how-to-sign-word-documents-with-xades-epes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C#でXAdES EPESを使用してWord文書に署名する方法

If you need to **how to sign word** files programmatically, this guide shows you a complete, production‑ready solution. You’ll learn how to load a PFX certificate, configure a **digital signature docx**, and create an XAdES‑EPES signature that can be verified by Microsoft Word and third‑party validators.

この例では GroupDocs.Signature for .NET ライブラリを使用していますが、概念は XAdES をサポートする任意の API に適用できます。チュートリアルの最後までに、配布用に準備された署名済みの `Signed_XAdES_EPES.docx` が手に入ります。

## 必要なもの

- .NET 6.0 以降（コードは .NET Framework 4.7+ でも動作します）
- プライベートキーを含む有効な PFX 証明書ファイル（`.pfx`）
- PFX ファイルのパスワード
- 署名したい Word 文書（`.docx`）
- NuGet パッケージ **GroupDocs.Signature**（`dotnet add package GroupDocs.Signature` でインストール）

## 手順 1: 必要な NuGet パッケージをインストールする

```bash
dotnet add package GroupDocs.Signature
```

The package provides the `Document` class, `XadesSignatureOptions`, and helper types for creating a **digitally sign word** file.

このパッケージは `Document` クラス、`XadesSignatureOptions`、および **digitally sign word** ファイルを作成するためのヘルパー型を提供します。

## 手順 2: 署名されていない Word 文書を読み込む

```csharp
using GroupDocs.Signature;
using GroupDocs.Signature.Options;
using System;
using System.Security.Cryptography.X509Certificates;

...

// Load the original Word file (must be a .docx)
var documentPath = @"C:\Docs\Unsigned.docx";
Document document = new Document(documentPath);
```

Loading the document gives you an object model that you can manipulate before applying the signature.

文書を読み込むことで、署名を適用する前に操作できるオブジェクトモデルが取得できます。

## 手順 3: PFX 証明書を読み込む (load pfx certificate)

```csharp
// Load the certificate that holds the private key
var certPath = @"C:\Certificates\mycert.pfx";
var certPassword = "yourPassword";          // keep this secret!
X509Certificate2 certificate = new X509Certificate2(certPath, certPassword);
```

> **Pro tip:** 証明書が Windows の証明書ストアに保存されている場合、ファイルを読み込む代わりに `X509Store` で取得できます。`load pfx certificate` のアプローチは、Linux コンテナを含むあらゆるプラットフォームで動作します。

## 手順 4: （オプション）ビジュアル署名行を追加する

A visual cue helps recipients see where the signature appears in Word.

ビジュアルなヒントを追加すると、受信者は Word 内で署名が表示される位置を確認できます。

```csharp
// Create a signature line that will be displayed in the document
SignatureLine signatureLine = new SignatureLine(document);
signatureLine.Id = Guid.NewGuid().ToString();
signatureLine.Signer = "John Smith";
signatureLine.Title = "Approved";

// Append the line to the first paragraph of the first section
document.FirstSection.Body.FirstParagraph.AppendChild(signatureLine);
```

If you prefer an invisible signature, you can skip this step. The **digital signature docx** will still be cryptographically valid.

目に見えない署名を希望する場合は、この手順をスキップできます。**digital signature docx** は暗号的に有効なままです。

## 手順 5: XAdES‑EPES オプションを設定する (create xades signature)

```csharp
// Set up XAdES‑EPES options – this creates a “qualified” electronic signature
XadesSignatureOptions signOptions = new XadesSignatureOptions
{
    SignatureType = XadesSignatureType.XAdES_EPES,
    // Optional: add a custom signing reason or location
    Reason = "Document approval",
    Location = "New York, USA"
};
```

The `XadesSignatureType.XAdES_EPES` flag tells the library to embed the signature according to the EPES (Explicit Policy-based Electronic Signature) profile, which is widely accepted by EU e‑IDAS regulations.

`XadesSignatureType.XAdES_EPES` フラグは、ライブラリに対して EPES（Explicit Policy-based Electronic Signature）プロファイルに従って署名を埋め込むよう指示します。このプロファイルは EU の e‑IDAS 規則で広く受け入れられています。

## 手順 6: デジタル署名を適用する

```csharp
// Sign the document with the loaded certificate and options
document.DigitalSignatures.Sign(certificate, signOptions);
```

The `Sign` method performs all the cryptographic work: it hashes the document parts, creates the XML‑DSig structure, and inserts the XAdES envelope into the Word file.

`Sign` メソッドはすべての暗号処理を実行します。文書の各パーツをハッシュし、XML‑DSig 構造を作成し、XAdES エンベロープを Word ファイルに挿入します。

## 手順 7: 署名済み文書を保存する

```csharp
// Save the signed file – you can overwrite or create a new file
var signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
document.Save(signedPath);
Console.WriteLine($"Document signed and saved to: {signedPath}");
```

After saving, open `Signed_XAdES_EPES.docx` in Microsoft Word. You should see a signature line (if you added one) and a **digitally sign word** status bar indicating that the file is signed and the signature is valid.

保存後、Microsoft Word で `Signed_XAdES_EPES.docx` を開きます。署名行（追加した場合）が表示され、ファイルが署名され署名が有効であることを示す **digitally sign word** ステータスバーが表示されます。

## 完全な実行可能サンプル

Below is the complete program you can copy‑paste into a console application.

以下はコンソールアプリケーションにコピー＆ペーストできる完全なプログラムです。

```csharp
using System;
using System.Security.Cryptography.X509Certificates;
using GroupDocs.Signature;
using GroupDocs.Signature.Options;

namespace WordXadesSigner
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the unsigned Word document
            string docPath = @"C:\Docs\Unsigned.docx";
            Document document = new Document(docPath);

            // 2️⃣ Load the signing certificate (load pfx certificate)
            string pfxPath = @"C:\Certificates\mycert.pfx";
            string pfxPassword = "yourPassword";
            X509Certificate2 cert = new X509Certificate2(pfxPath, pfxPassword);

            // 3️⃣ (Optional) Add a visual signature line
            SignatureLine sigLine = new SignatureLine(document)
            {
                Id = Guid.NewGuid().ToString(),
                Signer = "John Smith",
                Title = "Approved"
            };
            document.FirstSection.Body.FirstParagraph.AppendChild(sigLine);

            // 4️⃣ Configure XAdES‑EPES options (create xades signature)
            XadesSignatureOptions xadesOptions = new XadesSignatureOptions
            {
                SignatureType = XadesSignatureType.XAdES_EPES,
                Reason = "Document approval",
                Location = "New York, USA"
            };

            // 5️⃣ Apply the digital signature (digitally sign word)
            document.DigitalSignatures.Sign(cert, xadesOptions);

            // 6️⃣ Save the signed document
            string signedPath = @"C:\Docs\Signed_XAdES_EPES.docx";
            document.Save(signedPath);

            Console.WriteLine($"Signed document saved to: {signedPath}");
        }
    }
}
```

### 期待される出力

```
Signed document saved to: C:\Docs\Signed_XAdES_EPES.docx
```

Opening the file in Word shows a green “Signed” banner and, if you added the visual line, the signature line appears at the location you specified.

Word でファイルを開くと緑色の “Signed” バナーが表示され、ビジュアルラインを追加した場合は、指定した位置に署名行が表示されます。

## よくある落とし穴の対処法

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| **証明書のパスワードが間違っています** | `X509Certificate2` コンストラクタが `CryptographicException` をスローします。 | パスワードを確認するか、セキュアなシークレットマネージャー（Azure Key Vault、AWS Secrets Manager）を使用してください。 |
| **Word が “Signature is invalid” と表示する** | 署名後に文書が変更されたか、署名ポリシーが欠如しています。 | ファイルが署名**後**に保存され、再度編集されていないことを確認してください。規制当局が要求する場合は、正しい XAdES ポリシーを埋め込んでください。 |
| **署名行が表示されない** | 文書が異なるセクションレイアウトを使用しています。 | `SignatureLine` を正しい段落に追加するか、追加する前に新しい段落を作成してください。 |
| **大きな文書でのパフォーマンス低下** | XAdES 署名はパッケージのすべての部分をハッシュします。 | `SignAsync` などのストリーミング API を使用するか、非常に大きなファイル（>50 MB）の場合はマシンリソースを増やしてください。 |

## ソリューションの拡張

- **Multiple signers** – 異なる証明書で `Sign` を繰り返し呼び出し、`SignatureId` を設定して各署名者を区別します。
- **Timestamping** – `XadesSignatureOptions` に `TimestampOptions` オブジェクトを追加して、信頼できるタイムスタンプを埋め込みます。
- **Custom policies** – 特定の標準に準拠するために、`XadesSignatureOptions.PolicyFilePath` で XML ポリシーファイルを指定します。

## 結論

これで、プログラムで **how to sign word** 文書に署名する方法、**load pfx certificate** の方法、そして GroupDocs.Signature を使用して **create xades signature** を作成する方法が分かりました。このチュートリアルでは、文書の読み込みから署名済み出力の保存までのすべての手順をカバーし、一般的なエッジケースに対する実用的なヒントも提供しました。  

次は、**digitally sign word** PDF のような関連トピックを探求したり、**digital signature docx** の検証を統合したり、**timestamp** サポートを追加して高度なコンプライアンス要件を満たすことを検討してください。署名を楽しんでください！

## 次に学ぶべきことは？

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを取り上げています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Detect Digital Signature on Word Document](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Signing Existing Signature Line In Word Document](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)
- [Access And Verify Signature In Word Document](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}