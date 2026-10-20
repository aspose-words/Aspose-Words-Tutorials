---
category: general
date: 2026-04-04
description: 在使用 Aspose.Words for Java 載入 Word 文件時捕捉字型取代警告，並自動偵測缺少的字型。請參考以下逐步指南。
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: zh-hant
og_description: 在使用 Aspose.Words for Java 加載 Word 文檔時捕獲字體替換警告，並通過簡單的幾個步驟檢測缺失的字體。
og_title: 捕捉字型替換警告 – 偵測缺失字型
tags:
- Aspose.Words
- Java
- Document Processing
title: 擷取字型替換警示 – 偵測缺少字型
url: /zh-hant/java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 捕捉字體替換警告 – 偵測缺失字體

有沒有曾經在開啟 Word 檔案時需要 **捕捉字體替換警告**，卻發現關鍵字體缺失？你並不孤單。在許多企業工作流程中，缺少字體會把原本排版完好的報告變成亂碼，而唯一的線索往往是一個大多數開發者看不到的靜默警告。

好消息是 Aspose.Words for Java 允許你在載入過程中掛鉤，**偵測缺失字體**，以免之後出問題。在本教學中，我們將逐步示範一個完整且可執行的範例，將每個替換警告直接輸出到主控台，讓你可以決定是嵌入正確的字體、替換它，或是提示使用者。

在本指南結束時，你將會知道如何：

* 設定一個帶有自訂警告回呼的 `LoadOptions` 物件。
* 過濾回呼，使其僅回應字體替換事件。
* 載入任何 `.docx` 檔案並即時看到警告。
* 擴充解決方案以記錄警告、拋出例外，或甚至自動安裝缺失的字體。

不需要額外文件說明——只要幾行 Java 程式碼和 Aspose.Words JAR 即可。

## 前置條件

在開始之前，請確保你已擁有：

* 已安裝 Java 8 或更新版本（最新的 LTS 版效果最佳）。
* Aspose.Words for Java 23.11 或更新版本——可從 Aspose 官方網站取得 Maven 套件或純 JAR。
* 一份在開發機上不存在的字體（例如 “MyFancyFont”）的 Word 文件。  
* 你慣用的 IDE 或文字編輯器——我使用 IntelliJ IDEA，但 Eclipse 或 VS Code 也同樣適用。

如果上述任一項你不熟悉，請先暫停並安裝好；接下來的教學假設這些已備妥。

---

## 使用 Aspose.Words 捕捉字體替換警告

解決方案的核心在於 `LoadOptions` 實例。透過指派 `IWarningCallback`，我們可以攔截載入階段庫所發出的每個警告。

```java
import com.aspose.words.*;

public class FontDiagnosticsTutorial {
    public static void main(String[] args) throws Exception {

        // Step 1️⃣: Create LoadOptions and set a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Capture only font substitution warnings.
                if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // Step 2️⃣: Load the document. The callback runs automatically.
        Document doc = new Document("YOUR_DIRECTORY/document-with-missing-font.docx", loadOptions);

        // Step 3️⃣: If you reach this line, the document is loaded.
        // Any missing‑font warnings have already been printed to the console.
        System.out.println("Document loaded successfully.");
    }
}
```

**為什麼這樣有效：**  
`LoadOptions` 告訴 Aspose.Words 如何處理傳入的檔案。`IWarningCallback` 介面是一個掛鉤，會為 *每個* 警告接收一個 `WarningInfo` 物件。透過檢查 `info.getWarningType()` 我們可以過濾掉除 `SUBSTITUTED_FONT` 之外的所有警告。`description` 屬性包含可讀的訊息，例如 “Font 'MyFancyFont' was substituted with 'Arial'”。

### 預期的主控台輸出

如果來源文件引用了未安裝的字體，你會看到類似以下的訊息：

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

如果文件只使用機器上已存在的字體，回呼將保持沉默，僅會顯示最終的 “Document loaded successfully.” 行。

---

## 在文件中偵測缺失字體

