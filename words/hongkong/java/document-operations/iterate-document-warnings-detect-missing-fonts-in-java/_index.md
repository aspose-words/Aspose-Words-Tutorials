---
category: general
date: 2026-04-28
description: 遍歷 Word 檔案中的文件警告，以偵測缺少的字型，取得缺少的字型名稱，並使用 Aspose.Words for Java 列印缺少字型的詳細資訊。
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: zh-hant
og_description: 遍歷文件警告以查找缺失字型，檢索缺失字型名稱，並使用完整的 Java 範例列印缺失字型詳細資訊。
og_title: 遍歷文件警告：偵測 Java 中缺少的字型
tags:
- Aspose.Words
- Java
- Document Processing
title: 遍歷文件警告：在 Java 中偵測缺失字型
url: /zh-hant/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 逐項檢查文件警告 – 偵測 Java 中缺少的字型

有沒有曾在開啟 Word 檔案時需要 **逐項檢查文件警告**，卻不知道缺少哪些字型？你並不是唯一遇到這個問題的人。缺少的字型會破壞報告的外觀，若沒有辦法即時發現，最終可能會交付一份與原稿相差甚遠的文件。

在本教學中，我們將示範如何 **偵測缺少的字型**：載入 Word 文件、逐項檢查其警告、取得缺少的字型名稱，最後將缺少的字型資訊印出——全部使用 Aspose.Words for Java。

我們會從第一行程式碼講起，直到預期的主控台輸出，讓你現在就能把可直接執行的範例複製貼上到專案中。無需額外文件說明。

## 前置條件

- 已安裝 Java 8 或更新版本。  
- Aspose.Words for Java 程式庫（截至 2026‑04‑28 的最新版本）。  
- 一個可能包含未在本機安裝字型的 Word 檔案（例如 `doc-with-missing-font.docx`）。

如果以上都已備妥，太好了——你已可以 **載入 Word 文件** 並開始逐項檢查。

## 步驟 1 – 使用預設選項載入 Word 文件

在能 **逐項檢查文件警告** 之前，必須先將檔案載入記憶體。Aspose.Words 只要呼叫一次建構子即可完成。雖然使用預設的 `LoadOptions` 通常已足夠，我們仍會示範明確建立的寫法，以利說明。

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **為什麼這很重要：**  
> 載入文件時，Aspose.Words 會掃描檔案中所有無法解析的資源，例如本機未安裝的字型。這些問題會以 **警告** 形式儲存，我們將在下一步 **逐項檢查文件警告**。

## 步驟 2 – 逐項檢查文件警告以找出字型問題

解決方案的核心出現在此：我們遍歷載入過程中庫所收集的每一筆警告。`WarningInfo` 物件會說明發生了什麼問題，我們可以篩選 `FontSubstitutionWarning` 以 **偵測缺少的字型**。

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **小技巧：** `instanceof` 檢查可確保只處理與字型相關的警告，忽略其他（例如影像載入失敗）的警告。如此一來迴圈效率更高，輸出也只聚焦在你真正需要 **取得缺少字型** 資訊的部分。

### 預期的主控台輸出

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

如果文件中沒有缺少的字型，迴圈會安靜結束——不會有任何 **印出缺少字型** 的訊息。

## 步驟 3 – 為什麼不直接捕捉例外？

你可能會想，「為什麼不把 `new Document(...)` 包在 try‑catch，直接捕捉例外？」答案有兩點：

1. **資訊更細緻：** 例外只告訴你發生錯誤，警告則會提供確切的字型名稱以及 Aspose.Words 所選的備用字型。  
2. **非致命問題：** 缺少字型通常不會導致載入失敗，文件仍能開啟，只是視覺呈現受影響。透過 **逐項檢查文件警告**，你仍能處理檔案的其餘部分。

## 步驟 4 – 延伸範例：將缺少的字型收集到 List

有時你需要將缺少的字型進一步處理——例如嵌入字型或在 UI 中提示使用者。以下示範如何把字型名稱收集到 `Set<String>`。

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

現在你可以以程式方式 **取得缺少字型**，再將資料傳給報表模組或字型安裝精靈。

## 步驟 5 – 實務考量

- **多重替代：** 同一個缺少的字型在文件不同區段可能會被不同的字型取代。警告清單會列出每一次的替代情況，因而可能出現重複的缺少字型條目。  
- **效能：** 載入極大型文件時，警告數量可能達數千筆。若只關心字型，請如前範例般提前過濾，以保持迴圈速度。  
- **跨平台字型：** 在 Linux 上，預設的替代字型通常是 *Liberation Sans*；在 Windows 上則可能是 *Arial*。了解備用字型有助於判斷是否需要隨應用程式一起部署自訂字型。

## 步驟 6 – 視覺說明

以下是主控台輸出的螢幕截圖（alt 文字已包含主要關鍵字以利 SEO）。

![Iterate document warnings console output showing missing fonts and their substitutes](/images/iterate-document-warnings.png)

*Alt text:* *iterate document warnings 範例顯示缺少的字型名稱與替代細節。*

## 結論

你已學會如何在 Aspose.Words for Java 中 **逐項檢查文件警告**、**偵測缺少的字型**、安全 **載入 Word 文件**、**取得缺少字型** 資訊，並將 **印出缺少字型** 的細節顯示於主控台。完整程式碼可直接執行，你也可以自行改寫成寫入檔案、彈出 UI 對話框，甚至自動嵌入缺少的字型。

接下來，你或許想探索如何 **載入 Word 文件** 並加入自訂字型來源（例如公司字型資料夾），或是直接將缺少的字型嵌入檔案，以確保跨機器的版面配置一致。這兩個主題皆是本教學的自然延伸。

祝開發順利，願你的 PDF 永遠如你所願呈現！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}