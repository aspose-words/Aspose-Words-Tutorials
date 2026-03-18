---
category: general
date: 2026-03-17
description: 如何在 C# 中使用 Aspose.Words 及警告回呼偵測字型。了解如何使用回呼在載入文件時捕捉缺少字型的替換情況。
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: zh-hant
og_description: 如何在 C# 中使用 Aspose.Words 檢測字型。本指南說明如何使用回呼在載入文件時捕獲缺少字型的警告。
og_title: 如何在 C# 中偵測字型 – 使用回呼函式與 Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: 如何在 C# 中偵測字型 – 使用 Aspose.Words 的回呼
url: /zh-hant/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中偵測字型 – 使用 Aspose.Words 的回呼

是否曾經需要以程式方式 **偵測字型** 在 Word 文件中，卻又疑惑為何轉換後某些字元顯示異常？你並不孤單。在許多實務專案——發票產生器、報表匯出工具或批次處理流程中——缺少字型會導致靜默的版面錯誤，且難以除錯。  

好消息是？Aspose.Words 提供了一個簡潔的方式，透過警告回呼將這些問題顯示出來。在本教學中，你將看到 **如何使用回呼** 來捕捉 Aspose 在載入文件時執行的每一次字型替換，並取得一個可直接執行的範例，列印缺少字型的清晰報告。

我們將涵蓋：

* 最小前置條件（.NET 專案與 Aspose.Words NuGet 套件）。  
* 如何實作 `IWarningCallback` 以監聽 `WarningType.FontSubstitution`。  
* 如何將回呼插入 `LoadOptions` 並載入文件。  
* 輸出結果的樣子，以及一些實務上對於正式環境的建議。

完成後，你將能自動 **偵測字型** 在任何 DOCX、DOC 或 RTF 檔案中，並根據缺少的字型資訊採取行動——無論是記錄、提醒使用者，或是替換為備用字型。

---

![使用 Aspose.Words 警告回呼偵測 Word 文件字型的方法](https://example.com/images/detect-fonts.png "如何偵測 Word 文件中的字型")

## 需求環境

* **.NET 6.0** 或更新版本（此範例亦可在 .NET Framework 4.6+ 編譯）。  
* **Aspose.Words for .NET** – 透過 NuGet 安裝：`Install-Package Aspose.Words`。  
* 一個刻意引用未安裝字型的範例 Word 檔（例如 `MissingFont.docx`）。  

不需要其他函式庫；所有功能皆位於 Aspose 命名空間內。

---

## 使用警告回呼偵測字型

### 步驟 1：建立警告回呼類別

此回呼實作 `IWarningCallback`。當 Aspose.Words 遇到找不到的字型時，會拋出帶有 `WarningType.FontSubstitution` 的 `WarningInfo`。我們的類別僅將友善訊息寫入主控台。

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**為何重要：** 只過濾 `WarningType.FontSubstitution` 可避免雜訊警告（例如已棄用的功能），讓日誌專注於你要解決的核心問題——**偵測機器上不存在的字型**。

### 步驟 2：將回呼接入 `LoadOptions`

`LoadOptions` 允許自訂文件的解析方式。將我們的 `FontWarningCollector` 指派給 `WarningCallback` 屬性，即可讓 Aspose 在遇到缺少字型時呼叫它。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**提示：** 也可以在此設定 `LoadOptions.FontSettings`，以程式方式提供備用字型。這是稍後會提到的進階情境。

### 步驟 3：載入文件並觀察輸出

現在正式載入檔案。Aspose 解析文件時，只要遇到找不到的字型，就會觸發我們的回呼。

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**預期的主控台輸出**（假設文件引用了未安裝的 *Comic Sans MS*）：

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

若文件包含多個缺少的字型，將會為每個字型輸出一行——正是你所需要的 **偵測字型** 資訊。

---

## 在更複雜情境下使用回呼

### 將日誌寫入檔案而非主控台

在正式環境中，你可能需要永久保存日誌。將 `Console.WriteLine` 換成 `StreamWriter`：

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### 收集警告以供後續分析

有時你需要在文件載入後取得缺少字型的清單，以便顯示 UI 對話框。將警告存入 `List<string>` 並公開它：

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### 以程式方式提供備用字型

若你有企業字型需要強制使用，可在載入前將其加入 `FontSettings`：

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

現在 Aspose 會以 *Arial Unicode MS* 替代缺少的字型，同時透過回呼回報替換情況。這是一種巧妙的 **使用回呼** 方式，既能偵測又能自動修正。

---

## 常見陷阱與專業提示

| 陷阱 | 發生原因 | 避免方式 |
|--------|----------------|--------------|
| **忘記引用 `Aspose.Words.Warnings`** | `IWarningCallback` 介面位於該命名空間。 | 在檔案頂部加入 `using Aspose.Words.Warnings;`。 |
| **未使用 `LoadOptions` 載入文件** | 預設載入器會靜默替換字型且不發出通知。 | 務必建立 `LoadOptions` 實例並指派你的回呼。 |
| **在權限受限的伺服器上執行** | 寫入日誌檔案可能拋出 `UnauthorizedAccessException`。 | 使用可寫入的資料夾（例如應用程式的資料目錄），或改用記憶體集合。 |
| **多執行緒共用同一個 collector** | `FontWarningCollector` 預設不是執行緒安全的。 | 為每個執行緒建立獨立的 collector，或使用鎖定保護列表。 |
| **假設回呼會對嵌入字型觸發** | 嵌入字型已隨文件一起存在，故不會產生警告。 | 若需驗證嵌入字型完整性，可透過 `FontSettings` 檢查 `FontInfo`。 |

---

## 完整可執行範例（直接複製貼上）

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**預期結果**（假設檔案引用了兩個缺少的字型）：

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

若檔案僅使用已安裝的字型，主控台只會印出：

```
Document loaded successfully.

No missing fonts detected.
```

---

## 小結

我們已說明如何透過將自訂警告回呼接入 Aspose.Words，**偵測 Word 文件中的字型**。此方法輕量且只需要

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}