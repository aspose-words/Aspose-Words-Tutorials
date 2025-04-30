---
"description": "了解如何在使用 Aspose.Words for .NET 將 Word 文件儲存為 HTML 時新增 CSS 類別名稱前綴。包括逐步指南、程式碼片段和常見問題。"
"linktitle": "加入 CSS 類別名稱前綴"
"second_title": "Aspose.Words文件處理API"
"title": "加入 CSS 類別名稱前綴"
"url": "/zh-hant/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 加入 CSS 類別名稱前綴

## 介紹

歡迎！如果您正在深入了解 Aspose.Words for .NET 的世界，那麼您將獲得巨大的收穫。今天，我們將探討如何在使用 Aspose.Words for .NET 將 Word 文件儲存為 HTML 時新增 CSS 類別名稱前綴。當您想要避免 HTML 文件中的類別名稱衝突時，此功能非常方便。

## 先決條件

在開始之前，請確保您具備以下條件：

- Aspose.Words for .NET：如果您尚未安裝， [點此下載](https://releases。aspose.com/words/net/).
- 開發環境：Visual Studio 或任何其他 C# IDE。
- Word 文件：我們將使用名為 `Rendering.docx`。將其放在您的專案目錄中。

## 導入命名空間

首先，請確保已將必要的命名空間匯入到您的 C# 專案中。在程式碼檔案的頂部添加這些：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

現在，讓我們深入了解逐步指南！

## 步驟 1：設定您的項目

在我們開始加入 CSS 類別名稱前綴之前，讓我們先設定我們的專案。

### 步驟 1.1：建立新項目

啟動 Visual Studio 並建立一個新的控制台應用程式專案。給它一個吸引人的名字，例如 `AsposeCssPrefixExample`。

### 步驟1.2：新增Aspose.Words for .NET

如果您還沒有，請透過 NuGet 將 Aspose.Words for .NET 新增至您的專案中。只需開啟 NuGet 套件管理器控制台並執行：

```bash
Install-Package Aspose.Words
```

偉大的！現在，我們準備開始編碼。

## 第 2 步：載入文檔

我們需要做的第一件事是載入要轉換為 HTML 的 Word 文件。

### 步驟 2.1：定義文檔路徑

設定文檔目錄的路徑。為了本教學的目的，我們假設您的文件位於名為 `Documents` 在您的專案目錄中。

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### 步驟 2.2：載入文檔

現在，讓我們使用 Aspose.Words 來載入文件：

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 步驟 3：設定 HTML 儲存選項

接下來，我們需要配置 HTML 儲存選項以包含 CSS 類別名稱前綴。

### 步驟 3.1：建立 HTML 儲存選項

實例化 `HtmlSaveOptions` 物件並將 CSS 樣式表類型設定為 `External`。

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### 步驟 3.2：設定 CSS 類別名稱前綴

現在，讓我們設定 `CssClassNamePrefix` 屬性到您想要的前綴。對於這個例子，我們將使用 `"pfx_"`。

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## 步驟 4：將文件儲存為 HTML

最後，讓我們使用配置的選項將文件儲存為 HTML 文件。


指定輸出 HTML 檔案路徑並儲存文件。

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## 步驟 5：驗證輸出

運行項目後，導航到您的 `Documents` 資料夾。您應該找到一個名為 `WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html`。在文字編輯器或瀏覽器中開啟此文件，以驗證 CSS 類別是否具有前綴 `pfx_`。

## 結論

就是這樣！透過遵循這些步驟，您已成功使用 Aspose.Words for .NET 將 CSS 類別名稱前綴新增至 HTML 輸出。這個簡單但強大的功能可以幫助您在 HTML 文件中保持乾淨且無衝突的樣式。

## 常見問題解答

### 我可以為每個保存操作使用不同的前綴嗎？
是的，您可以在每次儲存文件時透過更改 `CssClassNamePrefix` 財產。

### 此方法是否支援內聯 CSS？
這 `CssClassNamePrefix` 屬性與外部 CSS 一起工作。對於內聯 CSS，您需要採用不同的方法。

### 我如何包含其他 HTML 保存選項？
您可以配置 `HtmlSaveOptions` 自訂您的 HTML 輸出。檢查 [文件](https://reference.aspose.com/words/net/) 了解更多詳情。

### 可以將 HTML 儲存到流中嗎？
絕對地！您可以透過將流物件傳遞給 `Save` 方法。

### 如果我遇到問題，如何獲得支援？
您可以從 [Aspose 論壇](https://forum。aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}