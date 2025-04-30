---
"description": "在本全面的逐步教學中學習如何使用 Aspose.Words for .NET 在郵件合併欄位中插入文件。"
"linktitle": "在郵件合併中插入文檔"
"second_title": "Aspose.Words文件處理API"
"title": "在郵件合併中插入文檔"
"url": "/zh-hant/net/clone-and-combine-documents/insert-document-at-mail-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在郵件合併中插入文檔

## 介紹

歡迎來到 Aspose.Words for .NET 文件自動化的世界！您是否想過如何在郵件合併作業期間將文件動態插入主文檔內的特定欄位？嗯，您來對地方了。本教學將引導您逐步完成使用 Aspose.Words for .NET 在郵件合併欄位插入文件的過程。這就像拼湊一個拼圖，每個碎片都完美地拼合在一起。那麼，就讓我們開始吧！

## 先決條件

在開始之前，請確保您具備以下條件：

1. Aspose.Words for .NET：您可以 [點此下載最新版本](https://releases.aspose.com/words/net/)。如果您需要購買許可證，您可以這樣做 [這裡](https://purchase.aspose.com/buy)。或者，您可以獲得 [臨時執照](https://purchase.aspose.com/temporary-license/) 或者嘗試一下 [免費試用](https://releases。aspose.com/).
2. 開發環境：Visual Studio 或任何其他 C# IDE。
3. C# 基礎知識：熟悉 C# 程式設計將使本教學變得輕而易舉。

## 導入命名空間

首先，您需要匯入必要的命名空間。這些就像您專案的基石。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

讓我們將這個過程分解為易於管理的步驟。每一步都建立在前一步的基礎上，從而引導您找到完整的解決方案。

## 步驟 1：設定目錄

在開始插入文件之前，您需要定義文檔目錄的路徑。這是儲存您的文件的地方。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 步驟2：載入主文檔

接下來，您將載入主文檔。該文件包含將插入其他文件的合併欄位。

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## 步驟3：設定欄位合併回調

為了處理合併過程，您需要設定一個回呼函數。此函數負責在指定的合併欄位中插入文件。

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## 步驟4：執行郵件合併

現在是時候執行郵件合併了。這就是奇蹟發生的地方。您將指定合併欄位和應插入此欄位的文件。

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## 步驟5：儲存文檔

郵件合併完成後，您將儲存修改後的文件。這個新文件將在您想要的位置插入內容。

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## 步驟 6：建立回呼處理程序

回呼處理程序是針對合併欄位進行特殊處理的類別。它會載入欄位值中指定的文件並將其插入到目前合併欄位中。

```csharp
private class InsertDocumentAtMailMergeHandler : IFieldMergingCallback
{
    void IFieldMergingCallback.FieldMerging(FieldMergingArgs args)
    {
        if (args.DocumentFieldName == "Document_1")
        {
            DocumentBuilder builder = new DocumentBuilder(args.Document);
            builder.MoveToMergeField(args.DocumentFieldName);

            Document subDoc = new Document((string)args.FieldValue);
            InsertDocument(builder.CurrentParagraph, subDoc);

            if (!builder.CurrentParagraph.HasChildNodes)
                builder.CurrentParagraph.Remove();

            args.Text = null;
        }
    }
}
```

## 步驟7：插入文檔

此方法將指定的文件插入到目前段落或表格儲存格中。

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        foreach (Node srcNode in srcSection.Body)
        {
            if (srcNode.NodeType == NodeType.Paragraph)
            {
                Paragraph para = (Paragraph)srcNode;
                if (para.IsEndOfSection && !para.HasChildNodes)
                    continue;
            }

            Node newNode = importer.ImportNode(srcNode, true);
            destinationParent.InsertAfter(newNode, insertionDestination);
            insertionDestination = newNode;
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}
```

## 結論

就是這樣！您已使用 Aspose.Words for .NET 在郵件合併作業期間成功將文件插入特定欄位。此強大的功能可為您節省大量時間和精力，尤其是在處理大量文件時。可以想像為擁有一位私人助理，為您處理所有繁重的工作。所以，繼續嘗試吧。編碼愉快！

## 常見問題解答

### 我可以在不同的合併欄位插入多個文件嗎？
是的，你可以。只需在 `MailMerge.Execute` 方法。

### 插入的文檔的格式是否可以與主文檔不同？
絕對地！您可以使用 `ImportFormatMode` 參數 `NodeImporter` 控制格式。

### 如果合併欄位名稱是動態的怎麼辦？
您可以透過將動態合併欄位名稱作為參數傳遞給回呼處理程序來處理它們。

### 我可以將此方法用於不同的文件格式嗎？
是的，Aspose.Words 支援各種文件格式，包括 DOCX、PDF 等。

### 如何處理文件插入過程中的錯誤？
在回調處理程序中實作錯誤處理來管理可能發生的任何異常。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}