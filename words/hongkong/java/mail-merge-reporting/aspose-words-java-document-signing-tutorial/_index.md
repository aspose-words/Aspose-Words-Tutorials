---
"date": "2025-03-28"
"description": "了解如何使用 Aspose.Words for Java 實現文件簽章自動化。本教學涵蓋設定環境、建立測試資料、新增簽名行以及對文件進行數位簽章。"
"title": "使用 Aspose.Words 實現 Java 文件簽章自動化綜合指南"
"url": "/zh-hant/java/mail-merge-reporting/aspose-words-java-document-signing-tutorial/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# 使用 Aspose.Words 在 Java 中自動進行文件簽章：綜合指南

## 介紹

在當今快節奏的商業世界中，高效的文件管理至關重要。自動建立和數位簽章文件可以節省時間並最大限度地減少錯誤。本教學將指導您使用 Aspose.Words for Java 為簽署者建立測試資料、新增簽名行以及對文件進行數位簽章。

**您將學到什麼：**
- 在 Java 專案中設定 Aspose.Words
- 使用 Java 建立測試簽署者數據
- 在 Word 文件中新增簽名行
- 使用數位證書對文件進行數位簽名

讓我們從準備您的開發環境開始！

## 先決條件

在深入學習本教學之前，請確保您的設定符合以下要求：

- **Java 開發工具包 (JDK)：** 版本 8 或更高版本。
- **整合開發環境（IDE）：** 例如 IntelliJ IDEA 或 Eclipse。
- **Java 版 Aspose.Words：** 該庫可以透過 Maven 或 Gradle 包含。

### 知識前提

對 Java 程式設計有基本的了解並熟悉處理文件和串流將會很有幫助。如果您是 Aspose 的新手，請不要擔心 - 我們將介紹基本知識。

## 設定 Aspose.Words

若要在您的專案中使用 Aspose.Words for Java，請依照下列步驟操作：

### Maven 依賴

將以下相依性新增至您的 `pom.xml` 文件：

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle 依賴

對於 Gradle 項目，請在您的 `build.gradle` 文件：

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### 許可證獲取

Aspose 提供不同的授權選項：

- **免費試用：** 下載免費試用版來測試其功能。
- **臨時執照：** 取得臨時許可證以用於評估目的。
- **購買：** 要獲得完全訪問權限，請從 Aspose 網站購買許可證。

確保您的專案配置了必要的依賴項和任何所需的許可證。此設定將允許您無縫利用 Aspose 強大的文件處理功能。

## 實施指南

我們將逐步介紹每個功能，從建立測試簽署者資料開始。

### 功能 1：為簽署者建立測試數據

#### 概述

此功能會產生具有唯一 ID、姓名、職位和影像的簽署者清單。這對於不使用真實資料測試文件簽章場景至關重要。

##### 步驟 1：設定 Java 類

建立一個名為 `SignPersonCreator` 並導入必要的庫：

```java
import java.io.ByteArrayOutputStream;
import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStream;
import java.util.ArrayList;
import java.util.UUID;

class DocumentHelper {
    public static byte[] getBytesFromStream(InputStream inputStream) throws IOException {
        int numRead; 
        byte[] buffer = new byte[1024]; 
        ByteArrayOutputStream baos = new ByteArrayOutputStream();

        while ((numRead = inputStream.read(buffer)) != -1) {
            baos.write(buffer, 0, numRead);
        }
        return baos.toByteArray();
    }
}

public class SignPersonCreator {
    private static ArrayList<SignPersonTestClass> gSignPersonList;

    public static void main(String[] args) throws IOException {
        createSignPersonData();
        System.out.println("Test data successfully added!");
    }

    private static void createSignPersonData() throws IOException {
        InputStream inputStream = new FileInputStream(YOUR_DOCUMENT_DIRECTORY + "Logo.jpg");

        gSignPersonList = new ArrayList<>();
        gSignPersonList.add(new SignPersonTestClass(UUID.randomUUID(), "Ron Williams", "Chief Executive Officer",
                DocumentHelper.getBytesFromStream(inputStream)));
        gSignPersonList.add(new SignPersonTestClass(UUID.randomUUID(), "Stephen Morse", "Head of Compliance",
                DocumentHelper.getBytesFromStream(inputStream)));
    }
}
```

##### 解釋

- **UUID：** 為每個簽名者產生一個唯一的識別碼。
- **取得位元組流：** 將圖像檔案轉換為位元組數組進行儲存。

