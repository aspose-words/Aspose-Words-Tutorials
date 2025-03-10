---
title: 在Word文檔中新增雙向標記
linktitle: 在Word文檔中新增雙向標記
second_title: Aspose.Words 文件處理 API
description: 透過本指南了解如何使用 Aspose.Words for .NET 在 Word 文件中新增雙向 (Bidi) 標記。確保多語言內容的文字方向正確。
weight: 10
url: /zh-hant/net/programming-with-txtsaveoptions/add-bidi-marks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在Word文檔中新增雙向標記

## 介紹

在文件處理領域，雙向 (Bidi) 文字的管理通常有點棘手。在處理具有不同文字方向的語言（例如阿拉伯語或希伯來語）時尤其如此。幸運的是，Aspose.Words for .NET 可以輕鬆處理這類場景。在本教學中，我們將介紹如何使用 Aspose.Words for .NET 將 Bidi 標籤新增至 Word 文件。

## 先決條件

在我們深入研究程式碼之前，請確保您具備以下條件：

1. Aspose.Words for .NET：您需要安裝 Aspose.Words for .NET。您可以從[Aspose 下載頁面](https://releases.aspose.com/words/net/).
2. .NET Framework 或 .NET Core：確保設定了相容的 .NET 環境來執行範例。
3. C#基礎：熟悉C#程式語言和.NET中的基本操作。

## 導入命名空間

首先，您需要匯入必要的命名空間。以下是將它們包含在您的項目中的方法：

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

讓我們將在 Word 文件中加入 Bidi 標記的過程分解為清晰的步驟。每個步驟將引導您了解程式碼及其用途。

## 第 1 步：設定您的文檔

首先建立一個新實例`Document`類別和一個`DocumentBuilder`向文件添加內容。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENTS DIRECTORY";

//建立文件並添加內容
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

在此步驟中，您將初始化一個新的 Word 文件並設置`DocumentBuilder`以方便內容插入。

## 第 2 步：將內容新增至文件中

接下來，在文件中添加一些文字。在這裡，我們將添加不同語言的文字來說明 Bidi 文字處理。

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

在這裡，我們首先添加一個標準的英語短語。然後，我們為後續文字（以希伯來語和阿拉伯語編寫）啟用 Bidi 文字格式。這示範如何合併雙向文字。

## 步驟 3：配置 Bidi 標記的儲存選項

為了確保Bidi標記正確保存在文件中，您需要配置`TxtSaveOptions`並啟用`AddBidiMarks`選項。

```csharp
//新增 Bidi 標記
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

在這一步驟中，我們建立一個實例`TxtSaveOptions`並設定`AddBidiMarks`財產給`true`。這可確保將文件另存為文字檔案時包含 Bidi 標記。

## 結論

在處理包含不同文字方向的語言的多語言內容時，在 Word 文件中新增 Bidi 標記可能是至關重要的一步。透過 Aspose.Words for .NET，這個過程既簡單又有效率。透過執行上述步驟，您可以確保您的文件正確表示 Bidi 文本，從而提高可讀性和準確性。

## 常見問題解答

### 什麼是 Bidi 商標以及它們為何如此重要？
雙向標記是用於控製文件中文字方向的特殊字元。它們對於正確顯示從右向左閱讀的語言（例如阿拉伯語和希伯來語）至關重要。

### 我可以使用 Aspose.Words for .NET 處理其他類型的文字方向問題嗎？
是的，Aspose.Words for .NET 為各種文字方向和格式需求提供全面支持，包括從右到左和從左到右語言。

### 是否可以將 Bidi 格式僅應用於文件的特定部分？
是的，您可以根據需要將 Bidi 格式套用至文件的特定段落或部分。

### 我可以將帶有 Bidi 標記的文檔儲存為哪些格式？
在提供的範例中，文件被儲存為文字檔案。但是，Aspose.Words 也支援以各種格式儲存文檔，同時保留 Bidi 標記。

### 在哪裡可以找到有關 Aspose.Words for .NET 的更多資訊？
您可以透過以下方式探索有關 Aspose.Words for .NET 的更多信息[Aspose文檔](https://reference.aspose.com/words/net/)並訪問[支援論壇](https://forum.aspose.com/c/words/8)以獲得更多幫助。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
