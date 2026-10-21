---
category: general
date: 2026-10-07
description: 學習如何在 Word 中建立圓餅圖、加入資料系列，並使用 Java 將圖表儲存為 PNG。遵循一步一步的指引，即可快速得到結果。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: zh-hant
lastmod: 2026-10-07
og_description: 快速在 Word 中建立圓餅圖：本教學示範如何新增資料系列、產生圖表，並將 Word 圖表另存為圖片（PNG）。請參考完整程式碼範例。
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: 在 Word 中建立圓餅圖並匯出為 PNG – 指南
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: 如何在 Word 中建立圓餅圖並另存為 PNG
url: /zh-hant/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中建立圓餅圖並儲存為 PNG

如果您需要在 Microsoft Word 檔案中 **建立圓餅圖** 物件，本指南將會一步一步示範如何使用 Java 完成。您還會學習如何 **新增資料系列** 到圖表，以及 **將圖表儲存為 PNG**，讓圖像能在 Word 之外重複使用。

直接在文件中產生圖表可免除將資料匯出至其他圖形工具的步驟。完成本教學後，您將擁有一個完整的 Word 檔案，內含圓餅圖以及相對應的 PNG 圖片。

## 前置條件

* 已安裝 Java 17 或更新版本。
* **GroupDocs.Viewer for Java**（或其他提供 `Document`、`Chart`、`ChartType` 與 `ImageSaveOptions` 類別的相容函式庫）。
* 可加入函式庫相依性的 Maven 或 Gradle 專案。
* 一個位於可從程式碼存取之資料夾內的輸入 Word 文件（`input.docx`）。

如果您使用 Maven，請加入以下相依性（將 `VERSION` 替換為最新版本）：

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## 如何在 Word 中建立圓餅圖

此解決方案的核心圍繞以下三個動作：

1. 載入來源 `.docx` 檔案。
2. **新增資料系列** 至類型為 `PIE` 的新 `Chart` 物件。
3. **將圖表儲存為 PNG**，以在 Word 文件旁產生影像檔案。

以下將逐步說明每個步驟，並提供相應的 Java 程式碼範例。

### 步驟 1：載入來源文件

您必須開啟將放置圖表的 Word 檔案。`Document` 類別會將 `.docx` 內容讀取至記憶體中。

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*為什麼這很重要*：載入文件會建立可變更的模型。所有後續的圖表操作皆會修改此記憶體中的表示，之後再寫回磁碟。

### 步驟 2：為圖表新增資料系列

建立 **圓餅圖** 從 `Chart` 實例開始。建構子會接收父層 `Document` 以及圖表類型（`ChartType.PIE`）。圖表物件建立後，您即可填入數值與可選的標籤。

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*為什麼這很重要*：`add` 方法 **新增資料系列** 到圖表。`values` 中的每個項目會成為圓餅的一個切片，而 `categories` 則提供圖例標籤。您可以提供任意數量的點，函式庫會自動計算切片角度。

### 步驟 3：將圖表儲存為 PNG

圖表加入文件後，即可匯出其視覺呈現。底層圖表物件的 `save` 方法會將 PNG 檔寫入檔案系統。

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*為什麼這很重要*：將圖表儲存為 PNG 可取得點陣圖，方便嵌入網頁、電子郵件或報告中，且不需原始 Word 檔。`ImageSaveOptions` 物件允許您控制格式、解析度及其他匯出設定。

## 在 Word 中產生圓餅圖 – 自訂外觀

除了基本步驟外，您可能想自訂顏色、標題或資料標籤。大多數函式庫都提供 `ChartOptions` 或類似物件。以下是一個快速範例，示範如何加入標題並變更切片顏色：

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

這些自訂項目為可選，但可說明如何 **在 Word 中產生圓餅圖**，以符合您的品牌形象。

## 將 Word 圖表儲存為影像 – 替代方法

如果您只需要影像而不需要將圖表插入文件，可省略將圖表形狀加入 Word 檔的步驟，直接在建立圖表後呼叫 `save` 方法。程式碼保持不變，只是省去將圖表加入文件主體的步驟。

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

此技巧在批次產生大量圖表且僅關注 PNG 輸出時特別有用。

## 完整可執行範例

將以下類別複製到您的專案，調整檔案路徑後執行。程式將會：

1. 載入 `input.docx`。
2. **建立圓餅圖**、**新增資料系列**，並將其嵌入文件中。
3. **將圖表儲存為 PNG**（`radial.png`）。
4. 將修改後的 Word 檔案儲存為 `output.docx`。

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.Chart;
import com.groupdocs.viewer.ChartType;
import com.groupdocs.viewer.options.ImageSaveOptions;
import com.groupdocs.viewer.options.SaveFormat;

public class PieChartGenerator {

    public static void main(String[] args) {
        // Adjust these paths for your environment
        String inputPath = "YOUR_DIRECTORY/input.docx";
        String outputPath = "YOUR_DIRECTORY/output.docx";


## 接下來您可以學習什麼？

以下教學涵蓋與本指南密切相關的主題，並以此為基礎延伸技術。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [如何使用 Aspose.Words for Java 建立柱狀圖](/words/english/java/document-conversion-and-export/using-charts/)
- [使用 Aspose.Words for .NET 建立 Word 散點圖](/words/english/net/working-with-charts/insert-scatter-chart/)
- [使用 Aspose.Words for .NET 在 Word 中插入柱狀圖](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}