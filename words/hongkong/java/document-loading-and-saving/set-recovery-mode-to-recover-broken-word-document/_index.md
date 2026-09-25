---
category: general
date: 2026-02-15
description: 設定復原模式可讓您載入文件並進行復原，輕鬆修復損壞的 Word 文件及解決復原 Word 文件錯誤。
draft: false
keywords:
- set recovery mode
- recover broken word document
- load document with recovery
- recover word document errors
language: zh-hant
og_description: 設定復原模式是載入文件時使用復原的關鍵，讓您能在 Java 中修復損毀的 Word 文件錯誤。
og_title: 設定復原模式 – 快速修復損壞的 Word 文件
tags:
- Aspose.Words
- Java
- Document Recovery
title: 設定復原模式以修復損毀的 Word 文件
url: /zh-hant/java/document-loading-and-saving/set-recovery-mode-to-recover-broken-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 設定復原模式 – 使用 Aspose.Words 復原損毀的 Word 文件

有沒有試過打開一個突然無法載入的 Word 檔案？你可能正面對一個損毀的 *.docx*，並在想是否需要從頭開始。好消息是？Aspose.Words 中的 **set recovery mode** 為你提供了一種優雅的方式來 *load document with recovery*，並保留大部分內容。

在本教學中，你將學會如何正確 **set recovery mode**、為什麼 *RELAXED* 選項通常是損毀檔案的最佳選擇，以及如何處理偶爾仍會出現的 *recover word document errors*。不需要外部工具，只需純 Java 以及少量程式碼。

> **你將學到的內容：** 一個完整、可執行的範例，能載入損毀的 Word 檔案、跳過無法讀取的部分，並為你留下可用的 `Document` 物件，以便進一步處理。

---

## 前置條件

- **Aspose.Words for Java**（v24.9 或更新版本）已透過 Maven 或手動 JAR 加入你的專案。
- 一個你想測試的 **corrupted .docx** 檔案（我們稱之為 `Corrupted.docx`）。
- 基本的 Java 知識——不需要成為 Word 處理高手，只要對 `main` 方法熟悉即可。

