---
title: 在Word文件中插入散佈圖
linktitle: 在Word文件中插入散佈圖
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 在 Word 中插入散佈圖。將可視化資料表示整合到文件中的簡單步驟。
weight: 10
url: /zh-hant/net/programming-with-charts/insert-scatter-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在Word文件中插入散佈圖

## 介紹

在本教學中，您將學習如何利用 Aspose.Words for .NET 將散佈圖插入 Word 文件中。散佈圖是功能強大的視覺化工具，可有效顯示基於兩個變數的資料點，使您的文件更具吸引力和資訊量。

## 先決條件

在我們深入使用 Aspose.Words for .NET 建立散佈圖之前，請確保您具備以下先決條件：

1. 安裝 Aspose.Words for .NET：從下列位置下載並安裝 Aspose.Words for .NET[這裡](https://releases.aspose.com/words/net/).
   
2. C# 基礎知識：熟悉 C# 程式語言和 .NET 框架將很有幫助。

## 導入命名空間

首先，您需要在 C# 專案中匯入必要的命名空間：

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
```

現在，讓我們分解一下使用 Aspose.Words for .NET 將散佈圖插入到 Word 文件中的過程：

## 第 1 步：初始化 Document 和 DocumentBuilder

首先，初始化一個新的實例`Document`類和`DocumentBuilder`類別開始建立您的文件。

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 第 2 步：插入散佈圖

使用`InsertChart`的方法`DocumentBuilder`類別將散點圖插入文件中。

```csharp
Shape shape = builder.InsertChart(ChartType.Scatter, 432, 252);
Chart chart = shape.Chart;
```

## 第 3 步：將資料系列新增至圖表中

現在，將資料系列新增至散佈圖中。此範例示範新增具有特定資料點的系列。

```csharp
chart.Series.Add("Aspose Series 1", new double[] { 0.7, 1.8, 2.6 }, new double[] { 2.7, 3.2, 0.8 });
```

## 步驟 4：儲存文檔

最後，使用以下命令將修改後的文件儲存到您想要的位置`Save`的方法`Document`班級。

```csharp
doc.Save(dataDir + "WorkingWithCharts.InsertScatterChart.docx");
```

## 結論

恭喜！您已成功學習如何使用 Aspose.Words for .NET 將散佈圖插入 Word 文件中。散點圖是可視化資料關係的出色工具，借助 Aspose.Words，您可以輕鬆地將它們整合到文件中，以提高清晰度和理解性。

## 常見問題解答

### 我可以使用 Aspose.Words 自訂散點圖的外觀嗎？
是的，Aspose.Words 允許對圖表屬性進行廣泛的自訂，例如顏色、軸和標籤。

### Aspose.Words 是否與不同版本的 Microsoft Word 相容？
Aspose.Words支援各種版本的Microsoft Word，確保跨平台的兼容性。

### Aspose.Words 是否提供其他類型圖表的支援？
是的，Aspose.Words 支援多種圖表類型，包括長條圖、折線圖和圓餅圖。

### 我可以透過程式動態更新散點圖中的資料嗎？
當然，您可以使用 Aspose.Words API 呼叫動態更新圖表資料。

### 我可以在哪裡獲得 Aspose.Words 的進一步幫助或支援？
如需進一步協助，請訪問[Aspose.Words 支援論壇](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
