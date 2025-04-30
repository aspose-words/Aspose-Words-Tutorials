---
"description": "透過本詳細的逐步指南了解如何使用 Aspose.Words for .NET 在 Word 文件中建立和格式化表格。"
"linktitle": "格式化表格"
"second_title": "Aspose.Words文件處理API"
"title": "格式化表格"
"url": "/zh-hant/net/programming-with-tables/formatted-table/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 格式化表格

## 介紹

以程式設計方式在 Word 文件中建立和格式化表格似乎是一項艱鉅的任務，但使用 Aspose.Words for .NET，它變得簡單且易於管理。在本教學中，我們將引導您如何使用 Aspose.Words for .NET 在 Word 文件中建立格式化表格。我們將介紹所有內容，從設定環境到使用格式精美的表格儲存文件。

## 先決條件

在深入研究程式碼之前，請確保您擁有所需的一切：

1. Aspose.Words for .NET Library：從以下位置下載 [這裡](https://releases。aspose.com/words/net/).
2. 開發環境：像 Visual Studio 這樣的 IDE。
3. .NET Framework：確保您的機器上安裝了 .NET Framework。

## 導入命名空間

在編寫實際程式碼之前，您需要匯入必要的命名空間：

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## 步驟 1：設定文檔目錄

首先，您需要定義文件的儲存路徑。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替 `"YOUR DOCUMENT DIRECTORY"` 與您想要儲存文件的實際路徑。

## 步驟 2：初始化 Document 和 DocumentBuilder

現在，初始化一個新文件和一個 DocumentBuilder 物件。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

這 `DocumentBuilder` 是一個輔助類，可簡化建置文件的過程。

## 步驟 3：啟動表格

接下來，開始使用 `StartTable` 方法。

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

需要插入一個儲存格才能開始表格。

## 步驟 4：套用表格寬度格式

您可以套用影響整個表格的格式。例如設定左縮排：

```csharp
table.LeftIndent = 20.0;
```

## 步驟 5：設定標題行的格式

設定標題行的高度、對齊方式和其他屬性。

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

在此步驟中，我們透過設定背景顏色、字體大小和對齊方式來使標題行脫穎而出。

## 步驟 6：插入附加標題儲存格

為標題行插入更多儲存格：

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## 步驟 7：設定正文行的格式

設定表頭後，設定表體格式：

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## 步驟 8：插入正文行

插入包含內容的正文行：

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

對其他行重複此操作：

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## 步驟9：儲存文檔

最後將文檔儲存到指定目錄：

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

這將建立並保存帶有格式化表格的 Word 文件。

## 結論

就是這樣！透過遵循這些步驟，您可以使用 Aspose.Words for .NET 在 Word 文件中建立格式良好的表格。這個強大的程式庫可以輕鬆地以程式設計方式操作 Word 文檔，從而節省您的時間和精力。

## 常見問題解答

### 什麼是 Aspose.Words for .NET？
Aspose.Words for .NET 是一個功能強大的程式庫，用於以程式設計方式建立、編輯和轉換 Word 文件。

### 我可以對不同的行使用不同的顏色嗎？
是的，您可以對不同的行或儲存格套用不同的格式，包括顏色。

### Aspose.Words for .NET 免費嗎？
Aspose.Words for .NET 是一個付費庫，但你可以獲得 [免費試用](https://releases。aspose.com/).

### 如何獲得 Aspose.Words for .NET 的支援？
您可以從 [Aspose 社群論壇](https://forum。aspose.com/c/words/8).

### 我可以使用 Aspose.Words for .NET 建立其他類型的文件嗎？
是的，Aspose.Words for .NET 支援各種文件格式，包括 PDF、HTML 和 TXT。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}