---
"description": "透過本綜合指南了解如何使用 Aspose.Words for .NET 處理 Word 文件中的形狀修訂。掌握追蹤變化、插入形狀等。"
"linktitle": "形狀修改"
"second_title": "Aspose.Words文件處理API"
"title": "形狀修改"
"url": "/zh-hant/net/working-with-revisions/shape-revision/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 形狀修改

## 介紹

以程式方式編輯 Word 文件可能是一項艱鉅的任務，尤其是在處理形狀時。無論您是建立報告、設計範本還是簡單地自動建立文檔，追蹤和管理形狀修訂的能力都至關重要。 Aspose.Words for .NET 提供了強大的 API，使這一過程無縫且高效。在本教學中，我們將深入探討修改 Word 文件中形狀的具體細節，確保您擁有輕鬆管理文件的工具和知識。

## 先決條件

在深入研究程式碼之前，請確保您擁有所需的一切：

- Aspose.Words for .NET：確保您已安裝 Aspose.Words 程式庫。你可以 [點此下載](https://releases。aspose.com/words/net/).
- 開發環境：您應該設定一個開發環境，例如 Visual Studio。
- C# 基本理解：熟悉 C# 程式語言和物件導向程式設計的基本概念。
- Word 文件：要使用的 Word 文檔，或者您可以在教學期間建立一個。

## 導入命名空間

首先，讓我們導入必要的命名空間。這些將為我們提供處理 Word 文件和形狀所需的類別和方法。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## 步驟 1：設定文檔目錄

在開始處理形狀之前，我們需要定義文檔目錄的路徑。這是我們保存修改後的文件的地方。

```csharp
// 文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 步驟2：建立新文檔

讓我們建立一個新的 Word 文檔，在其中插入和修改形狀。

```csharp
Document doc = new Document();
```

## 步驟 3：插入內嵌形狀

我們首先在文件中插入一個內聯形狀，但不追蹤修訂。內聯形狀是與文字一起流動的形狀。

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## 步驟 4：開始追蹤修訂

為了追蹤文件中的變化，我們需要啟用修訂追蹤。這對於識別形狀所做的修改至關重要。

```csharp
doc.StartTrackRevisions("John Doe");
```

## 步驟5：插入另一個帶有修訂的形狀

現在已經啟用了修訂跟踪，讓我們插入另一個形狀。這一次，任何變化都會被追蹤。

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## 步驟 6：檢索並修改形狀

我們可以檢索文件中的所有形狀並根據需要修改它們。在這裡，我們將獲取形狀並刪除第一個。

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## 步驟7：儲存文檔

完成更改後，我們需要儲存文件。這確保所有修訂和修改都被儲存。

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## 步驟8：處理形狀移動修訂

當形狀被移動時，Aspose.Words 會將其作為修訂進行追蹤。這意味著該形狀將有兩個實例：一個在其原始位置，一個在其新位置。

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## 結論

就是這樣！您已成功學習如何使用 Aspose.Words for .NET 處理 Word 文件中的形狀修訂。無論您是管理文件範本、自動化報告還是僅僅追蹤變化，這些技能都是無價的。透過遵循本逐步指南，您不僅掌握了基礎知識，還可以了解更高階的文件處理技術。

## 常見問題解答

### 什麼是 Aspose.Words for .NET？
Aspose.Words for .NET 是一個功能強大的程式庫，可讓開發人員使用 C# 以程式設計方式建立、修改和轉換 Word 文件。

### 我可以追蹤 Word 文件中其他元素所做的更改嗎？
是的，Aspose.Words for .NET 支援追蹤各種元素的變化，包括文字、表格等。

### 如何免費試用 Aspose.Words for .NET？
您可以免費試用 Aspose.Words for .NET [這裡](https://releases。aspose.com/).

### 是否可以透過程式設計接受或拒絕修訂？
是的，Aspose.Words for .NET 提供了以程式設計方式接受或拒絕修訂的方法。

### 除了 C# 之外，我可以將 Aspose.Words for .NET 與其他 .NET 語言一起使用嗎？
絕對地！ Aspose.Words for .NET 可與任何 .NET 語言一起使用，包括 VB.NET 和 F#。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}