---
category: general
date: 2026-06-27
description: 學習如何在 Java 中使用 Aspose.Words 捕捉字型取代警告。本分步教學亦會介紹警告回呼以及 LoadOptions 的使用。
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: zh-hant
og_description: 捕捉 Java 中使用 Aspose.Words 的字型替換警告。請依照本指南設定警告回呼、使用 LoadOptions，並處理缺少的字型。
og_title: 在 Java 中捕捉字型替換警告 – Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: 在 Java 中使用 Aspose.Words 捕捉字體替換警告 – 完整指南
url: /zh-hant/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中使用 Aspose.Words 捕捉字型替換警告 – 完整指南

是否曾在載入使用稀有字型的 DOCX 時，需要 **捕捉字型替換警告**？你並不是唯一遇到這個問題的人。在許多實務專案中——例如自動化報表產生器或批次文件轉換工具——缺少的字型會悄悄被替換，導致版面配置失真。

幸好，Aspose.Words 提供了簡潔的方式來監聽這些警告。在本教學中，我們將說明如何設定 **LoadOptions**、掛接 **Aspose.Words 警告回呼**，以及將每個 *字型替換* 訊息印出至主控台。完成後，你將能精確掌握字型何時被替換，並以程式方式作出回應。

> **你將得到：** 完整可執行的 Java 程式碼、每段程式碼意義的說明，以及處理自訂字型目錄等邊緣案例的技巧。

## 前置條件與所需環境

在開始之前，請確保你已具備：

- 已安裝 Java 8 或更新版本（程式碼同樣支援 Java 11+）。
- 最新的 Aspose.Words for Java JAR（可從官方網站或 Maven Central 下載）。
- 一個引用了本機未安裝字型的 DOCX 檔案（例如 Aspose 示範套件中的 *font‑rich.docx*）。
- 一個好用的 IDE（IntelliJ IDEA、Eclipse，或是安裝 Java 擴充套件的 VS Code）。

除 Aspose.Words 之外，無需其他外部函式庫，範例可在純 `main` 方法中執行。

## 步驟 1：設定 LoadOptions – 自訂載入的入口點

`LoadOptions` 是 Aspose.Words 用來告訴函式庫 *如何* 讀取文件的設定容器。預設情況下，它會靜默替換缺少的字型，但你可以透過警告回呼改變此行為。

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**為什麼重要：** 若不使用 `LoadOptions`，文件會安靜地載入，無法得知缺少的字型。建立此實例即可為警告系統提供掛點。

## 步驟 2：定義警告回呼以 *捕捉字型替換警告*

Aspose.Words 會透過 `IWarningCallback` 介面傳遞警告事件。你可以在同一檔案內實作（或另建類別），並篩選 `WarningType.FONT_SUBSTITUTION`。

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**說明：**  
- `info.getWarningType()` 會回傳警告的類別。  
- `WarningType.FONT_SUBSTITUTION` 是我們關注的列舉值。  
- `info.getDescription()` 包含可讀的訊息，例如 *“Font 'Comic Sans MS' not found, substituted with 'Arial'.”*  

透過印出 description，你即可 **即時捕捉字型替換警告**。

## 步驟 3：使用已設定的 LoadOptions 載入文件

回呼設定完成後，使用 `Document` 讀取 DOCX。警告回呼會在解析過程自動觸發。

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

將 `YOUR_DIRECTORY` 替換為實際的測試檔案路徑。當 `Document` 建構子執行時，任何缺字型都會觸發先前定義的回呼，並在主控台顯示替換訊息。

## 步驟 4：驗證已載入的文件（可選但有幫助）

載入後，你可能想確認文件的完整性——頁數、文字抽取等。此步驟對捕捉警告不是必須，但能讓你觀察替換對版面的影響。

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

若字型被替換，版面可能會略有移位；檢查頁數即可發現此類變化。

## 步驟 5：進階 – 程式化處理被替換的字型

有時你不只想記錄警告，還需要嵌入備援字型或調整樣式。以下提供一個快速範例供你參考。

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

透過將 Aspose.Words 指向包含原始字型的資料夾，你可以 *防止* 替換發生。若資料夾不存在，警告回呼仍會捕捉事件，讓你有後備策略。

## 完整可執行範例

將上述步驟整合，以下是完整、可直接執行的程式：

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**預期的主控台輸出**（當遇到缺少的字型時）：

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

若所有字型皆已安裝，回呼將保持沉默——不會印出任何內容，這正是我們所期待的行為。

## 常見陷阱與專業提示

| 陷阱 | 為何會發生 | 解決方式 |
|------|------------|----------|
| **回呼從未觸發** | 你忘記將回呼掛到 `LoadOptions` **或** 使用了不帶 `loadOptions` 參數的 `Document` 預設建構子。 | 必須呼叫 `loadOptions.setWarningCallback(...)` **且** 使用 `new Document(path, loadOptions)` 的重載版本。 |
| **警告過多佔滿日誌** | 大型文件中缺少多個字型會產生每個替換一次的警告。 | 進一步篩選 `info.getDescription()` 只保留特定字型名稱，或將警告聚合至列表，稍後一次處理。 |
| **替換字型影響版面** | 替代字型的度量（大小、間距）可能與原字型不同。 | 參考步驟 5提供自訂字型資料夾，或在載入後調整文件樣式。 |
| **在無頭伺服器上執行** | 預設的字型備援可能依賴未安裝於伺服器的系統字型。 | 隨應用程式一起部署所需字型，並使用 `FontSettings` 指向該資料夾。 |

## 常見問答

**Q: 這個機制能用於 PDF 或其他格式嗎？**  
A: 能。警告回呼與格式無關，會在 Aspose.Words 載入任何文件類型（DOC、DOCX、RTF、HTML 等）時觸發。唯一差別是不同格式可能產生的警告類型。

**Q: 我可以捕捉其他類型的警告，例如 *影像解析度* 警告嗎？**  
A: 當然可以。在 `warning` 方法內檢查 `info.getWarningType()`，若值為 `WarningType.IMAGE_RESOLUTION`，即可自行處理。

**Q: 載入文件後，我該如何取得所有被替換的字型清單？**  
A: 在回呼中將每筆 `info.getDescription()` 存入 `List<String>`。文件載入完成後，你就擁有一個可供記錄、傳送至監控服務，或觸發字型下載流程的集合。

## 結論

現在你已掌握 **在 Java 中使用 Aspose.Words 捕捉字型替換警告** 的完整方法，了解每個環節的意義，並能依實際需求擴充解決方案。透過 `LoadOptions`、`Aspose.Words 警告回呼`，以及可選的 `FontSettings`，你可以完整掌握缺字型情況，確保文件轉換流程的可靠性。

準備好下一步了嗎？試著把 `System.out.println` 換成 SLF4J 等日誌框架，或將警告清單整合至 UI，於批次轉換前即時提醒使用者。你也可以探索 **Aspose.Words 警告回呼** 的其他類型，例如 *不支援的功能* 或 *高解析度影像* 警告。

祝程式開發順利，願你的 PDF 再也不會因意外的字型替換而出問題！

![Screenshot showing console output of captured font substitution warnings](image-placeholder.png "capture font substitution warnings")


## 接下來你可以學習什麼？

以下教學與本指南緊密相關，能進一步深化你所學的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助你在專案中靈活運用其他 API 功能或探索替代實作方式。

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}