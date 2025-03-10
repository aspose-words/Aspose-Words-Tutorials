---
title: 設定具有不同邊框的表格和儲存格格式
linktitle: 設定具有不同邊框的表格和儲存格格式
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 設定具有不同邊框的表格和儲存格格式。使用自訂表格樣式和儲存格底紋增強您的 Word 文件。
weight: 10
url: /zh-hant/net/programming-with-table-styles-and-formatting/format-table-and-cell-with-different-borders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 設定具有不同邊框的表格和儲存格格式

## 介紹

您是否曾經嘗試過透過自訂表格和儲存格的邊框來讓您的Word文件看起來更專業？如果沒有，你就大飽口福了！本教學將引導您完成使用 Aspose.Words for .NET 設定具有不同邊框的表格和儲存格格式的過程。想像一下，只需幾行程式碼就可以更改表格的外觀。有興趣嗎？讓我們深入探討如何輕鬆實現這一目標。

## 先決條件

在我們開始之前，請確保您具備以下先決條件：
- 對 C# 程式設計有基本了解。
- Visual Studio 安裝在您的電腦上。
-  Aspose.Words for .NET 函式庫。如果您還沒有安裝，可以下載[這裡](https://releases.aspose.com/words/net/).
- 有效的 Aspose 許可證。您可以從以下位置取得免費試用版或臨時許可證[這裡](https://purchase.aspose.com/temporary-license/).

## 導入命名空間

若要使用 Aspose.Words for .NET，您需要將必要的命名空間匯入到您的專案中。在程式碼檔案頂部新增以下 using 指令：

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;
```

## 步驟1：初始化Document和DocumentBuilder

首先，您需要建立一個新文件並初始化 DocumentBuilder，這有助於建立文件內容。 

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 第 2 步：開始建立表

接下來，使用 DocumentBuilder 開始建立表格並插入第一個儲存格。

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

## 第 3 步：設定表格邊框

設定整個表格的邊框。除非另有說明，此步驟可確保表中的所有儲存格具有一致的邊框樣式。

```csharp
//設定整個表格的邊框。
table.SetBorders(LineStyle.Single, 2.0, Color.Black);
```

## 第 4 步：套用儲存格陰影

對單元格套用陰影，使它們在視覺上清晰可見。在此範例中，我們將第一個單元格的背景顏色設為紅色。


```csharp
//設定該單元格的單元格底紋。
builder.CellFormat.Shading.BackgroundPatternColor = Color.Red;
builder.Writeln("Cell #1");
```

## 第 5 步：插入另一個具有不同底紋的單元格

插入第二個單元格並套用不同的底紋顏色。這使得表格更加豐富多彩並且更易於閱讀。

```csharp
builder.InsertCell();
//為第二個單元格指定不同的單元格底紋。
builder.CellFormat.Shading.BackgroundPatternColor = Color.Green;
builder.Writeln("Cell #2");
builder.EndRow();
```

## 第 6 步：清除儲存格格式

清除先前操作中的儲存格格式，以確保下一個儲存格不會繼承相同的樣式。


```csharp
//清除之前操作中的儲存格格式。
builder.CellFormat.ClearFormatting();
```

## 第 7 步：自訂特定單元格的邊框

自訂特定單元格的邊框以使它們脫穎而出。在這裡，我們將為新行的第一個儲存格設定更大的邊框。

```csharp
builder.InsertCell();
//為該行的第一個儲存格建立更大的邊框。這將會有所不同
//與為表格設定的邊框相比。
builder.CellFormat.Borders.Left.LineWidth = 4.0;
builder.CellFormat.Borders.Right.LineWidth = 4.0;
builder.CellFormat.Borders.Top.LineWidth = 4.0;
builder.CellFormat.Borders.Bottom.LineWidth = 4.0;
builder.Writeln("Cell #3");
```

## 第 8 步：插入最終儲存格

插入最後一個儲存格並確保清除其格式，以便它使用表格的預設樣式。

```csharp
builder.InsertCell();
builder.CellFormat.ClearFormatting();
builder.Writeln("Cell #4");
```

## 第9步：儲存文檔

最後將文檔儲存到指定目錄。

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.FormatTableAndCellWithDifferentBorders.docx");
```

## 結論

現在你就擁有了！您剛剛學習如何使用 Aspose.Words for .NET 設定具有不同邊框的表格和儲存格格式。透過自訂表格邊框和儲存格底紋，您可以顯著增強文件的視覺吸引力。因此，請繼續嘗試不同的樣式，讓您的文件脫穎而出！

## 常見問題解答

### 我可以為每個單元格使用不同的邊框樣式嗎？
是的，您可以使用以下命令為每個單元格設定不同的邊框樣式`CellFormat.Borders`財產。

### 如何刪除表格中的所有邊框？
您可以將邊框樣式設定為來刪除所有邊框`LineStyle.None`.

### 是否可以為每個單元格設定不同的邊框顏色？
絕對地！您可以使用以下命令自訂每個單元格的邊框顏色`CellFormat.Borders.Color`財產。

### 我可以使用圖像作為單元格背景嗎？
雖然Aspose.Words不直接支援圖像作為單元格背景，但您可以將圖像插入單元格並調整其大小以覆蓋單元格區域。

### 如何合併表格中的儲存格？
您可以使用以下命令合併儲存格`CellFormat.HorizontalMerge`和`CellFormat.VerticalMerge`特性。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
