---
category: general
date: 2026-08-07
description: 如何在 Java 中使用 Aspose.Words 將圓餅圖切片分離。學習為圓餅圖添加指示線、建立 Word 圖表以及自訂圓餅圖切片。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: zh-hant
lastmod: 2026-08-07
og_description: 如何在 Java 中使用 Aspose.Words 爆炸式切片餅圖。本指南將示範如何為餅圖添加引導線、建立 Word 圖表，以及自訂餅圖切片以呈現清晰的視覺效果。
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: 如何在 Java 中將餅圖切片分離 – Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: 在 Java 中如何將餅圖切片分離 – Aspose.Words 圖表教學
url: /zh-hant/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中將餅圖切片突出顯示 – Aspose.Words 圖表教學

如果您需要了解**如何在餅圖切片突出顯示**在使用 Java 的 Word 文件中，本教學將為您完整說明。我們還會示範**如何為餅圖添加引導線**、**java 建立 word 圖表**物件，以及**自訂餅圖切片**以獲得精緻的效果。完成本指南後，您將擁有一個完整、可執行的範例，可直接放入任何 Java 專案中。

![如何在 Java 中將餅圖切片突出顯示 – Aspose.Words 圖表](/images/pie-chart-exploded.png)

## 前置條件

* Java Development Kit (JDK) 8 或以上。  
* Maven 或 Gradle 用於相依性管理。  
* Aspose.Words for Java 授權（免費評估版可用於學習目的）。  
* 具備 Java 語法與物件導向概念的基本熟悉度。

> **專業提示：** 即使 Aspose.Words 提供免費試用，購買授權也能移除產生文件中的評估水印。

## 本教學涵蓋內容

* 從頭建立新的 Word 文件。  
* 使用 `DocumentBuilder` 插入**餅圖**。  
* **將餅圖切片突出顯示**以突顯資料點。  
* **為餅圖添加引導線**以獲得更清晰的標籤。  
* 自訂切片外觀，例如顏色與邊框。  
* 將文件儲存至磁碟並驗證結果。

---

## 使用 Aspose.Words 在 Java 中將餅圖切片突出顯示

第一步是設定圖表物件並將目標切片突出顯示。Aspose.Words 透過 `Shape` 類別公開圖表，而每個切片都是一個 `ChartPoint`。透過設定 `Explosion` 屬性，即可控制切片向外移動的距離。

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**為什麼這樣有效：**  
`setExplosion(20)` 告訴圖表引擎將切片從圖表中心偏移 20 點。此數值為相對值；數字越大效果越明顯。您可以透過變更索引 (`get(1)`, `get(2)`, …) 來突出顯示任意切片。

## 為餅圖添加引導線以獲得更清晰的標籤

引導線將切片的標籤連接至其邊緣，當切片被突出顯示或圖表包含許多小區段時特別有用。`setLeaderLines(true)` 呼叫會為整個系列啟用此功能。

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**為什麼需要引導線：**  
當切片被突出顯示時，預設標籤可能會與其他元素重疊。引導線透過從切片繪製短線至文字方塊，使標籤保持可讀性。

## Java 建立 Word 圖表 – 插入資料系列

沒有資料的圖表幾乎沒有用處。必須以類別與數值填充系列。以下我們加入三個代表市場佔有率的類別。

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**說明：**  
`ChartSeries` 同時保存類別（切片名稱）與數值。啟用 `ShowCategoryName` 與 `ShowPercentage` 可讓圖表自我說明，且與先前加入的引導線相得益彰。

## 自訂餅圖切片（除突出顯示外）

除了突出顯示切片外，您通常還想調整顏色、邊框，甚至完全隱藏某個切片。以下程式碼示範三種常見的自訂方式：

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**為什麼要自訂切片：**  
自訂顏色可讓圖表符合企業品牌形象，邊框則提升列印頁面的可讀性。隱藏切片在您希望保留資料模型完整性但暫時在視覺輸出中省略某類別時相當有用。

## 儲存文件並驗證結果

最後，將文件寫入磁碟。您可以在 Microsoft Word、LibreOffice 或任何支援此格式的檢視器中開啟產生的 `.docx`。

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**預期輸出：**  
當您開啟 `PieChartDemo.docx` 時，會看到一個餅圖，第一個切片（Product A）向外突出顯示，引導線從每個切片指向其標籤，且切片以自訂的綠、藍、橙色呈現。被隱藏的切片（Product C）不會顯示，但百分比仍會加總至 100 %，因為資料仍保留在圖表的系列中。

---

## 完整、可執行範例

以下是完整的程式碼，您可在專案加入 Aspose.Words 相依性後，直接複製、貼上並執行。

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**相依性（Maven）**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

## 接下來您應該學習什麼？

以下教學涵蓋與本指南緊密相關的主題，並在此基礎上進一步擴展。每個資源皆提供完整可運作的程式碼範例與逐步說明，協助您精通其他 API 功能，並在自己的專案中探索替代實作方式。

- [如何使用 Aspose.Words for Java 建立柱狀圖](/words/english/java/document-conversion-and-export/using-charts/)
- [如何使用 Aspose.Words Java 載入 Word 文件：完整指南](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [如何使用 Aspose.Words for Java 的 DocumentBuilder 建立表單欄位並加入內容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}