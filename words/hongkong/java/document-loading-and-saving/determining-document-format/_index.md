---
date: 2026-02-22
description: 學習如何使用 Aspose.Words 在 Java 中偵測文件格式，並自動依格式搬移檔案。識別 DOC、DOCX 等等。
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: 使用 Aspose.Words for Java 檢測文件格式
url: /zh-hant/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for Java 偵測文件格式 (Java)

當您需要在大量檔案中 **detect document format java** 時，能自動將它們分類至正確資料夾的功能可以節省數小時的手動工作。本文將示範如何利用 Aspose.Words for Java 輕鬆辨識 Word、RTF、HTML、ODT 以及其他多種格式，並 **依格式搬移檔案** 至有條理的目錄。

## 快速回答
- **「detect document format java」是什麼意思？** 這是指使用 Java 程式碼以程式化方式辨識檔案的文字處理格式（DOC、DOCX、RTF 等）。  
- **哪個函式庫提供此功能？** Aspose.Words for Java 提供 `FileFormatUtil.detectFileFormat` API。  
- **此工具能處理加密檔案嗎？** 能——`FileFormatInfo.isEncrypted()` 旗標會告訴您文件是否受密碼保護。  
- **正式環境需要授權嗎？** 商業版 Aspose.Words 授權是非評估部署的必要條件。  
- **偵測後能自動搬移檔案嗎？** 當然可以——將偵測結果與 `FileUtils.copyFile` 結合，即可將檔案排序至自訂資料夾。

## 什麼是 detect document format java？
`detect document format java` 指的是使用 Java 程式碼檢查檔案的二進位標頭，判斷其屬於哪種文字處理格式（例如 DOC、DOCX、ODT）。Aspose.Words 會在不完整載入文件的情況下讀取檔案，使操作快速且節省記憶體。

## 為什麼要依格式搬移檔案？
依原生格式整理文件可簡化後續處理：

- **批次轉換**：所有 DOCX 檔案集中於同一資料夾時，轉換工作變得直接。  
- **舊版支援**：可將 97 版以前的 Word 檔案隔離，進行特殊處理。  
- **安全性**：加密文件可自動隔離，降低風險。  

## 前置條件

在開始之前，請確保您已具備：

- [Aspose.Words for Java](https://releases.aspose.com/words/java/)（下載最新版本）  
- 已安裝 Java Development Kit (JDK) 8 以上  
- 具備基本的 Java I/O 與串流概念  

## 步驟 1：為每種格式建立資料夾

首先建立一個乾淨的資料夾結構，供偵測後的檔案搬移使用。這樣可讓工作流程保持整潔，且日後若要加入新格式類別也很方便。

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

> **小技巧：** 使用絕對路徑或透過屬性檔設定基礎目錄，可避免在正式程式碼中硬編碼路徑。

## 步驟 2：偵測文件格式並搬移檔案

**detect document format java** 的核心邏輯位於下方迴圈。它會掃描每一個檔案、判斷類型，然後將檔案複製至對應的資料夾。

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

`switch` 區塊可依需求擴充，以涵蓋您關心的所有格式。每個 case 都會印出友善訊息，並將檔案搬至相符的資料夾。

## 完整範例程式碼：偵測文件格式 (Java)

以下提供可直接執行的完整範例，結合資料夾設定與偵測邏輯。將程式碼貼入 Java 類別、調整基礎路徑後，即可對混合文件資料夾進行測試。

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

## 常見問題與除錯

| 問題 | 為何會發生 | 解決方式 |
|------|------------|----------|
| **`FileFormatUtil.detectFileFormat` 回傳 `UNKNOWN`** | 檔案損毀或屬於非 Word 類型。 | 檢查檔案副檔名，或加入備援機制將其搬至 *Unknown* 資料夾（範例已示）。 |
| **加密檔案拋出例外** | API 在檢查加密前嘗試讀取內容。 | 在對文件執行其他操作前，先呼叫 `info.isEncrypted()`。 |
| **Linux 上建立資料夾失敗** | 權限不足或缺少上層資料夾。 | 確認 Java 進程具寫入權限，且基礎路徑已存在。 |

## 常見問答

**Q: 如何安裝 Aspose.Words for Java？**  
A: 前往 [此處](https://releases.aspose.com/words/java/) 下載 Aspose.Words for Java，並依照提供的安裝說明操作。

**Q: 支援偵測哪些文件格式？**  
A: Aspose.Words 可偵測 DOC、DOCX、DOT、DOTX、DOCM、DOTM、RTF、HTML、MHTML、ODT、OTT、FLAT_OPC、WORD_ML，以及早期的 pre‑97 格式等多種類型。

**Q: 這段程式碼能處理受密碼保護的文件嗎？**  
A: 能。`FileFormatInfo.isEncrypted()` 旗標會辨識加密檔案，讓您在不開啟文件的情況下將其搬至安全資料夾。

**Q: 大量資料夾掃描會不會影響效能？**  
A: 偵測僅讀取檔案標頭，即使處理上千個檔案也相當快速。若批次極大，可考慮使用平行串流 (parallel streams)。  

**Q: 如何擴充腳本以轉換不支援的格式？**  
A: 偵測完畢後，可呼叫 `Document.save` 並指定目標格式，對任何支援的來源類型進行轉換。

## 結論

透過 **detect document format java** 搭配 Aspose.Words，您可以可靠地自動分類、隔離或轉換與 Word 相關的檔案。範例程式碼示範了如何建立清晰的資料夾層級、辨識每個檔案的格式，並依結果搬移檔案，從而節省時間、降低人工錯誤。

---

**最後更新：** 2026-02-22  
**測試環境：** Aspose.Words for Java 24.12（最新）  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}