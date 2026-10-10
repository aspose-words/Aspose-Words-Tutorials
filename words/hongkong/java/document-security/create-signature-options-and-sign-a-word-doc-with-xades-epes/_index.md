---
category: general
date: 2026-10-10
description: 建立簽署選項並使用 XAdES EPES 於 Java 中簽署 Word 檔案。了解如何在幾個清晰步驟內使用憑證簽署 Office 文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create signature options
- sign word doc
- sign office document
- how to sign docx
language: zh-hant
lastmod: 2026-10-10
og_description: 在 Java 中使用 XAdES EPES 建立簽署選項並簽署 Word 文件。本指南將示範如何使用證書安全地簽署 Office 文件。
og_image_alt: Screenshot of Java code that creates signature options and signs a DOCX
  file
og_title: 建立簽署選項並使用 XAdES EPES 簽署 Word 文件
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
title: 建立簽署選項並使用 XAdES EPES 簽署 Word 文件
url: /zh-hant/java/document-security/create-signature-options-and-sign-a-word-doc-with-xades-epes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立簽章選項並使用 XAdES EPES 簽署 Word 文件

如果您需要為 DOCX 檔案 **建立簽章選項**，本指南將示範如何在 Java 中使用 XAdES‑EPES 級別簽署 Word 文件。您將獲得一個完整、可執行的範例，只需幾行程式碼即可使用 PFX 憑證簽署 Office 文件。

簽署 Office 文件是法律工作流程、合約自動化處理與安全文件交換的常見需求。在本教學中您將學習：

* 如何為 XAdES‑EPES 設定 `SignatureOptions`。
* 如何呼叫 `DigitalSignatureUtil.sign` 以 **簽署 Word 文件**。
* 如何處理常見的陷阱，例如憑證載入與密碼錯誤。

> **先決條件** – Java 17 或更新版本、GroupDocs.Signature for Java 函式庫（或相容的 XAdES 函式庫），以及有效的 `.pfx` 憑證檔案。

---

## 您需要的項目

| 項目 | 原因 |
|------|--------|
| Java 17+ | 現代語言功能與更佳的安全 API |
| GroupDocs.Signature for Java (or equivalent) | 提供 `SignatureOptions`、`XmlDsigLevel` 與 `DigitalSignatureUtil` |
| A PFX certificate (`.pfx`) | 提供用於數位簽章的私鑰 |
| Password for the certificate | 用於解鎖私鑰的必要密碼 |
| An unsigned DOCX file (`Unsigned.docx`) | 您想要 **簽署 Office 文件** 的來源文件 |

Make sure the library JAR is on your classpath:

```bash
# Example using Maven
mvn dependency:copy -Dartifact=com.groupdocs:groupdocs-signature:23.3
```

---

## 步驟 1：匯入必要的類別

開始時匯入處理簽章與檔案 I/O 的類別。

```java
import com.groupdocs.signature.SignatureOptions;
import com.groupdocs.signature.XmlDsigLevel;
import com.groupdocs.signature.DigitalSignatureUtil;
import java.io.IOException;
```

這些匯入讓您能使用用於 **建立簽章選項** 的 API，並執行實際的簽署作業。

---

## 步驟 2：建立簽章選項

`SignatureOptions` 物件保存簽署過程所需的所有設定，例如簽章級別、視覺外觀與時間戳記設定。

```java
// Step 2: Create signature options
SignatureOptions signatureOptions = new SignatureOptions();
```

建立全新的 `SignatureOptions` 實例是 **如何簽署 docx** 檔案的第一步，因為它會將每個簽署請求彼此隔離，避免跨文件的副作用。

---

## 步驟 3：指定 XAdES EPES 簽章級別

XAdES‑EPES（Explicit Policy‑based Electronic Signature）是廣受接受的 Office 文件簽章政策。設定級別可告訴函式庫使用哪種加密配置檔。

```java
// Step 3: Specify the XAdES EPES signature level
signatureOptions.setXmlDsigLevel(XmlDsigLevel.XAdES_EPES);
```

為什麼選擇 XAdES‑EPES？它會將簽章政策直接嵌入簽章本身，使簽署的文件自包含，且符合多項電子簽章法規。

---

## 步驟 4：簽署 DOCX 檔案

