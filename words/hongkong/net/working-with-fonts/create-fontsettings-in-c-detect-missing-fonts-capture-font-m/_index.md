---
category: general
date: 2026-03-01
description: 在 C# 中建立 FontSettings，以偵測缺少的字型、捕捉字型訊息，並使用 Aspose.Words 處理缺少的字型。開發者逐步指南。
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: zh-hant
og_description: 在 C# 中建立 FontSettings 以偵測缺失字型、捕捉字型訊息，並使用 Aspose.Words 處理缺失字型。完整教學與程式碼。
og_title: 在 C# 中建立 FontSettings – 偵測缺失的字型並捕捉字型訊息
tags:
- Aspose.Words
- C#
- Font Management
title: 在 C# 中建立 FontSettings – 偵測缺失字型並捕捉字型訊息
url: /zh-hant/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中建立 FontSettings – 偵測缺少的字型與擷取字型訊息

是否曾需要在 .NET 專案中 **create FontSettings**，卻不確定如何找出目標機器上未安裝的字型？你並不孤單。在許多實務應用中——例如自動報表產生器或文件轉換器——缺少的字型會悄悄破壞版面，直到 PDF 看起來怪怪的你才會發現。  

如果你能 **detect missing fonts**、**capture font messages**，以及 **handle missing fonts**，在它們破壞輸出之前就處理？好消息是 Aspose.Words 讓這變得輕而易舉。在本教學中，我們將逐步說明整個流程，從設定 `FontSettings` 物件到連接一個警告回呼，告訴你哪些字形被替換。

> **TL;DR:** 完成後，你將擁有一個可直接執行的 C# 主控台應用程式，會記錄每一次字型替換，讓你決定是否嵌入替代字型或提醒使用者。

---

## 前置條件

- .NET 6 SDK（或任何較新的 .NET 版本）  
- Visual Studio 2022 或 VS Code 搭配 C# 擴充功能  
- Aspose.Words for .NET 授權（免費試用可用於此示範）  
- 一個參考了你未安裝字型的範例 DOCX（例如在 Linux 機上使用 *Comic Sans MS*）

除了 `Aspose.Words` 之外，無需其他 NuGet 套件。

## 第一步 – 安裝 Aspose.Words 並設定專案

首先，建立一個新的主控台專案，並將 Aspose.Words 函式庫加入其中。

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **Pro tip**：如果你已經有解決方案，只需透過 NuGet 套件管理員 UI 加入套件——這樣更易於追蹤版本。

## 第二步 – 建立 FontSettings（此處出現主要關鍵字）

**create FontSettings** 步驟是任何字型相關工作流程的基石。`FontSettings` 告訴 Aspose.Words 在哪裡尋找字型、是否使用系統資料夾，以及在缺少字型時如何回退。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

為什麼這很重要？如果沒有正確設定的 `FontSettings`，引擎會悄悄將缺少的字形替換為預設系統字型，而你永遠不會看到警告。

## 第三步 – 使用 FontSettings 連接 LoadOptions

`LoadOptions` 讓你將 `FontSettings` 傳入文件載入器。這是讓引擎在 `Document` 建構階段 **detect missing fonts** 的橋樑。

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

現在每次使用 `loadOptions` 載入 DOCX 時，Aspose.Words 都會參考先前設定的 `FontSettings`。

## 第四步 – 附加警告回呼以 **Capture Font Messages**

Aspose.Words 會針對各種情況發出警告——字型替換是常見情形之一。透過提供 `IWarningCallback` 的實作，你可以即時 **capture font messages**。

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### 警告處理程式類別

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

`info.Description` 欄位包含可讀的訊息，例如 *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* 這正是你需要的，用於優雅 **handle missing fonts** 的輸出。

## 第五步 – 載入文件並讓回呼執行其工作

所有設定完成後，載入文件變得簡單。如果來源檔案參考了系統中不存在的字型，我們的警告處理程式就會觸發。

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

執行程式時，你會看到類似以下的主控台輸出：

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

該輸出即為我們工作流程中 **capture font messages** 的部分。你可以擴充處理程式，以寫入檔案、傳送遙測，或在關鍵字型缺失時中止轉換。

## 第六步 – 完整可執行範例（全部組合）

以下是一個完整、可直接複製貼上的程式。貼到 `Program.cs`，調整檔案路徑，然後執行 `dotnet run`。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### 預期輸出

在缺少 *Comic Sans MS* 的機器上執行程式，會印出類似以下內容：

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

你也會得到使用了替代字型的 `Result.pdf`，確保轉換過程不會崩潰。

## 常見問題與邊緣案例

| Question | Answer |
|----------|--------|
| **如果我想讓轉換失敗而不是自動替換，該怎麼辦？** | 在 `FontSubstitutionWarningHandler` 內，當 `info.Description` 包含關鍵字型名稱時拋出例外。 |
| **我可以自動嵌入替代字型嗎？** | 可以。偵測到缺少字型後，你可以從已知路徑載入備用的 `FontInfo`，並透過 `fontSettings.SetFontsFolder` 加入 `fontSettings`。 |
| **這在 Linux/macOS 上可用嗎？** | 絕對可以。`FontSettings` 支援跨平台；只要確保備用資料夾內有相應的 `.ttf` 或 `.otf` 檔案即可。 |
| **警告回呼是執行緒安全的嗎？** | 回呼在載入文件的同一執行緒上執行，因此對於主控台日誌不需要額外同步。若在多執行緒情境下，請保護共享資源。 |
| **如何將警告寫入檔案？** | 將 `Console.WriteLine` 改為 `File.AppendAllText("font_warnings.log", ...)`，或使用任何日誌框架（Serilog、NLog）。 |

## 生產環境字型處理的專業技巧

1. **快取字型查詢** – 在多個文件載入間重複使用相同的 `FontSettings` 實例，可避免重複的檔案系統掃描。  
2. **白名單關鍵字型** – 若品牌需要特定字型，請提前驗證其是否存在，若缺少則以清晰的錯誤訊息中止。  
3. **遞迴使用 `SetFontFolder`** – 設定 `recursive: true` 可確保掃描子資料夾，當你提供完整字型集合時非常方便。  
4. **結合 `FontSubstitutionSettings`** – 你可以微調替換規則（例如，優先使用相同字族名稱的字型）。  

## 結論

我們剛剛 **created FontSettings**，設定 `LoadOptions` 以 **detect missing fonts**，附加了一個 **captures font messages** 的回呼，並示範如何以乾淨、適合生產環境的方式 **handle missing fonts**。整個流程僅需數十行 C# 程式碼，卻能讓你完整掌握任何 DOCX 的字型情況。

接下來，你可以探索：

- **將備用字型嵌入** 直接到輸出 PDF（`PdfSaveOptions.FontEmbeddingMode`）。  
- **根據企業品牌規則以程式方式替換字型**。  
- **與 CI 流程整合**，自動標記使用未授權字型的文件。

試試看，依需求調整警告處理程式，讓你的文件流程自信運行——再也不會因看不見的字型交換而出現神祕的版面錯誤。

祝程式開發愉快！🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}