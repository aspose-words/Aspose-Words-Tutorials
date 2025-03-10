---
title: 在 PDF 文件中嵌入子集字體
linktitle: 在 PDF 文件中嵌入子集字體
second_title: Aspose.Words 文件處理 API
description: 使用 Aspose.Words for .NET 僅嵌入必要的字體子集來減少 PDF 檔案大小。按照我們的逐步指南有效優化您的 PDF。
weight: 10
url: /zh-hant/net/programming-with-pdfsaveoptions/embedded-subset-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 PDF 文件中嵌入子集字體

## 介紹

您是否注意到某些 PDF 文件比其他文件大得多，即使它們包含相似的內容？罪魁禍首往往在於字體。在 PDF 中嵌入字體可確保它在任何裝置上看起來都相同，但也會使檔案大小增大。幸運的是，Aspose.Words for .NET 提供了一個方便的功能，可以只嵌入必要的字體子集，從而保持 PDF 的精簡和高效。本教學將逐步引導您完成整個過程。

## 先決條件

在我們開始之前，請確保您具備以下條件：

-  Aspose.Words for .NET：您可以下載它[這裡](https://releases.aspose.com/words/net/).
- .NET 環境：確保您有一個有效的 .NET 開發環境。
- C# 基礎知識：熟悉 C# 程式設計將有助於您跟進。

## 導入命名空間

若要使用 Aspose.Words for .NET，您需要在專案中匯入必要的命名空間。將這些添加到 C# 檔案的頂部：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## 第 1 步：載入文檔

首先，我們需要載入要轉換為PDF的Word文件。這是使用以下方法完成的`Document`Aspose.Words 提供的類別。

```csharp
//文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

此程式碼片段載入位於以下位置的文檔`dataDir`。確保更換`"YOUR DOCUMENT DIRECTORY"`與文檔的實際路徑。

## 步驟 2：設定 PDF 儲存選項

接下來我們配置`PdfSaveOptions`以確保僅嵌入必要的字體子集。透過設定`EmbedFullFonts`到`false`，我們告訴 Aspose.Words 僅嵌入文件中使用的字形。

```csharp
//輸出 PDF 將包含文件中字體的子集。
// PDF 字型中僅包含文件中使用的字形。
PdfSaveOptions saveOptions = new PdfSaveOptions { EmbedFullFonts = false };
```

這個小但關鍵的步驟有助於大幅減小 PDF 檔案的大小。

## 步驟 3：將文件另存為 PDF

最後，我們使用以下命令將文件另存為 PDF：`Save`方法，應用配置的`PdfSaveOptions`.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf", saveOptions);
```

此程式碼將產生一個 PDF 文件，其名稱為`WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf`在指定的目錄中，僅嵌入必要的字體子集。

## 結論

現在你就擁有了！透過遵循這些簡單的步驟，您可以使用 Aspose.Words for .NET 僅嵌入必要的字體子集，從而有效地減少 PDF 檔案的大小。這不僅可以節省儲存空間，還可以確保更快的載入時間和更好的效能，特別是對於具有大量字體的文件。

## 常見問題解答

### 為什麼我應該只在 PDF 中嵌入字體子集？
僅嵌入必要的字體子集可以顯著減小 PDF 文件大小，而不會影響文件的外觀和可讀性。

### 如果需要，我可以恢復嵌入完整字體嗎？
是的，你可以。只需設定`EmbedFullFonts`財產給`true`在`PdfSaveOptions`.

### Aspose.Words for .NET 支援其他 PDF 最佳化功能嗎？
絕對地！ Aspose.Words for .NET 提供了一系列用於最佳化 PDF 的選項，包括圖片壓縮和刪除未使用的物件。

### 使用 Aspose.Words for .NET 可以嵌入哪些類型的字體子集？
Aspose.Words for .NET 支援文件中使用的所有 TrueType 字體的子集嵌入。

### 如何驗證 PDF 中嵌入了哪些字體？
您可以在 Adobe Acrobat Reader 中開啟 PDF，然後檢查「字型」標籤下的屬性以查看嵌入的字型。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
