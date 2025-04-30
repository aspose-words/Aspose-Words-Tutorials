---
"description": "使用 Aspose.Words for .NET 將文件轉換為 HTML 時，將元檔案轉換為 EMF 或 WMF 格式的逐步指南。"
"linktitle": "將圖元檔轉換為 Emf 或 Wmf"
"second_title": "Aspose.Words文件處理API"
"title": "將圖元檔轉換為 Emf 或 Wmf"
"url": "/zh-hant/net/programming-with-htmlsaveoptions/convert-metafiles-to-emf-or-wmf/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 將圖元檔轉換為 Emf 或 Wmf

## 介紹

歡迎深入了解 Aspose.Words for .NET 的世界。今天，我們要講解一個巧妙的技巧：在 Word 文件中將 SVG 影像轉換為 EMF 或 WMF 格式。這聽起來可能有點技術性，但別擔心。完成本教學後，您將成為這方面的專家。無論您是經驗豐富的開發人員還是剛開始使用 Aspose.Words for .NET，本指南都會逐步引導您了解所有需要了解的內容。

## 先決條件

在深入研究程式碼之前，讓我們確保一切都已設定好。您需要：

1. Aspose.Words for .NET Library：確保您擁有最新版本。如果你沒有，你可以從 [這裡](https://releases。aspose.com/words/net/).
2. .NET Framework：確保您的機器上安裝了 .NET Framework。
3. 開發環境：像 Visual Studio 這樣的 IDE 將使您的生活更輕鬆。
4. C# 基礎知識：您不需要成為專家，但基本的了解會有所幫助。

都拿到了嗎？偉大的！讓我們開始吧。

## 導入命名空間

首先，我們需要導入必要的命名空間。這很關鍵，因為它告訴我們的程式在哪裡可以找到我們將要使用的類別和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

這些命名空間涵蓋了從基本系統功能到本教學所需的特定 Aspose.Words 功能的所有內容。

## 步驟 1：設定文檔目錄

讓我們先定義文檔目錄的路徑。當我們轉換圖元檔案後，您的 Word 文件將保存在這裡。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替 `"YOUR DOCUMENT DIRECTORY"` 使用您想要儲存文件的實際路徑。

## 步驟 2：使用 SVG 建立 HTML 字串

接下來，我們需要一個包含要轉換的 SVG 圖像的 HTML 字串。這是一個簡單的例子：

```csharp
string html = 
    @"<html>
        <svg xmlns='http://www.w3.org/2000/svg' width='500' height='40' viewBox='0 0 500 40'>
            <text x='0' y='35' font-family='Verdana' font-size='35'>Hello world!</text>
        </svg>
    </html>";
```

此 HTML 程式碼片段包含一個基本的 SVG，內容為「Hello world！」。

## 步驟3：使用ConvertSvgToEmf選項載入HTML

現在，我們使用 `HtmlLoadOptions` 指定我們如何在 HTML 中處理 SVG 圖像。環境 `ConvertSvgToEmf` 到 `true` 確保 SVG 影像轉換為 EMF 格式。

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { ConvertSvgToEmf = true };
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

此程式碼片段建立一個新的 `Document` 透過使用指定的載入選項將 HTML 字串載入到物件中。

## 步驟 4：設定圖元檔案格式的 HtmlSaveOptions

為了使用正確的圖元文件格式儲存文檔，我們使用 `HtmlSaveOptions`。在這裡，我們設定 `MetafileFormat` 到 `HtmlMetafileFormat.Png`，但你可以將其更改為 `Emf` 或者 `Wmf` 取決於您的需求。

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { MetafileFormat = HtmlMetafileFormat.Png };
```

## 步驟5：儲存文檔

最後，我們使用指定的儲存選項來儲存文件。

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToPng.html", saveOptions);
```

這會將文件保存在指定的目錄中，並以定義的方式轉換圖元文件格式。

## 結論

就是這樣！透過遵循這些步驟，您已成功使用 Aspose.Words for .NET 將 Word 文件中的 SVG 影像轉換為 EMF 或 WMF 格式。此方法可方便地確保相容性並維護文件在不同平台上的視覺完整性。編碼愉快！

## 常見問題解答

### 我可以使用此方法轉換其他圖像格式嗎？
是的，您可以透過相應地調整載入和儲存選項來轉換各種圖像格式。

### 是否必須使用特定的 .NET Framework 版本？
Aspose.Words for .NET 支援多個 .NET Framework 版本，但為了獲得最佳相容性和功能，最好使用最新版本。

### 將 SVG 轉換為 EMF 或 WMF 有什麼好處？
將 SVG 轉換為 EMF 或 WMF 可確保向量圖形在可能不完全支援 SVG 的環境中正確保存和呈現。

### 我可以針對多個文件自動執行此程序嗎？
絕對地！您可以循環遍歷多個 HTML 文件，套用相同的程序來自動執行批次的轉換。

### 在哪裡可以找到更多有關 Aspose.Words for .NET 的資源和支援？
您可以找到全面的文檔 [這裡](https://reference.aspose.com/words/net/) 並獲得 Aspose 社區的支持 [這裡](https://forum。aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}