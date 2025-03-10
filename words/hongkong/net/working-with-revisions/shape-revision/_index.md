---
title: 形狀修正
linktitle: 形狀修正
second_title: Aspose.Words 文件處理 API
description: 透過這份綜合指南，了解如何使用 Aspose.Words for .NET 處理 Word 文件中的形狀修訂。掌握追蹤更改、插入形狀等。
weight: 10
url: /zh-hant/net/working-with-revisions/shape-revision/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 形狀修正

## 介紹

以程式方式編輯 Word 文件可能是一項艱鉅的任務，尤其是在處理形狀時。無論您是建立報告、設計範本還是簡單地自動建立文檔，追蹤和管理形狀修訂的能力都至關重要。 Aspose.Words for .NET 提供了強大的 API 來使流程無縫且有效率。在本教學中，我們將深入探討修改 Word 文件中的形狀的細節，確保您擁有輕鬆管理文件的工具和知識。

## 先決條件

在我們深入研究程式碼之前，讓我們確保您擁有所需的一切：

-  Aspose.Words for .NET：確保您已安裝 Aspose.Words 程式庫。你可以[在這裡下載](https://releases.aspose.com/words/net/).
- 開發環境：您應該設定一個開發環境，例如 Visual Studio。
- 對C#的基本了解：熟悉C#程式語言和物件導向程式設計的基本概念。
- Word 文件：要使用的 Word 文檔，或者您可以在教學期間建立一個。

## 導入命名空間

首先，讓我們導入必要的名稱空間。這些將使我們能夠存取處理 Word 文件和形狀所需的類別和方法。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## 第 1 步：設定您的文件目錄

在開始使用形狀之前，我們需要定義文檔目錄的路徑。這是我們保存修改後的文件的地方。

```csharp
//文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 第 2 步：建立新文檔

讓我們建立一個新的 Word 文檔，在其中插入和修改形狀。

```csharp
Document doc = new Document();
```

## 第 3 步：插入內嵌形狀

我們將首先在文件中插入內聯形狀，而不追蹤修訂。內聯形狀是一種隨文字流動的形狀。

```csharp
Shape shape = new Shape(doc, ShapeType.Cube);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## 第 4 步：開始追蹤修訂

為了追蹤文件中的更改，我們需要啟用修訂追蹤。這對於識別對形狀的修改至關重要。

```csharp
doc.StartTrackRevisions("John Doe");
```

## 第 5 步：插入另一個經過修改的形狀

現在已啟用修訂跟踪，讓我們插入另一個形狀。這一次，任何更改都會被追蹤。

```csharp
shape = new Shape(doc, ShapeType.Sun);
shape.WrapType = WrapType.Inline;
shape.Width = 100.0;
shape.Height = 100.0;
doc.FirstSection.Body.FirstParagraph.AppendChild(shape);
```

## 第 6 步：檢索和修改形狀

我們可以檢索文件中的所有形狀並根據需要修改它們。在這裡，我們將獲取形狀並刪除第一個形狀。

```csharp
List<Shape> shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
shapes[0].Remove();
```

## 步驟7：儲存文檔

進行更改後，我們需要儲存文件。這可確保儲存所有修訂和修改。

```csharp
doc.Save(dataDir + "Revision shape.docx");
```

## 第 8 步：處理形狀移動修改

當形狀移動時，Aspose.Words 會將此作為修訂進行追蹤。這意味著該形狀將有兩個實例：一個位於其原始位置，一個位於其新位置。

```csharp
doc = new Document(dataDir + "Revision shape.docx");
shapes = doc.GetChildNodes(NodeType.Shape, true).Cast<Shape>().ToList();
```

## 結論

現在你就擁有了！您已成功學習如何使用 Aspose.Words for .NET 處理 Word 文件中的形狀修訂。無論您是管理文件範本、自動化報告還是只是追蹤更改，這些技能都是非常寶貴的。透過遵循本逐步指南，您不僅掌握了基礎知識，而且還深入了解了更高級的文件處理技術。

## 常見問題解答

### 什麼是 Aspose.Words for .NET？
Aspose.Words for .NET 是一個功能強大的程式庫，可讓開發人員使用 C# 以程式設計方式建立、修改和轉換 Word 文件。

### 我可以追蹤 Word 文件中其他元素所做的更改嗎？
是的，Aspose.Words for .NET 支援追蹤各種元素的更改，包括文字、表格等。

### 如何獲得 Aspose.Words for .NET 的免費試用版？
您可以免費試用 Aspose.Words for .NET[這裡](https://releases.aspose.com/).

### 是否可以以程式方式接受或拒絕修訂？
是的，Aspose.Words for .NET 提供了以程式設計方式接受或拒絕修訂的方法。

### 我可以將 Aspose.Words for .NET 與 C# 以外的其他 .NET 語言一起使用嗎？
絕對地！ Aspose.Words for .NET 可與任何 .NET 語言一起使用，包括 VB.NET 和 F#。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
