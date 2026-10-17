---
category: general
date: 2026-01-03
description: 如何在 Aspose.Words 中偵測字型並使用 Aspose 字型設定處理警告 – 開發人員的逐步指南.
draft: false
keywords:
- how to detect fonts
- how to handle warnings
- aspose font settings
- how to configure warnings
language: zh-hant
og_description: 如何在 Aspose.Words 中偵測字型，並使用 Aspose 字型設定配置警告。只需數分鐘即可了解完整工作流程。
og_title: 如何在 Aspose.Words 中偵測字型 – 處理警告
tags:
- Aspose.Words
- C#
- Document Processing
title: 如何在 Aspose.Words 中偵測字型 – 處理警告與設定
url: /zh-hant/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words 中偵測字型 – 處理警告與設定

有沒有想過 **如何偵測字型** 在 Word 文件中，避免在上線前出現問題？你並不是唯一的擔憂。缺少字型會導致版面混亂，若沒有適當的警告，你甚至可能在不知情的情況下發佈錯誤的 PDF 或 DOCX。

在本教學中，我們將示範 **如何偵測字型**，說明 **如何處理警告**，並調整 **Aspose 字型設定**，讓你可以 **依需求配置警告**。完成後，你將擁有一段即時可執行的程式碼，能列印 Aspose 執行的每一次字型替換，並了解如何將其套用到自己的專案中。

## 前置條件

- .NET 6+（或 .NET Framework 4.6+）。  
- 透過 NuGet 安裝 Aspose.Words for .NET（`Install-Package Aspose.Words`）。  
- 一個刻意引用缺少字型的 Word 檔（例如 *DocumentWithMissingFonts.docx*）。  

如果以上都已備妥，太好了——讓我們開始吧。

![如何偵測字型截圖](https://example.com/detect-fonts.png "如何偵測字型範例輸出")

## 使用 Aspose.Words 偵測字型的方法

第一步是告訴 Aspose.Words 你關心字型替換事件。這可以透過 **Aspose 字型設定** 提供自訂的警告回呼 (warning callback) 來完成。回呼會為每一次替換收到一個 `WarningInfo` 物件，讓你在執行期間 **偵測字型**。

### 步驟 1：建立警告回呼類別

實作 `IWarningCallback` 介面。在 `Warning` 方法內，篩選 `WarningType.FontSubstitution` 並記錄相關資訊。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Receives warnings from Aspose.Words during document loading.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only act on font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **detect fonts** that were missing.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

> **小技巧：** `info.Description` 文字同時包含缺少的字型名稱與 Aspose 所選的替代字型。若需要結構化報表，可自行解析此字串。

### 步驟 2：使用 Aspose 字型設定配置 LoadOptions

建立 `LoadOptions` 實例，附加全新的 `FontSettings` 物件，並將 `WarningCallback` 指向剛才建立的處理器。如此即可告訴 Aspose **如何配置警告**。

```csharp
// Prepare load options – this is where we **configure warnings**.
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings can be further customized (e.g., add a custom folder).
    FontSettings = new FontSettings(),
    WarningCallback = new FontSubstitutionWarningHandler()
};
```

如果你有私有字型資料夾，可這樣加入：

```csharp
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

上述程式碼展示了 **Aspose 字型設定** 的另一個面向——你可以自行決定 Aspose 在替換前會搜尋哪些資料夾。

### 步驟 3：載入文件並觸發回呼

使用 `loadOptions` 載入目標文件。當 Aspose 解析檔案時，任何缺少的字型都會觸發警告處理器，從而 **即時偵測字型**。

```csharp
// The document contains missing fonts, which will fire our warning handler.
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);
```

執行程式後，你會看到類似以下的輸出：

```
Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font substituted: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

### 步驟 4：（可選）收集警告以供日後使用

若需將替換資訊保存為報表，可修改處理器，將訊息累積到清單中。

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public List<string> Substitutions { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Substitutions.Add(info.Description);
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

之後你可以將 `handler.Substitutions` 寫入 JSON 檔、傳送至日誌服務，或在 UI 中顯示。

### 步驟 5：以程式方式驗證結果

有時你想斷言 **沒有** 發生任何替換（例如在 CI 建置中）。以下是一段快速檢查程式碼：

```csharp
var handler = new FontSubstitutionWarningHandler();
loadOptions.WarningCallback = handler;

Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);

if (handler.Substitutions.Count == 0)
{
    Console.WriteLine("All fonts were found – no substitutions.");
}
else
{
    Console.WriteLine($"Detected {handler.Substitutions.Count} missing fonts.");
}
```

此片段示範了 **如何處理警告**，讓你在建置流程中取得完全掌控。

## 常見問題與邊緣案例

**如果我要忽略特定的替換該怎麼辦？**  
在 `Warning` 方法內加入條件判斷，對你認為可接受的字型直接 `return` 而不記錄。

**能否完全關閉警告，只回傳布林結果？**  
可以——將 `loadOptions.WarningCallback = null`，然後在載入後檢查 `doc.FontInfo`（但會失去詳細日誌）。

**這在 PDF 轉換時也有效嗎？**  
絕對可以。當你呼叫 `doc.Save("out.pdf")` 時，同樣的警告機制會被觸發，回呼會捕捉轉換過程中的字型交換。

**會不會影響效能？**  
影響極小——每個缺少的字型只會多呼叫幾次方法。若處理大量文件，可考慮快取結果。

## 小結：本章重點

- 透過實作自訂 `IWarningCallback` **偵測字型**。  
- 透過 `LoadOptions.WarningCallback` **處理警告**。  
- 調整 **Aspose 字型設定**（加入自訂字型資料夾、啟用/停用警告）。  
- **配置警告** 以同時支援即時主控台輸出與日後分析。  

有了這些技巧，你即可自信地處理 Word 文件，確保缺少字型會被標記，並在不同環境中保持輸出一致。

## 後續步驟

- 探索 `FontSettings.SubstitutionSettings` 以取得更細緻的控制（例如將特定缺少的字型映射到指定的替代字型）。  
- 結合此方法與 Aspose.PDF，產生保留精確排版的 PDF。  
- 在 CI/CD 流程中自動化警告檢查，阻止含有字型問題的版本發布——對於將 **處理警告** 作為品質門檻的團隊而言，這是完美的做法。

對 **Aspose 字型設定** 有更多疑問，或需要將此整合到更大型服務中？歡迎在下方留言，祝開發順利！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}