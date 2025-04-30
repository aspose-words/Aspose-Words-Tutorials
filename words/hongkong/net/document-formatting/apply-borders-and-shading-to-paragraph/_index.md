---
"description": "使用 Aspose.Words for .NET 對 Word 文件中的段落套用邊框和陰影。請按照我們的逐步指南來增強您的文件格式。"
"linktitle": "在 Word 文件中對段落套用邊框和底紋"
"second_title": "Aspose.Words文件處理API"
"title": "在 Word 文件中對段落套用邊框和底紋"
"url": "/zh-hant/net/document-formatting/apply-borders-and-shading-to-paragraph/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 文件中對段落套用邊框和底紋

## 介紹

嘿，有沒有想過如何讓你的 Word 文件帶有一些漂亮的邊框和陰影？嗯，您來對地方了！今天，我們將深入研究 Aspose.Words for .NET 的世界，使我們的段落更加生動。想像一下，只需幾行程式碼，您的文件就會看起來像專業設計師的作品一樣精美。準備好開始了嗎？我們走吧！

## 先決條件

在我們捲起袖子開始編碼之前，讓我們確保我們擁有所需的一切。以下是您的快速檢查清單：

- Aspose.Words for .NET：您需要安裝此程式庫。您可以從 [Aspose 網站](https://releases。aspose.com/words/net/).
- 開發環境：Visual Studio 或任何其他支援 .NET 的 IDE。
- C# 基礎知識：足以理解和調整程式碼片段。
- 有效駕照： [臨時執照](https://purchase.aspose.com/temporary-license/) 或從 [Aspose](https://purchase。aspose.com/buy).

## 導入命名空間

在進入程式碼之前，我們需要確保已將必要的命名空間匯入到我們的專案中。這使得我們可以使用 Aspose.Words 的所有酷炫功能。

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System.Drawing;
```

現在，讓我們將這個過程分解成幾個小步驟。每個步驟都會有一個標題和詳細的解釋。準備好？我們走吧！

## 步驟 1：設定文檔目錄

首先，我們需要一個地方來保存格式精美的文件。讓我們設定您的文檔目錄的路徑。

```csharp
// 文檔目錄的路徑。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

該目錄是保存最終文件的地方。代替 `"YOUR DOCUMENT DIRECTORY"` 使用您機器上的實際路徑。

## 步驟 2：建立新文件和 DocumentBuilder

接下來，我們需要建立一個新文件和一個 `DocumentBuilder` 目的。這 `DocumentBuilder` 是我們的魔杖，可以讓我們操縱文檔。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

這 `Document` 物件代表我們的整個 Word 文檔，並且 `DocumentBuilder` 幫助我們新增和格式化內容。

## 步驟 3：定義段落邊框

現在，讓我們為段落添加一些時尚的邊框。我們將定義與文字的距離並設定不同的邊框樣式。

```csharp
BorderCollection borders = builder.ParagraphFormat.Borders;
borders.DistanceFromText = 20;
borders[BorderType.Left].LineStyle = LineStyle.Double;
borders[BorderType.Right].LineStyle = LineStyle.Double;
borders[BorderType.Top].LineStyle = LineStyle.Double;
borders[BorderType.Bottom].LineStyle = LineStyle.Double;
```

這裡我們設定文字和邊框之間的距離是20點。所有邊（左、右、上、下）的邊框都設定為雙線。很奇特吧？

## 步驟 4：對段落套用陰影

邊框很棒，但是讓我們通過一些陰影使其更上一層樓。我們將使用混合顏色的對角十字圖案來使我們的段落脫穎而出。

```csharp
Shading shading = builder.ParagraphFormat.Shading;
shading.Texture = TextureIndex.TextureDiagonalCross;
shading.BackgroundPatternColor = System.Drawing.Color.LightCoral;
shading.ForegroundPatternColor = System.Drawing.Color.LightSalmon;
```

在這一步驟中，我們應用了對角十字紋理，以淺珊瑚色作為背景色，淺鮭魚色作為前景色。這就像給你的段落穿上名牌服裝一樣！

## 步驟 5：為段落新增文本

沒有文字的段落是什麼？讓我們加入一個範例句子來查看我們的格式。

```csharp
builder.Write("I'm a formatted paragraph with double border and nice shading.");
```

此行將我們的文字插入文件中。簡單，但現在它被包裹在時尚的框架和陰影背景中。

## 步驟6：儲存文檔

最後，是時候保存我們的工作了。讓我們將文件儲存到具有描述性名稱的指定目錄中。

```csharp
doc.Save(dataDir + "DocumentFormatting.ApplyBordersAndShadingToParagraph.doc");
```

這將使用以下名稱儲存我們的文檔 `DocumentFormatting.ApplyBordersAndShadingToParagraph.doc` 在我們之前指定的目錄中。

## 結論

就是這樣！只需幾行程式碼，我們就將一個簡單的段落轉換成視覺上吸引人的內容。 Aspose.Words for .NET 讓您可以非常輕鬆地為您的文件添加專業外觀的格式。無論您準備的是報告、信函還是任何文件，這些技巧都會幫助您留下深刻的印象。所以，繼續嘗試吧，看看你的文件如何變得生動起來！

## 常見問題解答

### 我可以為每個邊框使用不同的線條樣式嗎？  
絕對地！ Aspose.Words for .NET 可讓您單獨自訂每個邊框。只需設定 `LineStyle` 對於指南中所示的每種邊框類型。

### 還有哪些其他陰影紋理可用？  
您可以使用多種紋理，例如實心、水平條紋、垂直條紋等。檢查 [Aspose 文檔](https://reference.aspose.com/words/net/) 以取得完整清單。

### 我怎麼改變邊框顏色？  
您可以使用 `Color` 每個邊界的屬性。例如， `borders[BorderType。Left].Color = Color.Red;`.

### 是否可以對文字的特定部分套用邊框和陰影？  
是的，你可以使用 `Run` 物件內的 `DocumentBuilder`。

### 我可以針對多個段落自動執行此程序嗎？  
確實！您可以循環遍歷段落並以程式設計方式套用相同的邊框和陰影設定。



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}