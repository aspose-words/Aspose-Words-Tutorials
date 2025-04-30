---
"description": "了解如何使用 Aspose.Words for .NET 將 Word 文件儲存為 HTML 並匯出 CSS 和字體等資源。請按照我們的逐步指南進行操作。"
"linktitle": "出口資源"
"second_title": "Aspose.Words文件處理API"
"title": "出口資源"
"url": "/zh-hant/net/programming-with-htmlsaveoptions/export-resources/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 出口資源

## 介紹

嘿，技術愛好者們！如果您發現自己需要將 Word 文件轉換為 HTML，那麼您來對地方了。今天，我們將深入探索 Aspose.Words for .NET 的奇妙世界。這個強大的程式庫使得以程式設計方式處理 Word 文件變得輕而易舉。在本教學中，我們將介紹使用 Aspose.Words for .NET 將 Word 文件儲存為 HTML 時匯出資源（如字體和 CSS）的步驟。繫好安全帶，享受有趣且知識豐富的旅程！

## 先決條件

在深入研究程式碼之前，讓我們確保您已經擁有開始所需的一切。以下是一份快速清單：

1. Visual Studio：確保您的機器上安裝了 Visual Studio。您可以從 [Visual Studio 網站](https://visualstudio。microsoft.com/).
2. Aspose.Words for .NET：您需要 Aspose.Words for .NET 函式庫。如果你還沒有，可以免費試用 [Aspose 版本](https://releases.aspose.com/words/net/) 或從 [Aspose 商店](https://purchase。aspose.com/buy).
3. C# 基礎知識：對 C# 的基本了解將幫助您理解程式碼範例。

明白了嗎？偉大的！讓我們繼續導入必要的命名空間。

## 導入命名空間

若要使用 Aspose.Words for .NET，您需要在專案中包含相關的命名空間。以下是操作方法：

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

這些命名空間對於存取我們將在教程中使用的 Aspose.Words 類別和方法至關重要。

讓我們分解一下將 Word 文件儲存為 HTML 時匯出資源的過程。我們將一步一步地進行，以便於理解。

## 步驟 1：設定文檔目錄

首先，您需要指定文檔目錄的路徑。這是您的 Word 文件所在的位置，也是 HTML 文件的儲存位置。

```csharp
// 文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替 `"YOUR DOCUMENT DIRECTORY"` 使用目錄的實際路徑。

## 第 2 步：載入 Word 文檔

接下來，讓我們載入要轉換為 HTML 的 Word 文件。在本教程中，我們將使用名為 `Rendering。docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

這行程式碼從指定目錄載入文件。

## 步驟 3：設定 HTML 儲存選項

要匯出 CSS 和字體等資源，您需要配置 `HtmlSaveOptions`。此步驟對於確保您的 HTML 輸出結構良好並包含必要的資源至關重要。

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://example.com/resources”
};
```

讓我們分解一下每個選項的作用：
- `CssStyleSheetType = CssStyleSheetType.External`：此選項指定 CSS 樣式應保存在外部樣式表中。
- `ExportFontResources = true`：這可以導出字體資源。
- `ResourceFolder = dataDir + "Resources"`：指定將保存資源（如字體和 CSS 檔案）的本機資料夾。
- `ResourceFolderAlias = "http://example.com/resources"`：設定資源資料夾的別名，該別名將在HTML檔案中使用。

## 步驟 4：將文件儲存為 HTML

配置儲存選項後，最後一步是將文件儲存為 HTML 檔案。以下是操作方法：

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

這行程式碼將文件與匯出的資源一起以 HTML 格式儲存。

## 結論

就是這樣！您已成功使用 Aspose.Words for .NET 將 Word 文件儲存為 HTML 並匯出資源。有了這個強大的庫，以程式設計方式處理 Word 文件就變得輕而易舉了。無論您正在開發 Web 應用程式還是只需要轉換文件以供離線使用，Aspose.Words 都能滿足您的需求。

## 常見問題解答

### 我可以將圖像與字體和 CSS 一起導出嗎？
是的，你可以！ Aspose.Words for .NET 也支援匯出影像。只需確保配置 `HtmlSaveOptions` 因此。

### 有沒有辦法嵌入 CSS 而不是使用外部樣式表？
絕對地。您可以設定 `CssStyleSheetType` 到 `CssStyleSheetType.Embedded` 如果您喜歡嵌入式樣式。

### 如何自訂輸出 HTML 檔案的名稱？
您可以在 `doc.Save` 方法。例如， `doc。Save(dataDir + "CustomFileName.html", saveOptions);`.

### Aspose.Words 除了 HTML 之外還支援其他格式嗎？
是的，它支援各種格式，包括 PDF、DOCX、TXT 等。查看 [文件](https://reference.aspose.com/words/net/) 以取得完整清單。

### 我可以在哪裡獲得更多支援和資源？
如需更多協助，請訪問 [Aspose.Words 支援論壇](https://forum.aspose.com/c/words/8)。您還可以在 [Aspose 網站](https://reference。aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}