### 功能 2：在文件中新增簽名行

#### 概述

此功能可在您的文件中新增簽名行，並將其與簽署者的詳細資訊關聯起來。

##### 步驟 1：建立 SignatureLineAdder 類

實施 `SignatureLineAdder` 類別如下：

```java
import com.aspose.words.*;

class SignatureLineAdder {
    public static void main(String[] args) throws Exception {
        String srcDocumentPath = YOUR_DOCUMENT_DIRECTORY + "Document.docx";
        String dstDocumentPath = YOUR_OUTPUT_DIRECTORY + "SignDocumentCustom.Sign.docx";
        
        SignPersonTestClass signPersonInfo = gSignPersonList.stream()
                .filter(x -> x.getName().equals("Ron Williams")).findFirst().orElse(null);

        if (signPersonInfo != null) {
            addSignatureLine(srcDocumentPath, dstDocumentPath, signPersonInfo);
            System.out.println("Signature line added successfully!");
        } else {
            System.out.println("Sign person does not exist, please check your parameters.");
        }
    }

    private static void addSignatureLine(final String srcDocumentPath, final String dstDocumentPath,
                                         final SignPersonTestClass signPersonInfo) throws Exception {
        Document document = new Document(srcDocumentPath);
        DocumentBuilder builder = new DocumentBuilder(document);

        SignatureLineOptions signatureLineOptions = new SignatureLineOptions();
        signatureLineOptions.setSigner(signPersonInfo.getName());
        signatureLineOptions.setSignerTitle(signPersonInfo.getPosition());

        SignatureLine signatureLine = builder.insertSignatureLine(signatureLineOptions).getSignatureLine();
        signatureLine.setId(String.valueOf(signPersonInfo.getPersonId()));

        builder.getDocument().save(dstDocumentPath);
    }
}
```

##### 解釋

- **簽名行選項：** 配置簽署者的姓名和職稱。
- **插入簽名行：** 在文件的目前遊標位置插入簽章行。

### 功能3：使用數位證書簽署文檔

#### 概述

此功能使用數位憑證對文件進行數位簽名，確保真實性和完整性。

##### 步驟 1：建立 DocumentSigner 類

實施 `DocumentSigner` 班級：

```java
import com.aspose.words.*;

class DocumentSigner {
    public static void main(String[] args) throws Exception {
        String srcDocumentPath = YOUR_DOCUMENT_DIRECTORY + "Document.docx";
        String dstDocumentPath = YOUR_OUTPUT_DIRECTORY + "SignDocumentCustom.Sign.docx";
        String certificatePath = YOUR_DOCUMENT_DIRECTORY + "morzal.pfx";
        String certificatePassword = "aw";

        SignPersonTestClass signPersonInfo = gSignPersonList.stream()
                .filter(x -> x.getName().equals("Ron Williams")).findFirst().orElse(null);

        if (signPersonInfo != null) {
            signDocument(srcDocumentPath, dstDocumentPath, signPersonInfo, certificatePath, certificatePassword);
            System.out.println("Document successfully signed!");
        } else {
            System.out.println("Sign person does not exist, please check your parameters.");
        }
    }

    private static void signDocument(final String srcDocumentPath, final String dstDocumentPath,
                                     final SignPersonTestClass signPersonInfo, final String certificatePath,
                                     final String certificatePassword) throws Exception {
        Document document = new Document(dstDocumentPath);

        CertificateHolder certificateHolder = CertificateHolder.create(certificatePath, certificatePassword);

        SignOptions signOptions = new SignOptions();
        signOptions.setSignatureLineId(String.valueOf(
            signPersonInfo.getPersonId()));

        document.sign(signOptions, certificateHolder);
    }
}
```

##### 解釋

- **證書持有人：** 表示用於簽署的數位憑證。
- **符號：** 使用指定的選項和憑證對文件進行簽署的方法。

## 結論

在本教學中，您學習如何使用 Aspose.Words 在 Java 中自動建立和簽署文件。透過遵循這些步驟，您可以簡化文件管理流程、增強安全性並確保資料完整性。為了進一步探索，請考慮深入了解 Aspose.Words 的更多進階功能。

**後續步驟：**
- 探索其他 Aspose.Words 功能，如郵件合併或報告產生。
- 查看 Aspose 文件以取得詳細指南和 API 參考。
- 嘗試 Aspose.Words 支援的不同文件格式。

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}