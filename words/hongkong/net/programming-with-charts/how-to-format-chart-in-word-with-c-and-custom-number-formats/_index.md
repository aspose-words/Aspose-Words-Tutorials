---
category: general
date: 2026-10-13
description: 如何使用 C# 在 Word 中格式化圖表，將自訂數字格式（例如貨幣）套用至圖表軸。附有逐步程式碼範例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: zh-hant
lastmod: 2026-10-13
og_description: 如何使用 C# 在 Word 中格式化圖表，可讓您為圖表軸套用自訂數字格式，確保數值以貨幣、百分比或任何您需要的模式顯示。請跟隨逐步指南。
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: 如何使用 C# 在 Word 中格式化圖表 – 自訂數字格式
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: 如何使用 C# 及自訂數字格式在 Word 中格式化圖表
url: /zh-hant/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 C# 及自訂數字格式在 Word 中格式化圖表

在需要專業呈現資料時，使用 C# 於 Word 中格式化圖表是一項常見需求。本指南將示範如何使用 **Aspose.Words for .NET** 為圖表的坐標軸套用自訂數字格式，讓數值顯示如您所預期。

您將學會如何載入 DOCX 檔案、定位第一個圖表、讀取目前的格式，然後設定如貨幣（兩位小數）的新模式。教學亦涵蓋如何為其他系列變更圖表坐標軸格式，以及在需要時如何重設格式。

## 前置條件

在開始之前，請確保您已具備：

* 已安裝 .NET 6.0 或更新版本  
* 使用 Visual Studio 2022（或任何支援 .NET 的 IDE）建立的專案  
* **Aspose.Words for .NET** NuGet 套件 (`Aspose.Words`)  
* 含有至少一個圖表的 Word 文件 (`input.docx`)

您可以使用以下指令加入套件：

```bash
dotnet add package Aspose.Words
```

## 使用 Aspose.Words 在 Word 中格式化圖表

以下完整程式示範了 **格式化圖表** 坐標軸值所需的每一步。將檔案另存為 `Program.cs`，然後從命令列或 IDE 執行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### 各步驟說明

| 步驟 | 為何重要 | 關鍵程式碼 |
|------|----------|----------|
| **載入文件** | 您需要一個 `Document` 物件來操作 Word 檔案。 | `new Document("input.docx")` |
| **取得圖表** | `Chart` 物件以 `Shape` 節點儲存；轉型後即可使用圖表專屬 API。 | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **存取 X 值** | 坐標軸格式化套用於資料系列的值集合。 | `chart.ChartData.Series[0].XValues` |
| **讀取目前格式** | 瞭解現有的 `FormatCode` 可協助決定是取代或補充。 | `xValues.FormatCode` |
| **設定自訂格式** | `FormatCode` 屬性接受任何 Excel 相容的模式，可實現貨幣、百分比、日期等。 | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **儲存文件** | 將變更寫回 DOCX 檔案，即可持久化新的坐標軸格式。 | `doc.Save("output_formatted.docx")` |

執行程式後會產生 `output_formatted.docx`。在 Word 中開啟後，您會看到圖表的 X 軸值顯示為 **$1,234.00**、**$2,345.00** …，而非純數字。

## 為圖表坐標軸套用自訂數字格式

如果您需要將 **自訂數字格式** 套用至 Y 軸或其他系列，流程完全相同——只要針對不同的集合即可：

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **Pro tip:** 使用雙引號包住格式字串以嵌入文字字元（例如 `"$"` 代表貨幣）。如上例所示，需對引號進行跳脫。

## 自訂數字格式 – 處理 Word 的語系設定

Word 會依文件的語系解讀數字格式。若文件使用非美國語系，您可能需要調整格式字串：

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

在使用德語語系設定的文件上測試此格式，可確認數值顯示為 **€ 1.234,00**。

## 以程式方式設定圖表屬性

除了坐標軸格式化外，您常會想 **設定圖表** 標題、圖例或資料標籤。以下程式片段示範在完成坐標軸格式化後，如何設定圖表標題：

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

將此片段與自訂數字格式結合，即可得到一張完整、精緻的圖表，隨時可用於報表。

## 根據使用者輸入動態變更圖表坐標軸格式

在實務應用中，您可能會讓使用者在執行時選擇格式。以下方法將格式化邏輯封裝起來：

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

您可以呼叫 `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` 以設定貨幣格式，或 `SetAxisFormat(chart, 0, "0%")` 以設定百分比。此做法讓主程式保持簡潔，亦方便未來擴充。

## 邊緣情況與常見陷阱

| 情況 | 需要注意的點 | 建議修正 |
|-----------|-------------------|---------------|
| 文件中 **沒有圖表** | `GetChild` 會回傳 `null`，導致轉型例外。 | 在轉型前先檢查是否為 `null`（參考範例）。 |
| 同一文件內有多個圖表 | 程式碼始終取得第一個圖表（`index 0`）。 | 迭代 `doc.GetChildNodes(NodeType.Shape, true)` 並以 `ShapeType.Chart` 篩選。 |
| 系列 **沒有 X 值**（例如圓餅圖） | 存取 `XValues` 可能拋出 `ArgumentOutOfRangeException`。 | 在格式化前確認 `Series[i].XValues` 非空。 |
| 語系不匹配 | 貨幣符號可能顯示不正確。 | 明確以適當的語系符號設定 `xValues.FormatCode`。 |

## 預期輸出

執行範例程式後，開啟 **output_formatted.docx**。圖表的 X 軸應以所選的自訂格式顯示數字。以貨幣範例為例，坐標軸標籤會是：

```
$1,000.00
$2,000.00
$3,000.00
```

若您將 Y 軸值套用百分比格式，Y 軸標籤則會顯示為：

```
10%
20%
30%
```

## 結論

本教學示範了如何透過 **套用自訂數字格式** 於坐標軸值，使用 C# 在 Word 中 **格式化圖表**。您現在擁有可重複使用的模式，能設定貨幣、百分比或任何其他數字樣式，同時也了解了語系、 多系列與動態使用者輸入的處理方式。

接下來，您可以探索 **設定圖表** 標題、資料標籤，甚至使用 `ChartRenderer` 將圖表匯出為影像。這些主題直接延伸自本教學的概念，將協助您打造全自動化的報表解決方案。

---


## 接下來該學什麼？

以下教學涵蓋與本指南技術緊密相關的主題，並在此基礎上進一步延伸。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [圖表坐標軸的數字格式](/words/english/net/programming-with-charts/number-format-for-axis/)
- [圖表資料標籤的數字格式](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [使用 Aspose.Words for .NET 在 Word 折線圖中格式化次要 X 軸並將顯示單位設定為千](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}