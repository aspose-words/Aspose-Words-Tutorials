---
"description": "了解如何使用 Aspose.Words for .NET 設定圖表中資料標籤的預設選項。按照我們的逐步指南輕鬆建立和自訂圖表。"
"linktitle": "設定圖表中資料標籤的預設選項"
"second_title": "Aspose.Words文件處理API"
"title": "設定圖表中資料標籤的預設選項"
"url": "/zh-hant/net/programming-with-charts/default-options-for-data-labels/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 設定圖表中資料標籤的預設選項

## 介紹

嘿！您是否對深入文件自動化的世界感到興奮？今天，我們將探討如何使用 Aspose.Words for .NET 以程式設計方式建立令人驚嘆的文件。 Aspose.Words 是一個功能強大的庫，可讓您輕鬆操作 Word 文檔，在本教程中，我們將重點介紹如何設定圖表中資料標籤的預設選項。無論您是經驗豐富的開發人員還是新手，本指南都會引導您完成每個步驟，讓您立即開始使用。

## 先決條件

在開始之前，請確保您已準備好學習本教學所需的一切。以下是一份快速清單：

- Visual Studio 或任何其他 .NET 相容 IDE：您可以在這裡編寫和執行程式碼。
- Aspose.Words for .NET：您可以 [下載最新版本](https://releases.aspose.com/words/net/) 並將其安裝在您的專案中。
- C# 程式設計的基礎：雖然本指南適合初學者，但稍微熟悉一下 C# 也會有所幫助。
- 安裝 .NET Framework：確保您的機器上已安裝 .NET Framework。
- Aspose.Words 的臨時許可證：取得一個 [這裡](https://purchase.aspose.com/temporary-license/) 解鎖全部功能。

一旦您滿足了這些先決條件，我們就可以開始了！

## 導入命名空間

首先，讓我們建立我們的專案並導入必要的命名空間。這些命名空間對於存取 Aspose.Words 功能至關重要。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## 步驟 1：建立新文檔


旅程從創建新文件並初始化 `DocumentBuilder`。這 `DocumentBuilder` 類別提供了一組方法來輕鬆操作文件內容。

```csharp
// 文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";

// 建立新文檔
Document doc = new Document();

// 初始化 DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);
```

### 解釋

在此步驟中，我們設定了用於插入和格式化內容的文件和建構器。這 `dataDir` 變數保存我們保存最終文檔的路徑。

## 第 2 步：插入圖表

接下來，我們將在文件中新增一個圓餅圖。這 `InsertChart` 方法 `DocumentBuilder` 課程讓這一切變得非常簡單。

```csharp
// 插入圓餅圖
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// 存取圖表對象
Chart chart = shape.Chart;
```

### 解釋

在這裡，我們將餅圖插入到我們的文件中。這 `InsertChart` 方法需要圖表類型、寬度和高度作為參數。插入圖表後，我們訪問圖表物件以進一步操作它。

## 步驟 3：自訂圖表系列

現在，我們將清除圖表中所有現有系列並新增我們的自訂系列。該系列將代表我們的數據點。

```csharp
// 清除現有圖表系列
chart.Series.Clear();

// 在圖表中新增系列
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### 解釋

在此步驟中，我們要清除所有預先存在的系列，以確保圖表為空。然後，我們新增一個具有自訂類別和值的新系列，它將顯示在我們的餅圖中。

## 步驟 4：設定資料標籤的預設選項

數據標籤對於使圖表資訊豐富至關重要。我們將設定選項來顯示百分比、值並自訂分隔符號。

```csharp
// 存取資料標籤集合
ChartDataLabelCollection labels = series.DataLabels;

// 設定資料標籤選項
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### 解釋

在這裡，我們正在訪問 `DataLabels` 我們系列的屬性來自訂每個資料標籤上顯示的外觀和資訊。我們選擇顯示百分比和值、隱藏引線並設定自訂分隔符號。

## 步驟5：儲存文檔

最後，我們將文檔儲存到指定的目錄。此步驟確保我們所有的變更都寫入檔案。

```csharp
// 儲存文件
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### 解釋

在最後一步中，我們使用 `Save` 方法。該文件將保存在指定的目錄中 `dataDir`，名稱為「WorkingWithCharts.DefaultOptionsForDataLabels.docx」。

## 結論

就是這樣！您已成功使用 Aspose.Words for .NET 建立了帶有自訂餅圖的 Word 文件。這個強大的庫可以輕鬆實現文件創建和操作的自動化，從而節省您的時間和精力。無論您產生報告、發票或任何其他類型的文檔，Aspose.Words 都能滿足您的需求。

隨意探索 [Aspose.Words 文檔](https://reference.aspose.com/words/net/) 了解更多功能和範例。編碼愉快！

## 常見問題解答

### 我可以免費使用 Aspose.Words 嗎？
您可以免費使用 Aspose.Words [臨時執照](https://purchase.aspose.com/temporary-license/) 或使用 [免費試用](https://releases。aspose.com/).

### 如何獲得 Aspose.Words 的支援？
您可以透過以下方式獲得支持 [Aspose.Words 支援論壇](https://forum。aspose.com/c/words/8).

### 我可以添加其他類型的圖表嗎？
是的，Aspose.Words 支援各種圖表類型，例如長條圖、折線圖和長條圖。檢查 [文件](https://reference.aspose.com/words/net/) 了解更多詳情。

### Aspose.Words 與 .NET Core 相容嗎？
是的，Aspose.Words 與 .NET Core 相容。您可以在 [文件](https://reference。aspose.com/words/net/).

### 如何購買 Aspose.Words 的授權？
您可以從 [Aspose 商店](https://purchase。aspose.com/buy).




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}