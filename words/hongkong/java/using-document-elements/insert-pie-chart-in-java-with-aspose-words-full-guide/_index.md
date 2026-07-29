---
category: general
date: 2026-07-29
description: 使用 Aspose.Words for Java 插入圓餅圖，並學習如何生成環形圖、格式化圓餅圖、格式化 Word 圖表，以及自訂圖表大小。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: zh-hant
lastmod: 2026-07-29
og_description: 使用 Aspose.Words for Java 插入圓餅圖，快速學習生成環形圖、格式化圓餅圖、格式化 Word 圖表，並自訂圖表大小，打造專業文件。
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: 在 Java 中插入餅圖 – 完整 Aspose.Words 教學
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: 在 Java 中使用 Aspose.Words 插入圓餅圖 – 完整指南
url: /zh-hant/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中使用 Aspose.Words 插入圓餅圖 – 完整指南

有沒有想過如何從 Java 程式碼 **insert pie chart** 到 Word 文件？你並非唯一遇到此問題的開發者——許多開發者在需要快速、程式化的方式來視覺化資料時都會卡關。好消息是？使用 Aspose.Words for Java，你只需幾行程式碼即可完成，同時還能 **generate doughnut chart**、**format pie chart**、**format chart Word**，以及 **customize chart size** 以符合你的品牌形象。

在本教學中，我們將示範一個真實案例：先建立空白文件、插入圓餅圖、微調幾個視覺屬性，最後儲存檔案。完成後，你將擁有一段可重複使用的程式碼片段，直接貼到任何需要圖表自動化的 Java 專案中。無需額外函式庫、無需手動操作 Office interop——只要乾淨、可編譯的 Java。

## What You’ll Need

- **Java 17**（或任何較新的 JDK；API 向下相容）
- **Aspose.Words for Java** 22.12 或更新版本——可從 Aspose 官網取得 Maven 套件或 .jar 檔。
- 任意輕量級 IDE（IntelliJ IDEA、Eclipse、VS Code…）——能執行 `main` 方法即可。
- 可選：若不想看到評估水印，請準備授權檔案。

如果已備妥上述環境，我們即可直接進入程式碼。

## Step 1: Insert pie chart with Aspose.Words

首先，我們 **insert pie chart** 到全新的文件中。這一步為後續所有操作奠定基礎，因為圖表物件讓我們可以存取系列、資料點以及視覺調整。

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Why this matters:** `DocumentBuilder.insertChart` 不僅會建立圖表，還會回傳一個 `Chart` 物件供我們操作。寬度與高度參數讓你在建立時就 **customize chart size**，不必在之後再調整大小。

## Step 2: Generate doughnut chart (optional)

如果設計需要中間有洞——也就是傳統的甜甜圈圖——Aspose 只要一行程式碼即可完成。同一個 `Chart` 實例只要調整孔徑即可從普通圓餅圖切換成甜甜圈圖。

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Tip:** 孔徑只對 `ChartType.DONUT` 生效。若仍使用 `PIE` 類型，該呼叫會被忽略，盡情試驗吧。

## Step 3: Format pie chart slices

好的視覺效果常會突顯特定切片。這裡我們 **format pie chart**，將第一片向外「炸」出 20 點，讓讀者的目光聚焦在最重要的資料點上。

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Pro tip:** 若有多個系列，可透過 `pieChart.getSeries()` 迴圈分別設定顏色、邊框或資料標籤。這就是在 **format chart Word** 文件時加入豐富樣式的方式。

## Step 4: Add data to the chart

沒有資料的圖表只是一個裝飾圖形。現在給它填入簡單的資料集——例如每季銷售額。

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Why we do this:** 透過明確加入 `ChartPoint` 物件，我們確保圖表正確反映業務邏輯。`setShowCategoryName` 與 `setShowValue` 兩個呼叫屬於 **formatting the pie chart**，可同時顯示類別名稱與數值。

## Step 5: Fine‑tune appearance (customize chart size & style)

除了最初的尺寸外，你可能還想調整圖例、標題，甚至資料標籤的字型。這些都屬於 **customize chart size** 以及整體格式化的範疇。

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Edge case:** 若之後將文件匯出為 PDF，圖表的向量資料仍保持清晰，因為尺寸是以點 (points) 為單位定義，而非像素。這對 **format chart Word** 以及後續格式都有好處。

## Step 6: Save and view the document

最後一步只要呼叫 `doc.save` 即可。這會產生一個 `.docx` 檔，你可以在 Microsoft Word、LibreOffice 或任何支援 OpenXML 的檢視器中開啟。

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Result:** 開啟 `PieChart.docx`，即可看到尺寸恰當的圓餅（或甜甜圈）圖表，包含炸出的切片、標題與圖例——全部在未觸碰 UI 的情況下自動產生。

### Expected Output

| Element | What you’ll see |
|---------|-----------------|
| Chart type | Pie chart (or doughnut if `holeSize` > 0) |
| Slice explosion | First slice offset by 20 pts |
| Legend | Positioned on the right |
| Title | “Quarterly Sales Distribution” in bold 14 pt |
| Data labels | Category name and value shown on each slice |
| Document | A standard Word `.docx` file ready for sharing |

## Common Questions & Gotchas

- **Do I need a license?**  
  評估版可用於測試，但會加上水印。將 `aspose.words.lic` 檔放入 classpath，即可產生無水印的輸出。

- **Can I use this with Maven?**  
  當然可以。將以下相依性加入 `pom.xml`：

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **What if I have more than one series?**  
  透過 `pieChart.getSeries()` 迴圈，對每個系列分別呼叫 `setExplosion`、`setFillColor` 或其他格式設定。這就是在 **format pie chart** 多維度資料時的做法。

- **Is the chart editable in Word after generation?**  
  可以——儲存後，你可以在 Word 中手動調整顏色、字型，甚至將圓餅圖轉換成長條圖等。

## Wrap‑Up

我們已使用 Aspose.Words for Java **inserted pie chart** 到 Word 文件，示範了如何 **generate doughnut chart**、多種 **format pie chart** 方法，說明了 **format chart Word** 的最佳實踐，並學會了 **customize chart size** 以達到精緻外觀。上方完整、可執行的範例可直接放入任何 Java 專案，讓你立即擁有圖表自動化功能，無需 COM interop 或 Office 安裝的負擔。

接下來可以嘗試將資料來源換成即時資料庫、根據門檻自動變更顏色，或將同一文件匯出為 PDF 產出列印版報告。每一步都建立在我們已鋪好的基礎上，轉換過程相當順暢。

如果在實作過程中遇到問題，或有其他想法（例如堆疊長條圖或折線圖），歡迎在下方留言。祝你圖表製作愉快！

## What Should You Learn Next?

以下教學與本指南緊密相關，能進一步深化你對 API 的掌握，並探索在專案中實作的其他方式。

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Number Format For Axis In A Chart](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}