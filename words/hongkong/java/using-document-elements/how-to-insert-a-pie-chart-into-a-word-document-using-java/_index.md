---
category: general
date: 2026-09-27
description: 學習如何使用 Java 在 Word 文件中插入圓餅圖、在 Word 中建立圓餅圖，並在圓餅圖上顯示百分比，以獲得清晰的數據洞察。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: zh-hant
lastmod: 2026-09-27
og_description: 如何使用 Java 在 Word 文件中插入餅圖。本指南將教您如何在 Word 中建立餅圖、在餅圖上顯示百分比以及添加引線。
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: 如何使用 Java 在 Word 文件中插入餅圖
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: 如何使用 Java 在 Word 文件中插入圓餅圖
url: /zh-hant/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中使用 Java 插入圓餅圖

如果您需要 **how to insert pie chart** 到 Word 檔案，本指南將帶您完整步驟。您將看到如何 **create pie chart in Word**、在每個切片上顯示百分比，並加入指引線以獲得精緻外觀。

Word 自動化常給人沉重的感覺，但使用 Aspose.Words for Java，您可以以程式方式產生完整格式化的文件。完成本教學後，您將擁有一段可執行的 Java 程式碼，產生包含樣式化圓餅圖的 Word 文件。

## 前置條件

- 安裝 Java 17 或更新版本
- 使用 Maven 或 Gradle 來管理相依性
- 在專案中加入 Aspose.Words for Java（版本 23.11 或更新） 
- 具備基本的 Java 語法知識

您不需要任何先前的圖表 API 經驗；以下步驟涵蓋從專案設定到最終輸出的一切。

## 步驟 1：設定 Maven 相依性

將 Aspose.Words 程式庫加入您的 `pom.xml`。此單一相依性即可讓您使用 `Document`、`DocumentBuilder` 以及圖表相關類別。

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

如果您使用 Gradle，等效的設定如下：

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **專業提示：** 使用最新的穩定版以獲得錯誤修正與新圖表功能的好處。

## 步驟 2：建立新文件與建構器

`Document` 物件代表 Word 檔案，而 `DocumentBuilder` 讓您插入內容。這是 **add chart to word document** 的基礎。

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

建構器現在已可在文件中的任何位置放置物件。

## 步驟 3：插入圓餅圖

Aspose.Words 支援多種圖表類型；我們選擇 `ChartType.PIE`。尺寸以點數表示（1 點 = 1/72 英吋）。

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

此時圖表包含預設的資料系列與佔位值。若有需要，您可以稍後替換這些值。

## 步驟 4：存取圖表系列

圓餅圖只有一個系列，用於保存各切片的數值。取得該系列以套用格式設定。

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## 步驟 5：將第一個切片突出顯示

將切片突出顯示可吸引注意力至特定資料點。這是想突顯關鍵指標時常用的視覺提示。

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## 步驟 6：在每個切片上顯示百分比

直接在圖表上顯示百分比可提升資料洞察。這滿足 **show percentages on pie chart** 的需求。

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## 步驟 7：加入指引線以獲得更清晰的標籤

指引線將切片標籤連接至相對應的區段，消除歧義。這符合 **how to add leader lines** 的需求。

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## 步驟 8：儲存文件

最後，將文件寫入磁碟。您可以選擇任何您有寫入權限的資料夾。

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

執行程式會產生 `output/PieFormatted.docx`。在 Microsoft Word 中開啟此檔案，您會看到一個圓餅圖，其特點如下：

- 第一個切片已突出顯示。
- 每個切片顯示其百分比數值。
- 指引線從百分比指向相對應的切片。

### 預期輸出

![已在 Word 中插入的格式化圓餅圖](/images/pie-formatted.png){: .center-image alt="已在 Word 中插入的格式化圓餅圖"}

此螢幕截圖（alt 文字使用主要關鍵字）展示最終外觀：一個乾淨、以資料為驅動的圓餅圖，適用於報告、提案或儀表板。

## 常見變化與邊緣案例

### 更改切片數值

如果您需要自訂資料，請替換預設系列的數值：

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### 多系列（甜甜圈圖）

雖然簡單的圓餅圖只有一個系列，Aspose.Words 亦支援具有多個系列的甜甜圈圖。將 `ChartType.PIE` 改為 `ChartType.DONUT`，並重複系列設定步驟。

### 匯出為 PDF

如果您的後續工作流程需要 PDF，請在圖表建立完成後呼叫 `doc.save("output/PieFormatted.pdf");`。視覺版面保持相同。

## 完整來源程式碼

以下是完整、獨立的 Java 檔案，您可以直接複製貼上至 IDE 中。

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

使用 `mvn compile exec:java -Dexec.mainClass=PieChartExample`（或等效的 Gradle 指令）編譯並執行程式。產生的 Word 檔案將包含完整格式化的圓餅圖。

## 結論

您現在已了解如何使用 Java **how to insert pie chart** 到 Word 文件、如何 **create pie chart in Word**、如何 **show percentages on pie chart**，以及如何在帶有指引線的情況下 **add chart to word document**。完整範例示範每個步驟，說明程式碼的撰寫原因，並提供自訂化的技巧。

接下來，您可以探索：

- 使用自訂字型加入資料標籤（**show percentages on pie chart** 變體）
- 在單一文件中結合多個圖表（**add chart to word document** 使用情境）
- 自動化產生包含表格與圖表的報告

歡迎隨意嘗試不同顏色、切片順序或匯出為 PDF。祝開發愉快！

## 接下來您應該學習什麼？

以下教學涵蓋與本指南密切相關的主題，建立在所示技巧之上。每個資源皆包含完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在專案中探索替代實作方式。

- [如何使用 Aspose.Words for Java 建立直條圖](/words/english/java/document-conversion-and-export/using-charts/)
- [在 Word 文件中隱藏圖表座標軸](/words/english/net/programming-with-charts/hide-chart-axis/)
- [使用 Aspose.Words for .NET 在 Word 中建立折線圖](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}