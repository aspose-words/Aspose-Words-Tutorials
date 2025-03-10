---
title: 設定圖表中資料標籤的預設選項
linktitle: 設定圖表中資料標籤的預設選項
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 設定圖表中資料標籤的預設選項。按照我們的逐步指南輕鬆建立和自訂圖表。
weight: 10
url: /zh-hant/net/programming-with-charts/default-options-for-data-labels/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 設定圖表中資料標籤的預設選項

## 介紹

嘿！您對進入文件自動化的世界感到興奮嗎？今天，我們將探討如何使用 Aspose.Words for .NET 以程式設計方式建立令人驚嘆的文件。 Aspose.Words 是一個功能強大的庫，可讓您輕鬆操作 Word 文檔，在本教程中，我們將重點關注為圖表中的資料標籤設定預設選項。無論您是經驗豐富的開發人員還是新手，本指南都將引導您完成每個步驟，以便您立即上手並運行。

## 先決條件

在開始之前，讓我們確保您已掌握本教學所需的一切。這是一個快速清單：

- Visual Studio 或任何其他 .NET 相容 IDE：您可以在此處編寫和執行程式碼。
-  Aspose.Words for .NET：您可以[下載最新版本](https://releases.aspose.com/words/net/)並將其安裝到您的專案中。
- C# 程式設計的基礎：雖然本指南適合初學者，但稍微熟悉一下 C# 將會有所幫助。
- 安裝 .NET Framework：確保您的電腦上安裝了 .NET Framework。
-  Aspose.Words 的臨時許可證：取得一個[這裡](https://purchase.aspose.com/temporary-license/)解鎖全部功能。

一旦您滿足了這些先決條件，我們就可以開始了！

## 導入命名空間

首先，讓我們設定專案並導入必要的命名空間。這些命名空間對於存取 Aspose.Words 功能至關重要。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## 第 1 步：建立一個新文檔


旅程從創建一個新文件並初始化一個`DocumentBuilder`。這`DocumentBuilder`類別提供了一組方法來輕鬆操作文件內容。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";

//建立一個新文檔
Document doc = new Document();

//初始化文檔產生器
DocumentBuilder builder = new DocumentBuilder(doc);
```

### 解釋

在此步驟中，我們設定了文件和建構器，我們將使用它們來插入和格式化內容。這`dataDir`變數保存我們保存最終文檔的路徑。

## 第 2 步：插入圖表

接下來，我們將向文件添加餅圖。這`InsertChart`的方法`DocumentBuilder`類別使這變得超級簡單。

```csharp
//插入圓餅圖
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

//存取圖表對象
Chart chart = shape.Chart;
```

### 解釋

在這裡，我們將餅圖插入到文件中。這`InsertChart`方法需要圖表類型、寬度和高度作為參數。插入圖表後，我們訪問圖表物件以進一步操作它。

## 第 3 步：自訂圖表系列

現在，我們將清除圖表中的任何現有系列並添加我們的自訂系列。該系列將代表我們的數據點。

```csharp
//清除現有圖表系列
chart.Series.Clear();

//將新系列加入圖表中
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### 解釋

在此步驟中，我們透過清除任何預先存在的系列來確保圖表為空。然後，我們新增一個具有自訂類別和值的新系列，這些系列將顯示在餅圖中。

## 步驟 4：設定資料標籤的預設選項

數據標籤對於使圖表資訊豐富至關重要。我們將設定選項來顯示百分比、值並自訂分隔符號。

```csharp
//存取資料標籤集合
ChartDataLabelCollection labels = series.DataLabels;

//設定資料標籤選項
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### 解釋

在這裡，我們正在訪問`DataLabels`我們系列的屬性可自訂每個資料標籤上顯示的外觀和資訊。我們選擇顯示百分比和值、隱藏引導線並設定自訂分隔符號。

## 第 5 步：儲存文檔

最後，我們將文檔儲存到指定的目錄。此步驟確保我們的所有變更都寫入文件中。

```csharp
//儲存文件
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### 解釋

在最後一步中，我們使用以下命令儲存文檔`Save`方法。該文件將保存在指定的目錄中`dataDir`，名稱為「WorkingWithCharts.DefaultOptionsForDataLabels.docx」。

## 結論

現在你就擁有了！您已使用 Aspose.Words for .NET 成功建立了帶有自訂餅圖的 Word 文件。這個功能強大的庫可以輕鬆實現文件創建和操作的自動化，從而節省您的時間和精力。無論您是產生報告、發票或任何其他類型的文檔，Aspose.Words 都能滿足您的需求。

隨意探索[Aspose.Words 文檔](https://reference.aspose.com/words/net/)了解更多功能和範例。快樂編碼！

## 常見問題解答

### 我可以免費使用 Aspose.Words 嗎？
您可以免費使用 Aspose.Words[臨時執照](https://purchase.aspose.com/temporary-license/)或使用探索其功能[免費試用](https://releases.aspose.com/).

### 如何獲得 Aspose.Words 支援？
您可以透過以下方式獲得支持[Aspose.Words 支援論壇](https://forum.aspose.com/c/words/8).

### 我可以添加其他類型的圖表嗎？
是的，Aspose.Words 支援各種圖表類型，例如長條圖、折線圖和長條圖。檢查[文件](https://reference.aspose.com/words/net/)了解更多詳情。

### Aspose.Words 與 .NET Core 相容嗎？
是的，Aspose.Words 與 .NET Core 相容。您可以在以下位置找到更多信息[文件](https://reference.aspose.com/words/net/).

### 如何購買 Aspose.Words 授權？
您可以從以下位置購買許可證[阿斯普斯商店](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
