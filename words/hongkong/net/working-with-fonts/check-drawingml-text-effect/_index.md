---
title: 檢查DrawingML文字效果
linktitle: 檢查DrawingML文字效果
second_title: Aspose.Words 文件處理 API
description: 透過我們詳細的逐步指南，了解如何使用 Aspose.Words for .NET 檢查 Word 文件中的 DrawingML 文字效果。輕鬆增強您的文件。
weight: 10
url: /zh-hant/net/working-with-fonts/check-drawingml-text-effect/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 檢查DrawingML文字效果

## 介紹

歡迎來到另一個關於使用 Aspose.Words for .NET 的詳細教學！今天，我們將深入了解 DrawingML 文本效果的迷人世界。無論您是想透過陰影、反射還是 3D 效果來增強 Word 文檔，本指南都會向您展示如何使用 Aspose.Words for .NET 檢查文檔中的這些文字效果。讓我們開始吧！

## 先決條件

在我們開始本教學之前，您需要滿足一些先決條件：

-  Aspose.Words for .NET 程式庫：確保您已安裝 Aspose.Words for .NET 程式庫。您可以從[Aspose 發佈頁面](https://releases.aspose.com/words/net/).
- 開發環境：您應該設定一個開發環境，例如 Visual Studio。
- C# 基礎知識：熟悉 C# 程式設計將會有所幫助。

## 導入命名空間

首先，您需要匯入必要的名稱空間。這些命名空間將使您能夠存取操作 Word 文件和檢查 DrawingML 文字效果所需的類別和方法。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## 檢查 DrawingML 文字效果的逐步指南

現在，讓我們將該過程分解為多個步驟，以便更容易遵循。

## 第 1 步：載入文檔

第一步是載入要檢查 DrawingML 文字效果的 Word 文件。 

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "DrawingML text effects.docx");
```

此程式碼片段從您指定的目錄載入名為「DrawingML texteffects.docx」的文件。

## 第 2 步：訪問運行集合

接下來，我們需要存取文件第一段中的運行集合。連續串是具有相同格式的文字部分。

```csharp
RunCollection runs = doc.FirstSection.Body.FirstParagraph.Runs;
```

這行程式碼從文檔第一部分的第一段中檢索運行。

## 第三步：取得第一次運行的字體

現在，我們將取得運行集合中第一次運行的字體屬性。這使我們能夠檢查應用於文字的各種 DrawingML 文字效果。

```csharp
Font runFont = runs[0].Font;
```

## 步驟 4： 檢查 DrawingML 文字效果

最後，我們可以檢查不同的 DrawingML 文字效果，例如陰影、3D 效果、反射、輪廓和填充。

```csharp
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Shadow));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Effect3D));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Reflection));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Outline));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Fill));
```

這幾行程式碼將會列印出來`true`或者`false`取決於每個特定的 DrawingML 文字效果是否會套用於執行的字體。

## 結論

恭喜！您剛剛學習如何使用 Aspose.Words for .NET 檢查 Word 文件中的 DrawingML 文字效果。這項強大的功能使您能夠以程式設計方式檢測和操作複雜的文字格式，從而更好地控製文件處理任務。


## 常見問題解答

### 什麼是 DrawingML 文字效果？
DrawingML 文字效果是 Word 文件中的進階文字格式選項，包括陰影、3D 效果、反射、輪廓和填滿。

### 我可以使用 Aspose.Words for .NET 套用 DrawingML 文字效果嗎？
是的，Aspose.Words for .NET 可讓您以程式設計方式檢查和套用 DrawingML 文字效果。

### 我需要許可證才能使用 Aspose.Words for .NET 嗎？
是的，Aspose.Words for .NET 需要完整功能的授權。您可以獲得[臨時執照](https://purchase.aspose.com/temporary-license/)進行評估。

### Aspose.Words for .NET 有沒有免費試用版？
是的，您可以下載一個[免費試用](https://releases.aspose.com/)購買前試用 Aspose.Words for .NET。

### 在哪裡可以找到有關 Aspose.Words for .NET 的更多文件？
您可以在以下位置找到詳細文檔[Aspose.Words for .NET 文件頁面](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
