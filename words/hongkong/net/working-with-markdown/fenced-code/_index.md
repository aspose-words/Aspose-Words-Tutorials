---
"description": "了解如何使用 Aspose.Words for .NET 為 Word 文件新增隔離程式碼和資訊字串。包含逐步指南。提升您的文件格式化技能。"
"linktitle": "圍欄代碼"
"second_title": "Aspose.Words文件處理API"
"title": "圍欄代碼"
"url": "/zh-hant/net/working-with-markdown/fenced-code/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 圍欄代碼

## 介紹

嘿，程式設計師朋友！今天，我們將深入研究 Aspose.Words for .NET 的世界，掌握在 Word 文件中新增隔離程式碼和帶有資訊字串的隔離程式碼的技巧。想像一下您的 Word 文件是一塊畫布，而您，這位藝術家，將以經驗豐富的開發人員的精確度進行繪畫。使用 Aspose.Words，您可以使用結構化、格式化的程式碼區塊以程式設計方式增強您的文檔，使您的技術文檔更加專業、清晰。

## 先決條件

在開始本教學之前，請確保您已準備好所需的一切：

- C# 基礎知識：對 C# 的一般了解將幫助您快速掌握概念。
- Aspose.Words for .NET：您需要安裝 Aspose.Words for .NET。如果你還沒有，那就抓住它 [這裡](https://releases。aspose.com/words/net/).
- 開發環境：Visual Studio 或任何您熟悉的其他 C# IDE。

## 導入命名空間

首先，您需要匯入必要的命名空間。這就像在開始一個專案之前收集所有的工具。

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

現在，讓我們逐步分解這個過程。

## 步驟 1：設定項目

在我們可以在 Word 文件中建立漂亮的格式化程式碼區塊之前，我們需要在 Visual Studio 中建立一個新專案。

1. 建立新專案：開啟 Visual Studio 並建立一個新的 C# 控制台應用程式。
2. 新增 Aspose.Words 參考：透過 NuGet 套件管理器安裝 Aspose.Words。您可以透過在解決方案資源管理器中右鍵單擊您的項目，選擇“管理 NuGet 套件”，然後搜尋 Aspose.Words 來執行此操作。

## 步驟2：初始化DocumentBuilder

現在您的專案已經設定好了，讓我們初始化 DocumentBuilder，它將是我們在 Word 文件中新增內容的主要工具。

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## 步驟 3：建立圍欄程式碼樣式

要新增圍欄程式碼，我們首先需要建立一種樣式。將其視為為我們的程式碼區塊設定主題。

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## 步驟 4：向文件新增隔離程式碼

樣式準備好後，我們現在可以為文件添加一個圍欄的程式碼區塊。

```csharp
builder.ParagraphFormat.Style = fencedCode;
builder.Writeln("This is a fenced code block");
```

## 步驟 5：使用資訊字串建立圍欄程式碼樣式

有時，您可能想要指定程式語言或為程式碼區塊添加額外資訊。讓我們為此創建一種風格。

```csharp
Style fencedCodeWithInfo = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode.C#");
fencedCodeWithInfo.Font.Name = "Courier New";
fencedCodeWithInfo.Font.Size = 10;
fencedCodeWithInfo.ParagraphFormat.LeftIndent = 20;
fencedCodeWithInfo.ParagraphFormat.RightIndent = 20;
fencedCodeWithInfo.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## 步驟 6：將帶有資訊字串的圍欄程式碼新增至文檔

現在，讓我們添加一個帶有資訊字串的圍欄程式碼區塊來表明它是 C# 程式碼。

```csharp
builder.ParagraphFormat.Style = fencedCodeWithInfo;
builder.Writeln("This is a fenced code block with info string - C#");
```

## 結論

恭喜！您剛剛使用 Aspose.Words for .NET 將隔離程式碼區塊和帶有資訊字串的隔離程式碼新增至您的 Word 文件。這只是冰山一角。使用 Aspose.Words，您可以自動化您的文件處理並將其提升到新的高度。繼續探索並快樂編碼！

## 常見問題解答

### 什麼是 Aspose.Words for .NET？
Aspose.Words for .NET 是一個強大的程式庫，可讓開發人員以程式設計方式建立、操作和轉換 Word 文件。

### 我可以將 Aspose.Words 與其他程式語言一起使用嗎？
Aspose.Words 主要支援 .NET 語言，但也有適用於 Java、Python 和其他語言的版本。

### Aspose.Words 可以免費使用嗎？
Aspose.Words 是一款商業產品，但您可以下載免費試用版 [這裡](https://releases.aspose.com/) 探索其特點。

### 如何獲得 Aspose.Words 的支援？
您可以獲得 Aspose 社群和開發人員的支持 [這裡](https://forum。aspose.com/c/words/8).

### Aspose.Words 還提供哪些功能？
Aspose.Words 提供廣泛的功能，包括文件轉換、基於範本的文件產生、報告等。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}