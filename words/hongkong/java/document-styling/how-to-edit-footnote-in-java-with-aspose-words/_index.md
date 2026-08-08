---
category: general
date: 2026-08-07
description: 如何在 Java 中使用 Aspose.Words 編輯腳註 – 新增自訂破折號、更改腳註分隔線，並設定段落對齊，以打造精緻文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit footnote
- add custom dash
- change footnote line
- change footnote separator
- set paragraph alignment
language: zh-hant
lastmod: 2026-08-07
og_description: 如何在 Java 中使用 Aspose.Words 編輯腳註。學習新增自訂破折號、更改腳註線，並在幾個步驟內設定段落對齊。
og_image_alt: Java code editing footnote separator with a custom dash and centered
  alignment
og_title: 如何在 Java 中編輯腳註 – 添加破折號、更改行、設定對齊
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  headline: How to edit footnote in Java with Aspose.Words
  type: TechArticle
- description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  name: How to edit footnote in Java with Aspose.Words
  steps:
  - name: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
    text: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
  - name: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
    text: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
  - name: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
    text: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
  - name: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
    text: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
  - name: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
    text: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
title: 如何在 Java 中使用 Aspose.Words 編輯註腳
url: /zh-hant/java/document-styling/how-to-edit-footnote-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中使用 Aspose.Words 編輯註腳

如果您需要 **how to edit footnote**（編輯 Word 文件中的註腳），本指南將展示完整的工作流程。您將學會加入自訂破折號、變更註腳線條，並設定段落對齊，使註腳分隔線看起來更專業。

編輯註腳是處理法律合約、學術論文或行銷手冊時的常見需求。以下步驟涵蓋從載入文件到儲存最終檔案的全部過程，且不需要額外工具。

## 前置條件

開始之前，請確保您已具備：

* 已安裝 Java 17 或更新版本。
* 已將 Aspose.Words for Java（最新版本）加入專案的 classpath。
* 一個包含至少一個註腳的 DOCX 檔案（`input.docx`）。

上述項目可確保程式碼執行時不會發生執行期錯誤。

## 如何編輯註腳分隔線與線條

註腳分隔線是位於正文與註腳清單之間的段落。調整其外觀可提升可讀性，並符合企業品牌形象。

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the document containing footnotes
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Get the footnote separator paragraph (the line before the footnote list)
        Paragraph separator = doc.getFootnoteSeparator();

        // Step 3: Center‑align the separator for better appearance
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Step 4: Replace the default separator line with a custom dash
        separator.getRuns().clear();                 // Remove existing runs
        separator.getRuns().add(new Run(doc, "—"));   // Add a custom dash character

        // Step 5: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### 為何每一行都很重要

1. **Loading the document** – `new Document(...)` 會將 DOCX 檔案讀入記憶體，讓您取得所有節點的存取權。
2. **Fetching the separator** – `getFootnoteSeparator()` 會回傳 Aspose.Words 視為註腳線的特殊段落。此物件是唯一可以安全修改分隔線的地方。
3. **Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)` 會變更線條的對齊方式。關鍵字 *set paragraph alignment* 直接套用於分隔線，確保破折號置中。
4. **Adding a custom dash** – 透過清除既有 Run 並加入包含 em‑dash（`—`）的 `Run`，即可實現 *add custom dash* 效果，同時 *change footnote line* 為您想要的樣式。
5. **Saving the document** – `doc.save(...)` 會將變更寫回磁碟，產生反映所有修改的輸出檔案。

## 為註腳分隔線加入自訂破折號

**Step 4** 的程式碼示範了 *add custom dash* 技巧。您可以將 em‑dash 替換為任意字串，例如 `"***"` 或 `"---"`，以符合文件的視覺語言。

```java
separator.getRuns().clear();                     // Remove default line
separator.getRuns().add(new Run(doc, "***"));    // Insert three asterisks as a custom dash
```

當預設的細線不符合品牌指引時，使用自訂破折號特別有幫助。

## 變更註腳線條樣式

如果您想要實心線而非破折號，可以插入 Unicode 方塊繪製字元或重複的底線。

```java
separator.getRuns().clear();
separator.getRuns().add(new Run(doc, "_____")); // Five underscores create a solid line
```

*change footnote line* 步驟不受您選擇的字元影響，因為分隔線段落僅會呈現其內含的文字。

## 設定註腳分隔線的段落對齊

*set paragraph alignment* 操作不限於置中對齊。您可以依版面需求將其左對齊、右對齊或兩端對齊。

```java
separator.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT); // Right‑align
```

將分隔線右對齊對於使用右對齊註腳的文件（例如雙語出版物）相當實用。

## 完整可執行範例

以下程式碼整合了所有概念——載入文件、編輯註腳分隔線、加入自訂破折號、變更線條樣式，以及設定對齊方式。

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the footnote separator paragraph
        Paragraph separator = doc.getFootnoteSeparator();

        // Set the desired alignment (center, left, right, or justify)
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Clear any existing content in the separator
        separator.getRuns().clear();

        // Add a custom dash – replace with any string to change footnote line
        separator.getRuns().add(new Run(doc, "—")); // Em‑dash as the custom dash

        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**預期結果：** `output.docx` 會在原本的細線位置顯示置中的 em‑dash。所有註腳保持完整，文件版面亦會呈現新的分隔線樣式。

## 常見問題與避免方式

| Issue | Reason | Fix |
|-------|--------|-----|
| Separator not found | Document has no footnotes or uses a custom footnote style | Ensure the source DOCX contains at least one footnote before calling `getFootnoteSeparator()` |
| Custom dash not visible | Font does not support the chosen character | Use a Unicode character that is supported by the document’s default font, or embed a compatible font |
| Alignment appears unchanged | Paragraph format is overridden later in the code | Apply alignment **after** any other formatting calls that might reset it |

針對上述情況進行處理，可避免執行期錯誤，確保 *how to edit footnote* 流程穩定可靠。

## 往後的步驟

既然您已掌握 **how to edit footnote** 元素，接下來可以探索以下相關任務：

* **Add custom footnote reference style** – 修改 `FootnoteReference` 節點以變更編號或符號。
* **Programmatically insert new footnotes** – 使用 `DocumentBuilder.insertFootnote()` 以程式方式插入動態內容。
* **Apply conditional formatting** – 依段落樣式或內容長度變更註腳外觀。

上述延伸功能皆基於您先前使用的 API，能讓您進一步 *add custom dash*、*change footnote line* 與 *set paragraph alignment*。

---

*Happy coding! 如果本教學幫助您精通註腳編輯，歡迎與團隊分享或提交 Pull Request 以進一步完善範例。*

## 接下來該學什麼？

以下教學與本指南所示技術緊密相關，提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能並探索其他實作方式：

- [Set Footnote And End Note Position](/words/hindi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}