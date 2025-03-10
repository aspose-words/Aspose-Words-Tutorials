---
title: 設定字體資料夾
linktitle: 設定字體資料夾
second_title: Aspose.Words 文件處理 API
description: 透過這份全面的逐步指南，了解如何在 Aspose.Words for .NET 中設定自訂字體資料夾。非常適合希望增強文件字體的開發人員。
weight: 10
url: /zh-hant/net/working-with-fonts/set-fonts-folders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 設定字體資料夾

## 介紹

嘿！準備好進入 Aspose.Words for .NET 中的自訂字體世界了嗎？讓我們開始吧。本教學將引導您完成設定自訂字體資料夾的過程，確保您的文件看起來像您想要的那樣。無論您是經驗豐富的開發人員還是新手，本指南都將引導您完成每一步。那麼，讓我們讓這些字體看起來棒極了！

## 先決條件

在我們開始之前，讓我們確保您擁有所需的一切：

-  Aspose.Words for .NET：您可以[下載](https://releases.aspose.com/words/net/)如果你還沒有的話。
- Visual Studio：任何版本都可以，但最新的總是最好的。
- 文件：本教學將使用 Word 文件。您可以創建自己的或使用現有的。
- 自訂字體：準備一些自訂字體。我們將使用它們來演示如何設定字體資料夾。

## 導入命名空間

首先，讓我們導入必要的名稱空間。這對於從 Aspose.Words 存取我們需要的類別和方法至關重要。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

匯入這些命名空間後，我們就可以開始設定自訂字體資料夾了。

## 第 1 步：定義您的文件目錄

讓我們先定義文檔目錄的路徑。這是您的 Word 文件的儲存位置。我們將使用一個名為的變數`dataDir`來儲存這個路徑。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替`"YOUR DOCUMENT DIRECTORY"`與目錄的實際路徑。這很重要，因為 Aspose.Words 需要知道在哪裡可以找到您的文件。

## 第2步：設定字體來源

接下來，我們需要設定字體來源。這是我們告訴 Aspose.Words 在哪裡可以找到我們的自訂字體的地方。我們將使用`FontSettings.DefaultInstance.SetFontsSources`方法來實現這一點。

```csharp
FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
	new SystemFontSource(), new FolderFontSource("C:\\MyFonts\\", true)
});
```

這就是我們正在做的事情：

- SystemFontSource：這告訴Aspose.Words使用系統的預設字體。
-  FolderFontSource：這是我們指定包含自訂字體的資料夾的位置。代替`"C:\\MyFonts\\"`以及自訂字體目錄的路徑。這`true`參數指示也應包含子目錄。

## 第 3 步：載入您的文檔

現在我們已經設定了字體來源，是時候載入我們想要使用的文件了。我們將使用`Document`Aspose.Words 中的類別用於此目的。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

確保`"Rendering.docx"`是您的 Word 文件的名稱。如果您的文件有不同的名稱，請確保相應更新。

## 步驟 4：將文件另存為 PDF

最後，讓我們將文件儲存為 PDF 以查看自訂字體的實際效果。我們將使用`Save`的方法`Document`班級。

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFolders.pdf");
```

這將使用我們先前設定的自訂字體將您的文件以 PDF 形式保存在指定目錄中。

## 結論

現在你就擁有了！您已成功在 Aspose.Words for .NET 中設定自訂字體資料夾，並將文件儲存為包含這些自訂字體的 PDF。很酷，對吧？自訂字體可以使文件的外觀發生巨大變化，現在您確切地知道如何操作。快樂編碼！

## 常見問題解答

### 如何安裝 Aspose.Words for .NET？

你可以[下載](https://releases.aspose.com/words/net/)來自網站的最新版本的 Aspose.Words for .NET。

### 我可以使用多個自訂字體資料夾嗎？

是的，您可以新增多個`FolderFontSource`實例到`SetFontsSources`使用不同目錄中的字體的方法。

### 是否需要包含系統字體？

包括系統字體是可選的，但建議使用以確保所有標準字體均可用。

### Aspose.Words 支援哪些文件類型？

Aspose.Words 支援多種檔案格式，包括 DOCX、DOC、PDF、TXT、HTML 等。

### 如何取得 Aspose.Words 的臨時授權？

您可以獲得[臨時執照](https://purchase.aspose.com/temporary-license/)從 Aspose 網站嘗試 Aspose.Words 的全部功能。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
