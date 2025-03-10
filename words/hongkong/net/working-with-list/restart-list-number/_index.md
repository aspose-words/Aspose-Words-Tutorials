---
title: 重新啟動清單編號
linktitle: 重新啟動清單編號
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 重新啟動 Word 文件中的清單編號。這本詳細的 2000 字指南涵蓋了您需要了解的所有內容，從設定到高級自訂。
weight: 10
url: /zh-hant/net/working-with-list/restart-list-number/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 重新啟動清單編號

## 介紹

您是否希望掌握使用 Aspose.Words for .NET 在 Word 文件中進行清單操作的藝術？嗯，您來對地方了！在本教程中，我們將深入探討重新啟動清單編號，這是一個很棒的功能，可以將您的文件自動化技能提升到一個新的水平。繫好安全帶，讓我們開始吧！

## 先決條件

在我們進入程式碼之前，讓我們確保您擁有所需的一切：

1.  Aspose.Words for .NET：您需要安裝 Aspose.Words for .NET。如果您還沒有安裝，您可以[在這裡下載](https://releases.aspose.com/words/net/).
2. 開發環境：確保您有合適的開發環境，例如 Visual Studio。
3. C# 的基本知識：對 C# 的基本了解將幫助您遵循本教學。

## 導入命名空間

首先，讓我們導入必要的名稱空間。這些對於存取 Aspose.Words 功能至關重要。

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

現在，讓我們將該過程分解為易於遵循的步驟。我們將涵蓋從建立清單到重新編號的所有內容。

## 第 1 步：設定您的文件和產生器

在開始操作清單之前，您需要一個文件和一個 DocumentBuilder。 DocumentBuilder 是為文件添加內容的首選工具。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 第 2 步：建立並自訂您的第一個列表

接下來，我們將基於模板建立一個清單並自訂其外觀。在此範例中，我們使用括號的阿拉伯數字格式。

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

在這裡，我們將字體顏色設為紅色並將文字向右對齊。

## 第 3 步：將項目新增到您的第一個清單中

準備好清單後，就可以再增加一些項目了。文檔產生器的`ListFormat.List`屬性有助於將清單格式應用於文字。

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## 第 4 步：重新開始清單編號

若要重複使用該清單並重新開始編號，您需要建立原始清單的副本。這允許您獨立修改新清單。

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

在此範例中，新清單從數字 10 開始。

## 第 5 步：將項目新增至新列表

就像以前一樣，將項目新增到新清單中。這示範了清單在指定的編號處重新啟動。

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## 第 6 步：儲存您的文檔

最後，將文檔儲存到指定目錄。

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## 結論

使用 Aspose.Words for .NET 重新啟動 Word 文件中的清單編號非常簡單且非常有用。無論您是要產生報告、建立結構化文檔，還是只是需要更好地控制列表，這種技術都能滿足您的需求。

## 常見問題解答

### 除了 NumberArabicParenthesis 之外，我還可以使用其他清單範本嗎？

絕對地！ Aspose.Words 提供各種清單模板，例如項目符號、字母、羅馬數字等。您可以選擇最適合您需求的一種。

### 如何更改列表等級？

您可以透過修改來更改列表級別`ListLevels`財產。例如，`list1.ListLevels[1]`將指列表的第二級。

### 我可以從任何號碼重新開始編號嗎？

是的，您可以使用以下命令將起始數字設定為任何整數值`StartAt`列表級別的屬性。

### 是否可以為不同的清單等級設定不同的格式？

的確！每個清單層級都可以有自己的格式設置，例如字體、對齊方式和編號樣式。

### 如果我想繼續從以前的清單編號而不是重新啟動怎麼辦？

如果您想繼續編號，則無需建立清單的副本。只需繼續將項目新增至原始清單即可。



{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
