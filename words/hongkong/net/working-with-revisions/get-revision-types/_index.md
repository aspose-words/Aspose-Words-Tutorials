---
title: 取得單字的修訂類型
linktitle: 取得單字的修訂類型
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 取得 Word 文件中單字的修訂類型。本逐步指南可協助您有效處理文件修訂。
weight: 10
url: /zh-hant/net/working-with-revisions/get-revision-types/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 取得單字的修訂類型

## 介紹

您是否曾經發現自己陷入了文件修訂的海洋之中，想知道誰在何時移動了哪些內容？你並不孤單。處理文件修訂可能是一項乏味的任務，尤其是在處理大量文件時。但是，不用擔心！透過 Aspose.Words for .NET，您可以輕鬆識別和管理這些修訂。在本指南中，我們將引導您逐步了解如何使用 Aspose.Words for .NET 取得 Word 文件中單字的修訂類型。所以，繫好安全帶，讓我們開始吧！

## 先決條件

在我們開始編寫一些程式碼之前，您需要準備一些東西：

1.  Aspose.Words for .NET Library：如果您還沒有，請從以下位置下載：[這裡](https://releases.aspose.com/words/net/).
2. 開發環境：Visual Studio 或任何其他 .NET 相容 IDE。
3. C# 基礎知識：了解 C# 程式語言將是有益的。
4. 經過修訂的 Word 文件：確保您有`.docx`包含追蹤更改的檔案以測試程式碼。

## 導入命名空間

首先，您需要在 C# 專案中匯入必要的命名空間。這將允許您存取 Aspose.Words for .NET 提供的功能。

```csharp
using Aspose.Words;
using Aspose.Words.Revision;
using System;
```

讓我們將範例分解為多個步驟，以便更好地理解和實現。

## 第 1 步：設定您的文件目錄

首先，您需要定義文檔目錄的路徑。這是經過修訂的 Word 文件所在的位置。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替`"YOUR DOCUMENT DIRECTORY"`與文件資料夾的實際路徑。

## 第 2 步：載入 Word 文檔

接下來，您需要將 Word 文件載入到您的專案中。該文件應該包含您想要分析的修訂。

```csharp
Document doc = new Document(dataDir + "Revisions.docx");
```

確保該文件`Revisions.docx`存在於指定目錄中。

## 第 3 步：訪問段落集合

現在您的文件已加載，您需要訪問文檔正文第一部分中的段落。這將幫助您迭代每個段落以檢查修訂。

```csharp
ParagraphCollection paragraphs = doc.FirstSection.Body.Paragraphs;
```

## 第 4 步：迭代段落並檢查修訂

這就是奇蹟發生的地方。您將遍歷每個段落並檢查它是否已被移動（刪除或插入）。

```csharp
for (int i = 0; i < paragraphs.Count; i++)
{
    if (paragraphs[i].IsMoveFromRevision)
        Console.WriteLine("Paragraph {0} has been moved (deleted).", i);
    if (paragraphs[i].IsMoveToRevision)
        Console.WriteLine("Paragraph {0} has been moved (inserted).", i);
}
```

該循環遍歷每個段落並使用`IsMoveFromRevision`和`IsMoveToRevision`屬性來決定段落是被移動（刪除）還是被移動（插入）。

## 結論

現在你就擁有了！只需幾行程式碼，您就可以使用 Aspose.Words for .NET 輕鬆識別 Word 文件中的修訂類型。這個強大的程式庫使處理文件修訂變得輕而易舉，讓您能夠專注於更重要的任務。 

## 常見問題解答

### 我可以使用 Aspose.Words for .NET 來追蹤特定使用者所做的變更嗎？

是的，Aspose.Words for .NET 提供了存取修訂詳細資訊的功能，包括更改的作者。

### Aspose.Words for .NET 有沒有免費試用版？

絕對地！您可以獲得免費試用[這裡](https://releases.aspose.com/).

### 如何申請 Aspose.Words for .NET 的臨時授權？

您可以向以下機構請求併申請臨時許可證[這裡](https://purchase.aspose.com/temporary-license/).

### 在哪裡可以找到有關 Aspose.Words for .NET 的更詳細文件？

詳細文件可在[阿斯普斯網站](https://reference.aspose.com/words/net/).

### 我可以在非商業專案中使用 Aspose.Words for .NET 嗎？

是的，Aspose.Words for .NET 可以在商業和非商業項目中使用，但請務必檢查許可條款。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
