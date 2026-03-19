---
category: general
date: 2026-03-19
description: 學習如何在 Aspose.Words for Java 中捕捉警告並偵測缺少的字型。此步驟指南亦示範如何優雅地處理缺少的字型。
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: zh-hant
og_description: 如何在 Aspose.Words for Java 中捕捉警告、偵測缺少的字型，並以完整程式碼範例處理缺少的字型。
og_title: 如何捕捉警告 – 偵測 Aspose.Words 中缺失的字型
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: 如何捕捉警告 – 偵測 Aspose.Words 中缺失的字型
url: /zh-hant/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何捕獲警告 – 偵測 Aspose.Words 中缺失的字型

有沒有想過 **如何捕獲警告**，當 Word 文件載入時機器上沒有某些字型？你並不孤單。在許多實務專案中，缺失的字型會導致靜默的版面移位，而唯一能得知發生了什麼的方式，就是監聽 Aspose.Words 所拋出的警告串流。

在本教學中，我們將一步步示範一個完整、可直接執行的範例，**偵測缺失的字型**、說明 **如何以程式方式偵測缺失的字型**，並提供一個快速的 **處理缺失字型** 小技巧，讓你的輸出保持可預測。

> **快速說明：** 此程式碼適用於 Aspose.Words 23.9（或更新版本），且需要 Java 8 以上。

---

## 需要的環境

- **Aspose.Words for Java**（Maven/Gradle 依賴或放在 classpath 的 JAR）  
- 一個會引用未在系統上安裝的字型（例如 “Comic Sans MS”）的 Word 檔 (`input.docx`)  
- Java IDE 或簡單的 `javac`/`java` 命令列環境  

除此之外不需要其他函式庫——所有功能皆內建於 Aspose.Words 套件。

---

## 第一步 – 設定 LoadOptions 以捕獲警告  

要開始監聽警告，必須建立 `LoadOptions` 實例。此物件會告訴載入器記錄它遇到的任何問題，例如缺失的字型。

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**為什麼這很重要：** 若不使用 `LoadOptions`，載入器會靜默地將缺失的字型替換為系統預設字型，你根本不會知道已發生替換。啟用警告即可完整可視化。

---

## 第二步 – 使用 LoadOptions 載入文件  

現在正式載入文件。我們剛才建立的 `LoadOptions` 會傳入建構子，讓解析過程中產生的任何警告都被捕獲。

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**小技巧：** 若一次處理大量檔案，請重複使用同一個 `LoadOptions` 實例，以避免不必要的物件建立。

---

## 第三步 – 迭代已捕獲的警告  

Aspose.Words 會將每個警告儲存為 `WarningInfo` 物件。我們只關心與字型相關的警告，因此會過濾出 `FontSubstitutionWarningInfo`。

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**說明：**  
- `document.getWarnings()` 會回傳載入期間發生的所有警告列表。  
- `FontSubstitutionWarningInfo` 含有兩個關鍵資訊：**請求的字型**（DOCX 要求的字型）以及 Aspose.Words **實際使用的字型**（替代字型）。  
- 同時印出兩者，即可立即看出哪些字型缺失以及採用了什麼替代方案。

---

## 第四步 – （可選）以程式方式處理缺失字型  

捕獲警告只是故事的一半。知道字型缺失後，你可能想 **處理缺失字型**，例如提供自訂替代或將問題記錄下來以供日後檢查。

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**為什麼要這麼做？**  
- 確保不同機器之間的渲染結果一致。  
- 防止稍後產生的 PDF 或影像出現意外的版面變化。  

你也可以把警告細節寫入資料庫、發送電子郵件給內容團隊，或在關鍵字型缺失時直接中止處理流程。

---

## 完整範例  

以下是可直接執行的完整程式。只要將 `YOUR_DIRECTORY/input.docx` 換成測試檔案的路徑，將 Aspose.Words JAR 加入 classpath，即可執行。

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**預期輸出**（當 “Comic Sans MS” 缺失時）：

```
Requested: Comic Sans MS → Substituted: Arial
```

執行可選的 fallback 程式碼後，儲存的 `output.docx` 會在原本引用 “Comic Sans MS” 的位置改用 **Arial** 來呈現。

---

## 常見問題與邊緣情況  

| 問題 | 解答 |
|----------|--------|
| *如果文件中有多個缺失的字型怎麼辦？* | 迴圈會為每個缺失字型產生一筆警告。你可以將它們收集到 `Map<String, String>` 中，進行批次處理。 |
| *這樣在從文件產生 PDF 時會有效嗎？* | 完全有效。字型替代發生在載入階段，之後的任何匯出（PDF、HTML、影像）都會使用已解析的字型。 |
| *我可以直接抑制警告而不是捕獲嗎？* | 可以——設定 `loadOptions.setWarningCallback(null);` 即可，但會失去對缺失字型的可視性。 |
| *保存文件後警告清單會被清除嗎？* | 警告集合屬於 `Document` 實例。呼叫 `document.save()` 後，列表仍保持不變，除非你建立新的 `Document`。 |
| *如果 DOCX 內嵌入了自訂字型呢？* | 內嵌字型會被視為可用；即使主機系統未安裝，Aspose.Words 也會直接使用它們。 |

---

## 生產環境的進階建議  

- **快取 FontSettings：** 若要處理上百個檔案，建議先建立單一的 `FontSettings`（設定好自訂替代字型），然後重複使用，以減少開銷。  
- **結構化日誌：** 與其使用 `System.out`，不如將警告寫成 JSON 日誌，這樣後續分析（例如「最常缺失的字型」）會更簡單。  
- **提前驗證：** 在進行大量運算前，先以 `LoadOptions` 做一次「乾載入」，若發現關鍵字型缺失即可提前中止。  
- **執行緒安全：** `Document` 物件本身不是執行緒安全的。請為每個檔案使用獨立執行緒，或使用執行緒本地的 `LoadOptions`。  

---

## 結論  

現在你已掌握 **如何在 Aspose.Words for Java 中捕獲警告**、**偵測缺失字型**，以及 **以乾淨的備援策略處理缺失字型**。透過 `LoadOptions` 與 `document.getWarnings()` 的結合，你可以完整掌握字型替代事件，確保產生的文件在任何環境下都能如預期呈現。

準備好下一步了嗎？試著將此模式延伸至 **偵測缺失圖片**、**追蹤不支援的功能**，甚至 **自動將缺失字型嵌入輸出檔**。相同的警告捕獲機制適用於眾多文件處理情境，讓你的程式碼更健全、更具未來延展性。

祝開發順利，願你的文件永遠渲染得美觀如初！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}