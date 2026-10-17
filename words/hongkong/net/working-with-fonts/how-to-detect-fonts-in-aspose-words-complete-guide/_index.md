---
category: general
date: 2026-04-07
description: 學習如何偵測字型，以及在使用 Aspose.Words 於 C# 處理缺失字型時如何捕捉警告。內含逐步程式碼示例。
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: zh-hant
og_description: 如何在 Aspose.Words 中偵測字型？跟隨本教學，即可輕鬆捕捉警示並處理缺少的字型。
og_title: 如何在 Aspose.Words 中偵測字體 – 完整指南
tags:
- Aspose.Words
- C#
- Font handling
title: 如何在 Aspose.Words 中偵測字型 – 完整指南
url: /zh-hant/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words 中偵測字型 – 完整指南

有沒有想過 **如何偵測** 在將 Word 文件上線前缺少的字型？你並不孤單。在許多企業情境下，偶爾遺失的字型會導致 PDF 轉換流程失敗，或產生不專業的版面錯位。好消息是 Aspose.Words 提供內建機制，讓你找出那些缺失的字型並顯示明確警告。

在本教學中，我們將逐步說明 **如何偵測字型**、**如何捕捉警告**，以及 **處理缺失字型** 的最佳實踐，讓你的應用程式保持穩定。無需外部工具、無需猜測——只要純 C# 程式碼，現在即可直接放入專案使用。

> **快速預覽：** 完成後，你將擁有可重複使用的 `FontSubstitutionWarningCollector`，在文件載入期間收集所有字型替換訊息，並了解當找不到字型時該如何回應。

---

## 你將學會

- 如何設定 `LoadOptions` 以監聽字型替換警告。  
- 如何在自訂收集器類別中捕捉這些警告。  
- 如何處理收集到的警告，決定是中止、記錄或替換字型。  
- 針對引用遠端或內嵌字型的文件的特殊情況處理。  

**先備條件：** .NET 6+（或 .NET Framework 4.6+）、Aspose.Words for .NET（最新版本），以及對 C# 的基本了解。若你從未使用過 Aspose.Words，也不必擔心——本指南只需要幾分鐘的設定時間。

---

## 使用 Aspose.Words LoadOptions 偵測字型

偵測缺失字型的第一步是告訴 Aspose.Words 要回報它們。這透過 `LoadOptions.WarningCallback` 屬性完成，該屬性接受任何實作 `IWarningCallback` 的類別。以下我們建立一個小型收集器，將每個警告儲存起來以供稍後檢查。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**為什麼這很重要：** 若未設定警告回呼，Aspose.Words 會悄悄以預設字型替代缺失的字型，你根本不會知道問題的存在。透過捕捉 `WarningType.FontSubstitution`，即可完整掌握 **偵測字型** 所需的所有資訊。

接下來，我們把收集器掛到 `LoadOptions`，並載入文件：

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **專業提示：** 若一次處理大量文件，請重複使用同一個 `FontSubstitutionWarningCollector` 實例，但務必在每次載入後呼叫 `Clear()`，避免不同檔案的警告混在一起。

---

## 在文件載入期間捕捉警告

文件載入完成後，收集器已經保存了所有與字型相關的警告。接下來的問題是：*如何以易於記錄或顯示的方式捕捉這些警告？*

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

典型輸出範例如下：

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**這告訴了你什麼：** 每一行都會顯示原始字型名稱以及 Aspose.Words 所選擇的備援字型。掌握這些資訊後，你可以判斷備援字型是否可接受，或是需要手動嵌入缺失的字型。

---

## 優雅地處理缺失字型

偵測與捕捉警告只是解決問題的一半。真正的價值在於 **以可投入生產的方式處理缺失字型**。以下列出三種常見策略：

1. **記錄並繼續** – 適用於批次處理，只需要留下稽核紀錄。  
2. **關鍵字型即中止** – 若缺少特定字型（例如品牌專屬字型），拋出例外終止流程。  
3. **即時嵌入缺失字型** – 從已知資料夾載入缺失字型，並在重新載入文件前向 Aspose.Words 註冊。

### 範例：關鍵字型即中止

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### 範例：自動嵌入缺失字型

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**為什麼這些模式有幫助：** 明確決定缺失字型時的處理方式，可避免靜默的替代行為，從而保護品牌形象與可讀性。這正是 **以受控方式處理缺失字型** 的核心。

---

## 完整可執行範例

將上述所有步驟整合，以下是一個可直接執行的程式，示範 **如何偵測字型**、**如何捕捉警告**，以及以記錄方式 **處理缺失字型** 的簡易政策。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**預期結果：** 當程式對一個引用了本機未安裝字型的文件執行時，主控台會列出每個替換警告。若任一警告涉及 `critical` 集合中的字型，程式會提前結束，防止產生有缺陷的 PDF。

---

## 常見問題 (FAQs)

| 問題 | 解答 |
|----------|--------|
| *我需要 Aspose.Words 的授權才能使用這段程式碼嗎？* | 需要。有效的 Aspose.Words 授權會移除評估水印，並解鎖全部功能。 |
| *此方法能偵測內嵌字型嗎？* | 內嵌字型已隨檔案一起存在，Aspose.Words 不會拋出替換警告。若需要列舉內嵌字型，可檢查 `Document.FontInfos`。 |
| *如果缺失的字型在 Windows 上是系統字型，但在 Linux 上不存在，會怎樣？* | 在 Linux 上會觸發相同的警告，因為該字型未安裝。請使用「處理缺失字型」策略，將必要的 `.ttf` 檔案隨應用程式一起部署。 |
| *Is the warning collector thread |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}