---
"description": "了解如何使用 Aspose.Words for .NET 將 XML 資料動態綁定到 Word 中的結構化文件標籤。請按照我們的逐步指南進行操作。"
"linktitle": "結構化文檔標籤範圍開始 XML 映射"
"second_title": "Aspose.Words文件處理API"
"title": "結構化文檔標籤範圍開始 XML 映射"
"url": "/zh-hant/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 結構化文檔標籤範圍開始 XML 映射

## 介紹

您是否曾經想過將 XML 資料動態插入 Word 文件？嗯，你很幸運！ Aspose.Words for .NET 讓這項任務變得輕而易舉。在本教學中，我們將深入研究結構化文件標籤範圍開始 XML 映射。此功能可讓您將自訂 XML 部分綁定到內容控件，確保您的文件內容與 XML 資料無縫更新。準備將您的文件轉換為動態傑作。

## 先決條件

在進入編碼部分之前，讓我們確保您擁有所需的一切：

1. Aspose.Words for .NET Library：確保您擁有最新版本。你可以下載 [這裡](https://releases。aspose.com/words/net/).
2. 開發環境：Visual Studio 或任何其他支援 C# 的 IDE。
3. C# 基礎知識：必須熟悉 C# 程式設計。
4. Word 文件：可供使用的範例 Word 文件。

## 導入命名空間

首先，讓我們導入必要的命名空間。這將確保我們可以存取 Aspose.Words for .NET 中所有必要的類別和方法。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## 步驟 1：設定文檔目錄

每個項目都需要基礎，對嗎？在這裡，我們設定您的文件目錄的路徑。

```csharp
// 文檔目錄的路徑 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 第 2 步：載入 Word 文檔

接下來我們載入Word文檔。這是我們將插入 XML 資料的文檔。

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## 步驟 3：新增自訂 XML 部分

我們需要建立一個包含我們想要插入的資料的 XML 部分，並將其新增至文件的 CustomXmlPart 集合中。這個自訂 XML 部分將作為我們結構化文件標籤的資料來源。

### 建立 XML 部件

首先，為XML部分產生一個唯一的ID並定義其內容。

```csharp
// 建構包含資料的 XML 元件並將其新增至文件的 CustomXmlPart 集合中。
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### 驗證 XML 部分內容

為了確保 XML 部分正確添加，我們列印其內容。

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## 步驟 4：建立結構化文件標籤

結構化文件標籤 (SDT) 是一種可以綁定到 XML 部分的內容控制項。在這裡，我們建立一個 SDT，它將顯示我們自訂 XML 部分的內容。

首先，在文件中找到 SDT 範圍的起點。

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## 步驟 5：設定 SDT 的 XML 映射

現在，是時候將我們的 XML 部分綁定到 SDT 了。透過設定 XML 映射，我們指定 XML 資料的哪部分應該顯示在 SDT 中。

XPath 指向我們想要顯示的 XML 部分中的特定元素。這裡我們指出第二個 `<text>` 元素內的 `<root>` 元素。

```csharp
// 為我們的 StructuredDocumentTag 設定映射
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## 步驟6：儲存文檔

最後，儲存文件以查看實際變更。 Word 文件中的 SDT 現在將顯示指定的 XML 內容。

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## 結論

就是這樣！您已成功使用 Aspose.Words for .NET 將 XML 部分對應到 Word 文件中的結構化文件標籤。此強大功能可讓您毫不費力地建立動態和資料驅動的文件。無論您產生報表、發票或任何其他文件類型，XML 對應都可以顯著簡化您的工作流程。

## 常見問題解答

### Word 中的結構化文件標籤是什麼？
結構化文件標籤（也稱為內容控制項）是 Word 文件中特定類型內容的容器。它們可用於綁定資料、限制編輯或指導使用者建立文件。

### 如何動態更新 XML 部分內容？
您可以透過修改 `xmlPartContent` 字串，然後再將其新增到文件中。只需使用新資料更新字串並將其新增至 `CustomXmlParts` 收藏。

### 我可以將多個 XML 部分綁定到同一文件中的不同 SDT 嗎？
是的，您可以將多個 XML 部分綁定到同一文件中的不同 SDT。每個 SDT 可以有自己獨特的 XML 部分和 XPath 映射。

### 是否可以將複雜的 XML 結構對應到 SDT？
絕對地！您可以使用詳細的 XPath 表達式將複雜的 XML 結構對應到 SDT，這些表達式精確指向 XML 部分中的所需元素。

### 如何從文件中刪除 XML 部分？
您可以透過調用 `Remove` 方法 `CustomXmlParts` 收集，傳遞 `xmlPartId` 您想要刪除的 XML 部分。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}