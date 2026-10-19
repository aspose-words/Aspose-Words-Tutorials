---
title: 使用 Aspose.Words for .NET 在 Word 折線圖中格式化次要 X 軸並將顯示單位設定為千位
weight: 710
limit:
description: 使用 Aspose.Words for .NET 建立 Word 折線圖、加入次要 X 軸、將顯示單位設定為千位，並套用自訂數字格式。
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 使用 Aspose.Words for .NET 建立 Word 折線圖、加入次要 X 軸、將顯示單位設定為千位，並套用自訂數字格式。
  headline: 使用 Aspose.Words for .NET 在 Word 折線圖中格式化次要 X 軸並將顯示單位設定為千位
  type: TechArticle
- description: 使用 Aspose.Words for .NET 建立 Word 折線圖、加入次要 X 軸、將顯示單位設定為千位，並套用自訂數字格式。
  name: 使用 Aspose.Words for .NET 在 Word 折線圖中格式化次要 X 軸並將顯示單位設定為千位
  steps:
  - name: 建立新的 Document 與 DocumentBuilder，以開始建構 Word 檔案。
    text: 建立新的 Document 與 DocumentBuilder，以開始建構 Word 檔案。
  - name: 在文件中插入大小為 500×300 的折線圖，並取得 Chart 物件。
    text: 在文件中插入大小為 500×300 的折線圖，並取得 Chart 物件。
  - name: 移除 Aspose.Words 自動加入的預設示範資料列。
    text: 移除 Aspose.Words 自動加入的預設示範資料列。
  - name: 定義一個用於 X 軸的類別標籤陣列。
    text: 定義一個用於 X 軸的類別標籤陣列。
  - name: 使用標籤與數值，新增名稱為「Main Data」的主要資料系列。
    text: 使用標籤與數值，新增名稱為「Main Data」的主要資料系列。
  - name: 建立類型為 Line 的次要系列群組，並指派給次要軸群組。
    text: 建立類型為 Line 的次要系列群組，並指派給次要軸群組。
  - name: 將次要 X 軸的顯示單位設定為千位，讓數值以 K 為單位顯示。
    text: 將次要 X 軸的顯示單位設定為千位，讓數值以 K 為單位顯示。
  - name: 對次要 X 軸的刻度標籤套用自訂數字格式「#,##0.0」。
    text: 對次要 X 軸的刻度標籤套用自訂數字格式「#,##0.0」。
  - name: 可選地向次要群組加入輔助資料系列。
    text: 可選地向次要群組加入輔助資料系列。
  - name: 將文件儲存為 .docx 檔案。
    text: 將文件儲存為 .docx 檔案。
  type: HowTo
- questions:
  - answer: 不會——`AxisX` 設定屬於 `ChartSeriesGroup`，因此您可以在加入系列之前或之後設定 `secondaryGroup.AxisX.DisplayUnit.Unit`
      與 `secondaryGroup.AxisX.NumberFormat.FormatCode`；設定會套用到該群組的軸上。
    question: 我是否必須在設定次要 X 軸的顯示單位與數字格式之前，先加入次要系列？
  - answer: 可以——指派任意 `AxisBuiltInUnit` 值，例如 `secondaryGroup.AxisX.DisplayUnit.Unit
      = AxisBuiltInUnit.Millions;`，即可將軸值顯示為百萬而非千位。
    question: 我可以為次要 X 軸使用其他內建單位，例如百萬嗎？
  - answer: 不會——格式碼僅套用於您修改的軸 (`secondaryGroup.AxisX.NumberFormat.FormatCode`)，因此主要
      X 軸會保留其預設格式。
    question: 自訂格式「#,##0.0」會影響主要 X 軸的標籤嗎？
  - answer: 圖表會同時包含預設的示範系列以及您自行加入的系列，可能導致多餘的線條與類別不匹配；清除集合可確保僅顯示您預期的資料。
    question: 如果忘記使用 `lineChart.Series.Clear();` 清除示範系列，會發生什麼情況？
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: 格式化次要 X 軸並將單位設定為千位
og_description: 在 Word 折線圖中加入次要 X 軸，並以自訂樣式將其標籤格式化為千位。
og_image_alt: 指南說明如何使用 Aspose.Words for .NET 在 Word 折線圖中加入次要 X 軸，並將標籤格式化為千位顯示單位。
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 折線圖中格式化次要 X 軸並將顯示單位設定為千位
本教學逐步說明如何建立包含折線圖的 Word 文件、加入次要 X 軸，並將該軸設定為以千位顯示數值。您還將學習如何對次要軸標籤套用自訂數字格式，從而精確控制資料的呈現方式。依照步驟操作，可提升 Word 報告中多軸圖表的可讀性。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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

**Q: 我是否必須在設定次要 X 軸的顯示單位與數字格式之前，先加入次要系列？**  
A: 不會——`AxisX` 設定屬於 `ChartSeriesGroup`，因此您可以在加入系列之前或之後設定 `secondaryGroup.AxisX.DisplayUnit.Unit` 與 `secondaryGroup.AxisX.NumberFormat.FormatCode`；設定會套用到該群組的軸上。

**Q: 我可以為次要 X 軸使用其他內建單位，例如百萬嗎？**  
A: 可以——指派任意 `AxisBuiltInUnit` 值，例如 `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;`，即可將軸值顯示為百萬而非千位。

**Q: 自訂格式「#,##0.0」會影響主要 X 軸的標籤嗎？**  
A: 不會——格式碼僅套用於您修改的軸 (`secondaryGroup.AxisX.NumberFormat.FormatCode`)，因此主要 X 軸會保留其預設格式。

**Q: 如果忘記使用 `lineChart.Series.Clear();` 清除示範系列，會發生什麼情況？**  
A: 圖表會同時包含預設的示範系列以及您自行加入的系列，可能導致多餘的線條與類別不匹配；清除集合可確保僅顯示您預期的資料。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}