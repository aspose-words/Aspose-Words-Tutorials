---
title: 使用 Aspose.Words for .NET 在 Word 圖表中將次要 Y 軸格式化為貨幣
weight: 710
limit:
description: 學習在 Word 折線圖中加入並將次要 Y 軸格式化為貨幣，使用 Aspose.Words for .NET。
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 學習在 Word 折線圖中加入並將次要 Y 軸格式化為貨幣，使用 Aspose.Words for .NET。
  headline: 使用 Aspose.Words for .NET 在 Word 圖表中將次要 Y 軸格式化為貨幣
  type: TechArticle
- description: 學習在 Word 折線圖中加入並將次要 Y 軸格式化為貨幣，使用 Aspose.Words for .NET。
  name: 使用 Aspose.Words for .NET 在 Word 圖表中將次要 Y 軸格式化為貨幣
  steps:
  - name: 建立一個新的空白 Word 文件，並使用 DocumentBuilder 進行編輯。
    text: 建立一個新的空白 Word 文件，並使用 DocumentBuilder 進行編輯。
  - name: 在文件中插入大小為 450×250 點的折線圖，並取得其 Chart 物件。
    text: 在文件中插入大小為 450×250 點的折線圖，並取得其 Chart 物件。
  - name: 移除 Aspose 為新圖表自動加入的預設佔位系列。
    text: 移除 Aspose 為新圖表自動加入的預設佔位系列。
  - name: 定義季別標籤，並向圖表加入帶有範例數值的主要資料系列。
    text: 定義季別標籤，並向圖表加入帶有範例數值的主要資料系列。
  - name: 建立一個類型為 Line 的次要系列群組，並指派給次要軸群組。
    text: 建立一個類型為 Line 的次要系列群組，並指派給次要軸群組。
  - name: 隱藏次要 X 軸，使僅顯示次要 Y 軸。
    text: 隱藏次要 X 軸，使僅顯示次要 Y 軸。
  - name: 顯示次要 Y 軸標題，並將文字設定為「Sales (USD)」。
    text: 顯示次要 Y 軸標題，並將文字設定為「Sales (USD)」。
  - name: 將次要 Y 軸的數字格式設定為帶兩位小數的貨幣模式，並取消與來源格式的連結。
    text: 將次要 Y 軸的數字格式設定為帶兩位小數的貨幣模式，並取消與來源格式的連結。
  - name: 向次要群組加入輔助系列，提供將以次要 Y 軸繪製的資料。
    text: 向次要群組加入輔助系列，提供將以次要 Y 軸繪製的資料。
  - name: 將完成的文件儲存為當前目錄下名為 ProfitChart.docx 的檔案。
    text: 將完成的文件儲存為當前目錄下名為 ProfitChart.docx 的檔案。
  type: HowTo
- questions:
  - answer: 圖表會保留 Aspose.Words 插入的預設佔位系列，因此您的自訂「Main Series」會與不需要的資料點一起顯示。
    question: 如果省略 `lineChart.Series.Clear()` 呼叫，會發生什麼情況？
  - answer: 設定 `secondarySeriesGroup.AxisX.Hidden = false;`（或直接省略將其設為 `true` 的那一行）。
    question: 如何顯示次要 X 軸而不是隱藏它？
  - answer: 可以 – 變更格式字串，例如 `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = \"\\\"€\\\"#,##0.00\";`
      以使用歐元，或依照您的地區調整模式。
    question: 我可以為次要 Y 軸使用不同的貨幣符號或格式嗎？
  - answer: 當 `IsLinkedToSource` 為 true 時，軸會從底層資料來源繼承數字格式，會覆寫任何自訂的 `FormatCode`；將其設為
      false 則強制圖表使用您指定的格式。
    question: 為什麼在套用自訂數字格式時需要將 `IsLinkedToSource = false` 設為 false？
  - answer: 可以，將 `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;`（預設為 `Right`）指派即可控制軸繪製於哪一側。
    question: 是否可以將次要 Y 軸移至圖表的左側？
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: 將圖表的次要軸格式化為貨幣
og_description: 學習在 Word 折線圖中加入次要 Y 軸，並以兩位小數的貨幣樣式設定。
og_image_alt: 螢幕截圖顯示使用 Aspose.Words for .NET 的 Word 折線圖，次要 Y 軸已格式化為貨幣
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 圖表中將次要 Y 軸格式化為貨幣
在本教學中，您將看到如何使用 Aspise.Words for .NET 建立 Word 文件、插入折線圖、加入次要 Y 軸、將該軸格式化為帶兩位小數的貨幣，並將次要資料系列繫結至該軸。將次要軸格式化為貨幣可讓您清晰地在主要系列旁呈現財務資料。請依照逐步程式碼操作，即可在產生的文件中直接看到圖表呈現。

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

**Q: 如果省略 `lineChart.Series.Clear()` 呼叫，會發生什麼情況？**  
A: 圖表會保留 Aspose.Words 插入的預設佔位系列，因此您的自訂「Main Series」會與不需要的資料點一起顯示。

**Q: 如何顯示次要 X 軸而不是隱藏它？**  
A: 設定 `secondarySeriesGroup.AxisX.Hidden = false;`（或直接省略將其設為 `true` 的那一行）。

**Q: 我可以為次要 Y 軸使用不同的貨幣符號或格式嗎？**  
A: 可以 – 變更格式字串，例如 `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = \"\\\"€\\\"#,##0.00\";` 以使用歐元，或依照您的地區調整模式。

**Q: 為什麼在套用自訂數字格式時需要將 `IsLinkedToSource = false` 設為 false？**  
A: 當 `IsLinkedToSource` 為 true 時，軸會從底層資料來源繼承數字格式，會覆寫任何自訂的 `FormatCode`；將其設為 false 則強制圖表使用您指定的格式。

**Q: 是否可以將次要 Y 軸移至圖表的左側？**  
A: 可以，將 `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;`（預設為 `Right`）指派即可控制軸繪製於哪一側。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}