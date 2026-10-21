---
category: general
date: 2026-08-20
description: 快速在 Java 中為餅圖添加領線。學習使用 Chart API 插入、分離、重新著色及標註切片。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: zh-hant
lastmod: 2026-08-20
og_description: 在 Java 中為圓餅圖新增領線，並提供簡潔範例。跟隨本指南，使用 Chart API 插入、分離、重新著色及標註切片。
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: 在 Java 中為餅圖添加引線 – 步驟式 Chart API 指南
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: 如何在 Java 使用 Chart API 為餅圖添加領導線
url: /zh-hant/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中使用 Chart API 為圓餅圖加入指示線

如果你需要 **為圓餅圖加入指示線**，本指南將一步步帶你完成整個流程。你將學會如何插入圓餅圖、將切片突出顯示、變更其顏色，最後啟用指示線以標示被突出顯示的區段。

本範例使用許多 Java 報表函式庫中提供的標準 Chart API。無需額外工具，程式碼可在任何 JDK 8+ 環境下執行。

## 你將達成的目標

完成本教學後，你將能夠：

* 建立 `Chart` 類型為 `ChartType.PIE` 且自訂尺寸的圖表。  
* 將第一個切片突出顯示以引起注意。  
* 將被突出顯示的切片顏色設定為藍色。  
* **為圓餅圖加入指示線**，使切片標籤清晰連結。

你應該已經在專案中加入了 Chart 函式庫的 classpath。若使用 Maven，請在先決條件區段加入相應的相依性。

## 先決條件

* 已安裝 JDK 8 或更新版本。  
* 已加入 Chart 函式庫（例如 `com.example.chart:chart-api:2.5.0`）。  
* 具備基本的 Java 類別與方法呼叫概念。

---

## 如何為圓餅圖加入指示線

以下是一個完整、可直接執行的程式範例，示範每一步驟。程式碼刻意保持自足，讓你可以直接複製、貼上並執行，無需額外修改。

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### 各步驟說明

| 步驟 | 程式碼功能 | 為何重要 |
|------|------------|----------|
| **1️⃣ 插入圓餅圖** | `builder.insertChart(ChartType.PIE, 400, 300)` 產生 400 × 300 像素的圓餅圖。 | 建立圖表容器並定義尺寸，會影響標籤位置與指示線長度。 |
| **2️⃣ 突出第一個切片** | `setExplosion(20)` 使切片偏移半徑的 20 %。 | 突出的切片能吸引觀者目光，同時讓指示線更易辨識。 |
| **3️⃣ 設定切片顏色** | `setSectorColor(Color.BLUE)` 將切片填色改為藍色。 | 顏色對比提升可讀性，特別是在切片被強調時。 |
| **4️⃣ 啟用指示線** | `setLeaderLines(true)` 開啟連接切片與標籤的指示線。 | 指示線確保即使切片向外移動，標籤仍保持可讀。 |

`saveAsPng` 呼叫為可選項目，但有助於驗證視覺結果。執行程式後，你應該會看到如下圖所示的圖片。

![為圓餅圖加入指示線](https://example.com/assets/pie-leader-lines.png "為圓餅圖加入指示線 – 突出藍色切片並帶有指示線")

*圖說：第一個切片被突出、著藍色，並以指示線連接其標籤的圓餅圖。*

## 客製化指示線（進階）

基本的 `setLeaderLines(true)` 會使用函式庫的預設樣式。你也可以進一步控制外觀：

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

在需要符合企業品牌或提升可及性時，這些選項相當實用。

### 處理多系列圖表

若圓餅圖包含多個系列，可能只想為特定切片顯示指示線。使用系列索引即可定位正確的元素：

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

當切片未被突出時，指示線通常會自動隱藏；但你可以透過 `setLeaderLineEnabled(true)` 強制顯示。

## 常見問題與避免方式

| 問題 | 現象 | 解決方法 |
|------|------|----------|
| **指示線未顯示** | 圖表渲染時沒有連接線。 | 確認切片已被突出 (`setExplosion` > 0) 或在切片上明確啟用指示線。 |
| **標籤重疊** | 標籤彼此相撞。 | 增大圖表尺寸或設定 `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)`。 |
| **顏色未套用** | 切片仍為預設顏色。 | 確認你針對正確的系列索引 (`getSeries().get(0)`)。 |
| **圖片未儲存** | `saveAsPng` 拋出例外。 | 檢查輸出目錄寫入權限，並確認函式庫支援 PNG 匯出。 |

提前處理這些問題可避免執行時的意外，並產出更精緻的圖表。

## 完整程式碼清單

為了方便起見，以下再次提供完整的原始檔案，包含匯入語句與註解：

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

執行此程式會產生 `pie-with-leader-lines.png`，顯示一個帶有突出藍色切片與清晰指示線的圓餅圖。

## 結論

現在你已掌握如何在 Java 中使用 Chart API **為圓餅圖加入指示線**。整個流程包括插入 `ChartType.PIE`、突出目標切片、客製化顏色，最後啟用指示線。透過可選的樣式設定，你還可以微調線條顏色、粗細與標籤位置，以符合任何視覺需求。

接下來，建議你探索以下相關主題，如 **pie chart explosion Java**、**set sector color Chart API**、以及 **builder.insertChart 用法**，以建立更進階的視覺化圖表，例如甜甜圈圖、堆疊圓餅圖或互動式儀表板。

盡情嘗試不同的切片索引、顏色與指示線樣式——每一次微調都會讓你的圖表更具資訊性與美觀度。祝程式開發愉快！

## 接下來你可以學什麼？

以下教學與本指南緊密相關，能進一步深化你所學的技巧。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助你掌握更多 API 功能，並在自己的專案中嘗試不同的實作方式。

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Add Date Time Values To Axis Of A Chart](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}