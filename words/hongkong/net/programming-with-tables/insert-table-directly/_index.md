---
"description": "了解如何使用 Aspose.Words for .NET 將表格直接插入 Word 文件。請按照我們詳細的逐步指南來簡化您的文件建立。"
"linktitle": "直接插入表格"
"second_title": "Aspose.Words文件處理API"
"title": "直接插入表格"
"url": "/zh-hant/net/programming-with-tables/insert-table-directly/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 直接插入表格

## 介紹
以程式設計方式建立表格可能是一個相當大的挑戰，特別是在處理複雜的文件結構時。但別擔心，我們會為您分解！在本指南中，我們將介紹使用 Aspose.Words for .NET 將表格直接插入 Word 文件的步驟。無論您是經驗豐富的開發人員還是剛起步，本教學都將幫助您輕鬆掌握流程。

## 先決條件

在深入研究程式碼之前，請確保您擁有開始所需的一切。以下是一份快速清單：

1. Aspose.Words for .NET 程式庫：請確定您已下載並安裝了 Aspose.Words for .NET 程式庫。您可以從 [下載頁面](https://releases。aspose.com/words/net/).
2. 開發環境：類似 Visual Studio 的開發環境。
3. C# 基礎知識：了解 C# 程式設計的基礎知識。
4. 文檔目錄：儲存文檔的目錄路徑。

滿足這些先決條件後，您就可以開始編碼了！

## 導入命名空間

首先，讓我們導入必要的命名空間。這些命名空間將為我們提供處理 Word 文件所需的類別和方法。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

現在我們已經有了命名空間，讓我們進入令人興奮的部分 - 直接在 Word 文件中建立和插入表格。

## 步驟1：設定文檔

讓我們先設定一個新的 Word 文件。這就是我們的表格插入的地方。

```csharp
// 文檔目錄的路徑 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

此程式碼初始化一個新的 Word 文件。你需要更換 `"YOUR DOCUMENT DIRECTORY"` 使用您的文件目錄的實際路徑。

## 步驟2：建立表對象

接下來，我們建立表物件。我們將在這裡定義表的結構。

```csharp
// 我們首先建立表物件。注意，我們必須傳遞文檔對象
// 到每個節點的構造函數。這是因為我們創建的每個節點都必須屬於
// 到一些文件。
Table table = new Table(doc);
doc.FirstSection.Body.AppendChild(table);
```

在這裡，我們建立一個新表並將其附加到文件第一部分的正文中。

## 步驟 3：新增行和儲存格

表格由行和單元格組成。讓我們一步一步地加入這些元素。

### 新增行

```csharp
// 在這裡我們可以呼叫 EnsureMinimum 來為我們建立行和單元格。此方法
// 確保指定的節點有效。在這種情況下，有效的表格應該至少有一行和一個儲存格。
// 相反，我們將自己創建行和表。
// 如果我們在演算法內部創建一個表，這將是最好的方法。
Row row = new Row(doc);
row.RowFormat.AllowBreakAcrossPages = true;
table.AppendChild(row);
```

此程式碼建立一個新行並將其附加到我們的表中。

### 在行中新增儲存格

現在，讓我們在行中新增一些儲存格。 

```csharp
Cell cell = new Cell(doc);
cell.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
cell.CellFormat.Width = 80;
cell.AppendChild(new Paragraph(doc));
cell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 1 Text"));
row.AppendChild(cell);
```

在此程式碼片段中，我們建立一個儲存格，將其背景顏色設為淺藍色，並定義其寬度。然後，我們向單元格添加一個段落和一個運行來保存我們的文本。

## 步驟4：克隆細胞

為了加快添加細胞的過程，我們可以克隆現有的細胞。

```csharp
// 然後，我們將對表格中的其他儲存格和行重複該過程。
// 我們還可以透過複製現有的單元格和行來加快速度。
row.AppendChild(cell.Clone(false));
row.LastCell.AppendChild(new Paragraph(doc));
row.LastCell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 2 Text"));
```

此程式碼複製現有儲存格並將其新增至行中。然後我們向新單元格添加一個段落和一個運行。

## 步驟5：套用自動調整設定

最後，讓我們將自動適應設定套用到表格以確保列具有固定的寬度。

```csharp
// 我們現在可以應用任何自動適應設定。
table.AutoFit(AutoFitBehavior.FixedColumnWidths);
```

## 步驟6：儲存文檔

當我們的表格完全設定好後，就該儲存文件了。

```csharp
doc.Save(dataDir + "WorkingWithTables.InsertTableDirectly.docx");
```

此程式碼保存了插入表格的文件。

## 結論

恭喜！您已成功使用 Aspose.Words for .NET 將表格直接插入 Word 文件。此過程可用於以程式設計方式建立複雜的表格，從而使您的文件自動化任務變得更加容易。無論您產生報告、發票或任何其他文件類型，了解如何操作表格都是一項關鍵技能。

## 常見問題解答

### 如何下載 Aspose.Words for .NET？
您可以從 [下載頁面](https://releases。aspose.com/words/net/).

### 可以在購買前試用 Aspose.Words for .NET 嗎？
是的，您可以申請 [免費試用](https://releases.aspose.com/) 在購買之前對圖書館進行評估。

### 如何購買 Aspose.Words for .NET？
您可以從 [購買頁面](https://purchase。aspose.com/buy).

### 在哪裡可以找到 Aspose.Words for .NET 的文檔？
文件可用 [這裡](https://reference。aspose.com/words/net/).

### 如果我在使用 Aspose.Words for .NET 時需要支援怎麼辦？
如需支持，您可以訪問 [Aspose.Words論壇](https://forum。aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}