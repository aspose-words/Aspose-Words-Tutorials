---
category: general
date: 2026-11-15
description: 學習如何使用 Aspose.Words for Java 在 Word 文件中加入圓餅圖。包括環形圖轉換、分離切片以及完整程式碼範例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: zh-hant
lastmod: 2026-11-15
og_description: 使用 Aspose.Words for Java 在 Word 文件中新增餅圖。本教學示範如何將切片炸開以及將圖表轉換為環形圖。
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: 使用 Java 為 Word 文件添加圓餅圖 – 逐步指南
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: 如何使用 Java 在 Word 文件中加入圓餅圖
url: /zh-hant/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 文件中加入圓餅圖 – 完整 Java 指南

如果您需要以程式方式 **在 Word 文件中加入圓餅圖**，本教學將向您展示如何使用 Aspose.Words for Java 完成。您將看到完整的工作流程：載入 DOCX、建立圓餅圖、將第一片分離（explode），以及透過設定孔徑大小將圖表轉換為環形圖（doughnut）。

本指南亦涵蓋常見的變化情況——例如加入多個資料列、客製化顏色，以及處理已包含圖表的文件——讓您能將程式碼套用於自動化報表或動態簡報等實務專案。

## 前置條件

在開始之前，請確保您已具備：

* Java 17 或更新版本（程式碼亦可在 JDK 11+ 上編譯）
* Maven 3.6+ 或 Gradle（用於相依性管理）
* Aspose.Words for Java 授權（免費試用版可用於測試）
* 具備基本的 Java 語法與 Maven 專案結構概念

## 步驟 1：設定 Maven 專案並匯入 Aspose.Words

建立一個新的 Maven 專案（或在現有專案中加入），並在 `pom.xml` 中加入 Aspose.Words 相依性：

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **小技巧：** 若您使用 Gradle，等效的寫法是 `implementation 'com.aspose:aspose-words:24.9'`。

此相依性會自動帶入您操作圖表所需的 `Document`、`Chart` 與 `ChartType` 類別。

## 步驟 2：載入目標文件

您可以從既有的 `.docx` 檔案開始，或是建立一個全新的空白文件。以下範例會載入位於 `src/main/resources` 資料夾下名為 `input.docx` 的範本：

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

如果檔案不存在，Aspose.Words 會在您呼叫 `new Document()`（未指定檔名）時自動建立一個空白文件。

## 步驟 3：建立圓餅圖並插入文件中

Aspose.Words 將圖表視為一種形狀，可放置於任何段落可出現的地方。下列程式碼會建立一個 **圓餅圖**、加入單一資料列，並將圖表插入於第一段落之後：

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**此步驟的重要性：**  
* `ChartType.PIE` 告訴 Aspose.Words 繪製傳統的圓餅圖。  
* 加入同時包含類別標籤與數值的資料列，可自動產生各切片。  
* 將圖表作為 `Paragraph` 的子項插入，可保持文件的排版流程不受影響。

## 步驟 4：分離第一片以突顯它

*分離的切片* 能將特定資料點凸顯出來。API 在 `ChartSeries` 物件上提供 `setExplode(boolean)` 方法。將其設定於第一個資料列（索引 0）即可讓第一片彈出。

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **常見問題：** *如果我有多個資料列怎麼辦？*  
> 您可以依索引指定特定資料列，例如 `pieChart.getSeries().get(1).setExplode(true)` 會對第二個資料列執行分離。

## 步驟 5：設定孔徑大小將圓餅圖轉換為環形圖

環形圖本質上是中心為空洞的圓餅圖。Aspose.Words 允許您以圖表半徑的百分比來定義孔徑大小。

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

`setHoleSize` 方法接受 **0**（普通圓餅）到 **100**（完全空心）的值。約 **30‑40** 的設定會產生視覺上平衡的環形圖。

## 步驟 6：儲存並驗證結果

完成所有修改後，將文件儲存。以下程式碼會把檔案寫入 `output` 資料夾：

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### 預期輸出

在 Microsoft Word 中開啟 `final-pie-doughnut.docx`：

* 環形圖會出現在第一段落的位置。  
* 「Apples」切片被分離（稍微與其他切片分開）。  
* 圖表顯示四個切片，分別標示為 *Apples*、*Bananas*、*Cherries*、*Dates*，並以您提供的百分比顯示。

如果您偏好 PDF 輸出，只需將 `SaveFormat` 改為 `SaveFormat.PDF`。

## 處理邊緣情況與變化

### 加入多個資料列

如果需要多個資料列（例如堆疊環形圖），可依序加入：

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### 自訂顏色

您可以透過 `ChartDataPoint.setFillFormat().setSolidFillColor()` 為每個切片指定顏色：

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### 處理已存在的圖表

若文件已包含圖表且您只想修改它，請先定位圖表形狀：

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### 授權處理

Aspose.Words 於正式環境必須使用授權。將您的 `Aspose.Words.lic` 檔案放在 classpath 中，並於應用程式啟動時載入：

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

未設定授權會在產生的文件上加上浮水印。

## 完整、可執行範例

以下為整合所有步驟的完整 Java 類別。將它複製到 `src/main/java/com/example/AddPieChart.java`，然後執行 `mvn compile exec:java`：

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

執行程式後會產生前述的環形圖。您可以依需求調整 `categories`、`values` 或 `holeSize`。

## 結論

您現在已掌握如何使用 Java 與 Aspose.Words **在 Word 文件中加入圓餅圖**。本教學涵蓋了載入文件、建立圓餅圖、分離切片、將圖表轉為環形圖，以及多資料列、客製化顏色與既有圖表等常見變化。憑藉這些基礎，您可以建構自動化報表工具、產生動態簡報，或直接在 Word 檔案中嵌入豐富的視覺化內容。

### 接下來可以探索的主題

* **add bar chart to Word document** – 步驟類似，但使用 `ChartType.BAR`。  
* **customize chart legends and titles** – 使用 `pieChart.getTitle().setText("...")` 以及 `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`。  
* **export the Word document as PDF** – 將 `SaveFormat` 改為 `PDF` 以產出可直接發佈的檔案。  
* **populate chart data from a database** – 將靜態陣列改為 JDBC 查詢結果。

盡情嘗試不同的圖表類型、資料來源與樣式設定吧。祝您寫程式愉快！

## 接下來應該學什麼？

以下教學與本指南所示技巧密切相關，能幫助您進一步掌握 API 的其他功能，並在專案中探索替代實作方式。每篇資源皆提供完整可執行的程式碼範例與逐步說明。

- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}