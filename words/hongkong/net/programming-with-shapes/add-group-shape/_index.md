---
title: 新增群組形狀
linktitle: 新增群組形狀
second_title: Aspose.Words 文件處理 API
description: 透過這個全面的逐步教學，了解如何使用 Aspose.Words for .NET 將群組形狀新增至 Word 文件。
weight: 10
url: /zh-hant/net/programming-with-shapes/add-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 新增群組形狀

## 介紹

創建具有豐富視覺元素的複雜文件有時可能是一項艱鉅的任務，尤其是在處理群組形狀時。但不要害怕！ Aspose.Words for .NET 簡化了這個過程，使其變得非常簡單。在本教學中，我們將引導您完成在 Word 文件中新增群組形狀的步驟。準備好潛入了嗎？讓我們開始吧！

## 先決條件

在我們開始之前，請確保您具備以下條件：

1.  Aspose.Words for .NET：您可以從[Aspose 發佈頁面](https://releases.aspose.com/words/net/).
2. 開發環境：Visual Studio 或任何其他與.NET 相容的IDE。
3. 對 C# 的基本了解：熟悉 C# 程式設計者優先。

## 導入命名空間

首先，我們需要在專案中導入必要的命名空間。這些命名空間提供對使用 Aspose.Words 操作 Word 文件所需的類別和方法的存取。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## 步驟1：初始化文檔

首先，讓我們初始化一個新的 Word 文件。將此視為建立一個空白畫布，我們將在其中新增群組形狀。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

這裡，`EnsureMinimum()`新增文件所需的最小節點集。

## 第 2 步：建立 GroupShape 對象

接下來，我們需要建立一個`GroupShape`目的。該物件將充當其他形狀的容器，使我們能夠將它們分組在一起。

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## 步驟 3：將形狀加入 GroupShape

現在，讓我們將單獨的形狀添加到我們的`GroupShape`容器。我們將從強調邊框形狀開始，然後新增操作按鈕形狀。

### 新增強調邊框形狀

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

此程式碼片段建立寬度和高度均為 100 個單位的重音邊框形狀，並將其新增至`GroupShape`.

### 新增操作按鈕形狀

```csharp
Shape actionButtonShape = new Shape(doc, ShapeType.ActionButtonBeginning)
{
    Left = 100,
    Width = 100,
    Height = 200
};
groupShape.AppendChild(actionButtonShape);
```

在這裡，我們創建一個操作按鈕形狀，定位它，並將其添加到我們的`GroupShape`.

## 步驟 4：定義 GroupShape 尺寸

為了確保我們的形狀很好地適合組，我們需要設定形狀的尺寸`GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

這定義了寬度和高度`GroupShape`為 200 個單位並相應地設定座標大小。

## 步驟 5：將 GroupShape 插入文件中

現在，讓我們插入我們的`GroupShape`到文件中使用`DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder`提供了一種向文件添加節點（包括形狀）的簡單方法。

## 第 6 步：儲存文檔

最後，將文件儲存到您指定的目錄中。

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

現在你就擁有了！您的帶有群組形狀的文檔已準備就緒。

## 結論

將群組形狀新增至 Word 文件不一定是一個複雜的過程。透過 Aspose.Words for .NET，您可以輕鬆建立和操作形狀，使您的文件更具視覺吸引力和實用性。按照本教程中概述的步驟操作，您很快就會成為專業人士！

## 常見問題解答

### 我可以為 GroupShape 添加兩個以上的形狀嗎？
是的，您可以根據需要添加任意數量的形狀`GroupShape`。只需使用`AppendChild`每種形狀的方法。

### 是否可以在 GroupShape 中設定形狀的樣式？
絕對地！每個形狀都可以使用可用的屬性單獨設定樣式`Shape`班級。

### 如何在文件中定位 GroupShape？
您可以將`GroupShape`透過設定其`Left`和`Top`特性。

### 我可以為 GroupShape 內的形狀添加文字嗎？
是的，您可以使用以下命令將文字新增至形狀中`AppendChild`方法添加一個`Paragraph`含有`Run`帶有文本的節點。

### 是否可以根據使用者輸入動態對形狀進行分組？
是的，您可以透過相應地調整屬性和方法，根據使用者輸入動態建立和分組形狀。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
