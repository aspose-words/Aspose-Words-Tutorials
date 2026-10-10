---
category: general
date: 2026-10-10
description: 學習如何在 Word 檔案中旋轉圖表，並在 Word 中修改圖表以調整環形圖的大小，並提供完整的 Java 範例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: zh-hant
lastmod: 2026-10-10
og_description: 如何在 Word 檔案中旋轉圖表，並使用 Aspose.Words for Java 修改圖表以調整環形圖大小。
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: 如何在 Word 文件中旋轉圖表 – Java 逐步指南
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: 如何在 Word 文件中使用 Aspose.Words 旋轉圖表
url: /zh-hant/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中使用 Aspose.Words 旋轉圖表

如果您需要在 Microsoft Word 檔案中 **旋轉圖表**，本教學會一步步說明。您還會學會如何 **在 Word 中修改圖表**，以 **變更環形圖大小**，且全程不離開 Java 程式碼。

Word 自動化常常感覺像是一系列不相關的 API 呼叫，但使用 Aspose.Words 時，您可以把圖表當作文件中的其他節點來處理。完成本教學後，您將擁有一個可執行的程式，能載入既有的 `.docx`，將環形圖旋轉 45°，將環孔縮小至半徑的 50%，並將結果另存為新檔案。

## 前置條件

在開始之前，請確保您已具備：

* 已安裝 Java 17 或更新版本。
* Maven（或 Gradle）用於管理相依性。
* 一個已包含環形圖的輸入 Word 文件（`input.docx`）。
* 有效的 Aspose.Words for Java 授權（或使用評估模式）。

## 第一步：建立 Maven 專案

建立一個新的 Maven 專案，或在現有的 `pom.xml` 中加入以下相依性：

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

執行 `mvn clean install` 後，會下載函式庫並將類別加入您的 classpath。

## 第二步：載入包含圖表的 Word 文件

第一個動作是開啟既有文件。`Document` 類別代表整個檔案。

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

載入檔案 **不會** 修改它；它只會在記憶體中建立一個可供查詢與編輯的表示。

## 第三步：建立 DocumentBuilder 以便導航

`DocumentBuilder` 提供類似游標的 API，讓您在文件樹中走訪。我們會使用它來定位第一個圖表形狀。

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

建構子預設位於文件開頭，之後若需要也可以將它移動到任意節點。

## 第四步：取得第一個圖表形狀

圖表以 `Shape` 節點儲存。透過過濾 `NodeType.SHAPE` 類型的子節點，我們即可取得圖表物件。

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

若文件中有多個圖表，您可以遍歷 `getChildNodes`，並在每個 `Shape` 上檢查 `hasChart()` 後再進行型別轉換。

## 第五步：旋轉圖表（how to rotate chart）

環形圖本質上是帶孔的圓餅圖。旋轉它會改變第一片的起始角度。

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

`setStartAngle` 方法接受以度數表示的 double 值。正值代表順時針旋轉，負值則為逆時針。

## 第六步：變更環形孔大小（change doughnut chart size）

孔的大小以圖表半徑的比例表示。`0.5` 代表孔佔總半徑的 50%。

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**小技巧：** 有效範圍為 `0.0`（無孔，即普通圓餅圖）到 `0.9`（非常細的環）。超出此範圍會拋出 `IllegalArgumentException`。

## 第七步：儲存已修改的文件

最後，將變更寫回磁碟。

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

當您在 Microsoft Word 中開啟 `DoughnutFormatted.docx` 時，會看到環形圖已旋轉 45°，且孔的大小縮小為原來的一半。

## 完整可執行範例

將所有片段組合起來，以下是您可以直接貼到 IDE 中的完整程式碼：

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### 預期輸出

執行程式會印出：

```
Chart rotated and doughnut size changed successfully.
```

開啟 `DoughnutFormatted.docx` 後，可看到環形圖的第一片起始於 45° 位置，且內半徑佔外半徑的一半。

## 常見變化與邊緣情況

| 情境 | 需要調整的地方 | 為什麼重要 |
|-----------|----------------|----------------|
| **多個圖表** | 迭代 `getChildNodes(NodeType.SHAPE, true)`，並對每個 `shape.hasChart()` 進行檢查 | 確保您修改的是目標圖表，而非第一個圖表 |
| **長條圖或折線圖** | `setStartAngle` 不適用；可使用 `chart.getSeries().get(0).setFillFormat(...)` 進行其他視覺調整 | 並非所有圖表類型都支援旋轉，只有環形/圓餅圖有起始角度設定 |
| **沒有環形孔的圖表** | 跳過 `setDoughnutHoleSize`，或先透過 `chart.setChartType(ChartType.DONUT)` 轉換為環形圖 | 在非環形圖上變更孔大小會拋出例外 |
| **大型文件** | 使用 `DocumentBuilder.moveToDocumentStart()` 並 `builder.moveToNode(chartShape)` 直接定位 | 可避免遍歷不相關節點，提高效能 |

## 可靠圖表操作的專業技巧

* **快取圖表參考** – 若要一次修改多個屬性，請將 `Chart` 物件存入本地變數，而不是重複呼叫 `chartShape.getChart()`。
* **驗證輸入值** – 在呼叫 `setStartAngle` 或 `setDoughnutHoleSize` 前，先檢查數值範圍，以免執行時錯誤。
* **使用授權** – 評估模式會在首頁插入浮水印。加入授權 (`License license = new License(); license.setLicense("Aspose.Words.lic");`) 後即可移除。

## 往下走

現在您已掌握 **旋轉圖表** 與 **變更環形圖大小** 的技巧，接下來可以探索其他 **在 Word 中修改圖表** 的情境：

* 使用 `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())` 變更切片顏色。
* 透過 `chart.getSeries().get(0).setHasDataLabel(true)` 加入資料標籤。
* 使用 `chart.toImage(300, 300, ImageType.PNG)` 將圖表匯出為影像。

上述所有延伸都遵循相同模式：取得 `Chart` 物件、呼叫相應的 setter，最後儲存文件。

---

**您已成功使用 Java 在 Word 中旋轉並調整環形圖尺寸。** 歡迎將此程式碼套用到其他圖表類型、整合至更大的文件產生流程，或與 Aspose.Slides 結合實作 PowerPoint 自動化。祝開發愉快！

## 接下來該學什麼？

以下教學與本篇內容密切相關，能在此基礎上延伸更多技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，助您掌握更多 API 功能，並在專案中探索不同的實作方式。

- [如何使用 Aspose.Words for Java 建立直條圖](/words/english/java/document-conversion-and-export/using-charts/)
- [在 Word 文件中隱藏圖表座標軸](/words/english/net/programming-with-charts/hide-chart-axis/)
- [在 Word 文件中插入氣泡圖](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}