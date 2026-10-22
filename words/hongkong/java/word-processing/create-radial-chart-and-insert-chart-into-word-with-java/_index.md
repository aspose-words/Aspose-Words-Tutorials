---
category: general
date: 2026-09-27
description: 在 Java 中建立徑向圖並將圖表插入 Word。了解如何設定圖表大小、加入資料系列，以及產生空白的 Word 文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: zh-hant
lastmod: 2026-09-27
og_description: 在 Java 中建立徑向圖，然後將圖表插入 Word。本指南說明如何設定圖表大小、加入資料系列，以及建立空白的 Word 文件。
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: 使用 Java 建立徑向圖表並插入至 Word
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: 使用 Java 建立徑向圖表並將圖表插入 Word
url: /zh-hant/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Java 建立徑向圖表並插入至 Word

如果您需要在 Word 檔案中使用 Java **建立徑向圖表**，本教學將完整示範操作步驟。您將會看到如何 **將圖表插入 Word**、設定圖表尺寸，以及從頭建立 **空白 Word 文件**。

我們將逐步說明所有必須的步驟，從初始化文件、加入資料序列到儲存最終的 `.docx`。完成後，您將擁有一個包含徑向圖表的完整 Word 檔案，並了解 **如何設定圖表大小** 以及 **如何加入資料序列圖表**，以便未來自訂。

## 前置條件

* Java 17 或更新版本（程式碼可在任何現代 JDK 上編譯）
* Aspose.Words for Java 24.9 或更新版本 – `setShowGraduations` 方法僅在此版本之後提供
* 可加入 Aspose.Words JAR 的 IDE 或建置工具（Maven/Gradle）
* 具備基本的 Java 語法與 Maven/Gradle 依賴管理知識

> **小技巧：** 若您使用 Maven，請在 `pom.xml` 中加入以下內容：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## 步驟 1：建立空白 Word 文件

空白文件是放置圖表的畫布。`Document` 類別代表整個 `.docx` 檔案。

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

建立空白文件可確保不會有既有內容干擾圖表版面配置。

## 步驟 2：初始化 DocumentBuilder

`DocumentBuilder` 提供方便的方式將物件、文字及其他元素插入文件中。

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

稍後會使用此 builder 來 **將圖表插入 Word**。

## 步驟 3：建立徑向圖表

Aspose.Words 支援多種圖表類型；`ChartType.RADIAL` 會建立徑向（極座標）圖表。

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

此時圖表已建立，但尚未設定資料、尺寸或視覺選項。

## 步驟 4：為圖表加入資料序列

沒有資料序列的圖表會是空的。`add` 方法接受序列名稱與數值陣列。

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

您可以多次呼叫 `add` 以加入多個序列。這滿足 **加入資料序列圖表** 的需求。

## 步驟 5：啟用刻度（可選）

刻度是提升可讀性的徑向格線。此功能僅在 24.9 版之後提供。

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

若使用較舊的 Aspose.Words 版本，這行程式會拋出例外——請先確認您的函式庫版本。

## 步驟 6：設定圖表尺寸

控制圖表尺寸可讓其在頁面邊界內恰當顯示。這說明了 **如何設定圖表大小**。

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

您可以依版面需求調整寬度與高度數值。請記得 1 point 約等於 1/72 英吋。

## 步驟 7：將圖表插入 Word 文件

現在圖表已準備好可放置。`DocumentBuilder` 的 `insertChart` 方法負責插入動作。

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

這就是 **將圖表插入 Word** 操作的核心。

## 步驟 8：儲存文件

最後，將文件寫入磁碟。檔案將包含您剛建立的徑向圖表。

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

執行程式後會在專案的工作目錄產生 `RadialChart.docx`。在 Microsoft Word 中開啟該檔案，即可看到包含三個資料點且顯示刻度的徑向圖表。

### 預期輸出

* 名為 `RadialChart.docx` 的 Word 檔案
* 檔案內僅有一頁，包含尺寸為 400 × 300 points 的徑向圖表
* 圖表顯示一個標題為 **Series 1** 的序列，數值為 **10, 20, 30**
* 刻度（徑向格線）在圖表周圍可見

## 常見變化與邊緣案例

| 情境 | 需要變更的地方 | 原因 |
|-----------|----------------|--------|
| **多個序列** | 對每個序列呼叫 `chart.getSeries().add(...)` | 允許比較性資料視覺化 |
| **不同圖表類型** | 將 `ChartType.RADIAL` 替換為 `ChartType.COLUMN`（或其他任意類型） | 使用最能表現資料的圖表類型 |
| **自訂顏色** | 存取 `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` | 提升視覺品牌形象 |
| **較舊的 Aspose.Words 版本** | 省略 `setShowGraduations` 行或升級函式庫 | 避免發生 `NoSuchMethodError` |
| **儲存為不同格式** | 使用 `doc.save("RadialChart.pdf", SaveFormat.PDF)` | 產生 PDF 而非 DOCX |

## 完整可執行範例

以下為完整、獨立的 Java 程式。請將其複製到名為 `RadialChartExample.java` 的檔案中，加入 Aspose.Words 依賴後執行。

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## 結論

您現在已掌握如何以程式方式 **建立徑向圖表**、**加入資料序列圖表**、控制 **如何設定圖表大小**，以及 **將圖表插入 Word**，且全程從 **空白 Word 文件** 開始。此範例使用 Aspose.Words for Java 24.9，但相同概念亦適用於其他提供類似 API 的圖表函式庫。

### 後續步驟

* 探索其他圖表類型（`ChartType.PIE`、`ChartType.LINE` 等）— 這與次要關鍵字 **insert chart into word** 相關。
* 自訂座標軸標籤、圖例與顏色，以符合品牌指引。
* 從資料庫查詢或 CSV 檔案動態產生圖表。
* 將產生的 `.docx` 轉換為 PDF 以供發佈（`doc.save("output.pdf", SaveFormat.PDF)`）。

## 接下來該學什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎延伸。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在專案中探索其他實作方式。

- [如何使用 Aspose.Words for Java 建立直條圖](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – 新增帶陰影效果的矩形形狀](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [在 Word 文件中插入區域圖表](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}