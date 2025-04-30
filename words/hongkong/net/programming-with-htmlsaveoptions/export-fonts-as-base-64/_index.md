---
"description": "在本詳細教學中了解如何使用 Aspose.Words for .NET 將字體匯出為 Base64。確保字體在 HTML 文件中嵌入並正確顯示。"
"linktitle": "將字體匯出為 Base 64"
"second_title": "Aspose.Words文件處理API"
"title": "將字體匯出為 Base 64"
"url": "/zh-hant/net/programming-with-htmlsaveoptions/export-fonts-as-base-64/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 將字體匯出為 Base 64

## 介紹

當談到以程式方式操作 Word 文件時，Aspose.Words for .NET 是一個強大的工具。它的一個巧妙功能是將字體以 Base64 格式匯出到 HTML 檔案中，確保字體在不同的瀏覽器和系統中正確嵌入和顯示。在本教程中，我們將深入探討如何實現這一點。準備好讓您的 Word 文件字體適合網頁嗎？讓我們開始吧！

## 先決條件

在開始編碼之前，讓我們確保您擁有所需的一切：

- Aspose.Words for .NET Library：您可以從 [Aspose 版本](https://releases.aspose.com/words/net/) 頁。
- .NET 開發環境：任何像 Visual Studio 這樣的 IDE 都可以完美運作。
- C# 基礎知識：您不需要成為專業人士，但基本了解會有所幫助。

## 導入命名空間

若要使用 Aspose.Words for .NET，您需要在 C# 程式碼中匯入必要的命名空間。這使得所有類別和方法都可供使用。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 步驟 1：設定您的項目

首先，讓我們設定您的專案並安裝 Aspose.Words 庫。

### 1.1 建立新項目

開啟 Visual Studio 並建立一個新的控制台應用程式專案。將其命名為有意義的名稱，例如“ExportFontsBase64”。

### 1.2 安裝 Aspose.Words

您可以透過 NuGet 套件管理器安裝 Aspose.Words for .NET：

1. 在解決方案資源管理器中以滑鼠右鍵按一下您的專案。
2. 選擇“管理 NuGet 套件”。
3. 搜尋“Aspose.Words”並安裝它。

或者，您可以在程式包管理器控制台中執行以下命令：

```sh
Install-Package Aspose.Words
```

## 第 2 步：載入 Word 文檔

現在您的專案已經設定好了，讓我們載入您想要從中匯出字體的 Word 文件。

### 2.1 定義文檔目錄

首先，定義您的Word文件所在的目錄：

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替 `"YOUR DOCUMENT DIRECTORY"` 使用您的文件目錄的實際路徑。

### 2.2 載入文檔

接下來，使用 `Document` 班級：

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

確保“Rendering.docx”位於您指定的目錄中。

## 步驟 3：設定 HTML 儲存選項

要將字體匯出為 Base64，我們需要配置 `HtmlSaveOptions`。


建立一個實例 `HtmlSaveOptions` 並設定 `ExportFontsAsBase64` 財產 `true`：

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { ExportFontsAsBase64 = true };
```

## 步驟 4：將文件儲存為 HTML

最後，讓我們儲存已配置選項的文件。


使用 `Save` 方法 `Document` 儲存文件的類別：

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
```

此行將儲存您的文件為 HTML 文件，並將字體匯出為 Base64，確保它們嵌入在 HTML 中。

## 結論

恭喜！您已成功使用 Aspose.Words for .NET 從 Word 文件將字體匯出為 Base64。這可確保您的字體在不同平台上已儲存並正確顯示。無論您準備在網路上顯示的文件還是僅確保相容性，此功能都非常有用。

## 常見問題解答

### 什麼是Base64編碼？
Base64 是一種將二進位資料（如字體）編碼為文字格式的方法。這確保了與 HTML 等基於文字的格式的兼容性。

### 為什麼 HTML 中的字型應該使用 Base64？
使用 Base64 可確保字體直接嵌入 HTML 中，避免字體檔案遺失的問題並確保顯示的一致性。

### 我可以將此方法用於圖像等其他資源嗎？
絕對地！ Aspose.Words for .NET 可讓您將各種資源（包括圖片）以 Base64 格式嵌入到 HTML 檔案中。

### 如果我的文件有多種字體怎麼辦？
沒問題！ Aspose.Words for .NET 會將文件中使用的所有字體以 Base64 格式嵌入到產生的 HTML 檔案中。

### Aspose.Words for .NET 可以免費使用嗎？
Aspose.Words for .NET 是一個商業函式庫。不過，您可以從 [Aspose 版本](https://releases.aspose.com/) 頁。



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}