如果缺少上述任何項目，請從[官方網站](https://products.aspose.com/words/java)取得最新的 Aspose.Words JAR，並將其加入 classpath。就這樣——不需要額外的相依性。

## 步驟 1：了解復原模式

| 模式 | 行為 | 何時使用 |
|------|----------|------------|
| **RELAXED** | 跳過無法讀取的部分，保留其餘內容。 | 大多數損毀檔案——你希望 **recover broken word document** 而不拋出例外。 |
| **STRICT** | 在任何錯誤時拋出例外。 | 當你需要保證完美、無錯誤的載入時（對於損毀來源而言較少見）。 |

> **專業提示：** *RELAXED* 是「只要拿回一些東西」情境的預設，而 *STRICT* 在必須在失敗時停止流程的自動化管線中很有用。

## 步驟 2：建立 `LoadOptions` 物件並 **set recovery mode**

這裡是關鍵字在程式碼中出現的地方。我們在載入檔案前，明確在 `LoadOptions` 實例上 **set recovery mode**。

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions and choose a recovery mode.
        // RELAXED will skip unreadable parts, while STRICT throws an exception.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // <-- set recovery mode

        // 2️⃣ Load the potentially corrupted document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 3️⃣ Verify that the document loaded and optionally save a cleaned copy.
        System.out.println("Document loaded successfully. Page count: " + doc.getPageCount());
        doc.save("Recovered.docx");
    }
}
```

**為什麼這很重要：** 透過呼叫 `setRecoveryMode`，你告訴 Aspose.Words 它應該多積極地嘗試拯救檔案。如果不這麼做，函式庫預設為 *STRICT*，會在首次發現問題時中止——這會破壞 *recover broken word document* 工作流程的目的。

## 步驟 3：驗證載入 – 我們真的 **recover broken word document** 了嗎？

載入後，你可以檢查 `Document` 物件：

```java
// Check if any sections were dropped
int sections = doc.getSections().getCount();
System.out.println("Sections recovered: " + sections);
```

如果主控台顯示合理的段落數量，表示你已成功 *load document with recovery*。實際上，你會發現大多數文字、表格與圖片都保留下來，而損毀的部分則會直接消失。

## 步驟 4：優雅地處理剩餘的 **recover word document errors**

即使使用 *RELAXED* 模式，仍有少數邊緣情況會拋出警告。將載入程式碼包在 try‑catch 中，以保持應用程式存活：

```java
try {
    Document doc = new Document("Corrupted.docx", loadOptions);
    // Continue processing...
} catch (Exception ex) {
    System.err.println("Recovery failed: " + ex.getMessage());
    // Optionally fallback to a backup copy or notify the user.
}
```

**什麼情況會發生？** 若檔案損毀到即使是寬鬆的解析器也無法辨識有效的文件結構，Aspose.Words 仍會拋出例外。在這些罕見情況下，你可能需要請使用者提供其他副本。

## 步驟 5：儲存復原後的檔案（可選）

大多數開發者希望有一個乾淨的版本交給下游系統。以下的 `save` 呼叫會寫入一個不再包含損毀片段的全新 `.docx`。

```java
doc.save("Recovered.docx");
System.out.println("Recovered file saved as Recovered.docx");
```

現在你擁有一個 **recover broken word document**，可在 Microsoft Word、Google Docs 或其他檢視器中開啟——不會出現錯誤對話框。

## 視覺概覽（圖片）

![顯示 set recovery mode 流程的圖表 – 從損毀檔案到復原文件](https://example.com/images/recovery-flow.png "set recovery mode 流程圖")

*此 alt 文字明確包含主要關鍵字，有助於搜尋引擎與螢幕閱讀器。*

## 常見問題與邊緣案例

| 問題 | 答案 |
|------|------|
| *如果我需要保留損毀部分以供鑑識分析呢？* | 使用 `LoadOptions.setRecoverMode(LoadOptions.RecoveryMode.STRICT)` 並捕捉例外。例外訊息會包含問題部分的詳細資訊。 |
| *我可以在執行時切換 RELAXED 與 STRICT 嗎？* | 當然可以——只要在每次載入前建立一個帶有所需模式的 `LoadOptions` 實例即可。 |
| *這能適用於較舊的 .doc 檔案嗎？* | 可以。相同的 `LoadOptions` 同時適用於 `.doc` 與 `.docx` 格式。 |
| *會有效能損失嗎？* | 幾乎沒有。額外的解析開銷相較於完整載入文件的成本可忽略不計。 |

## 完整可執行範例（可直接複製貼上）

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) {
        try {
            // Step 1 – configure recovery mode
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // set recovery mode

            // Step 2 – load the corrupted file
            Document doc = new Document("Corrupted.docx", loadOptions);

            // Step 3 – optional verification
            System.out.println("Loaded! Pages: " + doc.getPageCount());

            // Step 4 – save a clean copy
            doc.save("Recovered.docx");
            System.out.println("Saved recovered document as Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to recover document: " + e.getMessage());
        }
    }
}
```

執行程式，指向你的損毀檔案，並觀察輸出。若一切順利，你會看到列印出的頁數，且在來源檔旁出現全新的 `Recovered.docx`。

## 結論

我們已說明在 Aspose.Words 中 **set recovery mode** 的所有必要步驟，從選擇正確的 `RecoveryMode` 列舉到處理可能仍會出現的少數 *recover word document errors*。依照上述步驟，你可以可靠地 **load document with recovery**，保留損毀檔案的良好部分，並輸出可供任何下游處理的乾淨版本。

準備好接受下一個挑戰了嗎？試著將 **set recovery mode** 與 Aspose.Words 的 **document cleaning** API 結合——移除隱藏段落、修復損毀的超連結，甚至一次性將復原檔案轉換為 PDF。可能性無窮，而你現在已具備穩固的基礎，能直接應對損毀的 Word 檔案。

祝程式開發順利，願你的文件保持健康！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}