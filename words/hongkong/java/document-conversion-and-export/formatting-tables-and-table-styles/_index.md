---
date: 2026-10-17
description: 了解如何使用 Aspose.Words for Java 更改表格儲存格的邊框，包括設定儲存格邊框樣式、套用第一欄樣式，以及自動調整表格內容。
keywords:
- how to change borders
- apply first column style
- Aspose.Words table styling
- Java document processing
lastmod: 2026-10-17
linktitle: 如何使用 Aspose.Words for Java 更改表格儲存格的邊框
og_description: 如何使用 Aspose.Words for Java 更改表格儲存格的邊框。本指南說明如何設定儲存格邊框粗細、套用第一欄樣式，以及自動調整表格以製作專業文件。
og_image_alt: Screenshot of a Java table with customized cell borders using Aspose.Words
og_title: 如何更改表格儲存格的邊框 – Aspose.Words for Java
schemas:
- author: Aspose
  dateModified: '2026-10-17'
  description: Learn how to change borders in table cells with Aspose.Words for Java,
    including setting cell border styles, applying first column style, and auto‑fit
    table contents.
  headline: How to change borders in table cells using Aspose.Words for Java
  type: TechArticle
- description: Learn how to change borders in table cells with Aspose.Words for Java,
    including setting cell border styles, applying first column style, and auto‑fit
    table contents.
  name: How to change borders in table cells using Aspose.Words for Java
  steps:
  - name: '**Java Development Kit (JDK) 8+** – ensure `java` is on your PATH.'
    text: '**Java Development Kit (JDK) 8+** – ensure `java` is on your PATH.'
  - name: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
    text: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
  - name: '**Aspose.Words for Java** – download the latest JAR from the [official
      site](https://releases.aspose.com/words/java/).'
    text: '**Aspose.Words for Java** – download the latest JAR from the [official
      site](https://releases.aspose.com/words/java/).'
  - name: '**Basic Java knowledge** – you should be comfortable creating a Maven/Gradle
      project and adding external JARs.'
    text: '**Basic Java knowledge** – you should be comfortable creating a Maven/Gradle
      project and adding external JARs.'
  type: HowTo
- questions:
  - answer: Yes, you can create and apply custom styles programmatically. See the
      [Aspose.Words documentation](https://reference.aspose.com/words/java/) for details.
    question: Can I use custom table styles not included in the default options?
  - answer: Use standard Java logic to inspect cell values, then call the appropriate
      formatting methods (e.g., change background colour if a value exceeds a threshold).
    question: How can I apply conditional formatting to cells?
  - answer: Absolutely. After merging cells, apply shading or borders using the same
      `CellFormat` APIs.
    question: Is it possible to format merged cells the same way as regular cells?
  - answer: Adjust column widths or call `autoFit` again after inserting new data
      to recalculate the layout.
    question: What if I need the table to resize dynamically based on user input?
  - answer: The official [Aspose.Words API documentation](https://reference.aspose.com/words/java/)
      contains a comprehensive set of samples.
    question: Where can I find more examples of table styling?
  type: FAQPage
second_title: Aspose.Words Java Document Processing API
tags:
- Aspose.Words
- Java tables
- document formatting
- border styling
title: 如何使用 Aspose.Words for Java 更改表格儲存格的邊框
url: /zh-hant/java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words for Java 更改表格儲存格的邊框

## 快速解答

`DocumentBuilder` 類別用於以程式方式建立文件與表格。  
- **建立表格的主要類別是什麼？** `DocumentBuilder` 以程式方式建立表格與儲存格。  
- **如何變更單一儲存格的邊框粗細？** 使用 `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)`。  
- **我可以套用預先定義的表格樣式嗎？** 可以 – 呼叫 `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)`。  
- **哪個方法可自動調整表格以符合內容？** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`。  
- **生產環境需要授權嗎？** 非試用使用必須擁有有效的 Aspose.Words 授權。

## Aspose.Words 中「如何更改儲存格邊框」是什麼？

更改儲存格邊框是指自訂分隔儲存格的視覺線條——顏色、寬度與線型。Aspose.Words for Java 提供細緻的 API，讓您能在表格、列或單一儲存格層級設定這些屬性，從而精確控制文件的外觀。

## 為什麼使用 Aspose.Words for Java 進行表格樣式設定？

Aspose.Words 支援 **35 種以上的輸入與輸出格式**（DOCX、PDF、HTML、ODT 等），且能在一般伺服器硬體上於 **3 秒內處理 500 頁文件**，無需 Microsoft Word。此函式庫在 Windows、Linux 與 macOS 上皆表現一致，讓您能在伺服器端產生或修改文件、套用內建表格樣式（如 *首欄樣式*），並以單一方法呼叫自動調整表格以符合內容。

## 前置條件

1. **Java Development Kit (JDK) 8+** – 確保 `java` 已加入 PATH。  
2. **IDE** – IntelliJ IDEA、Eclipse，或您偏好的任何編輯器。  
3. **Aspose.Words for Java** – 從[官方網站](https://releases.aspose.com/words/java/)下載最新的 JAR。  
4. **基本的 Java 知識** – 您應熟悉建立 Maven/Gradle 專案並加入外部 JAR。

## 匯入套件

`Document`、`DocumentBuilder`、`Table`、`StyleIdentifier` 等相關類別位於 `com.aspose.words` 命名空間。匯入此套件即可取得完整的表格樣式工具箱。`DocumentBuilder` 類別提供以程式方式建構與修改文件的方法。

```java
import com.aspose.words.*;
```

## 如何更改儲存格邊框

以下是一個簡潔的逐步指南，說明如何建立表格、套用全域邊框，然後自訂單一儲存格的邊緣。

### 直接答案

`Document` 代表 Word 檔案，而 `DocumentBuilder` 用於建立如表格等內容。載入新的 `Document`，使用 `DocumentBuilder` 插入 `Table`，為整個表格設定 2 點的黑色邊框，接著將第三個儲存格的左、右、上、下邊框加粗至 4 點。此作法可讓您突顯任意儲存格，同時保持表格其餘部分的統一樣式。

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
- **全域邊框** – `table.setBorders` 為整個表格設定 2 點的黑線。  
- **儲存格底色** – 示範如何為單一儲存格著色（紅色與綠色）。  
- **自訂儲存格邊框** – 第三個儲存格的四側邊框皆設定為 4 點，使其突出。

## 套用表格樣式（含首欄樣式）

表格樣式讓您只需一次呼叫即可套用一致的外觀。我們也會啟用 *首欄樣式*，並自動調整表格以符合內容。

### 直接答案

`StyleIdentifier` 列舉內建的表格樣式，`AutoFitBehavior` 控制表格如何依內容調整。建立全新的 `Document`，建立 `Table`，將其 `StyleIdentifier` 設為 `MEDIUM_SHADING_1_ACCENT_1`，啟用 `FirstColumn` 與 `RowBands`，最後呼叫 `autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`，使欄寬自動縮放以符合插入的資料。

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
- **樣式識別碼** – `MEDIUM_SHADING_1_ACCENT_1` 為表格提供乾淨且帶陰影的外觀。  
- **首欄樣式** – 突顯首欄可提升可讀性，特別是在報告中。  
- **列帶** – 交替的列顏色使大型表格更易於閱讀。  
- **自動調整** – 確保表格寬度依內容自動調整，避免文字被截斷。

## 常見問題與故障排除

| Issue | Typical cause | Quick fix |
|-------|----------------|-----------|
| Borders not appearing | Using `clearFormatting()` after setting borders | Set borders **after** clearing formatting, or re‑apply them. |
| Shading ignored on merged cells | Shading applied before merging | Apply shading **after** merging the cells. |
| Table width exceeds page margins | No auto‑fit applied | Call `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` or set a fixed width. |
| Style not applied | Wrong `StyleIdentifier` value | Verify the identifier exists in the version of Aspose.Words you’re using. |

翻譯後的表格：

| 問題 | 常見原因 | 快速解決方案 |
|------|----------|--------------|
| 邊框未顯示 | 在設定邊框後使用 `clearFormatting()` | 在清除格式後 **設定** 邊框，或重新套用。 |
| 合併儲存格的底色被忽略 | 在合併之前套用底色 | 在合併儲存格後 **套用** 底色。 |
| 表格寬度超出頁面邊距 | 未套用自動調整 | 呼叫 `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` 或設定固定寬度。 |
| 樣式未套用 | `StyleIdentifier` 值錯誤 | 確認您使用的 Aspose.Words 版本中存在該識別碼。 |

## 常見問答

**Q: 我可以使用預設選項未包含的自訂表格樣式嗎？**  
A: 可以，您可以以程式方式建立並套用自訂樣式。詳情請參閱 [Aspose.Words 文件](https://reference.aspose.com/words/java/)。

**Q: 如何對儲存格套用條件格式？**  
A: 使用標準的 Java 邏輯檢查儲存格值，然後呼叫相應的格式化方法（例如，若值超過閾值則變更背景顏色）。

**Q: 合併儲存格能以與普通儲存格相同的方式格式化嗎？**  
A: 完全可以。合併儲存格後，使用相同的 `CellFormat` API 來套用底色或邊框。

**Q: 如果需要根據使用者輸入動態調整表格大小該怎麼辦？**  
A: 調整欄寬或在插入新資料後再次呼叫 `autoFit` 以重新計算版面配置。

**Q: 哪裡可以找到更多表格樣式的範例？**  
A: 官方的 [Aspose.Words API 文件](https://reference.aspose.com/words/java/) 包含完整的範例集。

## 結論

您現在已擁有完整的工具箱，可使用 Aspose.Words for Java **更改表格儲存格的邊框**、套用 *首欄樣式*，以及 **自動調整表格內容**。掌握這些技巧後，您能產出資料豐富且視覺精緻的文件——非常適合報告、發票及任何關鍵商業輸出。

---

**最後更新：** 2026-10-17  
**測試環境：** Aspose.Words for Java 24.12 (latest at time of writing)  
**作者：** Aspose

## 相關教學

- [Aspose.Words Java 格式與樣式教學 - 強化您的文件](/words/java/formatting-styles/)
- [使用 Aspose.Words for Java 的進階文件邊框：完整指南](/words/java/headers-footers-page-setup/advanced-document-borders-aspose-words-java/)
- [使用 Aspose.Words for Java 為文件添加浮水印](/words/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}