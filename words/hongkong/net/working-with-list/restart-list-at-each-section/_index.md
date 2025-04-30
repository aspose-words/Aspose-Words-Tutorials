---
"description": "了解如何使用 Aspose.Words for .NET 在 Word 文件的每個部分重新啟動清單。按照我們詳細的逐步指南有效地管理清單。"
"linktitle": "在每個部分重新啟動列表"
"second_title": "Aspose.Words文件處理API"
"title": "在每個部分重新啟動列表"
"url": "/zh-hant/net/working-with-list/restart-list-at-each-section/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在每個部分重新啟動列表

## 介紹

創建結構化且組織良好的文件有時就像解決一個複雜的難題。這個難題的一部分是有效地管理列表，特別是當您希望它們在每個部分重新啟動時。使用 Aspose.Words for .NET，您可以無縫地實現這一點。讓我們深入了解如何使用 Aspose.Words for .NET 在 Word 文件的每個部分重新啟動清單。

## 先決條件

在開始之前，請確保您具備以下條件：

1. Aspose.Words for .NET：從下載並安裝最新版本 [Aspose 版本](https://releases.aspose.com/words/net/) 頁。
2. .NET 環境：安裝 .NET 後設定您的開發環境。
3. 對 C# 的基本了解：建議熟悉 C# 程式語言。
4. Aspose 許可證：您可以選擇 [臨時執照](https://purchase.aspose.com/temporary-license/) 如果你沒有。

## 導入命名空間

在編寫程式碼之前，請確保導入必要的命名空間：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

現在，讓我們將這個過程分解為多個步驟，以便於遵循。

## 步驟 1：初始化文檔

首先，您需要建立一個新的文檔實例。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
```

## 步驟 2：新增編號列表

接下來，在文件中新增編號清單。此清單將遵循預設編號格式。

```csharp
doc.Lists.Add(ListTemplate.NumberDefault);
```

## 步驟 3：存取清單並設定重啟屬性

檢索剛剛建立的清單並設定其 `IsRestartAtEachSection` 財產 `true`。這確保清單在每個新部分重新開始編號。

```csharp
List list = doc.Lists[0];
list.IsRestartAtEachSection = true;
```

## 步驟 4：建立文件產生器並關聯列表

創建一個 `DocumentBuilder` 將內容插入文件並將其與清單關聯。

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

## 步驟6：儲存文檔

最後，使用適當的選項儲存文件以確保合規。

```csharp
OoxmlSaveOptions options = new OoxmlSaveOptions { Compliance = OoxmlCompliance.Iso29500_2008_Transitional };
doc.Save(dataDir + "WorkingWithList.RestartListAtEachSection.docx", options);		
```

## 結論

就是這樣！遵循這些步驟，您可以使用 Aspose.Words for .NET 輕鬆地在 Word 文件的每個部分重新啟動清單。此功能對於建立需要單獨部分並具有自己的清單編號的結構良好的文件非常有用。使用 Aspose.Words，處理此類任務變得輕而易舉，讓您專注於製作高品質的內容。

## 常見問題解答

### 我可以在每個部分重新啟動不同清單類型的清單嗎？
是的，Aspose.Words for .NET 可讓您重新啟動各種清單類型，包括項目符號和編號清單。

### 如果我想自訂編號格式怎麼辦？
您可以透過修改 `ListTemplate` 建立清單時的屬性。

### 清單中的項目數量有限制嗎？
不，使用 Aspose.Words for .NET 時，清單中的項目數量沒有具體限制。

### 我可以在 PDF 等其他文件格式中使用此功能嗎？
是的，您可以使用 Aspose.Words 將 Word 文件轉換為 PDF 等其他格式，同時保留清單結構。

### 如何免費試用 Aspose.Words for .NET？
您可以從 [Aspose 版本](https://releases.aspose.com/) 頁。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}