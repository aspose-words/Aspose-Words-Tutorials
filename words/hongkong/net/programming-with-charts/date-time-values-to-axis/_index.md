---
title: 將日期時間值加到圖表的軸
linktitle: 將日期時間值加到圖表的軸
second_title: Aspose.Words 文件處理 API
description: 在此綜合逐步指南中了解如何使用 Aspose.Words for .NET 將日期和時間值新增至圖表的軸。
weight: 10
url: /zh-hant/net/programming-with-charts/date-time-values-to-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將日期時間值加到圖表的軸

## 介紹

在文件中建立圖表是可視化資料的有效方法。處理時間序列資料時，將日期和時間值新增至圖表的軸對於清晰起見至關重要。在本教學中，我們將引導您完成使用 Aspose.Words for .NET 將日期和時間值新增至圖表軸的過程。本逐步指南將幫助您設定環境、編寫程式碼並了解流程的每個部分。讓我們深入了解吧！

## 先決條件

在我們開始之前，請確保您具備以下先決條件：

1. Visual Studio 或任何 .NET IDE：您需要一個開發環境來編寫和執行 .NET 程式碼。
2.  Aspose.Words for .NET：您應該安裝 Aspose.Words for .NET 程式庫。您可以從以下位置下載：[這裡](https://releases.aspose.com/words/net/).
3. C# 基礎知識：本教學假設您對 C# 程式設計有基本了解。
4. 有效的 Aspose 許可證：您可以從以下位置取得臨時許可證[這裡](https://purchase.aspose.com/temporary-license/).

## 導入命名空間

首先，請確保您的專案中導入了必要的命名空間。此步驟對於存取 Aspose.Words 類別和方法至關重要。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## 第 1 步：設定您的文件目錄

首先，您需要定義儲存文件的目錄。這對於組織文件並確保程式碼正確運行非常重要。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 第 2 步：建立新文件和 DocumentBuilder

接下來，建立一個新實例`Document`類別和一個`DocumentBuilder`目的。這些物件將幫助您建置和操作文件。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 步驟 3：將圖表插入文檔

現在，使用以下命令將圖表插入到您的文件中`DocumentBuilder`目的。在此範例中，我們使用長條圖，但您也可以選擇其他類型。

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## 第4步：清除現有系列

清除圖表中任何現有的系列，以確保您從一張白紙開始。此步驟對於自訂資料至關重要。

```csharp
chart.Series.Clear();
```

## 步驟 5：為系列新增日期和時間值

將日期和時間值加入圖表系列。此步驟涉及為日期和相應值建立數組。

```csharp
chart.Series.Add("Aspose Series 1",
    new[]
    {
        new DateTime(2017, 11, 06), new DateTime(2017, 11, 09), new DateTime(2017, 11, 15),
        new DateTime(2017, 11, 21), new DateTime(2017, 11, 25), new DateTime(2017, 11, 29)
    },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2, 5.3 });
```

## 第 6 步：配置 X 軸

設定 X 軸的縮放比例和刻度線。這可確保您的日期以適當的間隔正確顯示。

```csharp
ChartAxis xAxis = chart.AxisX;
xAxis.Scaling.Minimum = new AxisBound(new DateTime(2017, 11, 05).ToOADate());
xAxis.Scaling.Maximum = new AxisBound(new DateTime(2017, 12, 03).ToOADate());
xAxis.MajorUnit = 7;
xAxis.MinorUnit = 1;
xAxis.MajorTickMark = AxisTickMark.Cross;
xAxis.MinorTickMark = AxisTickMark.Outside;
```

## 步驟7：儲存文檔

最後，將文檔儲存到指定目錄。此步驟結束該過程，您的文件現在應該包含一個 X 軸上帶有日期和時間值的圖表。

```csharp
doc.Save(dataDir + "WorkingWithCharts.DateTimeValuesToAxis.docx");
```

## 結論

使用 Aspose.Words for .NET 將日期和時間值新增至文件中圖表的軸是一個簡單的過程。透過遵循本教程中概述的步驟，您可以建立清晰且資訊豐富的圖表，以有效地視覺化時間序列資料。無論您是準備報告、簡報或任何需要詳細資料表示的文檔，Aspose.Words 都能為您提供成功所需的工具。

## 常見問題解答

### 我可以在 Aspose.Words for .NET 中使用其他圖表類型嗎？

是的，Aspose.Words 支援各種圖表類型，包括折線圖、長條圖、圓餅圖等。

### 如何自訂圖表的外觀？

您可以透過存取圖表的屬性並設定樣式、顏色等來自訂外觀。

### 是否可以為圖表添加多個系列？

絕對地！您可以透過呼叫將多個系列新增到圖表中`Series.Add`使用不同的數據多次方法。

### 如果我需要動態更新圖表資料怎麼辦？

您可以根據您的要求透過程式設計操作系列和軸屬性來動態更新圖表資料。

### 在哪裡可以找到有關 Aspose.Words for .NET 的更詳細文件？

你可以找到更詳細的文檔[這裡](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
