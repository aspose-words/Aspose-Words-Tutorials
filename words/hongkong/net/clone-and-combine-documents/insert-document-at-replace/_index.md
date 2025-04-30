---
"description": "透過我們詳細的逐步指南，了解如何使用 Aspose.Words for .NET 將一個 Word 文件無縫插入到另一個 Word 文件中。非常適合希望簡化文件處理的開發人員。"
"linktitle": "在替換處插入文檔"
"second_title": "Aspose.Words文件處理API"
"title": "在替換處插入文檔"
"url": "/zh-hant/net/clone-and-combine-documents/insert-document-at-replace/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在替換處插入文檔

## 介紹

嘿，文檔大師們！您是否曾發現自己深陷程式碼之中，試圖弄清楚如何將一個 Word 文件無縫地插入到另一個 Word 文件中？不要害怕，因為今天我們將深入研究 Aspose.Words for .NET 的世界，讓這項任務變得輕而易舉。我們將逐步指導您如何使用這個強大的庫在查找和替換操作期間在特定點插入文件。準備好成為 Aspose.Words 嚮導了嗎？讓我們開始吧！

## 先決條件

在我們進入程式碼之前，您需要做好以下幾件事：

- Visual Studio：確保您的機器上安裝了 Visual Studio。如果你還沒有，你可以從 [這裡](https://visualstudio。microsoft.com/).
- Aspose.Words for .NET：您需要 Aspose.Words 函式庫。您可以從 [Aspose 網站](https://releases。aspose.com/words/net/).
- 基本 C# 知識：對 C# 和 .NET 的基本了解將幫助您學習本教學。

好了，解決了這些問題之後，讓我們開始寫一些程式碼吧！

## 導入命名空間

首先，我們需要導入必要的命名空間來使用 Aspose.Words。這就像在開始一個專案之前收集所有的工具。在 C# 檔案的頂部新增以下使用指令：

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

現在我們已經滿足了先決條件，讓我們將流程分解為幾個小步驟。每一步都至關重要，都會讓我們更接近目標。

## 步驟 1：設定文檔目錄

首先，我們需要指定儲存文檔的目錄。這就像是大型演出前的舞台佈置。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替 `"YOUR DOCUMENT DIRECTORY"` 使用您的目錄的路徑。這是您的文件生存和發展的地方。

## 步驟 2：載入主文檔

接下來，我們載入想要插入另一個文檔的主文檔。將其視為我們所有行動發生的主要舞台。

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

此程式碼從指定目錄載入主文檔。

## 步驟 3：設定查找和取代選項

為了找到我們想要插入文件的具體位置，我們使用尋找和取代功能。這就像使用地圖來找到新成員的確切位置一樣。

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

在這裡，我們將方向設定為向後，並指定接下來定義的自訂回調處理程序。

## 步驟4：執行取代操作

現在，我們告訴主文件尋找特定的佔位符文字並將其替換為空，同時使用自訂回調插入另一個文件。

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

此程式碼執行尋找和取代操作，然後儲存更新的文件。

## 步驟 5：建立自訂替換回呼處理程序

我們的自訂回調處理程序就是奇蹟發生的地方。此處理程序將定義在尋找和取代作業期間如何執行文件插入。

```csharp
private class InsertDocumentAtReplaceHandler : IReplacingCallback
{
    ReplaceAction IReplacingCallback.Replacing(ReplacingArgs args)
    {
        Document subDoc = new Document(dataDir + "Document insertion 2.docx");

        // 在包含符合文字的段落後插入文件。
        Paragraph para = (Paragraph)args.MatchNode.ParentNode;
        InsertDocument(para, subDoc);

        // 刪除包含符合文字的段落。
        para.Remove();
        return ReplaceAction.Skip;
    }
}
```

在這裡，我們載入要插入的文檔，然後呼叫輔助方法來執行插入。

## 步驟6：定義插入文件方法

我們的難題的最後一部分是將文件實際插入指定位置的方法。

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    // 檢查插入目標是否為段落或表格
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;

        // 建立 NodeImporter 以從來源文件導入節點
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        // 循環遍歷來源文檔各部分中的所有區塊級節點
        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        {
            foreach (Node srcNode in srcSection.Body)
            {
                // 跳過章節的最後一個空白段落
                if (srcNode.NodeType == NodeType.Paragraph)
                {
                    Paragraph para = (Paragraph)srcNode;
                    if (para.IsEndOfSection && !para.HasChildNodes)
                        continue;
                }

                // 導入節點並將其插入目標中
                Node newNode = importer.ImportNode(srcNode, true);
                destinationParent.InsertAfter(newNode, insertionDestination);
                insertionDestination = newNode;
            }
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}

```

此方法負責從要插入的文件中匯入節點並將它們放置在主文件中的正確位置。

## 結論

就是這樣！使用 Aspose.Words for .NET 將一個文件插入另一個文件的綜合指南。透過遵循這些步驟，您可以輕鬆地自動執行文件組裝和操作任務。無論您是建立文件管理系統還是只需要簡化文件處理工作流程，Aspose.Words 都是您值得信賴的夥伴。

## 常見問題解答

### 什麼是 Aspose.Words for .NET？
Aspose.Words for .NET 是一個功能強大的程式庫，用於以程式設計方式操作 Word 文件。它允許您輕鬆建立、修改、轉換和處理 Word 文件。

### 我可以一次插入多個文件嗎？
是的，您可以修改回呼處理程序，透過遍歷文件集合來處理多個插入。

### 有免費試用嗎？
絕對地！您可以從下載免費試用版 [這裡](https://releases。aspose.com/).

### 如何獲得 Aspose.Words 的支援？
您可以透過訪問 [Aspose.Words論壇](https://forum。aspose.com/c/words/8).

### 我可以保留插入文件的格式嗎？
是的， `NodeImporter` 類別可讓您指定在從一個文件向另一個文件匯入節點時如何處理格式。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}