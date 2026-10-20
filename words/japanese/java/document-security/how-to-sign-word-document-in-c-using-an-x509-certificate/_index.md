---
category: general
date: 2026-08-20
description: 契約書類にデジタル署名でWord文書に署名する方法を学びましょう。このガイドでは、PFXからx509証明書を読み込み、署名を作成する手順を解説しています。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- sign word document
- load x509 certificate
- digital signature for contract
- how to sign document
- load certificate from pfx
language: ja
lastmod: 2026-08-20
og_description: 契約書類用にWord文書にデジタル署名を付けます。PFXから証明書を読み込み、XAdES EPES署名を作成する手順をステップバイステップでご案内します。
og_image_alt: Diagram showing how to sign word document using an X509 certificate
og_title: C#でWord文書に署名 – X509証明書をロードしてデジタル署名を適用
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to sign word document with a digital signature for contract
    files. This guide covers loading x509 certificate from a PFX and creating the
    signature.
  headline: How to sign word document in C# using an X509 certificate
  type: TechArticle
tags:
- digital signature
- C#
- X509Certificate2
title: C#でX509証明書を使用してWord文書に署名する方法
url: /ja/java/document-security/how-to-sign-word-document-in-c-using-an-x509-certificate/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# で X509 証明書を使用して Word 文書に署名する方法

プログラムで **Word 文書に署名** する必要がある場合、このチュートリアルでは完全な、すぐに実行できるソリューションを示します。**x509 証明書をロード**する方法（*.pfx* ファイルから）、署名レベルの設定方法、そして契約書に添付できる標準準拠の XML 署名の生成方法を学びます。

以下の手順は .NET 6+ と無料の GroupDocs.Signature for .NET ライブラリで動作します。このライブラリは低レベルの XML‑DSig の詳細を抽象化しつつ、署名プロセスを完全に制御できるようにします。

## 前提条件

- .NET 6 SDK 以降がインストールされていること  
- Visual Studio 2022（または .NET をサポートする任意の IDE）  
- **PFX** 形式の有効な X509 証明書（`certificate.pfx`）と既知のパスワード  
- NuGet パッケージ `GroupDocs.Signature`（`dotnet add package GroupDocs.Signature` でインストール）  

> **なぜこれらの前提条件が必要か？**  
> `X509Certificate2` クラスは、プライベートキーがエクスポート可能な場合にのみ PFX を読み取ることができ、GroupDocs.Signature は多くの **契約用デジタル署名** シナリオで必要とされる XAdES EPES レベルを処理します。

## 手順 1: 署名証明書のロード（x509 証明書のロード）

```csharp
using System.Security.Cryptography.X509Certificates;

// Replace with the actual path to your PFX file and its password
string certPath = @"C:\Certificates\certificate.pfx";
string certPassword = "yourPassword";

// Load the certificate that contains the private key
X509Certificate2 certificate = new X509Certificate2(certPath, certPassword,
    X509KeyStorageFlags.MachineKeySet | X509KeyStorageFlags.PersistKeySet);
```

**説明**  
`X509Certificate2` は **pfx から証明書をロード** し、署名に使用できるプライベートキーを取得します。フラグはキーをマシンストアに保存することを保証し、Windows サービスでの権限問題を回避します。

**プロ・ティップ:** キーへのアクセスに関する `CryptographicException` が発生した場合、コードを実行しているアカウントが PFX ファイルに対して読み取り権限を持っていること、そしてキーがエクスポート可能としてマークされていることを確認してください。

## 手順 2: SignatureHelper の初期化と証明書の割り当て

```csharp
using GroupDocs.Signature;
using GroupDocs.Signature.Options;

// Create the helper that will perform the signing
SignatureHelper signer = new SignatureHelper();

// Attach the previously loaded certificate
signer.SetCertificate(certificate);
```

**説明**  
`SignatureHelper` は GroupDocs.Signature の薄いラッパーで、ワークフローを簡素化します。`SetCertificate` を呼び出すことで、ライブラリに **ドキュメントの署名方法** 操作で使用するプライベートキーを指定します。

## 手順 3: XAdES 署名レベルの選択（契約用デジタル署名）

```csharp
// XAdES_EPES is commonly required for contract signing because it embeds
// the signing certificate and timestamp information directly in the XML.
signer.SetXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

**説明**  
XAdES‑EPES（Explicit Policy‑Based Electronic Signature）は、**契約用デジタル署名** の多くの法的要件を満たします。ライブラリは必要な `<QualifyingProperties>` 要素を自動的に作成します。

## 手順 4: 署名対象の Word 文書をロード

```csharp
using GroupDocs.Signature.Domain;

// The document you want to sign – a .docx contract, for example
string docPath = @"C:\Contracts\contract.docx";
Document document = new Document(docPath);
```

**説明**  
`Document` はメモリ上の Word ファイルを表します。任意の `.docx` ファイルを使用でき、ファイル拡張子を変更すれば同じコードが PDF や他の OpenXML フォーマットでも動作します。

## 手順 5: XML 署名ファイルの生成

```csharp
// Destination for the generated XML signature
string signaturePath = @"C:\Contracts\signature.xml";

