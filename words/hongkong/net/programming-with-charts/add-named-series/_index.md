---
title: 使用 Aspose.Words for .NET 在 Word 直方圖圖表中加入具名稱的資料系列
weight: 610
limit:
description: 了解如何在 Word 文件中嵌入直方圖圖表，並使用 Aspose.Words for .NET 加入具名稱的資料系列。
keywords: [Aspose.Words for .NET, add named series chart, histogram chart in Word, ChartSeriesCollection Add overload, DocumentBuilder chart example, named data series Word]
url: /net/programming-with-charts/add-named-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 了解如何在 Word 文件中嵌入直方圖圖表，並使用 Aspose.Words for .NET 加入具名稱的資料系列。
  headline: 使用 Aspose.Words for .NET 在 Word 直方圖圖表中加入具名稱的資料系列
  type: TechArticle
- description: 了解如何在 Word 文件中嵌入直方圖圖表，並使用 Aspose.Words for .NET 加入具名稱的資料系列。
  name: 使用 Aspose.Words for .NET 在 Word 直方圖圖表中加入具名稱的資料系列
  steps:
  - name: 建立一個全新的空白 Word 文件，並使用 DocumentBuilder 進行編輯。
    text: 建立一個全新的空白 Word 文件，並使用 DocumentBuilder 進行編輯。
  - name: 在文件中插入大小為 500×300 的直方圖圖表形狀，並取得其 Chart 物件。
    text: 在文件中插入大小為 500×300 的直方圖圖表形狀，並取得其 Chart 物件。
  - name: 移除 Aspose.Words 為新圖表自動加入的預設佔位系列。
    text: 移除 Aspose.Words 為新圖表自動加入的預設佔位系列。
  - name: 在直方圖圖表中加入名為「Demo Series」且包含指定資料點的系列。
    text: 在直方圖圖表中加入名為「Demo Series」且包含指定資料點的系列。
  - name: 將文件儲存為包含已標籤圖表系列的 .docx 檔案。
    text: 將文件儲存為包含已標籤圖表系列的 .docx 檔案。
  type: HowTo
- questions:
  - answer: '`InsertChart` 會建立預設的佔位系列；清除它可移除該空白系列，讓圖表僅顯示您透過 `Series.Add` 新增的資料。'
    question: 為什麼在加入自訂系列之前，需要呼叫 `histogramChart.Series.Clear()`？
  - answer: 可以，對 `histogramChart.Series.Add` 呼叫多次，每次提供不同的名稱與 `double[]` 數值；每個系列都會在圖例中以提供的名稱顯示。
    question: 我可以使用相同的重載新增多個系列嗎？每個系列會否各自顯示其標籤？
  - answer: 此重載僅接受 `double[]`；若您有 `int[]` 或其他數值陣列，請先轉型或轉換為 `double[]` 再傳入。
    question: '`double[]` 參數是唯一接受的資料點類型嗎？'
  - answer: 作為第一個參數傳入的字串（例如「Demo Series」）會作為系列標題，預設會顯示在圖表圖例中。
    question: 我提供的系列名稱會自動顯示在圖表上嗎？
  type: FAQPage
images:
- /net/programming-with-charts/add-named-series/og-image.png
og_title: 在 Word 直方圖圖表中加入具名稱的系列
og_description: 使用 Aspose.Words 快速為 Word 圖表系列加上標籤，並即時顯示渲染結果。
og_image_alt: 螢幕截圖顯示使用 Aspose.Words for .NET 建立、包含帶標籤資料系列的直方圖圖表的 Word 文件。
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 直方圖圖表中加入具名稱的資料系列
本教學示範如何使用 Aspose.Words for .NET 建立 Word 文件、插入直方圖圖表，並使用接受名稱與數值的 ChartSeriesCollection.Add 重載來新增帶標籤的資料系列。為系列命名可清楚辨識圖表中的每個資料集，讓視覺輸出更易於閱讀與解釋。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/add-named-series" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: 為什麼在加入自訂系列之前，需要呼叫 `histogramChart.Series.Clear()`？**  
A: `InsertChart` 會建立預設的佔位系列；清除它可移除該空白系列，讓圖表僅顯示您透過 `Series.Add` 新增的資料。

**Q: 我可以使用相同的重載新增多個系列嗎？每個系列會否各自顯示其標籤？**  
A: 可以，對 `histogramChart.Series.Add` 呼叫多次，每次提供不同的名稱與 `double[]` 數值；每個系列都會在圖例中以提供的名稱顯示。

**Q: `double[]` 參數是唯一接受的資料點類型嗎？**  
A: 此重載僅接受 `double[]`；若您有 `int[]` 或其他數值陣列，請先轉型或轉換為 `double[]` 再傳入。

**Q: 我提供的系列名稱會自動顯示在圖表上嗎？**  
A: 作為第一個參數傳入的字串（例如「Demo Series」）會作為系列標題，預設會顯示在圖表圖例中。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}