你可能會想，*「字體替換警告等同於缺失字體嗎？」* 在大多數情況下，答案是肯定的——Aspose.Words 會以備用字體取代缺失的字體，並透過 `SUBSTITUTED_FONT` 報告。然而，也有例外情況：字體本身存在，但特定樣式（粗斜體、特定 OpenType 功能）不存在，會導致微妙的替換。

為了確保捕捉到所有缺口，你可以將警告回呼與載入後檢查結合起來：

```java
// After loading the document, iterate through all runs.
for (Paragraph para : (Iterable<Paragraph>) doc.getFirstSection().getBody().getChildNodes(NodeType.PARAGRAPH, true)) {
    for (Run run : (Iterable<Run>) para.getChildNodes(NodeType.RUN, true)) {
        Font font = run.getFont();
        if (font.getName().equalsIgnoreCase("MyFancyFont")) {
            System.out.println("Run still uses the missing font: " + font.getName());
        }
    }
}
```

**小技巧：** 若發現仍有文字跑（run）引用缺失的字體，你可以即時替換它們：

```java
font.setName("Arial"); // fallback
```

如此一來，即使原始警告被抑制，也能保證視覺結果一致。

---

## 常見陷阱與避免方式

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| **忘記設定回呼** | `LoadOptions` 預設為無操作回呼，導致警告消失。 | 在載入之前，務必呼叫 `loadOptions.setWarningCallback(...)`。 |
| **使用錯誤的警告類型** | `WarningType.SUBSTITUTED_FONT` 是唯一表示缺失字體的列舉。 | 精確過濾 `WarningType.SUBSTITUTED_FONT`；其他類型（例如 `UNKNOWN_FILE_FORMAT`）不相關。 |
| **硬編碼檔案路徑** | 在本機可行，但在 CI/CD 流程中會失效。 | 使用相對路徑或將檔案位置作為命令列參數傳入。 |
| **忽略 Unicode 字體** | 某些缺失字體只會在特定字符上出問題。 | 使用包含你預期支援的完整字元集的文件進行測試。 |
| **在無字體設定的無頭伺服器上執行** | 伺服器可能沒有任何備用字體，導致意外的替換。 | 在伺服器上安裝最小套件的常用字體（Arial、Times New Roman）。 |

---

## 擴充解決方案

既然你已能 **捕捉字體替換警告**，接下來可能想要：

* **將警告記錄到檔案** – 用像 SLF4J 之類的 logger 取代 `System.out.println`。
* **拋出例外** – 在自動化流水線中，缺失字體應導致建置失敗時很有用：

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **自動安裝缺失字體** – 在執行時下載所需的 TTF/OTF，並加入 Java 的 `GraphicsEnvironment`。這是較進階的情境，但完全可行。

---

## 圖表（可選）

![捕捉字體替換警告流程圖，說明 Aspose.Words 如何將缺失字體警告導向自訂回呼。](capture-font-substitution-warnings-diagram.png)

*Alt text:* “捕捉字體替換警告流程圖，說明 Aspose.Words 如何將缺失字體警告導向自訂回呼。”

---

## 結論

我們剛剛說明了如何在使用 Aspose.Words for Java 載入 Word 文件時 **捕捉字體替換警告** 與 **偵測缺失字體**。透過設定 `LoadOptions` 物件並實作簡易的 `IWarningCallback`，即可完整掌握字體備援流程，讓你能記錄、替換或在缺失字體時中止。

簡而言之：設定回呼、過濾 `SUBSTITUTED_FONT`、載入文件，然後依需求處理輸出。之後你可以擴展至記錄框架、CI 檢查，甚至自動字體供應。

想更進一步？試試以下：

* **將字體嵌入** 直接到儲存的文件中（`doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))` 搭配 `FontEmbeddingMode.EMBED_ALL`）。
* **產生 PDF** 在修正字體後，確保最終輸出與預期完全相同。
* **掃描整個資料夾** 的文件以偵測缺失字體，並產生摘要報告。

今天就說到這裡——祝開發愉快，願你的文件永遠以正確的字體呈現！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}