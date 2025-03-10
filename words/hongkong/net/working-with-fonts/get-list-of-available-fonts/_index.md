---
title: 取得可用字體列表
linktitle: 取得可用字體列表
second_title: Aspose.Words 文件處理 API
description: 在此詳細的逐步教學中了解如何使用 Aspose.Words for .NET 取得可用字體清單。提升您的字體管理技能。
weight: 10
url: /zh-hant/net/working-with-fonts/get-list-of-available-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 取得可用字體列表

## 介紹

您是否曾經發現自己在管理 Word 文件中的字體時遇到困難？如果您是 .NET 開發人員，Aspose.Words for .NET 可以拯救您！這個強大的程式庫不僅可以幫助您以程式設計方式建立和操作 Word 文檔，還提供廣泛的字體管理功能。在本指南中，我們將引導您逐步了解如何使用 Aspose.Words for .NET 取得可用字體清單。我們會將其分解為易於理解的步驟，以確保您可以輕鬆遵循。那麼，讓我們深入研究，讓字體管理變得輕而易舉！

## 先決條件

在我們開始之前，您需要準備一些東西：

-  Aspose.Words for .NET：請確定您已安裝 Aspose.Words for .NET 程式庫。您可以從以下位置下載：[這裡](https://releases.aspose.com/words/net/).
- Visual Studio：本範例使用Visual Studio作為開發環境。
- .NET Framework：請確定您的電腦上安裝了 .NET Framework。
- 文檔目錄：儲存文檔的目錄路徑。

## 導入命名空間

首先，將必要的命名空間匯入到您的專案中：

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

## 第 1 步：初始化字體設置

第一步是初始化字體設定。這將允許您管理文件的字體來源。

```csharp
FontSettings fontSettings = new FontSettings();
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

- FontSettings：此類用於指定字型替換和字型來源的設定。
- fontSources：我們根據目前字體設定建立現有字體來源的清單。

## 步驟2：定義文檔目錄

接下來，指定文檔目錄的路徑。這是 Aspose.Words 搜尋字體的地方。

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

-  dataDir：此字串變數儲存字體所在目錄的路徑。代替`"YOUR DOCUMENT DIRECTORY"`與實際路徑。

## 第 3 步：新增自訂字體資料夾

現在，新增一個新的資料夾來源以指示 Aspose.Words 在此資料夾中搜尋字體。

```csharp
FolderFontSource folderFontSource = new FolderFontSource(dataDir, true);
```

- FolderFontSource：此類表示資料夾字體來源。第二個參數（`true`) 指示是否在子資料夾中遞歸搜尋字體。

## 第 4 步：更新字型來源

將自訂字體資料夾新增至現有字體來源清單並更新字體設定。

```csharp
fontSources.Add(folderFontSource);
FontSourceBase[] updatedFontSources = fontSources.ToArray();
```

- fontSources.Add(folderFontSource)：將自訂字體資料夾新增至現有字體來源。
- UpdatedFontSources：將字體來源清單轉換為陣列。

## 第 5 步：檢索並顯示字體

最後，檢索可用字體並顯示其詳細資訊。

```csharp
foreach (PhysicalFontInfo fontInfo in updatedFontSources[0].GetAvailableFonts())
{
    Console.WriteLine("FontFamilyName : " + fontInfo.FontFamilyName);
    Console.WriteLine("FullFontName  : " + fontInfo.FullFontName);
    Console.WriteLine("Version  : " + fontInfo.Version);
    Console.WriteLine("FilePath : " + fontInfo.FilePath);
}
```

- GetAvailableFonts()：從更新清單中的第一個字體來源檢索可用字體清單。
- 字體資訊：一個實例`PhysicalFontInfo`包含有關每種字體的詳細資訊。

## 結論

恭喜！您已使用 Aspose.Words for .NET 成功檢索了可用字體清單。本教學引導您完成從初始化字體設定到顯示字體詳細資訊的每個步驟。有了這些知識，您現在可以輕鬆管理 Word 文件中的字體。請記住，Aspose.Words for .NET 是一個功能強大的工具，可以顯著增強您的文件處理能力。因此，繼續探索更多功能，使您的開發流程更有效率。

## 常見問題解答

### 我可以將 Aspose.Words for .NET 與其他 .NET 框架一起使用嗎？
是的，Aspose.Words for .NET 與各種 .NET 框架相容，包括 .NET Core 和 .NET 5+。

### 如何安裝 Aspose.Words for .NET？
您可以透過 Visual Studio 中的 NuGet 套件管理器搜尋「Aspose.Words」來安裝它。

### 是否可以新增多個自訂字體資料夾？
是的，您可以透過建立多個來新增多個自訂字型資料夾`FolderFontSource`實例並將它們新增至字體來源清單。

### 我可以從特定字體來源檢索字體詳細資訊嗎？
是的，您可以透過在中指定字體來源的索引來從任何字體來源檢索字體詳細信息`updatedFontSources`大批。

### Aspose.Words for .NET 支援字體替換嗎？
是的，它支援字體替換，以確保即使原始字體不可用也能正確呈現文字。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
