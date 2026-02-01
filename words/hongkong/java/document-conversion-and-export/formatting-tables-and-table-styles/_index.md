---
date: 2026-02-01
description: 學習如何格式化表格、套用表格樣式、設定表格邊框，以及使用 Aspose.Words for Java 自動調整表格大小。本指南將帶您一步步建立具專業樣式的
  Word 表格。
linktitle: Formatting Tables and Table Styles
second_title: Aspose.Words Java Document Processing API
title: 如何使用 Aspose.Words for Java 格式化表格並套用表格樣式
url: /zh-hant/java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words for Java 格式化表格並套

當您需要 **如何格式化表格** 在 Word 文件中時，Aspose.Words for Java 為您提供完整的工具組，讓您能以程式方式建立、樣表格格式化都能讓資料呈現得清格邊框、套用儲存格底色、使用自動調整表格功能，並套用預定義的表格樣式——全部以易於跟隨的 Java 程式碼示範。

## 快速解答
- **建立表格的主要類別是什麼？** `DocumentBuilder` 用於建立和填充表格。  
- **如何為整個表格設定邊框？** 使用 `table.setBordersStyleIdentifier(Style哪個方法可自動調整欄S)`。  
- **是否可以使用條件格式化？** 您可以在程式碼中根據任何條件以程式方式變更儲存格底色或邊框。  

## 什麼是 Aspose.Words 中的表格格式化？

表格格式化是指定義視覺屬性——邊框、底與整體樣式——的過程，使表格看起來精緻且符合文件的設計語言。使用 Aspose.Words，您可以從 Java 完全掌控 Word 表格的每個細節。

## 為什麼要套用表格樣式？

套用表格樣式可免除手動設定每個屬性。像 **MEDIUM_SHADING_1_ACCENT_1** 這類樣式會自動格式化標題列、條紋列與第一欄，讓多個表格保持一致的外觀。

## 前置條件DK) 8+** – 執行 Aspose.Words Java 的編輯器。  
 從 [here](https://releases.aspose** – 以便了解以下程式碼片段。  

## 匯入套件

要開始，匯入 Aspose.Words 命名空間：

```java
import com.aspose.words.*;
```

此單一匯入即提供建立與格式化表格所需的全部類別。

## 步驟 1：格式化表格

### 載入文件

首先，建立一個空白文件，並建立一個可協助插入內容的 `DocumentBuilder`。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

###並套用儲存格底色，以說明如何 **設定表格邊框** 與 **建立 word table** 儲存格的不同背景顏色。

```java
Table table = builder.startTable();
builder.insertCell();

// Set the borders for the entire table.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Set the cell shading for this cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Specify a different cell shading for the second cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### 自訂儲存格粗的邊框。

```java
// Clear the cell formatting from previous operations.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Create larger borders for the first cell of this row.
builder.getCellFormat().getBorders().getLeft().setLineWidth(4.0);
builder.getCellFormat().getBorders().getRight().setLineWidth(4.0);
builder.getCellFormat().getBorders().getTop().setLineWidth(4.0);
builder.getCellFormat().getBorders().getBottom().setLineWidth(4.0);
builder.writeln("Cell #3");

builder.insertCell();
builder.getCellFormat().clearFormatting();
builder.writeln("Cell #4");
        
doc.save("FormatTableAndCellWithDifferentBorders.docx");
```

#### 說明

- **設定邊框：** `table.setBorders` 為整個表格定義單線、2 點粗的邊框。  
- **儲存格底色：** 背景顏色（紅、綠）使每個儲存格突出。  
- **儲存格邊框：** 第三個儲存格的粗的邊框，示範如何套用表格樣式

### 建立文件與表格

列。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

###特定樣式選項，例如條紋列與突顯的第一欄。

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### 新增表格資料

現在填入示範資料。請注意 **auto fit table** 的使用，可自動調整欄寬。

```java
builder.writeln("Item");
builder.getCellFormat().setRightPadding(40.0);
builder.insertCell();
builder.writeln("Quantity (kg)");
builder.endRow();

builder.insertCell();
builder.writeln("Apples");
builder.insertCell();
builder.writeln("20");
builder.endRow();

builder.insertCell();
builder.writeln("Bananas");
builder.insertCell();
builder.writeln("40");
builder.endRow();

builder.insertCell();
builder.writeln("Carrots");
builder.insertCell();
builder.writeln("50");
builder.endRow();

doc.save("BuildTableWithStyle.docx");
```

#### 說明

- **設定表格樣式：** `MEDIUM_SHADING_1_ACCENT_1` 提供乾淨且帶底紋的外觀。  
- **樣式選項：條紋與首列會自動套用格式。  
- **自動調整：** `AUTO_FIT_TO_CONTENTS`。  

## 常見問題與解決方案

| 問題 | 解決方案 |
|------|----------|
| 邊框未 **before**，或在修改後重新整理 builder。 |
| 合併儲存格未套用底色 | 在合併儲存格 **after** 後套用底色，使用| 表格寬度超出頁面邊_TO_CONTENTS)` 或設定明確的欄寬。 |
| 迭代列/儲存格，根據業務邏輯套用底色或邊框。 |

## 常見問答

**Q: 我可以使用未包含在預？**  
A: 是的，您可以使用 Aspose.Words for Java 定義並套用自訂樣式到表格。請參閱 [documentation](https://reference.aspose.com/words/java/) 以取得有關建立自訂樣式的更多資訊件格式化？**  
A: 方法（例如 `setBackgroundPatternColor`、`getBorders().setLineWidth`），即可動態樣式化儲存格。

**Q: 我可以格式化表格中的合併儲存格嗎？**  
A: 當然可以。使用 `Cell.merge` 合併儲存格後，對合併後的儲存格套框，即可看到變更。

**Q: 是否可以動態調整表格版面？**  
A: 可以，您可以在執行時根據內容或使用者輸入修改儲存格寬度、表格寬度，並套用 `autoFit`。

**Q: 我在哪裡可以取得更多關於表格考，請造訪 [Aspose.Words API documentation](https://reference.aspose.com/words/java/)。  

---

**最後更新：** ** Aspose.Words for Java 24.12（撰寫時的最新版本）  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}