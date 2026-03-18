---
category: general
date: 2026-03-17
description: 學習 Aspose 警告回呼教學，以偵測缺少的字型並追蹤 Java 文件中的缺字，並提供完整可執行的範例。
draft: false
keywords:
- aspose warning callback tutorial
- detect missing fonts
- track missing fonts
language: zh-hant
og_description: 精通 Aspose 警告回呼教學，偵測缺失字型並在 Java 文書處理工作流程中追蹤缺失字型。
og_title: Aspose 警告回呼教學 – 偵測缺失字型
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Aspose 警告回呼教學 – 偵測與追蹤缺失字型
url: /zh-hant/java/document-rendering/aspose-warning-callback-tutorial-detect-and-track-missing-fo/
---

愉快！"

Then closing shortcodes: {{< /blocks/products/pf/tutorial-page-section >}} etc remain.

Also include the backtop button shortcode unchanged.

Now produce final content with all translations, preserving code block placeholders and shortcodes.

Make sure to keep markdown formatting.

Let's craft final answer.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose 警告回呼教學 – 偵測與追蹤缺失字型

有沒有想過在使用 Aspose.Words 轉換或編輯 Word 檔案時，如何 **偵測缺失字型**？你並不孤單。在許多實務專案中，偶然的字型缺失會導致版面錯位，而你需要一個可靠的方式在問題發生前 **追蹤缺失字型**。

好消息是？**Aspose 警告回呼教學** 為你提供一個乾淨的程式化掛鉤，能即時列印字型取代警告。本文將逐步說明如何設定回呼、載入文件，以及在 Java 中觀察警告的實際運作。

閱讀完本篇後，你將能自動偵測缺失字型、記錄它們，並決定是嵌入替代字型還是調整來源檔案。無需額外工具。

## 前置條件

- **Java 8+**（程式碼可在任何近期的 JDK 上編譯）
- **Aspose.Words for Java** 版本 23.10 或更新 – 從 Aspose 入口網站下載或加入 Maven 依賴。
- 一個刻意引用未安裝字型的範例 DOCX（例如在 Linux 系統上使用 “Comic Sans MS”）。

就這樣—不需要額外的函式庫，也不需要複雜的建置步驟。

## 步驟 1：註冊警告回呼 – Aspose 警告回呼教學的核心

本教學的第一步是教你如何附加警告監聽器。Aspose.Words 會為每個遇到的問題拋出 `WarningInfo` 物件，而 `WarningSource.FONT_SUBSTITUTION` 旗標則精確指出字型被替換的時機。

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {

        // Step 1: Register a warning callback to capture font substitution warnings.
        Document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about font‑substitution events.
                if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution warning:");
                    System.out.println("  Original:   " + info.getDescription());
                    System.out.println("  Substituted:" + info.getAdditionalInfo());
                }
            }
        });
```

**為何重要：** 若未設定回呼，Aspose 會悄悄替換缺失字型，你永遠不會知道哪些字形可能顯示不正確。透過記錄警告，你可以提前 **偵測缺失字型**，並決定是否嵌入正確的字型。

> **專業提示：** 若需要稍後報告收集警告，請將它們存入 `List<WarningInfo>`，而非直接列印。

## 步驟 2：載入文件 – 缺失字型可能隱藏之處

現在我們載入可能引用機器上不存在字型的 DOCX。載入動作會在有缺失字型時觸發警告回呼。

```java
        // Step 2: Load a document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**背後發生了什麼？** Aspose 會解析文件的樣式定義、掃描每個文字執行序，並檢查系統的字型庫。當找不到完全匹配時，會退回使用替代字型，並觸發我們剛剛掛鉤的警告。

## 步驟 3：儲存文件 – 觸發警告

最後，我們儲存文件。儲存操作同樣會重新評估字型，因此在載入時未發出的警告會在此時出現。

```java
        // Step 3: Save the document; any font substitution warnings will be printed by the callback.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

執行程式後，你會看到類似以下的主控台輸出：

```
Font substitution warning:
  Original:   Font "Comic Sans MS" not found.
  Substituted: Using "Arial" as fallback.
