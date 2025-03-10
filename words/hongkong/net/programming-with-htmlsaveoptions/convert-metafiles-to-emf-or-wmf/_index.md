---
title: 將圖元檔轉換為 Emf 或 Wmf
linktitle: 將圖元檔轉換為 Emf 或 Wmf
second_title: Aspose.Words 文件處理 API
description: 使用 Aspose.Words for .NET 將文件轉換為 HTML 時將圖元檔案轉換為 EMF 或 WMF 格式的逐步指南。
weight: 10
url: /zh-hant/net/programming-with-htmlsaveoptions/convert-metafiles-to-emf-or-wmf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將圖元檔轉換為 Emf 或 Wmf

## 介紹

歡迎再次深入了解 Aspose.Words for .NET 的世界。今天，我們正在解決一個巧妙的技巧：將 Word 文件中的 SVG 圖像轉換為 EMF 或 WMF 格式。這聽起來可能有點技術性，但不用擔心。學完本教學後，您將成為這方面的專家。無論您是經驗豐富的開發人員還是剛開始使用 Aspose.Words for .NET，本指南都將逐步引導您完成您需要了解的所有內容。

## 先決條件

在我們深入研究程式碼之前，讓我們確保一切都已設定完畢。這是您需要的：

1.  Aspose.Words for .NET Library：確保您擁有最新版本。如果沒有，您可以從以下位置下載[這裡](https://releases.aspose.com/words/net/).
2. .NET Framework：請確定您的電腦上安裝了 .NET Framework。
3. 開發環境：像 Visual Studio 這樣的 IDE 會讓您的生活更輕鬆。
4. C# 基礎知識：您不需要成為專家，但基本了解會有所幫助。

東西都齊全了嗎？偉大的！讓我們開始吧。

## 導入命名空間

首先，我們需要導入必要的名稱空間。這很重要，因為它告訴我們的程式在哪裡可以找到我們將使用的類別和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

這些命名空間涵蓋了從基本系統功能到本教學所需的特定 Aspose.Words 功能的所有內容。

## 第 1 步：設定您的文件目錄

讓我們先定義文檔目錄的路徑。這是我們轉換圖元檔案後儲存您的 Word 文件的位置。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替`"YOUR DOCUMENT DIRECTORY"`與您要儲存文件的實際路徑。

## 第 2 步：使用 SVG 建立 HTML 字串

接下來，我們需要一個包含要轉換的 SVG 圖像的 HTML 字串。這是一個簡單的例子：

```csharp
string html = 
    @"<html>
        <svg xmlns='http://www.w3.org/2000/svg' width='500' height='40' viewBox='0 0 500 40'>
            <text x='0' y='35' font-family='Verdana' font-size='35'>Hello world!</text>
        </svg>
    </html>";
```

此 HTML 程式碼片段包含一個基本的 SVG，內容為「Hello world!」。

## 步驟 3：使用 ConvertSvgToEmf 選項載入 HTML

現在，我們使用`HtmlLoadOptions`指定我們希望如何處理 HTML 中的 SVG 圖像。環境`ConvertSvgToEmf`到`true`確保 SVG 影像轉換為 EMF 格式。

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { ConvertSvgToEmf = true };
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

這段程式碼創造了一個新的`Document`透過使用指定的載入選項將 HTML 字串載入到物件中。

## 步驟 4：設定圖元檔案格式的 HtmlSaveOptions

為了使用正確的圖元文件格式儲存文檔，我們使用`HtmlSaveOptions`。在這裡，我們設定`MetafileFormat`到`HtmlMetafileFormat.Png`，但你可以將其更改為`Emf`或者`Wmf`根據您的需求。

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { MetafileFormat = HtmlMetafileFormat.Png };
```

## 第 5 步：儲存文檔

最後，我們使用指定的儲存選項來儲存文件。

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToPng.html", saveOptions);
```

這會將文件保存在指定的目錄中，並按照定義轉換圖元文件格式。

## 結論

現在你就擁有了！透過執行這些步驟，您已使用 Aspose.Words for .NET 在 Word 文件中成功將 SVG 文件轉換為 EMF 或 WMF 格式。此方法可以方便地確保相容性並保持文件在不同平台上的視覺完整性。快樂編碼！

## 常見問題解答

### 我可以使用此方法轉換其他圖像格式嗎？
是的，您可以透過相應調整載入和儲存選項來轉換各種圖像格式。

### 是否需要使用特定的 .NET Framework 版本？
Aspose.Words for .NET 支援多個 .NET Framework 版本，但使用最新版本以獲得最佳相容性和功能始終是一個好主意。

### 將 SVG 轉換為 EMF 或 WMF 有什麼優勢？
將 SVG 轉換為 EMF 或 WMF 可確保在可能不完全支援 SVG 的環境中正確保留和渲染向量圖形。

### 我可以針對多個文件自動執行此程序嗎？
絕對地！您可以循環存取多個 HTML 文件，應用相同的過程來自動進行批次轉換。

### 在哪裡可以找到更多有關 Aspose.Words for .NET 的資源和支援？
您可以找到全面的文檔[這裡](https://reference.aspose.com/words/net/)並獲得 Aspose 社區的支持[這裡](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
