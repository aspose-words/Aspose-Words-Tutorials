---
title: 設定字體資料夾預設實例
linktitle: 設定字體資料夾預設實例
second_title: Aspose.Words 文件處理 API
description: 透過此逐步教學，了解如何為 Aspose.Words for .NET 中的預設實例設定字型資料夾。輕鬆自訂您的 Word 文件。
weight: 10
url: /zh-hant/net/working-with-fonts/set-fonts-folders-default-instance/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 設定字體資料夾預設實例

## 介紹

嘿，編碼員朋友！如果您在 .NET 中處理 Word 文檔，您可能知道正確使用字體的重要性。今天，我們將深入研究如何使用 Aspose.Words for .NET 設定預設實例的字體資料夾。想像一下，所有自訂字體都觸手可及，使您的文件看起來完全符合您的設想。聽起來不錯，對吧？讓我們開始吧！

## 先決條件

在我們深入了解具體細節之前，讓我們確保您擁有所需的一切：
-  Aspose.Words for .NET：確保您已安裝程式庫。如果沒有，您可以[在這裡下載](https://releases.aspose.com/words/net/).
- 開發環境：Visual Studio 或任何其他 .NET 相容 IDE。
- C# 基礎知識：您應該熟悉 C# 程式設計。
- 字體資料夾：包含自訂字體的目錄。

## 導入命名空間

首先，讓我們導入必要的名稱空間。這有助於存取設定字體資料夾所需的類別和方法。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

讓我們將這個過程分解為簡單易懂的步驟。

## 第 1 步：定義資料目錄

每一個偉大的旅程都從一個步驟開始，而我們的旅程從定義儲存文件的目錄開始。 Aspose.Words 將在此處找到您的 Word 文件。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

在這裡，替換`"YOUR DOCUMENT DIRECTORY"`與文檔目錄的實際路徑。這是來源文件所在的位置以及輸出的保存位置。

## 第2步：設定字體資料夾

現在，讓我們告訴 Aspose.Words 在哪裡可以找到您的自訂字體。這是透過使用設定字體資料夾來完成的`FontSettings.DefaultInstance.SetFontsFolder`方法。

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

在這一行中，`"C:\\MyFonts\\"`是自訂字型資料夾的路徑。第二個參數，`true`，表示應遞歸掃描該資料夾中的字型。

## 第 3 步：載入您的文檔

設定字體資料夾後，下一步是將 Word 文件載入到 Aspose.Words 中。這是使用以下方法完成的`Document`班級。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

這裡，`dataDir + "Rendering.docx"`指的是Word文檔的完整路徑。確保您的文件位於指定目錄中。

## 步驟 4：儲存文檔

最後一步是設定字型資料夾後儲存文件。這可確保您的自訂字體在輸出中正確應用。

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

此行將您的文件儲存為套用了自訂字體的 PDF。輸出檔案將位於與來源文件相同的目錄中。

## 結論

現在你就擁有了！當您將其分解為簡單的步驟時，為 Aspose.Words for .NET 中的預設實例設定字體資料夾是一件輕而易舉的事。透過遵循本指南，您可以確保您的 Word 文件看起來完全符合您的要求，並且所有自訂字體都已就位。所以，繼續嘗試吧，讓您的文件大放異彩！

## 常見問題解答

### 我可以設定多個字體資料夾嗎？
是的，您可以使用以下命令設定多個字體資料夾`SetFontsFolders`接受資料夾路徑數組的方法。

### Aspose.Words 支援哪些文件格式來儲存文件？
Aspose.Words 支援多種格式，包括 DOCX、PDF、HTML、EPUB 等。

### 是否可以在 Aspose.Words 中使用線上字體？
不，Aspose.Words 目前僅支援本地字體檔案。

### 如何確保我的自訂字體嵌入到已儲存的 PDF 中？
透過設定`FontSettings`正確並確保字體可用，Aspose.Words 會將它們嵌入 PDF 輸出中。

### 如果在指定資料夾中找不到字型會怎樣？
如果找不到指定的字體，Aspose.Words 將使用後備字體。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
