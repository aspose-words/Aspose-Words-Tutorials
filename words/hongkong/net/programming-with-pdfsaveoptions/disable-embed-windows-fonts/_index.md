---
"description": "透過使用 Aspose.Words for .NET 停用嵌入字體來減少 PDF 大小。請按照我們的逐步指南優化您的文檔，以實現高效儲存和共用。"
"linktitle": "透過停用嵌入字體來減少 PDF 大小"
"second_title": "Aspose.Words文件處理API"
"title": "透過停用嵌入字體來減少 PDF 大小"
"url": "/zh-hant/net/programming-with-pdfsaveoptions/disable-embed-windows-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 透過停用嵌入字體來減少 PDF 大小

## 介紹

減小 PDF 檔案的大小對於高效儲存和快速共享至關重要。一種有效的方法是停用嵌入字體，尤其是當大多數系統上已經有標準字體時。在本教學中，我們將探討如何使用 Aspose.Words for .NET 停用嵌入字體來減少 PDF 大小。我們將逐步介紹每個步驟，以確保您可以在自己的專案中輕鬆實現這一點。

## 先決條件

在深入研究程式碼之前，請確保您已具備以下條件：

- Aspose.Words for .NET：如果您還沒有，請從 [下載連結](https://releases。aspose.com/words/net/).
- .NET 開發環境：Visual Studio 是個受歡迎的選擇。
- 範例 Word 文件：準備好要轉換為 PDF 的 DOCX 文件。

## 導入命名空間

首先，請確保已將必要的命名空間匯入到專案中。這使您可以存取我們的任務所需的類別和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

讓我們將這個過程分解為簡單、易於管理的步驟。每個步驟都會引導您完成任務，確保您了解每個點發生的情況。

## 步驟 1：初始化文檔

首先，我們需要載入要轉換為 PDF 的 Word 文件。您的旅程從這裡開始。

```csharp
// 文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

這裡， `dataDir` 是您的文件所在目錄的佔位符。代替 `"YOUR DOCUMENT DIRECTORY"` 與實際路徑。

## 步驟 2：設定 PDF 儲存選項

接下來，我們將設定 PDF 儲存選項。在這裡我們指定我們不想嵌入標準 Windows 字型。

```csharp
// 輸出的 PDF 將會被儲存，但不嵌入標準 Windows 字型。
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedNone
};
```

透過設定 `FontEmbeddingMode` 到 `EmbedNone`，我們指示 Aspose.Words 不要在 PDF 中包含這些字體，從而減少檔案大小。

## 步驟 3：將文件儲存為 PDF

最後，我們使用配置的儲存選項將文件儲存為 PDF。這是您的 DOCX 轉換為緊湊 PDF 的關鍵時刻。

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.DisableEmbedWindowsFonts.pdf", saveOptions);
```

代替 `"YOUR DOCUMENT DIRECTORY"` 再次使用您的實際目錄路徑。輸出的 PDF 現在將保存在指定的目錄中，不包含嵌入的標準字體。

## 結論

透過遵循這些步驟，您可以顯著減少 PDF 文件的大小。停用嵌入字體是一種簡單而有效的方法，可以讓您的文件更輕、更易於共享。 Aspose.Words for .NET 讓這個過程變得無縫，確保您可以以最少的努力優化您的檔案。

## 常見問題解答

### 為什麼我應該禁用 PDF 中的嵌入字體？
停用嵌入字體可以顯著減少 PDF 的檔案大小，使其更有效率地儲存和更快地共享。

### 如果沒有嵌入字體，PDF 還能正確顯示嗎？
是的，只要字體是標準的並且在查看 PDF 的系統上可用，它就會正確顯示。

### 我可以選擇性地在 PDF 中嵌入某些字體嗎？
是的，Aspose.Words for .NET 可讓您自訂嵌入的字體，從而靈活地減少檔案大小。

### 我是否需要 Aspose.Words for .NET 來停用 PDF 中的嵌入字體？
是的，Aspose.Words for .NET 提供了在 PDF 中配置字體嵌入選項所需的功能。

### 如果遇到問題，如何獲得支援？
您可以訪問 [支援論壇](https://forum.aspose.com/c/words/8) 為您遇到的任何問題提供協助。



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}