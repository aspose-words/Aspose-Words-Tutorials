---
"description": "透過本全面的逐步指南了解如何使用 Aspose.Words for .NET 將日期和時間值新增至圖表的軸。"
"linktitle": "將日期時間值加到圖表的軸上"
"second_title": "Aspose.Words文件處理API"
"title": "將日期時間值加到圖表的軸上"
"url": "/zh-hant/net/programming-with-charts/date-time-values-to-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 將日期時間值加到圖表的軸上

## 介紹

在文件中建立圖表是實現資料視覺化的有效方法。處理時間序列資料時，將日期和時間值新增至圖表的軸上對於清晰度至關重要。在本教學中，我們將引導您完成使用 Aspose.Words for .NET 在圖表軸上新增日期和時間值的過程。本逐步指南將幫助您設定環境、編寫程式碼並了解流程的每個部分。讓我們開始吧！

## 先決條件

在開始之前，請確保您已滿足以下先決條件：

1. Visual Studio 或任何 .NET IDE：您需要一個開發環境來編寫和執行您的 .NET 程式碼。
2. Aspose.Words for .NET：您應該安裝 Aspose.Words for .NET 程式庫。您可以從下載 [這裡](https://releases。aspose.com/words/net/).
3. C# 基礎知識：本教學假設您對 C# 程式設計有基本的了解。
4. 有效的 Aspose 許可證：您可以從 [這裡](https://purchase。aspose.com/temporary-license/).

## 導入命名空間

首先，請確保您已在專案中匯入必要的命名空間。此步驟對於存取 Aspose.Words 類別和方法至關重要。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## 步驟 1：設定文檔目錄

首先，您需要定義儲存文件的目錄。這對於組織您的文件和確保您的程式碼正確運行非常重要。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 步驟 2：建立新文件和 DocumentBuilder

接下來，建立一個新的實例 `Document` 類別和一個 `DocumentBuilder` 目的。這些物件將幫助您建立和操作您的文件。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 步驟 3：將圖表插入文檔

現在，使用 `DocumentBuilder` 目的。在這個例子中，我們使用了長條圖，但您也可以選擇其他類型。

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## 步驟 4：清除現有系列

清除圖表中所有現有系列，以確保您從一張白紙開始。此步驟對於自訂資料至關重要。

```csharp
chart.Series.Clear();
```

## 步驟 5：為系列新增日期和時間值

將日期和時間值加入圖表系列。此步驟涉及建立日期和相應值的陣列。

```csharp
chart.Series.Add("Aspose Series 1",
    new[]
    {
        new DateTime(2017, 11, 06), new DateTime(2017, 11, 09), new DateTime(2017, 11, 15),
        new DateTime(2017, 11, 21), new DateTime(2017, 11, 25), new DateTime(2017, 11, 29)
    },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2, 5.3 });
```

## 步驟 6：配置 X 軸

設定 X 軸的縮放比例和刻度標記。這可確保您的日期以適當的間隔正確顯示。

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.Scaling.Minimum = new AxisBound(new DateTime(2017, 11, 05).ToOADate());
xAxis.Scaling.Maximum = new AxisBound(new DateTime(2017, 12, 03).ToOADate());
xAxis.MajorUnit = 7;
xAxis.MinorUnit = 1;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
```

## 步驟 7：儲存文檔

最後，將您的文件儲存到指定目錄。此步驟結束了整個過程，現在您的文件應該包含一個 X 軸上有日期和時間值的圖表。

```csharp
doc.Save(dataDir + "WorkingWithCharts.DateTimeValuesToAxis.docx");
```

## 結論

使用 Aspose.Words for .NET 在文件中圖表的軸上新增日期和時間值是一個簡單的過程。透過遵循本教程中概述的步驟，您可以建立清晰且資訊豐富的圖表，有效地視覺化時間序列資料。無論您準備的是報告、簡報或任何需要詳細資料表示的文檔，Aspose.Words 都能為您提供成功所需的工具。

## 常見問題解答

### 我可以將其他圖表類型與 Aspose.Words for .NET 一起使用嗎？

是的，Aspose.Words 支援各種圖表類型，包括折線圖、長條圖、圓餅圖等。

### 如何自訂圖表的外觀？

您可以透過存取圖表的屬性和設定樣式、顏色等來自訂外觀。

### 是否可以為圖表添加多個系列？

絕對地！您可以透過調用 `Series.Add` 使用不同的數據多次執行該方法。

### 如果我需要動態更新圖表資料怎麼辦？

您可以根據需要透過程式操作系列和軸屬性來動態更新圖表資料。

### 在哪裡可以找到有關 Aspose.Words for .NET 的更詳細文件？

您可以找到更詳細的文檔 [這裡](https://reference。aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}