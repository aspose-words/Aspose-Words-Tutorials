---
"description": "透過本逐步教學了解如何在 Aspose.Words for .NET 中為預設實例設定字體資料夾。輕鬆自訂您的 Word 文件。"
"linktitle": "設定字體資料夾預設實例"
"second_title": "Aspose.Words文件處理API"
"title": "設定字體資料夾預設實例"
"url": "/zh-hant/net/working-with-fonts/set-fonts-folders-default-instance/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 設定字體資料夾預設實例

## 介紹

嘿，程式設計師朋友！如果您在 .NET 中使用 Word 文檔，您可能知道正確使用字體的重要性。今天，我們將深入研究如何使用 Aspose.Words for .NET 為預設實例設定字體資料夾。想像一下，您可以輕鬆獲得所有自訂字體，讓您的文件看起來與您設想的完全一樣。聽起來很棒，對吧？讓我們開始吧！

## 先決條件

在深入探討細節之前，讓我們先確保您已準備好所需的一切：
- Aspose.Words for .NET：確保您已安裝程式庫。如果沒有，你可以 [點此下載](https://releases。aspose.com/words/net/).
- 開發環境：Visual Studio 或任何其他 .NET 相容 IDE。
- C# 基礎知識：您應該熟悉 C# 程式設計。
- 字體資料夾：包含自訂字體的目錄。

## 導入命名空間

首先，讓我們導入必要的命名空間。這有助於存取設定字體資料夾所需的類別和方法。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

讓我們將這個過程分解為簡單、易於理解的步驟。

## 步驟 1：定義資料目錄

每一次偉大的旅程都始於一步，而我們的旅程始於定義儲存文件的目錄。 Aspose.Words 將在此找到您的 Word 文件。

```csharp
// 文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

在這裡，替換 `"YOUR DOCUMENT DIRECTORY"` 使用您的文件目錄的實際路徑。這是您的來源文件所在的位置以及輸出的儲存位置。

## 步驟 2：設定字型資料夾

現在，讓我們告訴 Aspose.Words 在哪裡找到您的自訂字體。這是透過使用以下方式設定字體資料夾來完成的 `FontSettings.DefaultInstance.SetFontsFolder` 方法。

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

在這一行中， `"C:\\MyFonts\\"` 是您的自訂字型資料夾的路徑。第二個參數， `true`，表示要遞歸掃描此資料夾中的字型。

## 步驟3：載入文檔

設定字體資料夾後，下一步是將 Word 文件載入到 Aspose.Words 中。這是使用 `Document` 班級。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

這裡， `dataDir + "Rendering.docx"` 指的是您的Word文件的完整路徑。確保您的文件位於指定的目錄中。

## 步驟4：儲存文檔

最後一步是設定字型資料夾後儲存文件。這可確保您的自訂字體在輸出中正確應用。

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

此行將您的文件儲存為套用了自訂字體的 PDF。輸出檔案將位於與來源文件相同的目錄中。

## 結論

就是這樣！當您將其分解為簡單的步驟時，在 Aspose.Words for .NET 中為預設實例設定字體資料夾就變得輕而易舉了。透過遵循本指南，您可以確保您的 Word 文件看起來完全符合您的要求，並且所有自訂字體都已到位。所以，繼續嘗試吧，讓您的文件大放異彩！

## 常見問題解答

### 我可以設定多個字體資料夾嗎？
是的，您可以使用 `SetFontsFolders` 接受資料夾路徑數組的方法。

### Aspose.Words 支援保存哪些文件格式的文件？
Aspose.Words 支援各種格式，包括 DOCX、PDF、HTML、EPUB 等。

### 是否可以在 Aspose.Words 中使用線上字體？
不，Aspose.Words 目前僅支援本地字體檔案。

### 如何確保我的自訂字體嵌入到已儲存的 PDF 中？
透過設定 `FontSettings` 正確並確保字體可用，Aspose.Words 會將它們嵌入 PDF 輸出中。

### 如果在指定資料夾中找不到字體會發生什麼？
如果未找到指定的字體，Aspose.Words 將使用後備字體。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}