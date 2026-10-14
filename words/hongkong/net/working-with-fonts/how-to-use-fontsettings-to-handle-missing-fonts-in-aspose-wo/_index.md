---
category: general
date: 2026-03-16
description: 學習如何在 Aspose.Words 中使用 FontSettings 優雅地處理缺失字型——完整程式碼、事件處理與最佳實踐技巧。
draft: false
keywords:
- how to use fontsettings
- handle missing fonts
- Aspose.Words font substitution
- missing font detection C#
- document loading options
language: zh-hant
og_description: 如何在 Aspose.Words 中使用 FontSettings 處理缺失字型——逐步指南，附完整 C# 範例與實用技巧。
og_title: 如何使用 FontSettings 處理 Aspose.Words 中缺失的字型
tags:
- Aspose.Words
- C#
- Font Management
title: 如何使用 FontSettings 處理 Aspose.Words 中缺失的字型
url: /zh-hant/net/working-with-fonts/how-to-use-fontsettings-to-handle-missing-fonts-in-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words 中使用 FontSettings 處理缺失字型

有沒有想過 **如何在 Word 文件引用了伺服器上未安裝的字型時使用 FontSettings**？你並不孤單。缺失的字型會導致醜陋的備援字型，甚至拋出例外，而大多數開發者會等到問題在正式環境出現才去處理。

在本教學中，我們將示範 **如何使用 FontSettings** 來 **處理缺失字型**，捕捉詳細警告，並讓文件渲染保持可預測。完成後，你將擁有可直接執行的 C# 範例，了解每一行程式碼的意義，並知道如何將此解決方案套用到更大型的專案。

## 本指南涵蓋內容

- 設定 **FontSettings** 並訂閱 `SubstitutionWarning` 事件。  
- 將設定附加至 `LoadOptions`，讓載入文件時能套用。  
- 執行一個刻意缺少字型的測試文件，並閱讀主控台輸出。  
- 記錄、停用自動替代以及處理多個缺失字型等邊緣情況的技巧。  

不需要額外的外部文件說明——所有資訊皆在此處。

## 前置條件

- .NET 6+（或 .NET Framework 4.6.2+）。  
- Aspose.Words for .NET 23.9 或更新版本（本教學使用的 API 在近期版本皆保持穩定）。  
- 一個 `.docx` 檔案，裡面引用了你知道未安裝的字型（例如在 Linux 容器中未安裝 *Comic Sans MS*）。  

就這些——不需要除 Aspose.Words 之外的其他 NuGet 套件。

## 為何要處理缺失字型

當文件引用的字型在執行環境找不到時，Aspose.Words 會自動替換為最相近的字型。這種替代在大多數情況下可接受，但有時你需要 **記錄** 哪些字型缺失（合規需求）或 **阻止** 替代（例如品牌專屬 PDF）。透過 `FontSettings.SubstitutionWarning`，你即可取得完整的可見性與控制權。

## 步驟 1：建立 FontSettings 並訂閱 Substitution‑Warning 事件

首先建立 `FontSettings`。此物件負責保存所有與字型相關的設定。關鍵在於連接 `SubstitutionWarning` 事件，該事件會在 Aspose.Words 找不到請求的字型時 **每次** 觸發。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – Initialise FontSettings and listen for missing‑font warnings
FontSettings fontSettings = new FontSettings();

// The lambda receives detailed info about the missing font and the chosen substitute.
fontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.MissingFontName  → the name Aspose.Words tried to load.
    // e.SubstitutedFontName → the font that was actually used instead.
    // e.WarningType → the enum describing why the warning was raised.
    Console.WriteLine($"Missing font: {e.MissingFontName}");
    Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
    Console.WriteLine($"Reason: {e.WarningType}");
};
```

**為什麼這很重要：**  
- **可見性：** 立即得知缺失的字型。  
- **可稽核性：** 主控台（或記錄器）可導向檔案，以供合規報告。  
- **可控制性：** 之後你可以自行替換為自訂字型。

> **小技巧：** 若你使用記錄框架（Serilog、NLog 等），可將 `Console.WriteLine` 改為 `logger.Information(...)`。

## 步驟 2：將 FontSettings 附加至 LoadOptions

`LoadOptions` 是告訴 Aspose.Words 在載入階段如何處理檔案的載具。將 `FontSettings` 物件指派給它，即可確保在解析任何內容之前，警告處理器已啟用。

```csharp
// Step 2 – Bind FontSettings to LoadOptions so the loader knows about our event handler
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**為什麼這很重要：**  
- 若未傳入 `LoadOptions` 就載入文件，預設的字型處理機制會啟動，你將錯過警告。  
- 此方式同時允許你在同一個物件中調整其他載入行為（例如密碼保護）。

