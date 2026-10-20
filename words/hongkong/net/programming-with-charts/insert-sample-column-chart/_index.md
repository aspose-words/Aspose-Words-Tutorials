---
title: 使用 Aspose.Words for .NET 在 Word 文件中插入範例直條圖
weight: 410
limit:
description: 一步一步的指南，說明如何建立 Word 檔案、使用 DocumentBuilder.InsertChart 插入預設直條圖、存取圖表物件，並儲存為 .docx。
keywords: [Aspose.Words for .NET, insert column chart, documentbuilder inserchart, create word document with chart, save chart to docx, chart object Aspose.Words]
url: /net/programming-with-charts/insert-sample-column-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 一步一步的指南，說明如何建立 Word 檔案、使用 DocumentBuilder.InsertChart 插入預設直條圖、存取圖表物件，並儲存為
    .docx。
  headline: 使用 Aspose.Words for .NET 在 Word 文件中插入範例直條圖
  type: TechArticle
- description: 一步一步的指南，說明如何建立 Word 檔案、使用 DocumentBuilder.InsertChart 插入預設直條圖、存取圖表物件，並儲存為
    .docx。
  name: 使用 Aspose.Words for .NET 在 Word 文件中插入範例直條圖
  steps:
  - name: 建立一個空白的 Word 文件，並使用 DocumentBuilder 進行編輯。
    text: 建立一個空白的 Word 文件，並使用 DocumentBuilder 進行編輯。
  - name: 在文件中插入尺寸為 432 × 252 點的直條圖。
    text: 在文件中插入尺寸為 432 × 252 點的直條圖。
  - name: 從已插入的圖形中取得 Chart 物件，以便在需要時進一步自訂。
    text: 從已插入的圖形中取得 Chart 物件，以便在需要時進一步自訂。
  - name: 將已包含插入直條圖的文件儲存為 .docx 檔案。
    text: 將已包含插入直條圖的文件儲存為 .docx 檔案。
  type: HowTo
- questions:
  - answer: 尺寸以點 (point) 為單位（1 點 = 1/72 吋），因此 432 pt 約等於 6 吋，252 pt 約等於 3.5 吋。
    question: InsertChart 中的寬度與高度參數（432、252）使用什麼單位？
  - answer: 可以——插入後可透過 `chartContainer.Chart` 取得 Chart 物件；您可以修改其 SeriesCollection、Categories
      以及 Values，以取代範例資料。
    question: 在使用預設資料集呼叫 InsertChart 後，我可以更改圖表資料嗎？
  - answer: 只需在 `InsertChart` 呼叫中將 `ChartType.Column` 替換為其他列舉值，例如 `ChartType.Line`。
    question: 是否可以使用相同程式碼插入不同類型的圖表（例如折線圖）？
  - answer: 不需要——`docBuilder.InsertChart` 會自動將圖表嵌入 `Shape` 中；呼叫 `wordDoc.Save` 即會將圖表與文件一起寫入。
    question: 在儲存文件之前，我需要呼叫其他方法來嵌入圖表嗎？
  type: FAQPage
images:
- /net/programming-with-charts/insert-sample-column-chart/og-image.png
og_title: 在 Word 文件中插入範例直條圖
og_description: 使用 Aspose.Words for .NET 在數分鐘內將現成的直條圖加入 Word 文件。
og_image_alt: 螢幕截圖顯示使用 Aspose.Words for .NET 插入範例直條圖的 Word 文件
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 文件中插入範例直條圖
本教學逐步說明如何建立新的 Word 文件，並使用 DocumentBuilder.InsertChart 插入預設直條圖。您還會了解如何取得嵌入的 Chart 物件以進行進一步操作。最後，說明如何將文件儲存為 .docx 檔案。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-sample-column-chart" >}}


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

**Q: InsertChart 中的寬度與高度參數（432、252）使用什麼單位？**  
A: 尺寸以點 (point) 為單位（1 點 = 1/72 吋），因此 432 pt 約等於 6 吋，252 pt 約等於 3.5 吋。

**Q: 在使用預設資料集呼叫 InsertChart 後，我可以更改圖表資料嗎？**  
A: 可以——插入後可透過 `chartContainer.Chart` 取得 Chart 物件；您可以修改其 SeriesCollection、Categories 以及 Values，以取代範例資料。

**Q: 是否可以使用相同程式碼插入不同類型的圖表（例如折線圖）？**  
A: 只需在 `InsertChart` 呼叫中將 `ChartType.Column` 替換為其他列舉值，例如 `ChartType.Line`。

**Q: 在儲存文件之前，我需要呼叫其他方法來嵌入圖表嗎？**  
A: 不需要——`docBuilder.InsertChart` 會自動將圖表嵌入 `Shape` 中；呼叫 `wordDoc.Save` 即會將圖表與文件一起寫入。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}