---
title: 將 Word 文件頁首頁腳書籤匯出至 PDF 文檔
linktitle: 將 Word 文件頁首頁腳書籤匯出至 PDF 文檔
second_title: Aspose.Words 文件處理 API
description: 透過我們的逐步指南，了解如何使用 Aspose.Words for .NET 將頁首和頁尾書籤從 Word 文件匯出為 PDF。
weight: 10
url: /zh-hant/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將 Word 文件頁首頁腳書籤匯出至 PDF 文檔

## 介紹

將 Word 文件轉換為 PDF 是一項常見任務，尤其是當您想要共用或存檔文件同時保留其格式時。有時，這些文件的頁首和頁尾中包含重要的書籤。在本教學中，我們將逐步介紹使用 Aspose.Words for .NET 將這些書籤從 Word 文件匯出到 PDF 的過程。

## 先決條件

在我們深入之前，請確保您具備以下條件：

- Aspose.Words for .NET：您需要安裝 Aspose.Words for .NET。您可以從以下位置下載：[這裡](https://releases.aspose.com/words/net/).
- 開發環境：設定您的開發環境。您可以使用 Visual Studio 或任何其他 .NET 相容 IDE。
- C# 基礎知識：需要熟悉 C# 程式設計才能理解程式碼範例。

## 導入命名空間

首先，您需要在 C# 專案中匯入必要的命名空間。在程式碼檔案的頂部新增這些行：

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

讓我們將這個過程分解為易於遵循的步驟。

## 步驟1：初始化文檔

第一步是載入 Word 文件。您可以這樣做：

```csharp
//文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

在此步驟中，您只需指定文件目錄的路徑並載入 Word 文件。

## 步驟 2：設定 PDF 儲存選項

接下來，您需要設定 PDF 儲存選項，以確保頁首和頁尾中的書籤正確匯出。

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

在這裡，我們正在設置`PdfSaveOptions`。這`DefaultBookmarksOutlineLevel`屬性設定書籤的大綱級別，並且`HeaderFooterBookmarksExportMode`屬性確保僅匯出頁首和頁尾中第一次出現的書籤。

## 步驟 3：將文件另存為 PDF

最後，使用配置的選項將文件另存為 PDF。

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

在此步驟中，您將使用您配置的選項將文件儲存到指定路徑。

## 結論

現在你就擁有了！透過執行以下步驟，您可以使用 Aspose.Words for .NET 輕鬆將書籤從 Word 文件的頁首和頁尾匯出到 PDF。此方法可確保文件中的重要導覽協助以 PDF 格式保留，從而使讀者更輕鬆地瀏覽文件。

## 常見問題解答

### 我可以將 Word 文件中的所有書籤匯出為 PDF 嗎？

是的，你可以。在`PdfSaveOptions`，您可以根據需要調整設定以包含所有書籤。

### 如果我還想從文件正文匯出書籤怎麼辦？

您可以配置`OutlineOptions`在`PdfSaveOptions`包括文檔正文中的書籤。

### 是否可以自訂 PDF 中的書籤等級？

絕對地！您可以自訂`DefaultBookmarksOutlineLevel`屬性為您的書籤設定不同的大綱層級。

### 如何處理沒有書籤的文件？

如果您的文件沒有書籤，則產生的 PDF 將不帶任何書籤輪廓。如果您需要在 PDF 中加入書籤，請確保您的文件包含書籤。

### 我可以將此方法用於其他文件類型（例如 DOCX 或 RTF）嗎？

是的，Aspose.Words for .NET 支援各種文件類型，包括 DOCX、RTF 等。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
