---
date: 2026-01-06
description: 學習如何使用 Aspose.Words for Java 從 Word 文件中移除頁腳，以及如何刪除分節符、分頁符等。
linktitle: Removing Content from Documents
second_title: Aspose.Words Java Document Processing API
title: 如何使用 Aspose.Words for Java 從 Word 文件中移除頁腳
url: /zh-hant/java/document-manipulation/removing-content-from-documents/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words for Java 移除 Word 文件的頁腳

## 介紹 Aspose.Words for Java

在本教學中，您將學會如何使用 Aspose.Words for Java 以程式方式 **移除 Word** 檔案的頁腳。無論您是需要清理產生的報告、剝除機密資訊，或只是整理範本，本指南都會帶您了解最常見的內容移除情境——分頁符、分節符、頁腳與目錄。讓我們開始吧！

## 快速解答
- **我可以在不影響其他內容的情況下移除頁腳嗎？** 是的，API 允許您只針對頁腳節點進行操作。
- **執行這些範例是否需要授權？** 免費試用版可用於開發；正式環境需購買授權。
- **支援哪些 Word 格式？** DOC、DOCX、DOCM 以及基於 OOXML 的格式。
- **此程式碼是否相容於 Java 8 及以上版本？** 當然，從 8 版起此函式庫即相容於 Java。
- **如何刪除分節符？** 請參閱下方的「如何刪除分節符」章節。

## 什麼是「從 Word 移除頁腳」？

從 Word 文件中移除頁腳是指刪除每頁底部的 `HeaderFooter` 節點。當您希望產生僅含標題的乾淨版面，或頁腳內含必須保密的資料時，這項操作相當常見。

## 為什麼在此任務中使用 Aspose.Words for Java？

Aspose.Words 提供高階物件模型，抽象化 DOCX 檔案格式的複雜性。您只需幾行 Java 程式碼即可操作段落、文字串、分節與頁腳，且不需在伺服器上安裝 Microsoft Word。

## 前置條件
- Java Development Kit (JDK) 8 或更新版本。
- Aspose.Words for Java 函式庫（從 Aspose 官方網站下載）。
- 放置於已知目錄中的範例 Word 文件（`Document.docx`）。

## 移除分頁符

分頁符控制頁面的分割，但有時需要將其剔除。以下程式碼會掃描每個段落，清除 `PageBreakBefore` 標記，並移除任何明確的分頁符字元。

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);
for (Paragraph para : (Iterable<Paragraph>) paragraphs) {
    if (para.getParagraphFormat().getPageBreakBefore()) {
        para.getParagraphFormat().setPageBreakBefore(false);
    }
    for (Run run : para.getRuns()) {
        if (run.getText().contains(ControlChar.PAGE_BREAK)) {
            run.setText(run.getText().replace(ControlChar.PAGE_BREAK, ""));
        }
    }
}
doc.save("Your Directory Path" + "RemoveContent.RemovePageBreaks.docx");
```

*小技巧：* 若希望單頁版面，請在移除頁腳之前先執行此步驟。

## 如何刪除分節符

分節符會將文件分割成獨立的節，每個節都有自己的標頭、頁腳與頁面設定。若要合併節並有效 **刪除分節符**，請以相反順序遍歷，將較早節的內容前置至最後一節，然後移除已空的節。

```java
for (int i = doc.getSections().getCount() - 2; i >= 0; i--) {
    doc.getLastSection().prependContent(doc.getSections().get(i));
    doc.getSections().get(i).remove();
}
```

此方法在保留所有內容的同時，消除結構性的分節符。

## 移除頁腳（主要目標：從 Word 移除頁腳）

頁腳通常包含頁碼、日期或機密備註。以下程式碼會從每個節中移除 **所有頁腳類型**——包括第一頁、主要頁腳以及偶數頁腳。

```java
Document doc = new Document("Your Directory Path" + "Header and footer types.docx");
for (Section section : doc.getSections()) {
    HeaderFooter footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_FIRST);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_EVEN);
    footer.remove();
}
doc.save("Your Directory Path" + "RemoveContent.RemoveFooters.docx");
```

執行此程式碼後，產生的文件將 **不含任何頁腳**，達成「從 Word 移除頁腳」的主要目標。

## 移除目錄

目錄（TOC）以欄位形式儲存。若要刪除它，請依索引找到 TOC 欄位，並移除其相關節點。

```java
Document doc = new Document("Your Directory Path" + "Table of contents.docx");
removeTableOfContents(doc, 0);
doc.save("Your Directory Path" + "RemoveContent.RemoveToc.doc");
```

*(`removeTableOfContents` 方法屬於 Aspose.Words 範例，用於移除指定的目錄節點。)*

## 常見問題與故障排除

| 症狀 | 可能原因 | 解決方式 |
|---------|--------------|-----|
| 執行程式碼後仍出現頁腳 | 文件包含未被存取的 **header/footer** 配對（例如缺少 `FOOTER_FIRST`） | 遍歷所有 `HeaderFooterType` 值，或在呼叫 `remove()` 前檢查是否為 `null`。 |
| 刪除分節符後頁面版面意外變更 | 分節的頁面設定（邊距、方向）遺失 | 在移除前將分節設定複製到目標分節。 |
| `ControlChar.PAGE_BREAK` 未被移除 | 文件使用 **section breaks** 而非分頁符字元 | 先使用「如何刪除分節符」方法。 |

## 常見問答

**問：我可以只移除特定的頁腳嗎（例如僅第一頁的頁腳）？**  
答：可以。依類型取得頁腳（`FOOTER_FIRST`），僅對該實例呼叫 `remove()`。

**問：如何在不合併內容的情況下刪除分節符？**  
答：若不需保留其內容，可直接移除 `Section` 節點，但請注意該節的所有標頭/頁腳也會一併遺失。

**問：在嘗試刪除之前，能否以程式方式偵測文件是否包含目錄？**  
答：使用 `doc.getRange().getFields()`，並檢查是否有 `FieldType.FIELD_TABLE_OF_CONTENTS` 類型的欄位。

**問：Aspose.Words 是否支援從加密的 Word 檔案中移除頁腳？**  
答：支援，只需使用密碼開啟文件：`new Document(path, new LoadOptions(password))`。

**問：移除頁腳會影響文件的分頁嗎？**  
答：移除頁腳不會改變頁碼，除非頁腳本身包含頁碼欄位。若需重新編號頁面，請相應更新頁碼欄位。

## 結論

我們已說明如何使用 Aspose.Words for Java **移除 Word** 文件的頁腳，並涵蓋相關任務，如刪除分頁符、**如何刪除分節符** 以及剔除目錄。透過這些程式碼片段，您可以產生符合應用需求的乾淨、專業文件。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Last Updated:** 2026-01-06  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

---