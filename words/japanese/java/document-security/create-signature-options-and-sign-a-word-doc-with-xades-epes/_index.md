---
category: general
date: 2026-10-10
description: JavaでXAdES EPESを使用して署名オプションを作成し、Word文書に署名します。数ステップで証明書を使って Office 文書に署名する方法を学びましょう。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create signature options
- sign word doc
- sign office document
- how to sign docx
language: ja
lastmod: 2026-10-10
og_description: JavaでXAdES EPESを使用して署名オプションを作成し、Word文書に署名します。このガイドでは、証明書を用いてオフィス文書に安全に署名する方法を示します。
og_image_alt: Screenshot of Java code that creates signature options and signs a DOCX
  file
og_title: 署名オプションを作成し、XAdES EPESでWord文書に署名する
schemas:
- author: GroupDocs
  dateModified: '2026-10-10'
  description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  headline: Create signature options and sign a Word doc with XAdES EPES
  type: TechArticle
- description: Create signature options and sign a Word doc using XAdES EPES in Java.
    Learn how to sign office document with a certificate in a few clear steps.
  name: Create signature options and sign a Word doc with XAdES EPES
  steps:
  - name: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
    text: The library loads the `.pfx` file and extracts the private key using the
      supplied password.
  - name: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
    text: It creates an XML‑DSig structure matching the XAdES‑EPES profile.
  - name: The signature is embedded into the DOCX package, preserving the original
      document layout.
    text: The signature is embedded into the DOCX package, preserving the original
      document layout.
  - name: Open `SignedXades.docx` in Word.
    text: Open `SignedXades.docx` in Word.
  - name: Click **File → Info → View signatures**.
    text: Click **File → Info → View signatures**.
  - name: Word should display a green checkmark indicating a valid digital signature.
    text: Word should display a green checkmark indicating a valid digital signature.
  type: HowTo
tags:
- digital signature
- Java
- XAdES
title: 署名オプションを作成し、XAdES EPESでWord文書に署名する
url: /ja/java/document-security/create-signature-options-and-sign-a-word-doc-with-xades-epes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 署名オプションを作成し、XAdES EPESでWord文書に署名する

DOCXファイルの**署名オプションを作成**する必要がある場合、このガイドではJavaでXAdES‑EPESレベルを使用してWord文書に署名する方法を示します。数行のコードでPFX証明書を使用してOffice文書に署名する完全な実行可能サンプルが得られます。

Office文書への署名は、法的ワークフロー、自動契約処理、セキュアな文書交換において一般的な要件です。このチュートリアルで学べることは次のとおりです：

* XAdES‑EPES用に `SignatureOptions` を設定する方法。
* `DigitalSignatureUtil.sign` を呼び出して **Word文書に署名** する方法。
* 証明書の読み込みやパスワードエラーなど、一般的な落とし穴への対処方法。

> **前提条件** – Java 17以降、GroupDocs.Signature for Java ライブラリ（または互換性のある XAdES ライブラリ）、および有効な `.pfx` 証明書ファイル。

## 必要なもの

| 項目 | 理由 |
|------|--------|
| Java 17+ | モダンな言語機能とより優れたセキュリティ API |
| GroupDocs.Signature for Java（または同等） | `SignatureOptions`、`XmlDsigLevel`、`DigitalSignatureUtil` を提供 |
| PFX 証明書（`.pfx`） | デジタル署名用のプライベートキーを提供 |
| 証明書のパスワード | プライベートキーのロックを解除するために必要 |
| 未署名の DOCX ファイル（`Unsigned.docx`） | **Office文書に署名** したい元のドキュメント |

ライブラリの JAR がクラスパスに含まれていることを確認してください：

```bash
# Example using Maven
mvn dependency:copy -Dartifact=com.groupdocs:groupdocs-signature:23.3
```

## 手順 1: 必要なクラスをインポートする

