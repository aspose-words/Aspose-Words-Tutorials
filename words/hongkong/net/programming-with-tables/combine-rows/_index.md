---
title: 合併行
linktitle: 合併行
second_title: Aspose.Words 文件處理 API
description: 透過我們的逐步指南，了解如何使用 Aspose.Words for .NET 將多個表格中的行合併為一個表格。
weight: 10
url: /zh-hant/net/programming-with-tables/combine-rows/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 合併行

## 介紹

將多個表中的行合併到單一內聚表中可能是一項艱鉅的任務。但使用 Aspose.Words for .NET，一切變得輕而易舉！本指南將引導您完成整個過程，讓您輕鬆無縫地合併表格。無論您是經驗豐富的開發人員還是剛入門，您都會發現本教學非常有價值。因此，讓我們深入研究並將這些分散的行轉換為統一的表。

## 先決條件

在我們進入編碼部分之前，讓我們確保您擁有所需的一切：

1.  Aspose.Words for .NET：您可以下載它[這裡](https://releases.aspose.com/words/net/).
2. 開發環境：Visual Studio 或任何其他 .NET 相容 IDE。
3. C# 基礎：了解 C# 將大有裨益。

如果您還沒有 Aspose.Words for .NET，您可以取得[免費試用](https://releases.aspose.com/)或購買它[這裡](https://purchase.aspose.com/buy)。如有任何疑問，[支援論壇](https://forum.aspose.com/c/words/8)是一個很好的起點。

## 導入命名空間

首先，您需要匯入必要的名稱空間。這將允許您存取 Aspose.Words 類別和方法。操作方法如下：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

現在我們已經完成了所有設置，讓我們將該過程分解為易於遵循的步驟。

## 第 1 步：載入您的文檔

第一步是載入 Word 文件。該文件應包含您要合併的表格。這是載入文檔的程式碼：

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Tables.docx");
```

在此範例中，替換`"YOUR DOCUMENT DIRECTORY"`以及您的文件的路徑。

## 第 2 步：識別表格

接下來，您需要確定要合併的表格。 Aspose.Words 可讓您使用以下方式從文件中取得表格`GetChild`方法。方法如下：

```csharp
Table firstTable = (Table) doc.GetChild(NodeType.Table, 0, true);
Table secondTable = (Table) doc.GetChild(NodeType.Table, 1, true);
```

在此程式碼中，我們從文件中取得第一個和第二個表。

## 步驟 3：將第二個表格中的行追加到第一個表格中

現在，是時候合併行了。我們將把第二個表中的所有行追加到第一個表中。這是使用一個簡單的 while 迴圈完成的：

```csharp
//將第二個表中的所有行追加到第一個表中
while (secondTable.HasChildNodes)
    firstTable.Rows.Add(secondTable.FirstRow);
```

此循環將繼續，直到第二個表中的所有行都新增到第一個表中。

## 步驟 4：刪除第二個表

附加行後，不再需要第二個表。您可以使用以下命令將其刪除`Remove`方法：

```csharp
secondTable.Remove();
```

## 第 5 步：儲存文檔

最後儲存修改後的文件。此步驟可確保您的變更寫入檔案：

```csharp
doc.Save(dataDir + "WorkingWithTables.CombineRows.docx");
```

就是這樣！您已使用 Aspose.Words for .NET 成功將兩個表格中的行合併為一個表格。

## 結論

將多個表中的行合併到一個表中可以顯著簡化文件處理任務。透過 Aspose.Words for .NET，這項任務變得簡單又有效率。透過遵循此逐步指南，您可以輕鬆合併表格並簡化您的工作流程。

如果您需要更多資訊或有任何疑問，[Aspose.Words 文檔](https://reference.aspose.com/words/net/)是一個極好的資源。您還可以探索購買選項[這裡](https://purchase.aspose.com/buy)或得到一個[臨時執照](https://purchase.aspose.com/temporary-license/)用於測試。

## 常見問題解答

### 我可以合併不同列數的表格嗎？

是的，Aspose.Words 允許您合併表格，即使它們具有不同的列數和寬度。

### 合併後行的格式會發生什麼變化？

當行附加到第一個表時，行的格式將被保留。

### 是否可以合併兩個以上的表格？

是的，您可以透過對每個附加表重複這些步驟來合併多個表。

### 我可以針對多個文件自動執行此程序嗎？

絕對地！您可以建立一個腳本來自動執行多個文件的此過程。

### 如果遇到問題，我可以從哪裡獲得協助？

這[Aspose.Words 支援論壇](https://forum.aspose.com/c/words/8)是獲得幫助並找到常見問題解決方案的好地方。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
