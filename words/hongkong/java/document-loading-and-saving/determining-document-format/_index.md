---
date: 2025-12-20
description: 了解如何在 Java 中使用 Aspose.Words 按類型組織檔案並偵測文件格式。支援 DOC、DOCX、RTF 等。
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: 使用 Aspose.Words for Java 按類型整理檔案
url: /zh-hant/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for Java 按類型組織檔案

當您需要在 Java 應用程式中**按類型組織檔案**時，第一步是可靠地確定每個文件的格式。Aspose.Words for Java 讓這變得簡單，能夠偵測 DOC、DOCX、RTF、HTML、ODT 以及許多其他格式——甚至是加密或未知的檔案。在本指南中，我們將說明如何設定資料夾、偵測檔案格式，並自動排序您的檔案。

## 快速解答
- **什麼是「按類型組織檔案」的意思？** 它指的是根據偵測到的格式（例如 DOCX、PDF、RTF）自動將文件移動到相應的資料夾。  
- **哪個函式庫可協助在 Java 中偵測檔案格式？** Aspose.Words for Java 提供 `FileFormatUtil.detectFileFormat()`。  
- **API 能辨識未知檔案類型嗎？** 能——它會回傳 `LoadFormat.UNKNOWN` 以表示不支援或無法辨識的檔案。  
- **是否支援加密文件的偵測？** 當然支援；`FileFormatInfo.isEncrypted()` 旗標會告訴您檔案是否受密碼保護。  
- **生產環境是否需要授權？** 商業部署必須使用有效的 Aspose.Words 授權。

## 介紹：使用 Aspose.Words for Java 按類型組織檔案

在 Java 中處理文件時，確定所處理檔案的格式至關重要。Aspose.Words for Java 提供強大的功能以**detect file format java**，我們將帶您一步步有效地組織檔案。

## 前置條件

在開始之前，請確保您具備以下前置條件：

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)
- 已在系統上安裝 Java Development Kit (JDK)
- 具備基本的 Java 程式設計知識

## 步驟 1：目錄設定

首先，我們需要設定必要的目錄，以有效地組織檔案。我們將為不同的文件類型建立資料夾。

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Create the directories if they do not already exist.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

我們已建立支援、未知、加密以及 pre‑97 文件類型的資料夾。

## 步驟 2：偵測文件格式

現在，讓我們偵測目錄中文件的格式。我們將使用 Aspose.Words for Java 來完成此操作。

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Display the document type
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Add cases for other document formats as needed
    }

    // Handle encrypted documents
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Handle other document types
        switch (info.getLoadFormat()) {
            case LoadFormat.DOC_PRE_WORD_60:
                FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                break;
            case LoadFormat.UNKNOWN:
                FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                break;
            default:
                FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                break;
        }
    }
}
```

在此程式碼片段中，我們會遍歷檔案，**detect file format java**，並將它們組織到相應的資料夾中。

## 完整來源程式碼：在 Aspose.Words for Java 中判斷文件格式

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Create the directories if they do not already exist.
        if (supportedDir.exists() == false)
            supportedDir.mkdir();
        if (unknownDir.exists() == false)
            unknownDir.mkdir();
        if (encryptedDir.exists() == false)
            encryptedDir.mkdir();
        if (pre97Dir.exists() == false)
            pre97Dir.mkdir();
        Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
                .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
                .map(File::getPath)
                .collect(Collectors.toSet());
        for (String fileName : listFiles) {
            String nameOnly = Paths.get(fileName).getFileName().toString();
            System.out.println(nameOnly);
            FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);
            // Display the document type
            switch (info.getLoadFormat()) {
                case LoadFormat.DOC:
                    System.out.println("\tMicrosoft Word 97-2003 document.");
                    break;
                case LoadFormat.DOT:
                    System.out.println("\tMicrosoft Word 97-2003 template.");
                    break;
                case LoadFormat.DOCX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Document.");
                    break;
                case LoadFormat.DOCM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
                    break;
                case LoadFormat.DOTX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Template.");
                    break;
                case LoadFormat.DOTM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
                    break;
                case LoadFormat.FLAT_OPC:
                    System.out.println("\tFlat OPC document.");
                    break;
                case LoadFormat.RTF:
                    System.out.println("\tRTF format.");
                    break;
                case LoadFormat.WORD_ML:
                    System.out.println("\tMicrosoft Word 2003 WordprocessingML format.");
                    break;
                case LoadFormat.HTML:
                    System.out.println("\tHTML format.");
                    break;
                case LoadFormat.MHTML:
                    System.out.println("\tMHTML (Web archive) format.");
                    break;
                case LoadFormat.ODT:
                    System.out.println("\tOpenDocument Text.");
                    break;
                case LoadFormat.OTT:
                    System.out.println("\tOpenDocument Text Template.");
                    break;
                case LoadFormat.DOC_PRE_WORD_60:
                    System.out.println("\tMS Word 6 or Word 95 format.");
                    break;
                case LoadFormat.UNKNOWN:
                    System.out.println("\tUnknown format.");
                    break;
            }
            if (info.isEncrypted()) {
                System.out.println("\tAn encrypted document.");
                FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
            } else {
                switch (info.getLoadFormat()) {
                    case LoadFormat.DOC_PRE_WORD_60:
                        FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                        break;
                    case LoadFormat.UNKNOWN:
                        FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                        break;
                    default:
                        FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                        break;
                }
            }
        }

```

