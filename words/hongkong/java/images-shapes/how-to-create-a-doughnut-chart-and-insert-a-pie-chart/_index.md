---
category: general
date: 2026-10-26
description: 在 Java 中使用逐步程式碼建立甜甜圈圖表並插入圓餅圖。學習完整的工作流程，以實現彈性圖表視覺化。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: zh-hant
lastmod: 2026-10-26
og_description: 使用本指南在 Java 中建立環形圖，並示範如何插入餅圖以實現彈性視覺化。
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: 建立環形圖並插入圓餅圖 – Java 教學
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: 如何建立環形圖並插入圓餅圖
url: /zh-hant/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何建立環形圖並插入圓餅圖

如果您需要在 Java 中 **建立環形圖**，本教學將逐步說明確切的操作步驟。我們亦會示範如何使用相同的 builder API **插入圓餅圖**，讓您能輕鬆在兩種視覺樣式之間切換。完成本指南後，您將擁有一個完整、可執行的程式，能產生兩種圖表並展示常見的自訂設定。

本教學涵蓋：

* 初始化所選函式庫提供的圖表建構器。  
* 建立環形圖並設定孔徑大小。  
* 插入圓餅圖並將切片爆炸以突顯重點。  
* 處理缺少系列或不支援的圖表類型等邊緣情況的技巧。

您只需要一個近期的 JDK（8 或以上）以及圖表函式庫的 JAR 放在 classpath 中。無需任何外部服務。

---

## 前置條件

| 項目 | 原因 |
|------|------|
| Java Development Kit (JDK) 8+ | 需要用於編譯和執行範例。 |
| 圖表函式庫（例如 **Aspose.Cells for Java** 或 **JFreeChart**） | 提供程式碼中使用的 `ChartBuilder`、`ChartType` 以及系列操作方法。 |
| IDE 或文字編輯器 | 用於撰寫與執行 Java 原始檔。 |

請確保將函式庫 JAR 加入專案的建置路徑。若使用 Maven，請加入相應的相依性；否則，將 JAR 放入 `libs` 資料夾，並在編譯時參考它。

---

## 步驟 1：設定圖表建構器

第一步是建立一個 `ChartBuilder`（或等效）實例，用來產生圖表物件。此物件充當工廠，並持有圖表將要放置的工作表或畫布。

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**為何這很重要：**  
建構器將圖表綁定到特定工作表，確保所有後續的圖表物件共用同一繪圖表面。若省略此步，將無法為視覺元素指定目標位置。

---

## 步驟 2：**建立環形圖**

現在我們產生一個具有指定大小的環形圖。孔徑大小決定圖表中心有多少空白，將普通的圓餅圖變成環形圖。

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**說明：**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` 會建立圖表物件並在工作表上保留空間。  
* `setHoleSize(30)` 將圓餅圖轉換為中心空白 30 % 的環形圖。  
* `add("{10, 20, 30, 40}", true)` 提供四個資料點；`true` 旗標告訴函式庫將這些值視為單一系列。

**邊緣情況：** 若所選圖表類型不支援孔徑（例如長條圖），呼叫 `getDoughnutChart()` 會拋出例外。調整孔徑大小前務必先確認圖表類型。

---

## 步驟 3：**插入圓餅圖**

環形圖完成後，我們示範如何使用相同的建構器 **插入圓餅圖**。此步驟凸顯兩種圖表的相似性，並說明如何突顯特定切片。

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**說明：**  

* `ChartType.PIE` 告訴建構器建立傳統的圓餅圖。  
* `setExplode(10)` 將第一片切片偏移半徑的 10 %，這是常見的突顯關鍵資料點的技巧。  

**提示：** `setExplode` 方法僅適用於圓餅圖的第一系列。若有多個系列，必須針對正確的索引進行設定。

---

## 步驟 4：儲存活頁簿

最後，將活頁簿寫入檔案，以便在 Excel 或任何相容檢視器中檢視圖表。

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**為何現在儲存：** 持久化活頁簿會完成所有繪圖操作。若在儲存前就開啟檔案，會得到空白或不完整的文件。

**結果：** 開啟 *DoughnutAndPieChart.xlsx* 後，可看到左側為 30 % 孔徑的環形圖，右側為第一片切片已爆炸的圓餅圖。

---

## 步驟 5：常見變化與疑難排解

| 情況 | 調整方式 |
|-----------|------------|
| **不同的圖表尺寸** | 在 `insertChart` 中變更寬度與高度參數。 |
| **多個資料系列** | 多次呼叫 `add` 或傳入二維陣列字串。 |
| **動態孔徑大小** | 根據資料範圍計算孔徑大小，然後呼叫 `setHoleSize`。 |
| **多片段爆炸** | 使用迴圈對每個想要偏移的切片呼叫 `chart.getSeries().get(i).setExplode(percent)`。 |
| **函式庫不支援環形圖** | 改用圓餅圖並手動繪製白色圓形覆蓋，雖然精確度較低。 |

**專業提示：** 在處理大型活頁簿時，插入圖表後務必呼叫 `builder.flush()`（若可用），可釋放內部緩衝區，防止記憶體洩漏。

![Java 程式碼建立環形圖並插入圓餅圖](https://example.com/images/doughnut-pie-java.png "在 Java 中建立環形圖範例")

*此圖示說明最終活頁簿的版面配置，兩個圖表並排顯示。*

---

## 結論

您現在已了解如何在 Java 中使用流暢的 builder API **建立環形圖** 與 **插入圓餅圖**。完整範例涵蓋初始化、尺寸設定、孔徑調整、切片爆炸與檔案輸出。接下來，您可以探索顏色、圖例、資料標籤等額外自訂，以符合報表需求。

**下一步**

* 嘗試 **chart customization Java** 功能，如漸層填色與資料標籤。  
* 將圖表產生整合至即時回傳活頁簿的 Web 服務。  
* 比較 builder 方式與其他函式庫（例如 JFreeChart），選擇最適合您專案的方案。

祝您圖表製作順利！

## 接下來該學什麼？

以下教學與本指南所示技術緊密相關，能在此基礎上進一步深化。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在自己的專案中探索替代實作方式。

- [如何在 Word 文件中使用 Java 建立環形圖](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [在 Java 中編輯環形圖後儲存 Word 文件](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [在 Java 中插入圓餅圖 – 爆炸、旋轉與突顯切片](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}