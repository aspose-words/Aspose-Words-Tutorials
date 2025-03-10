---
title: 分割表
linktitle: 分割表
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 分割 Word 文件中的表格。我們的逐步指南使餐桌管理變得簡單且有效率。
weight: 10
url: /zh-hant/net/programming-with-tables/split-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 分割表

## 介紹

您是否曾經發現自己正在處理 Word 文件中的一個大表格，並希望將其拆分為兩個更小、更易於管理的表格？今天，我們將深入探討如何使用 Aspose.Words for .NET 來實現這一目標。無論您是處理大量資料表還是複雜的文件結構，分割表都可以幫助增強可讀性和組織性。讓我們來探索使用 Aspose.Words for .NET 分割表格的逐步流程。

## 先決條件

在我們開始學習本教學之前，請確保您具備以下條件：

1.  Aspose.Words for .NET 程式庫：請確定您已下載並安裝 Aspose.Words for .NET 程式庫。您可以從[Aspose 發佈頁面](https://releases.aspose.com/words/net/).
2. 開發環境：建置支援.NET框架的開發環境，例如Visual Studio。
3. 範例文件：準備一個 Word 文件（`Tables.docx`）至少有一個表格來應用拆分操作。

## 導入命名空間

首先，將必要的命名空間匯入到您的專案中。這允許您存取 Aspose.Words 提供的類別和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## 第 1 步：載入文檔

讓我們先載入包含要拆分的表的文檔。確保指定文件的正確路徑。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

## 第 2 步：確定要拆分的表

接下來，識別並檢索您想要拆分的表。在此範例中，我們將定位文件中的第一個表。

```csharp
Table firstTable = (Table)doc.GetChild(NodeType.Table, 0, true);
```

## 步驟 3：選擇要分割的行

確定要拆分錶的行。在這裡，我們在第三行（含）處拆分錶格。

```csharp
Row row = firstTable.Rows[2];
```

## 步驟4：建立一個新的表容器

建立一個新的表容器來保存將從原始表中移動的行。

```csharp
Table table = (Table)firstTable.Clone(false);
```

## 第 5 步：插入新表容器

將新表格容器插入文件中原始表格之後。

```csharp
firstTable.ParentNode.InsertAfter(table, firstTable);
```

## 步驟6：新增緩衝段落

在兩個表之間新增一個緩衝區段落以確保它們保持獨立。

```csharp
firstTable.ParentNode.InsertAfter(new Paragraph(doc), firstTable);
```

## 步驟 7：將行移至新表

將行從原始表移至新表容器。此循環將繼續，直到指定的行（包括）被移動。

```csharp
Row currentRow;
do
{
    currentRow = firstTable.LastRow;
    table.PrependChild(currentRow);
} while (currentRow != row);
```

## 第 8 步：儲存文檔

最後，儲存修改後的文件並拆分錶格。

```csharp
doc.Save(dataDir + "WorkingWithTables.SplitTable.docx");
```

## 結論

現在你就擁有了！透過執行下列步驟，您可以使用 Aspose.Words for .NET 輕鬆分割 Word 文件中的表格。此方法可幫助您更有效地管理大型表格，從而提高文件的可讀性和組織性。嘗試一下，看看它如何簡化您在 Word 文件中使用表格的工作。

## 常見問題解答

### 我可以將一個表拆分為多行嗎？
是的，您可以透過對每個拆分點重複此程序來將表拆分為多行。

### 原始表格的格式會發生什麼變化？
新表繼承了原始表的格式。任何特定的格式變更都可以根據需要套用於新表。

### 是否可以將表重新合併在一起？
是的，您可以透過使用類似的方法將行從一個表移動到另一個表來合併表。

### 此方法適用於巢狀表嗎？
是的，Aspose.Words for .NET 也支援巢狀資料表的操作。

### 我可以針對多個文件自動執行此程序嗎？
絕對地！您可以建立腳本或應用程式來自動執行多個文件的表拆分過程。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
