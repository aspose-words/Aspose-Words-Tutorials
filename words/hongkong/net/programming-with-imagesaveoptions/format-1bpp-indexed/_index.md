---
title: 格式 1Bpp 索引
linktitle: 格式 1Bpp 索引
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 將 Word 文件轉換為 1Bpp 索引圖片。請按照我們的逐步指南輕鬆轉換。
weight: 10
url: /zh-hant/net/programming-with-imagesaveoptions/format-1bpp-indexed/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 格式 1Bpp 索引

## 介紹

有沒有想過如何只用幾行程式碼將Word文件另存為黑白影像？嗯，你很幸運！今天，我們將深入研究一個使用 Aspose.Words for .NET 的巧妙小技巧，它可以讓您將文件轉換為 1Bpp 索引圖像。此格式非常適合某些類型的數位存檔、列印或需要節省空間的情況。我們將分解每個步驟，使其變得簡單。準備好開始了嗎？讓我們深入了解吧！

## 先決條件

在我們動手之前，您需要準備好一些東西：

-  Aspose.Words for .NET：確保您已安裝程式庫。你可以[在這裡下載](https://releases.aspose.com/words/net/).
- .NET 開發環境：Visual Studio 是不錯的選擇，但您可以使用任何您喜歡的環境。
- C# 基礎：別擔心，我們會保持簡單，但稍微熟悉一下 C# 會有幫助。
- Word 文件：準備好要轉換的範例 Word 文件。

## 導入命名空間

首先，我們需要導入必要的名稱空間。這很重要，因為它允許我們從 Aspose.Words 存取我們需要的類別和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 第 1 步：設定您的文件目錄

您需要指定文檔目錄的路徑。這是您的 Word 文件的儲存位置以及轉換後的影像的儲存位置。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 步驟2：載入Word文檔

現在，讓我們將 Word 文件載入到 Aspose.Words 中`Document`目的。該物件代表您的 Word 文件並允許您對其進行操作。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 步驟 3：設定影像儲存選項

接下來，我們需要設定`ImageSaveOptions`。這就是奇蹟發生的地方。我們將其配置為使用 1Bpp 索引色彩模式以 PNG 格式儲存圖片。

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1),
    ImageColorMode = ImageColorMode.BlackAndWhite,
    PixelFormat = ImagePixelFormat.Format1bppIndexed
};
```

- SaveFormat.Png：這指定我們要將文件儲存為 PNG 映像。
- PageSet(1)：這表示我們只轉換第一頁。
- ImageColorMode.BlackAndWhite：這會將影像設為黑白。
- ImagePixelFormat.Format1bppIndexed：這會將影像格式設定為 1Bpp 索引。

## 步驟 4：將文件另存為影像

最後，我們使用以下命令將文件儲存為圖像：`Save`的方法`Document`目的。

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## 結論

現在你就擁有了！只需幾行程式碼，您就可以使用 Aspose.Words for .NET 將 Word 文件轉換為 1Bpp 索引圖片。此方法對於從文件創建高對比度、節省空間的圖像非常有用。現在，您可以輕鬆地將其整合到您的專案和工作流程中。快樂編碼！

## 常見問題解答

### 什麼是 1Bpp 索引圖像？
1Bpp（每像素 1 位元）索引影像是一種黑白影像格式，其中每個像素由一位（0 或 1）表示。

### 我可以一次轉換 Word 文件的多個頁面嗎？
是的，你可以。修改`PageSet`財產在`ImageSaveOptions`包括多個頁面或整個文件。

### 我需要許可證才能使用 Aspose.Words for .NET 嗎？
是的，Aspose.Words for .NET 需要完整功能的授權。你可以獲得一個[臨時許可證在這裡](https://purchase.aspose.com/temporary-license/).

### 我可以將 Word 文件轉換為哪些其他圖像格式？
 Aspose.Words 支援各種影像格式，包括 JPEG、BMP 和 TIFF。只需更改`SaveFormat`在`ImageSaveOptions`.

### 在哪裡可以找到有關 Aspose.Words for .NET 的更多文件？
您可以在以下位置找到詳細文檔[Aspose.Words for .NET 文件頁面](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
