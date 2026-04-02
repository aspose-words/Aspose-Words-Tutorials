---
category: general
date: 2026-04-02
description: 如何使用 Aspose.Words 在 C# 文件中偵測字型。學習設定字型配置並有效處理缺少的字型。
draft: false
keywords:
- how to detect fonts
- configure font settings
- handle missing fonts
- font substitution warning
- Aspose.Words font handling
language: zh-hant
og_description: 如何使用 Aspose.Words 在 C# 文件中偵測字型。本指南將教您如何設定字型設定以及處理缺少的字型。
og_title: 如何在 C# 中偵測字體 – 完整指南
tags:
- C#
- Aspose.Words
- Document Processing
title: 如何在 C# 中偵測字型 – 完整指南
url: /zh-hant/net/working-with-fonts/how-to-detect-fonts-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中偵測字型 – 完整指南

有沒有想過在 .NET 中載入 Word 文件時，**如何偵測字型**缺失或被替代？你並不是唯一遇到這個問題的人——開發人員常常在文件引用了伺服器上未安裝的字型時卡住。好消息是 Aspose.Words 為你提供了一個乾淨、程式化的方式來找出這些缺口。

在本教學中，我們將逐步示範一個實作範例，不僅展示 **如何偵測字型**，還示範如何 **設定字型設定** 以及 **優雅地處理缺失字型**。完成後，你將擁有一段可直接執行的程式碼片段，會列印所有字型替換警告，讓你可以記錄、提醒或依需求替換字型。

---

## 需要的條件

- **Aspose.Words for .NET**（最新版本效果最佳；以下程式碼以 .NET 6+ 為目標）
- .NET 開發環境（Visual Studio、Rider 或 VS Code）
- 一個引用了你未安裝字型的範例 `.docx`（非常適合測試）

除了 Aspose.Words 之外不需要額外的 NuGet 套件，且此解決方案可在 Windows、Linux 與 macOS 上執行。

---

## 步驟 1：安裝與參考 Aspose.Words

首先，將此函式庫加入你的專案。NuGet 指令非常簡單：

```bash
dotnet add package Aspose.Words
```

> **專業提示：** 若你在 CI 伺服器上，請鎖定套件版本以避免意外的破壞性變更。

---

## 步驟 2：設定字型設定（並準備載入選項）

在開啟文件之前，你可以告訴 Aspose.Words 從哪裡尋找備用字型。這就是 **設定字型設定** 的部分，可防止引擎在未經你同意的情況下靜默替換字型。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 2: Create a FontSettings object and point it to a folder with fallback fonts
var fontSettings = new FontSettings();

// Example: add a custom folder that contains common Windows fonts
fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);

// You can also embed a default font to use when nothing matches
fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

