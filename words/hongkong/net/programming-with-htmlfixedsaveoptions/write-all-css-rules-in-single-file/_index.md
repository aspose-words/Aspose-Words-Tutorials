---
title: 將所有 CSS 規則寫入單一文件
linktitle: 將所有 CSS 規則寫入單一文件
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 將 Word 文件轉換為 HTML，並將所有 CSS 規則放在單一檔案中，以實現更清晰的程式碼和更輕鬆的維護。
weight: 10
url: /zh-hant/net/programming-with-htmlfixedsaveoptions/write-all-css-rules-in-single-file/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將所有 CSS 規則寫入單一文件

## 介紹

將 Word 文件轉換為 HTML 時，您是否曾發現自己陷入了散落各處的 CSS 規則網絡中？不用擔心！今天，我們將深入研究 Aspose.Words for .NET 的一個巧妙功能，它允許您在單一檔案中編寫所有 CSS 規則。這不僅可以整理您的程式碼，還可以讓您的生活變得更加輕鬆。繫好安全帶，讓我們開始這段更乾淨、更有效率的 HTML 輸出之旅吧！

## 先決條件

在我們深入討論實際問題之前，讓我們先把事情做好。以下是您開始使用時所需要的：

1.  Aspose.Words for .NET：請確定您擁有 Aspose.Words for .NET 函式庫。如果您還沒有，您可以[在這裡下載](https://releases.aspose.com/words/net/).
2. .NET 開發環境：您需要在電腦上設定 .NET 開發環境。 Visual Studio 是個受歡迎的選擇。
3. C# 基礎知識：對 C# 程式設計的基本了解會很有幫助。
4. Word 文件：準備好要轉換的 Word 文件 (.docx)。

## 導入命名空間

首先，讓我們在 C# 專案中導入必要的命名空間。這將使我們能夠輕鬆存取 Aspose.Words 功能。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

好吧，讓我們將這個過程分解為易於遵循的步驟。每個步驟將引導您完成流程的特定部分，以確保一切順利進行。

## 第 1 步：設定您的文件目錄

首先，我們需要定義文檔目錄的路徑。這是您的 Word 文件的儲存位置以及轉換後的 HTML 的儲存位置。

```csharp
//文檔目錄的存取路徑
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## 步驟2：載入Word文檔

接下來，我們載入要轉換為 HTML 的 Word 文件。這是使用以下方法完成的`Document`來自 Aspose.Words 庫的類別。

```csharp
//載入Word文檔
Document doc = new Document(dataDir + "Document.docx");
```

## 步驟 3：設定 HTML 儲存選項

現在，我們需要配置 HTML 儲存選項。具體來說，我們希望啟用將所有 CSS 規則寫入單一檔案的功能。這是透過設定來實現的`SaveFontFaceCssSeparately`財產給`false`.

```csharp
//使用「將所有 CSS 規則寫入一個檔案」功能配置備份選項
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions 
{ 
    SaveFontFaceCssSeparately = false 
};
```

## 步驟 4：將文件轉換為固定 HTML

最後，我們使用配置的儲存選項將文件儲存為 HTML 文件。此步驟可確保所有 CSS 規則都寫入單一檔案中。

```csharp
//將文檔轉換為固定 HTML
doc.Save(dataDir + "WorkingWithHtmlFixedSaveOptions.WriteAllCssRulesInSingleFile.html", saveOptions);
```

## 結論

現在你就擁有了！只需幾行程式碼，您就可以成功地將 Word 文件轉換為 HTML，並將所有 CSS 規則整齊地組織在一個檔案中。這種方法不僅簡化了 CSS 管理，還增強了 HTML 文件的可維護性。因此，下次您執行轉換 Word 文件的任務時，您就知道如何保持文件整潔！

## 常見問題解答

### 為什麼我應該為 HTML 輸出使用單一 CSS 檔案？
使用單一 CSS 檔案可以簡化樣式的管理和維護。它使您的 HTML 更清晰、更有效率。

### 如果需要，我可以分離字體 CSS 規則嗎？
是的，透過設定`SaveFontFaceCssSeparately`到`true`，您可以將字體 CSS 規則分離到不同的文件中。

### Aspose.Words for .NET 可以免費使用嗎？
 Aspose.Words 提供免費試用版，您可以[在這裡下載](https://releases.aspose.com/)。如需繼續使用，請考慮購買許可證[這裡](https://purchase.aspose.com/buy).

### Aspose.Words for .NET 還可以轉換為哪些其他格式？
Aspose.Words for .NET 支援各種格式，包括 PDF、TXT 以及 JPEG 和 PNG 等圖片格式。

### 在哪裡可以找到更多有關 Aspose.Words for .NET 的資源？
查看[文件](https://reference.aspose.com/words/net/)取得全面的指南和 API 參考。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
