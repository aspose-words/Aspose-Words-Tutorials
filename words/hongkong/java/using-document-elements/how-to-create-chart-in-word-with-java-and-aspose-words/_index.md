---
category: general
date: 2026-09-24
description: 學習如何使用 Java 在 Word 中建立圖表、插入雷達圖，並使用 Aspose.Words 將文件儲存為 docx。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create chart in word
- save document as docx
- add chart to word
- create word document java
- insert radial chart
language: zh-hant
lastmod: 2026-09-24
og_description: 使用 Java 與 Aspose.Words 在 Word 中建立圖表。本教學示範如何加入徑向圖表、客製化資料，並將文件儲存為 docx。
og_image_alt: Radial chart inserted in a Word document using Java code
og_title: 使用 Java 在 Word 中建立圖表 – 步驟教學
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  headline: How to create chart in Word with Java and Aspose.Words
  type: TechArticle
- description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  name: How to create chart in Word with Java and Aspose.Words
  steps:
  - name: You should see a single page with a centered radial chart.
    text: You should see a single page with a centered radial chart.
  - name: If you added series data, the chart displays four slices labeled Q1‑Q4.
    text: If you added series data, the chart displays four slices labeled Q1‑Q4.
  - name: Right‑click the chart → **Edit Data** to confirm the underlying data table.
    text: Right‑click the chart → **Edit Data** to confirm the underlying data table.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Chart
- DOCX
title: 如何使用 Java 與 Aspose.Words 在 Word 中建立圖表
url: /zh-hant/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Java 和 Aspose.Words 在 Word 中建立圖表

如果您需要 **在 Word 中建立圖表**，本指南將帶您完成完整流程。您將看到如何加入徑向圖表、（可選）填入系列資料，最後使用 Aspose.Words for Java 套件 **將文件儲存為 docx**。

在 Word 檔案內產生視覺化資料是報表、發票或自動化文件產生的常見需求。完成本教學後，您將能夠在 **create word document java** 專案中 **add chart to Word** 檔案，且不需任何手動編輯。

## 前置條件

開始之前，請確保您已具備：

* Java Development Kit (JDK) 8 或更新版本。
* 用於相依管理的 Maven 或 Gradle。
* IntelliJ IDEA、Eclipse 或 VS Code 等 IDE。
* 有效的 Aspose.Words for Java 授權（開發階段可使用免費試用版）。

上述工具為以下程式碼範例提供基礎。

## 第一步：設定 Maven 專案

建立一個新的 Maven 專案（或更新既有專案），並在 `pom.xml` 中加入 Aspose.Words 相依性：

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word‑chart‑demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

執行 `mvn clean install` 後，會下載套件並將 `Document`、`DocumentBuilder`、`ChartType` 等類別加入 classpath。

> **專業提示：** 請保持套件版本為最新。新版本會加入更多圖表類型並提升渲染效能。

## 第二步：建立新的 Word 文件

**在 Word 中建立圖表** 的第一個程式化步驟是實例化一個空的 `Document`。此物件代表整個 `.docx` 套件。

```java
import com.aspose.words.*;

public class RadialChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a blank Word document
        Document doc = new Document();

        // Step 2.2: Obtain a DocumentBuilder to insert content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` 如同游標；它知道目前的插入點，並提供插入文字、表格與圖表的方法。此時您已 **created word document java** —— 一個乾淨的畫布，準備加入內容。

## 第三步：插入徑向圖表

Aspose.Words 支援多種圖表類型。若要 **insert radial chart**，呼叫 `insertChart` 並傳入 `ChartType.RADIAL`。此方法同時需要以點 (point) 為單位的寬度與高度（1 point ≈ 1/72 inch）。

```java
        // Step 3: Insert a radial chart (400 × 300 points)
        Shape chart = builder.insertChart(ChartType.RADIAL, 400, 300);
```

回傳的 `Shape` 物件內含底層的圖表物件。圖表會自動為 24.9° 版面產生刻度，這是 Word 中徑向圖表的預設設定。

### 為什麼使用徑向圖表？