// Wrap the settings into LoadOptions so Aspose.Words uses them when loading
var loadOptions = new LoadOptions { FontSettings = fontSettings };
```

為什麼要這麼做？如果文件引用了 *Comic Sans*，但你的伺服器只有 *Calibri*，Aspose.Words 會將 *Calibri* 替代並拋出警告。透過設定搜尋路徑，你可以減少不必要的驚喜。

---

## 步驟 3：使用先前設定的選項載入文件

現在我們真正開啟檔案。前一步建立的 `LoadOptions` 會直接傳遞給 `Document` 建構函式。

```csharp
// Step 3: Load the Word file using the configured FontSettings
var docPath = @"C:\Docs\input.docx";
var document = new Document(docPath, loadOptions);
```

如果找不到檔案或檔案損毀，會拋出例外——因此在正式環境的程式碼中，你可能需要將其包在 try/catch 中。

---

## 步驟 4：掃描文件警告以偵測字型替換

Aspose.Words 在解析時會收集一系列警告。其中，`FontSubstitutionWarning` 會精確告訴你哪個字型被替換。

```csharp
// Step 4: Iterate over warnings and look for FontSubstitutionWarning instances
foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fontWarning)
    {
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
}
```

`Warnings` 集合可能還包含其他項目（例如 `DocumentStructureWarning`）。過濾 `FontSubstitutionWarning` 可確保我們只回報 **處理缺失字型** 的情境。

---

## 步驟 5：整合全部 – 完整、可執行的範例

以下是完整程式。將它複製貼上到新的 console 應用程式並執行；你會看到每個缺失的字型被印出到主控台。

```csharp
// Full example: Detect font substitutions in a Word document
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare font settings (configure font settings)
        var fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);
        fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

        // 2️⃣ Build load options with those settings
        var loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document (handle missing fonts gracefully)
        var docPath = @"C:\Docs\input.docx";
        Document document;
        try
        {
            document = new Document(docPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Scan warnings for font substitution events
        bool anySubstitutions = false;
        foreach (WarningInfo warning in document.Warnings)
        {
            if (warning is FontSubstitutionWarning fontWarning)
            {
                anySubstitutions = true;
                Console.WriteLine(
                    $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
            }
        }

        // 5️⃣ Inform the user if everything was fine
        if (!anySubstitutions)
        {
            Console.WriteLine("No font substitutions detected – all fonts were found.");
        }
    }
}
```

**預期輸出**（範例）：

```
Font 'Times New Roman' was substituted with 'Arial'.
Font 'Comic Sans MS' was substituted with 'Arial'.
```

如果文件僅使用機器上已存在的字型，則會看到 “No font substitutions detected” 這行文字。

---

## 邊緣情況與常見問題

### 如果文件根本沒有 **任何警告** 呢？

這僅表示所有引用的字型皆在你設定的搜尋資料夾中找到。範例中的 `anySubstitutions` 旗標已處理此情況。

### 我可以將警告 **記錄** 到檔案而不是主控台嗎？

當然可以。將 `Console.WriteLine` 呼叫換成你選擇的記錄器（Serilog、NLog 等）。如果需要更詳細資訊，`WarningInfo` 物件也會公開 `WarningType` 與 `WarningMessage`。

### 我該如何 **忽略** 某些字型，例如永遠不該被替換的公司品牌字型？

你可以加入自訂的替換規則：

```csharp
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("MyBrandFont", new[] { "Arial", "Helvetica" });
```

現在 Aspose.Words 只會將 *MyBrandFont* 替換為列出的備選字型，且仍會收到可供處理的警告。

### 這在 **Linux** 容器上可行嗎？

是的——只要確保掛載包含所需 `.ttf`/`.otf` 檔案的資料夾，並將 `SetFontsFolder` 指向該資料夾。Aspose.Words 不依賴作業系統安裝的字型。

---

## 視覺概覽

![如何偵測字型流程圖](detect-fonts.png "顯示文件中偵測字型步驟的圖示")

*圖片說明文字：* **如何偵測字型** 流程圖，說明設定、載入與警告檢查。

---

## 重點回顧 – 我們學到了什麼

- **如何偵測字型**：使用 Aspose.Words 警告偵測缺失或被替代的字型。  
- 如何 **設定字型設定**：指向自訂字型資料夾並設定預設備用字型。  
- **處理缺失字型** 的策略：從記錄到自訂替換規則。

所有這些都整合在一個緊湊、獨立的 console 應用程式中，你可以將它放入任何 .NET 解決方案。

---

## 往後步驟與相關主題

- **嵌入字型**：直接將字型嵌入輸出文件，以避免未來的替換（使用 `SaveOptions` 搭配 `EmbedFullFonts`）。  
- **程式化字型替換**：在儲存前將缺失的字型替換為特定的備選字型。  
- **效能調校**：在批次處理大量文件時快取 `FontSettings`。

如果你對這些主題感興趣，可搜尋 *configure font settings* 與 *handle missing fonts*——它們會帶你深入了解 Aspose.Words 的字型管理。

祝開發順利！遇到奇怪的字型邊緣情況嗎？留下評論，我們一起排除問題。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}