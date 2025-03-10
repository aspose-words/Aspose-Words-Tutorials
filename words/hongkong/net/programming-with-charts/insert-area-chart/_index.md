---
title: 將面積圖插入 Word 文檔
linktitle: 將面積圖插入 Word 文檔
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 將面積圖插入文件中。新增系列資料並使用圖表儲存文件。
weight: 10
url: /zh-hant/net/programming-with-charts/insert-area-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將面積圖插入 Word 文檔

## 介紹

歡迎閱讀本逐步指南，以了解如何使用 Aspose.Words for .NET 將面積圖插入 Word 文件中。無論您是經驗豐富的開發人員還是剛剛入門，本教學都將引導您完成在 Word 文件中創建令人驚嘆且資訊豐富的面積圖所需了解的所有內容。我們將介紹先決條件，向您展示如何匯入必要的命名空間，並透過清晰、易於遵循的說明指導您完成流程的每個步驟。

## 先決條件

在我們深入之前，讓我們確保您擁有開始所需的一切：

1.  Aspose.Words for .NET：請確定您已安裝 Aspose.Words for .NET。你可以下載它[這裡](https://releases.aspose.com/words/net/).
2. .NET Framework：請確定您的電腦上安裝了 .NET Framework。
3. IDE：類似 Visual Studio 的整合開發環境 (IDE)，用於編寫和執行程式碼。
4. 基本 C# 知識：對 C# 程式設計的基本了解會很有幫助。

滿足這些先決條件後，您就可以開始在 Word 文件中建立漂亮的面積圖了。

## 導入命名空間

首先，讓我們導入必要的名稱空間。這些命名空間提供了在 Aspose.Words for .NET 中處理 Word 文件和圖表所需的類別和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
```

現在我們已經導入了必要的命名空間，讓我們繼續建立文件並逐步插入面積圖。

## 第 1 步：建立一個新的 Word 文檔

讓我們先建立一個新的 Word 文件。這將是我們插入面積圖的基礎。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

在這一步驟中，我們初始化一個新的`Document`代表我們的Word文檔的物件。

## 步驟 2：使用 DocumentBuilder 插入圖表

接下來，我們將使用`DocumentBuilder`類別將面積圖插入到我們的文件中。

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.InsertChart(ChartType.Area, 432, 252);
```

在這裡，我們創建一個`DocumentBuilder`物件並使用它將特定尺寸 (432x252) 的面積圖插入到我們的文件中。

## 第 3 步：存取圖表對象

插入圖表後，我們需要訪問`Chart`物件客製化我們的面積圖。

```csharp
Chart chart = shape.Chart;
```

這行程式碼檢索`Chart`我們剛剛插入的形狀中的物件。

## 第 4 步：將系列資料新增至圖表中

現在，是時候為我們的圖表添加一些數據了。我們將新增一個包含日期和對應值的系列。

```csharp
chart.Series.Add("Aspose Series 1", new []
{
    new DateTime(2002, 05, 01),
    new DateTime(2002, 06, 01),
    new DateTime(2002, 07, 01),
    new DateTime(2002, 08, 01),
    new DateTime(2002, 09, 01)
}, 
new double[] { 32, 32, 28, 12, 15 });
```

在此步驟中，我們新增一個名為「Aspose Series 1」的系列，其中包含一組日期和對應的值。

## 第 5 步：儲存文檔

最後，我們將使用插入的面積圖來儲存文件。

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertAreaChart.docx");
```

這行程式碼使用給定的檔案名稱將文件儲存到指定的目錄。

## 結論

恭喜！您已使用 Aspose.Words for .NET 成功將面積圖插入 Word 文件中。本指南引導您完成從設定環境到儲存最終文件的每個步驟。透過 Aspose.Words for .NET，您可以在 Word 文件中建立各種圖表和其他複雜元素，讓您的報表和簡報更加動態和資訊豐富。

## 常見問題解答

### 我可以將 Aspose.Words for .NET 與其他 .NET 語言一起使用嗎？
是的，Aspose.Words for .NET 支援其他 .NET 語言，例如 VB.NET。

### 是否可以自訂圖表的外觀？
絕對地！ Aspose.Words for .NET 提供了廣泛的選項來自訂圖表的外觀。

### 我可以將多個圖表新增到單一 Word 文件中嗎？
是的，您可以根據需要在單一 Word 文件中插入任意數量的圖表。

### Aspose.Words for .NET 支援其他圖表類型嗎？
是的，Aspose.Words for .NET 支援各種圖表類型，包括長條圖、折線圖、圓餅圖等。

### 在哪裡可以獲得 Aspose.Words for .NET 的臨時授權？
您可以從以下地址取得臨時許可證[這裡](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
