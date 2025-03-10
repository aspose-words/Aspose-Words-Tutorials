---
title: 在每個部分重新啟動列表
linktitle: 在每個部分重新啟動列表
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 重新啟動 Word 文件中每個部分的清單。請遵循我們詳細的逐步指南來有效管理清單。
weight: 10
url: /zh-hant/net/working-with-list/restart-list-at-each-section/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在每個部分重新啟動列表

## 介紹

創建結構化且組織良好的文件有時感覺就像在解決一個複雜的難題。其中一個難題是有效管理列表，特別是當您希望它們在每個部分重新啟動時。透過 Aspose.Words for .NET，您可以無縫地完成此任務。讓我們深入了解如何使用 Aspose.Words for .NET 在 Word 文件的每個部分重新啟動清單。

## 先決條件

在我們開始之前，請確保您具備以下條件：

1.  Aspose.Words for .NET：從以下位置下載並安裝最新版本[Aspose 發布](https://releases.aspose.com/words/net/)頁。
2. .NET 環境：設定安裝了 .NET 的開發環境。
3. 對 C# 的基本了解：建議熟悉 C# 程式語言。
4.  Aspose 許可證：您可以選擇[臨時執照](https://purchase.aspose.com/temporary-license/)如果你沒有的話。

## 導入命名空間

在編寫程式碼之前，請確保導入必要的命名空間：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

現在，讓我們將該過程分解為多個步驟，以便於遵循。

## 步驟1：初始化文檔

首先，您需要建立一個新的文檔實例。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
```

## 第 2 步：新增編號列表

接下來，將編號清單新增至文件。此清單將遵循預設的編號格式。

```csharp
doc.Lists.Add(ListTemplate.NumberDefault);
```

## 步驟 3：存取清單並設定重啟屬性

檢索您剛剛建立的清單並設定其`IsRestartAtEachSection`財產給`true`。這可確保清單在每個新部分重新編號。

```csharp
List list = doc.Lists[0];
list.IsRestartAtEachSection = true;
```

## 步驟 4：建立文件產生器並關聯列表

創建一個`DocumentBuilder`將內容插入文件並將其與清單關聯。

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.ListFormat.List = list;
```

## 步驟 5：新增清單項目並插入分節符

現在，將項目新增至清單。為了說明重新啟動功能，我們將在一定數量的項目後插入分節符。

```csharp
for (int i = 1; i < 45; i++)
{
    builder.Writeln($"List item {i}");

    if (i == 15)
        builder.InsertBreak(BreakType.SectionBreakNewPage);
}
```

## 第 6 步：儲存文檔

最後，使用適當的選項儲存文件以確保合規性。

```csharp
OoxmlSaveOptions options = new OoxmlSaveOptions { Compliance = OoxmlCompliance.Iso29500_2008_Transitional };
doc.Save(dataDir + "WorkingWithList.RestartListAtEachSection.docx", options);		
```

## 結論

現在你就擁有了！透過執行這些步驟，您可以使用 Aspose.Words for .NET 輕鬆地重新啟動 Word 文件中每個部分的清單。此功能對於建立結構良好的文件非常有用，這些文件需要具有自己的清單編號的單獨部分。透過 Aspose.Words，處理此類任務變得輕而易舉，讓您專注於製作高品質的內容。

## 常見問題解答

### 我可以在每個部分為不同的清單類型重新啟動清單嗎？
是的，Aspose.Words for .NET 可讓您重新啟動各種清單類型，包括項目符號清單和編號清單。

### 如果我想自訂編號格式怎麼辦？
您可以透過修改來自訂編號格式`ListTemplate`建立清單時的屬性。

### 清單中的項目數量有限制嗎？
不，使用 Aspose.Words for .NET 的清單中的項目數量沒有具體限制。

### 我可以在 PDF 等其他文件格式中使用此功能嗎？
是的，您可以使用 Aspose.Words 將 Word 文件轉換為 PDF 等其他格式，同時保留清單結構。

### 如何獲得 Aspose.Words for .NET 的免費試用版？
您可以從以下網站獲得免費試用[Aspose 發布](https://releases.aspose.com/)頁。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
