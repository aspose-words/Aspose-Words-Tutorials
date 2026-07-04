---
category: general
date: 2026-05-23
description: 設定 Aspose 警告回呼，以捕捉 Aspose.Words 中的字型替換警告。了解 LoadOptions、FontSettings
  與 IWarningCallback 的實作。
draft: false
keywords:
- set warning callback aspose
- aspose words loadoptions
- aspose fonts substitution
- iwarningcallback implementation
- aspose document loading
language: zh-hant
og_description: 設定 Aspose 警告回呼，以監控 Aspose.Words 中的字型替換。本教學展示 LoadOptions、FontSettings
  以及警告處理程式的實作。
og_title: 設定警告回調 aspose – 步驟指南
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  headline: set warning callback aspose – Complete Guide for Word Document Loading
  type: TechArticle
- description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  name: set warning callback aspose – Complete Guide for Word Document Loading
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well). -
      A valid Aspose.Words for .NET license or a trial key. - Visual Studio, Rider,
      or any C# editor you prefer. - A sample DOCX (`fontTest.docx`) that references
      a missing font (optional but helpful).'
  - name: Expected console output
    text: 'If `fontTest.docx` references a font that isn’t installed, you’ll see something
      like:'
  - name: When to use a custom LoadOptions
    text: '- **Batch processing** of many files where you want a uniform logging strategy.
      - **Cloud services** that need to report missing fonts back to the caller. -
      **Testing pipelines** that verify documents adhere to a corporate font policy.'
  type: HowTo
tags:
- Aspose.Words
- C#
- FontSettings
title: 設定警告回呼 aspose – 完整指南：Word 文件載入
url: /zh-hant/net/programming-with-loadoptions/set-warning-callback-aspose-complete-guide-for-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 設定警告回呼 aspose – Word 文件載入完整指南

有沒有想過如何 **set warning callback aspose**，讓你不會再錯過字體替換警示？你並不孤單。當 DOCX 參考了未安裝的字體時，Aspose.Words 會靜默地替換它，若沒有適當的回呼，你可能永遠不會知道有變更。

在本教學中，我們將逐步說明完整且可執行的範例，展示如何捕捉這些警示。完成後，你將了解 **Aspose.Words LoadOptions**、如何設定 **FontSettings**，以及為何實作 **IWarningCallback** 是保持資訊同步的最佳方式。沒有多餘的說明——只提供可直接放入 .NET 專案的程式碼。

## 你將學到

- 如何在 `LoadOptions` 實例上 **set warning callback aspose**。  
- 在開啟文件時 **Aspose.Words LoadOptions** 的作用。  
- 使用 `FontSettings` 設定 **Aspose fonts substitution** 處理方式。  
- 編寫自訂的 **IWarningCallback implementation** 以記錄字體問題。  
- 使用 **Aspose document loading** 的最佳實踐安全載入文件。

### 前置條件

- .NET 6.0 或更新版本（此程式碼亦可於 .NET Framework 4.5+ 執行）。  
- 有效的 Aspose.Words for .NET 授權或試用金鑰。  
- Visual Studio、Rider，或任何你偏好的 C# 編輯器。  
- 一個參考缺失字體的範例 DOCX（`fontTest.docx`）（可選，但有助於測試）。

> **專業提示：** 若沒有缺字體的 DOCX，只需在文件樣式中將字體重新命名，即可看到警示觸發。

## 如何為文件載入設定警告回呼 aspose

以下是完整且獨立的程式。將其儲存為 `Program.cs`，還原 NuGet 套件，然後執行。主控台會列印出 Aspose.Words 在載入檔案時產生的每個字體替換警示。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// ------------------------------------------------------------
// Step 1: Create a warning handler that implements IWarningCallback
// ------------------------------------------------------------
class FontSubstitutionWarningHandler : IWarningCallback
{
    // This method is called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property tells you which font was substituted.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// ------------------------------------------------------------
// Step 2: Prepare FontSettings (default works for most cases)
// ------------------------------------------------------------
FontSettings fontSettings = new FontSettings();
// You could add custom font folders here if you want to avoid substitution:
// fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// ------------------------------------------------------------
// Step 3: Build LoadOptions and attach our warning callback
// ------------------------------------------------------------
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontSubstitutionWarningHandler()
};

