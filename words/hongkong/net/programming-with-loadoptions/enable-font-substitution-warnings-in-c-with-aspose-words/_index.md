---
category: general
date: 2026-06-20
description: 使用 Aspose.Words 在 C# 中啟用字型替代警告。學習如何設定 LoadOptions、捕捉警告，並有效處理缺少的字型。
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: zh-hant
og_description: 在 C# 中使用 Aspose.Words 啟用字型置換警告。本指南說明如何設定 LoadOptions、讀取 WarningInfo，並顯示缺少字型的訊息。
og_title: 在 C# 中啟用字型替代警告 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: 在 C# 中使用 Aspose.Words 啟用字型置換警告
url: /zh-hant/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中使用 Aspose.Words 啟用字型替代警告

有沒有想過在 Word 文件引用了伺服器上未安裝的字型時，**如何啟用字型替代警告**？你並不是唯一有此疑問的人。缺少字型會在產生 PDF 或影像時悄悄破壞版面，而捕捉這類問題的唯一方法，就是監聽 Aspose.Words 所拋出的警告。

在本教學中，我們將透過實作範例一步步示範如何開啟這些警告、從 `WarningInfo` 集合中取出資訊，並將有意義的訊息印出到主控台。完成後，你將了解如何設定 **Aspose.Words LoadOptions**、處理 **C# 字型替代警告**，讓文件處理流程更加可靠。

我們也會簡要說明幾個邊緣情況——例如壓制警告或改為記錄而非直接印出——並提供一段可直接複製貼上的完整程式碼範例，適用於最新的 Aspose.Words for .NET（截至 24.10 版）。

## 需要的環境

- .NET 6.0 或更新版本（程式碼同樣支援 .NET Framework 4.7+）
- 以 NuGet 方式加入 `Aspose.Words`（使用 `dotnet add package Aspose.Words` 安裝）
- 一個引用了 **未**安裝字型的 Word 檔（例如 `DocumentWithMissingFont.docx`）
- 任一主流 IDE（Visual Studio、Rider 或 VS Code）

就這些——不需要額外服務或專有工具。準備好了嗎？讓我們開始吧。

## 步驟 1：啟用字型替代警告

首先必須告訴 Aspose.Words，在替代缺少的字型時要發出通知。這透過 `LoadOptions` 物件的 `FontSettings` 屬性完成。預設情況下，警告是 **關閉** 的，以保持 API 靜默，我們需要自行打開它。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **為什麼會這樣運作：** 當 `FontSettings` 不為 `null` 時，函式庫會自動在載入文件的過程中，將所有 `WarningType.FontSubstitution` 事件填入 `Document.WarningInfo`。可以把它想成為字型的「除錯模式」。

## 步驟 2：使用已設定的選項載入文件

警告集合已啟動後，使用剛才建立的 `LoadOptions` 來載入文件。如果文件中有缺少的字型，Aspose.Words 會使用備援字型並將警告寫入 `WarningInfo` 清單。

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **小技巧：** 若在迴圈中處理大量檔案，請重複使用同一個 `LoadOptions` 實例——只建立一次即可為每次迭代節省數毫秒的時間。

## 步驟 3：遍歷 WarningInfo 並顯示字型替代訊息

文件載入完成後，`WarningInfo` 集合會保存載入期間發生的所有警告。我們只關心 `WarningType.FontSubstitution`，因此需要過濾。

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

執行上述程式碼，若文件引用了缺少的 “Papyrus” 字型，可能會得到類似以下的輸出：

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

這就是你一直在找的 **字型替代訊息**——簡潔、可操作，且可直接寫入日誌或傳送至警示系統。

## 完整可執行範例

以下是一個自包含的 Console 程式，將前述步驟全部整合。直接複製貼上到新的 `.csproj` 後執行 **Run** 即可。

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### 預期輸出

若文件引用了未安裝的字型，會看到類似以下的訊息：

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

若機器上已安裝所有字型，程式則只會印出：

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## 常見問題與進階小技巧

| 問題 | 為何會發生 | 解決方式 / 預防措施 |
|------|------------|-------------------|
| **警告消失** | 你清除了 `FontSettings` 或使用了未設定 `FontSettings` 的 `LoadOptions`。 | 即使不修改屬性，也必須實例化 `FontSettings`。 |
| **警告過多** | 文件使用了大量異國字型。 | 可透過 `FontSettings.SetFontsFolder` 加入自訂字型資料夾，減少替代次數。 |
| **迴圈效能下降** | 每次迭代都重新建立 `LoadOptions`。 | 在所有文件間共用同一個 `LoadOptions` 實例。 |
| **主控台無輸出** | 在 GUI 應用程式中 `Console.WriteLine` 被忽略。 | 將警告導向日誌 (`ILogger`) 或寫入檔案。 |

### 在實際服務中處理警告

在 Web API 中通常不會直接寫到主控台。可以改為把警告寫入結構化日誌：

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

如此一來，即可保留 **文件警告處理** 的同時，保持服務的整潔。

## 延伸範例

- **捕捉其他警告類型**（例如 `WarningType.UnknownFileFormat`）只要移除 `if` 篩選即可。
- **將所有警告匯出為 JSON**，供後續分析使用。
- **強制使用特定備援字型**，只要設定 `FontSettings.SubstitutionSettings.DefaultFontName`。

掌握了 **啟用字型替代警告** 後，以上這些延伸功能都能輕鬆實作。

## 結論

我們示範了如何在 C# 中使用 Aspose.Words **啟用字型替代警告**，從設定 `LoadOptions`、遍歷 `WarningInfo` 到印出友善訊息。依照上述步驟，你可以防止因缺少字型而導致的版面靜默變更，讓文件處理管線更加安全。

接下來，試著加入自訂字型資料夾、將警告寫入檔案，或傳送至監控儀表板。相同的模式同樣適用於任何 **文件警告處理** 情境，無論是轉 PDF、渲染影像或執行郵件合併。

對 **C# 字型替代警告** 有任何問題，或想分享巧妙的解法嗎？歡迎在下方留言——祝開發順利！

## 接下來該學什麼？

以下教學與本篇內容緊密相關，能進一步深化你對 API 的運用與不同實作方式的了解。每篇資源皆提供完整可執行的程式碼範例與逐步說明，助你在專案中快速上手。

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}