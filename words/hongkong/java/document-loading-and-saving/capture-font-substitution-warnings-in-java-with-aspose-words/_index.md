---
category: general
date: 2026-01-11
description: 學習如何使用 Aspose.Words for Java 捕捉字型替換警告。本分步教學亦涵蓋 LoadOptions 與警告回呼。
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: zh-hant
og_description: 使用 Aspose.Words for Java 捕捉字型替換警告。請依照本指南設定 LoadOptions 及警告回呼，以確保文件載入的可靠性。
og_title: 在 Java 中捕捉字型替換警告 – 完整教學
tags:
- Aspose.Words
- Java
- Document Processing
title: 在 Java 中使用 Aspose.Words 捕捉字型替換警告 – 完整指南
url: /zh-hant/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 捕捉字型替代警告 – 完整 Java 教程

有沒有曾經在開啟缺少字型的 Word 文件時需要**捕捉字型替代警告**？這是常見的麻煩，尤其是當你在伺服器上產生 PDF 或列印，而該伺服器未安裝所有字型。好消息是？Aspose.Words for Java 讓這變得輕鬆——只需設定 `LoadOptions` 物件並掛接警告回呼。在本指南中，你將看到如何操作、為何重要，以及警告觸發時會發生什麼。

我們還會涉及相關主題，如 **Aspose.Words 字型替代**、使用 **Java 警告回呼**，以及 **LoadOptions 使用** 的最佳實踐。完成後，你將擁有一段可直接執行的程式碼片段，能記錄每一次缺字型事件，讓後續處理不會出乎意料。

## 前置條件

- 已安裝並設定 Java 17（或任何較新的 JDK）。
- 在 classpath 中加入 Aspose.Words for Java 23.10（或更新版本）。
- 一個引用了本機未安裝字型的 Word 文件（例如 `DocWithMissingFont.docx`）。
- 基本了解 Java 的 try/catch 區塊——不需要太高深。

如果上述任一項目不熟悉，請稍作停頓，從 Maven Central 安裝此函式庫：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

現在基礎已就緒，讓我們進入程式碼。

## 步驟 1：設定警告回呼以**捕捉字型替代警告**

你首先需要的是一個回呼，Aspose.Words 在遇到缺少字型時會呼叫它。這就是我們**捕捉字型替代警告**的地方。此回呼實作 `IWarningCallback` 介面，並檢查 `WarningType`。

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**為什麼這很重要：** 若沒有回呼，Aspose.Words 會悄悄將缺少的字型換成預設字型，你永遠不會知道視覺輸出已變更。透過捕捉警告，你可以記錄、提醒，甚至在缺少關鍵字型時中止載入。

## 步驟 2：設定 **LoadOptions** 並註冊回呼

現在我們建立 `LoadOptions` 實例，並附加我們的 `FontWarningCallback`。此步驟對於 **LoadOptions 使用** 至關重要，確保每次文件載入都會經過相同的警告過濾。

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

**提示：** 你可以在多個文件間重複使用同一個 `LoadOptions` 物件，這樣可以減少程式碼量，並確保在整個應用程式中一致處理 **文件載入警告**。

## 步驟 3：載入文件並觀察輸出

將回呼掛接好後，只需載入你的 Word 檔案。若文件引用了未安裝的字型，回呼會被觸發，並將詳細資訊印到主控台。

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### 預期的主控台輸出

假設 `DocWithMissingFont.docx` 引用了缺少的字型 *“Comic Sans MS”*，你會看到類似以下的訊息：

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

如果文件**沒有缺少字型**，主控台只會顯示最後一行，證實你的回呼沒有產生任何誤報。

## 步驟 4：處理邊緣情況與常見陷阱

### 多個缺少字型

若文件使用了多個不可用的字型，回呼會對每個字型執行一次。你會收到一連串訊息，每個都有自己的 `source` 與 `description`。不需要額外程式碼——只要確保你的日誌系統能處理快速連續的呼叫即可。

### 抑制警告

在罕見情況下，你可能想忽略某些替代（例如，你知道特定的備援是可接受的）。擴充回呼邏輯：

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### 執行緒安全性

Aspose.Words 的 `LoadOptions` 預設並非執行緒安全。若你平行載入文件，請為每個執行緒建立獨立的 `LoadOptions` 實例，或同步回呼以避免競爭條件。

## 步驟 5：驗證結果文件中的替代字型

載入後，你可能想確認替代已確實發生。API 允許你遍歷所有 run，檢查實際使用的字型名稱：

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

此程式碼片段會印出每個文字 run 及其最終字型。當你建構自動化 PDF 轉換流程時，這是一個方便的完整性檢查。

## 完整可執行範例

將所有部份整合起來，以下是完整、可直接執行的程式：

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

將此檔案儲存為 `FontSubstitutionInfo.java`，使用 `javac` 編譯，然後執行 `java FontSubstitutionInfo`。你應該會看到警告訊息（若有），接著是 run 列表及其最終字型。

## 視覺說明

![顯示字型替代警告的主控台輸出截圖](/images/font-substitution-warning.png "捕捉字型替代警告範例")

*Alt text:* **捕捉字型替代警告** – 載入缺少字型的文件後的主控台輸出。

## 結論

現在你已了解如何使用 Aspose.Words for Java **捕捉字型替代警告**。透過設定 `LoadOptions` 物件並提供自訂的 `IWarningCallback`，你可以完整掌握任何缺少字型的事件，避免它們悄悄影響文件外觀。此技巧直接結合 **Aspose.Words 字型替代** 處理，確保可靠的 **文件載入警告**，並讓你依據業務規則彈性地記錄、提醒或中止。

### 接下來？

- 探索 **Java 警告回呼** 的其他警告類型模式（例如 `DEPRECATED_FEATURE`）。
- 將此方法與 **PDF 轉換** 結合，確保替代字型不會破壞版面配置。
- 更深入了解 **LoadOptions 使用**——嘗試 `Password`、`Encoding` 與 `ResourceLoadingCallback` 以應對更進階的情境。

隨意調整回呼、將警告導向日誌框架，或在關鍵字型缺失時拋出自訂例外。沒有任何限制，現在你已擁有堅實的基礎可供構建。

祝開發愉快，願你的文件永遠如預期般正確呈現！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}