徑向圖表將資料圍繞圓形呈現，特別適合顯示週期性模式（例如每月銷售、時鐘式指標）。相同的 API 也可插入長條圖、圓餅圖或折線圖，但徑向類型能在不額外樣式程式碼的情況下提供獨特外觀。

## 第四步：（可選）填入圖表系列資料

若要讓圖表顯示實際數值，必須加入系列與資料點。以下程式碼片段會新增一個包含三個資料點的系列：

```java
        // Optional: add data to the chart
        Chart chartObj = chart.getChart();
        chartObj.getSeries().clear(); // remove any default series

        // Create a new series
        ChartSeries series = chartObj.getSeries().add("Quarterly Revenue");

        // Add data points (value, category)
        series.getDataPoints().add(15000, "Q1");
        series.getDataPoints().add(21000, "Q2");
        series.getDataPoints().add(18000, "Q3");
        series.getDataPoints().add(24000, "Q4");
```

您可以依需求重複 `add` 呼叫以加入更多資料點。Aspose.Words 會自動更新視覺呈現，徑向切片會隨新值調整。

> **常見問題：** *如果要從資料庫綁定資料該怎麼做？*  
> 先取得資料列，於迴圈中呼叫 `series.getDataPoints().add(value, label)`。此 API 為執行緒安全，能與任何您提供的 `ResultSet` 搭配使用。

## 第五步：將文件儲存為 DOCX

圖表完成後，最後一步是 **save document as docx**。`save` 方法會根據檔案副檔名判斷輸出格式。

```java
        // Step 5: Persist the document
        String outputPath = "output/RadialChartDemo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

產生的檔案包含完整功能的徑向圖表，可在 Microsoft Word、LibreOffice 或任何支援 DOCX 格式的檢視器中開啟。由於使用 `.docx` 副檔名，Word 會以 Open XML 格式儲存檔案，這是現代 Word 文件的標準。

### 驗證結果

在 Word 中開啟 `RadialChartDemo.docx`：

1. 您應該會看到單頁且置中的徑向圖表。  
2. 若已加入系列資料，圖表會顯示四個切片，標籤為 Q1‑Q4。  
3. 右鍵點擊圖表 → **Edit Data** 以確認底層資料表。

若圖表顯示為空白，請再次確認已在加入系列前呼叫 `chart.getChart()`，且文件建構器的游標已定位於欲插入圖表的位置。

## 第六步：進階圖表使用技巧

| Tip | Why it matters |
|-----|----------------|
| **設定圖表樣式** – `chart.getChart().setStyle(ChartStyle.STYLE_PRESET_5);` | 在不手動格式化每個元素的情況下提升視覺一致性。 |
| **插入後調整大小** – `chart.setWidth(500); chart.setHeight(350);` | 依頁面版面微調圖表尺寸。 |
| **新增標題** – `chart.getChart().getTitle().setText("Revenue Overview");` | 為未閱讀周圍文字的讀者提供上下文說明。 |
| **匯出為 PDF** – `doc.save("RadialChartDemo.pdf");` | 需要不可編輯版本以供發佈時非常實用。 |
| **授權處理** – `License lic = new License(); lic.setLicense("Aspose.Words.lic");` | 防止評估版浮水印出現在正式建置中。 |

這些增強功能為可選項目，但能示範在您已學會 **add chart to Word** 後，如何進一步自訂圖表。

## 結論

您現在擁有一個完整、獨立的範例，說明如何使用 Java **create chart in Word**、**insert radial chart**、（可選）填入資料，並 **save document as docx**。相同的模式同樣適用於其他圖表類型，您可以依需求延伸至長條圖、折線圖或圓餅圖。

接下來您可以探索：

* 結合表格、圖片與多個圖表的 **create word document java** 專案。  
* 同時使用 **save document as docx** 與 **save document as pdf** 進行多格式報表。  
* 從 REST API 或資料庫動態取得資料填入圖表。

歡迎自行嘗試不同的樣式選項、圖表尺寸與資料來源。祝您開發順利！

## 接下來該學什麼？

以下教學與本指南緊密相關，能在此基礎上進一步擴充技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，並在自己的專案中探索替代實作方式。

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}