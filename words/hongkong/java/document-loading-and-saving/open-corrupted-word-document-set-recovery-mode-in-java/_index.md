---
category: general
date: 2026-05-26
description: 使用 Aspose.Words 在 Java 中開啟受損的 Word 檔案。了解如何設定復原模式，並可靠地修復受損的 Word 檔案。
draft: false
keywords:
- open corrupted word document
- set recovery mode
- how to recover corrupted word file
- Aspose.Words Java
- document recovery Java
language: zh-hant
og_description: 使用 Aspose.Words 在 Java 中開啟受損的 Word 文件。本指南說明如何設定復原模式，並有效修復受損的 Word
  檔案。
og_title: 開啟損壞的 Word 文件 – 在 Java 中設定復原模式
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  headline: Open Corrupted Word Document – Set Recovery Mode in Java
  type: TechArticle
- description: Open corrupted word document in Java with Aspose.Words. Learn how to
    set recovery mode and recover corrupted Word files reliably.
  name: Open Corrupted Word Document – Set Recovery Mode in Java
  steps:
  - name: Why each line matters
    text: '* **`LoadOptions loadOptions = new LoadOptions();`** – without this object
      Aspose.Words uses default recovery, which *rejects* corrupted files. Creating
      it gives you the hook to change that behavior. * **`setRecoveryMode(...)`**
      – this is the **set recovery mode** call that decides whether warnings '
  - name: 1. File Not Found
    text: 'If the path is wrong, `Document` throws a `FileNotFoundException`. Wrap
      the load in a try‑catch block and log a friendly message:'
  - name: 2. Irrecoverable Corruption
    text: Even with `RECOVER_WITH_WARNINGS`, some structures are beyond repair. In
      that case Aspose.Words still loads what it can, but you’ll see warnings like
      “Cannot read paragraph properties”. Pay attention to the console output; those
      warnings often point to missing sections that you may need to reconstru
  - name: 3. Large Files and Performance
    text: Recovery adds a small overhead because the library parses the file twice—once
      to detect issues, again to rebuild. For multi‑gigabyte documents, consider streaming
      the file or increasing the JVM heap (`-Xmx2g`) to avoid `OutOfMemoryError`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word
title: 開啟損毀的 Word 文件 – 在 Java 中設定復原模式
url: /zh-hant/java/document-loading-and-saving/open-corrupted-word-document-set-recovery-mode-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 開啟損毀的 Word 文件 – 在 Java 中設定復原模式

有沒有試過開啟損毀的 Word 文件，結果程式因例外而當機？你並不孤單——那些損壞的 .docx 檔案真的會讓人頭疼。好消息是 Aspose.Words for Java 提供了細緻的控制，讓你 **開啟損毀的 Word 文件** 時不會讓應用程式崩潰，甚至可以自行決定是顯示警告、靜默復原，或是直接拒絕。

在本教學中，我們將逐步說明完整流程：從建立正確的 `LoadOptions`、選擇適當的 **設定復原模式** 值，最後確認文件確實已載入。完成後，你將知道 **如何以程式方式復原損毀的 Word 檔案**，不需要手動複製貼上。

> **你需要的環境**  
> * Java 8 或更新版本（API 亦支援 Java 11）  
> * Aspose.Words for Java 23.9（或最新版本）  
> * 一個範例損毀的 .docx 檔案——如果手頭沒有，可將任何有效檔案重新命名來模擬損毀  

讓我們開始吧。

## 開啟損毀的 Word 文件 – 步驟概覽

以下是我們將實作的高階流程：

1. **建立 `LoadOptions`** – 這個物件告訴 Aspose.Words 在遇到問題時的行為。  
2. **設定復原模式** – 選擇 `RECOVER_WITH_WARNINGS`、`RECOVER_WITHOUT_WARNINGS` 或 `REJECT_CORRUPTED`。  
3. **使用已設定的選項載入文件**。  
4. **驗證** 載入是否成功（例如，印出頁數）。  

每個步驟都會詳細說明，並提供可直接複製貼上到 IDE 的程式碼片段。

## 為不同情境設定復原模式

Aspose.Words 在 `LoadOptions.RecoveryMode` 中定義了三種復原策略：

| 模式 | 行為說明 | 使用時機 |
|------|-----------|-------------|
| `RECOVER_WITH_WARNINGS` | 嘗試載入文件，並在主控台顯示任何問題的警告。 | 想要了解 *發生了什麼* 而不立即中止時。 |
| `RECOVER_WITHOUT_WARNINGS` | 靜默修復可修復的部分，且不顯示警告。 | 需要保持日誌乾淨的正式環境。 |
| `REJECT_CORRUPTED` | 一旦偵測到損毀即拋出例外。 | 必須快速失敗的嚴格驗證流程。 |

