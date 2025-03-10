---
title: 圖表中軸的數字格式
linktitle: 圖表中軸的數字格式
second_title: Aspose.Words 文件處理 API
description: 透過此逐步指南，了解如何使用 Aspose.Words for .NET 設定圖表軸編號的格式。輕鬆增強文件的可讀性和專業性。
weight: 10
url: /zh-hant/net/programming-with-charts/number-format-for-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 圖表中軸的數字格式

## 介紹

嘿！您是否曾經在文件中使用過圖表，並希望可以格式化軸上的數字以使它們看起來更專業？嗯，你很幸運！在本教程中，我們將深入探討如何使用 Aspose.Words for .NET 來實現這一目標。這個強大的程式庫讓您可以輕鬆地處理 Word 文件。今天，我們的重點是使用自訂數字格式對這些圖表軸進行改造。

## 先決條件

在開始之前，讓我們確保您已擁有所需的一切。這是一個快速清單：

-  Aspose.Words for .NET：確保您已安裝它。如果沒有，您可以[在這裡下載](https://releases.aspose.com/words/net/).
- .NET Framework：確保您安裝了相容的 .NET 框架。
- 開發環境：像 Visual Studio 這樣的 IDE 就可以完美運作。
- C# 基礎知識：這將幫助您遵循編碼範例。

## 導入命名空間

首先，您需要在專案中匯入必要的命名空間。這就像蓋房子之前先打地基一樣。在程式碼檔案頂部新增以下 using 指令：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Reporting;
```

現在，讓我們將該過程分解為簡單、易於遵循的步驟。

## 第 1 步：設定文檔

標題：初始化您的文檔

首先，您需要建立一個新文件和一個文件產生器。將此步驟視為在開始創作之前準備好畫布和畫筆。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

這裡，`dataDir`是儲存最終檔案的文檔目錄的路徑。`Document`和`DocumentBuilder`是 Aspose.Words 中的類，可協助您建立和操作 Word 文件。

## 第 2 步：插入圖表

標題：將圖表新增到文件中

接下來，讓我們將圖表新增到您的文件中。這就是魔法開始的地方。我們將插入一個長條圖作為空白畫布。

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

這`InsertChart`方法將指定類型（在本例中為長條圖）和維度的圖表插入文件中。

## 第 3 步：自訂圖表系列

標題：用數據填滿圖表

現在，我們需要在圖表中添加一些數據。此步驟類似於用有意義的資訊填滿圖表。

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1900000, 850000, 2100000, 600000, 1500000 });
```

在這裡，我們新增了一個名為「Aspose Series 1」的新系列，其中包含五個資料點。這`Series.Clear`方法確保在新增系列之前刪除任何預先存在的資料。

## 第 4 步：設定軸編號格式

標題：美化您的軸編號

最後，讓我們格式化 Y 軸上的數字，使其更易於閱讀。這就像是對你的藝術品進行最後的修飾。

```csharp
chart.AxisY.NumberFormat.FormatCode = "#,##0";
```

這`FormatCode`屬性允許您為軸上的數字設定自訂格式。在這個例子中，`#,##0`確保大數字以千位逗號顯示。

## 第 5 步：儲存文檔

標題：儲存你的傑作

現在一切都已設定完畢，是時候儲存文件了。這一步是你的作品的盛大展示。

```csharp
doc.Save(dataDir + "WorkingWithCharts.NumberFormatForAxis.docx");
```

在這裡，`Save`方法將文件以檔案名稱儲存到指定路徑`WorkingWithCharts.NumberFormatForAxis.docx`.

## 結論

現在你就擁有了！您已使用 Aspose.Words for .NET 成功設定了圖表 Y 軸上數字的格式。這不僅使您的圖表看起來更專業，而且還增強了可讀性。 Aspose.Words 提供了大量功能，可以幫助您以程式設計方式建立令人驚嘆的 Word 文件。那麼，為什麼不進行更多探索，看看還能做些什麼呢？

## 常見問題解答

### 什麼是 Aspose.Words for .NET？
Aspose.Words for .NET 是一個功能強大的程式庫，可讓開發人員以程式設計方式建立、操作和轉換 Word 文件。

### 除了軸編號之外，我還可以格式化圖表的其他方面嗎？
絕對地！ Aspose.Words for .NET 可讓您設定標題、標籤的格式，甚至自訂圖表的外觀。

### Aspose.Words for .NET 有沒有免費試用版？
是的，您可以獲得[在這裡免費試用](https://releases.aspose.com/).

### 我可以將 Aspose.Words for .NET 與 C# 以外的其他 .NET 語言一起使用嗎？
是的，Aspose.Words for .NET 與任何 .NET 語言相容，包括 VB.NET 和 F#。

### 在哪裡可以找到更詳細的文件？
詳細文件可在[Aspose.Words for .NET 文件頁面](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
