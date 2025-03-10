---
title: 使用形狀建立和自訂圖表
linktitle: 使用形狀建立和自訂圖表
second_title: Aspose.Words 文件處理 API
description: 透過此逐步指南，了解如何使用 Aspose.Words for .NET 在 Word 文件中建立和自訂圖表。非常適合數據視覺化。
weight: 10
url: /zh-hant/net/programming-with-charts/create-chart-using-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用形狀建立和自訂圖表

## 介紹

在當今數據驅動的世界中，在文件中建立和自訂圖表是一項至關重要的技能。圖表可以幫助可視化數據，使複雜的資訊更容易理解。 Aspose.Words for .NET 是一個功能強大的程式庫，可讓您以程式設計方式建立和操作 Word 文件。在本教學中，我們將引導您完成使用 Aspose.Words for .NET 建立和自訂折線圖的過程。閱讀本指南後，您將能夠輕鬆建立具有專業外觀的圖表。

## 先決條件

在深入研究程式碼之前，請確保您具備以下條件：

-  Aspose.Words for .NET Library：您可以下載它[這裡](https://releases.aspose.com/words/net/).
- Visual Studio：任何支援 .NET 的版本。
- C# 基礎知識：了解 C# 基礎知識將幫助您遵循本教學。

## 導入命名空間

首先，您需要匯入必要的命名空間。此步驟至關重要，因為它允許您使用 Aspose.Words for .NET 提供的類別和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## 第 1 步：建立一個新文檔

首先，您需要建立一個新的Word文件。該文件將作為您的圖表的畫布。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 第 2 步：插入圖表

接下來，您將在文件中插入折線圖。這`DocumentBuilder.InsertChart`方法就是用於此目的。

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

## 第 3 步：自訂圖表標題

自訂圖表標題有助於為所顯示的資料提供上下文。您可以使用以下程式碼顯示標題並設定其文字：

```csharp
chart.Title.Show = true;
chart.Title.Text = "Line Chart Title";
chart.Title.Overlay = false;
//請注意，如果將 null 或空值指定為標題文本，則會顯示自動產生的標題。
```

## 第4步：調整圖例位置

圖例有助於識別圖表中的不同資料系列。您可以自訂其位置和覆蓋設置，如下所示：

```csharp
chart.Legend.Position = LegendPosition.Left;
chart.Legend.Overlay = true;
```

## 第 5 步：儲存文檔

最後，您需要儲存文件。此步驟可確保您的所有變更都寫入文件中。

```csharp
doc.Save(dataDir + "WorkingWithCharts.CreateChartUsingShape.docx");
```

## 結論

在本教學中，我們介紹如何使用 Aspose.Words for .NET 在 Word 文件中建立和自訂折線圖。透過遵循逐步指南，您現在可以建立具有視覺吸引力的圖表，以有效地傳達數據。 Aspose.Words for .NET 提供了廣泛的自訂選項，可讓您根據您的特定需求自訂圖表。

## 常見問題解答

### 我可以使用 Aspose.Words for .NET 建立其他類型的圖表嗎？

是的，Aspose.Words for .NET 支援各種圖表類型，包括長條圖、圓餅圖等。您可以瀏覽文檔[這裡](https://reference.aspose.com/words/net/)了解更多詳情。

### 購買前如何試用 Aspose.Words for .NET？

您可以從以下位置下載免費試用版[這裡](https://releases.aspose.com/)。這使您可以在購買之前測試該庫及其功能。

### 如果我遇到問題，有辦法獲得支援嗎？

絕對地。您可以透過 Aspose 社群論壇獲得支持[這裡](https://forum.aspose.com/c/words/8)。社區和 Aspose 工作人員反應非常積極。

### 如何購買 Aspose.Words for .NET 的授權？

您可以直接從 Aspose 網站購買許可證[這裡](https://purchase.aspose.com/buy)。有多種授權選項可以滿足不同的需求。

### 如果我需要短期專案的臨時許可證怎麼辦？

 Aspose 提供臨時許可證，您可以申請[這裡](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
