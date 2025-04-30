---
"description": "了解如何使用 Aspose.Words for .NET 防止表格在 Word 文件中跨頁斷裂。請按照我們的指南來維護專業、可讀的文件。"
"linktitle": "保持桌子齊整"
"second_title": "Aspose.Words文件處理API"
"title": "保持桌子齊整"
"url": "/zh-hant/net/programming-with-tables/keep-table-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 保持桌子齊整

## 介紹

當 Word 文件中的表格跨越兩頁時，您是否感到沮喪？這就像您精心佈置的訊息突然決定中途休息一下！將表格放在同一頁上對於可讀性和演示效果至關重要。無論是報告、專案提案或個人文件，分割表格都會造成不協調的感覺。幸運的是，Aspose.Words for .NET 有一個巧妙的方法來解決這個問題。在本教程中，我們將逐步介紹如何保持表格完好無損且外觀清晰。讓我們開始吧！

## 先決條件

在開始之前，請確保您具備以下條件：

1. Aspose.Words for .NET - 如果您尚未安裝，可以從 [這裡](https://releases。aspose.com/words/net/).
2. 帶有表格的 Word 文件 - 我們將使用包含跨越多頁的表格的範例文件。
3. C# 基礎知識 - 本教學假設您對 C# 程式設計有基本的了解。

## 導入命名空間

首先，讓我們導入必要的命名空間。這將使我們能夠存取 Aspose.Words for .NET 所需的類別和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

讓我們將這個過程分解為簡單易懂的步驟。我們將從載入文件開始，到將更新後的文件與表格儲存在一起為止。

## 步驟 1：載入文檔

要使用 Word 文檔，我們首先需要載入它。我們將使用 `Document` 為此課程。

```csharp
// 文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## 第 2 步：訪問表

接下來，我們需要將我們想要保留的表格放在一起。我們假設它是文件中的第一個表格。

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## 步驟 3：設定段落的 KeepWithNext

為了防止表格跨頁斷裂，我們需要設置 `KeepWithNext` 表格中每個段落的屬性，最後一行的最後幾段除外。

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
    foreach (Paragraph para in cell.Paragraphs)
    {
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
    }
}
```

## 步驟4：儲存文檔

最後，我們儲存更新後的文件。這將應用我們的更改並確保表格保持在一頁上。

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

## 結論

就是這樣！只需幾行程式碼，您就可以防止表格在 Word 文件中跨頁分裂。這個簡單而有效的解決方案可確保您的表格保持整潔和專業，從而增強文件的可讀性。 Aspose.Words for .NET 讓處理此類格式問題變得輕而易舉，讓您可以專注於創建精彩的內容。

## 常見問題解答

### 我可以使用此方法將多個表放在一起嗎？  
是的，您可以透過遍歷文件中的每個表將相同的邏輯套用到多個表。

### 如果我的表格太大，無法放在一頁上怎麼辦？  
如果表格太大而無法放在一頁上，它仍然會跨越頁面。這種方法可以確保較小的表保持完整而不會分裂。

### 有沒有辦法自動對文件中的所有表格進行此操作？  
是的，您可以循環遍歷文件中的所有表格並套用 `KeepWithNext` 每個段落的屬性。

### 我需要 Aspose.Words for .NET 的付費授權嗎？  
您可以從以下位置開始免費試用 [這裡](https://releases.aspose.com/)，但為了獲得全部功能，建議購買付費許可證。

### 我可以將其他格式應用於表格同時保持它們一致嗎？  
絕對地！您可以根據需要格式化表格，同時確保它們保持在一頁上。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}