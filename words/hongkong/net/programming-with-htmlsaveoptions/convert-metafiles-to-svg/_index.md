---
title: 將圖元檔轉換為 Svg
linktitle: 將圖元檔轉換為 Svg
second_title: Aspose.Words 文件處理 API
description: 透過這份詳細的逐步指南，使用 Aspose.Words for .NET 將 Word 文件中的圖元檔案轉換為 SVG。非常適合各個層級的開發人員。
weight: 10
url: /zh-hant/net/programming-with-htmlsaveoptions/convert-metafiles-to-svg/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將圖元檔轉換為 Svg

## 介紹

嘿，程式設計愛好者！您是否想知道如何使用 Aspose.Words for .NET 將 Word 文件中的圖元檔案轉換為 SVG？好吧，你可要好好享受一下了！今天，我們將深入了解 Aspose.Words 的世界，這是一個功能強大的程式庫，讓文件操作變得輕而易舉。學完本教學後，您將成為將圖元檔案轉換為 SVG 的專家，從而使您的 Word 文件更加通用且更具視覺吸引力。那麼，讓我們開始吧？

## 先決條件

在我們深入討論具體細節之前，讓我們確保我們擁有開始所需的一切：

1.  Aspose.Words for .NET：您可以從[Aspose 發佈頁面](https://releases.aspose.com/words/net/).
2. .NET Framework：請確定您的電腦上安裝了 .NET Framework。
3. 開發環境：任何像 Visual Studio 這樣的 IDE 都可以做到這一點。
4. C# 基礎知識：稍微熟悉一下 C# 將會有所幫助，但如果您是新手，請不要擔心 — 我們將詳細解釋所有內容。

## 導入命名空間

首先，讓我們導入。在您的 C# 專案中，您需要匯入必要的命名空間。這對於存取 Aspose.Words 功能至關重要。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

現在我們已經對先決條件和命名空間進行了排序，接下來讓我們深入了解將圖元檔案轉換為 SVG 的分步指南。

## 第 1 步：初始化 Document 和 DocumentBuilder

好吧，讓我們開始建立一個新的 Word 文件並初始化`DocumentBuilder`目的。這個建構器將幫助我們為文件添加內容。

```csharp
//文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

在這裡，我們初始化一個新文件和一個文檔產生器。這`dataDir`變數會保存您將在其中儲存文件的文檔目錄的路徑。

## 第 2 步：為文件新增文本

接下來，讓我們為文件添加一些文字。我們將使用`Write`的方法`DocumentBuilder`插入文字。

```csharp
builder.Write("Here is an SVG image: ");
```

此行將文字「Here is an SVG image:」新增至您的文件。為您要插入的 SVG 圖像提供一些上下文或描述總是一個好主意。

## 第 3 步：插入 SVG 影像

現在，有趣的部分！我們將使用以下命令將 SVG 映像插入到我們的文件中`InsertHtml`方法。

```csharp
builder.InsertHtml(
    @"<svg height='210' width='500'>
    <polygon points='100,10 40,198 190,78 10,78 160,198' 
    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />
</svg> ");
```

此程式碼片段將 SVG 圖像插入到文件中。 SVG 程式碼定義了一個具有指定點、顏色和樣式的簡單多邊形。您可以根據您的要求隨意自訂 SVG 程式碼。

## 步驟 4：定義 HtmlSaveOptions

為了確保我們的圖元檔案儲存為 SVG，我們將定義`HtmlSaveOptions`並設定`MetafileFormat`財產給`HtmlMetafileFormat.Svg`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    MetafileFormat = HtmlMetafileFormat.Svg
};
```

這告訴 Aspose.Words 在匯出到 HTML 時將文件中的任何圖元檔案儲存為 SVG。

## 第 5 步：儲存文檔

最後，讓我們保存我們的文件。我們將使用`Save`的方法`Document`class 並傳入目錄路徑並儲存選項。

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html", saveOptions);
```

該行將文件儲存到指定目錄，文件名為`WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html`。這`saveOptions`確保圖元檔案轉換為 SVG。

## 結論

現在你就擁有了！您已使用 Aspose.Words for .NET 成功將 Word 文件中的圖元檔案轉換為 SVG。很酷，對吧？只需幾行程式碼，您就可以透過添加可縮放向量圖形來增強您的 Word 文檔，使它們更具動態性和視覺吸引力。因此，請繼續在您的專案中嘗試。快樂編碼！

## 常見問題解答

### 什麼是 Aspose.Words for .NET？
Aspose.Words for .NET 是一個功能強大的程式庫，可讓您使用 C# 以程式設計方式建立、修改和轉換 Word 文件。

### 我可以將 Aspose.Words for .NET 與 .NET Core 一起使用嗎？
是的，Aspose.Words for .NET 支援 .NET Core，使其適用於不同的 .NET 應用程式。

### 如何獲得 Aspose.Words for .NET 的免費試用版？
您可以從以下位置下載免費試用版：[Aspose 發佈頁面](https://releases.aspose.com/).

### 是否可以使用 Aspose.Words 將其他影像格式轉換為 SVG？
是的，Aspose.Words 支援將各種圖像格式（包括圖元檔案）轉換為 SVG。

### 在哪裡可以找到 Aspose.Words for .NET 的文檔？
您可以在以下位置找到詳細文檔[Aspose 文件頁面](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
