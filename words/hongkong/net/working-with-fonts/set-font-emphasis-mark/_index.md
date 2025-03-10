---
title: 設定字體強調標記
linktitle: 設定字體強調標記
second_title: Aspose.Words 文件處理 API
description: 透過這份詳細的逐步指南，了解如何使用 Aspose.Words for .NET 在 Word 文件中設定字體強調標記。非常適合 .NET 開發人員。
weight: 10
url: /zh-hant/net/working-with-fonts/set-font-emphasis-mark/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 設定字體強調標記

## 介紹

在今天的教學中，我們將深入探討如何使用 Aspose.Words for .NET 在 Word 文件中設定字體強調標記。無論您是想用獨特的標記在特定文字下劃線，還是只是想讓某些單字脫穎而出，本指南都能滿足您的需求。所以，繫好安全帶，讓我們開始吧！

## 先決條件

在我們深入了解具體細節之前，請確保您已勾選以下先決條件：

-  Aspose.Words for .NET 程式庫：確保您已安裝 Aspose.Words for .NET 程式庫。您可以從以下位置下載：[這裡](https://releases.aspose.com/words/net/).
- 開發環境：工作開發環境，例如 Visual Studio。
- .NET Framework：確保您已安裝 .NET Framework。

## 導入命名空間

若要使用 Aspose.Words for .NET，您需要匯入必要的命名空間。將這些添加到程式碼檔案的頂部：

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

現在，讓我們將該過程分解為簡單的步驟。仔細按照每個步驟在 Word 文件中設定字型強調標記。

## 步驟1：初始化Document和DocumentBuilder

首先，您需要初始化一個新文件和一個 DocumentBuilder。 DocumentBuilder 類別提供了將文字和其他元素插入文件的方法。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";

//初始化一個新文檔
Document document = new Document();

//使用文件初始化 DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(document);
```

## 第2步：設定字體強調標記

準備好 DocumentBuilder 後，現在可以設定字體強調標記。在此範例中，我們將使用“UnderSolidCircle”強調標記。

```csharp
//設定字體強調標記
builder.Font.EmphasisMark = EmphasisMark.UnderSolidCircle;

//用強調標記書寫文本
builder.Write("Emphasis text");
builder.Writeln();
```

## 第 3 步：清除格式並新增常規文本

設定強調標記後，您可能想要添加一些不帶任何強調的常規文字。為此，您需要清除格式。

```csharp
//清除字體格式
builder.Font.ClearFormatting();

//寫入常規文本
builder.Write("Simple text");
```

## 步驟 4：儲存文檔

在新增所需的所有文字和格式後，最後一步是儲存文件。指定要儲存文件的路徑和檔案名稱。

```csharp
//儲存文件
document.Save(dataDir + "WorkingWithFonts.SetFontEmphasisMark.docx");
```

## 結論

現在你就擁有了！使用 Aspose.Words for .NET 在 Word 文件中設定字體強調標記就是這麼簡單。只需幾行程式碼，您就可以使您的文字脫穎而出，並為您的文件添加專業風格。請毫不猶豫地嘗試不同的強調標記和樣式來滿足您的需求。

## 常見問題解答

### 什麼是字體強調標記？

字體強調標記是添加到文字中以使其脫穎而出的特殊符號。它們可以包括點、圓圈和其他裝飾標記。

### 我可以在 Aspose.Words for .NET 中使用其他強調標記嗎？

是的，Aspose.Words for .NET 支援各種強調標記。您可以參考以下內容探索不同的選項[文件](https://reference.aspose.com/words/net/).

### Aspose.Words for .NET 可以免費使用嗎？

Aspose.Words for .NET 需要完整功能的授權。您可以獲得免費試用[這裡](https://releases.aspose.com/)或購買許可證[這裡](https://purchase.aspose.com/buy).

### 如何獲得 Aspose.Words for .NET 支援？

您可以透過造訪 Aspose 社群和支持團隊獲得支持[支援論壇](https://forum.aspose.com/c/words/8).

### 我可以將 Aspose.Words for .NET 與其他 .NET 框架一起使用嗎？

是的，Aspose.Words for .NET 與各種 .NET 框架相容，包括 .NET Core 和 .NET 5/6。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