```

該輸出證明 **Aspose 警告回呼教學** 正常運作，你已成功 **偵測缺失字型**，並透過日誌 **追蹤缺失字型**。

## 如何在 Word 文件中偵測缺失字型 – 超越基礎

回呼方式適合一次性的執行，但有時你需要可重複使用的工具。以下是一個可直接放入任何專案的快速封裝：

```java
public class FontMissingChecker {
    private final List<String> missingFonts = new ArrayList<>();

    public FontMissingChecker() {
        Document.setWarningCallback((WarningInfo info) -> {
            if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                missingFonts.add(info.getDescription());
            }
        });
    }

    public List<String> check(String path) throws Exception {
        new Document(path); // triggers warnings
        return missingFonts;
    }
}
```

這樣呼叫它：

```java
FontMissingChecker checker = new FontMissingChecker();
List<String> fonts = checker.check("input.docx");
if (!fonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    fonts.forEach(System.out::println);
}
```

現在你擁有一個可重複使用的 **偵測缺失字型** 方法，會回傳列表，可供 CI 流程或 UI 使用。

## 使用 Aspose.Words 追蹤缺失字型 – 團隊報告

在較大的團隊中，你可能想產生所有文件中缺失字型的 CSV 報告。將前述工具與簡單的檔案迭代結合：

```java
import java.nio.file.*;
import java.io.*;

public class BulkFontReporter {
    public static void main(String[] args) throws Exception {
        Path folder = Paths.get("YOUR_DIRECTORY");
        try (BufferedWriter writer = Files.newBufferedWriter(folder.resolve("missing-fonts-report.csv"))) {
            writer.write("Document,Missing Font\n");
            Files.list(folder)
                 .filter(p -> p.toString().endsWith(".docx"))
                 .forEach(p -> {
                     try {
                         FontMissingChecker checker = new FontMissingChecker();
                         List<String> missing = checker.check(p.toString());
                         for (String msg : missing) {
                             // Extract font name from description
                             String font = msg.replaceAll("Font \"(.*?)\".*", "$1");
                             writer.write(p.getFileName() + "," + font + "\n");
                         }
                     } catch (Exception e) {
                         // In a real app, log the error
                     }
                 });
        }
        System.out.println("Report generated at missing-fonts-report.csv");
    }
}
```

執行此腳本會產生一個 **追蹤缺失字型** 的 CSV，讓每位開發者在提交文件至正式環境前快速檢視。

## 常見陷阱與避免方法

| 陷阱 | 發生原因 | 解決方法 |
|------|----------|----------|
| **回呼未觸發** | 你忘記在載入文件 **之前** 設定回呼。 | 在 `main` 的最上方放置 `Document.setWarningCallback`。 |
| **僅出現第一個警告** | Aspose 會對每個 `Document` 實例快取警告。 | 為每個檔案使用新的 `Document` 物件，或在執行間重設回呼。 |
| **日誌中的字型名稱錯誤** | 描述文字包含額外資訊（例如 “Font … not found”）。 | 如 CSV 範例所示，使用正規表達式去除多餘文字。 |
| **大量批次時效能下降** | 回呼會在每個文字執行序上執行，成本較高。 | 將檢查限制在前置步驟；若只需偵測可略過儲存。 |

## 預期結果與驗證

1. **主控台輸出** – 你應該會看到每個缺失字型至少一行 “Font substitution warning”。  
2. **CSV 報告** – 批次腳本完成後，開啟 `missing-fonts-report.csv`，確認每列列出文件名稱與確切缺失的字型。  
3. **儲存的文件** – 輸出的 DOCX 會使用備用字型呈現，但視覺版面可能與原始文件不同。

若上述任一步驟未如預期，請再次確認 Aspose.Words 的 JAR 已在 classpath 中，且 `input.docx` 確實引用了系統中不存在的字型。

## 結論

你剛完成 **Aspose 警告回呼教學**，示範了如何在 Java 應用程式中 **偵測缺失字型** 與 **追蹤缺失字型**。透過註冊警告監聽器、載入文件，並可選擇匯出結果，你即可在字型相關問題進入正式環境前獲得完整可見性。

接下來，你可以探索：

- 直接使用 `LoadOptions.setFontSubstitution` 嵌入缺失字型。
- 使用 `FontSettings` 類別將缺失字型對映至特定替代字型。
- 將 CSV 報告整合至 CI/CD 流程，於出現未記錄的字型時使建置失敗。

試著執行看看，依照你的日誌框架調整回呼，讓文件工作流程變得更穩健。祝開發愉快！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}