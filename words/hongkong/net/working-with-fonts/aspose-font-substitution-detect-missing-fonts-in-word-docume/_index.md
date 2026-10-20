---
category: general
date: 2026-04-05
description: Aspose 字型替換指南：在載入 Word 文件時偵測缺失的字型。學習如何設定字型參數，並有效處理缺失的字型。
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- configure font settings
- handle missing fonts
language: zh-hant
og_description: Aspose 字體置換指南：在載入 Word 文件時偵測缺失字體。學習如何設定字體設定並有效處理缺失字體。
og_title: Aspose 字體替換 – 檢測 Word 文件中缺失的字體
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose 字型替換 – 偵測 Word 文件中缺失的字型
url: /zh-hant/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docume/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose 字型替換 – 偵測 Word 文件中缺少的字型

有沒有遇過同一個 Word 檔在一台機器上顯示正常，卻在另一台機器上出現奇怪的字型變更？這就是經典的 **aspose font substitution** 問題，通常代表目標系統缺少某些字型。在本教學中，我們將一步一步示範如何在 **載入 Word 文件** 時 **偵測缺少的字型**、如何 **設定字型選項**，以及如何優雅地 **處理缺少的字型**。

我們會走過完整、可執行的 C# 範例，說明每一行程式碼的意義，並展示預期的主控台輸出。完成後，你將能在文件載入的瞬間即發現字型替換，無需猜測。

## 你將學到

- 如何為 Aspose.Words 啟用字型警告的診斷收集器。  
- 載入 Word 文件時使用自訂 **字型設定** 的完整程式碼。  
- 如何遍歷 `WarningInfo` 物件以列出每一個被替換的字型。  
- 抑制不必要警告或提供備用字型的技巧。  
- 可直接複製貼上到 Visual Studio 的即用範例。

### 前置條件

- .NET 6.0 或更新版本（在 .NET Framework 上的 API 行為相同）。  
- Aspose.Words for .NET（NuGet 套件 `Aspose.Words`）。  
- 一個引用了你未安裝字型的 Word 檔（例如 `MissingFont.docx`）。  

如果你已具備上述條件，讓我們開始吧。

## 第一步 – 啟用診斷收集器（設定字型選項）

首先要先讓 Aspose.Words 記錄字型替換警告，必須建立 `FontSettings` 物件並指派給 `LoadOptions` 實例。這就像為字型處理開啟「除錯燈」一樣。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options with a fresh FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    // The FontSettings object is the hub for all font‑related configuration.
    FontSettings = new FontSettings()
};
```

**為什麼要這樣做？**  
如果沒有 `FontSettings` 物件，警告收集器會保持沉默，你永遠不會知道哪些字型被替換。將它以空設定初始化，我們就讓 Aspose 使用預設系統字型 *同時* 追蹤任何替換情況。

> **專業提示：** 若你知道某個資料夾內有公司字型，可使用 `SetFontsFolder("path")` 指向該資料夾，這樣可以減少缺少字型的警告數量。

## 第二步 – 使用已設定的選項載入文件（載入 Word 文件）

收集器啟動後，使用相同的 `LoadOptions` 載入 `.docx` 檔。此時 Aspose 會掃描文件、檢查每一個字型參考，並決定是否需要替換。

```csharp
// Step 2: Load the Word file while applying the previously defined load options.
Document document = new Document(@"C:\Docs\MissingFont.docx", loadOptions);
```

**這有什麼重要性？**  
如果直接呼叫 `new Document("MissingFont.docx")`，會套用預設設定，且警告清單會保持空白。傳入 `loadOptions` 可確保診斷收集器已掛接到載入流程中。

## 第三步 – 取得並顯示字型替換警告（偵測缺少的字型）

文件載入記憶體後，Aspose 會將警告存於 `document.WarningCallback.Warnings`。遍歷此集合，篩選 `WarningType.FontSubstitution`，並印出說明文字。每條說明都會告訴你哪個字型缺失、使用了哪個備用字型。

```csharp
// Step 3: Examine the warning list for any font substitution entries.
foreach (WarningInfo warningInfo in document.WarningCallback.Warnings)
{
    if (warningInfo.Type == WarningType.FontSubstitution)
    {
        // The Description contains a human‑readable message, e.g.,
        // "Font 'Comic Sans MS' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warningInfo.Description}");
    }
}
```

**預期的主控台輸出**

```
Substituted font: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Substituted font: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