## 如何偵測檔案格式 Java

`FileFormatUtil.detectFileFormat()` 方法會檢查檔案標頭，並回傳 `FileFormatInfo` 物件。此物件會告訴您 **load format**、檔案是否加密以及其他有用的中繼資料。利用這些資訊，您可以以程式方式 **identify unknown file types**，並決定如何處理每個檔案。

## 辨識未知檔案類型

當 API 回傳 `LoadFormat.UNKNOWN` 時，表示該檔案可能已損毀或使用 Aspose.Words 不支援的格式。在我們的範例程式碼中，我們會將這些檔案移至 **Unknown** 資料夾，以便您稍後檢查。

## 常見問題與解決方案

| Issue | Reason | Fix |
|-------|--------|-----|
| 檔案總是被放入 *Supported* 資料夾 | `FileFormatUtil` 無法讀取標頭（例如，檔案為空） | 請確保傳入正確的檔案路徑，且檔案不是零位元組。 |
| 加密檔案拋出例外 | 在未處理加密的情況下嘗試讀取 | 在進一步處理前使用 `info.isEncrypted()` 檢查，如程式碼所示。 |
| Pre‑97 Word 文件未被偵測 | 舊格式需要 `DOC_PRE_WORD_60` 情況 | 保留 `case LoadFormat.DOC_PRE_WORD_60` 區塊，以將其導向 *Pre97* 資料夾。 |

## 常見問答

### 如何安裝 Aspose.Words for Java？

您可以從[此處](https://releases.aspose.com/words/java/)下載 Aspose.Words for Java，並依照提供的安裝說明進行。

### 支援哪些文件格式？

Aspose.Words for Java 支援多種文件格式，包括 DOC、DOCX、RTF、HTML、ODT 等等。完整清單請參考官方文件。

### 如何使用 Aspose.Words for Java 偵測加密文件？

使用 `FileFormatUtil.detectFileFormat()` 方法；回傳的 `FileFormatInfo.isEncrypted()` 旗標會指示是否加密，如本指南所示。

### 使用舊文件格式時有什麼限制嗎？

舊格式如 MS Word 6 或 Word 95 可能缺少現代功能，且可能有相容性問題。建議在可能的情況下將其轉換為較新格式。

### 我可以在 Java 應用程式中自動化文件格式偵測嗎？

可以，將提供的程式碼嵌入您的應用程式處理流程中，即可根據偵測到的格式自動排序與處理。

---

**最後更新：** 2025-12-20  
**測試環境：** Aspose.Words for Java 24.12 (latest)  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}