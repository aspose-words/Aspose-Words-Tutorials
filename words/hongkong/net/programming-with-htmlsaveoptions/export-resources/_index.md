---
title: 出口資源
linktitle: 出口資源
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 匯出 CSS 和字體等資源，同時將 Word 文件儲存為 HTML。請遵循我們的逐步指南。
weight: 10
url: /zh-hant/net/programming-with-htmlsaveoptions/export-resources/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 出口資源

## 介紹

嘿，科技愛好者朋友們！如果您發現自己需要將 Word 文件轉換為 HTML，那麼您來對地方了。今天，我們將深入探討 Aspose.Words for .NET 的奇妙世界。這個功能強大的程式庫使得以程式設計方式處理 Word 文件變得輕而易舉。在本教學中，我們將逐步介紹使用 Aspose.Words for .NET 將 Word 文件儲存為 HTML 時匯出資源（例如字體和 CSS）的步驟。繫好安全帶，享受有趣、資訊豐富的旅程！

## 先決條件

在我們深入研究程式碼之前，讓我們確保您已具備開始使用所需的一切。這是一個快速清單：

1.  Visual Studio：確保您的電腦上安裝了 Visual Studio。您可以從[視覺工作室網站](https://visualstudio.microsoft.com/).
2. Aspose.Words for .NET：您需要 Aspose.Words for .NET 函式庫。如果您還沒有獲得，請從以下位置取得免費試用版[Aspose 發布](https://releases.aspose.com/words/net/)或從[阿斯普斯商店](https://purchase.aspose.com/buy).
3. C# 基礎知識：對 C# 的基本了解將幫助您理解程式碼範例。

明白了嗎？偉大的！讓我們繼續導入必要的命名空間。

## 導入命名空間

若要使用 Aspose.Words for .NET，您需要在專案中包含相關的命名空間。操作方法如下：

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

這些命名空間對於存取我們將在教程中使用的 Aspose.Words 類別和方法至關重要。

讓我們分解一下將 Word 文件另存為 HTML 時匯出資源的過程。我們將逐步進行，因此很容易遵循。

## 第 1 步：設定您的文件目錄

首先，您需要指定文檔目錄的路徑。這是您的 Word 文件所在的位置以及 HTML 文件的儲存位置。

```csharp
//文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替`"YOUR DOCUMENT DIRECTORY"`與目錄的實際路徑。

## 步驟2：載入Word文檔

接下來，讓我們載入要轉換為 HTML 的 Word 文件。在本教程中，我們將使用名為的文檔`Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

這行程式碼從指定目錄載入文件。

## 步驟 3：設定 HTML 儲存選項

要匯出CSS、字體等資源，需要配置`HtmlSaveOptions`。此步驟對於確保 HTML 輸出結構良好並包含必要的資源至關重要。

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
- `ResourceFolder = dataDir + "Resources"`：指定保存資源（如字體和 CSS 檔案）的本機資料夾。
- `ResourceFolderAlias = "http://example.com/resources"`：為資源資料夾設定別名，該別名將在 HTML 檔案中使用。

## 步驟 4：將文件另存為 HTML

配置儲存選項後，最後一步是將文件儲存為 HTML 檔案。操作方法如下：

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

這行程式碼以 HTML 格式儲存文件以及匯出的資源。

## 結論

現在你就擁有了！您已成功匯出資源，同時使用 Aspose.Words for .NET 將 Word 文件儲存為 HTML。有了這個強大的庫，以程式設計方式處理 Word 文件變得輕而易舉。無論您是在開發網頁應用程式還是只需要轉換文件以供離線使用，Aspose.Words 都能滿足您的需求。

## 常見問題解答

### 我可以導出圖像以及字體和 CSS 嗎？
是的，你可以！ Aspose.Words for .NET 也支援匯出影像。只需確保配置`HtmlSaveOptions`因此。

### 有沒有辦法嵌入 CSS 而不是使用外部樣式表？
絕對地。您可以設定`CssStyleSheetType`到`CssStyleSheetType.Embedded`如果您喜歡嵌入式樣式。

### 如何自訂輸出 HTML 檔案的名稱？
您可以在其中指定任何您喜歡的檔案名`doc.Save`方法。例如，`doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### Aspose.Words 是否支援 HTML 以外的其他格式？
是的，它支援多種格式，包括 PDF、DOCX、TXT 等。查看[文件](https://reference.aspose.com/words/net/)以獲得完整清單。

### 我可以從哪裡獲得更多支援和資源？
如需更多協助，請訪問[Aspose.Words 支援論壇](https://forum.aspose.com/c/words/8)。您也可以在以下位置找到詳細的文件和範例[阿斯普斯網站](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