## 步驟 3：使用已設定的選項載入文件

現在終於讀取 Word 檔案。路徑可以是絕對或相對路徑；Aspose.Words 會遵循我們剛剛準備好的 `LoadOptions`。

```csharp
// Step 3 – Load the document while applying our FontSettings
string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";   // <-- adjust to your environment
Document document = new Document(docPath, loadOptions);
```

如果文件中包含未安裝的字型，`SubstitutionWarning` 事件會被觸發，主控台會顯示類似以下的輸出。

### 預期的主控台輸出

```
Missing font: Comic Sans MS
Substituted with: Arial
Reason: FontSubstitution
```

實際的替代字型會依作業系統的字型備援鏈而異，但 **缺失的字型名稱** 必定會被報告。

## 步驟 4：驗證結果（可選的渲染）

通常你會想確認文件在替代後仍然保持正常外觀。最簡單的方式是將其另存為 PDF 並開啟檢視。

```csharp
// Optional: Save as PDF to visually confirm the substitution
document.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
Console.WriteLine("Document saved as PDF – check the rendering.");
```

如果你想 **完全阻止** 替代，可在載入前設定 `FontSettings.SubstitutionSettings.TableSubstitution = false`。此時 Aspose.Words 會因缺失字型拋出例外，你可以自行捕獲並處理。

```csharp
// Disable automatic substitution – will raise an exception on missing fonts
fontSettings.SubstitutionSettings.TableSubstitution = false;
```

## 完整可執行範例

以下是完整、可直接執行的程式。將它貼到 Console 應用程式中，調整檔案路徑後按 **F5**。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create FontSettings and hook the warning event
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionWarning += (sender, e) =>
            {
                Console.WriteLine($"Missing font: {e.MissingFontName}");
                Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
                Console.WriteLine($"Reason: {e.WarningType}");
            };

            // 2️⃣ Attach FontSettings to LoadOptions
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings
                // Uncomment the next line to *disable* substitution and force an exception
                // , FontSettings = { SubstitutionSettings = { TableSubstitution = false } }
            };

            // 3️⃣ Load the document
            string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save as PDF to see the visual result
            doc.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
            Console.WriteLine("Processing complete. Check the console for missing‑font warnings.");
        }
    }
}
```

### 期待的結果

- 主控台會列印每個缺失字型以及所選的替代字型。  
- 若保留了可選的另存動作，產生的 PDF 會使用備援字型顯示文件，確保版面完整。

## 常見問題與邊緣情況

| 問題 | 解答 |
|----------|--------|
| **如果同時缺少多個字型，該怎麼辦？** | 事件會對每個缺失的字型觸發一次，會產生多行獨立的記錄。 |
| **我可以用自訂字型取代備援字型嗎？** | 可以。在事件處理器內呼叫 `e.SubstitutedFont = new FontInfo("MyCustomFont")` 即可。 |
| **嵌入的字型載入失敗也會觸發警告嗎？** | 會——不論是外部字型或嵌入字型，警告機制相同。 |
| **需要手動釋放 `Document` 嗎？** | `Document` 實作 `IDisposable`。若在迴圈中大量載入檔案，建議使用 `using` 區塊。 |
| **在 Linux 容器上可行嗎？** | 只要 Aspose.Words 能透過 `fontconfig` 找到系統字型，事件機制同樣適用。 |

## 最佳實踐與進階技巧

- **集中式記錄：** 建立輔助方法，同時寫入主控台與永久性日誌檔。  
- **批次處理：** 轉換大量文件時，重複使用同一個 `FontSettings` 實例，以避免重複訂閱事件。  
- **效能考量：** 警告本身開銷極低，但若處理上千檔案，可在驗證完字型集合後考慮關閉警告。  
- **版本安全性：** `SubstitutionWarning` API 自 Aspose.Words 16.0 起即穩定，未來升級可放心使用。

## 結論

我們已示範 **如何在 Aspose.Words 中使用 FontSettings** 來 **優雅地處理缺失字型**。透過建立 `FontSettings` 物件、訂閱 `SubstitutionWarning`，以及以 `LoadOptions` 載入文件，你可以完整掌握字型問題，決定是記錄、替換或在缺失時中止。

從簡單的主控台輸出到自訂替代邏輯，此模式可擴展至大型批次文件管線，確保輸出始終一致且可稽核。

**後續步驟：**  

- 探索在事件內指派 `e.SubstitutedFont` 以實作 **自訂字型替代**。  
- 結合此方法與 **文件渲染為影像**，產生縮圖。  
- 若需將替代字型直接嵌入最終 PDF，請參考 **Aspose.PDF**。

祝開發順利，願你的文件永遠不再受缺失字型的困擾！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}