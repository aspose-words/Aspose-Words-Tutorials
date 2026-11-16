---
category: general
date: 2026-11-15
description: 使用 Java 在 Word 文件中設定段落行距。了解如何透過 Aspose.Words 程式化設定行距，以實現精確的文件格式化。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: zh-hant
lastmod: 2026-11-15
og_description: 使用 Java 在 Word 文件中設定段落行距。本指南說明如何使用 Aspose.Words 為段落和註腳分隔線設定行距，讓您完整掌控文件版面配置。
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: 使用 Java 設定 Word 段落行距
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: 使用 Java 在 Word 文件中設定段落行距
url: /zh-hant/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 文件中使用 Java 設定段落行距

如果您需要在 Word 文件中 **設定段落行距**，本教學將示範如何使用 Java 及 Aspose.Words 來完成。您還會學習 **如何設定行距** 於註腳分隔線——這是格式化專業文件時的常見需求。

在以下章節中您將會：

* 載入現有的 *.docx* 檔案。  
* 取得註腳分隔線段落。  
* 套用自訂的行距值。  
* 儲存更新後的文件。

不需要額外的設定，只要將 Aspose.Words 程式庫加入專案，即可直接複製程式碼並立即執行。

## 前置條件

開始之前，請確保您已具備：

* 已安裝 Java 17 或更新版本。  
* Maven（或其他建置工具）以管理相依性。  
* 有效的 Aspose.Words for Java 授權（免費評估版可用於測試）。  
* 位於已知目錄下的輸入 Word 文件（`input.docx`）。

將 Aspose.Words 相依性加入您的 `pom.xml`：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## 使用 Aspose.Words 設定段落行距

此 H2 標題包含主要關鍵字，滿足 SEO 需求。

### 步驟 1：載入 Word 文件

首先，建立指向來源檔案的 `Document` 實例。

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*為什麼這很重要*：載入文件會產生一個記憶體中的模型，您可以在不觸碰原始檔案的情況下進行操作，直到明確儲存為止。

### 步驟 2：取得註腳分隔線

註腳分隔線是出現在註腳與正文之間的特殊段落。若要變更其外觀，需要存取 `FootnoteSeparator` 物件。

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*提示*：即使文件中沒有註腳，分隔線仍以隱藏段落的形式存在，因此此呼叫永不會回傳 `null`。

### 步驟 3：如何為分隔線的段落設定行距

現在套用所需的行距。Aspose.Words 使用點 (pts) 作為行距單位；12 pts 大約相當於大多數字型的單行距。

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

您也可以使用其他間距模式：

| 模式                     | 方法呼叫                                      |
|--------------------------|--------------------------------------------------|
| **Exactly**（固定 pts） | `setLineSpacingRule(LineSpacingRule.EXACTLY)`   |
| **Multiple**（例如 1.5） | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

選擇正確的規則可確保文件在 Word、Google Docs 以及其他檢視器中保持一致的呈現效果。

### 步驟 4：儲存更新後的文件

最後，將變更寫回磁碟。

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

當您在 Microsoft Word 中開啟 `output.docx` 時，註腳分隔線會以您設定的行距顯示。

## 了解如何為一般段落設定行距

相同的 API 也適用於任何 `Paragraph` 物件，不僅限於註腳分隔線。以下是一個快速範例，調整正文第一段的間距：

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**為什麼可能需要這樣做**：報告、合約與學術論文常常要求特定的行距樣式（例如草稿的雙行距）。使用相同的 `setLineSpacing` 方法可保證得到預期的版面配置。

## 常見陷阱與避免方法

| 問題                                 | 原因                                   | 解決方式 |
|---------------------------------------|----------------------------------------|-----|
| 行距未變更                            | `LineSpacingRule` 保持預設 (AUTO)      | 使用 `setLineSpacingRule` 明確設定規則。 |
| 分隔線之後出現多餘的空白行            | 分隔線包含隱藏的換行字元               | 在套用間距前以 `separator.getText().trim();` 修剪文字。 |
| 儲存後文件損毀                        | 使用過時的 Aspose.Words 版本           | 升級至最新版本（例如 24.10），其中已修正儲存相關的錯誤。 |

## 專業提示：批次處理多個文件

如果需要一次更新數十個檔案，可將邏輯封裝於輔助方法，並對資料夾內的檔案逐一迭代：

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

在迴圈中執行此方法，可為您節省大量手動編輯的時間。

## 預期輸出

執行完整程式後，`output.docx` 會：

* 保留原始內容，僅變更行距。  
* 以單行距（12 pts）顯示註腳分隔線。  
* 保持其他所有格式（樣式、圖片、表格）不變。

在 Word 中開啟檔案，驗證分隔線的行距是否更緊（或更鬆，視您設定的值而定）。

## 結論

您現在已掌握如何使用 Java **設定段落行距**，同時也了解 **如何為註腳分隔線與一般段落設定行距**。完整且可執行的範例示範了載入文件、調整行距屬性以及儲存結果的步驟，全部只需幾個簡潔的 API 呼叫。

**接下來的步驟** 您可以探索：

* **如何為表格與清單項目設定行距**。  
* 為標題與正文套用不同的間距規則。  
* 使用 `Style` 物件在整份文件中強制統一間距。

嘗試不同的數值，結合其他格式化選項，您就能在任何 Java 應用程式中完整掌控文件版面。祝開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，進一步擴展所示技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [如何在 Aspose.Words for Java 中設定選項 – 完整指南](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [如何在 Aspose.Words for Java 中設定 LoadOptions](/words/english/java/document-loading-and-saving/using-load-options/)
- [變更 Word 文件中亞洲段落間距與縮排](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}