まず、署名とファイル I/O を処理するクラスをインポートします。

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import java.io.IOException;
```

これらのインポートにより、**署名オプションを作成**するための API と、実際の署名操作を実行するための API にアクセスできます。

## 手順 2: 署名オプションを作成する

`SignatureOptions` オブジェクトは、署名レベル、ビジュアル外観、タイムスタンプ設定など、署名プロセスに必要なすべての構成を保持します。

```java
// Step 2: Create signature options
SignatureOptions signatureOptions = new SignatureOptions();
```

新しい `SignatureOptions` インスタンスを作成することは、**docx に署名する方法** の最初のステップです。これにより各署名リクエストが分離され、ドキュメント間の副作用を防止します。

## 手順 3: XAdES EPES 署名レベルを指定する

XAdES‑EPES（Explicit Policy-based Electronic Signature）は、Office 文書の署名に広く受け入れられているポリシーです。レベルを設定することで、ライブラリに使用すべき暗号プロファイルを指示します。

```java
// Step 3: Specify the XAdES EPES signature level
signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

なぜ XAdES‑EPES なのか？ 署名ポリシーを署名に直接埋め込むことで、署名済み文書が自己完結型となり、多くの電子署名規制に準拠します。

## 手順 4: DOCX ファイルに署名する

次に `DigitalSignatureUtil.sign` を呼び出します。このメソッドはソースファイルを読み取り、署名を適用し、署名済みの出力を書き込みます。

```java
// Step 4: Sign the document using the provided certificate
try {
    DigitalSignatureUtil.sign(
        "YOUR_DIRECTORY/Unsigned.docx",   // input file
        "YOUR_DIRECTORY/SignedXades.docx", // output file
        "YOUR_DIRECTORY/mycert.pfx",      // certificate file
        "password",                       // certificate password
        signatureOptions                  // options configured above
    );
    System.out.println("Document signed successfully: SignedXades.docx");
} catch (IOException e) {
    System.err.println("Failed to sign the document: " + e.getMessage());
}
```

**内部で何が起きているか？**  
1. ライブラリは `.pfx` ファイルを読み込み、提供されたパスワードでプライベートキーを抽出します。  
2. XAdES‑EPES プロファイルに一致する XML‑DSig 構造を作成します。  
3. 署名は DOCX パッケージに埋め込まれ、元の文書レイアウトが保持されます。  

証明書のパスワードが間違っている、またはファイルが読み取れない場合、`IOException` がスローされます。示されているようにハンドルしてください。

## 手順 5: 署名済み文書を検証する（オプション）

署名後、署名が存在し有効であることを確認したい場合があります。GroupDocs は検証 API を提供していますが、Microsoft Word を使って手動で簡単に確認できます。

1. Word で `SignedXades.docx` を開く。  
2. **ファイル → 情報 → 署名の表示** をクリック。  
3. Word が緑のチェックマークを表示し、デジタル署名が有効であることを示します。

ライブラリを使用した自動検証は以下のようになります：

```java
import com.groupdocs.signature.VerificationResult;

VerificationResult result = DigitalSignatureUtil.verify(
    "YOUR_DIRECTORY/SignedXades.docx",
    signatureOptions
);

if (result.isSuccessful()) {
    System.out.println("Signature verification succeeded.");
} else {
    System.out.println("Signature verification failed: " + result.getErrorMessage());
}
```

検証ステップを実行することで、**Office文書への署名** が成功したことをプログラム上で確信できます。

## 完全な実行可能サンプル

すべての要素を組み合わせた、コピーして貼り付けて実行できる自己完結型の Java クラスを以下に示します。

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import com.groupdocs.signature.VerificationResult;
import java.io.IOException;

/**
 * Demonstrates how to create signature options and sign a DOCX file with XAdES EPES.
 */
public class XadesSignatureDemo {

    public static void main(String[] args) {
        // Paths – update these to match your environment
        String inputPath = "YOUR_DIRECTORY/Unsigned.docx";
        String outputPath = "YOUR_DIRECTORY/SignedXades.docx";
        String certPath = "YOUR_DIRECTORY/mycert.pfx";
        String certPassword = "password";

        // 1️⃣ Create signature options
        SignatureOptions signatureOptions = new SignatureOptions();

        // 2️⃣ Set XAdES EPES level
        signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);

