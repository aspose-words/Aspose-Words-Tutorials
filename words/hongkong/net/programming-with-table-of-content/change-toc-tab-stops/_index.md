---
title: 更改 Word 文件中的目錄製表位
linktitle: 更改 Word 文件中的目錄製表位
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 變更 Word 文件中的 TOC 製表位。本逐步指南將協助您建立具有專業外觀的目錄。
weight: 10
url: /zh-hant/net/programming-with-table-of-content/change-toc-tab-stops/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 更改 Word 文件中的目錄製表位

## 介紹

有沒有想過如何讓 Word 文件中的目錄 (TOC) 變得生動活潑？也許您希望這些製表位能夠完美對齊以達到專業的風格。您來對地方了！今天，我們將深入探討如何使用 Aspose.Words for .NET 變更 TOC 製表位。堅持下去，我保證你會帶著所有的專業知識離開，讓你的 TOC 看起來時髦和整潔。

## 先決條件

在開始之前，讓我們確保您擁有所需的一切：

1.  Aspose.Words for .NET：您可以[在這裡下載](https://releases.aspose.com/words/net/).
2. 開發環境：Visual Studio 或任何 C# 相容 IDE。
3. Word 文件：具體來說，是包含目錄的文件。

明白了嗎？驚人的！讓我們滾吧。

## 導入命名空間

首先，您需要匯入必要的名稱空間。這就像在開始專案之前打包工具一樣。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

讓我們將這個過程分解為簡單易懂的步驟。我們將載入文件、修改目錄製表位以及儲存更新的文件。

## 第 1 步：載入文檔

為什麼？我們需要存取包含要修改的目錄的 Word 文件。

如何？以下是一個簡單的程式碼片段，可以幫助您入門：

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENTS DIRECTORY";

//載入包含目錄的文檔
Document doc = new Document(dataDir + "Table of contents.docx");
```

想像一下您的文件就像一個蛋糕，我們要添加一些糖霜。第一步是將蛋糕從盒子裡拿出來。

## 第 2 步：確定目錄段落

為什麼？我們需要查明構成目錄的段落。 

如何？循環瀏覽段落並檢查它們的樣式：

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        //找到目錄段落
    }
}
```

可以把它想像成掃描人群來尋找你的朋友。在這裡，我們正在尋找樣式為目錄條目的段落。

## 步驟 3：修改製表位

為什麼？這就是奇蹟發生的地方。更改製表位可以讓您的目錄看起來更乾淨。

如何？刪除現有的製表位並在修改的位置新增一個新的製表位：

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        TabStop tab = para.ParagraphFormat.TabStops[0];
        para.ParagraphFormat.TabStops.RemoveByPosition(tab.Position);
        para.ParagraphFormat.TabStops.Add(tab.Position - 50, tab.Alignment, tab.Leader);
    }
}
```

這就像調整客廳裡的家具直到感覺合適為止。我們正在調整這些製表位以求完美。

## 第四步：儲存修改後的文檔

為什麼？確保您的所有辛苦工作都得到保存並可以查看或共享。

如何？使用新名稱儲存文件以保持原始文件不變：

```csharp
//儲存修改後的文檔
doc.Save(dataDir + "WorkingWithTableOfContent.ChangeTocTabStops.docx");
```

瞧！現在，目錄中的製表位正好位於您想要的位置。

## 結論

一旦將其分解，使用 Aspose.Words for .NET 更改 Word 文件中的 TOC 製表位就非常簡單。透過載入文件、識別目錄段落、修改製表位以及儲存文檔，您可以獲得精美且專業的外觀。請記住，熟能生巧，因此請不斷嘗試不同的製表位位置，以獲得您想要的確切佈局。

## 常見問題解答

### 我可以分別修改不同目錄層級的製表位嗎？
是的，你可以！只需檢查每個特定的 TOC 等級（Toc1、Toc2 等）並進行相應調整。

### 如果我的文件有多個目錄怎麼辦？
程式碼會掃描所有 TOC 樣式的段落，因此它將修改文件中存在的所有 TOC。

### 是否可以在目錄條目中新增多個製表位？
絕對地！您可以根據需要添加任意數量的製表位，方法是調整`para.ParagraphFormat.TabStops`收藏。

### 我可以更改製表位對齊方式和引線樣式嗎？
是的，您可以在新增製表位時指定不同的對齊方式和引線樣式。

### 我需要許可證才能使用 Aspose.Words for .NET 嗎？
是的，您需要有效的授權才能在試用期結束後使用 Aspose.Words for .NET。你可以獲得一個[臨時執照](https://purchase.aspose.com/temporary-license/)或者[買一個](https://purchase.aspose.com/buy).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
