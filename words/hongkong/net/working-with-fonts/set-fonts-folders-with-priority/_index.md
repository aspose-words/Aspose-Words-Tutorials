---
title: 設定優先權字體資料夾
linktitle: 設定優先權字體資料夾
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 在 Word 文件中設定優先字體資料夾。我們的指南可確保您的文件每次都能完美呈現。
weight: 10
url: /zh-hant/net/working-with-fonts/set-fonts-folders-with-priority/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 設定優先權字體資料夾

## 介紹

在文件操作領域，設定自訂字型資料夾可以在確保文件完美呈現方面發揮巨大作用，無論在何處查看。今天，我們將深入探討如何使用 Aspose.Words for .NET 在 Word 文件中設定優先字體資料夾。這份綜合指南將引導您完成每個步驟，使整個過程盡可能順利。

## 先決條件

在開始之前，讓我們確保我們擁有所需的一切。這是一個快速清單：

-  Aspose.Words for .NET：您需要安裝此程式庫。如果您還沒有，您可以[在這裡下載](https://releases.aspose.com/words/net/).
- 開發環境：確保您有一個有效的 .NET 開發環境，例如 Visual Studio。
- 文件目錄：確保您有一個文件目錄。對於我們的範例，我們將使用`"YOUR DOCUMENT DIRECTORY"`作為此路徑的佔位符。

## 導入命名空間

首先，我們需要導入必要的名稱空間。這些命名空間對於存取 Aspose.Words 提供的類別和方法至關重要。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

現在，讓我們分解每個步驟來設定優先字體資料夾。

## 第 1 步：設定字體來源

首先，您需要定義字體來源。您可以在此處告訴 Aspose.Words 在哪裡找到字體。您可以指定多個字型資料夾，甚至可以設定它們的優先權。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";

FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
    new SystemFontSource(), 
    new FolderFontSource("C:\\MyFonts\\", true, 1)
});
```

在此範例中，我們設定兩個字體來源：
- SystemFontSource：這是預設字型來源，包括系統上安裝的所有字型。
-  FolderFontSource：這是一個自訂字體資料夾，位於`C:\\MyFonts\\`。這`true`參數指定應遞歸掃描該資料夾，並且`1`設定其優先權。

## 第 2 步：載入您的文檔

接下來，載入您要使用的文檔。確保該文件位於您指定的目錄中。

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

這行程式碼載入一個名為的文檔`Rendering.docx`從您的文件目錄。

## 步驟 3：使用新字體設定儲存文檔

最後，儲存您的文件。當您儲存文件時，Aspose.Words 將使用您指定的字體設定。

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersWithPriority.pdf");
```

這會將文件作為 PDF 保存在您的文件目錄中，名稱為`WorkingWithFonts.SetFontsFoldersWithPriority.pdf`.

## 結論

現在你就擁有了！您已使用 Aspose.Words for .NET 成功設定了優先字體資料夾。透過指定自訂字型資料夾和優先級，您可以確保文件呈現一致，無論在何處查看。這在預設情況下未安裝特定字體的環境中特別有用。

## 常見問題解答

### 為什麼需要設定自訂字體資料夾？
設定自訂字型資料夾可確保您的文件正確呈現，即使它們使用的字型未安裝在正在檢視的系統上。

### 我可以設定多個自訂字體資料夾嗎？
是的，您可以指定多個字型資料夾。 Aspose.Words 允許您設定每個資料夾的優先級，確保首先找到最重要的字體。

### 如果所有指定來源中缺少某種字體，會發生什麼情況？
如果所有指定來源中缺少某種字體，Aspose.Words 將使用後備字體來確保文件仍然可讀。

### 我可以更改系統字體的優先順序嗎？
預設始終包含系統字體，但您可以設定它們相對於自訂字體資料夾的優先順序。

### 是否可以使用自訂字型資料夾的網路路徑？
是的，您可以將網頁路徑指定為自訂字型資料夾，從而使您可以將字型資源集中在網頁位置上。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
