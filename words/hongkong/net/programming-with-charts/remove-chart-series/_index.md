---
title: 使用 Aspose.Words for .NET 從 Word 文件中移除圖表系列
weight: 510
limit:
description: 了解如何使用 Aspose.Words for .NET 從 Word 文件中的直條圖刪除特定資料系列。
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 了解如何使用 Aspose.Words for .NET 從 Word 文件中的直條圖刪除特定資料系列。
  headline: 使用 Aspose.Words for .NET 從 Word 文件中移除圖表系列
  type: TechArticle
- description: 了解如何使用 Aspose.Words for .NET 從 Word 文件中的直條圖刪除特定資料系列。
  name: 使用 Aspose.Words for .NET 從 Word 文件中移除圖表系列
  steps:
  - name: 建立一個新的 Word Document，並建立與之關聯的 DocumentBuilder。
    text: 建立一個新的 Word Document，並建立與之關聯的 DocumentBuilder。
  - name: 插入大小為 432×252 點的直條圖，並取得 Chart 物件以便進一步操作。
    text: 插入大小為 432×252 點的直條圖，並取得 Chart 物件以便進一步操作。
  - name: 定義要移除的資料系列的零基索引（第二個系列）。
    text: 定義要移除的資料系列的零基索引（第二個系列）。
  - name: 如果索引有效，對圖表的 Series 集合呼叫 RemoveAt 以刪除該系列。
    text: 如果索引有效，對圖表的 Series 集合呼叫 RemoveAt 以刪除該系列。
  - name: 將更新後的文件儲存為 .docx 檔案。
    text: 將更新後的文件儲存為 .docx 檔案。
  type: HowTo
- questions:
  - answer: '`if` 檢查 (`targetSeriesIdx < columnChart.Series.Count`) 會失敗，因此不會呼叫 `RemoveAt`，圖表保持不變。'
    question: 如果傳入的索引等於圖表中系列的數量，會發生什麼情況？
  - answer: 會的，在執行 `columnChart.Series.RemoveAt` 後，圖例會重新產生以反映剩餘的系列，因而被移除的項目會從圖例中消失。
    question: 移除系列會自動更新圖例嗎？
  - answer: 此程式碼適用於任何支援 `Series` 集合的圖表類型；只需在插入圖表時將 `ChartType.Column` 改為所需的類型即可。
    question: 我可以使用相同的程式碼刪除折線圖或圓餅圖的系列嗎？
  - answer: 即使圖表沒有任何系列，它仍然是有效的 `Shape`，會被儲存，但在最終文件中會顯示為空白。
    question: 如果我移除圖表中唯一的系列，圖表仍能正確儲存嗎？
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: 在 Word 文件中刪除圖表系列
og_description: 使用 Aspose.Words for .NET 從 Word 圖表中剝除資料系列的逐步指南。
og_image_alt: 說明如何使用 Aspose.Words for .NET 從 Word 文件的直條圖中刪除特定資料系列的指南
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 從 Word 文件中移除圖表系列
本教學示範如何建立 Word 文件、使用 DocumentBuilder 新增直條圖，然後透過 ChartSeriesCollection.RemoveAt 方法刪除該圖表中的特定資料系列。完成後，您將得到一個已儲存且已移除不需要系列的文件，讓您能直接從 .NET 程式碼精確控制圖表內容。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


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

**Q: 如果傳入的索引等於圖表中系列的數量，會發生什麼情況？**  
A: `if` 檢查 (`targetSeriesIdx < columnChart.Series.Count`) 會失敗，因此不會呼叫 `RemoveAt`，圖表保持不變。

**Q: 移除系列會自動更新圖例嗎？**  
A: 會的，在執行 `columnChart.Series.RemoveAt` 後，圖例會重新產生以反映剩餘的系列，因而被移除的項目會從圖例中消失。

**Q: 我可以使用相同的程式碼刪除折線圖或圓餅圖的系列嗎？**  
A: 此程式碼適用於任何支援 `Series` 集合的圖表類型；只需在插入圖表時將 `ChartType.Column` 改為所需的類型即可。

**Q: 如果我移除圖表中唯一的系列，圖表仍能正確儲存嗎？**  
A: 即使圖表沒有任何系列，它仍然是有效的 `Shape`，會被儲存，但在最終文件中會顯示為空白。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}