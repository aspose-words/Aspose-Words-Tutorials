---
title: 設定字體資料夾系統和自訂資料夾
linktitle: 設定字體資料夾系統和自訂資料夾
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 在 Word 文件中設定係統和自訂字體資料夾，確保您的文件在不同環境中正確顯示。
weight: 10
url: /zh-hant/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 設定字體資料夾系統和自訂資料夾

## 介紹

想像一下，您正在製作一個具有獨特字體樣式的文檔，卻發現這些字體在另一台電腦上無法正確顯示。令人沮喪，對吧？這就是配置字體資料夾發揮作用的地方。使用 Aspose.Words for .NET，您可以定義系統和自訂字體資料夾，以確保您的文件始終如預期顯示。讓我們深入探討如何實現這一目標。

## 先決條件

在我們開始之前，請確保您具備以下條件：

-  Aspose.Words for .NET Library：如果您還沒有，請下載它[這裡](https://releases.aspose.com/words/net/).
- 開發環境：像Visual Studio這樣的IDE。
- C# 基礎知識：熟悉 C# 將幫助您理解程式碼範例。

## 導入命名空間

首先，在專案中導入必要的命名空間：

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

現在，讓我們將該過程分解為簡單的步驟。

## 第 1 步：載入文檔

首先，將 Word 文件載入到 Aspose.Words 中`Document`目的。該文件將是您要設定字體資料夾的位置。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## 第 2 步：初始化字體設置

建立一個新實例`FontSettings`。該物件將允許您管理字體來源。

```csharp
FontSettings fontSettings = new FontSettings();
```

## 步驟 3：檢索系統字型來源

檢索預設系統字體來源。在 Windows 電腦上，這通常包括「Windows\Fonts\”目錄。

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## 第 4 步：新增自訂字體資料夾

新增包含其他字體的自訂資料夾。如果系統字體目錄中未安裝特定字體，這非常有用。

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## 第 5 步：更新字體來源

將字體來源清單轉換回數組並將其設為`FontSettings`目的。

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## 步驟 6：將字型設定套用到文檔

最後應用配置的`FontSettings`到您的文件並將其儲存為您所需的格式，例如 PDF。

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## 結論

現在你就擁有了！透過執行以下步驟，您可以確保您的 Word 文件使用正確的字體，無論它們是系統字體還是儲存在特定目錄中的自訂字體。此設定有助於在不同環境中保持文件外觀的完整性。

## 常見問題解答

### 如果系統資料夾和自訂資料夾中都缺少字體，會發生什麼情況？

Aspose.Words 將使用預設字體來替換遺失的字體，確保文件仍然可讀。

### 我可以添加多個自訂字體資料夾嗎？

是的，您可以透過重複建立過程來新增多個自訂字體資料夾`FolderFontSource`物件並將它們添加到字體來源列表中。

### 是否可以使用自訂字型資料夾的網路路徑？

是的，您可以在`FolderFontSource`構造函數。

### Aspose.Words 支援哪些文件格式來儲存文件？

Aspose.Words 支援多種格式，包括 DOCX、PDF、HTML 等。

### 如何處理字型替換通知？

您可以使用以下方法處理字型替換通知`FontSettings`班級的`FontSubstitutionWarning`事件。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
