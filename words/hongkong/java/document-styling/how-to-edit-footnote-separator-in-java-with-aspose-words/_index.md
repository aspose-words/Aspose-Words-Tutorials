---
category: general
date: 2026-10-04
description: 使用 Aspose.Words 在 Java 中編輯腳註分隔符 – 了解如何更改腳註分隔符並向 Word 文件加入自訂分隔字。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit footnote separator
- change footnote separator
- custom separator word
language: zh-hant
lastmod: 2026-10-04
og_description: 使用 Aspose.Words 在 Java 中編輯註腳分隔線。此教學示範如何變更註腳分隔線並插入自訂的分隔字元。
og_image_alt: Screenshot of a Java IDE showing code that edits a footnote separator
  in a Word document
og_title: 在 Java 中編輯腳註分隔符 – 完整 Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  headline: How to edit footnote separator in Java with Aspose.Words
  type: TechArticle
- description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  name: How to edit footnote separator in Java with Aspose.Words
  steps:
  - name: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
    text: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
  - name: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
    text: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
  - name: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
    text: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
- Word processing
title: 如何在 Java 中使用 Aspose.Words 編輯腳註分隔線
url: /zh-hant/java/document-styling/how-to-edit-footnote-separator-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中使用 Aspose.Words 編輯腳註分隔線

如果您需要在 Word 文件中**編輯腳註分隔線**，本指南將向您展示如何在 Java 中完成此操作。無論您想將**腳註分隔線**改為破折號、星號或任何**自訂分隔字詞**，以下步驟都能滿足您的需求。

您將學會如何載入 `.docx` 檔案、取得特殊的分隔區段、修改其內容，並儲存結果。無需外部腳本或手動編輯——所有操作皆透過 Aspose.Words for Java 程式庫以程式方式完成。

## 前置條件

- 已安裝 Java 17 或更新版本。
- 使用 Maven 或 Gradle 來管理相依性（範例使用 Maven）。
- 有效的 Aspose.Words for Java 授權（或免費評估金鑰）。
- 已包含腳註的 Word 文件（只有存在腳註時才會有分隔線）。

## 將 Aspose.Words 加入您的專案

如果您使用 Maven，請將以下相依性加入您的 `pom.xml`：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.11</version> <!-- Use the latest version -->
</dependency>
```

若使用 Gradle，請加入：

```gradle
implementation 'com.aspose:aspose-words:24.11'
```

## 步驟 1：載入包含腳註的文件

第一步是開啟您想要修改的 Word 檔案。Aspose.Words 會將檔案讀取為 `Document` 物件，讓您完整存取文件的所有部分，包括腳註分隔線。

```java
import com.aspose.words.*;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // Path to the source document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";

        // Load the document
        Document document = new Document(inputPath);
        
        // Continue with separator editing...
    }
}
```

**為什麼這很重要：** 載入文件會在記憶體中建立表示，您可以安全地修改任何節點，直到明確儲存之前，原始檔案不會受到影響。

## 步驟 2：取得腳註分隔線區段

Word 會將腳註分隔線儲存為特殊的 `Separator` 節點。Aspose.Words 提供 `getFootnoteSeparator()` 方法可直接取得它。

```java
// Get the footnote separator (the line that appears between footnotes and the main text)
Separator footnoteSeparator = document.getFootnoteSeparator();

if (footnoteSeparator == null) {
    System.out.println("The document does not contain a footnote separator.");
    return;
}
```

**專業提示：** 只有當文件已至少包含一個腳註時，分隔線節點才會存在。如果您嘗試編輯沒有腳註的文件，`getFootnoteSeparator()` 會回傳 `null`，因此請務必檢查此情況。

## 步驟 3：插入自訂分隔字詞

現在您可以變更分隔線的外觀。在此範例中，我們將預設的直線替換為長破折號（`—`）。您也可以插入任何**自訂分隔字詞**，例如 `"NOTE:"` 或 `"***"`。

```java
// Access the first paragraph of the separator (there is usually only one)
Paragraph separatorParagraph = footnoteSeparator.getParagraphs().get(0);

// Clear any existing runs (text fragments) to avoid mixing old and new content
separatorParagraph.clearChildren();

