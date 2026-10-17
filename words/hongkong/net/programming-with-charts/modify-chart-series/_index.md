---
title: 使用 Aspose.Words for .NET 在 Word 文件中更新 Chart 系列資料。
weight: 610
limit:
description: 學習如何在 Word 文件中修改圖表 series 資料點，並使用 Aspose.Words for .NET 重新整理圖表。
keywords: [Aspose.Words for .NET, modify chart series, update chart data points, Word chart manipulation, C# chart editing, column chart in Word]
url: /net/programming-with-charts/modify-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 學習如何在 Word 文件中修改圖表 series 資料點，並使用 Aspose.Words for .NET 重新整理圖表。
  headline: 使用 Aspose.Words for .NET 在 Word 文件中更新 Chart 系列資料。
  type: TechArticle
- description: 學習如何在 Word 文件中修改圖表 series 資料點，並使用 Aspose.Words for .NET 重新整理圖表。
  name: 使用 Aspose.Words for .NET 在 Word 文件中更新 Chart 系列資料。
  steps:
  - name: 建立一個新的 Document，使用 DocumentBuilder 插入 column chart，並將其儲存為初始檔案。
    text: 建立一個新的 Document，使用 DocumentBuilder 插入 column chart，並將其儲存為初始檔案。
  - name: 開啟已儲存的檔案，定位圖表形狀以取得現有的 Chart 物件。
    text: 開啟已儲存的檔案，定位圖表形狀以取得現有的 Chart 物件。
  - name: 清除第一個 series 的值並加入新資料點，接著透過移除第二個 series 的第一個點並新增一個點來調整該 series。
    text: 清除第一個 series 的值並加入新資料點，接著透過移除第二個 series 的第一個點並新增一個點來調整該 series。
  - name: 將修改後的文件儲存為包含更新圖表的新檔案。
    text: 將修改後的文件儲存為包含更新圖表的新檔案。
  type: HowTo
- questions:
  - answer: 使用 `document.GetChildNodes(NodeType.Shape, true)` 取得所有形狀，然後以 `s.HasChart`
      進行篩選，選取第一個（或您需要的那個）— 這樣可避免選到不相關的圖片或文字方塊。
    question: 如何在可能包含其他形狀的文件中可靠地定位 chart shape？
  - answer: '`ClearValues()` 會移除現有的資料點；若不這樣做，新資料點會被附加到舊的資料點之後，可能導致類別重複或總計不正確。'
    question: 為什麼在為 series 加入新資料點之前需要呼叫 `ClearValues()`？
  - answer: 當圖表的 X 軸類別為文字（例如\"Group A\"）時使用 `FromString`，而當軸需要數值（如日期或測量值）時則使用 `FromDouble`。
    question: 什麼時候應該使用 `ChartXValue.FromString` 而非 `ChartXValue.FromDouble` 來設定 X
      軸的值？
  - answer: 嘗試存取不存在的 series 會拋出 `ArgumentOutOfRangeException`；在引用特定索引前，務必先檢查 `existingChart.Series.Count`。
    question: 如果 chart 只有一個 series，卻嘗試存取 `existingChart.Series[1]`，會發生什麼情況？
  - answer: 儲存 `openedDoc` 已足夠，因為它是包含已修改圖表的文件實例；原始的 `document` 只用於建立初始檔案。
    question: 在修改圖表後，我是否需要重新儲存原始的 `document`，或只儲存 `openedDoc` 就足夠？
  type: FAQPage
images:
- /net/programming-with-charts/modify-chart-series/og-image.png
og_title: 編輯 Word 中的 Chart 系列資料。
og_description: 使用 Aspose.Words for .NET 在 Word 檔案中變更圖表 series 數值的逐步指南。
og_image_alt: 說明使用 Aspose.Words for .NET 前後更新 series 資料的 Word 文件與 column chart 的範例。
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 文件中更新 Chart 系列資料。
本教學說明如何建立包含 column chart 的 Word 文件，然後重新開啟檔案、取得現有圖表系列、修改其資料點，並儲存文件，使圖表顯示新數值。請依照一步一步的程式碼，了解使用 Aspose.Words for .NET 以程式方式調整圖表資料是多麼簡單。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/modify-chart-series" >}}


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

**Q: 如何在可能包含其他形狀的文件中可靠地定位 chart shape？**  
A: 使用 `document.GetChildNodes(NodeType.Shape, true)` 取得所有形狀，然後以 `s.HasChart` 進行篩選，選取第一個（或您需要的那個）— 這樣可避免選到不相關的圖片或文字方塊。

**Q: 為什麼在為 series 加入新資料點之前需要呼叫 `ClearValues()`？**  
A: `ClearValues()` 會移除現有的資料點；若不這樣做，新資料點會被附加到舊的資料點之後，可能導致類別重複或總計不正確。

**Q: 什麼時候應該使用 `ChartXValue.FromString` 而非 `ChartXValue.FromDouble` 來設定 X 軸的值？**  
A: 當圖表的 X 軸類別為文字（例如\"Group A\"）時使用 `FromString`，而當軸需要數值（如日期或測量值）時則使用 `FromDouble`。

**Q: 如果 chart 只有一個 series，卻嘗試存取 `existingChart.Series[1]`，會發生什麼情況？**  
A: 嘗試存取不存在的 series 會拋出 `ArgumentOutOfRangeException`；在引用特定索引前，務必先檢查 `existingChart.Series.Count`。

**Q: 在修改圖表後，我是否需要重新儲存原始的 `document`，或只儲存 `openedDoc` 就足夠？**  
A: 儲存 `openedDoc` 已足夠，因為它是包含已修改圖表的文件實例；原始的 `document` 只用於建立初始檔案。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}