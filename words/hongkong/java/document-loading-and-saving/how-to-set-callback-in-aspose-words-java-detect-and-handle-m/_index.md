---
category: general
date: 2026-06-20
description: 如何在 Aspose.Words Java 中設定回呼，以偵測缺失字型並自訂文件載入。一步一步學習處理字型替換警告。
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: zh-hant
og_description: 如何在 Aspose.Words Java 中設定回呼，以偵測缺失字型、處理字型替代，並自訂文件載入。完整指南與程式碼。
og_title: 如何設定回呼 – 在 Aspose.Words Java 中偵測缺少的字型
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: 如何在 Aspose.Words Java 中設定回呼 – 偵測與處理缺失字型
url: /zh-hant/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words Java 中設定回呼 – 偵測與處理缺少的字型

有沒有想過 **如何在 Aspose.Words Java 中設定回呼**，以便在缺少字型破壞您的 PDF 或 DOCX 之前就能發現它們？您並非唯一有此疑慮的人。缺少字型的警告可能會悄悄破壞版面配置，若沒有適當的警告回呼，您可能直到最終文件顯示異常才注意到。

在本教學中，我們將逐步說明一個完整、可直接執行的範例，該範例 **偵測缺少的字型**、**優雅地處理缺少的字型**，並示範如何使用警告回呼 **自訂文件載入**。完成後，您將擁有一個可自行放入任何專案的獨立 Java 類別——不需要額外搜尋文件說明。

## 您需要的條件

- Java 8 或更新版本（程式碼同樣支援 Java 11+）  
- Aspose.Words for Java 函式庫（版本 23.9 或更新）  
- 一個引用了您未安裝字型的 DOCX 檔案（例如自訂企業字型）  

如果您尚未將 Aspose.Words 加入 Maven 專案，只需加入以下內容：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

就這樣——不需要額外的外掛程式，也不需要原生相依性。

---

## 步驟 1：了解 WarningCallback 機制

**警告回呼**是 Aspose.Words 在載入或儲存文件時發生意外情況時向您發出提醒的方式。透過實作 `IWarningCallback`，您可以完整掌控哪些資訊被記錄、忽略，甚至轉為例外。

> **為何重要：**  
> 當字型缺失時，Aspose 會使用備用字型取代。視覺效果可能會有顯著差異，尤其是對品牌導向的 PDF。透過捕捉 `WarningType.FONT_SUBSTITUTION`，您可以記錄確切的字型名稱、決定是否中止，或以程式方式替換為自訂字型。

---

## 步驟 2：建立 LoadOptions 實例

`LoadOptions` 是自訂文件載入的入口點。您需要在實際載入檔案之前，將回呼附加到此物件上。

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

此時 `loadOptions` 只是一個普通的容器——尚未發生任何事。真正的魔法在於我們插入回呼時開始。

---

## 步驟 3：實作並附加回呼

以下是一個緊湊的匿名類別，實作 `IWarningCallback`。每當發生字型取代時，它會在主控台印出友善訊息。

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **專業提示：** 若您想透過提供替代字型來 **處理缺少的字型**，也可以在 `LoadOptions` 上設定 `FontSettings`，將缺少的字型對映到已知的備用字型。

---

## 步驟 4：使用自訂選項載入文件

現在回呼已設定完成，載入文件。如果檔案引用了您未安裝的字型，您將看到警告訊息被印出。

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

執行程式時，主控台可能會顯示：

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

這行訊息證明您已成功 **偵測缺少的字型**，且現在可以依需求 **處理缺少的字型**。

---

## 步驟 5（可選）：以已知字型取代缺少的字型

如果您想自動將任何缺少的字型取代為，例如 `Times New Roman`，可以加入 `FontSettings` 物件：

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

現在文件會被載入，所有對 `MyCustomFont` 的引用會悄悄換成 `Times New Roman`。主控台仍會告知您哪些字型被取代，讓您保持資訊同步。

---

## 完整可執行範例

以下是一個整合上述所有步驟的單一 Java 類別。將其複製貼上至您的 IDE，調整 `docPath` 後執行。

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**預期輸出**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

您現在擁有一個可重現的方式來 **偵測缺少的字型**、**處理缺少的字型**，以及 **自訂文件載入**——全部透過正確學會 **如何設定回呼**。

---

## 常見問題

### 如果我想在字型缺失時停止載入程式該怎麼辦？

在 `warning` 方法內拋出例外：

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

底部的 catch 區塊會捕捉該例外，您可以決定如何記錄或提醒使用者。

### 這對從 DOCX 產生的 PDF 有效嗎？

絕對有效。回呼在 **載入** 階段觸發，對所有輸出格式（`save` 為 PDF、DOCX、HTML 等）皆相同。只要使用相同的 `LoadOptions` 載入來源文件，即可在缺少字型影響最終 PDF 前捕捉到。

### 我可以捕捉其他警告類型嗎（例如影像轉換）？

可以——`WarningInfo.getWarningType()` 可與其他列舉值（如 `WarningType.IMAGE_CONVERSION`）比較。只要在回呼中加入更多 `if` 分支即可。

### 這會影響效能嗎？

可忽略不計。回呼於載入期間同步執行，額外檢查負擔輕微。若一次載入上千份文件，您可能想在正式環境透過設定 `loadOptions.setWarningCallback(null);` 來停用警告。

---

## 視覺概覽

![在 Aspose.Words Java 中設定回呼範例](https://example.com/images/callback-diagram.png "在 Aspose.Words Java 中設定回呼")

*此圖示說明流程：`LoadOptions` → `IWarningCallback` → 文件載入 → 字型取代處理。*

---

## 總結

我們已說明了在 Aspose.Words Java 中 **如何設定回呼**，示範了 **偵測缺少的字型**，展示了實用的 **處理缺少的字型** 方法，並說明了如何使用 `LoadOptions` **自訂文件載入**。  
有了這些知識，您現在可以保護文件流程免於靜默的字型替換，維持品牌一致性，並在問題發生時提供使用者清晰的回饋。

### 接下來？

- 探索 **字型取代表**，以大量對映多個缺少的字型。  
- 將此回呼與 **文件驗證** 結合，以強制執行樣式指南。  
- 嘗試 **自訂警告回呼**，將訊息寫入日誌檔或監控系統，而非 `System.out`。  

歡迎自行實驗，並告訴我們您在專案中如何自訂回呼。祝程式開發愉快！

---

## 接下來該學什麼？

以下教學涵蓋與本指南技術密切相關的主題，並在此基礎上延伸。每個資源皆包含完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在專案中探索替代實作方式。

- [如何在 Aspose.Words for Java 中設定 LoadOptions](/words/english/java/document-loading-and-saving/using-load-options/)
- [如何在 Aspose.Words 中偵測字型 – 處理警告與設定](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [如何在 Aspose.Words 中捕捉字型 – 完整指南](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}