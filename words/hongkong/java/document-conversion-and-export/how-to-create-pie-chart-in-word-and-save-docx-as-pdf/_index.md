---
category: general
date: 2026-11-15
description: 學習如何在 Word 文件中建立圓餅圖，並使用 Java 將 docx 另存為 PDF。本指南亦涵蓋將 Word 轉換為 PDF 以及如何加入圖表。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: zh-hant
lastmod: 2026-11-15
og_description: 使用 Java 在 Word 檔案中建立圓餅圖，並將 docx 另存為 PDF。跟隨此一步一步的教學，將 Word 轉換為 PDF
  並加入圖表。
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: 在 Word 中建立圓餅圖並將 docx 另存為 PDF – Java 指南
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: 如何在 Word 中建立圓餅圖並將 docx 另存為 PDF
url: /zh-hant/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中建立圓餅圖並將 docx 儲存為 PDF

如果您需要在 Word 文件中 **create pie chart** 並且 **save docx as PDF**，本教學會完整說明。您將看到一個完整、可執行的範例，將 .docx 檔案轉換為 PDF 並嵌入圓餅圖，讓您能夠回答「how to add chart」而不必四處搜尋零散的程式碼片段。

在本指南中您將學會：

* 載入現有的 *.docx*（或從頭開始）  
* 使用 Aspose.Words for Java 來 **create pie chart** 並填入資料  
* **Save docx as PDF**，圖表正確呈現  
* 了解在圖表相關情況下 **convert word to pdf** 的細節  

這些步驟適用於 Aspose.Words 2024‑x.x 與 Java 17，但概念同樣適用於任何支援 Word 圖表操作的函式庫。

## 前置條件

在開始之前，請確保您具備：

| 需求 | 原因說明 |
|-------------|----------------|
| Java 17 (or later) | 需要最新的 Aspose.Words JAR |
| Maven or Gradle build tool | 簡化相依性管理 |
| Aspose.Words for Java (latest version) | 提供 `Document`、`Chart` 與 `ChartType` 類別 |
| An input **.docx** file (or a blank document) | 圖表將插入此檔案 |

將 Aspose.Words 相依性加入您的 `pom.xml`（Maven）或 `build.gradle`（Gradle）。以下為 Maven 範例：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## 步驟 1：載入 Word 文件（或建立新文件）

第一步是取得 `Document` 例項。如果您已有範本，傳入其路徑；否則建立空白文件。

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*Why this step?* `Document` 物件是所有 Word 內容（包括圖表）的容器。載入現有檔案可保留周圍文字與樣式，同時加入新的視覺元素。

## 步驟 2：**Create pie chart** – “how to create chart” 的核心

現在我們以 `ChartType.PIE` 來實例化 `Chart` 物件。此動作會自動建立一個圓餅圖佔位符，之後可填入資料。

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*Explanation*: `ChartType.PIE` 告訴 Aspose.Words 使用圓餅圖範本。圖表會被加入文件的正文中，因而出現在您需要的位置。這在一次呼叫中即滿足了 “how to add chart” 的需求。

## 步驟 3：填入圖表資料 – 以資料回應 “how to add chart”

沒有系列資料的圓餅圖是沒有意義的。使用 `Series` 集合加入類別與數值。

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*Why this matters*: 每次呼叫 `add` 都會產生圓餅圖的一個切片。第一個參數是標籤，第二個參數是數值。您可以將其替換為來自資料庫或 CSV 檔的動態資料。

### 可選：自訂外觀（非必要但有用）

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

這些調整示範了如何在 Java 程式碼中 **how to create chart**，打造專業外觀，而無需離開程式碼。

## 步驟 4：**Save docx as PDF** – “convert word to pdf” 的最後一步

圖表嵌入後，將文件匯出為 PDF。Aspose.Words 會將圖表渲染為向量圖形，保留品質。

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*Key point*: `save` 方法會自動將 Word 檔案轉換為 PDF，處理圖表光柵化、字型嵌入與頁面版面配置。這達成 **save docx as pdf** 目標，並示範在圖表存在時可靠的 **convert word to pdf** 方式。

### 預期輸出

執行程式會產生 `output.pdf`，內容包含：

* `input.docx` 的原始內容（若有）  
* 完整呈現的圓餅圖，標題為 *Sales Distribution Q1*  
* 與資料相符的切片百分比（40 %，30 %，30 %）

在任何 PDF 檢視器中開啟，即可看到清晰的圓餅圖，與 Word 檔案中顯示的完全相同。

## 常見陷阱與避免方法

| 問題 | 原因 | 解決方案 |
|-------|-------|-----|
| PDF 中圖表顯示為空白 | 缺少字型或圖表渲染設定 | 確保使用最新的 Aspose.Words 版本；它已捆綁所需的渲染函式庫。 |
| 資料值四捨五入不正確 | 使用大型整數值 | 提供 `double` 型別的值，或在加入系列前先對數字做縮放。 |
| 輸出 PDF 體積過大 | 嵌入的影像 DPI 較高 | 若同時嵌入影像，請設定 `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)`。 |
| “convert word to pdf” 拋出 `UnsupportedOperationException` | 使用較舊的 Java 版本（< 11） | 升級至 Java 17 或更新版本，Aspose.Words 24.x 需要此版本。 |

## 專業提示：重複使用圖表建立邏輯

如果需要在同一文件中加入多個圖表，請將圖表建立程式碼抽取為輔助方法：

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

現在您可以對每個資料集呼叫 `doc.getFirstSection().getBody().appendChild(createPieChart(...));`，保持程式碼 DRY（不要重複自己）。

## 結論

您現在已了解如何在 Word 文件中 **create pie chart**，填入資料，並使用 Java **save docx as PDF**。此端對端範例涵蓋完整的 **convert word to pdf** 工作流程，回答 **how to add chart**，並示範以程式方式 **how to create chart**。

從此您可以探索：

* 加入長條圖或折線圖 (`ChartType.BAR`, `ChartType.LINE`) – 另一個 **how to create chart** 情境。  
* 匯出為其他格式，如 PNG 或 HTML (`SaveFormat.PNG`, `SaveFormat.HTML`)。  
* 在插入圖表前，以表格或佔位符動態產生輸入文件。

歡迎嘗試不同的資料集、樣式選項，甚至在每頁嵌入多個圖表。祝開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南技術緊密相關的主題，並提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，或在自己的專案中探索其他實作方式。

- [如何使用 Java 在 Word 文件中插入圓餅圖](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [如何在 Java 中將 Word 儲存為 PDF 並建立可存取的 PDF](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [如何使用 Java 與 Aspose.Words 在 Word 中建立圖表](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}