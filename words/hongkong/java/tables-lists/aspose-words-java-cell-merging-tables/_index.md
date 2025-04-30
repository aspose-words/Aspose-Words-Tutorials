---
"date": "2025-03-28"
"description": "了解如何使用 Aspose.Words for Java 掌握表格中的垂直和水平儲存格合併。本指南涵蓋設定、實施和實際應用。"
"title": "使用 Aspose.Words Java 掌握表格中的儲存格合併&#58;垂直和水平技術"
"url": "/zh-hant/java/tables-lists/aspose-words-java-cell-merging-tables/"
"weight": 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}


# 使用 Aspose.Words Java 掌握表格中的垂直和水平單元格合併

## 介紹
在文件自動化中，操作表格單元格格式對於增強資料呈現至關重要。無論是建立發票還是報告，合併儲存格都可以提高可讀性和美觀性。控制垂直和水平合併可能具有挑戰性。

Aspose.Words for Java 透過強大的 API 簡化了這些任務，輕鬆建立具有專業外觀的文件。本教學將引導您使用 Java 中的 Aspose.Words 掌握儲存格合併。

### 您將學到什麼：
- 使用 Aspose.Words Java 垂直和水平合併儲存格
- 使用 Maven 或 Gradle 依賴項設定您的環境
- 實作實用的程式碼片段
- 常見問題故障排除

首先，請確保您已準備好後續操作所需的一切。

## 先決條件
在深入進行單元合併之前，請確保您擁有必要的工具和知識：

### 所需的庫和相依性：
1. **Aspose.Words for Java**：以程式設計方式操作 Word 文件的主要函式庫。
2. **JUnit 5（TestNG）**：用於運行測試案例，如程式碼片段所示。

### 環境設定要求：
- 可用的 Java 開發工具包 (JDK) 8 或更高版本
- 整合開發環境 (IDE)，例如 IntelliJ IDEA、Eclipse 或 NetBeans

### 知識前提：
- 對 Java 程式設計有基本的了解
- 熟悉 Maven 或 Gradle 建置工具以進行依賴管理

## 設定 Aspose.Words
若要開始合併儲存格，請在專案中設定 Aspose.Words。

### 新增依賴項：
**Maven：**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle：**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### 許可證取得：
Aspose.Words for Java 採用商業許可，但您可以先免費試用以探索其功能：
1. **免費試用**：從下載 Aspose.Words 庫 [官方網站](https://releases.aspose.com/words/java/) 並可無限制地開始使用 30 天。
2. **臨時執照**：造訪以下網址取得臨時許可證 [Aspose 的許可頁面](https://purchase.aspose.com/temporary-license/) 如果您希望在試用期結束後繼續測試。
3. **購買**：如需長期使用，請考慮從 [購買頁面](https://purchase。aspose.com/buy).

### 基本初始化：
若要啟動您的項目，請初始化 `Document` 和 `DocumentBuilder` 類別如下：
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
這將設定一個用於建立表格的空白文件。

## 實施指南
讓我們將合併表格單元格的流程分解為可管理的步驟，並專注於垂直和水平合併。

### 垂直單元格合併

#### 概述：
垂直儲存格合併將多行合併到一列中，非常適合建立標題或將相關資訊分組。

#### 逐步實施：
**1.建立文檔和建構器：**
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

**2. 插入垂直合併儲存格：**

- **第一個儲存格（合併開始）：** 設定為垂直合併的開始。
  ```java
  builder.insertCell();
  builder.getCellFormat().setVerticalMerge(CellMerge.FIRST); // 將此儲存格標記為合併的起點。
  builder.write("Text in merged cells.");
  ```

- **第二個儲存格（非合併）：**
  ```java
  builder.insertCell();
  builder.getCellFormat().setVerticalMerge(CellMerge.NONE); // 這裡不應用合併。
  builder.write("Text in unmerged cell.");
  builder.endRow(); // 結束目前行。
  ```

- **第三個儲存格（繼續合併）：** 與第一個儲存格垂直合併。
  ```java
  builder.insertCell();
  builder.getCellFormat().setVerticalMerge(CellMerge.PREVIOUS); // 從前一個單元格繼續垂直合併。
  builder.endRow(); // 完成第二行。
  ```

**3.儲存文件：**
```java
doc.save("VerticalMergeOutput.docx");
```

### 水平單元格合併

#### 概述：
水平合併將單元格組合到一行中，非常適合創建綜合標題或跨越資訊。

#### 逐步實施：
**1.建立文檔和建構器：**
重複使用與先前相同的初始化程式碼。

**2. 插入水平合併儲存格：**

- **第一個儲存格（合併開始）：**
  ```java
  builder.insertCell();
  builder.getCellFormat().setHorizontalMerge(CellMerge.FIRST); // 開始水平合併。
  builder.write("Text in merged cells.");
  ```

- **第二個儲存格（繼續合併）：**
  ```java
  builder.insertCell();
  builder.getCellFormat().setHorizontalMerge(CellMerge.PREVIOUS); // 從第一個單元格水平繼續。
  builder.endRow(); // 結束目前行，完成水平合併。
  ```

**3.儲存文件：**
```java
doc.save("HorizontalMergeOutput.docx");
```

### 單元格填充

#### 概述：
透過在儲存格中新增填充可以在文字和邊框之間建立空白來增強可讀性。

#### 逐步實施：
**1. 設定單元格的填充：**
```java
builder.getCellFormat().setPaddings(5.0, 10.0, 40.0, 50.0); // 頂部、右側、底部、左側的填滿（以點為單位）。
```

**2. 插入有填充的儲存格：**
```java
builder.startTable();
builder.insertCell();
builder.write("Lorem ipsum dolor sit amet...");
builder.endRow();
builder.endTable();
doc.save("PaddingOutput.docx");
```

## 實際應用
了解如何合併儲存格和新增填充可以透過多種方式增強文件：
1. **發票創建**：對跨越多行的項目描述使用垂直合併，提高清晰度。
2. **報告生成**：水平合併非常適合跨表的統一部分標題。
3. **履歷模板**：添加填充以確保簡歷部分內的文字看起來舒適。

## 性能考慮
處理大型文件或大量表格操作時：
- **優化文檔載入：** 使用 `Document` 如果可能的話，透過僅載入文件的必要部分來有效地建構函數。
- **批次：** 將多個儲存格格式變更組合成單一操作，以最大限度地減少處理開銷。

## 結論
使用 Aspose.Words for Java 合併表格中的儲存格可增強文件自動化專案。透過掌握垂直和水平合併以及添加填充，您就可以建立精美的文件。

### 後續步驟：
- 進一步試驗 Aspose.Words 功能。
- 探索表格樣式或影像插入等附加功能，以進一步豐富您的文件。

## 常見問題部分
**問題 1：我可以垂直合併兩個以上的儲存格嗎？**
A1：是的，繼續設置 `CellMerge.PREVIOUS` 對於您希望包含在垂直合併中的每個儲存格。

**問題 2：將文件轉換為 PDF 時如何處理合併儲存格？**
A2：Aspose.Words 可以跨格式一致地處理格式。確保在轉換之前正確設定合併。

**Q3：合併有影像或複雜內容的儲存格是否有限制？**
A3：基本文字可以無縫運行，但請確保任何複雜元素在合併過程中保持其格式。

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}