這段輸出會精確告訴執行程式的機器缺少哪些字型。接著你可以決定是安裝缺少的字型、將其嵌入文件，或是保留替換結果。

![顯示 Aspose 字型替換警告的主控台輸出](/images/aspose-font-substitution-console.png)

*圖片說明：* aspose 字型替換 – 主控台輸出列出被替換的字型

## 第四步 – 可選：自訂替換行為（處理缺少的字型）

有時候你不只想知道 *發生了* 替換，還想控制 *如何* 替換。Aspose.Words 允許你註冊自訂的 `IFontSubstitutionRule`。以下範例會將所有缺少的字型強制回退至 `Tahoma`。

```csharp
// Optional Step 4 – Define a custom substitution rule.
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        // Always return Tahoma regardless of the missing font.
        return new FontInfo("Tahoma");
    }
}

// Apply the rule to the FontSettings we created earlier.
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(new TahomaFallbackRule());
```

**什麼情況下會使用這個？**  
如果你為 Web 服務產生 PDF，且知道所有客戶端都能正確渲染 `Tahoma`，強制回退可保證視覺一致性，且不必攜帶大量字型檔案。

## 完整可執行範例（結合所有步驟）

以下是可直接貼到新 Console 專案的完整程式碼。只要已安裝 Aspose.Words NuGet 套件，即可直接編譯執行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1 – Enable diagnostic collector (configure font settings)
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Optional: Force all missing fonts to Tahoma
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(
            new TahomaFallbackRule());

        // -------------------------------------------------
        // Step 2 – Load the document (load word document)
        // -------------------------------------------------
        Document doc = new Document(@"C:\Docs\MissingFont.docx", loadOptions);

        // -------------------------------------------------
        // Step 3 – List any font substitutions (detect missing fonts)
        // -------------------------------------------------
        foreach (WarningInfo warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"Substituted font: {warning.Description}");
        }
    }
}

// -------------------------------------------------
// Optional custom rule class (handle missing fonts)
// -------------------------------------------------
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        return new FontInfo("Tahoma");
    }
}
```

執行程式，觀察主控台，即可看到每一次缺少字型的事件被列印出來。之後你可以決定是安裝缺少的字型、將其嵌入，或是保留回退設定。

## 常見問題

**Q: 這能用於 PDF 轉換嗎？**  
可以。當你稍後呼叫 `doc.Save("output.pdf")` 時，載入期間被替換的字型會被嵌入 PDF。因此提前捕捉警告可避免最終 PDF 出現意外的字型變更。

**Q: 若要處理大量文件該怎麼做？**  
將載入邏輯包在 try‑catch 區塊內，並在多個文件之間重複使用同一個 `FontSettings` 實例。這樣可減少開銷，且每個檔案都會保有警告收集器。

**Q: 能完全抑制警告嗎？**  
可以在載入前設定 `loadOptions.WarningCallback = null;`，但這會失去 **偵測缺少字型** 的能力——通常不是你想要的結果。

## 結論

我們已完整說明如何掌握 **aspose font substitution**：啟用診斷收集器、使用自訂 **字型設定** 載入 Word 檔、擷取缺少字型清單，甚至覆寫預設的替換規則以 **自行處理缺少的字型**。只需幾行 C# 程式碼，即可獲得對字型問題的完整可視性，避免因隱藏的版面變化而產生困擾。

接下來的步驟？試著使用 `FontSettings.SetFontsFolder` 將原始字型嵌入文件，或探索 `FontSourceBase` 從資料庫載入字型。你也可以實驗 `Document.BuiltInStyle` 集合，觀察樣式層級的字型變更如何傳遞。

對 Aspose.Words 或字型管理還有其他疑問嗎？歡迎留言、參考官方 Aspose 文件，或開啟新專案親自玩玩上面的程式碼。祝開發順利，文件永遠如你所願正確呈現！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}