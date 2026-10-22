---
category: general
date: 2026-09-18
description: 學習使用 Aspose.Words for Java 建立 Word 文件並插入圓餅圖。包括旋轉圓餅圖及產生 Word 檔案的步驟。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: zh-hant
lastmod: 2026-09-18
og_description: 使用 Java 建立 Word 文件並插入圓餅圖。按照本指南可旋轉圓餅圖、分離切片，並產生 Word 檔案。
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: 建立含圓餅圖的 Word 文件 – 逐步 Java 指南
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: 如何在 Java 中建立含圓餅圖的 Word 文件
url: /zh-hant/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中建立包含圓形圖表的 Word 文件

如果您需要 **建立 Word 文件** 以視覺化資料，本指南將示範如何使用 Aspose.Words for Java 完成。您將學會插入圓形圖表、突出切片、旋轉圖表，最後 **產生 Word 檔案**，可於 Microsoft Word 開啟。

建立結合文字與圖表的報告不需要額外的圖形工具。完成本教學後，您將擁有一個完整、可執行的程式，能產生包含完整設定圓形圖表的 .docx 檔案。

## 前置條件

- Java 17 或更新版本（程式碼亦可在 Java 8+ 編譯）
- 用於相依管理的 Maven 或 Gradle
- Aspose.Words for Java 授權（免費試用可用於本範例）
- 基本的 Java 語法熟悉度

## 步驟 1：設定 Maven 專案

建立一個新的 Maven 專案，並將 Aspose.Words 相依加入 `pom.xml`：

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **小技巧：** 請保持版本號為最新；較新版本會加入圖表類型的改進與錯誤修正。

## 步驟 2：建立新的 Word 文件

以程式方式 **建立 Word 文件** 時的第一個動作是實例化 `Document` 物件。此物件在記憶體中代表整個 .docx 檔案。

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

`Document` 類別是所有 Word 處理功能的入口點。目前尚未寫入檔案至磁碟；所有操作皆在記憶體中進行，直至呼叫 `save` 為止。

## 步驟 3：插入圓形圖表

`DocumentBuilder` 讓您能向文件加入內容。使用 `insertChart` 可直接 **插入圓形圖表** 物件。

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` 告訴 Aspose.Words 建立圓形圖表。尺寸以點 (point) 為單位表示 (1 pt ≈ 1/72 in)。此呼叫之後，圖表會出現在新段落上。

## 步驟 4：為圖表填入資料

圓形圖表需要一系列數值。此處我們加入三個類別：「Apples」(蘋果)、「Bananas」(香蕉) 與 「Cherries」(櫻桃)。

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

`add` 方法會建立系列並自動產生圖例項目。您可以將此模式重複使用於任何數值資料集。

## 步驟 5：強調第一個切片

將切片「爆炸」可突顯特定數值。第一個切片（索引 0）以 20 點的距離向外爆炸。

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

在系列上設定 `explode` 會影響整個圖表，因此僅第一個資料點會被偏移。

## 步驟 6：旋轉圓形圖表

旋轉圖表可提升視覺平衡，尤其當最大切片不在最上方時。`setRotationAngle` 方法接受角度（度）作為參數。

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

45° 的旋轉會將起始角度順時針移動，使圖表在多種版面配置下更易閱讀。

## 步驟 7：儲存文件並產生 Word 檔案

最後，將文件寫入磁碟。此步驟 **產生 Word 檔案**，可於 Microsoft Word、LibreOffice 或任何相容的檢視器開啟。

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

`save` 方法會自動偵測 .docx 副檔名並寫入 Word 相容的封裝。必須先確保 `output` 資料夾已存在，或可於程式中自行建立。

### 預期輸出

執行程式後，開啟 `output/PieChart.docx`。您應該會看到：

- 單一頁面，內含 400 × 300 pt 的圓形圖表。
- 「Apples」切片向外爆炸 20 pt。
- 整個圖表順時針旋轉 45°。
- 圖例與三種水果類別相符。

## 常見變形與邊緣情況

### 插入多個圖表

如果需要多於一個圖表，於移動游標後再次呼叫 `builder.insertChart`：

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### 變更圖表顏色

您可透過系列的 `getPoints()` 集合自訂切片顏色：

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### 處理大型資料集

對於超過 10 個切片的資料集，建議使用環形圖 (`ChartType.DOUGHNUT`) 以保持視覺清晰。

## 結論

現在您已了解如何使用 Aspose.Words for Java **建立 Word 文件**、**插入圓形圖表**、**旋轉圓形圖表**，以及 **產生 Word 檔案**。完整的解決方案示範了從文件初始化到最終檔案輸出的完整工作流程，涵蓋每一步的「如何」與「為何」。

接下來，您可以探索相關主題，例如 **如何從資料庫建立圓形圖表資料**、加入資料標籤，或將圖表匯出為影像。嘗試不同的圖表類型（長條圖、折線圖、環形圖），以擴充您的 Word 自動化工具箱。

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，建立於本教學所示技巧之上。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}