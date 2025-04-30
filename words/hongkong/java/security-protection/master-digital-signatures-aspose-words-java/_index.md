---
"date": "2025-03-28"
"description": "了解如何使用 Aspose.Words 將數位簽章功能無縫整合到您的 Java 應用程式中。本指南涵蓋載入、驗證、簽署和刪除數位簽章。"
"title": "使用 Aspose.Words 掌握 Java 中的數位簽章綜合指南"
"url": "/zh-hant/java/security-protection/master-digital-signatures-aspose-words-java/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# 使用 Aspose.Words API 掌握 Java 中的數位簽名

數位簽章對於安全文件處理、確保真實性和完整性至關重要。 Aspose.Words for Java 程式庫可以將數位簽章功能無縫整合到您的應用程式中。本綜合指南將指導您使用 Java 中的 Aspose.Words 載入、驗證、簽署和刪除數位簽章。

## 介紹

在當今數位化的世界中，文件安全比以往任何時候都更加重要。無論處理合約、報告或官方文件，確保其真實性至關重要。使用 Aspose.Words Java 函式庫，您可以有效地管理 Java 應用程式中的數位簽章。本指南將協助您掌握使用 Aspose.Words 處理數位簽名，包括載入和驗證現有簽名、簽署新文件以及在必要時刪除簽名。

**您將學到什麼：**
- 如何從文件和流加載數位簽章。
- 驗證數位簽章文件的技術。
- 在 Java 應用程式中新增和刪除數位簽章的步驟。
- 處理具有數位簽章的加密文件的最佳實踐。

讓我們深入了解開始所需的先決條件！

## 先決條件

要遵循本教程，您需要：

- **Java 開發工具包 (JDK)：** 確保您的系統上安裝了 JDK 8 或更高版本。
- **Aspose.Words函式庫：** 您將使用 Aspose.Words for Java 版本 25.3。
- **Maven 或 Gradle 建置工具：** 本指南包含 Maven 和 Gradle 使用者的依賴資訊。
- **對 Java I/O 操作的基本了解：** 熟悉 Java 中的文件處理至關重要。

## 設定 Aspose.Words

首先，確保您已設定必要的依賴項。以下是使用 Maven 或 Gradle 新增 Aspose.Words 的方法：

**Maven：**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle：**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### 許可證獲取

Aspose.Words 是一個商業庫，但您可以先免費試用或申請臨時許可證來探索其全部功能。

