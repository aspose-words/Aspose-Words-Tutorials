---
category: general
date: 2026-09-11
description: 使用 Aspose.Words for Java 編輯環形圖後儲存 Word 文件。了解如何調整環形圖孔徑、旋轉環形圖以及編輯環形圖屬性。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: zh-hant
lastmod: 2026-09-11
og_description: 使用 Aspose.Words for Java 編輯環形圖後儲存 Word 文件。本教學示範如何變更環形圖的孔洞大小、旋轉環形圖以及自訂圖表外觀。
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: 編輯環形圖後儲存 Word 文件 – Java 指南
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: 在 Java 中編輯環形圖後儲存 Word 文件
url: /zh-hant/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中編輯環形圖後儲存 Word 文件

如果您需要 **儲存 Word 文件**，且其中包含自訂的環形圖，本指南將一步步說明如何操作。只需幾行 Java 程式碼，即可更改環形圖的內孔、旋轉環形圖，然後將結果寫回磁碟。

您將看到一個完整且可執行的範例，使用 Aspose.Words for Java，並提供處理多個圖表、驗證節點類型以及避免常見陷阱的技巧。無需任何外部參考——所有必要內容皆已包含。

## 前置條件

- 已安裝 Java 17 或更新版本
- 使用 Maven 或 Gradle 來管理相依性
- 已在專案中加入 Aspose.Words for Java（版本 23.9 或更新）  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- 一個包含單一環形圖的 Word 檔案（`input.docx`）

## 步驟 1：載入 Word 文件

第一步是開啟來源檔案。此步驟至關重要，因為之後的所有操作皆在記憶體中的 `Document` 物件上執行。

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **為什麼？** 載入文件會建立 DOM 表示，使您能遍歷圖形、表格與圖表。如果檔案無法開啟，Aspose.Words 會拋出例外，讓您立即知道路徑錯誤。

## 步驟 2：定位環形圖形狀

圖表儲存在 `Shape` 節點內。我們取得第一個包含圖表的形狀，並將其渲染器轉型為 `Chart`。

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **為什麼？** 檢查 `isChart()` 可避免在文件中圖表前有圖像或其他形狀時發生 `ClassCastException`。這使得程式碼在含有混合內容的文件中更具韌性。

## 步驟 3：變更環形孔大小  

現在我們編輯環形孔。`setHoleSize` 方法接受圖表半徑的百分比（10 – 90）。

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **為什麼？** 更改環形孔（`change doughnut hole` / `change chart hole size`）可強調或淡化中心區域。超出 10‑90 % 的值會被 API 忽略。

## 步驟 4：旋轉環形圖  

要控制第一片開始的位置，請設定第一片角度。這等同於 **旋轉環形圖**。

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **為什麼？** 旋轉圖表在您希望特定切片位於頂部或符合設計規範時非常有用。

## 步驟 5：儲存更新後的文件  

最後，將變更寫回新檔案。此時您會 **儲存 Word 文件**，其中包含已編輯的圖表。

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **預期結果：** `output.docx` 包含原始內容，但環形圖的孔徑已變為 30 %，且第一片從 45 ° 開始。使用 Microsoft Word 開啟檔案時，將顯示已變更的圖表。

## 完整可執行範例

以下是完整程式碼，您可以直接複製貼上到 IDE 中。它包含所有匯入與錯誤處理，能安全地 **編輯環形圖** 並 **儲存 Word 文件**。

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### 預期輸出

當您開啟 `output.docx` 時：

- 環形圖的中心孔大約佔圖表半徑的三分之一。  
- 第一片從 45 度位置開始，使整個圖表順時針旋轉。

兩項視覺變更會立即在 Word 中呈現。

## 常見變化與邊緣情況

| 情況 | 處理方式 |
|-----------|----------------|
| **Multiple charts** | 迭代 `doc.getChildNodes(NodeType.SHAPE, true)`，篩選 `shape.isChart()`；對每個 `Chart` 套用 `setHoleSize` / `setFirstSliceAngle`。 |
| **Chart is not a doughnut** | 檢查 `chart.getType()`；僅在 `chart.getType() == ChartType.DOUGHNUT` 時呼叫 `setHoleSize`。 |
| **Need to change hole size dynamically** | 根據資料值計算所需的百分比，然後呼叫 `setHoleSize(computedValue)`。 |
| **Saving to a stream** | 使用

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎。每個資源都提供完整的可執行程式碼範例與逐步說明，協助您精通其他 API 功能，並在自己的專案中探索替代實作方式。

- [如何使用 Aspose.Words for Java 建立柱狀圖](/words/english/java/document-conversion-and-export/using-charts/)
- [如何使用 Aspose.Words for Java 將文件另存為 PDF](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [使用 Aspose.Words for Java 為 Word 加密儲存](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}