---
category: general
date: 2026-10-13
description: Aspose.Words 徑向圖範例，示範如何使用 C# 及 Aspose.Words 24.9+ 在徑向圖上啟用刻度。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: zh-hant
lastmod: 2026-10-13
og_description: Aspose.Words 徑向圖範例，示範如何在徑向圖上啟用刻度，使用 C# 以及最新的 24.9+ 版函式庫。
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Aspose.Words 徑向圖示例 – 在 C# 中啟用刻度
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: Aspose.Words 徑向圖範例：在 C# 中啟用刻度
url: /zh-hant/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words 徑向圖表範例：在 C# 中啟用刻度

如果您正在尋找 **aspose.words 徑向圖表範例**，恭喜您來對地方了。本教學將逐步說明如何使用 Aspose.Words for .NET API 為徑向圖表開啟刻度。

徑向圖表非常適合視覺化週期性資料，例如一天中的時間指標或季節性趨勢。預設情況下，圓形座標軸上的刻度（即刻度標記）是隱藏的，這會讓圖表較難閱讀。啟用它只需要一行程式碼，但您必須了解正確的物件模型以及支援此功能的版本。

在本指南中，您將學會：

* 載入已包含徑向圖表的 Word 文件。  
* 透過 Aspose.Words 圖表 API 取得圖表形狀。  
* 開啟 **刻度可見性**（自 **Aspose.Words 版本 24.9** 起提供）。  
* 儲存已修改的文件並驗證結果。

完整、可執行的程式碼已提供，您只需將其貼到新的 Console 專案，即可立即看到效果。

![Aspose.Words 徑向圖表範例（已啟用刻度）](https://example.com/images/radial-chart-graduations.png "Aspose.Words 徑向圖表範例顯示已啟用刻度")

## 前置條件

在開始之前，請確保您具備以下條件：

| 需求 | 重要原因 |
|-------------|----------------|
| .NET 6.0 或更新版本 | Aspose.Words for .NET 24.9+ 以 .NET Standard 2.0 為目標，亦可在 .NET 6+ 上執行。 |
| Aspose.Words for .NET **24.9** 或更新版本 | `IsGraduationsVisible` 屬性於 24.9 版首次加入。較舊版本會拋出 `MissingMemberException`。 |
| 包含徑向圖表的 Word 文件（`RadialChart.docx`） | 本範例操作既有圖表；若要從頭建立圖表屬於另一主題。 |
| C# IDE（Visual Studio、Rider、VS Code） | 任何能編譯 .NET 專案的 IDE 都可使用。 |
| NuGet 套件 `Aspose.Words` | 透過 `dotnet add package Aspose.Words --version 24.9.0`（或更新版本）安裝。 |

> **專業提示：** 若無法升級至 24.9，仍可修改其他圖表屬性，但刻度將保持隱藏，因為 API 尚未公開此旗標。

## Aspose.Words 徑向圖表範例 – 步驟說明

以下各節將整個流程拆解為易於跟隨的步驟。每一步皆提供所需的完整程式碼與簡短說明，說明 *為何* 需要此步驟。

### 步驟 1：載入包含徑向圖表的文件

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**為何重要：**  
`Document` 是 **Aspose.Words 圖表 API** 的入口點。它會將 DOCX 檔載入記憶體，讓您能存取所有節點——段落、表格與圖表形狀。若檔案找不到，`Document` 會拋出 `FileNotFoundException`，此例外應在正式環境中加以處理。

### 步驟 2：從文件中取得第一個圖表形狀

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**為何重要：**  
圖表以 `Shape` 節點儲存。使用 `GetChild` 搭配 `NodeType.Shape` 可遍歷 DOM，回傳第一個符合條件的形狀。將其轉型為 `Chart` 後，即可存取圖表專屬屬性，例如 `RadialChart`。此處的 null 檢查可在文件未包含圖表時提供明確錯誤訊息，這是重複使用範本時常見的邊緣情況。

### 步驟 3：在徑向圖表上啟用刻度

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**為何重要：**  
`IsGraduationsVisible` 控制圓形座標軸周圍的刻度標記。設為 `true` 後，圖表會顯示刻度，提升需要精確讀取數值的使用者的可讀性。此屬性位於 `RadialChart`，而 `RadialChart` 是 `Chart` 的子類型。若在非徑向圖表（例如長條圖）上使用，`RadialChart` 會是 `null`，因此在較複雜的情境下應先驗證圖表類型。

#### 處理非徑向圖表（可選）

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

此防護程式碼可在來源文件可能包含其他圖表類型時，提高程式的健全性。

### 步驟 4：儲存已修改的文件

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**為何重要：**  
呼叫 `Save` 會將記憶體中的 DOM 寫回 .docx 檔，將您對圖表所做的變更永久保存。輸出檔可於 Microsoft Word、LibreOffice 或任何支援 DOCX 的檢視器開啟，您將看到徑向圖表已顯示刻度。

## 完整、可執行的範例

以下程式碼可直接貼入 .NET Console 專案的 `Program.cs` 中。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### 預期結果

當您在 Word 中開啟 `RadialChart_Graduations.docx` 時，徑向圖表會在圓形座標軸上顯示刻度標記，與前述螢幕截圖相同。圖表的其他部分（資料系列、圖例、標題）則保持不變。

## 常見變形與邊緣案例

| 情況 | 解決方案 |
|-----------|----------|
| **舊版 Aspose.Words (< 24.9)** | 升級至最新的 NuGet 套件。`IsGraduationsVisible` 屬性在較早版本中不存在。 |
| **同一文件中有多個圖表** | 使用 `doc.GetChild(NodeType.Shape, index, true)` 並指定正確的 `index`，或遍歷 `doc.GetChildNodes(NodeType.Shape, true)` 並以 `ChartType.Radial` 進行篩選。 |
| **程式化建立圖表** | 使用 `DocumentBuilder` 插入圖表，然後在取得的 `RadialChart` 上設定 `IsGraduationsVisible`。 |

## 接下來您可以學習什麼？

以下教學與本指南緊密相關，能進一步深化您對 API 的運用，並提供可直接套用於專案的完整程式碼範例與步驟說明。

- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Remove a Chart Series from a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/remove-chart-series/)
- [Hide Plot Area Border in a Column Chart with Aspose.Words for .NET](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}