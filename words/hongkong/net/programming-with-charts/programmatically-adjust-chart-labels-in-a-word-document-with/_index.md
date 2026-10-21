---
category: general
date: 2026-10-13
description: 學習如何以 C# 程式方式調整 Word 文件中的圖表標籤。本指南涵蓋 Aspose.Words 圖表操作與標籤對齊。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: zh-hant
lastmod: 2026-10-13
og_description: 使用 C# 程式化調整 Word 文件中的圖表標籤。請參考本完整教學，以變更標籤位置、對齊方式等。
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: 以程式方式調整 Word 中的圖表標籤 – C# 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: 使用 C# 程式化調整 Word 文件中的圖表標籤
url: /zh-hant/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 C# 程式化調整 Word 文件中的圖表標籤

如果您需要 **程式化調整圖表標籤**，本教學將示範如何使用 C# 完成此操作。無論是產生報表、自動化儀表板，或是自訂範本，您都會看到一個完整、可執行的範例，說明如何變更 .docx 檔案中圖表的標籤位置與對齊方式。

您還會學到 **Aspose.Words 圖表操作** 的技巧、如何處理多個系列，以及在使用 **C# 圖表資料標籤** 物件時常見的陷阱。

## 前置條件

開始之前，請確保您已具備：

* .NET 6.0（或更新版本）已安裝  
* Visual Studio 2022（或任何 C# IDE）  
* **Aspose.Words for .NET** NuGet 套件（`Install-Package Aspose.Words`）  
* 一個包含至少一個圖表的 Word 文件（`input.docx`）  

以上項目是我們將要修改的 **Word 文件圖表範例** 所必需的。

## 步驟 1：建立專案並匯入命名空間

建立一個新的 Console 專案，並加入必要的 `using` 指令。這樣即可為 **程式化調整圖表標籤** 做好環境準備。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*為什麼要這樣做？*  
載入文件後，您即可存取內部的 **Word 文件圖表範例** 樹狀結構，圖表以 shape 節點的形式儲存。

## 步驟 2：定位第一個圖表 Shape

圖表以 `Shape` 節點儲存。以下程式碼會取得文件中的第一個圖表，作為我們調整標籤的目標。

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*為什麼要這樣做？*  
`GetChild` 方法會遞迴搜尋（`true`），並回傳第一個 `Shape` 類型的節點。將其轉型為 `Chart` 後，即可使用圖表專屬的 API。

## 步驟 3：取得要修改的資料標籤

圖表中的每個系列都有一個資料標籤集合。對於簡單的圖表，第一個標籤通常已足夠。以下程式碼示範如何取得它。

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*為什麼要這樣做？*  
`ChartSeries` 代表一組資料點。`DataLabelCollection` 保存該系列的標籤，讓您能精確控制其位置與對齊方式。

## 步驟 4：變更標籤的放置與對齊

現在，我們透過設定位置、水平對齊與垂直對齊，**程式化調整圖表標籤**。這些屬性對應於 Word 使用者介面中的選項。

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*為什麼要這樣設定？*  

* `OutsideEnd` 會把標籤放在每根長條或柱狀的末端外側，提升可讀性。  
* `HorizontalAlignment.Center` 讓文字在點上水平置中，而 `VerticalAlignment.Top` 則把標籤的上緣與資料點對齊，避免與其他元素重疊。

### 小技巧
如果圖表有多個系列，請遍歷 `chart.Series`，對每個 `DataLabelCollection` 套用相同設定。這樣可確保整個圖表外觀一致。

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## 步驟 5：儲存已修改的文件

完成標籤調整後，將變更寫入新檔案。這樣即可完成 **修改圖表標籤位置** 的流程。

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

當您開啟 `output.docx` 時，會看到所有圖表標籤已移至資料點的外側端點，水平置中且垂直對齊於頂部。

## 邊緣情況與變化

| 情境 | 需要注意的地方 | 推薦做法 |
|-----------|-------------------|----------------------|
| **同一文件中有多個圖表** | `GetChild` 只會回傳第一個圖表。 | 使用 `doc.GetChildNodes(NodeType.Shape, true)` 迭代所有圖表 Shape。 |
| **系列沒有資料標籤** | `DataLabelCollection` 可能為空。 | 在存取集合前先檢查 `series.HasDataLabels`。 |
| **不同圖表類型**（圓餅圖、折線圖、散佈圖） | 並非所有 `DataLabelPosition` 值皆適用。 | 對於需要自動決定最佳放置的圖表，使用 `DataLabelPosition.Auto`。 |
| **本地化** | 對齊常數與語言無關，但呈現的文字可能需要右至左支援。 | 若需 RTL 語言，設定 `dataLabel.TextDirection`。 |

## 完整可執行範例

以下是完整程式碼，您可以直接複製、貼上並執行。請將 `YOUR_DIRECTORY` 替換為實際的資料夾路徑。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**預期結果：** 開啟 `output.docx` 後，每個圖表標籤皆會位於資料點外側，水平置中，垂直對齊於頂部——正是您透過 **程式化調整圖表標籤** 所實作的效果。

## 結論

現在您已掌握如何使用 C# **程式化調整 Word 文件中的圖表標籤**。本教學涵蓋：

* 使用 **Aspose.Words 圖表操作** 載入文件  
* 取得 **C# 圖表資料標籤**  
* 變更 **修改圖表標籤位置** 與對齊方式  
* 儲存檔案並處理常見的邊緣情況  

接下來，您可以探索更進階的情境，例如自訂標籤字型、加入條件格式，或一次批次更新多個圖表。試著玩玩不同的 `DataLabelPosition` 選項，找出最適合您報表風格的樣式。

---

*準備好提升自動化報表流程了嗎？試著為標籤加入自訂數字格式，或將圖表匯出為影像以用於 PDF。*


## 接下來該學什麼？

以下教學與本指南緊密相關，能在此基礎上延伸更多技巧。每篇資源皆提供完整可執行的程式碼範例與逐步說明，助您精通其他 API 功能，並在專案中探索替代實作方式。

- [Set Uniform Data Labels in a Column Chart Using Aspose.Words for .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}