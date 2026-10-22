---
title: 使用 Aspose.Words for .NET 自訂直條圖的 X 軸格線
weight: 610
limit:
description: 學習如何在 Word 直條圖中加入並自訂主要 X 軸格線的顏色，使用 Aspose.Words for .NET。
keywords: [Aspose.Words for .NET, column chart, customize x axis gridlines, word chart gridlines, primary x axis gridlines, chart formatting .NET]
url: /net/programming-with-charts/customize-x-axis-gridlines/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 學習如何在 Word 直條圖中加入並自訂主要 X 軸格線的顏色，使用 Aspose.Words for .NET。
  headline: 使用 Aspose.Words for .NET 自訂直條圖的 X 軸格線
  type: TechArticle
- description: 學習如何在 Word 直條圖中加入並自訂主要 X 軸格線的顏色，使用 Aspose.Words for .NET。
  name: 使用 Aspose.Words for .NET 自訂直條圖的 X 軸格線
  steps:
  - name: 建立一個新的 Word 文件，並使用 DocumentBuilder 進行編輯。
    text: 建立一個新的 Word 文件，並使用 DocumentBuilder 進行編輯。
  - name: 在文件中插入一個 432×252 的直條圖，並取得其 Chart 物件。
    text: 在文件中插入一個 432×252 的直條圖，並取得其 Chart 物件。
  - name: 移除預設資料系列，並新增一個包含三個群組與數值的自訂系列。
    text: 移除預設資料系列，並新增一個包含三個群組與數值的自訂系列。
  - name: 取得圖表主要水平（X）軸的參考。
    text: 取得圖表主要水平（X）軸的參考。
  - name: 啟用主要 X 軸的格線顯示。
    text: 啟用主要 X 軸的格線顯示。
  - name: 將格線顏色設為藍色，粗細設定為 2 點。
    text: 將格線顏色設為藍色，粗細設定為 2 點。
  - name: 將文件儲存為 .docx 檔案。
    text: 將文件儲存為 .docx 檔案。
  type: HowTo
- questions:
  - answer: 將相同軸屬性設為 false：`horizontalAxis.HasMajorGridlines = false;` 可切換 X 軸主要格線的可見性。
    question: 啟用格線後，如何再次隱藏主要格線？
  - answer: 不會，`Format.Stroke` 設定僅套用於您所修改的軸；若要設定 Y 軸格線，必須分別調整 `chart.AxisY.Format.Stroke`。
    question: 變更 `horizontalAxis.Format.Stroke.Color` 會同時影響 Y 軸格線嗎？
  - answer: 使用 `horizontalAxis.Format.Stroke.Weight`，並指定雙精度數值（例如 `0.5`）即可讓格線變細。
    question: 哪個屬性控制 X 軸主要格線的粗細？
  - answer: 可以，將 `horizontalAxis.Format.Stroke.DashStyle` 設為 `DashStyle` 列舉值，例如 `DashStyle.Dash`
      或 `DashStyle.Dot`。
    question: 我可以變更 X 軸主要格線的虛線樣式嗎？
  type: FAQPage
images:
- /net/programming-with-charts/customize-x-axis-gridlines/og-image.png
og_title: 設定 Word 直條圖 X 軸格線樣式
og_description: 使用 Aspose.Words for .NET 開啟並自訂 Word 圖表主要 X 軸格線的顏色。
og_image_alt: 本指南示範使用 Aspose.Words for .NET 的 Word 文件與直條圖，將主要 X 軸格線以自訂顏色突顯。
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 自訂直條圖的 X 軸格線
在本教學中，您將學習如何建立 Word 文件、插入直條圖、取代其預設資料，然後啟用主要 X 軸的格線。您還會看到如何將格線的線條顏色更改為符合設計風格。依循一步一步的程式碼，即可精確控制 X 軸格線的可見性與樣式。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/customize-x-axis-gridlines" >}}


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

**Q: 啟用格線後，如何再次隱藏主要格線？**  
A: 將相同軸屬性設為 false：`horizontalAxis.HasMajorGridlines = false;` 可切換 X 軸主要格線的可見性。

**Q: 變更 `horizontalAxis.Format.Stroke.Color` 會同時影響 Y 軸格線嗎？**  
A: 不會，`Format.Stroke` 設定僅套用於您所修改的軸；若要設定 Y 軸格線，必須分別調整 `chart.AxisY.Format.Stroke`。

**Q: 哪個屬性控制 X 軸主要格線的粗細？**  
A: 使用 `horizontalAxis.Format.Stroke.Weight`，並指定雙精度數值（例如 `0.5`）即可讓格線變細。

**Q: 我可以變更 X 軸主要格線的虛線樣式嗎？**  
A: 可以，將 `horizontalAxis.Format.Stroke.DashStyle` 設為 `DashStyle` 列舉值，例如 `DashStyle.Dash` 或 `DashStyle.Dot`。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}