---
"description": "透過我們的逐步指南了解如何使用 Aspose.Words for .NET 將多個表格中的行合併為一個。"
"linktitle": "合併行"
"second_title": "Aspose.Words文件處理API"
"title": "合併行"
"url": "/zh-hant/net/programming-with-tables/combine-rows/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 合併行

## 介紹

將多個表中的行合併為一個內聚表可能是一項艱鉅的任務。但有了 Aspose.Words for .NET，一切都變得輕而易舉！本指南將引導您完成整個過程，使您能夠輕鬆無縫地合併表格。無論您是經驗豐富的開發人員還是剛起步，您都會發現本教學非常有價值。因此，讓我們深入研究並將這些分散的行轉換為統一的表。

## 先決條件

在進入編碼部分之前，讓我們確保您擁有所需的一切：

1. Aspose.Words for .NET：您可以下載 [這裡](https://releases。aspose.com/words/net/).
2. 開發環境：Visual Studio 或任何其他 .NET 相容 IDE。
3. C# 基礎知識：了解 C# 將會很有幫助。

如果您還沒有 Aspose.Words for .NET，您可以取得 [免費試用](https://releases.aspose.com/) 或購買 [這裡](https://purchase.aspose.com/buy)。如有任何疑問， [支援論壇](https://forum.aspose.com/c/words/8) 是一個很好的起點。

## 導入命名空間

首先，您需要匯入必要的命名空間。這將允許您存取 Aspose.Words 類別和方法。以下是操作方法：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

現在我們已經設定好了一切，讓我們將流程分解為易於遵循的步驟。

## 步驟 1：載入文檔

第一步是載入您的 Word 文件。該文件應包含您想要合併的表格。這是載入文檔的程式碼：

```csharp
// 文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Tables.docx");
```

在此範例中，替換 `"YOUR DOCUMENT DIRECTORY"` 以及您的文件的路徑。

## 第 2 步：識別表

接下來，您需要確定要合併的表格。 Aspose.Words 允許您使用 `GetChild` 方法。方法如下：

```csharp
Table firstTable = (Table) doc.GetChild(NodeType.Table, 0, true);
Table secondTable = (Table) doc.GetChild(NodeType.Table, 1, true);
```

在這段程式碼中，我們從文件中取得第一個和第二個表。

## 步驟 3：將第二個表中的行附加到第一個表中

現在，是時候合併行了。我們將把第二個表中的所有行附加到第一個表。這是使用一個簡單的 while 迴圈完成的：

```csharp
// 將第二個表中的所有行附加到第一個表
while (secondTable.HasChildNodes)
    firstTable.Rows.Add(secondTable.FirstRow);
```

該循環一直持續，直到第二個表中的所有行都新增到第一個表中。

## 步驟 4：刪除第二張表

新增行之後，不再需要第二個表。您可以使用 `Remove` 方法：

```csharp
secondTable.Remove();
```

## 步驟5：儲存文檔

最後儲存修改後的文件。此步驟可確保您的變更寫入檔案：

```csharp
doc.Save(dataDir + "WorkingWithTables.CombineRows.docx");
```

就是這樣！您已成功使用 Aspose.Words for .NET 將兩個表格中的行合併為一個。

## 結論

將多個表中的行合併為一個表格可以大幅簡化文件處理任務。使用 Aspose.Words for .NET，這項任務變得簡單又有效率。透過遵循本逐步指南，您可以輕鬆合併表格並簡化工作流程。

如果您需要更多資訊或有任何疑問， [Aspose.Words 文檔](https://reference.aspose.com/words/net/) 是一個極好的資源。您還可以探索購買選項 [這裡](https://purchase.aspose.com/buy) 或得到 [臨時執照](https://purchase.aspose.com/temporary-license/) 用於測試。

## 常見問題解答

### 我可以合併不同列數的表格嗎？

是的，Aspose.Words 允許您合併表格，即使它們具有不同的列數和寬度。

### 合併後行的格式會發生什麼變化？

當行附加到第一個表時，行的格式將被保留。

### 可以合併兩個以上的表格嗎？

是的，您可以透過對每個附加表重複這些步驟來合併多個表。

### 我可以針對多個文件自動執行此程序嗎？

絕對地！您可以建立一個腳本來自動執行多個文件的此過程。

### 如果我遇到問題，我可以在哪裡獲得協助？

這 [Aspose.Words 支援論壇](https://forum.aspose.com/c/words/8) 是獲得協助和尋找常見問題解決方案的好地方。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}