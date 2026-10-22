---
category: general
date: 2026-10-04
description: 學習如何在 Word 圖表中分離切片、分離圓餅圖切片以及調整環形圖大小，並提供逐步 Java 範例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: zh-hant
lastmod: 2026-10-04
og_description: 如何在 Word 圖表中將切片爆炸顯示，並使用 Java 自訂餅圖或環形圖。請參考完整範例以修改 Word 中的圖表。
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: 如何在 Word 圖表中將切片突出顯示 – 完整 Java 教程
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: 如何在 Word 圖表中將切片拉開並自訂外觀
url: /zh-hant/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 圖表中炸開切片並自訂外觀

如果您需要 **how to explode slice** 在 Word 圖表中，本指南會精確說明做法。無論您是在準備銷售簡報或財務報告，炸開餅圖切片或調整甜甜圈孔都能讓最重要的資料脫穎而出。在以下章節中，您還會學習如何 **modify chart in Word**、**explode pie chart slice**、**change doughnut chart size**，以及使用 Aspose.Words for Java **customize pie chart word** 文件。

您將完成本教學，得到一個完整、可直接執行的 Java 程式，該程式會載入 `.docx` 檔案、炸開第一個餅圖的切片、變更甜甜圈孔大小，並儲存結果。無需外部腳本或手動編輯。

## 前置條件

- 已在開發機器上安裝 Java 17 或更新版本。  
- Maven 3.6+（或 Gradle）用於管理相依性。  
- Aspose.Words for Java 函式庫（免費試用版可用於開發）。  
- 含有至少一個圖表（餅圖或甜甜圈）的 Word 文件（`input.docx`）。

## 步驟 1：將 Aspose.Words 加入專案

如果您使用 Maven，請在 `pom.xml` 中加入以下相依性：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

對於 Gradle，請將以下內容放入 `build.gradle`：

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **專業提示：** 請保持函式庫版本為最新；較新的發行版會加入對更多圖表類型的支援，並提升效能。

## 步驟 2：載入包含圖表的 Word 文件

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**為什麼重要：** 載入文件會在記憶體中建立可供 Aspose.Words 走訪的表示。沒有此物件就無法存取圖表節點。

## 步驟 3：取得文件中的第一個圖表

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **說明：** `NodeType.SHAPE` 包含所有繪圖物件，包括圖表。`true` 參數告訴 Aspose 以遞迴方式搜尋，確保即使圖表被嵌入表格中也能找到第一個圖表。

## 步驟 4：炸開餅圖的第一個切片

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**運作原理：** `setExplosion` 方法接受一個數值，用來決定切片離中心的距離。`20` 的數值在視覺上足夠明顯，同時不會破壞圖表版面配置。

## 步驟 5：調整甜甜圈圖的孔大小

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**為什麼有幫助：** 當資料點很多時，較大的甜甜圈孔能提升可讀性。`setDoughnutHoleSize` 方法接受百分比（0‑100）。

## 步驟 6：儲存已修改的文件

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### 預期輸出

- 第一個餅圖的第一個切片會向外偏移，突顯出來。  
- 若圖表為甜甜圈，中心孔會擴大至圖表半徑的 40 %。  
- 產生的檔案 `PieChart.docx` 可在 Microsoft Word、LibreOffice 或任何相容檢視器中開啟，顯示程式化套用的視覺變更。

## 完整、可執行的範例

以下是一個完整的程式碼區塊。將其複製到 `ChartExploder.java`，調整檔案路徑，然後使用 `mvn compile exec:java`（或 IDE 的執行設定）執行。

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

執行此程式碼會自動 **modify chart in Word**、**explode pie chart slice**，以及 **change doughnut chart size**。

## 常見問題與邊緣情況

| Question | Answer |
|----------|--------|
| *What if the document contains multiple charts?* | The sample targets the **first** chart (`NodeType.SHAPE, 0`). To work with other charts, change the index or iterate through `doc.getChildNodes(NodeType.SHAPE, true)` and filter by `shape.getChart() != null`. |
| *Can I explode a slice other than the first one?* | Yes. Access the desired series via `chart.getSeries().get(seriesIndex)` and call `setExplosion(value)`. Indexes are zero‑based. |
| *Does this work with Word 2007‑2021 files?* | Aspose.Words supports `.doc`, `.docx`, `.dot`, and `.dotx`. The same code works across versions because the library abstracts the file format. |
| *What if the chart is a bar or line chart?* | `setExplosion` and `setDoughnutHoleSize` are only applicable to pie‑type charts. The code safely skips those operations when the chart type differs. |
| *Do I need a license for Aspose.Words?* | A free evaluation license removes the 30‑day limit but adds a watermark. For production, purchase a license to remove the watermark and unlock full functionality. |

## 結論

現在您已了解如何 **how to explode slice** 在 Word 圖表中，如何 **modify chart in Word**，以及如何使用 Aspose.Words for Java **change doughnut chart size**。完整範例示範了從載入文件、定位圖表、套用視覺調整到儲存結果的完整工作流程，讓您能將這些步驟整合到任何報表或文件產生管線中。

**後續步驟**

- 探索其他圖表客製化方式，例如變更顏色、加入資料標籤，或切換圖表類型（`chart.setChartType(ChartType.BAR_CLUSTERED)`）。  
- 結合此邏輯與 Aspose.PDF，產生相同報表的 PDF 版本。  
- 透過在目錄中迴圈處理檔案，將此流程自動化以批次處理多份文件。

歡迎嘗試不同的炸開值或甜甜圈孔百分比，以符合您的設計指引。祝開發愉快！

## 接下來該學什麼？

以下教學與本指南的技術緊密相關，能進一步深化您的技巧。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在自己的專案中探索替代實作方式。

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Insert Bubble Chart In Word Document](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}