// ------------------------------------------------------------
// Step 4: Load the document using the configured LoadOptions
// ------------------------------------------------------------
try
{
    // Replace the path with the location of your test document.
    Document doc = new Document("YOUR_DIRECTORY/fontTest.docx", loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

### 預期的主控台輸出

如果 `fontTest.docx` 參考了未安裝的字體，將會看到類似以下的訊息：

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Document loaded successfully.
```

如果所有字體皆已安裝，唯一列印的行將是 *Document loaded successfully*——沒有警示，沒有雜訊。

![set warning callback aspose example](image.png "set warning callback aspose example")

## 了解 Aspose.Words 中的 LoadOptions

`LoadOptions` 是調整 **aspose document loading** 各項設定的入口。它允許你：

1. **指定自訂的 `FontSettings`** – 當你的應用程式自帶字體時很有用。  
2. **附加警告回呼** – 正是我們用來捕捉字體替換的方式。  
3. 控制文件格式偵測、密碼處理等更多功能。

由於 `LoadOptions` 會傳遞給 `Document` 建構子，設定會 **一次** 生效，於檔案解析的瞬間套用。因此我們能保證警告處理程式會在文件甚至尚未載入記憶體前，就看到每一次的替換。

### 何時使用自訂 LoadOptions

- **批次處理** 多個檔案時，需要統一的記錄策略。  
- **雲端服務** 需要將缺失字體回報給呼叫端。  
- **測試流水線** 用於驗證文件是否符合公司字體政策。

## 為 Aspose 字體替換設定 FontSettings

`FontSettings` 物件控制 Aspose.Words 如何解析字體。預設情況下，它會搜尋系統字體資料夾，然後回退至內建替代字體。你可以微調此行為：

```csharp
FontSettings fontSettings = new FontSettings();

// Add a folder that contains your corporate fonts.
fontSettings.SetFontsFolder(@"C:\Corporate\Fonts", recursive: true);

// Optionally, map a missing font to a specific substitute.
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "MissingFont", new[] { "Arial", "Times New Roman" });
```

這些程式碼對於基本的 “set warning callback aspose” 情境是可選的，但它示範了如何透過事先提供正確字體來 **減少** 替換警示的數量。

## 為字體替換警示實作 IWarningCallback

`IWarningCallback` 介面非常小——僅有一個 `Warning` 方法。但它讓你對警示的處理擁有 **完整控制**：

- **記錄至檔案** 而非主控台。  
- **收集警示** 到清單以供日後分析。  
- **拋出例外** 針對關鍵警示（例如缺少必要字體）。

以下是一個快速範例，將警示存入 `List<string>`：

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

之後你可以在載入文件後檢查 `handler.Messages`，決定是否中止處理。

## 使用自訂警告處理載入文件（完整工作流程）

將所有部份結合起來，你最終可能會重複使用的模式如下：

```csharp
// 1️⃣ Create the warning handler.
CollectingWarningHandler handler = new CollectingWarningHandler();

// 2️⃣ Set up FontSettings (add custom fonts if needed).
FontSettings fs = new FontSettings();
fs.SetFontsFolder(@"C:\MyApp\Fonts", true);

// 3️⃣ Build LoadOptions with both FontSettings and the handler.
LoadOptions opts = new LoadOptions
{
    FontSettings = fs,
    WarningCallback = handler
};

// 4️⃣ Load the document.
Document doc = new Document("input.docx", opts);

// 5️⃣ React to any font‑substitution warnings.
if (handler.Messages.Any())
{
    Console.WriteLine("The following fonts were substituted:");
    foreach (var msg in handler.Messages)
        Console.WriteLine("- " + msg);
}
else
{
    Console.WriteLine("No font issues detected.");
}
```

此程式碼片段示範了在正式環境中使用的 **aspose document loading** 流程：設定、載入，然後回應。無論是處理單一檔案或是成千上萬的迴圈，此模式都能良好擴展。

## 常見問題與邊緣情況

**如果文件受密碼保護怎麼辦？**  
在 `LoadOptions` 初始化器中加入 `Password = "secret"`。檔案解密後，警告回呼仍會正常運作。

**回呼會對其他類型的警示觸發嗎？**  
會——`WarningInfo.Type` 可能是 `DocumentStructure`、`UnsupportedFileFormat` 等。在本例中我們只過濾 `FontSubstitution`，但移除 `if` 判斷即可記錄所有警示。

**這會影響效能嗎？**  
影響可以忽略不計。回呼僅在發生警示時才被呼叫，遠少於正常的解析步驟。

**能否完全停用字體替換？**  
可以將 `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` 設為 false，但屆時 Aspose.Words 會在缺少字體時拋出例外，而非自動替換。

## 結論

你現在已清楚瞭解如何 **set warning callback aspose**，於 **Aspose.Words LoadOptions** 處理過程中監控字體替換事件。透過設定 `FontSettings`、實作輕量的 `IWarningCallback`，並以這些選項載入文件，即可完整掌握 Aspose 在背後所做的任何字體變更。  

接下來你可以：

- 將警告處理程式擴充為寫入集中式日誌服務。  
- 結合回呼與自訂的字體備援策略。  
- 在建構驗證客戶上傳文件的雲端 API 時使用此模式。

試著使用自己的 DOCX 檔案，調整 `FontSettings`，觀察主控台精確顯示哪些字體被替換。祝開發順利，願你的文件永遠如預期般呈現！

## 相關教學

- [在 Java 中捕捉字體替換警示 – Aspose.Words 完整指南](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [在 Aspose.Words 中啟用字體替換警示 – 完整指南](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [如何在 Aspose.Words for Java 中設定 LoadOptions](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}