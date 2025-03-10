---
title: 透過不嵌入核心字體來減少 PDF 文件大小
linktitle: 透過不嵌入核心字體來減少 PDF 文件大小
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 透過不嵌入核心字體來減少 PDF 檔案大小。請按照我們的逐步指南來優化您的 PDF。
weight: 10
url: /zh-hant/net/programming-with-pdfsaveoptions/avoid-embedding-core-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 透過不嵌入核心字體來減少 PDF 文件大小

## 介紹

您是否曾經發現自己摸不著頭腦，想知道為什麼您的 PDF 檔案如此之大？嗯，你並不孤單。一個常見的罪魁禍首是嵌入 Arial 和 Times New Roman 等核心字體。幸運的是，Aspose.Words for .NET 有一個巧妙的方法來解決這個問題。在本教程中，我將向您展示如何透過避免嵌入這些核心字體來減少 PDF 文件大小。讓我們開始吧！

## 先決條件

在我們踏上這段令人興奮的旅程之前，讓我們確保您已擁有所需的一切。這是一個快速清單：

-  Aspose.Words for .NET：請確定您已安裝 Aspose.Words for .NET。如果您還沒有，可以下載[這裡](https://releases.aspose.com/words/net/).
- 開發環境：您需要一個開發環境，例如 Visual Studio。
- Word 文件：本教學將使用 Word 文件（例如「Rendering.docx」）。
- 基本 C# 知識：對 C# 的基本了解將幫助您跟進。

好了，一切準備就緒，讓我們進入正題吧！

## 導入命名空間

首先，讓我們導入必要的名稱空間。此步驟確保我們能夠存取我們需要的所有 Aspose.Words 功能。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## 第 1 步：初始化您的文件目錄

在開始操作文檔之前，我們需要指定儲存文檔的目錄。這對於存取文件至關重要。

```csharp
//文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替`"YOUR DOCUMENT DIRECTORY"`與您的Word文件所在的實際路徑。

## 步驟2：載入Word文檔

接下來，我們需要載入要轉換為 PDF 的 Word 文件。在此範例中，我們使用名為「Rendering.docx」的文件。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

這行程式碼將文件載入到記憶體中，準備進一步處理。

## 步驟 3：設定 PDF 儲存選項

現在神奇的部分來了！我們將配置 PDF 儲存選項以避免嵌入核心字體。這是有助於減小 PDF 檔案大小的關鍵步驟。

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    UseCoreFonts = true
};
```

環境`UseCoreFonts`到`true`確保 Arial 和 Times New Roman 等核心字體不會嵌入 PDF 中，從而顯著減少檔案大小。

## 步驟 4：將文件另存為 PDF

最後，我們使用配置的儲存選項將 Word 文件儲存為 PDF。此步驟產生 PDF 文件，但不嵌入核心字體。

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.AvoidEmbeddingCoreFonts.pdf", saveOptions);
```

現在你就擁有了！您的 PDF 檔案現在保存在指定的目錄中，沒有那些龐大的核心字體。

## 結論

使用 Aspose.Words for .NET 可以輕鬆縮小 PDF 檔案大小。透過避免嵌入核心字體，您可以顯著減小檔案大小，從而更輕鬆地共用和儲存文件。我希望本教程對您有所幫助，並使您清楚地了解該過程。請記住，小小的調整可以帶來很大的不同！

## 常見問題解答

### 為什麼我應該避免在 PDF 中嵌入核心字體？
避免嵌入核心字體可以減小檔案大小，從而更容易共享和儲存。

### 在沒有嵌入核心字體的情況下我仍然可以正確查看 PDF 嗎？
是的，Arial 和 Times New Roman 等核心字體通常在大多數系統上可用。

### 如果我需要嵌入自訂字體怎麼辦？
您可以自訂`PdfSaveOptions`根據需要嵌入特定字體。

### Aspose.Words for .NET 可以免費使用嗎？
 Aspose.Words for .NET 需要授權。您可以獲得免費試用[這裡](https://releases.aspose.com/).

### 在哪裡可以找到有關 Aspose.Words for .NET 的更多文件？
你可以找到詳細的文檔[這裡](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
