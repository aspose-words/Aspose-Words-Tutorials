---
"description": "透過本逐步指南了解如何使用 Aspose.Words for .NET 設定圖表中資料標籤的格式。輕鬆增強您的 Word 文件。"
"linktitle": "圖表中資料標籤的格式數量"
"second_title": "Aspose.Words文件處理API"
"title": "圖表中資料標籤的格式數量"
"url": "/zh-hant/net/programming-with-charts/format-number-of-data-label/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 圖表中資料標籤的格式數量

## 介紹

創建引人入勝且資訊豐富的文件通常涉及包含格式良好的數據標籤的圖表。如果您是 .NET 開發人員，希望使用複雜的圖表來增強您的 Word 文檔，那麼 Aspose.Words for .NET 是一個可以幫助您實現這一目標的絕佳庫。本教學將逐步引導您使用 Aspose.Words for .NET 在圖表中格式化數位標籤的過程。

## 先決條件

在深入研究程式碼之前，您需要滿足一些先決條件：

- Aspose.Words for .NET：請確定您已安裝 Aspose.Words for .NET 程式庫。如果你還沒有安裝，你可以 [點此下載](https://releases。aspose.com/words/net/).
- 開發環境：您應該設定一個.NET 開發環境。強烈推薦 Visual Studio。
- C# 基礎知識：熟悉 C# 程式設計至關重要，因為本教學涉及編寫和理解 C# 程式碼。
- 臨時授權：若要無限制使用 Aspose.Words，您可以獲得 [臨時執照](https://purchase。aspose.com/temporary-license/).

現在，讓我們深入了解在圖表中格式化數字標籤的逐步過程。

## 導入命名空間

首先，我們需要匯入必要的命名空間才能使用 Aspose.Words for .NET。在 C# 檔案的頂部新增以下行：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## 步驟 1：設定文檔目錄

在開始處理 Word 文件之前，您需要指定已儲存文件的目錄。這對於稍後的保存操作至關重要。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替 `"YOUR DOCUMENT DIRECTORY"` 使用您的文件目錄的實際路徑。

## 步驟 2：初始化 Document 和 DocumentBuilder

下一步是初始化一個新的 `Document` 和一個 `DocumentBuilder`。這 `DocumentBuilder` 是一個輔助類，允許我們建立文件內容。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 步驟 3：將圖表插入文檔

現在，讓我們使用 `DocumentBuilder`。在本教程中，我們將使用折線圖作為範例。

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
chart.Title.Text = "Data Labels With Different Number Format";
```

這裡我們插入一個具有特定寬度和高度的折線圖，並設定圖表標題。

## 步驟 4：清除預設系列並新增系列

預設情況下，圖表會有一些預先產生的系列。我們需要清除這些並添加具有特定數據點的我們自己的系列。

```csharp
// 刪除預設產生的系列。
chart.Series.Clear();

// 新增具有自訂資料點的新系列。
ChartSeries series1 = chart.Series.Add("Aspose Series 1", 
	new string[] { "Category 1", "Category 2", "Category 3" }, 
	new double[] { 2.5, 1.5, 3.5 });
```

## 步驟 5：啟用資料標籤

為了在圖表上顯示數據標籤，我們需要為我們的系列啟用它們。

```csharp
series1.HasDataLabels = true;
series1.DataLabels.ShowValue = true;
```

## 步驟 6：格式化資料標籤

本教學的核心是格式化資料標籤。我們可以對每個資料標籤單獨套用不同的數字格式。

```csharp
series1.DataLabels[0].NumberFormat.FormatCode = "\"$\"#,##0.00"; // 貨幣格式
series1.DataLabels[1].NumberFormat.FormatCode = "dd/mm/yyyy"; // 日期格式
series1.DataLabels[2].NumberFormat.FormatCode = "0.00%"; // 百分比格式
```

此外，您也可以將資料標籤的格式連結到來源儲存格。當連結時， `NumberFormat` 將被重置為常規並從來源單元格繼承。

```csharp
series1.DataLabels[2].NumberFormat.IsLinkedToSource = true;
```

## 步驟 7：儲存文檔

最後將文檔儲存到指定目錄。

```csharp
doc.Save(dataDir + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

這將以指定的名稱儲存您的文檔，並確保保留帶有格式化資料標籤的圖表。

## 結論

使用 Aspose.Words for .NET 格式化圖表中的資料標籤可以大幅增強 Word 文件的可讀性和專業性。透過遵循本逐步指南，您現在應該能夠建立圖表、新增資料系列並格式化資料標籤以滿足您的需求。 Aspose.Words for .NET 是一款功能強大的工具，允許對 Word 文件進行廣泛的客製化和自動化，這使其成為 .NET 開發人員的寶貴資產。

## 常見問題解答

### 什麼是 Aspose.Words for .NET？
Aspose.Words for .NET 是一個功能強大的函式庫，可使用 C# 以程式設計方式建立、操作和轉換 Word 文件。

### 我可以使用 Aspose.Words for .NET 格式化其他類型的圖表嗎？
是的，Aspose.Words for .NET 支援多種圖表類型，包括長條圖、長條圖、圓餅圖等。

### 如何取得 Aspose.Words for .NET 的臨時授權？
您可以獲得臨時駕照 [這裡](https://purchase。aspose.com/temporary-license/).

### 是否可以將資料標籤連結到 Excel 中的來源儲存格？
是的，您可以將資料標籤連結到來源單元格，從而允許從來源單元格繼承數字格式。

### 在哪裡可以找到有關 Aspose.Words for .NET 的更詳細文件？
您可以找到全面的文檔 [這裡](https://reference。aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}