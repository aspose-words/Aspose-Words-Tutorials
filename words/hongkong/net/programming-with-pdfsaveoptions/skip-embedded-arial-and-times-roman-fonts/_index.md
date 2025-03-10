---
title: 透過跳過嵌入的 Arial 和 Times Roman 字體優化 PDF 大小
linktitle: 透過跳過嵌入的 Arial 和 Times Roman 字體優化 PDF 大小
second_title: Aspose.Words 文件處理 API
description: 使用 Aspose.Words for .NET 跳過嵌入的 Arial 和 Times Roman 字體來優化 PDF 大小。請按照此逐步指南來簡化您的 PDF 文件。
weight: 10
url: /zh-hant/net/programming-with-pdfsaveoptions/skip-embedded-arial-and-times-roman-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 透過跳過嵌入的 Arial 和 Times Roman 字體優化 PDF 大小

## 介紹

您是否曾經遇到過 PDF 文件太大的情況？這就像是收拾行李去度假，卻發現你的行李箱已經爆滿了。你知道你需要減肥，但你要放棄什麼？處理 PDF 文件（尤其是從 Word 文件轉換而來的 PDF 文件）時，嵌入字體會使文件大小增大。值得慶幸的是，Aspose.Words for .NET 提供了一個時尚的解決方案來保持您的 PDF 簡潔明了。在本教程中，我們將深入探討如何透過跳過嵌入的 Arial 和 Times Roman 字體來優化 PDF 大小。讓我們開始吧！

## 先決條件

在我們深入討論細節之前，您需要準備一些東西：
-  Aspose.Words for .NET：確保您安裝了這個功能強大的程式庫。如果沒有，您可以從以下位置下載[這裡](https://releases.aspose.com/words/net/).
- 對 C# 的基本了解：這將幫助您理解程式碼片段。
- Word 文件：我們將使用範例文件來示範該過程。 

## 導入命名空間

首先，確保導入了必要的命名空間。這為存取 Aspose.Words 功能奠定了基礎。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

好吧，讓我們一步步分解這個過程。

## 第 1 步：設定您的環境

首先，您需要設定開發環境。開啟您最喜歡的 C# IDE（如 Visual Studio）並建立一個新專案。

## 步驟2：載入Word文檔

下一步是載入要轉換為 PDF 的 Word 文件。確保您的文件位於正確的目錄中。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

在此程式碼片段中，替換`"YOUR DOCUMENT DIRECTORY"`與您的文檔目錄的路徑。

## 步驟 3：設定 PDF 儲存選項

現在，我們需要配置 PDF 儲存選項來控製字體的嵌入方式。預設情況下，所有字體都會嵌入，這會增加檔案大小。我們將更改此設定。

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};
```

## 步驟 4：將文件另存為 PDF

最後，使用指定的儲存選項將文件儲存為 PDF。這就是奇蹟發生的地方。

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.SkipEmbeddedArialAndTimesRomanFonts.pdf", saveOptions);
```

此命令將您的文件儲存為名為「OptimizedPDF.pdf」的 PDF 檔案並儲存在指定目錄中。

## 結論

現在你就擁有了！您剛剛學習如何使用 Aspose.Words for .NET 跳過 Arial 和 Times Roman 字體的嵌入來優化 PDF 檔案大小。這個簡單的調整可以顯著減小檔案大小，使它們更易於共享和儲存。這就像去健身房看 PDF，減輕不必要的重量，同時保持所有必需品完好無損。

## 常見問題解答

### 為什麼我應該跳過嵌入 Arial 和 Times Roman 字體？
跳過這些常見字體可以減少 PDF 檔案的大小，因為大多數系統已經安裝了這些字體。

### 這會影響 PDF 的外觀嗎？
不，不會的。由於 Arial 和 Times Roman 是標準字體，因此外觀在不同系統中保持一致。

### 我也可以跳過嵌入其他字體嗎？
是的，如果需要，您可以配置儲存選項以跳過嵌入其他字體。

### Aspose.Words for .NET 是免費的嗎？
 Aspose.Words for .NET 提供免費試用版，您可以下載[這裡](https://releases.aspose.com/)，但要獲得完全訪問權限，您需要購買許可證[這裡](https://purchase.aspose.com/buy).

### 在哪裡可以找到更多關於 Aspose.Words for .NET 的教學？
您可以找到全面的文件和教程[這裡](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
