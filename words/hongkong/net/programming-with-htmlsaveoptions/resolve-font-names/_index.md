---
title: 解析字體名稱
linktitle: 解析字體名稱
second_title: Aspose.Words 文件處理 API
description: 了解使用 Aspose.Words for .NET 轉換為 HTML 時如何解析 Word 文件中的字體名稱。附有詳細說明的分步指南。
weight: 10
url: /zh-hant/net/programming-with-htmlsaveoptions/resolve-font-names/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 解析字體名稱

## 介紹

嘿，編碼員朋友！如果您在將 Word 文件另存為 HTML 時遇到過字體問題，那麼您並不孤單。字體可能很棘手，但不用擔心；我支持你。今天，我們將深入探討如何使用 Aspose.Words for .NET 解析 Word 文件中的字型名稱。本指南將逐步引導您完成整個過程，確保您的字體在 HTML 格式中看起來恰到好處。

## 先決條件

在開始之前，讓我們確保您擁有所需的一切：

1.  Aspose.Words for .NET：如果還沒有，您可以下載它[這裡](https://releases.aspose.com/words/net/).
2. 有效許可證：您可以購買許可證[這裡](https://purchase.aspose.com/buy)或獲得臨時許可證[這裡](https://purchase.aspose.com/temporary-license/).
3. C# 和 .NET 的基本知識：本教學假設您熟悉 C# 中的基本程式設計概念。
4. Visual Studio：任何支援.NET框架的版本。

現在我們已經解決了先決條件，讓我們開始行動吧！

## 導入命名空間

在我們開始編碼之前，請確保您已將必要的命名空間匯入到您的專案中。這對於存取 Aspose.Words 功能至關重要。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 第 1 步：設定文檔目錄

首先，讓我們設定文檔目錄的路徑。這是您的 Word 文件所在的位置以及您將儲存輸出的位置。

```csharp
//文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

解釋：
這裡，`dataDir`儲存文檔目錄的路徑。代替`"YOUR DOCUMENT DIRECTORY"`與系統上的實際路徑。

## 步驟2：載入Word文檔

接下來，我們需要載入我們想要處理的Word文件。該文件應該包含您要解析的字體。

```csharp
Document doc = new Document(dataDir + "Missing font.docx");
```

解釋：
我們創建一個`Document`物件並載入名為“Missing font.docx”的 Word 文件`dataDir`.

## 步驟 3：設定 HTML 儲存選項

現在，讓我們設定將文件另存為 HTML 的選項。在這裡，我們將確保正確解析字體名稱。

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    PrettyFormat = true,
    ResolveFontNames = true
};
```

解釋：
我們建立一個實例`HtmlSaveOptions`和`SaveFormat.Html`。這`PrettyFormat`選項使 HTML 輸出更具可讀性，並且`ResolveFontNames`確保字體名稱得到解析。

## 步驟 4：將文件另存為 HTML

最後，我們使用配置的儲存選項將文件儲存為 HTML 文件。

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ResolveFontNames.html", saveOptions);
```

解釋：
我們稱之為`Save`方法上的`Document`對象，指定我們配置的輸出路徑和儲存選項。這將產生一個 HTML 文件，其中包含已解析的字體名稱。

## 結論

現在你就擁有了！透過執行這些步驟，您在使用 Aspose.Words for .NET 將 Word 文件轉換為 HTML 時成功解析了字體名稱。這不僅可以確保您的字體正確顯示，還可以使您的 HTML 輸出看起來美觀且專業。快樂編碼！

## 常見問題解答

### 什麼是 Aspose.Words for .NET？
Aspose.Words for .NET 是一個功能強大的程式庫，可讓開發人員以程式設計方式建立、修改和轉換 Word 文件。

### 如何安裝 Aspose.Words for .NET？
您可以從以下位置下載 Aspose.Words for .NET[這裡](https://releases.aspose.com/words/net/)。請按照文件中提供的安裝說明進行操作。

### 我可以在沒有授權的情況下使用 Aspose.Words for .NET 嗎？
是的，但它會有一些限制。如需完整功能，您可以購買許可證[這裡](https://purchase.aspose.com/buy)或獲得臨時許可證[這裡](https://purchase.aspose.com/temporary-license/).

### 為什麼我的字體在 HTML 中無法正確顯示？
如果在轉換過程中未正確解析字體，則可能會發生這種情況。使用`ResolveFontNames = true`在`HtmlSaveOptions`可以幫助解決這個問題。

### 在哪裡可以獲得 Aspose.Words for .NET 支援？
您可以從以下方面獲得支持[Aspose.Words 支援論壇](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