現在呼叫 `DigitalSignatureUtil.sign`。此方法會讀取來源檔案、套用簽章，並寫入簽署後的輸出。

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

**背後發生了什麼？**  
1. 函式庫載入 `.pfx` 檔案，並使用提供的密碼抽取私鑰。  
2. 它建立符合 XAdES‑EPES 配置檔的 XML‑DSig 結構。  
3. 簽章被嵌入 DOCX 套件中，保留原始文件的版面配置。  

如果憑證密碼錯誤或檔案無法讀取，會拋出 `IOException`，您應依範例處理此例外。

---

## 步驟 5：驗證已簽署的文件（可選）

簽署完成後，您可能想確認簽章是否存在且有效。GroupDocs 提供驗證 API，但也可以使用 Microsoft Word 進行快速手動檢查：

1. 在 Word 中開啟 `SignedXades.docx`。  
2. 點選 **File → Info → View signatures**。  
3. Word 應顯示綠色勾勾，表示數位簽章有效。

使用函式庫的自動驗證如下所示：

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

執行驗證步驟可讓您以程式方式確保 **簽署 Office 文件** 成功。

---

## 完整、可執行的範例

將所有片段整合起來，以下是一個可自行複製、貼上並執行的自包含 Java 類別。

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

**預期輸出**

```
Document signed successfully: YOUR_DIRECTORY/SignedXades.docx
Signature verification succeeded.
```

若發生任何錯誤，主控台會顯示清晰的錯誤訊息，協助您排除憑證或檔案路徑相關問題。

---

## 常見問題與邊緣案例處理

| 問題 | 答案 |
|----------|--------|
| **我可以使用不同的簽章級別嗎？** | 可以。將 `XmlDsigLevel.XAdES_EPES` 替換為 `XAdES_BES`、`XAdES_T` 等，視合規需求而定。 |
| **如果我的憑證儲存在 keystore 而非 .pfx 檔案，該怎麼辦？** | 手動載入 `KeyStore`，抽取 `PrivateKey` 與 `Certificate`，再傳入接受 `KeyStore` 物件的 `sign` 重載方法。 |
| **如何加入可見的簽章圖像？** | 在呼叫 `sign` 前使用 `signatureOptions.setSignatureImage("path/to/image.png")`。 |
| **簽署過程是否為執行緒安全？** | `DigitalSignatureUtil.sign` 方法是無狀態的；只要每個執行緒使用自己的 `SignatureOptions` 實例，即可安全地在多執行緒環境中呼叫。 |
| **如果 DOCX 已包含現有簽章，會發生什麼？** | 函式庫會在簽章套件中新增一個條目，保留先前的簽章。若有需要，請確認簽章政策允許多重簽章。 |

---

## 提示與最佳實踐（E‑E‑A‑T）

* **專業提示：** 將憑證密碼儲存在安全保管庫（例如 Azure Key Vault），不要硬編碼在程式碼中。  
* **注意事項：** Windows (`\`) 與 Unix (`/`) 的檔案路徑分隔符不同。使用 `Paths.get(...)` 建立跨平台的路徑。  
* **效能：** 簽署大型 DOCX 檔案可能受 I/O 限制；若批次處理大量文件，考慮以串流方式讀取輸入檔案。  
* **合規性：** XAdES‑EPES 符合 EU eIDAS 法規；在選擇簽章級別前，請先確認本地法律需求。

---

## 結論

在本教學中，您學會了如何 **建立簽章選項** 並使用 Java 以 XAdES‑EPES 級別 **簽署 Word 文件**。完整範例涵蓋憑證載入、選項設定、簽署呼叫以及可選的驗證步驟，為您在生產環境中 **如何簽署 docx** 檔案提供即用的解決方案。

## 接下來您可以學習什麼？

以下教學與本指南所示技術密切相關，能進一步深化您的 API 使用技巧與實作方式，每篇皆提供完整可執行的程式碼範例與逐步說明，協助您在專案中靈活運用。

- [在 Java 中建立載入選項 – 偵測缺少字型與如何載入 DOCX](/words/english/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/)
- [在 Aspose.Words for Java 中使用文件選項與設定](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [如何在 Aspose.Words for Java 中於唯讀文件建立可編輯範圍](/words/english/java/security-protection/editable-ranges-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}