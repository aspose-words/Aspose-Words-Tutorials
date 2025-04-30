---
"description": "透過我們詳細的逐步指南，學習使用 Aspose.Words for .NET 將 Word 文件的每一頁儲存為單獨的 PNG 圖像。"
"linktitle": "頁面儲存回調"
"second_title": "Aspose.Words文件處理API"
"title": "頁面儲存回調"
"url": "/zh-hant/net/programming-with-imagesaveoptions/page-saving-callback/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 頁面儲存回調

## 介紹

嘿！是否曾覺得需要將 Word 文件的每一頁儲存為單獨的圖片？也許您想將大型報告分解為易於理解的視覺效果，或者您可能需要建立縮圖以供預覽。無論出於何種原因，使用 Aspose.Words for .NET 都可以讓這項任務變得輕而易舉。在本指南中，我們將引導您完成設定頁面儲存回調的過程，以將文件的每一頁儲存為單獨的 PNG 映像。讓我們開始吧！

## 先決條件

在開始之前，請確保您具備以下條件：

1. Aspose.Words for .NET：如果您還沒有，請從 [這裡](https://releases。aspose.com/words/net/).
2. Visual Studio：任何版本都可以，但在本指南中我會使用 Visual Studio 2019。
3. C# 基礎知識：您需要對 C# 有基本的了解才能繼續學習。

## 導入命名空間

首先，我們需要導入必要的命名空間。這有助於我們存取所需的類別和方法，而無需每次都輸入完整的命名空間。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## 步驟 1：設定文檔目錄

好的，讓我們先定義文檔目錄的路徑。這是您的輸入 Word 文件所在的位置，也是輸出影像的儲存位置。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 第 2 步：載入文檔

接下來，我們將載入您想要處理的文件。確保您的文件（“Rendering.docx”）位於指定的目錄中。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## 步驟3：設定影像儲存選項

我們需要配置保存影像的選項。在這種情況下，我們將頁面儲存為 PNG 檔案。

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

這裡， `PageSet` 指定要儲存的頁面範圍，以及 `PageSavingCallback` 指向我們的自訂回調類別。

## 步驟4：實作頁面儲存回調

現在，讓我們實作處理如何保存每個頁面的回呼類別。

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

此類實現 `IPageSavingCallback` 介面內 `PageSaving` 方法中，我們為每個已儲存的頁面定義命名模式。

## 步驟5：將文件儲存為影像

最後，我們使用配置的選項來儲存文件。

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## 結論

就是這樣！您已成功設定頁面儲存回調，以使用 Aspose.Words for .NET 將 Word 文件的每一頁儲存為單獨的 PNG 映像。這種技術對於各種應用程式都非常有用，從建立頁面預覽到為報告產生單獨的頁面圖像。 

編碼愉快！

## 常見問題解答

### 我可以將頁面儲存為 PNG 以外的格式嗎？  
是的，您可以透過更改 `SaveFormat` 在 `ImageSaveOptions`。

### 如果我只想保存特定頁面怎麼辦？  
您可以透過調整 `PageSet` 參數輸入 `ImageSaveOptions`。

### 可以自訂影像品質嗎？  
絕對地！您可以設定以下屬性 `ImageSaveOptions.JpegQuality` 控制輸出影像的品質。

### 如何有效率地處理大型文件？  
對於大型文檔，請考慮分批處理頁面以有效管理記憶體使用情況。

### 在哪裡可以找到有關 Aspose.Words for .NET 的更多資訊？  
查看 [文件](https://reference.aspose.com/words/net/) 以獲得全面的指南和範例。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}