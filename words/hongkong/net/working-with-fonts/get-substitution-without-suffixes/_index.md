---
"description": "了解如何在 Aspose.Words for .NET 中管理沒有後綴的字體替換。按照我們的逐步指南，確保您的文件每次都看起來完美無缺。"
"linktitle": "取得不含後綴的替換"
"second_title": "Aspose.Words文件處理API"
"title": "取得不含後綴的替換"
"url": "/zh-hant/net/working-with-fonts/get-substitution-without-suffixes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 取得不含後綴的替換

## 介紹

歡迎閱讀有關使用 Aspose.Words for .NET 管理字體替換的綜合指南。如果您曾經為文件中字體無法正確顯示而苦惱，那麼您來對地方了。本教學將引導您逐步完成有效處理不含後綴的字體替換的過程。

## 先決條件

在深入學習本教學之前，請確保您已具備以下條件：

- C# 基礎知識：了解 C# 程式設計將使遵循和執行步驟變得更容易。
- Aspose.Words for .NET Library：從下載並安裝該程式庫 [下載連結](https://releases。aspose.com/words/net/).
- 開發環境：設定一個像 Visual Studio 這樣的開發環境來編寫和運行您的程式碼。
- 範例文件：範例文件（例如， `Rendering.docx`) 在本教程中使用。

## 導入命名空間

首先，我們需要導入必要的命名空間來存取 Aspose.Words 提供的類別和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## 步驟1：定義文檔目錄

首先，指定文檔所在的目錄。這有助於找到您想要處理的文件。

```csharp
// 文檔目錄的路徑
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 步驟 2：設定替換警告處理程序

接下來，我們需要設定一個警告處理程序，當文件處理過程中發生字體替換時，它會通知我們。這對於捕獲和處理任何字體問題至關重要。

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## 步驟3：新增自訂字體來源

在此步驟中，我們將新增自訂字體來源，以確保 Aspose.Words 可以找到並使用正確的字體。如果您在自訂目錄中儲存了特定的字體，這將特別有用。

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

在此程式碼中：
- 我們檢索目前字體來源並新增新的 `FolderFontSource` 指向我們的自訂字體目錄（`C:\\MyFonts\\`）。
- 然後我們使用這個新清單更新字體來源。

## 步驟4：儲存文檔

最後，應用字型替換設定後儲存文件。對於本教程，我們將其儲存為 PDF。

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## 步驟 5：建立警告處理程序類

為了有效地處理警告，請建立一個自訂類別來實現 `IWarningCallback` 介面.此類將捕獲並記錄任何字體替換警告。

```csharp
public class DocumentSubstitutionWarnings : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            FontWarnings.Warning(info);
    }

    public WarningInfoCollection FontWarnings = new WarningInfoCollection();
}
```

在本課程中：
- 這 `Warning` 方法捕獲與字體替換相關的警告。
- 這 `FontWarnings` 集合儲存這些警告以供進一步檢查或記錄。

## 結論

現在，您已經掌握了使用 Aspose.Words for .NET 處理不含後綴的字體替換的過程。這些知識將確保您的文件保持其預期的外觀，無論系統上可用的字體是什麼。繼續嘗試不同的設定和來源，以充分利用 Aspose.Words 的強大功能。

## 常見問題解答

### 如何使用來自多個自訂目錄的字體？

您可以新增多個 `FolderFontSource` 實例 `fontSources` 列出並相應地更新字體來源。

### 哪裡可以下載 Aspose.Words for .NET 的免費試用版？

您可以從 [Aspose 免費試用頁面](https://releases。aspose.com/).

### 我可以使用 `IWarningCallback`？

是的， `IWarningCallback` 介面可讓您處理各種類型的警告，而不僅僅是字體替換。

### 我可以在哪裡獲得 Aspose.Words 的支援？

如需支持，請訪問 [Aspose.Words 支援論壇](https://forum。aspose.com/c/words/8).

### 可以購買臨時許可證嗎？

是的，你可以從 [臨時執照頁面](https://purchase。aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}