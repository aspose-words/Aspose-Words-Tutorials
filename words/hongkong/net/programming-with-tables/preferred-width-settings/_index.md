---
title: 首選寬度設定
linktitle: 首選寬度設定
second_title: Aspose.Words 文件處理 API
description: 透過此逐步指南，了解如何在 Aspose.Words for .NET 中建立具有絕對、相對和自動寬度設定的表格。
weight: 10
url: /zh-hant/net/programming-with-tables/preferred-width-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 首選寬度設定

## 介紹

表格是在 Word 文件中組織和呈現資訊的有效方式。在 Aspose.Words for .NET 中使用表格時，您可以使用多種選項來設定表格單元格的寬度，以確保它們完美地適合文件的佈局。本指南將引導您完成使用 Aspose.Words for .NET 建立具有首選寬度設定的表格的過程，重點是絕對、相對和自動調整大小選項。 

## 先決條件

在深入學習本教學之前，請確保您具備以下條件：

1.  Aspose.Words for .NET：請確定您的開發環境中安裝了 Aspose.Words for .NET。你可以下載它[這裡](https://releases.aspose.com/words/net/).

2. .NET 開發環境：設定 .NET 開發環境，例如 Visual Studio。

3. C# 基礎知識：熟悉 C# 程式設計將有助於您更好地理解程式碼片段和範例。

4.  Aspose.Words 文件：請參閱[Aspose.Words 文檔](https://reference.aspose.com/words/net/)取得詳細的 API 資訊和進一步閱讀。

## 導入命名空間

在開始編碼之前，您需要將必要的命名空間匯入到您的 C# 專案中：

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

這些命名空間提供對 Aspose.Words 和 Table 物件的核心功能的訪問，可讓您操作文件表。

讓我們將建立具有不同首選寬度設定的表格的過程分解為清晰、可管理的步驟。

## 第 1 步：初始化 Document 和 DocumentBuilder

標題：建立新文件和 DocumentBuilder

說明：先建立一個新的Word文件和一個`DocumentBuilder`實例。這`DocumentBuilder`類別提供了一種向文件添加內容的簡單方法。

```csharp
//定義儲存文檔的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";

//建立一個新文件。
Document doc = new Document();

//為此文件建立一個 DocumentBuilder。
DocumentBuilder builder = new DocumentBuilder(doc);
```

在這裡，您指定保存文件的目錄並初始化`Document`和`DocumentBuilder`對象。

## 步驟 2：插入第一個具有絕對寬度的表格儲存格

將第一個儲存格插入表格中，固定寬度為 40 磅。這將確保該單元格始終保持 40 磅的寬度，無論表格大小如何。

```csharp
//插入絕對大小的儲存格。
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

在此步驟中，您將開始建立表格並插入具有絕對寬度的儲存格。這`PreferredWidth.FromPoints(40)`方法將單元格的寬度設定為 40 磅，並且`Shading.BackgroundPatternColor`應用淺黃色背景顏色。

## 步驟 3：插入相對大小的儲存格

插入另一個寬度為表格總寬度 20% 的儲存格。這種相對大小可確保儲存格根據表格寬度按比例調整。

```csharp
//插入相對（百分比）大小的儲存格。
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

該單元格的寬度將是表格總寬度的 20%，使其能夠適應不同的螢幕尺寸或文件佈局。

### 步驟 4：插入自動調整大小的儲存格

最後，插入一個根據表中剩餘可用空間自動調整自身大小的儲存格。

```csharp
//插入自動調整大小的儲存格。
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. The size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

這`PreferredWidth.Auto`設定允許此單元格根據考慮其他單元格後剩餘的空間進行擴展或收縮。這確保了桌子佈局看起來平衡且專業。

## 第 5 步：完成並儲存文檔

插入所有儲存格後，填寫表格並將文件儲存到指定的路徑。

```csharp
//儲存文檔。
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

此步驟完成表格並將文件保存在指定目錄中，文件名為「WorkingWithTables.PreferredWidthSettings.docx」。

## 結論

一旦您了解了可用的不同大小選項，在 Aspose.Words for .NET 中建立具有首選寬度設定的表格就很簡單。無論您需要固定、相對或自動儲存格寬度，Aspose.Words 都能靈活且有效率地處理各種表格佈局情境。透過遵循本指南中概述的步驟，您可以確保 Word 文件中的表格結構良好且具有視覺吸引力。

## 常見問題解答

### 絕對單元格寬度和相對單元格寬度有什麼不同？
絕對單元格寬度是固定的並且不會更改，而相對寬度則根據表格的總寬度進行調整。

### 我可以使用負百分比作為相對寬度嗎？
不，負百分比對於單元格寬度無效。只允許使用正百分比。

### 自動調整大小功能如何運作？
自動調整大小會調整儲存格的寬度，以在調整其他儲存格的大小後填滿表格中的任何剩餘空間。

### 我可以對具有不同寬度設定的儲存格套用不同的樣式嗎？
是的，您可以將各種樣式和格式套用至儲存格，無論其寬度設定為何。

### 如果表格的總寬度小於所有儲存格寬度的總和，會發生什麼情況？
表格將自動調整儲存格的寬度以適合可用空間，這可能會導致某些儲存格縮小。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
