---
title: 設定字體資料夾多個資料夾
linktitle: 設定字體資料夾多個資料夾
second_title: Aspose.Words 文件處理 API
description: 了解如何使用 Aspose.Words for .NET 在 Word 文件中設定多個字體資料夾。本逐步指南可確保您的文件使用您所需的確切字體。
weight: 10
url: /zh-hant/net/working-with-fonts/set-fonts-folders-multiple-folders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 設定字體資料夾多個資料夾

## 介紹

有沒有想過如何管理 Word 文件中的多個字型來源？也許您有一組分散在不同資料夾中的字體，並且您需要一種方法來確保您的文件無縫地使用它們。嗯，你很幸運！今天，我們將深入研究如何使用 Aspose.Words for .NET 設定字體資料夾。本指南將引導您逐步完成整個過程，確保您的文件看起來如您所願。

## 先決條件

在我們開始之前，讓我們確保您擁有所需的一切。以下是您需要遵循的操作：

-  Aspose.Words for .NET：如果您尚未下載並安裝 Aspose.Words for .NET，請下載並安裝。你可以得到它[這裡](https://releases.aspose.com/words/net/).
- 開發環境：Visual Studio 或任何其他.NET 相容的開發環境。
- C# 基礎知識：稍微熟悉一下 C# 將有助於您理解範例。
- 字體檔案：確保將字體檔案儲存在可以輕鬆存取的目錄中。

## 導入命名空間

首先，讓我們在 C# 專案中導入必要的命名空間。這可確保您能夠存取所需的所有 Aspose.Words 功能。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

完成該設定後，讓我們深入了解在 Aspose.Words for .NET 中設定字體資料夾的逐步指南。

## 第 1 步：載入您的文檔

好吧，讓我們先載入您要使用的 Word 文件。確保您已準備好文件路徑。在此範例中，我們將使用名為「Rendering.docx」的文件。

```csharp
//文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

在這裡，我們從指定目錄載入文件。很簡單，對吧？

## 第 2 步：建立 FontSettings 對象

接下來，我們需要建立一個`FontSettings`目的。該物件將允許我們管理文件的字體來源。

```csharp
FontSettings fontSettings = new FontSettings();
```

這`FontSettings`物件將幫助我們定義要使用的字體資料夾。

## 第三步：設定字體資料夾

現在到了關鍵的部分——設定字體資料夾。您可以在此指定字體所在的目錄。在此範例中，我們在「C:\MyFonts\」和「D:\Misc\Fonts\」。

```csharp
fontSettings.SetFontsFolders(new[] { @"C:\MyFonts\", @"D:\Misc\Fonts\" }, true);
```

第二個參數（`true` ) 表示這些資料夾將覆蓋任何預設字體來源。如果您還想保留系統字體來源，您可以使用以下組合`GetFontSources`和`SetFontSources`.

## 步驟 4：將字型設定套用到文檔

設定字體資料夾後，我們需要將這些設定套用到我們的文件中。這可確保文件在渲染期間使用指定的字體。

```csharp
doc.FontSettings = fontSettings;
```

## 第 5 步：儲存文檔

最後，讓我們儲存文件。我們將其儲存為 PDF 以查看實際使用的字體。

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersMultipleFolders.pdf");
```

現在你就擁有了！您已成功為文件設定多個字型資料夾。

## 結論

管理文件中的字體似乎是一項艱鉅的任務，但使用 Aspose.Words for .NET，這一切變得輕而易舉！透過執行這些簡單的步驟，您可以確保您的文件看起來專業並使用您需要的確切字體。無論您正在處理需要特定品牌的專案還是只想更好地控製文件的外觀，設定字體資料夾都是值得掌握的技能。

## 常見問題解答

### 我可以使用字體資料夾的網頁路徑嗎？
是的，您可以使用字型資料夾的網頁路徑。只需確保可以從您的應用程式存取這些路徑即可。

### 如果指定資料夾中缺少字體會發生什麼情況？
如果缺少字體，Aspose.Words 將回退到指定的預設字體或使用替代字體。

### 我可以添加字體資料夾而不覆蓋系統字體嗎？
絕對地！使用`FontSettings.GetFontSources`檢索現有來源並將其與您的自訂資料夾組合使用`FontSettings.SetFontSources`.

### 我可以添加的字體文件夾數量有限制嗎？
字體資料夾的數量沒有嚴格限制。但是，請注意效能，因為更多資料夾可能會增加字體載入時間。

### 如何檢查我的文件中使用了哪些字體？
您可以使用`FontSettings.GetFontsSources`檢索和檢查目前為文件設定的字型來源的方法。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
