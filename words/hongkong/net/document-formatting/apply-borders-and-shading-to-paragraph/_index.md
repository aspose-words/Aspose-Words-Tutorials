---
title: 將邊框和底紋套用到 Word 文件中的段落
linktitle: 將邊框和底紋套用到 Word 文件中的段落
second_title: Aspose.Words 文件處理 API
description: 使用 Aspose.Words for .NET 將邊框和底紋套用到 Word 文件中的段落。請按照我們的逐步指南來增強您的文件格式。
weight: 10
url: /zh-hant/net/document-formatting/apply-borders-and-shading-to-paragraph/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將邊框和底紋套用到 Word 文件中的段落

## 介紹

嘿，有沒有想過如何讓您的 Word 文件帶有一些精美的邊框和底紋？嗯，您來對地方了！今天，我們將深入了解 Aspose.Words for .NET 的世界，讓我們的段落變得生動有趣。想像一下，您的文件看起來就像專業設計師的作品一樣時尚，只需幾行程式碼。準備好開始了嗎？我們走吧！

## 先決條件

在我們捲起袖子開始編碼之前，讓我們確保我們擁有所需的一切。這是您的快速清單：

-  Aspose.Words for .NET：您需要安裝此程式庫。您可以從[阿斯普斯網站](https://releases.aspose.com/words/net/).
- 開發環境：Visual Studio 或任何其他支援.NET 的IDE。
- C# 基礎知識：足以理解和調整程式碼片段。
- 有效許可證：[臨時執照](https://purchase.aspose.com/temporary-license/)或從以下網站購買的[阿斯普斯](https://purchase.aspose.com/buy).

## 導入命名空間

在進入程式碼之前，我們需要確保將必要的命名空間匯入到我們的專案中。這使得我們可以使用 Aspose.Words 的所有酷炫功能。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System.Drawing;
```

現在，讓我們將這個過程分解為幾個小步驟。每個步驟都有一個標題和詳細說明。準備好？我們走吧！

## 第 1 步：設定您的文件目錄

首先，我們需要一個地方來保存格式精美的文件。讓我們設定文檔目錄的路徑。

```csharp
//文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

該目錄是儲存最終文件的位置。代替`"YOUR DOCUMENT DIRECTORY"`與您機器上的實際路徑。

## 第 2 步：建立新文件和 DocumentBuilder

接下來，我們需要建立一個新文件和一個`DocumentBuilder`目的。這`DocumentBuilder`是我們操縱文檔的魔杖。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

這`Document`物件代表我們的整個Word文檔，並且`DocumentBuilder`幫助我們新增和格式化內容。

## 第 3 步：定義段落邊框

現在，讓我們為我們的段落添加一些時尚的邊框。我們將定義與文字的距離並設定不同的邊框樣式。

```csharp
BorderCollection borders = builder.ParagraphFormat.Borders;
borders.DistanceFromText = 20;
borders[BorderType.Left].LineStyle = LineStyle.Double;
borders[BorderType.Right].LineStyle = LineStyle.Double;
borders[BorderType.Top].LineStyle = LineStyle.Double;
borders[BorderType.Bottom].LineStyle = LineStyle.Double;
```

在這裡，我們設定文字和邊框之間的距離為 20 點。所有邊（左、右、上、下）的邊框均設定為雙線。很喜歡，對吧？

## 第 4 步：為段落加上底紋

邊框很棒，但讓我們通過一些陰影來提高它的水平。我們將使用混合顏色的對角線交叉圖案來使我們的段落脫穎而出。

```csharp
Shading shading = builder.ParagraphFormat.Shading;
shading.Texture = TextureIndex.TextureDiagonalCross;
shading.BackgroundPatternColor = System.Drawing.Color.LightCoral;
shading.ForegroundPatternColor = System.Drawing.Color.LightSalmon;
```

在這一步驟中，我們應用了對角交叉紋理，淺珊瑚色作為背景色，淺鮭魚色作為前景色。這就像給你的段落穿上名牌服裝一樣！

## 第 5 步：為段落新增文本

什麼是沒有文字的段落？讓我們加入一個例句來查看我們的格式設定的實際效果。

```csharp
builder.Write("I'm a formatted paragraph with double border and nice shading.");
```

該行將我們的文字插入文件中。很簡單，但現在它被包裹在時尚的框架和陰影背景中。

## 第 6 步：儲存文檔

最後，是時候保存我們的工作了。讓我們使用描述性名稱將文件儲存到指定目錄。

```csharp
doc.Save(dataDir + "DocumentFormatting.ApplyBordersAndShadingToParagraph.doc");
```

這將使用名稱來保存我們的文檔`DocumentFormatting.ApplyBordersAndShadingToParagraph.doc`在我們之前指定的目錄中。

## 結論

現在你就擁有了！只需幾行程式碼，我們就將一個簡單的段落轉換為視覺吸引力的內容。 Aspose.Words for .NET 讓您可以非常輕鬆地在文件中新增具有專業外觀的格式。無論您是在準備報告、信件或任何文件，這些技巧都將幫助您給人留下深刻的印象。所以，繼續嘗試吧，看看您的文件變得栩栩如生！

## 常見問題解答

### 我可以為每個邊框使用不同的線條樣式嗎？  
絕對地！ Aspose.Words for .NET 可讓您單獨自訂每個邊框。只需設定`LineStyle`對於指南中所示的每種邊框類型。

### 還有哪些其他可用的著色紋理？  
您可以使用多種紋理，例如純色、水平條紋、垂直條紋等。檢查[Aspose 文檔](https://reference.aspose.com/words/net/)以獲得完整清單。

### 如何更改邊框顏色？  
您可以使用以下命令設定邊框顏色`Color`每個邊界的屬性。例如，`borders[BorderType.Left].Color = Color.Red;`.

### 是否可以對文字的特定部分應用邊框和底紋？  
是的，您可以使用以下命令將邊框和底紋應用於特定的文字運行`Run`內的對象`DocumentBuilder`.

### 我可以為多個段落自動執行此程序嗎？  
確實！您可以循環瀏覽段落並以程式設計方式套用相同的邊框和底紋設定。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
