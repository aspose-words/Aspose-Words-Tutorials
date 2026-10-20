---
category: general
date: 2026-04-04
description: 使用 Aspose.Words 於 C# 復原損毀的 Word 檔案。學習如何顯示復原模式並有效處理檔案錯誤。
draft: false
keywords:
- recover corrupted word file
- display recovery mode
language: zh-hant
og_description: 使用 Aspose.Words 復原損壞的 Word 檔案並顯示復原模式。為 C# 開發者提供完整的逐步指南。
og_title: 恢復損毀的 Word 檔案 – 在 C# 中顯示復原模式
tags:
- Aspose.Words
- C#
- Document Recovery
title: 修復損壞的 Word 檔案並在 C# 中顯示復原模式
url: /zh-hant/net/programming-with-loadoptions/recover-corrupted-word-file-and-display-recovery-mode-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 復原損毀的 Word 檔案 – 完整指南：在 C# 中顯示復原模式

有沒有遇過在檔案總管裡看起來正常的 Word 文件，卻在程式碼中載入時拋出錯誤？這就是典型的 *recover corrupted word file* 情境。在本教學中，我們將示範如何 **復原損毀的 Word 檔案**，同時使用 Aspose.Words for .NET **顯示所選的復原模式**。

我們會一步步說明所有必備步驟——安裝函式庫、設定 `LoadOptions`、處理邊緣案例，並將復原模式印到主控台。完成後，你將擁有一段可直接放入專案的、可投入生產環境的程式碼片段。

## 你將學會

- 如何設定 Aspose.Words 的 `LoadOptions` 以控制損毀處理方式。  
- 為何在 *recover corrupted word file* 的使用情境下，`RecoveryMode.Strict` 是最安全的預設。  
- **顯示復原模式** 的完整程式碼。  
- 常見陷阱（例如檔案不存在、未支援的損毀類型）以及避免方法。  

**先備條件：** .NET 6+（或 .NET Framework 4.6+）、已授權或評估版的 Aspose.Words，以及對 C# 的基本認識。無需其他相依套件。

---

## 步驟 1：安裝 Aspose.Words for .NET

首先，取得 NuGet 套件。在專案資料夾的終端機執行：

```bash
dotnet add package Aspose.Words
```

> **小技巧：** 若你的舊專案仍使用 `packages.config`，請改在套件管理員主控台執行 `Install-Package Aspose.Words`。

此套件已包含所有必需元件：`Document` 類別、`LoadOptions`，以及 `RecoveryMode` 列舉。

## 步驟 2：設定 LoadOptions 以復原損毀的 Word 檔案

現在告訴 Aspose.Words 在面對損毀檔案時要多積極。`RecoveryMode` 列舉有三個值：

| 值 | 行為 |
|---|------|
| **Strict** | 發生嚴重損毀時中止。 |
| **Relaxed** | 嘗試修復輕微問題。 |
| **NoRecovery** | 不進行任何復原，直接載入。 |

對於大多數正式環境，你會希望使用 **Strict**——它可防止在背後靜默載入受損文件，避免後續錯誤。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Step 2: Define recovery behaviour for a potentially damaged file.
var loadOptions = new LoadOptions
{
    // Abort loading if the corruption is severe (alternatives: Relaxed, NoRecovery).
    RecoveryMode = RecoveryMode.Strict
};
```

> **為什麼重要：** 使用 `Strict` 能讓你 **真的** 知道檔案是否無法挽救，而不是等到文件渲染錯誤時才發現問題。

## 步驟 3：使用已設定的選項載入文件

`loadOptions` 準備好後，就可以嘗試開啟檔案。若檔案完整，流程順利；若已損毀，會拋出例外（稍後會捕捉）。

```csharp
// Step 3: Load the document using the configured recovery options.
string filePath = @"C:\Docs\PotentiallyCorrupt.docx";
Document document = null;