正確選擇模式即是 **設定復原模式** 的核心。在大多除錯情境下，`RECOVER_WITH_WARNINGS` 是最佳選擇，因為它會告訴你哪些部分被修復了。

## 使用 Aspose.Words 復原損毀的 Word 檔案

以下是一個 **完整、可執行的 Java 程式**，示範整個流程。只要將它放入 `RecoveryModeDemo.java`，調整路徑後執行即可。

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions – this controls recovery
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // -------------------------------------------------
        // Step 2: Choose the recovery behavior
        // -------------------------------------------------
        // Option A – show warnings (great for debugging)
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITH_WARNINGS);

        // Uncomment ONE of the alternatives below if you need a different behavior:
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RECOVER_WITHOUT_WARNINGS);
        // loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.REJECT_CORRUPTED);

        // -------------------------------------------------
        // Step 3: Load the potentially corrupted document
        // -------------------------------------------------
        // Replace the placeholder with the actual path to your .docx file
        String corruptedPath = "C:/temp/corrupted.docx";
        Document doc = new Document(corruptedPath, loadOptions);

        // -------------------------------------------------
        // Step 4: Verify that the document is usable
        // -------------------------------------------------
        System.out.println("Document loaded successfully!");
        System.out.println("Page count = " + doc.getPageCount());

        // Bonus: you can now save the repaired file if you wish
        doc.save("C:/temp/recovered.docx");
        System.out.println("Recovered file saved as recovered.docx");
    }
}
```

### 為什麼每一行都很重要

* **`LoadOptions loadOptions = new LoadOptions();`** – 若沒有這個物件，Aspose.Words 會使用預設的復原行為，預設會 *拒絕* 損毀的檔案。建立它即可掛鉤自訂行為。  
* **`setRecoveryMode(...)`** – 這就是 **設定復原模式** 的呼叫，決定警告是否顯示、是否隱藏，或是否拋出例外。  
* **`new Document(path, loadOptions);`** – 建構子接受我們剛剛配置好的 `LoadOptions`，因此程式庫從一開始就知道要如何處理損毀的檔案。  
* **`doc.getPageCount()`** – 快速的合理性檢查。如果文件成功載入並回傳頁數，代表你已成功 **如何復原損毀的 Word 檔案**。  
* **`doc.save(...)`** – 雖非必要，但相當實用；你可以將修復後的版本寫回磁碟，以便日後使用。

## 處理常見的邊緣案例

### 1. 找不到檔案

如果路徑錯誤，`Document` 會拋出 `FileNotFoundException`。將載入程式碼包在 try‑catch 區塊，並記錄友善訊息：

```java
try {
    Document doc = new Document(corruptedPath, loadOptions);
    // proceed...
} catch (FileNotFoundException e) {
    System.err.println("The file was not found: " + corruptedPath);
}
```

### 2. 無法復原的損毀

即使使用 `RECOVER_WITH_WARNINGS`，某些結構仍可能無法修復。此時 Aspose.Words 仍會載入可用的部分，但會在主控台顯示類似「Cannot read paragraph properties」的警告。請留意這些訊息，因為它們通常指向需要手動重建的遺失段落或區段。

### 3. 大檔案與效能

復原會產生少量額外開銷，因為程式庫會先檢測問題一次，再重建一次。對於多 GB 的文件，建議使用串流方式讀取，或提升 JVM 記憶體上限（例如 `-Xmx2g`），以避免 `OutOfMemoryError`。

## 專業小技巧 – 讓復原更穩健

* **將警告寫入檔案** – 把 `System.err` 重新導向至日誌系統，保留修復紀錄。  
* **復原後再次驗證** – 呼叫 `doc.updatePageLayout();` 後重新檢查頁數；有時版面會在修復斷裂區段後變更。  
* **批次自動復原** – 把示範程式包在迴圈中，處理整個資料夾的損毀檔案，並重複使用相同的 `LoadOptions`。

## 結論

現在你已完全掌握 **如何以 Aspose.Words for Java 復原損毀的 Word 檔案**。只要建立 `LoadOptions` 實例、將 **設定復原模式** 為符合情境的策略，然後以該選項載入文件，即可安全地 **開啟損毀的 Word 文件** 而不會讓應用程式崩潰。上方的範例程式碼是一個完整、即時可執行的解決方案，會印出頁數，甚至可以儲存清理過的副本。

接下來可以嘗試將復原模式改為 `RECOVER_WITHOUT_WARNINGS`，比較主控台輸出，或是實驗載入加密文件（需要透過密碼提供）。


## 相關教學

- [Aspose.Words Java：完整的 Word 文件處理指南](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [如何使用 Aspose.Words for Java 將 Word 轉換為 PDF](/words/english/java/document-converting/using-document-converting/)
- [如何使用 Aspose.Words for Java 比較兩個 Word 檔案](/words/english/java/document-manipulation/comparing-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}