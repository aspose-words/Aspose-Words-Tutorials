---
date: 2025-11-28
description: 了解如何使用 Aspose.Words for Java 更改儲存格邊框與格式化表格。本分步指南涵蓋設定邊框、套用首欄樣式、自動調整表格內容以及套用表格樣式。
language: zh-hant
linktitle: How to Change Cell Borders in Tables – Aspose.Words for Java
second_title: Aspose.Words Java Document Processing API
title: 如何在表格中更改儲存格邊框 – Aspose.Words for Java
url: /java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何在表格中變更儲存格邊框 – Aspose.Words for Java

## 介紹

在文件排版中，表格扮演關鍵角色，**了解如何變更儲存格邊框**是打造清晰、專業版面的必要技巧。若您使用 Java 與 Aspose.Words 開發，已擁有一套強大的工具箱。本教學將完整說明表格排版、變更儲存格邊框、套用 *首欄樣式*，以及使用 *自動調整表格內容* 讓文件更精緻的全過程。

## 快速解答
- **建立表格的主要類別是什麼？** `DocumentBuilder` 以程式方式建立表格與儲存格。  
- **如何變更單一儲存格的邊框粗細？** 使用 `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)`。  
- **我可以套用預先定義的表格樣式嗎？** 可以 – 呼叫 `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)`。  
- **哪個方法可讓表格自動適應內容？** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`。  
- **正式環境需要授權嗎？** 非試用版使用時必須擁有有效的 Aspose.Words 授權。

## 什麼是 Aspose.Words 中的「變更儲存格邊框」？

變更儲存格邊框即是自訂分隔儲存格的視覺線條——包括顏色、寬度與線型。Aspose.Words 提供完整的 API，讓您在表格、列或單一儲存格層級調整這些屬性，從而精細控制文件的外觀。

## 為什麼使用 Aspose.Words for Java 進行表格樣式設定？

- **跨平台外觀一致** – 相同的樣式程式碼可在 Windows、Linux 與 macOS 上執行。  
- **不依賴 Microsoft Word** – 可在伺服器端產生或修改文件。  
- **豐富的樣式庫** – 內建表格樣式（如 *首欄樣式*）與完整的自動調整功能。  

## 前置條件

1. **Java Development Kit (JDK) 8+** – 確認 `java` 已加入 PATH。  
2. **IDE** – IntelliJ IDEA、Eclipse，或任何您慣用的編輯器。  
3. **Aspose.Words for Java** – 從[官方網站](https://releases.aspose.com/words/java/)下載最新 JAR。  
4. **基本的 Java 知識** – 您應該能建立 Maven/Gradle 專案並加入外部 JAR。

## 匯入套件

開始操作表格前，需要匯入 Aspose.Words 的核心類別：

```java
import com.aspose.words.*;
```

這一行匯入即可使用 `Document`、`DocumentBuilder`、`Table`、`StyleIdentifier` 等多項實用工具。

## 如何變更儲存格邊框

以下示範如何建立簡易表格、變更整體邊框，接著自訂單一儲存格。

### 步驟 1：載入新文件

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### 步驟 2：建立表格並設定全域邊框

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

### 步驟 3：變更單一儲存格的邊框

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

#### 程式碼說明
- **全域邊框** – `table.setBorders` 為整個表格設定 2 點的黑色線條。  
- **儲存格底紋** – 示範如何為單一儲存格上色（紅色與綠色）。  
- **自訂儲存格邊框** – 第三個儲存格的四側皆設定 4 點邊框，使其突顯。

## 套用表格樣式（含首欄樣式）

表格樣式讓您只需一次呼叫即可套用一致的外觀。我們同時示範如何啟用 *首欄樣式* 並自動調整表格寬度以符合內容。

### 步驟 4：建立新文件以套用樣式

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### 步驟 5：套用預定義樣式並啟用首欄格式

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### 步驟 6：填入資料至表格

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

#### 為什麼這很重要
- **樣式識別碼** – `MEDIUM_SHADING_1_ACCENT_1` 為表格提供乾淨、帶底紋的外觀。  
- **首欄樣式** – 突顯第一欄可提升可讀性，特別是在報告中。  
- **列帶** – 交替的列底色讓大型表格更易於閱讀。  
- **自動調整** – 確保表格寬度依內容自動變化，避免文字被截斷。

## 常見問題與疑難排解

| 問題 | 常見原因 | 快速解決方案 |
|------|----------|--------------|
| 邊框未顯示 | 在設定邊框後使用了 `clearFormatting()` | **在** 清除格式後再設定邊框，或重新套用邊框。 |
| 合併儲存格的底紋被忽略 | 底紋在合併之前就已設定 | **在** 合併儲存格之後再套用底紋。 |
| 表格寬度超出頁邊距 | 未執行自動調整 | 呼叫 `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` 或設定固定寬度。 |
| 樣式未套用 | 使用了錯誤的 `StyleIdentifier` 值 | 確認該識別碼在您使用的 Aspose.Words 版本中存在。 |

## 常見問答

**Q: 我可以使用預設選項之外的自訂表格樣式嗎？**  
A: 可以，您可以以程式方式建立並套用自訂樣式。詳情請參考 [Aspose.Words 文件](https://reference.aspose.com/words/java/)。

**Q: 如何對儲存格套用條件格式？**  
A: 使用標準的 Java 邏輯檢查儲存格值，然後呼叫相應的格式化方法（例如，當數值超過門檻時變更背景顏色）。

**Q: 合併儲存格能否像一般儲存格一樣進行格式設定？**  
A: 完全可以。合併儲存格後，使用相同的 `CellFormat` API 來套用底紋或邊框。

**Q: 若需根據使用者輸入動態調整表格大小，該怎麼做？**  
A: 在插入新資料後調整欄寬或再次呼叫 `autoFit`，以重新計算版面配置。

**Q: 哪裡可以找到更多表格樣式的範例？**  
A: 官方的 [Aspose.Words API 文件](https://reference.aspose.com/words/java/) 提供了完整的範例集。

## 結論

現在您已掌握 **變更儲存格邊框**、套用 *首欄樣式*，以及使用 Aspose.Words for Java **自動調整表格內容** 的完整工具箱。熟練這些技巧後，您可以產出資料豐富且視覺美觀的文件，適用於報告、發票及任何商業關鍵的輸出。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**最後更新：** 2025-11-28  
**測試於：** Aspose.Words for Java 24.12 (撰寫時最新版本)  
**作者：** Aspose