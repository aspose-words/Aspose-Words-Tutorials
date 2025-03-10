---
title: 在郵件合併中插入文檔
linktitle: 在郵件合併中插入文檔
second_title: Aspose.Words 文件處理 API
description: 在此全面的逐步教學中，了解如何使用 Aspose.Words for .NET 在郵件合併欄位中插入文件。
weight: 10
url: /zh-hant/net/clone-and-combine-documents/insert-document-at-mail-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在郵件合併中插入文檔

## 介紹

歡迎來到 Aspose.Words for .NET 的文件自動化世界！您是否想知道如何在郵件合併作業期間將文件動態插入主文檔中的特定欄位？嗯，您來對地方了。本教學將引導您逐步完成使用 Aspose.Words for .NET 在郵件合併欄位中插入文件的過程。這就像拼圖一樣，每一塊都完美地拼湊到位。那麼，讓我們深入了解一下吧！

## 先決條件

在我們開始之前，請確保您具備以下條件：

1.  Aspose.Words for .NET：您可以[在這裡下載最新版本](https://releases.aspose.com/words/net/)。如果您需要購買許可證，您可以這樣做[這裡](https://purchase.aspose.com/buy)。或者，您可以獲得[臨時執照](https://purchase.aspose.com/temporary-license/)或者嘗試一下[免費試用](https://releases.aspose.com/).
2. 開發環境：Visual Studio 或任何其他 C# IDE。
3. C# 基礎知識：熟悉 C# 程式設計將使本教學變得輕而易舉。

## 導入命名空間

首先，您需要匯入必要的名稱空間。這些就像您專案的構建塊。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

讓我們將這個過程分解為可管理的步驟。每一步都將建立在前一步的基礎上，從而引導您獲得完整的解決方案。

## 第 1 步：設定您的目錄

在開始插入文件之前，您需要定義文檔目錄的路徑。這是您的文件的儲存位置。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 步驟2：載入主文檔

接下來，您將載入主文檔。該文件包含將插入其他文件的合併欄位。

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## 第三步：設定欄位合併回調

要處理合併過程，您需要設定一個回呼函數。此函數將負責在指定的合併欄位中插入文件。

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## 步驟 4：執行郵件合併

現在是執行郵件合併的時候了。這就是奇蹟發生的地方。您將指定合併欄位以及應在此欄位插入的文件。

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## 第 5 步：儲存文檔

郵件合併完成後，您將儲存修改後的文件。這個新文件將在您想要的位置插入內容。

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## 第 6 步：建立回調處理程序

回呼處理程序是一個對合併欄位進行特殊處理的類別。它會載入欄位值中指定的文件並將其插入到目前合併欄位中。

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

此方法將指定文件插入到目前段落或表格儲存格中。

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

現在你就擁有了！您已使用 Aspose.Words for .NET 在郵件合併作業期間成功將文件插入到特定欄位。這項強大的功能可以為您節省大量的時間和精力，特別是在處理大量文件時。您可以將其視為擁有私人助理，為您處理所有繁重的工作。所以，繼續嘗試吧。快樂編碼！

## 常見問題解答

### 我可以在不同的合併欄位插入多個文件嗎？
是的，你可以。只需在中指定適當的合併欄位和相應的文件路徑即可`MailMerge.Execute`方法。

### 插入文件的格式是否可以與主文件不同？
絕對地！您可以使用`ImportFormatMode`中的參數`NodeImporter`來控制格式。

### 如果合併欄位名稱是動態的怎麼辦？
您可以透過將動態合併欄位名稱作為參數傳遞給回呼處理程序來處理動態合併欄位名稱。

### 我可以對不同的文件格式使用此方法嗎？
是的，Aspose.Words 支援各種文件格式，包括 DOCX、PDF 等。

### 如何處理文件插入過程中的錯誤？
在回調處理程序中實作錯誤處理以管理可能發生的任何異常。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
