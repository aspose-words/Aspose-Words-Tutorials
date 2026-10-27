---
category: general
date: 2026-07-20
description: 在 Java 中插入圓餅圖，提供逐步指南。學習如何將切片分離、如何旋轉圓餅圖、如何突顯圓餅圖切片以及如何自訂圓餅圖切片。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: zh-hant
lastmod: 2026-07-20
og_description: 在 Java 中插入餅圖，並掌握如何將切片分離、旋轉餅圖、突顯餅圖切片，以及自訂餅圖切片，以製作精緻的視覺報告。
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: 在 Java 中插入餅圖 – 分離、旋轉與突顯
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: 在 Java 中插入圓餅圖 – 分離、旋轉與高亮切片
url: /zh-hant/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Java 中插入圓餅圖 – 爆炸、旋轉與突顯切片

是否曾需要在 Java 報表中 **插入圓餅圖**，卻不確定要如何讓單一切片突出顯示？你並非唯一遇到這個問題的人。無論是打造儀表板、產生發票，或是視覺化調查結果，一張設計精美的圓餅圖都能將原始數據瞬間轉化為易於理解的洞見。

在本教學中，你將看到一個完整、可直接執行的範例，說明如何 **插入圓餅圖**、**爆炸切片**、**旋轉圓餅圖**，甚至 **以自訂顏色突顯圓餅圖切片**。完成後，你將擁有一段可重複使用的程式碼，能直接放入任何使用 *JFreeChart*（或類似 API）的 Java 專案中。

## 前置條件

- Java 17 或更新版本（程式碼在舊版亦可編譯，但我們會使用 `var` 語法以簡化程式）。
- Maven 或 Gradle 以取得 `org.jfree:jfreechart` 相依套件。
- 具備基本的 Java 類別概念與圖表建構器的認識。

如果你從未在 Maven 專案中加入套件，只要把以下內容貼到 `pom.xml` 即可：

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

就這樣——不需要額外設定。

## 步驟 1：插入圓餅圖 – 建立 Builder 與 Chart 物件

首先，我們需要一個 *builder*（可視為工廠），負責產生圖表。在 JFreeChart 中，`ChartFactory` 承擔了這項重任。

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

為什麼一開始就建立資料集？因為圖表本身只是數字的視覺化包裝。此時 **插入圓餅圖** 已經產生了一個 400 × 300 的畫布（尺寸會在渲染成影像時套用）。

## 步驟 2：如何爆炸切片 – 強調第一段

圖表已建立，接下來讓第一個切片突出。爆炸切片會將其稍微移離圓心，吸引讀者目光。

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

注意我們在方法名稱中使用了 **how to explode slice** 這個字串，讓意圖一目了然。`setExplodePercent` 方法接受切片標籤與百分比兩個參數，你可以依需求調整「彈出」的距離。

## 步驟 3：如何旋轉圓餅圖 – 變更起始角度

預設的圓餅圖會從 12 點鐘方向開始。有時你希望第一個切片從其他位置開始——可能是為了配合設計稿，或是與其他圖表對齊。

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

呼叫 `rotateChart(chart, 45)` 會將整個圓餅圖旋轉，使「Apples」切片從 45 度角開始，正符合 **how to rotate pie chart** 的需求。

## 步驟 4：突顯圓餅圖切片 – 自訂顏色與標籤

除了爆炸之外，你可能想給某個切片設定獨特顏色或加粗標籤，以真正 **突顯圓餅圖切片**。

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

此處我們 **customize pie chart slice**，透過改變其繪圖顏色與標籤樣式。隨意替換顏色或字型，以符合你的品牌配色。

## 步驟 5：將圖表渲染為影像（可選但實用）

大多數實務應用都需要將圖表輸出為 PNG、JPEG，甚至 PDF。以下提供一個快速寫入檔案的範例。

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

執行完整流程後，會產生一個 400 × 300 的 PNG，效果大致如下：

![Insert pie chart example](image.png){: alt="插入圓餅圖範例，展示已爆炸且已旋轉的切片"}

## 完整可執行範例

將以下程式碼放入全新 Java 類別的 `main` 方法，即可直接執行：

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### 預期輸出

執行程式後會產生名為 **fruit-pie.png** 的檔案。開啟後你會看到：

- 一張 400 × 300 的圓餅圖，標題為「Fruit Distribution」。
- 「Apples」切片向外爆炸 15 %。
- 整個圖表已旋轉，使「Apples」從 45 度位置開始。
- 爆炸的切片已使用自訂顏色與標籤突顯。

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，進一步擴充你在本篇示範中學到的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助你掌握更多 API 功能，並在自己的專案中探索其他實作方式。

- [如何使用 Aspose.Words for Java 建立柱狀圖](/words/english/java/document-conversion-and-export/using-charts/)
- [插入散點圖](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [插入區域圖](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}