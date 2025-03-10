---
title: 加入 CSS 類別名稱前綴
linktitle: 加入 CSS 類別名稱前綴
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 將 Word 文件儲存為 HTML 時新增 CSS 類別名稱前綴。包括逐步指南、程式碼片段和常見問題。
weight: 10
url: /zh-hant/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 加入 CSS 類別名稱前綴

## 介紹

歡迎！如果您正在深入探索 Aspose.Words for .NET 的世界，那麼您將會大飽口福。今天，我們將探討如何使用 Aspose.Words for .NET 將 Word 文件儲存為 HTML 時新增 CSS 類別名稱前綴。當您想要避免 HTML 文件中的類別名稱衝突時，此功能非常方便。

## 先決條件

在我們開始之前，請確保您具備以下條件：

-  Aspose.Words for .NET：如果您還沒有安裝它，[在這裡下載](https://releases.aspose.com/words/net/).
- 開發環境：Visual Studio 或任何其他 C# IDE。
-  Word 文件：我們將使用名為`Rendering.docx`。將其放在您的專案目錄中。

## 導入命名空間

首先，請確保您已將必要的命名空間匯入到您的 C# 專案中。將這些添加到程式碼檔案的頂部：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

現在，讓我們深入了解逐步指南！

## 第 1 步：設定您的項目

在開始加入 CSS 類別名稱前綴之前，讓我們先設定我們的專案。

### 步驟1.1：建立一個新項目

啟動 Visual Studio 並建立一個新的控制台應用程式專案。給它取個吸引人的名字，例如`AsposeCssPrefixExample`.

### 步驟1.2：新增Aspose.Words for .NET

如果您尚未透過 NuGet 將 Aspose.Words for .NET 新增至您的專案中。只需開啟 NuGet 套件管理器控制台並執行：

```bash
Install-Package Aspose.Words
```

偉大的！現在，我們準備開始編碼。

## 第 2 步：載入您的文檔

我們需要做的第一件事是載入要轉換為 HTML 的 Word 文件。

### 步驟2.1：定義文檔路徑

設定文檔目錄的路徑。為了本教學的目的，我們假設您的文件位於名為`Documents`在您的專案目錄中。

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### 步驟2.2：載入文檔

現在，讓我們使用 Aspose.Words 來載入文件：

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 步驟 3：設定 HTML 儲存選項

接下來，我們需要配置 HTML 儲存選項以包含 CSS 類別名稱前綴。

### 步驟 3.1：建立 HTML 儲存選項

實例化`HtmlSaveOptions`物件並將 CSS 樣式表類型設定為`External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### 步驟3.2：設定CSS類別名稱前綴

現在，讓我們設定`CssClassNamePrefix`屬性到您想要的前綴。對於這個例子，我們將使用`"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## 步驟 4：將文件另存為 HTML

最後，讓我們使用配置的選項將文件儲存為 HTML 文件。


指定輸出 HTML 檔案路徑並儲存文件。

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## 第 5 步：驗證輸出

運行項目後，導航到您的`Documents`資料夾。您應該找到一個名為`WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html`。在文字編輯器或瀏覽器中開啟此文件以驗證 CSS 類別是否具有前綴`pfx_`.

## 結論

現在你就擁有了！透過執行這些步驟，您已成功使用 Aspose.Words for .NET 將 CSS 類別名稱前綴新增至 HTML 輸出。這個簡單而強大的功能可以幫助您在 HTML 文件中保持乾淨且無衝突的樣式。

## 常見問題解答

### 我可以為每個保存操作使用不同的前綴嗎？
是的，您可以在每次儲存文件時透過更改前綴來自訂前綴`CssClassNamePrefix`財產。

### 這個方法支援內聯CSS嗎？
這`CssClassNamePrefix`屬性與外部 CSS 一起使用。對於內聯 CSS，您需要不同的方法。

### 如何包含其他 HTML 保存選項？
您可以配置各種屬性`HtmlSaveOptions`自訂您的 HTML 輸出。檢查[文件](https://reference.aspose.com/words/net/)了解更多詳情。

### 是否可以將 HTML 儲存到流中？
絕對地！您可以透過將流物件傳遞給`Save`方法。

### 如果遇到問題，我該如何獲得支援？
您可以從以下方面獲得支持[Aspose論壇](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
