---
"description": "透過本全面的逐步指南了解如何在 Aspose.Words for .NET 中設定自訂字體資料夾。非常適合希望增強文件字體的開發人員。"
"linktitle": "設定字體資料夾"
"second_title": "Aspose.Words文件處理API"
"title": "設定字體資料夾"
"url": "/zh-hant/net/working-with-fonts/set-fonts-folders/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 設定字體資料夾

## 介紹

嘿！準備好深入了解 Aspose.Words for .NET 中的自訂字體世界了嗎？讓我們開始吧。本教學將引導您完成設定自訂字型資料夾的過程，確保您的文件看起來符合您的要求。無論您是經驗豐富的開發人員還是剛起步，本指南都會引導您完成每個步驟。所以，讓我們讓這些字體看起來棒極了！

## 先決條件

在我們開始之前，讓我們確保您擁有所需的一切：

- Aspose.Words for .NET：您可以 [下載](https://releases.aspose.com/words/net/) 如果你還沒有這樣做的話。
- Visual Studio：任何版本都可以，但最新的總是最好的。
- 文件：本教學中我們將使用 Word 文件。您可以創建自己的或使用現有的。
- 自訂字體：準備一些自訂字體。我們將使用這些來示範如何設定字體資料夾。

## 導入命名空間

首先，讓我們導入必要的命名空間。這對於存取 Aspose.Words 所需的類別和方法至關重要。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

匯入這些命名空間後，我們就可以開始設定自訂字體資料夾了。

## 步驟 1：定義文件目錄

讓我們先定義文檔目錄的路徑。這是儲存您的 Word 文件的地方。我們將使用一個名為 `dataDir` 儲存此路徑。

```csharp
// 文檔目錄的路徑 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替 `"YOUR DOCUMENT DIRECTORY"` 使用目錄的實際路徑。這很關鍵，因為 Aspose.Words 需要知道在哪裡找到您的文件。

## 步驟2：設定字體來源

接下來，我們需要設定字體來源。在這裡我們告訴 Aspose.Words 在哪裡找到我們的自訂字體。我們將使用 `FontSettings.DefaultInstance.SetFontsSources` 方法來實現這一點。

```csharp
FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
	new SystemFontSource(), new FolderFontSource("C:\\MyFonts\\", true)
});
```

以下是我們正在做的事情：

- SystemFontSource：這告訴 Aspose.Words 使用系統的預設字體。
- FolderFontSource：這是我們指定包含自訂字體的資料夾的地方。代替 `"C:\\MyFonts\\"` 使用您的自訂字體目錄的路徑。這 `true` 參數表示也應包括子目錄。

## 步驟3：載入文檔

現在我們已經設定了字體來源，是時候載入我們想要處理的文件了。我們將使用 `Document` 來自 Aspose.Words 的類別。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

確保 `"Rendering.docx"` 是您的 Word 文件的名稱。如果您的文件有不同的名稱，請確保相應地更新。

## 步驟 4：將文件儲存為 PDF

最後，讓我們將文件儲存為 PDF 以查看自訂字體的實際效果。我們將使用 `Save` 方法 `Document` 班級。

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFolders.pdf");
```

這將使用我們先前設定的自訂字體將您的文件儲存為指定目錄中的 PDF。

## 結論

就是這樣！您已成功在 Aspose.Words for .NET 中設定自訂字體資料夾，並使用自訂字體將文件儲存為 PDF。很酷吧？自訂字體可以使您的文件的外觀發生巨大的變化，現在您知道該如何操作了。編碼愉快！

## 常見問題解答

### 如何安裝 Aspose.Words for .NET？

你可以 [下載](https://releases.aspose.com/words/net/) 從網站上取得最新版本的 Aspose.Words for .NET。

### 我可以使用多個自訂字體資料夾嗎？

是的，您可以新增多個 `FolderFontSource` 實例 `SetFontsSources` 使用不同目錄的字體的方法。

### 是否需要包含系統字體？

包括系統字體是可選的，但建議確保所有標準字體都可用。

### Aspose.Words 支援哪些文件類型？

Aspose.Words 支援多種檔案格式，包括 DOCX、DOC、PDF、TXT、HTML 等。

### 如何取得 Aspose.Words 的臨時授權？

您可以獲得 [臨時執照](https://purchase.aspose.com/temporary-license/) 從 Aspose 網站試用 Aspose.Words 的完整功能。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}