        // 3️⃣ Sign the document
        try {
            DigitalSignatureUtil.sign(inputPath, outputPath, certPath, certPassword, signatureOptions);
            System.out.println("Document signed successfully: " + outputPath);
        } catch (IOException e) {
            System.err.println("Signing failed: " + e.getMessage());
            return;
        }

        // 4️⃣ (Optional) Verify the signature
        VerificationResult verification = DigitalSignatureUtil.verify(outputPath, signatureOptions);
        if (verification.isSuccessful()) {
            System.out.println("Signature verification succeeded.");
        } else {
            System.out.println("Signature verification failed: " + verification.getErrorMessage());
        }
    }
}
```

**期待される出力**

```
Document signed successfully: YOUR_DIRECTORY/SignedXades.docx
Signature verification succeeded.
```

何か問題が発生した場合、コンソールに明確なエラーメッセージが表示され、証明書やファイルパスの問題をトラブルシュートするのに役立ちます。

## よくある質問とエッジケースの対処

| 質問 | 回答 |
|----------|--------|
| **別の署名レベルを使用できますか？** | はい。コンプライアンス要件に応じて、`XmlDsigLevel.XAdES_EPES` を `XAdES_BES`、`XAdES_T` などに置き換えてください。 |
| **証明書が .pfx ファイルではなくキーストアに保存されている場合はどうすればよいですか？** | `KeyStore` を手動でロードし、`PrivateKey` と `Certificate` を抽出して、`KeyStore` オブジェクトを受け取る `sign` のオーバーロードに渡します。 |
| **可視署名画像を追加するにはどうすればよいですか？** | `sign` を呼び出す前に `signatureOptions.setSignatureImage("path/to/image.png")` を使用します。 |
| **署名プロセスはスレッドセーフですか？** | `DigitalSignatureUtil.sign` メソッドはステートレスです。各スレッドが独自の `SignatureOptions` インスタンスを使用すれば、複数スレッドから安全に呼び出せます。 |
| **DOCX に既存の署名が含まれている場合はどうなりますか？** | ライブラリは新しい署名パッケージエントリを追加し、以前の署名を保持します。必要に応じて、署名ポリシーが複数署名を許可しているか確認してください。 |

## ヒントとベストプラクティス (E‑E‑A‑T)

* **プロのコツ:** 証明書のパスワードはハードコーディングせず、セキュアなボールト（例: Azure Key Vault）に保存してください。  
* **注意点:** Windows のファイルパス区切り文字 (`\`) と Unix の (`/`) に注意してください。`Paths.get(...)` を使用してプラットフォームに依存しないパスを構築しましょう。  
* **パフォーマンス:** 大きな DOCX ファイルの署名は I/O がボトルネックになることがあります。バッチで多数の文書を処理する場合は、入力ファイルをストリーミングすることを検討してください。  
* **コンプライアンス:** XAdES‑EPES は EU の eIDAS 規則に準拠しています。署名レベルを選択する前に、ローカルの法的要件を確認してください。

## 結論

このチュートリアルでは、Java を使用して XAdES‑EPES レベルで **署名オプションを作成**し、**Word 文書に署名**する方法を学びました。完全なサンプルは証明書のロード、オプション設定、署名呼び出し、オプションの検証を網羅しており、実運用で **docx に署名する方法** のためのすぐに使えるソリューションを提供します。

## 次に学ぶべきことは？

以下のチュートリアルは、本ガイドで示した手法を基にした密接に関連するトピックを扱っています。各リソースには、ステップバイステップの解説と完全な動作コード例が含まれており、追加の API 機能を習得し、プロジェクトで代替実装アプローチを検討するのに役立ちます。

- [Java でロードオプションを作成 – フォント欠損の検出と DOCX のロード方法](/words/english/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/)
- [Aspose.Words for Java でのドキュメントオプションと設定の使用](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Aspose.Words for Java を使用して読み取り専用ドキュメントに編集可能範囲を作成する方法](/words/english/java/security-protection/editable-ranges-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}