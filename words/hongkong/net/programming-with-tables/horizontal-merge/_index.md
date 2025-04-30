---
"description": "透過本詳細的逐步教學了解如何使用 Aspose.Words for .NET 在 Word 文件中水平合併儲存格。"
"linktitle": "水平合併"
"second_title": "Aspose.Words文件處理API"
"title": "水平合併"
"url": "/zh-hant/net/programming-with-tables/horizontal-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 水平合併

## 介紹

嘿！準備好深入了解 Aspose.Words for .NET 的世界了嗎？今天，我們將討論一個非常有用的功能：表格中的水平合併。這聽起來可能有點技術性，但別擔心，我會支持你。在本教學結束時，您將能夠熟練地以程式設計方式合併 Word 文件中的儲存格。那麼，讓我們捲起袖子開始行動吧！

## 先決條件

在我們深入討論細節之前，您需要先做好以下幾件事：

1. Aspose.Words for .NET 函式庫：如果您還沒下載，請下載 Aspose.Words for .NET 函式庫。你可以抓住它 [這裡](https://releases。aspose.com/words/net/).
2. 開發環境：確保您已設定合適的開發環境，例如 Visual Studio。
3. C# 基礎知識：對 C# 程式設計有基本的了解將會很有幫助。

一旦解決了這些問題，您就可以開始了！

## 導入命名空間

在深入研究程式碼之前，讓我們確保已經導入了必要的命名空間。在您的 C# 專案中，請確保包含：

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

好吧，讓我們分解使用 Aspose.Words for .NET 在 Word 文件中水平合併表格單元格的過程。

## 步驟1：設定文檔

首先，我們需要建立一個新的 Word 文件並初始化 `DocumentBuilder`：

```csharp
// 文檔目錄的路徑 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

此程式碼片段設定了一個新文件並準備 `DocumentBuilder` 採取行動。

## 步驟 2：插入第一個儲存格

接下來，我們開始插入第一個儲存格並將其標記為水平合併：

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

在這裡，我們插入一個新單元格並設定其 `HorizontalMerge` 財產 `CellMerge.First`，表示該儲存格是合併儲存格序列的開頭。

## 步驟3：插入合併儲存格

現在，我們插入將與前一個儲存格合併的儲存格：

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

此儲存格設定為與前一個儲存格合併，方法是使用 `CellMerge.Previous`。注意我們如何用 `builder。EndRow()`.

## 步驟 4：插入未合併的儲存格

為了說明差異，讓我們插入幾個未合併的儲存格：

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

這裡我們插入兩個沒有水平合併的儲存格。這顯示了當細胞不是合併序列的一部分時它們的行為。

## 第五步：完成表格

最後，我們結束表格並儲存文件：

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

此程式碼片段完成表格並將文件儲存到指定目錄。

## 結論

就是這樣！您剛剛掌握了使用 Aspose.Words for .NET 在 Word 文件中水平合併單元格的技術。透過遵循這些步驟，您可以輕鬆建立複雜的表格結構。繼續嘗試並探索 Aspose.Words 的功能，讓您的文件盡可能地動態和靈活。編碼愉快！

## 常見問題解答

### 什麼是 Aspose.Words for .NET？
Aspose.Words for .NET 是一個功能強大的程式庫，可讓開發人員在 .NET 應用程式中以程式設計方式建立、編輯和操作 Word 文件。

### 我可以使用 Aspose.Words for .NET 垂直合併儲存格嗎？
是的，您也可以使用 `CellFormat.VerticalMerge` 財產。

### Aspose.Words for .NET 可以免費使用嗎？
Aspose.Words for .NET 提供免費試用，但要使用全部功能，您需要購買授權。您可以獲得臨時駕照 [這裡](https://purchase。aspose.com/temporary-license/).

### 如何了解更多關於 Aspose.Words for .NET 的資訊？
您可以探索詳細文檔 [這裡](https://reference。aspose.com/words/net/).

### 在哪裡可以獲得 Aspose.Words for .NET 的支援？
如有任何疑問或問題，您可以造訪 Aspose 支援論壇 [這裡](https://forum。aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}