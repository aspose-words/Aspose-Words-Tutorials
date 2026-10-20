---
category: general
date: 2026-02-28
description: 學習如何在 Aspose.Words 中使用 C# 處理字型警告及偵測缺失字型。完整的逐步指南與完整程式碼。
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: zh-hant
og_description: 在 Aspose.Words 中處理字型警告，並使用即時執行的 C# 範例偵測缺失的字型。按照步驟操作，即可看到輸出。
og_title: 處理 Aspose.Words 中的字型警告 – 完整指南
tags:
- Aspose.Words
- C#
- Document Loading
title: 處理 Aspose.Words 的字型警告 – 偵測缺失字型
url: /zh-hant/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 處理 Aspose.Words 中的字型警告 – 偵測缺少的字型

是否曾在載入 Word 文件時需要 **處理字型警告**，卻不明白為什麼某些文字顯示異常？你並不孤單。缺少的字型會觸發替換警告，悄悄破壞視覺版面，如果你不 **偵測缺少的字型**，就永遠不會知道出了什麼問題。

在本教學中，我們將示範如何使用 Aspose.Words 的 `IWarningCallback` 以實務方式 **處理字型警告**。完成本指南後，你將能夠捕捉每一次字型替換事件、將其記錄，甚至決定是否中止載入。無需外部文件，只需一個可直接複製貼上的範例。

## 你將學會

- 設定自訂警告處理程式，只回應字型替換警示。  
- 將處理程式附加至 `LoadOptions`，讓每次文件載入都經過它。  
- 在主控台驗證輸出，並了解每個警告的含義。  

**先決條件**

- .NET 6.0 或更新版本（此程式碼亦相容 .NET Framework 4.6 以上）。  
- 透過 NuGet 安裝 Aspose.Words for .NET（`Install-Package Aspose.Words`）。  
- 一個引用了未在本機安裝之字型的 Word 檔（例如自訂企業字型）。  

如果缺少上述任何項目，請立即取得——否則，讓我們直接開始吧。

## 如何在 Aspose.Words 中處理字型警告

以下是完整且可執行的程式範例。它包含了從 `using` 陳述式到 `Main` 方法的全部內容，你只需將它放入主控台應用程式並按 **F5** 即可執行。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **預期的主控台輸出**（假設文件使用了你未安裝的字型）:
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

如果文件中 **沒有缺少的字型**，警告行將不會出現——因此你只在需要時才有效地 **偵測缺少的字型**。

### 為什麼這樣可行

Aspose.Words 會在解析檔案時對每個非關鍵問題拋出 `WarningInfo`。透過實作 `IWarningCallback`，你即可取得此流程的掛鉤。`WarningType.FontSubstitution` 標誌會精確告知何時庫必須以備用字型取代請求的字型。這是處理字型警告最可靠的方式，因為它在 *載入期間* 執行，甚至在你接觸文件物件模型之前。

## 在不破壞應用程式的情況下偵測缺少的字型

有時你可能想將缺少的字型視為致命錯誤——或許你的品牌指南禁止任何替換。你可以修改處理程式，使其拋出例外而非僅記錄：

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

現在，圍繞 `new Document(...)` 的 `try…catch` 區塊會捕捉此問題，讓你決定是中止、使用備援，或提示使用者。

## 加分項：在 UI 應用程式中視覺化警告

如果你正在開發 WinForms 或 WPF 應用程式，請將 `Console.WriteLine` 換成 UI 友善的呼叫：

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

如此一來，最終使用者即可立即看到警告，且你仍能在所有平台上一致地 **處理字型警告**。

## 常見陷阱與專業提示

- **陷阱：** 忘記設定 `WarningCallback`。預設行為是忽略字型警告，因此你永遠不會看到它們。  
  **專業提示：** 即使只需要警告處理程式，也請始終建立 `LoadOptions` 實例。這成本低且明確。  

- **陷阱：** 在非 Windows 作業系統上使用錯誤的路徑分隔符。  
  **專業提示：** 使用 `Path.Combine` 或原始字串（`@"C:\Docs\MissingFont.docx"` 在 Windows 可用；在 Linux 使用 `"/home/user/docs/MissingFont.docx"`）。  

- **陷阱：** 假設嵌入式字型也會觸發警告。  
  **專業提示：** 嵌入式字型被視為已存在，故不會出現替換警告。請使用真正 *缺少* 的字型來測試處理程式的運作。  

- **陷阱：** 過度記錄所有警告類型。  
  **專業提示：** 如範例所示，以 `WarningType.FontSubstitution` 進行過濾——這樣可保持主控台整潔，並聚焦於 **偵測缺少的字型** 情境。  

## 完整範例回顧

以下再次提供完整程式碼，這次移除註解，適合想要乾淨檢視的讀者：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

複製、貼上、執行——你的主控台現在會自動 **處理字型警告** 並 **偵測缺少的字型**。

## 往後步驟

- **記錄至檔案：** 將 `Console.WriteLine` 換成記錄器（例如 NLog），以達到正式環境的追蹤需求。  
- **批次處理：** 迭代文件資料夾，將所有字型替換事件收集至 CSV 報表。  
- **自動安裝字型：** 在警告處理程式中掛鉤，於載入繼續前從企業字型庫下載缺少的字型。  

上述每項延伸功能皆建立在以乾淨、可重用方式 **處理字型警告** 的核心概念上。

---

*祝編程愉快！若在嘗試 **偵測缺少的字型** 時遇到任何問題，歡迎在下方留言。我很樂意協助你排除故障。*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}