---
category: general
date: 2026-01-14
description: 在使用 Aspose.Words 載入 Word 文件時記錄字型替換警告。學習如何偵測缺少的字型以及在 C# 中捕捉缺少的字型。
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: zh-hant
og_description: 在使用 Aspose.Words 載入 Word 文件時記錄字型替換警告。了解如何偵測缺少的字型並在 C# 中捕捉缺少的字型。
og_title: 字型置換警告日誌 – 完整 Aspose.Words 指南
tags:
- Aspose.Words
- C#
- Document Processing
title: 字型置換警告日誌 – 完整 Aspose.Words 指南
url: /zh-hant/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 記錄字型替換警告 – 完整 Aspose.Words 指南

記錄字型替換警告在您需要保證 Word 文件在 Aspose.Words 載入後外觀完全相同時相當重要。如果您曾想過要 **偵測缺少的字型**，或想了解 **如何擷取缺少的字型**，這裡就是您的答案。  

在本教學中，我們將示範一個真實情境，提供完整的 C# 程式碼，並說明每一行的意義。完成後，您將能記錄每一次字型替換事件，並依此採取行動——不再有神祕的警告。

![記錄字型替換警告範例](/images/font-warnings.png "螢幕截圖顯示記錄字型替換警告的主控台輸出")

## 您將學習

- 如何設定 `LoadOptions`，讓 Aspose.Words 為字型替換拋出型別化警告。  
- 在文件載入過程中 **偵測缺少的字型** 的完整步驟。  
- 一種乾淨的方式 **擷取缺少的字型**，並寫入您自己的日誌或監控系統。  
- 邊緣案例處理（例如：文件使用了伺服器上未安裝的字型）。  

### 前置條件

- .NET 6.0 或更新版本（此程式碼亦支援 .NET Framework 4.6+）。  
- 有效的 Aspose.Words for .NET 授權（或免費試用版）。  
- 基本的 C# 與主控台應用程式知識。  

如果您已具備上述條件，讓我們開始吧。

## 第一步 – 設定 LoadOptions 以拋出型別化警告

解決方案的核心在於 `LoadOptions.FontSubstitutionWarning`。將其切換為 `RaiseTypedWarnings` 後，您告訴 Aspose.Words **每當找不到精確字型時** 都會觸發事件。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **為什麼這很重要：**  
> 預設行為會在找不到字型時靜默地換成最相近的字型，這可能導致您未曾預見的版面配置問題。拋出型別化警告則能讓您完整掌握情況。

## 第二步 – 訂閱警告事件

現在我們連接到 `loadOptions.FontSubstitutionWarning`。lambda 會收到一個 `e` 物件，告訴我們哪個字型缺失以及使用了哪個替代字型。

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **小技巧：** 若您在 Web 伺服器上執行此程式，請將 `Console.WriteLine` 改為結構化日誌（Serilog、NLog 等），以便日後查詢。

## 第三步 – 使用已設定的選項載入文件

在警告機制就緒後，直接以平常方式載入文件即可。每一個缺少的字型都會自動觸發事件。

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### 預期的主控台輸出

如果 `input.docx` 參考了未安裝的 *MyFancyFont*，您會看到：

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

每一行都對應到一次 **偵測缺少的字型** 事件，提供完整的稽核軌跡。

## 第四步 – 處理邊緣案例與進階情境

### 4.1 沒有發生替換時

有時文件只使用系統已安裝的字型，這種情況下警告事件不會觸發，主控台會保持空白。這表示您的環境已具備所有必需的字型，屬於好現象。

### 4.2 為日後分析擷取警告

若您需要將警告儲存起來以供夜間報表使用，可將它們收集到清單中：

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

載入完成後，您可以將 `missingFonts` 序列化為 JSON、寫入資料庫，或寄送摘要郵件。

### 4.3 處理 PDF 或其他格式

相同的 `LoadOptions` 方式同樣適用於 PDF、RTF，甚至 HTML 檔案的 `Load` 呼叫。只要傳入相同的 options 實例，Aspose.Words 就會為任何找不到匹配的字型拋出警告。

## 第五步 – 以程式方式驗證結果

如果您想以自動化測試取代肉眼觀察主控台，可斷言清單中包含預期的項目：

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

此片段示範了 **如何在程式碼中擷取缺少的字型**，而不僅僅是寫入日誌。

## 常見問題與避免方式

| 常見問題 | 發生原因 | 解決方法 |
|----------|----------|----------|
| 忘記設定 `RaiseTypedWarnings` | 預設為 `DoNotRaise`，因此不會觸發事件。 | 如步驟 1 所示，明確設定 `FontSubstitutionWarning`。 |
| 在 Web 應用中使用 `Console.WriteLine` | IIS/ASP.NET Core 會讓主控台輸出消失。 | 改用持久化日誌（例如 Serilog）。 |
| 使用相對路徑載入文件 | 執行時的工作目錄可能不同。 | 使用絕對路徑或 `Path.Combine(AppContext.BaseDirectory, "input.docx")`。 |
| 忽略 `SubstitutedFontName` | 失去哪個備用字型被選擇的資訊。 | 必須同時記錄 `FontName` 與 `SubstitutedFontName`。 |

## 加分：自動化安裝字型

若您能掌控部署環境，可使用 PowerShell 腳本預先安裝缺少的字型：

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

在應用程式啟動前執行此腳本，可消除大多數 **偵測缺少的字型** 警告。

## 結論

我們已完整說明在使用 Aspose.Words 載入 Word 文件時，**記錄字型替換警告** 的所有步驟。透過設定 `LoadOptions`、訂閱警告事件，並視需要持久化結果，您可以可靠地 **偵測缺少的字型**，並了解 **如何擷取缺少的字型**，適用於任何 .NET 專案。

拿取範例程式碼，依您的日誌框架調整，即可避免再次遭遇靜默的字型替換。未來可能的延伸方向包括：

- 將警告清單整合至 CI/CD 流程，於關鍵字型缺失時中止建置。  
- 擴充此機制以監控整個文件群的字型使用情況。  
- 探索 Aspose.Words 的 `FontSettings` API，提供自訂的備援字型。

有任何問題或特殊情境想討論？歡迎留言，我們一起排除故障。祝開發順利！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}