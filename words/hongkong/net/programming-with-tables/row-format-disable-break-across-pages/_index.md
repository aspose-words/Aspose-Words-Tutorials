---
"description": "了解如何使用 Aspose.Words for .NET 停用 Word 文件中跨頁的換行符，以保持表格的可讀性和格式。"
"linktitle": "行格式停用跨頁"
"second_title": "Aspose.Words文件處理API"
"title": "行格式停用跨頁"
"url": "/zh-hant/net/programming-with-tables/row-format-disable-break-across-pages/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 行格式停用跨頁

## 介紹

在 Word 文件中使用表格時，您可能希望確保行不會跨頁，這對於保持文件的可讀性和格式至關重要。 Aspose.Words for .NET 提供了一個簡單的方法來停用跨頁的換行。

在本教學中，我們將引導您完成使用 Aspose.Words for .NET 在 Word 文件中停用跨頁換行的過程。

## 先決條件

在開始之前，請確保您符合以下先決條件：
- 已安裝 Aspose.Words for .NET 程式庫。
- 包含跨多頁表格的 Word 文件。

## 導入命名空間

首先，在您的專案中匯入必要的命名空間：

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## 步驟 1：載入文檔

載入包含跨越多頁的表格的文件。

```csharp
// 文檔目錄的路徑 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## 第 2 步：訪問表

存取文件中的第一個表。這假設您要修改的表是文件中的第一個表。

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## 步驟 3：停用所有行的跨頁功能

循環遍歷表中的每一行並設置 `AllowBreakAcrossPages` 財產 `false`。這確保行不會跨頁斷開。

```csharp
// 停用表格中所有行的跨頁斷行功能。
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## 步驟4：儲存文檔

將修改後的文件儲存到指定的目錄中。

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## 結論

在本教學中，我們示範如何使用 Aspose.Words for .NET 停用 Word 文件中跨頁的換行符號。透過遵循上面概述的步驟，您可以確保表格行保持完整併且不會跨頁面分割，從而保持文件的可讀性和格式。

## 常見問題解答

### 我可以針對特定行（而不是所有行）停用跨頁換行嗎？  
是的，您可以透過存取所需行並設定其 `AllowBreakAcrossPages` 財產 `false`。

### 此方法對具有合併儲存格的表格有效嗎？  
是的，此方法適用於具有合併儲存格的表格。該物業 `AllowBreakAcrossPages` 適用於整行，無論儲存格是否合併。

### 如果表格嵌套在另一個表中，此方法是否有效？  
是的，您可以以相同的方式存取和修改巢狀表。確保透過索引或其他屬性正確引用巢狀表。

### 如何檢查某一行是否允許跨頁？  
您可以透過訪問 `AllowBreakAcrossPages` 的財產 `RowFormat` 並檢查其值。

### 有沒有辦法將此設定套用到文件中的所有表格？  
是的，您可以循環遍歷文件中的所有表格並將此設定套用至每個表格。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}