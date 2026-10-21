---
title: 使用 Aspose.Words for .NET 在柱形圖中設定統一的資料標籤
weight: 110
limit:
description: 學習如何使用 Aspose.Words for .NET 建立 Word 柱形圖，並將統一的資料標籤字型大小與顏色套用至所有系列。
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 學習如何使用 Aspose.Words for .NET 建立 Word 柱形圖，並將統一的資料標籤字型大小與顏色套用至所有系列。
  headline: 使用 Aspose.Words for .NET 在柱形圖中設定統一的資料標籤
  type: TechArticle
- description: 學習如何使用 Aspose.Words for .NET 建立 Word 柱形圖，並將統一的資料標籤字型大小與顏色套用至所有系列。
  name: 使用 Aspose.Words for .NET 在柱形圖中設定統一的資料標籤
  steps:
  - name: 建立一個新的空白 Word 文件，並使用 DocumentBuilder 進行編輯。
    text: 建立一個新的空白 Word 文件，並使用 DocumentBuilder 進行編輯。
  - name: 在文件中插入一個 500×300 的柱形圖，並取得其 Chart 物件。
    text: 在文件中插入一個 500×300 的柱形圖，並取得其 Chart 物件。
  - name: 移除 Aspose.Words 為新圖表自動加入的預設範例系列。
    text: 移除 Aspose.Words 為新圖表自動加入的預設範例系列。
  - name: 定義類別標籤，並將兩個資料系列（Item Alpha 與 Item Beta）及其數值加入圖表。
    text: 定義類別標籤，並將兩個資料系列（Item Alpha 與 Item Beta）及其數值加入圖表。
  - name: 設定基礎字型大小與顏色，將套用於所有資料標籤。
    text: 設定基礎字型大小與顏色，將套用於所有資料標籤。
  - name: 為每個系列啟用資料標籤、顯示數值，並套用預先定義的字型大小與顏色。
    text: 為每個系列啟用資料標籤、顯示數值，並套用預先定義的字型大小與顏色。
  - name: 將文件儲存為 .docx 檔案。
    text: 將文件儲存為 .docx 檔案。
  type: HowTo
- questions:
  - answer: '`InsertChart` 會建立一個帶有預設範例系列的圖表；呼叫 Clear 會移除該佔位系列，使圖表僅顯示您加入的系列（`Item Alpha`
      與 `Item Beta`）。'
    question: 為什麼在加入自訂系列之前，需要呼叫 `chart.Series.Clear()`？
  - answer: 將 `Color.White` 替換為任意 `System.Drawing.Color` 值，例如 `Color.Black` 或 `Color.FromArgb(255,
      30, 144, 255)`；新顏色會在迴圈中透過 `series.DataLabels.Font.Color` 套用。
    question: 如何將資料標籤的顏色改成非白色？
  - answer: 資料標籤會被隱藏，導致您設定的字型樣式無法顯示；必須將 `HasDataLabels` 保持為 `true`，標籤及其樣式才會出現。
    question: 如果在設定字型大小與顏色之後，將 `series.HasDataLabels = false`，會發生什麼情況？
  - answer: 是的——每個 `ChartSeries` 都有自己的 `DataLabels` 物件，因此在首次迴圈之後新增的任何系列，都必須同樣設定 `HasDataLabels`、`ShowValue`
      以及字型屬性，可透過再次遍歷或將樣式抽取成輔助方法來完成。
    question: 如果稍後在程式碼中再加入另一個系列，是否需要再次遍歷所有系列？
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: 將統一的資料標籤套用至 Word 圖表
og_description: 使用 Aspose.Words for .NET 快速為所有圖表標籤設定相同的字型大小與顏色。
og_image_alt: 本指南展示使用 Aspose.Words for .NET 建立的 Word 文件，其中的柱形圖所有資料標籤共用相同的字型大小與顏色。
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在柱形圖中設定統一的資料標籤
本教學說明如何使用 Aspose.Words for .NET 產生 Word 文件、插入柱形圖，並加入自訂資料系列。接著示範如何定義預設的資料標籤字型大小與顏色，使圖表中的每個系列都顯示相同的標籤。透過套用單一樣式，即可確保整個圖表的視覺外觀保持一致。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/uniform-data-labels" >}}


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

**Q: 為什麼在加入自訂系列之前，需要呼叫 `chart.Series.Clear()`？**  
A: `InsertChart` 會建立一個帶有預設範例系列的圖表；呼叫 Clear 會移除該佔位系列，使圖表僅顯示您加入的系列（`Item Alpha` 與 `Item Beta`）。

**Q: 如何將資料標籤的顏色改成非白色？**  
A: 將 `Color.White` 替換為任意 `System.Drawing.Color` 值，例如 `Color.Black` 或 `Color.FromArgb(255, 30, 144, 255)`；新顏色會在迴圈中透過 `series.DataLabels.Font.Color` 套用。

**Q: 如果在設定字型大小與顏色之後，將 `series.HasDataLabels = false`，會發生什麼情況？**  
A: 資料標籤會被隱藏，導致您設定的字型樣式無法顯示；必須將 `HasDataLabels` 保持為 `true`，標籤及其樣式才會出現。

**Q: 如果稍後在程式碼中再加入另一個系列，是否需要再次遍歷所有系列？**  
A: 是的——每個 `ChartSeries` 都有自己的 `DataLabels` 物件，因此在首次迴圈之後新增的任何系列，都必須同樣設定 `HasDataLabels`、`ShowValue` 以及字型屬性，可透過再次遍歷或將樣式抽取成輔助方法來完成。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}