---
category: general
date: 2026-06-17
description: 在 Java 中使用 Aspose.Words 記錄字型替換警告——捕捉文件載入時缺失的字型，保持輸出一致。
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: zh-hant
og_description: 在 Java 中使用 Aspose.Words 記錄字型替換警告。學習在載入文件時捕捉缺少字型提醒，確保 PDF 保持完好無損。
og_title: 在 Java 中記錄字型置換警告 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: 在 Java 中使用 Aspose.Words 記錄字型替換警告
url: /zh-hant/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中記錄字型替換警告 – 完整指南

有沒有想過在 Word 文件載入伺服器上沒有的字型時，如何**記錄字型替換警告**？你並不是唯一對靜默被替換的缺失字型感到困惑的人。好消息是？Aspose.Words for Java 為你提供了一個乾淨的方式，在文件載入的瞬間捕捉這些替換。

在本教學中，我們將手把手示範如何註冊警告回呼、篩選字型替換警示，並將它們寫入主控台（或任何你偏好的日誌）。完成後，你將擁有一段可重複使用的程式碼片段，能直接放入任何使用 **Aspose.Words Java** 的 Java 專案。

## 你將學到什麼

- 如何設定 **LoadOptions** 以捕獲警告。
- 如何實作只回應 **font substitution** 事件的 **IWarningCallback**。
- 如何安全載入文件，同時保留缺失字型的清晰稽核紀錄。
- 將解決方案延伸至檔案日誌或監控系統的技巧。

### 前置條件

- Java 8 或更新版本（程式碼同樣支援 Java 11+）。
- Aspose.Words for Java 套件（建議使用 23.10 或更新版本）。
- 一個引用了未安裝字型的 `.docx` 範例（例如 `MissingFont.docx`）。

不需要額外的框架——只要純 Java 與 Aspose.JAR 即可。

---

## 步驟 1：為 Aspose.Words Java 配置 LoadOptions

在你能攔截任何警告之前，需要先建立一個 **LoadOptions** 實例。此物件告訴 Aspose.Words 在解析輸入檔案時的行為方式。

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

為什麼這一步很關鍵？如果沒有 `LoadOptions` 物件，函式庫會靜默地替換缺失的字型，你永遠不會看到任何痕跡。透過明確建立它，你就能開啟自訂 **warning callback**，精確記錄你關心的資訊。

> **專業提示：** 若一次批次載入多個文件，請重複使用同一個 `LoadOptions` 實例，以避免不必要的物件產生。

---

## 步驟 2：實作字型替換的警告回呼

Aspose.Words 內建 `IWarningCallback` 介面。實作它即可自行決定當引擎拋出 `WarningInfo` 時的處理方式。在本例中，我們只想對 `WarningType.FONT_SUBSTITUTION` 作出回應。

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

需要注意的幾點：

1. **過濾** – `if` 陳述式確保我們忽略不相關的警告（例如版面配置問題），保持日誌整潔。
2. **執行緒安全** – 回呼在載入文件的同一執行緒上執行，對於簡單的主控台輸出不需要額外同步。若寫入共用日誌，請確保其具備執行緒安全性。
3. **可擴充性** – 想寫入檔案嗎？只要把 `System.out.println` 換成 `java.util.logging.Logger` 或第三方日誌框架即可。

---

## 步驟 3：使用已配置的選項載入文件

現在回呼已設定好，載入你的 Word 檔案。Aspose.Words 解析文件的瞬間，任何缺失的字型都會觸發上述回呼。

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

如果來源檔案引用了未安裝的字型，你會看到類似以下的輸出：

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

這行即是你想要的 **log font substitution warnings**。接下來你可以採取行動——例如提醒使用者、切換到備用樣式表，或僅僅將其記錄以符合法規要求。

---

## 步驟 4：繼續正常處理

載入完成後，文件的行為與任何其他 `Document` 物件相同。你可以自由檢查章節、擷取文字，或轉換成 PDF。警告日誌會在載入階段自動產生，無需額外程式碼。

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

此時主控台將同時顯示字型替換警告（若有）**以及**章節數量，證明文件已完整可用。

---

## 進階技巧與邊緣情況

### 將日誌寫入檔案而非主控台

如果你偏好永久保存的日誌，可將 `System.out.println` 呼叫換成 `FileWriter`：

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

在正式環境中務必妥善處理 `IOException`。

### 在迴圈中捕獲多個文件

處理資料夾內的多個文件時，可重複使用同一個回呼：

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

由於回呼已綁定於 `loadOptions`，每次迭代都會自動記錄任何字型替換事件。

### 處理嵌入式字型

若啟用此功能，Aspose.Words 甚至可以嵌入缺失的字型：

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

即使開啟了嵌入，警告回呼仍會觸發，讓你得以看見被替換的字型。

---

## 完整範例程式

以下是完整、可直接執行的程式。將其複製到名為 `FontSubstitutionDiagnostics.java` 的類別中，調整檔案路徑後執行。

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**預期輸出**（假設來源文件引用了缺失的字型）：

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

主控台與 `font_substitution_log.txt` 都會包含該警告，提供可靠的稽核紀錄。

---

## 結論

我們剛剛示範了如何在 Java 中使用 Aspose.Words **記錄字型替換警告**。只要配置 `LoadOptions`、接上 `IWarningCallback`，再載入文件，即可完整掌握原本可能被忽略的缺字型事件。接下來你可以：

- 將警告導向集中式日誌服務。
- 為品質管控流程觸發警示。
- 結合其他 **document loading** 策略，例如 PDF 轉換或合併列印。

盡情實驗吧——把主控台日誌換成 SLF4J、加入時間戳記，甚至推送警示至監控儀表板。核心模式不變，現在你已具備在任何基於 Java 的文件工作流中穩健處理字型的堅實基礎。

有什麼新想法想分享嗎？或許你已將此功能整合到 Spring Boot 或雲端函式中。歡迎在下方留言，讓討論持續下去。祝編程愉快！

## 接下來該學什麼？

以下教學與本指南所示技巧緊密相關，能進一步擴展你的能力。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助你掌握更多 API 功能，並在自己的專案中探索替代實作方式。

- [在 Java 中捕獲字型替換警告 – 完整指南](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [在 Aspose.Words for Java 中使用文件選項與設定](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [啟用字型替換警告 – 完整指南](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}