// Append a new Run that contains the custom separator word
Run customRun = new Run(document, "—");   // Replace "—" with any text you need
separatorParagraph.appendChild(customRun);
```

### 程式碼說明

1. **`clearChildren()`** 會移除任何現有的 Run，確保分隔線僅包含您提供的文字。
2. **`new Run(document, "—")`** 會建立一個包含所需分隔符的文字節點。`Run` 物件會遵循文件的樣式，因此分隔線會繼承原始腳註分隔線的格式。
3. **`appendChild(customRun)`** 將新的 Run 插入到分隔線段落中。

您也可以對 Run 套用格式，例如：

```java
customRun.getFont().setBold(true);
customRun.getFont().setSize(10);
customRun.getFont().setColor(Color.BLUE);
```

## 步驟 4：儲存已修改的文件

編輯完分隔線後，將文件寫回磁碟。請選擇新檔名，以免覆寫原始檔案。

```java
// Path to the output document
String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";

// Save the changes
document.save(outputPath);

System.out.println("Footnote separator edited successfully. Saved to " + outputPath);
```

**結果驗證：** 在 Microsoft Word 中開啟 `ModifiedNotes.docx`。腳註分隔線應顯示自訂的破折號（或您選擇的字詞），而非預設的直線。

## 處理多種腳註分隔線

Word 支援三種特殊的分隔線類型：

| 分隔線類型 | 方法 |
|----------------|----------------------------|
| Footnote separator | `getFootnoteSeparator()` |
| Footnote continuation separator | `getFootnoteContinuationSeparator()` |
| Footnote separator for the first page | `getFootnoteSeparatorForFirstPage()` |

如果您需要編輯全部這些分隔線，請對每個方法重複 **步驟 2** 和 **步驟 3**。範例：

```java
Separator continuation = document.getFootnoteContinuationSeparator();
if (continuation != null) {
    // Apply the same custom run or a different one
    Paragraph p = continuation.getParagraphs().get(0);
    p.clearChildren();
    p.appendChild(new Run(document, "*"));
}
```

## 常見陷阱與避免方法

| 問題 | 原因 | 解決方式 |
|-------|-------|-----|
| 儲存後未出現分隔線 | 文件沒有腳註 → 分隔線節點為 `null` | 在編輯前至少加入一個腳註，或以程式方式建立虛擬腳註。 |
| 分隔線顯示多餘空格 | 未清除現有的 Run | 在加入新 Run 前呼叫 `clearChildren()`。 |
| 格式看起來不同 | Run 繼承自原始分隔線的樣式 | 若需要特定外觀，請明確設定 `Run` 的字型屬性。 |

## 完整範例程式

將所有步驟整合起來，以下是一個可直接複製、編譯與執行的獨立 Java 類別：

```java
import com.aspose.words.*;
import java.awt.Color;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the footnote separator
        Separator footnoteSeparator = doc.getFootnoteSeparator();
        if (footnoteSeparator == null) {
            System.out.println("Document has no footnote separator.");
            return;
        }

        // 3️⃣ Replace the separator with a custom word (e.g., an em dash)
        Paragraph para = footnoteSeparator.getParagraphs().get(0);
        para.clearChildren();                       // Remove old runs
        Run customRun = new Run(doc, "—");          // Change "—" to any word you need
        customRun.getFont().setBold(true);         // Optional styling
        customRun.getFont().setSize(9);
        customRun.getFont().setColor(Color.DARK_GRAY);
        para.appendChild(customRun);

        // 4️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";
        doc.save(outputPath);

        System.out.println("Footnote separator edited successfully.");
    }
}
```

執行程式後，開啟 `ModifiedNotes.docx` 以確認分隔線已更新。

## 結論

現在您已了解如何使用 Java 與 Aspose.Words **編輯 Word 文件中的腳註分隔線**。本教學說明了載入文件、取得特殊分隔節點、插入**自訂分隔字詞**，以及儲存結果的整個流程。依照這些步驟，您也能 **變更續頁腳註分隔線** 或首頁腳註的分隔線。

接下來，您可以探索：

- 為首頁腳註加入不同的分隔線（`getFootnoteSeparatorForFirstPage()`）。
- 在沒有腳註時以程式方式建立腳註。
- 使用 Aspose.Words 來設定腳註文字的樣式（字型、顏色、縮排）。

隨意嘗試其他字元或字詞，以符合文件的品牌需求。祝開發順利！

## 接下來您可以學習什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎延伸技術。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索替代實作方式。

- [在 Word 中插入文件樣式分隔線](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)
- [取得 Word 文件段落樣式分隔線](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [使用 Aspose.Words Java 載入 Word 文件：完整指南](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}