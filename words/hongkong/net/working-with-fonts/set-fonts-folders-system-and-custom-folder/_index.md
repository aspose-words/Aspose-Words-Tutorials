---
"description": "了解如何使用 Aspose.Words for .NET 在 Word 文件中設定係統和自訂字體資料夾，確保您的文件在不同環境中正確顯示。"
"linktitle": "設定字體資料夾系統和自訂資料夾"
"second_title": "Aspose.Words文件處理API"
"title": "設定字體資料夾系統和自訂資料夾"
"url": "/zh-hant/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 設定字體資料夾系統和自訂資料夾

## 介紹

想像一下，您正在製作具有獨特字體樣式的文檔，卻發現該字體在另一台機器上無法正確顯示。令人沮喪，對吧？這就是配置字體資料夾發揮作用的地方。使用 Aspose.Words for .NET，您可以定義系統和自訂字體資料夾，以確保您的文件始終符合預期。讓我們深入探討如何實現這一目標。

## 先決條件

在開始之前，請確保您具備以下條件：

- Aspose.Words for .NET Library：如果您還沒有下載，請下載 [這裡](https://releases。aspose.com/words/net/).
- 開發環境：像 Visual Studio 這樣的 IDE。
- C# 基礎知識：熟悉 C# 將幫助您理解程式碼範例。

## 導入命名空間

首先，在您的專案中匯入必要的命名空間：

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

現在，讓我們將這個過程分解為簡單的步驟。

## 步驟 1：載入文檔

首先，將您的 Word 文件載入到 Aspose.Words `Document` 目的。該文件將是您想要設定字型資料夾的文件。

```csharp
// 文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## 步驟2：初始化字型設定

建立新實例 `FontSettings`。該物件將允許您管理字體來源。

```csharp
FontSettings fontSettings = new FontSettings();
```

## 步驟3：檢索系統字型來源

檢索預設系統字體來源。在 Windows 機器上，這通常包括「Windows\Fonts」目錄。

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## 步驟 4：新增自訂字型資料夾

新增包含其他字體的自訂資料夾。如果您有未安裝在系統字體目錄中的特定字體，這將很有用。

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## 步驟 5：更新字型來源

將字體來源清單轉換回數組並將其設為 `FontSettings` 目的。

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## 步驟 6：將字型設定套用至文檔

最後，應用程式配置 `FontSettings` 到您的文件並將其儲存為您想要的格式，例如 PDF。

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## 結論

就是這樣！透過遵循這些步驟，您可以確保您的 Word 文件使用正確的字體，無論它們是系統字體還是儲存在特定目錄中的自訂字體。此設定有助於在不同環境中保持文件外觀的完整性。

## 常見問題解答

### 如果系統資料夾和自訂資料夾中都缺少某種字體，會發生什麼情況？

Aspose.Words 將使用預設字體來取代缺少的字體，確保文件仍然可讀。

### 我可以添加多個自訂字體資料夾嗎？

是的，您可以透過重複建立過程來新增多個自訂字體資料夾 `FolderFontSource` 物件並將它們添加到字體來源列表中。

### 是否可以使用網頁路徑來儲存自訂字體資料夾？

是的，您可以在 `FolderFontSource` 構造函數。

### Aspose.Words 支援保存哪些文件格式的文件？

Aspose.Words 支援各種格式，包括 DOCX、PDF、HTML 等。

### 如何處理字型替換通知？

您可以使用以下方式處理字型替換通知 `FontSettings` 班級的 `FontSubstitutionWarning` 事件。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}