try
{
    document = new Document(filePath, loadOptions);
}
catch (Exception ex)
{
    Console.WriteLine($"⚠️ Failed to load document: {ex.Message}");
    // You might log the error or attempt a fallback strategy here.
}
```

> **邊緣案例：** 若檔案根本不存在，會拋出 `FileNotFoundException`。在呼叫 `new Document` 前務必先驗證路徑。

## 步驟 4：驗證載入成功並 **顯示復原模式**

假設沒有例外拋出，`Document` 物件已就緒。接下來確認載入成功，並印出實際使用的復原模式，以滿足 *display recovery mode* 的需求。

```csharp
// Step 4: Confirm that the document was loaded and show the recovery mode.
if (document != null)
{
    Console.WriteLine($"✅ Document loaded successfully.");
    Console.WriteLine($"RecoveryMode = {loadOptions.RecoveryMode}");
}
else
{
    Console.WriteLine("❌ Document could not be loaded.");
}
```

典型的主控台輸出如下：

```
✅ Document loaded successfully.
RecoveryMode = Strict
```

如果你將 `RecoveryMode` 改為 `Relaxed`，輸出會相應顯示——這對除錯或採用較寬鬆的復原策略很有幫助。

## 步驟 5：可選 – 處理特定的損毀情境

有時你可能想在損毀程度較輕時仍能 **recover corrupted word file**，而不讓整個操作中止。以下是一個快速調整：

```csharp
// Switch to a more forgiving mode if you need to salvage partially damaged docs.
loadOptions.RecoveryMode = RecoveryMode.Relaxed;

try
{
    document = new Document(filePath, loadOptions);
    Console.WriteLine($"Loaded with Relaxed mode. RecoveryMode = {loadOptions.RecoveryMode}");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed even with Relaxed mode: {ex.Message}");
}
```

> **何時使用 Relaxed：** 若你在處理大量上傳且能容忍少量格式錯誤，`Relaxed` 能為你節省時間。只要在最終發布前先驗證文件即可。

## 完整範例

將上述所有步驟整合，以下是一個可直接複製貼上的完整程式，示範如何 **recover corrupted word file** 並 **display recovery mode**：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // 1️⃣ Define recovery behaviour.
        var loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.Strict // Change to Relaxed if needed.
        };

        // 2️⃣ Path to the possibly damaged document.
        string filePath = @"C:\Docs\PotentiallyCorrupt.docx";

        // 3️⃣ Attempt to load the document.
        Document document = null;
        try
        {
            document = new Document(filePath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"⚠️ Error loading document: {ex.Message}");
            // Early exit if loading fails.
            return;
        }

        // 4️⃣ Verify and **display recovery mode**.
        if (document != null)
        {
            Console.WriteLine($"✅ Document loaded with RecoveryMode = {loadOptions.RecoveryMode}");
        }
        else
        {
            Console.WriteLine("❌ Document could not be loaded.");
        }

        // 5️⃣ (Optional) Do something with the document, e.g., save as PDF.
        // document.Save("Recovered.pdf");
    }
}
```

執行程式後，你會看到檔案是否通過嚴格檢查，以及實際套用的模式。

---

## 常見問題與小技巧

- **如果檔案被加密怎麼辦？**  
  Aspose.Words 能開啟受密碼保護的文件，只要在 `LoadOptions.Password` 中提供密碼即可。復原模式仍會在解密後套用。

- **我可以記錄詳細的損毀資訊嗎？**  
  設定 `loadOptions.LoadFormat = LoadFormat.Docx` 並啟用 `Document.CompatibilityOptions`，即可取得更細緻的診斷資訊。

- **`Strict` 是預設值嗎？**  
  不是——若未指定 `RecoveryMode`，Aspose.Words 會預設為 `Relaxed`。明確設定 `Strict` 才是 *recover corrupted word file* 時最安全的做法。

- **效能影響大嗎？**  
  復原過程會帶來少量開銷（一般 1 MB DOCX 約 < 5 ms）。若處理大量批次工作，可考慮平行化載入。

---

## 結論

現在你已掌握如何使用 Aspose.Words **復原損毀的 Word 檔案**、設定適當的 `RecoveryMode`，以及 **顯示復原模式** 以驗證策略。此方法讓你能完整掌控錯誤處理，確保應用程式要麼取得乾淨的文件，要麼立即失敗並給予明確訊息。

接下來可以嘗試將 `RecoveryMode.Strict` 換成 `Relaxed`，觀察函式庫如何修復輕微問題。也可以把復原後的文件另存為其他格式（PDF、HTML），確認內容是否成功保留。

祝開發順利！若在處理損毀檔案時遇到任何問題，或有妙招想分享，歡迎留下評論。

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}