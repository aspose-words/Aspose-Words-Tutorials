---
title: 將文字輸入表單欄位匯出為文字
linktitle: 將文字輸入表單欄位匯出為文字
second_title: Aspose.Words 文件處理 API
description: 透過這份全面的逐步指南，了解如何使用 Aspose.Words for .NET 將文字輸入表單欄位匯出為純文字。
weight: 10
url: /zh-hant/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將文字輸入表單欄位匯出為文字

## 介紹

那麼，您正在深入了解 Aspose.Words for .NET 的世界嗎？很棒的選擇！如果您想了解如何將文本輸入表單欄位匯出為文本，那麼您來對地方了。無論您是剛入門還是溫習技能，本指南都將引導您完成您需要了解的所有內容。讓我們開始吧，好嗎？

## 先決條件

在我們深入討論細節之前，讓我們確保您擁有順利進行操作所需的一切：

-  Aspose.Words for .NET：從以下位置下載並安裝最新版本[這裡](https://releases.aspose.com/words/net/).
- IDE：Visual Studio 或任何 C# 開發環境。
- 基本 C# 知識：了解基本 C# 語法和物件導向程式設計概念。
- 文件：Word 文檔範例（`Rendering.docx`）與文字輸入表單欄位。

## 導入命名空間

首先，您需要匯入必要的名稱空間。這些就像是使一切順利運行的構建塊。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

好吧，現在我們已經準備好了命名空間，讓我們開始行動吧！

## 第 1 步：設定項目

在我們進入程式碼之前，讓我們確保我們的專案設定正確。

## 創建專案

1. 開啟 Visual Studio：先開啟 Visual Studio 或您首選的 C# 開發環境。
2. 建立一個新項目：導航至`File > New > Project`。選擇`Console App (.NET Core)`或任何其他相關項目類型。
3. 為您的專案命名：為您的專案指定一個有意義的名稱，例如`AsposeWordsExportExample`.

## 加入 Aspose.Words

1. 管理 NuGet 套件：在解決方案資源管理器中以滑鼠右鍵按一下您的項目，然後選擇`Manage NuGet Packages`.
2. 搜尋 Aspose.Words：在 NuGet 套件管理器中，搜尋`Aspose.Words`.
3. 安裝Aspose.Words：點選`Install`將 Aspose.Words 庫新增到您的專案中。

## 步驟2：載入Word文檔

現在我們的專案已經設定完畢，讓我們載入包含文字輸入表單欄位的 Word 文件。

1. 指定文檔目錄：定義儲存文檔的目錄路徑。
2. 載入文檔：使用`Document`類別來載入 Word 文件。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## 第 3 步：準備匯出目錄

在導出之前，讓我們確保導出目錄已準備就緒。這是我們的 HTML 檔案和圖像的保存位置。

1. 定義匯出目錄：指定匯出檔案的儲存路徑。
2. 檢查並清理目錄：確保目錄存在並且為空。

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## 步驟 4：配置儲存選項

這就是奇蹟發生的地方。我們需要設定保存選項以將文字輸入表單欄位匯出為純文字。

1. 建立保存選項：初始化一個新的`HtmlSaveOptions`目的。
2. 設定匯出文字選項：配置`ExportTextInputFormFieldAsText`財產給`true`.
3. 設定影像資料夾：定義儲存影像的資料夾。

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    ExportTextInputFormFieldAsText = true,
    ImagesFolder = imagesDir
};
```

## 步驟 5：將文件另存為 HTML

最後，讓我們使用配置的儲存選項將 Word 文件儲存為 HTML 文件。

1. 定義輸出路徑：指定儲存 HTML 檔案的路徑。
2. 儲存文件：使用`Save`的方法`Document`類別來導出文檔。

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## 結論

現在你就擁有了！您已使用 Aspose.Words for .NET 成功將文字輸入表單欄位匯出為純文字。本指南應該為您提供了一個清晰、逐步的方法來完成此任務。請記住，熟能生巧，因此請不斷嘗試不同的選項和設置，看看您還可以使用 Aspose.Words 做什麼。

## 常見問題解答

### 我可以使用相同的方法匯出其他類型的表單欄位嗎？

是的，您可以透過配置表單的不同屬性來匯出其他類型的表單欄位`HtmlSaveOptions`班級。

### 如果我的文件有圖像怎麼辦？

圖像將保存在指定的圖像資料夾中。確保設定`ImagesFolder`財產在`HtmlSaveOptions`.

### 我需要 Aspose.Words 授權嗎？

是的，您可以獲得免費試用[這裡](https://releases.aspose.com/)或購買許可證[這裡](https://purchase.aspose.com/buy).

### 我可以自訂匯出的 HTML 嗎？

絕對地！ Aspose.Words 提供了各種選項來自訂 HTML 輸出。請參閱[文件](https://reference.aspose.com/words/net/)了解更多詳情。

### Aspose.Words 與 .NET Core 相容嗎？

是的，Aspose.Words 與 .NET Core、.NET Framework 和其他 .NET 平台相容。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
