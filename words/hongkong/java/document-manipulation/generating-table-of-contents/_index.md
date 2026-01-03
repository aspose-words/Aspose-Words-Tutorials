---
date: 2026-01-03
description: 了解如何在使用 Aspose.Words for Java 插入目錄時調整頁碼。自訂目錄樣式，輕鬆建立文件。
linktitle: Generating Table of Contents
second_title: Aspose.Words Java Document Processing API
title: 調整頁碼並使用 Aspose.Words for Java 產生目錄
url: /zh-hant/java/document-manipulation/generating-table-of-contents/
weight: 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 調整頁碼並在 Aspose.Words for Java 中產生目錄

在本教學中，您將了解如何 **調整頁碼** 以及 **插入目錄** (TOC) 使用 Aspose.Words for Java。結構良好的目錄可讓長文件更易於瀏覽，微調頁碼對齊則能為讀者提供專業的體驗。我們將逐步說明如何建立文件、客製化目錄樣式，以及調整定位點，使頁碼精確對齊至您想要的位置。

## 快速解答
- **「調整頁碼」是什麼意思？** 修改目錄中對齊頁碼的定位點。  
- **我可以自動插入目錄嗎？** 是 – 使用 `FieldToc` 類別。  
- **我需要授權才能執行程式碼嗎？** 免費試用可用於開發；正式環境需購買授權。  
- **支援哪個 Aspose 版本？** 這些範例適用於最新的 Aspose.Words for Java 版本。  
- **可以自訂目錄樣式嗎？** 當然可以 – 您可以變更字型、粗體等設定。

## 什麼是 Aspose.Words 中的目錄？
目錄（TOC）是一個欄位，會掃描文件中的標題樣式（例如 Heading 1、Heading 2），並產生帶有頁碼的條目清單。Aspose.Words 允許您以程式方式插入此欄位，並完整控制其外觀。

## 為什麼要在目錄中調整頁碼？
調整定位點可讓您精確控制頁碼顯示位置，這對於以下需求至關重要：
- 保持整潔、欄位對齊的版面。  
- 符合公司樣式指南。  
- 提升列印與數位文件的可讀性。

## 前置條件
- 已在專案中加入 Aspose.Words for Java（Maven/Gradle）。  
- 具備基本的 Java 語法知識。  

## 步驟說明

### 步驟 1：建立新文件
首先，實例化一個空的 `Document` 物件，用於保存您的內容與目錄。

```java
Document doc = new Document();
```

### 步驟 2：自訂目錄樣式
您可以變更每個目錄層級的外觀。在此範例中，我們將第一層條目設為粗體，這是常見的格式需求。

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

### 步驟 3：向文件添加內容
插入標題（例如 `Heading1`、`Heading2`）以及一般段落。目錄欄位稍後會自動抓取這些標題。（*為簡潔起見省略程式碼 – 重點在於產生目錄。*）

### 步驟 4：插入目錄欄位
將目錄放置在您希望的位置——通常是文件的開頭。

```java
// Insert a TOC field at the desired location in your document.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

### 步驟 5：保存文件
將文件寫入磁碟。您可以選擇任何支援的格式，如 DOCX、PDF 或 HTML。

```java
doc.save("your_output_path_here");
```

## 自訂目錄中的定位點（調整頁碼）
如果預設的定位點未能如您所需對齊頁碼，您可以遍歷所有目錄段落並修改其定位點位置。

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Get the first tab used in this paragraph, which aligns the page numbers.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Remove the old tab.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Insert a new tab at a modified position (e.g., 50 units to the left).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

現在目錄條目的頁碼會精確顯示在您想要的位置，為文件增添精緻外觀。

## 常見問題與技巧
- **目錄中缺少標題：** 確保您的標題使用內建樣式（`Heading1`、`Heading2` 等）或將自訂樣式對映至目錄層級。  
- **定位點未套用：** 確認該段落實際屬於 TOC 樣式（`TOC_1`‑`TOC_9`）。  
- **大型文件的效能：** 在插入目錄後呼叫 `doc.updateFields()`，一次性刷新條目。  

## 常見問答

**Q: 如何變更目錄條目的格式？**  
A: 使用 `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)`（*X* 為層級 1‑9），並修改其字型、顏色或段落設定。

**Q: 如何為目錄新增更多層級？**  
A: 調整 `FieldToc` 的開關 `\o \"1-3\"`（例如）以納入更多標題層級，然後更新相應的 `TOC_X` 樣式。

**Q: 能否為特定目錄條目變更定位點位置？**  
A: 可以 – 如「自訂定位點」章節所示，遍歷段落並逐一修改每個定位點。

**Q: 能否在 PDF 輸出中產生目錄？**  
A: 當然可以。目錄產生後，將文件另存為 PDF（`doc.save(\"output.pdf\")`），欄位會自動呈現。

**Q: 是否需要手動呼叫 `updateFields()`？**  
A: 插入 `FieldToc` 後，Aspose.Words 會在保存時自動更新，但呼叫 `doc.updateFields()` 可立即取得結果，方便除錯。

## 結論
您已學會如何 **調整頁碼**、**插入目錄**，以及使用 Aspose.Words for Java **自訂目錄樣式**。這些技巧可讓您建立清晰、易於導覽且符合任何出版標準的專業文件。

---  

**最後更新：** 2026-01-03  
**測試環境：** Aspose.Words for Java（最新版本）  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}