// Perform the signing operation
signer.SignDocument(document, signaturePath);

// Optional: verify that the file was created
if (System.IO.File.Exists(signaturePath))
{
    Console.WriteLine($"Signature saved to: {signaturePath}");
}
```

**説明**  
`SignDocument` は XAdES EPES プロファイルに準拠した XML ファイルを作成します。生成された `signature.xml` は元の Word ファイルと一緒に送信するか、後でカスタム XML パートを使用して埋め込むことができます。

**期待される出力**

```
Signature saved to: C:\Contracts\signature.xml
```

XML ファイルには `<Signature>`、`<SignedInfo>`、`<X509Data>` などの要素が含まれ、ロードされた **x509 証明書のロード** を参照します。

## 完全な実行可能サンプル

```csharp
using System;
using System.Security.Cryptography.X509Certificates;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;

class Program
{
    static void Main()
    {
        // 1. Load the signing certificate (load x509 certificate)
        string certPath = @"C:\Certificates\certificate.pfx";
        string certPassword = "yourPassword";
        X509Certificate2 certificate = new X509Certificate2(certPath, certPassword,
            X509KeyStorageFlags.MachineKeySet | X509KeyStorageFlags.PersistKeySet);

        // 2. Initialize the SignatureHelper and assign the certificate
        SignatureHelper signer = new SignatureHelper();
        signer.SetCertificate(certificate);

        // 3. Set the XAdES signature level (digital signature for contract)
        signer.SetXmlDsigLevel(XmlDsigLevel.XAdES_EPES);

        // 4. Load the Word document that will be signed
        string docPath = @"C:\Contracts\contract.docx";
        Document document = new Document(docPath);

        // 5. Generate the XML signature file
        string signaturePath = @"C:\Contracts\signature.xml";
        signer.SignDocument(document, signaturePath);

        // Confirmation
        Console.WriteLine(File.Exists(signaturePath)
            ? $"Signature saved to: {signaturePath}"
            : "Failed to create signature file.");
    }
}
```

ファイルを `Program.cs` として保存し、`dotnet run` を実行すると、法的検証に使用できる署名済み XML ファイルが取得できます。

## 一般的なバリエーションとエッジケース

| シナリオ | 変更点 | 理由 |
|----------|----------------|-----|
| **Word の代わりに PDF に署名** | `Document` を `PdfDocument` に置き換え、ファイル拡張子を変更します。 | GroupDocs.Signature は複数のフォーマットをサポートしており、署名フローは同一です。 |
| **Windows ストアから証明書を使用** | PFX ファイルの代わりに `X509Store` を使用して証明書をロードします。 | コンプライアンス上、プライベートキーがマシンから出ないようにしたい場合に有用です。 |
| **タイムスタンプの追加** | `signer.SetTimestampProvider(new Rfc3161TimestampProvider(url))` を呼び出します。 | 多くの契約ワークフローでは、署名が適用された時点を証明するために信頼できるタイムスタンプが必要です。 |
| **.docx 内への署名埋め込み** | `signer.SignDocument(document, signaturePath, new XmlSignatureOptions { EmbedIntoDocument = true })` を使用します。 | 埋め込むことで、1 つのファイルだけで配布できるため、配布が簡素化されます。 |

## 本番環境での使用に関するヒント

- **PFX の保護** – ファイルシステムではなく Azure Key Vault や AWS Secrets Manager に保存します。  
- **証明書チェーンの検証** – 署名前にチェーンを検証し、署名者が信頼できることを確認します。  
- **署名操作のログ記録**（証明書のサムプリント、ドキュメントハッシュ、タイムスタンプ） – ほとんどの **契約用デジタル署名** ポリシーで求められる監査証跡のために記録します。  

## 結論

これで、プログラムで **Word 文書に署名** する方法、PFX ファイルから **x509 証明書をロード** する方法、そして標準準拠の **契約用デジタル署名** ファイルを生成する方法が分かりました。この例は、証明書のロードから署名生成までの **ドキュメントの署名方法** 全体のワークフローをカバーし、実際のプロジェクトで遭遇する可能性のある一般的なバリエーションも含んでいます。

**次のステップ**

- 長期的な有効性のために XAdES‑T や XAdES‑LT などの他の署名レベルを調査する。  
- `EmbedIntoDocument` オプションを使用して、XML 署名を Word ファイルに直接埋め込んでみる。  
- 受信した契約書の署名を確認するために検証ロジック（`signer.VerifyDocument`）を統合する。

コードを自分のプロジェクト構成に合わせて自由に調整し、署名を楽しんでください！

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説付きの完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Word 文書のデジタル署名を検出](/words/english/net/programming-with-fileformat/detect-document-signatures/)
- [Word 文書の署名へのアクセスと検証](/words/english/net/programming-with-digital-signatures/access-and-verify-signature/)
- [Word 文書の既存署名行に署名](/words/english/net/programming-with-digital-signatures/signing-existing-signature-line/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}