1. **免費試用：** 從以下位置下載 Aspose.Words JAR [這裡](https://releases.aspose.com/words/java/) 並將其包含在您的項目中。
2. **臨時執照：** 存取以下網址以取得完全存取權限的臨時許可證 [此連結](https://purchase。aspose.com/temporary-license/).
3. **購買：** 如需長期使用，請考慮從 [Aspose的購買頁面](https://purchase。aspose.com/buy).

### 基本初始化

設定好庫後，請在 Java 應用程式中初始化它：

```java
// 確保在獲得許可證後包含此行
com.aspose.words.License license = new com.aspose.words.License();
license.setLicense("path/to/your/license/file");
```

## 實施指南

本節針對您要實現的每個功能分為幾個邏輯步驟。

### 從檔案載入簽名

#### 概述

從文件載入數位簽章可確保文件自簽章以來未被變更。此步驟驗證文件是否經過數位簽署並有助於維護其完整性。

**步驟 1：導入所需的類**

```java
import com.aspose.words.DigitalSignatureCollection;
import com.aspose.words.DigitalSignatureUtil;
```

**步驟 2：從檔案路徑載入簽名**

```java
DigitalSignatureCollection digitalSignatures =
        DigitalSignatureUtil.loadSignatures("YOUR_DOCUMENT_DIRECTORY/Digitally signed.docx");

if (digitalSignatures.getCount() > 0) {
    System.out.println("Document is digitally signed.");
}
```

**解釋：** 這 `loadSignatures` 方法檢索指定文件中的所有簽章。收集的數量有助於確定是否存在任何簽名。

### 從串流中載入簽名

#### 概述

使用流加載簽章提供了靈活性，特別是在處理未儲存在磁碟上的文件時。

**步驟 1：導入所需的類**

```java
import java.io.FileInputStream;
import java.io.InputStream;
```

**步驟 2：建立輸入流並載入簽名**

```java
InputStream stream = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/Digitally signed.docx");
try {
    DigitalSignatureCollection digitalSignatures =
            DigitalSignatureUtil.loadSignatures(stream);

    if (digitalSignatures.getCount() > 0) {
        System.out.println("Document is digitally signed.");
    }
} finally {
    if (stream != null) stream.close();
}
```

**解釋：** 此方法示範如何透過 InputStream 讀取文檔，從而允許您處理來自各種來源的文件。

### 使用檔案路徑刪除所有簽名

#### 概述

撤銷先前的核准或修改文件內容時可能需要刪除數位簽章。

**步驟 1：導入所需類別**

```java
import com.aspose.words.DigitalSignatureUtil;
```

**第 2 步：使用 `removeAllSignatures` 方法**

```java
DigitalSignatureUtil.removeAllSignatures(
        "YOUR_DOCUMENT_DIRECTORY/Digitally signed.docx",
        "YOUR_OUTPUT_DIRECTORY/UnsignedDocument.docx");
```

**解釋：** 此命令清除指定文件中的所有數位簽章並將其儲存為新文件。

### 使用串流刪除所有簽名

#### 概述

對於需要基於流的處理的應用程序，透過 InputStream 和 OutputStream 刪除簽名會很有利。

**步驟 1：導入所需的類**

```java
import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.InputStream;
import java.io.OutputStream;
```

**步驟 2：使用串流刪除簽名**

```java
InputStream streamIn = new FileInputStream("YOUR_DOCUMENT_DIRECTORY/Digitally signed.docx");
try {
    OutputStream streamOut = new FileOutputStream(
            "YOUR_OUTPUT_DIRECTORY/UnsignedDocumentFromStream.docx");

    try {
        DigitalSignatureUtil.removeAllSignatures(streamIn, streamOut);
    } finally {
        if (streamOut != null) streamOut.close();
    }
} finally {
    if (streamIn != null) streamIn.close();
}
```

**解釋：** 這種方法允許您動態處理文檔，而無需直接存取文件系統。

### 簽署文件

#### 概述

對文件進行數位簽章對於驗證其來源和完整性至關重要。此步驟涉及使用以 PKCS#12 格式儲存的 X.509 憑證。

**步驟 1：導入所需的類**

```java
import com.aspose.words.CertificateHolder;
import com.aspose.words.DigitalSignatureUtil;
import com.aspose.words.SignOptions;
import java.util.Date;
```

**步驟 2：建立證書持有者並簽署文檔**

```java
CertificateHolder certificateHolder = CertificateHolder.create(
        "YOUR_DOCUMENT_DIRECTORY/morzal.pfx", "aw");

SignOptions signOptions = new SignOptions();
signOptions.setComments("My comment");
signOptions.setSignTime(new Date());

InputStream streamIn = new FileInputStream(
        "YOUR_DOCUMENT_DIRECTORY/Document.docx");
try {
    OutputStream streamOut = new FileOutputStream(
            "YOUR_OUTPUT_DIRECTORY/SignedDocument.docx");

    try {
        DigitalSignatureUtil.sign(streamIn, streamOut, certificateHolder, signOptions);
    } finally {
        if (streamOut != null) streamOut.close();
    }
} finally {
    if (streamIn != null) streamIn.close();
}
```

**解釋：** 這 `create` 方法從 PKCS#12 檔案初始化 CertificateHolder。 SignOptions 類別可讓您指定額外的簽名詳細資訊。

### 簽署加密文檔

#### 概述

簽署加密文件需要先解密，這可以透過在簽章選項中設定解密密碼來實現。

**步驟 1：導入所需的類**

```java
import com.aspose.words.CertificateHolder;
import com.aspose.words.DigitalSignatureUtil;
import com.aspose.words.SignOptions;
import java.util.Date;
```

**步驟2：使用解密密碼對加密文件進行簽名**

```java
CertificateHolder certificateHolder = CertificateHolder.create(
        "YOUR_DOCUMENT_DIRECTORY/morzal.pfx", "aw");

SignOptions signOptions = new SignOptions();
signOptions.setComments("My comment on encrypted document");
signOptions.setDecryptionPassword("your-password-here");
signOptions.setSignTime(new Date());

InputStream streamIn = new FileInputStream(
        "YOUR_DOCUMENT_DIRECTORY/EncryptedDocument.docx");
try {
    OutputStream streamOut = new FileOutputStream(
            "YOUR_OUTPUT_DIRECTORY/SignedEncryptedDocument.docx");

    try {
        DigitalSignatureUtil.sign(streamIn, streamOut, certificateHolder, signOptions);
    } finally {
        if (streamOut != null) streamOut.close();
    }
} finally {
    if (streamIn != null) streamIn.close();
}
```

**解釋：** 簽署加密文件時，在 `SignOptions` 允許 Aspose.Words 解密並簽署文件。

## 最佳實踐

- **保護您的憑證：** 始終保證證書的安全性並避免在代碼中硬編碼密碼。
- **版本相容性：** 透過徹底測試確保與不同版本的 Aspose.Words 相容。
- **錯誤處理：** 實作強大的錯誤處理來管理簽章過程中的異常。
- **測試：** 定期測試您的實施以確保可靠性和安全性。

透過遵循本指南，您可以使用 Aspose.Words 將數位簽章功能有效地整合到您的 Java 應用程式中。

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}