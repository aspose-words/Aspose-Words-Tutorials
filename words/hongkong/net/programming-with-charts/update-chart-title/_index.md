---
title: 使用 Aspose.Words for .NET 在 Word 中更新圖表標題並切換圖例可見性
weight: 810
limit:
description: 學習在 Word 文件中使用 Aspose.Words for .NET 變更圖表標題並控制圖例可見性。
keywords: [Aspose.Words for .NET, update chart title, toggle legend visibility, word chart manipulation, c# chart title, aspose words chart legend]
url: /net/programming-with-charts/update-chart-title/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 學習在 Word 文件中使用 Aspose.Words for .NET 變更圖表標題並控制圖例可見性。
  headline: 使用 Aspose.Words for .NET 在 Word 中更新圖表標題並切換圖例可見性
  type: TechArticle
- description: 學習在 Word 文件中使用 Aspose.Words for .NET 變更圖表標題並控制圖例可見性。
  name: 使用 Aspose.Words for .NET 在 Word 中更新圖表標題並切換圖例可見性
  steps:
  - name: 定義使用者提供的圖表標題以及是否顯示圖例。
    text: 定義使用者提供的圖表標題以及是否顯示圖例。
  - name: 建立一個全新的 Word 文件，並使用 DocumentBuilder 來加入內容。
    text: 建立一個全新的 Word 文件，並使用 DocumentBuilder 來加入內容。
  - name: 在文件中插入一個 432 × 252 pt 的柱形圖，並確認該 Shape 確實包含圖表。
    text: 在文件中插入一個 432 × 252 pt 的柱形圖，並確認該 Shape 確實包含圖表。
  - name: 取得 Chart 物件，將其標題文字設定為使用者提供的值，並確保標題顯示。
    text: 取得 Chart 物件，將其標題文字設定為使用者提供的值，並確保標題顯示。
  - name: 設定圖例：若要求則顯示於右側，否則隱藏，且允許圖例覆蓋繪圖區域。
    text: 設定圖例：若要求則顯示於右側，否則隱藏，且允許圖例覆蓋繪圖區域。
  - name: 將修改後的文件儲存至磁碟，檔名為 CustomChart.docx。
    text: 將修改後的文件儲存至磁碟，檔名為 CustomChart.docx。
  type: HowTo
- questions:
  - answer: 當 `displayLegend` 為 `true` 時，程式會將 `chartLegend.Position` 設為 `LegendPosition.Right`，使圖例顯示在繪圖區域的右側；`Overlay`
      屬性仍為 `true`，因此圖例可以與圖表重疊以節省空間。
    question: 將 `displayLegend` 設為 `true` 會對產生的圖表產生什麼變化？
  - answer: 在設定 `chartTitle.Text` 後，將 `chartTitle.Show = false`（或直接不將 `Show` 設為 `true`），即可使標題不會在
      Word 文件中呈現。
    question: 如果使用者未提供圖表標題，該如何隱藏標題？
  - answer: 是的——`InsertChart` 會回傳一個應包含圖表的 `Shape`，但檢查 `HasChart` 可確保該 Shape 真正持有 `Chart`
      物件；若未通過檢查，程式會拋出 `InvalidOperationException`。
    question: 在呼叫 `InsertChart` 後，是否有必要檢查 `chartContainer.HasChart`？
  - answer: 當然可以；將 `LegendPosition` 列舉中的任意值（例如 `LegendPosition.Top`、`LegendPosition.Bottom`、`LegendPosition.Left`）指定給
      `chartLegend.Position`，即可依需求重新定位圖例。
    question: 我可以將圖例放在右側以外的其他位置嗎？
  type: FAQPage
images:
- /net/programming-with-charts/update-chart-title/og-image.png
og_title: 變更 Word 中的圖表標題與圖例
og_description: 學習在 Word 文件中使用 Aspose.Words for .NET 設定自訂圖表標題並控制圖例顯示。
og_image_alt: 指南：示範使用 Aspose.Words for .NET 更新 Word 文件中圖表標題並切換圖例的程式碼
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 中更新圖表標題並切換圖例可見性
本教學示範如何使用 Aspose.Words for .NET 以程式方式修改 Word 文件中的圖表。您將學會插入柱形圖、以使用者提供的文字取代圖表標題，並根據使用者偏好控制圖例的可見性與覆蓋。透過這些步驟，您可以動態調整圖表呈現，而無需手動編輯。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/update-chart-title" >}}


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

**Q: 將 `displayLegend` 設為 `true` 會對產生的圖表產生什麼變化？**  
A: 當 `displayLegend` 為 `true` 時，程式會將 `chartLegend.Position` 設為 `LegendPosition.Right`，使圖例顯示在繪圖區域的右側；`Overlay` 屬性仍為 `true`，因此圖例可以與圖表重疊以節省空間。

**Q: 如果使用者未提供圖表標題，該如何隱藏標題？**  
A: 在設定 `chartTitle.Text` 後，將 `chartTitle.Show = false`（或直接不將 `Show` 設為 `true`），即可使標題不會在 Word 文件中呈現。

**Q: 在呼叫 `InsertChart` 後，是否有必要檢查 `chartContainer.HasChart`？**  
A: 是的——`InsertChart` 會回傳一個應包含圖表的 `Shape`，但檢查 `HasChart` 可確保該 Shape 真正持有 `Chart` 物件；若未通過檢查，程式會拋出 `InvalidOperationException`。

**Q: 我可以將圖例放在右側以外的其他位置嗎？**  
A: 當然可以；將 `LegendPosition` 列舉中的任意值（例如 `LegendPosition.Top`、`LegendPosition.Bottom`、`LegendPosition.Left`）指定給 `chartLegend.Position`，即可依需求重新定位圖例。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}