---
title: 使用 Aspose.Words for .NET 隱藏直條圖的繪圖區邊框
weight: 410
limit:
description: 學習如何在 Word 直條圖中使用 Aspose.Words for .NET 隱藏圖表的繪圖區邊框，同時保留座標軸線可見。
keywords: [aspose.words for .net, hide plot border, column chart, chart formatting, word document chart, plot area border removal]
url: /net/programming-with-charts/hide-plot-border/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 學習如何在 Word 直條圖中使用 Aspose.Words for .NET 隱藏圖表的繪圖區邊框，同時保留座標軸線可見。
  headline: 使用 Aspose.Words for .NET 隱藏直條圖的繪圖區邊框
  type: TechArticle
- description: 學習如何在 Word 直條圖中使用 Aspose.Words for .NET 隱藏圖表的繪圖區邊框，同時保留座標軸線可見。
  name: 使用 Aspose.Words for .NET 隱藏直條圖的繪圖區邊框
  steps:
  - name: 建立一個新的空白 Word 文件，並使用 DocumentBuilder 進行編輯。
    text: 建立一個新的空白 Word 文件，並使用 DocumentBuilder 進行編輯。
  - name: 在文件中插入一個 432×252 的直條圖，並取得其 Chart 物件。
    text: 在文件中插入一個 432×252 的直條圖，並取得其 Chart 物件。
  - name: 清除任何現有的系列，定義三個類別標籤，並向圖表加入一個包含範例值的系列。
    text: 清除任何現有的系列，定義三個類別標籤，並向圖表加入一個包含範例值的系列。
  - name: 將繪圖區的筆劃粗細設定為 0，移除其邊框，同時保留座標軸線可見。
    text: 將繪圖區的筆劃粗細設定為 0，移除其邊框，同時保留座標軸線可見。
  - name: 將修改後的文件儲存為 .docx 檔案。
    text: 將修改後的文件儲存為 .docx 檔案。
  type: HowTo
- questions:
  - answer: '`Stroke` 屬性屬於 `Chart` 物件的整體格式，用於繪製繪圖區四周的矩形邊框；座標軸線是獨立的 `Axis` 物件，不會受到圖表
      `Stroke` 設定的影響。'
    question: 為什麼將 `columnChart.Format.Stroke.Weight = 0` 設定為 0 會移除繪圖區邊框卻仍保留座標軸線可見？
  - answer: 不能，`Stroke` 屬性控制整個繪圖區的邊框作為單一矩形，因此無法透過 Aspose.Words 隱藏部分邊框；若需此效果，必須覆蓋自訂形狀或手動編輯圖表。
    question: 我可以只隱藏繪圖區邊框的一側（例如左側），而保留其他三側嗎？
  - answer: 會的，`Stroke` 屬性與 `ChartType` 無關，將其 `Weight` 設為 0 會移除折線圖、圓餅圖或任何其他支援圖表類型的繪圖區邊框。
    question: 如果我將圖表類型改為折線圖或圓餅圖，`columnChart.Format.Stroke.Weight = 0` 仍會隱藏繪圖區邊框嗎？
  - answer: 不需要額外刷新；清除系列並加入新系列會在內部更新圖表，`wordDoc.Save(...)` 會將目前狀態寫入 .docx 檔案。
    question: 在呼叫 `columnChart.Series.Clear()` 後，我需要在儲存文件前刷新圖表嗎？
  type: FAQPage
images:
- /net/programming-with-charts/hide-plot-border/og-image.png
og_title: 在 Word 直條圖中隱藏繪圖區邊框
og_description: 使用 Aspose.Words for .NET 在 Word 直條圖中移除繪圖區邊框，同時保留座標軸線可見。
og_image_alt: 本指南展示一個包含直條圖的 Word 文件，該圖的繪圖區邊框已隱藏，但座標軸線仍保持可見，使用 Aspose.Words for .NET。
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 隱藏直條圖的繪圖區邊框
在本教學中，您將學習如何產生 Word 文件、插入直條圖、以範例資料填充，然後隱藏圖表的繪圖區邊框同時保留座標軸線可見。逐步示範的程式碼展示每個操作，最後儲存文件，讓您立即看到結果。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/hide-plot-border" >}}


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

**Q: 為什麼將 `columnChart.Format.Stroke.Weight = 0` 設定為 0 會移除繪圖區邊框卻仍保留座標軸線可見？**  
A: `Stroke` 屬性屬於 `Chart` 物件的整體格式，用於繪製繪圖區四周的矩形邊框；座標軸線是獨立的 `Axis` 物件，不會受到圖表 `Stroke` 設定的影響。

**Q: 我可以只隱藏繪圖區邊框的一側（例如左側），而保留其他三側嗎？**  
A: 不能，`Stroke` 屬性控制整個繪圖區的邊框作為單一矩形，因此無法透過 Aspose.Words 隱藏部分邊框；若需此效果，必須覆蓋自訂形狀或手動編輯圖表。

**Q: 如果我將圖表類型改為折線圖或圓餅圖，`columnChart.Format.Stroke.Weight = 0` 仍會隱藏繪圖區邊框嗎？**  
A: 會的，`Stroke` 屬性與 `ChartType` 無關，將其 `Weight` 設為 0 會移除折線圖、圓餅圖或任何其他支援圖表類型的繪圖區邊框。

**Q: 在呼叫 `columnChart.Series.Clear()` 後，我需要在儲存文件前刷新圖表嗎？**  
A: 不需要額外刷新；清除系列並加入新系列會在內部更新圖表，`wordDoc.Save(...)` 會將目前狀態寫入 .docx 檔案。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}