---
title: 直接插入表格
linktitle: 直接插入表格
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 將表格直接插入 Word 文件中。請按照我們詳細的逐步指南來簡化您的文件建立。
weight: 10
url: /zh-hant/net/programming-with-tables/insert-table-directly/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 直接插入表格

## 介紹
以程式設計方式建立表格可能是一個相當大的挑戰，尤其是在處理複雜的文件結構時。但別擔心，我們會為您一一解答！在本指南中，我們將逐步介紹使用 Aspose.Words for .NET 將表格直接插入 Word 文件中的步驟。無論您是經驗豐富的開發人員還是新手，本教學都將幫助您輕鬆掌握流程。

## 先決條件

在深入研究程式碼之前，讓我們確保您擁有開始使用所需的一切。這是一個快速清單：

1.  Aspose.Words for .NET 程式庫：請確定您已下載並安裝 Aspose.Words for .NET 程式庫。您可以從[下載頁面](https://releases.aspose.com/words/net/).
2. 開發環境：Visual Studio等開發環境。
3. C# 基礎知識：了解 C# 程式設計的基礎知識。
4. 文檔目錄：儲存文檔的目錄路徑。

滿足這些先決條件後，您就可以開始編碼了！

## 導入命名空間

首先，讓我們導入必要的名稱空間。這些命名空間將為我們提供處理 Word 文件所需的類別和方法。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

現在我們已經有了命名空間，讓我們繼續令人興奮的部分——建立表格並將其直接插入到 Word 文件中。

## 第 1 步：設定文檔

讓我們先設定一個新的 Word 文件。這是我們的表格將被插入的地方。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

此程式碼初始化一個新的 Word 文件。你需要更換`"YOUR DOCUMENT DIRECTORY"`與文檔目錄的實際路徑。

## 第 2 步：建立表格對象

接下來，我們建立表物件。這是我們定義表結構的地方。

```csharp
//我們首先建立表物件。注意我們必須傳遞文檔對象
//到每個節點的構造函數。這是因為我們創建的每個節點都必須屬於
//到某個文檔。
Table table = new Table(doc);
doc.FirstSection.Body.AppendChild(table);
```

在這裡，我們建立一個新表並將其附加到文件第一部分的正文中。

## 第 3 步：新增行和儲存格

表格由行和單元格組成。讓我們逐步加入這些元素。

### 新增行

```csharp
//在這裡，我們可以呼叫 EnsureMinimum 來為我們建立行和單元格。使用這個方法
//確保指定的節點有效。在這種情況下，有效的表格應至少具有一行和一個儲存格。
//相反，我們將自己處理創建行和表。
//如果我們在演算法中建立表，這將是最好的方法。
Row row = new Row(doc);
row.RowFormat.AllowBreakAcrossPages = true;
table.AppendChild(row);
```

此程式碼建立一個新行並將其附加到我們的表中。

### 將儲存格新增至行中

現在，讓我們在行中新增一些儲存格。 

```csharp
Cell cell = new Cell(doc);
cell.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
cell.CellFormat.Width = 80;
cell.AppendChild(new Paragraph(doc));
cell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 1 Text"));
row.AppendChild(cell);
```

在此程式碼片段中，我們建立一個儲存格，將其背景顏色設為淺藍色，並定義其寬度。然後，我們在儲存格上新增一個段落和一個段落來儲存文字。

## 第四步：克隆細胞

為了加快添加單元的過程，我們可以複製現有單元。

```csharp
//然後，我們將對錶中的其他單元格和行重複該過程。
//我們還可以透過複製現有的單元格和行來加快速度。
row.AppendChild(cell.Clone(false));
row.LastCell.AppendChild(new Paragraph(doc));
row.LastCell.FirstParagraph.AppendChild(new Run(doc, "Row 1, Cell 2 Text"));
```

此程式碼複製現有儲存格並將其新增至該行。然後，我們為新儲存格新增一個段落和一個運行。

## 第 5 步：套用自動調整設定

最後，讓我們對表格應用自動調整設置，以確保列具有固定寬度。

```csharp
//我們現在可以套用任何自動調整設定。
table.AutoFit(AutoFitBehavior.FixedColumnWidths);
```

## 第 6 步：儲存文檔

表格完全設定完畢後，就可以儲存文件了。

```csharp
doc.Save(dataDir + "WorkingWithTables.InsertTableDirectly.docx");
```

此程式碼保存插入了表格的文件。

## 結論

恭喜！您已使用 Aspose.Words for .NET 成功將表格直接插入 Word 文件中。此過程可用於以程式設計方式建立複雜的表格，使您的文件自動化任務變得更加容易。無論您是產生報告、發票或任何其他文件類型，了解如何操作表格都是一項至關重要的技能。

## 常見問題解答

### 如何下載 Aspose.Words for .NET？
您可以從以下位置下載 Aspose.Words for .NET[下載頁面](https://releases.aspose.com/words/net/).

### 可以在購買前試用 Aspose.Words for .NET 嗎？
是的，您可以請求[免費試用](https://releases.aspose.com/)在購買之前評估圖書館。

### 如何購買 Aspose.Words for .NET？
您可以從以下位置購買 Aspose.Words for .NET[購買頁面](https://purchase.aspose.com/buy).

### 在哪裡可以找到 Aspose.Words for .NET 的文檔？
文件可用[這裡](https://reference.aspose.com/words/net/).

### 如果我在使用 Aspose.Words for .NET 時需要支援怎麼辦？
如需支持，您可以訪問[Aspose.Words 論壇](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
