---
title: 圍欄代碼
linktitle: 圍欄代碼
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 將隔離程式碼和資訊字串新增至 Word 文件。包括逐步指南。提升您的文件格式化技能。
weight: 10
url: /zh-hant/net/working-with-markdown/fenced-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 圍欄代碼

## 介紹

嘿，編碼員朋友！今天，我們將深入了解 Aspose.Words for .NET 的世界，掌握在 Word 文件中添加防護程式碼和帶有資訊字串的防護程式碼的藝術。將您的 Word 文件想像成一塊畫布，而您，這位藝術家，將以經驗豐富的開發人員的精確度進行繪畫。透過 Aspose.Words，您可以透過結構化、格式化的程式碼區塊以程式設計方式增強您的文檔，使您的技術文件煥發專業性和清晰度。

## 先決條件

在我們開始本教程之前，讓我們確保您擁有所需的一切：

- C# 基礎知識：對 C# 的整體了解將幫助您快速掌握概念。
-  Aspose.Words for .NET：您需要安裝 Aspose.Words for .NET。如果你還沒有得到它，抓住它[這裡](https://releases.aspose.com/words/net/).
- 開發環境：Visual Studio 或您熟悉的任何其他 C# IDE。

## 導入命名空間

首先，您需要匯入必要的名稱空間。這就像在開始專案之前收集所有工具一樣。

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

現在，讓我們逐步分解這個過程。

## 第 1 步：設定您的項目

在我們可以在 Word 文件中建立漂亮的格式化程式碼區塊之前，我們需要在 Visual Studio 中設定一個新專案。

1. 建立新專案：開啟 Visual Studio 並建立一個新的 C# 控制台應用程式。
2. 新增 Aspose.Words 參考：透過 NuGet 套件管理器安裝 Aspose.Words。您可以透過在解決方案資源管理器中右鍵單擊您的項目，選擇「管理 NuGet 套件」並蒐索 Aspose.Words 來完成此操作。

## 第 2 步：初始化 DocumentBuilder

現在您的專案已設定完畢，讓我們初始化 DocumentBuilder，它將成為我們在 Word 文件中新增內容的主要工具。

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## 第 3 步：為受保護的程式碼建立樣式

要新增防護程式碼，我們首先需要建立一個樣式。將此視為為我們的程式碼區塊設定主題。

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## 步驟 4：將受防護的程式碼加入文件中

準備好樣式後，我們現在可以為文件添加受隔離的程式碼區塊。

```csharp
builder.ParagraphFormat.Style = fencedCode;
builder.Writeln("This is a fenced code block");
```

## 第 5 步：使用資訊字串為受保護程式碼建立樣式

有時，您可能想要指定程式語言或在程式碼區塊中添加額外的資訊。讓我們為此創建一個樣式。

```csharp
Style fencedCodeWithInfo = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode.C#");
fencedCodeWithInfo.Font.Name = "Courier New";
fencedCodeWithInfo.Font.Size = 10;
fencedCodeWithInfo.ParagraphFormat.LeftIndent = 20;
fencedCodeWithInfo.ParagraphFormat.RightIndent = 20;
fencedCodeWithInfo.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## 第 6 步：將帶有資訊字串的防護代碼新增至文件中

現在，讓我們新增一個帶有資訊字串的隔離程式碼區塊，以指示它是 C# 程式碼。

```csharp
builder.ParagraphFormat.Style = fencedCodeWithInfo;
builder.Writeln("This is a fenced code block with info string - C#");
```

## 結論

恭喜！您剛剛使用 Aspose.Words for .NET 將防護程式碼區塊和帶有資訊字串的防護程式碼新增至您的 Word 文件。這只是冰山一角。使用 Aspose.Words，您可以將文件處理自動化並增強到新的高度。繼續探索並快樂編碼！

## 常見問題解答

### 什麼是 Aspose.Words for .NET？
Aspose.Words for .NET 是一個功能強大的程式庫，可讓開發人員以程式設計方式建立、操作和轉換 Word 文件。

### 我可以將 Aspose.Words 與其他程式語言一起使用嗎？
Aspose.Words 主要支援 .NET 語言，但也有適用於 Java、Python 和其他語言的版本。

### Aspose.Words 可以免費使用嗎？
 Aspose.Words是一個商業產品，但您可以下載免費試用版[這裡](https://releases.aspose.com/)來探索它的特點。

### 我如何獲得 Aspose.Words 支援？
您可以獲得 Aspose 社群和開發人員的支持[這裡](https://forum.aspose.com/c/words/8).

### Aspose.Words 還提供哪些功能？
Aspose.Words 提供了廣泛的功能，包括文件轉換、基於範本的文件產生、報告等等。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
