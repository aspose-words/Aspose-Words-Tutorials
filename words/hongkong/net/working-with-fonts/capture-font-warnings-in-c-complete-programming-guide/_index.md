---
category: general
date: 2026-02-18
description: 學習如何在 C# 中使用 Aspose.Words 捕捉字型警告並偵測缺失字型。跟隨此一步一步的指南，有效處理缺失字型。
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: zh-hant
og_description: 在 C# 中捕捉字型警告，學習如何偵測缺失字型、處理缺失字型，並列出缺失字型，附完整程式碼範例。
og_title: 在 C# 中捕捉字型警告 – 完整指南
tags:
- Aspose.Words
- C#
- Font Management
title: 捕捉字型警告於 C# – 完整程式設計指南
url: /zh-hant/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capture Font Warnings in C# – Complete Programming Guide

有沒有想過在文件引用了伺服器上未安裝的字型時，**捕捉字型警告**？你並不是唯一遇到這個問題的人。在許多企業應用程式中，缺少字型會導致版面配置錯亂，而唯一可靠的偵測方式就是監聽程式庫拋出的警告。

在本教學中，我們會示範一個可直接執行的解決方案，不僅能 **捕捉字型警告**，還能 **偵測缺少的字型**、**處理缺少的字型**，甚至 **列出缺少的字型**，讓你決定是替換、嵌入或提示使用者。無需額外文件——只要複製、貼上、執行即可。

## What You’ll Learn

- 如何設定 `LoadOptions` 以開啟字型替換警告。  
- 讀取 DOCX 並取得所有警告的完整程式碼。  
- 為何每一步都很重要，包含效能考量。  
- 針對混合腳本字型或自訂字型資料夾等邊緣情況的處理方式。  

**Prerequisites**: .NET 6+（或 .NET Framework 4.6+）、已參考 **Aspose.Words** NuGet 套件，並具備 C# 基礎。若你從未使用過 Aspose.Words，也不用擔心——本指南會一步步說明所有細節。

![Diagram showing capture font warnings flow](image.png){alt="捕捉字型警告流程圖"}

## Capture Font Warnings – Why It Matters

當 Aspose.Words 載入文件時，會悄悄將任何不可用的字型替換為備用字型。這樣雖然可以讓載入操作繼續，但視覺結果可能會完全偏離預期。透過開啟 **SubstitutionWarningLevel.All** 標誌，程式庫會為每個缺少的字型加入 `WarningInfo` 條目，讓你在文件渲染或儲存前 **偵測缺少的字型**。

> **Pro tip:** 若你在批次作業中處理上百個檔案，將這些警告記錄到集中儲存庫，可為日後的手動 QA 節省大量時間。

## Step 1: Set Up Your Project

1. 開啟你慣用的 IDE（Visual Studio、Rider、VS Code）。  
2. 建立一個新的 Console 專案：

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. 加入 Aspose.Words 套件：

```bash
dotnet add package Aspose.Words
```

就這樣——不需要額外的 DLL，也不需要 COM interop。程式庫已內建處理 **缺少字型** 所需的一切。

## Step 2: Prepare Load Options to Capture All Font Substitution Warnings

要讓引擎 **捕捉字型警告**，必須告訴它記錄每一次替換。以下程式碼會建立 `LoadOptions` 實例、啟用警告等級，並（可選）指向一個包含自訂字型的資料夾。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**Why this matters:**  
- `SubstitutionWarningLevel.All` 確保 **每一個** 缺字型事件都被記錄，而不只是第一個。  
- 若未設定此旗標，Aspose.Words 會悄悄替換字型，你永遠不會知道問題的存在。

## Step 3: Load the Document Using the Configured Options

現在正式開啟檔案。將 `DocumentWithMissingFonts.docx` 替換為你的測試文件路徑。

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

如果檔案中有任何未在機器（或先前設定的資料夾）中找到的字型，`document.WarningInfoCollection` 會被填入相應資訊。

## Step 4: Find and Display Any Font Substitution Warnings

以下是本教學的核心：遍歷 `WarningInfoCollection` 以 **列出缺少的字型**。我們會以 `WarningType.FontSubstitution` 為條件過濾，並印出友善訊息。

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Expected Output

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

若文件僅使用已安裝的字型，則會看到 “✅ No missing fonts detected” 這行訊息。

## Step 5: Advanced – How to **Handle Missing Fonts** Programmatically

單純列印清單或許足以作為診斷工具，但許多正式環境需要自動 **處理缺少字型**。以下提供兩種常見策略：

### 5.1 Substitute with a Known Fallback

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 Embed a Custom Font on the Fly

若你有企業字型檔（`MyBrand.ttf`），可以在偵測到缺少字型時即時嵌入：

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **Note:** 嵌入字型會增加輸出檔案大小，請在保真度與頻寬之間權衡。

## Common Pitfalls and How to Avoid Them

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| 即使文件顯示異常仍未出現警告 | `SubstitutionWarningLevel` 未設為 `All` | 確認第 2 步已如範例設定旗標 |
| 警告列出相同字型多次 | 文件在多個樣式中使用了該字型 | 若只需要唯一清單，可使用 `fontWarnings.Select(w => w.Description).Distinct()` 去除重複 |
| 大型 DOCX 檔案執行時崩潰 | 使用預設記憶體設定載入 | 使用 `LoadOptions.LoadFormat` 或以串流方式載入以降低記憶體壓力 |

## Full Working Example (Copy‑Paste Ready)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

使用 `dotnet run` 執行程式。你應該會在主控台看到缺少字型的清單，證明已成功 **捕捉字型警告**。

## Conclusion

現在你已掌握一套完整、可投入生產環境的模式，能夠 **捕捉字型警告**、**偵測缺少字型**、**處理缺少字型**，以及 **列出缺少字型**，全程使用 Aspose.Words 於 C#。此方法輕量、只需幾行程式碼，且可直接嵌入任何既有的工作流程——無論你

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}