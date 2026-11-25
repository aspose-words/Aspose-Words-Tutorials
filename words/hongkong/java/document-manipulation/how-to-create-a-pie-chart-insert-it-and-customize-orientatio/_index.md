---
category: general
date: 2026-11-25
description: 學習如何在 Java 中建立圓餅圖、將圓餅圖插入 Word 文件、將圓餅切片突出顯示，以及變更圖表方向，並提供清晰的程式碼範例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: zh-hant
lastmod: 2026-11-25
og_description: 在 Java 中建立圓餅圖，將圓餅圖插入文件，分離圓餅切片並以逐步程式碼更改圖表方向。
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: 在 Java 中建立圓餅圖 – 插入、分離切片與旋轉
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: 如何在 Java 中建立圓餅圖、插入並自訂方向
url: /zh-hant/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中建立餅圖、插入它，並自訂方向

如果您需要在 Word 文件中 **create a pie chart**，本指南會精確說明如何操作。您將看到如何 **insert pie chart**、將切片炸開以強調，並使用簡單的旋轉 **change chart orientation**。

本教學涵蓋您所需的全部內容——從設定 Aspose.Words for Java 函式庫，到產生顯示已旋轉、已炸開餅圖的最終 `.docx` 檔案。無需外部文件說明，只要依照步驟執行程式碼即可。

## 前置條件

* 已安裝 Java 17 或更新版本。
* 使用 Maven 或 Gradle 來管理相依性。
* 有效的 Aspose.Words for Java 授權（或使用免費評估模式）。

將 Aspose.Words 相依性加入您的 `pom.xml`（Maven）或 `build.gradle`（Gradle）。以下為 Maven 範例：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **專業提示：** 請保持函式庫版本為最新；截至撰寫時的最新版本 (24.10) 已包含圖表渲染的錯誤修正。

## 步驟 1：建立餅圖並插入文件中

第一步是 **create pie chart** 物件並將其嵌入 Word 檔案。以下程式碼會建立簡易文件、加入圖表佔位元，並插入尺寸為 400 × 300 像素的餅圖。

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**為什麼這很重要：** `builder.insertChart` 會建立圖表佔位元，文件儲存時 Aspose.Words 會自動轉換為 OOXML 圖表。`ChartType.PIE` 參數指示函式庫渲染餅圖，滿足 **insert pie chart** 的需求。

## 步驟 2：炸開餅圖切片以突顯區段

炸開切片可將注意力聚焦於特定資料點。以下程式碼將第一個切片（索引 0）炸開 10 點：

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

您可以變更索引以針對其他切片，或調整炸開距離以獲得較細緻的效果。炸開切片是 Aspose.Words 中 **explode pie slice** 的標準做法。

## 步驟 3：透過旋轉變更圖表方向

旋轉圖表可提供全新的視覺觀感。使用 `setRotationAngle` 以順時針方向旋轉整個圖表（角度以度為單位）。

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

上述呼叫同時滿足 **rotate pie chart** 與 **change chart orientation** 的需求。接受 0 到 360 度之間的任意角度。

## 完整可執行範例

將所有步驟整合起來，以下是一個完整、獨立的程式，可建立餅圖、炸開切片並旋轉圖表。可於 IDE 中執行，或於命令列使用 `java -cp <classpath> PieChartDemo` 執行。

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### 預期輸出

* 工作目錄中會產生名為 **CreatePieChartDemo.docx** 的檔案。
* 使用 Microsoft Word 開啟該檔案時，會顯示 400 × 300 像素的餅圖。
* 第一個切片 (Q1) 向外偏移 10 點，產生 **explode pie slice** 效果。
* 整個圖表傾斜 45 度，示範 **change chart orientation** 與 **rotate pie chart**。

## 常見變化與邊緣情況

| 情況 | 如何調整程式碼 |
|-----------|-----------------------|
| **不同的圖表尺寸** | 在 `insertChart` 中將 `400, 300` 參數改為其他值。 |
| **多個資料系列** | 向 `chart.getSeries()` 新增更多 `ChartSeries` 物件。 |
| **炸開不同的切片** | 使用 `setExplode(sliceIndex, distance)`，將 `sliceIndex` 設為欲炸開的索引。 |
| **不需要旋轉** | 移除 `setRotationAngle` 呼叫，或將角度設為 `0`。 |
| **匯出為 PDF 而非 DOCX** | 建立文件後，呼叫 `doc.save("output.pdf")` 並指定 PDF 格式。 |

> **注意：** 使用負值的炸開距離會拋出 `IllegalArgumentException`。請始終提供非負值。

## 效能提示

如果在迴圈中產生大量圖表，請重複使用同一個 `DocumentBuilder`，僅在每次迭代時呼叫 `insertChart`。這樣可減少記憶體開銷並加快處理速度。

## 結論

現在您已了解如何使用 Aspose.Words for Java **create pie chart**、**insert pie chart**、**explode pie slice** 與 **rotate pie chart**。完整範例示範了完整工作流程——從初始化文件到儲存顯示已旋轉、已炸開餅圖的檔案。

接下來，您可以進一步探索透過 3‑D 效果 **changing chart orientation**，或嘗試其他圖表類型，如 **Bar** 或 **Line**。相同的 API 模式適用，擴充本教學相當簡單。

歡迎自行修改資料、切片索引或旋轉角度，以符合您的報表需求，並與社群分享您的成果！

## 接下來您可以學習什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通其他 API 功能，並在專案中探索替代實作方式。

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}