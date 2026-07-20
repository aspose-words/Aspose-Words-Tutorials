---
category: general
date: 2026-07-19
description: 使用 Aspose.Words for C# 爆炸餅圖切片。學習如何將餅圖切片分離、調整環形圖孔徑大小，以及快速變更圖表資料點。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: zh-hant
lastmod: 2026-07-19
og_description: 使用 Aspose.Words for C# 來分離餅圖切片。本指南示範如何分離餅圖切片、調整環形圖孔洞大小，以及有效變更圖表資料點。
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: 在 C# 中將餅圖切片分離 – Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: 在 C# 中使用 Aspose.Words 爆炸式顯示圓餅圖切片 – 完整指南
url: /zh-hant/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 使用 Aspose.Words 爆炸式餅圖切片 – 完整指南

有沒有想過要在 Word 文件中 **爆炸式餅圖切片**（explode pie chart slice）？不只你有這個需求。無論是製作銷售簡報或視覺化調查結果，將切片拉開都能把目光聚焦在你想要的地方。本教學將一步步說明整個流程——載入文件、取得圖表、爆炸第一個切片、調整甜甜圈孔大小，甚至變更圖表資料點。

我們也會順帶說明你可能在找的次要概念：**如何爆炸餅圖切片**、**調整甜甜圈孔大小**、以及**變更圖表資料點**。沒有冗長說明，直接給你完整、可直接複製貼上的解決方案。

---

## 需要的前置條件

在開始之前，請確保你已具備：

- **Aspose.Words for .NET**（截至 2026‑07‑19 的最新版本）。可使用 `Install-Package Aspose.Words` 從 NuGet 取得。
- **.NET 6+** 專案（若仍使用舊版，則需 .NET Framework 4.7.2+）。
- 一個已包含餅圖或甜甜圈圖的 Word 檔（`Chart.docx`）。若沒有，可在 Word 中快速建立圖表並儲存。

就這些——不需要額外函式庫、也不需要 COM interop，純粹的受管理程式碼。

---

## 爆炸式餅圖切片 – 步驟實作

以下將任務拆解為多個小步驟。每個段落都有清楚的標題、程式碼片段，以及說明 *為什麼* 這樣做。

### 步驟 1：安裝並參考 Aspose.Words

首先，將 Aspose.Words 套件加入專案。在套件管理員主控台執行：

```powershell
Install-Package Aspose.Words
```

> **小技巧：** 若使用 Visual Studio 內建的 NuGet UI，搜尋 “Aspose.Words” 並點選 Install。這樣可確保取得最新的錯誤修正與圖表支援功能。

### 步驟 2：載入包含圖表的 Word 文件

我們需要一個指向含有圖表的 `.docx` 的 `Document` 物件。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **為什麼重要：** `Document` 是 Aspose.Words 所有操作的入口點。提前檢查圖表是否存在，可避免之後在爆炸切片時發生 null 參考例外。

### 步驟 3：取得第一個圖表節點

大多數範例假設只有一個圖表，我們就抓第一個。若有多個圖表，請自行調整索引。

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **備註：** 在確認圖表存在後再進行 `Chart` 型別的轉型是安全的。此物件讓我們可以存取系列、資料點，以及圖表類型專屬的設定。

### 步驟 4：爆炸餅圖的第一個切片

現在重點來了——**如何爆炸餅圖切片**。我們只要設定第一個資料點的 `Exploded` 屬性。

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **為什麼會生效：** `Exploded` 告訴 Word 把該切片從中心拉開，產生經典的「爆炸式餅圖」效果。此屬性為布林值，設為 `true` 即可。

### 步驟 5：調整甜甜圈孔大小（若為甜甜圈圖）

如果圖表是甜甜圈，可能想 **調整甜甜圈孔大小**。孔大小以圖表半徑的百分比表示。

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **數值說明：** `30` 代表內圈佔總半徑的 30 %，外環會相對較厚。

### 步驟 6：變更圖表資料點（可選）

有時需要 **變更圖表資料點**——例如底層數字已更新，想讓視覺即時反映。

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **為什麼要這麼做：** 變更資料點的值會自動重新計算切片比例，讓圖表保持正確，而不必在 Word 中手動編輯。

### 步驟 7：儲存修改後的文件

最後，將變更寫回磁碟。可以覆寫原檔，也可以產生新檔，視需求而定。

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **小提示：** 若需明確指定格式，可使用 `SaveFormat.Docx`，但 `Save(string)` 會自動依副檔名偵測格式。

---

## 預期結果

當你在 Microsoft Word 中開啟 `FormattedChart.docx` 時，應該會看到：

- 餅圖的第一個切片 **向外爆炸**。
- 若圖表為甜甜圈，中心孔現在佔 **30 %** 的半徑。
- 任何已修改的資料點會顯示新設定的數值。

以下是爆炸切片的示意圖（僅供參考）：

![使用 Aspose.Words 於 C# 建立的爆炸式餅圖切片](exploded-pie-slice.png)

*Alt text:* **爆炸式餅圖切片**，顯示在 Word 文件中被拉離中心的區段。

---

## 常見問題與邊緣情況

**如果圖表不是餅圖或甜甜圈呢？**  
程式碼會先檢查 `ChartType`，只有在屬於餅圖或甜甜圈時才套用 `Exploded` 或 `HoleSize`。對於長條圖、折線圖或面積圖，這些屬性根本不存在，程式會安全跳過。

**可以同時爆炸多個切片嗎？**  
當然可以。遍歷 `chart.PieChartData.Series[0].DataPoints`，在任意索引上設定 `Exploded = true` 即可。

**需要擔心文化特定的數字格式嗎？**  
Aspose.Words 以 double 儲存數值，與本機語系無關，無需擔心逗號與句點的差異。

**圖表若嵌入頁首/頁腳怎麼處理？**  
使用 `doc.GetChildNodes(NodeType.Chart, true)` 取得所有圖表，然後檢查每個節點的 `ParentNode` 位置。相同的爆炸邏輯仍然適用。

---

## 結論

現在你已掌握一套完整、可直接複製貼上的 **爆炸餅圖切片** 解決方案，使用 Aspose.Words 於 C# 實作。我們從載入文件、取得圖表、爆炸切片、**調整甜甜圈孔大小**、**變更圖表資料點**，最後儲存檔案，完整說明了一遍。

隨意嘗試：爆炸不同的切片、將孔大小調整至 45 %，或一次更新多筆資料點。Aspose.Words API 讓這些調整變得輕鬆，開啟 Word 檔時即可即時看到變化。

---

### 接下來可以做什麼？

- **樣式化爆炸切片**（變更填色、邊框，或加入資料標籤）。搜尋 “Aspose.Words chart formatting”。
- **批次處理多份文件**——遍歷資料夾、爆炸切片、再儲存新版本。
- **結合 Aspose.Slides**，若需要在 PowerPoint 簡報中使用相同圖表。

對圖表操作還有其他疑問，或想深入了解其他圖表類型？歡迎在下方留言，祝開發順利！

## 接下來該學什麼？

以下教學與本指南緊密相關，能進一步擴展你的技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，助你掌握更多 API 功能，或探索其他實作方式。

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}