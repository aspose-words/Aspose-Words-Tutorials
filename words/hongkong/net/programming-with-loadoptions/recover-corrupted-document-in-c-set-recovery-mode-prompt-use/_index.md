---
category: general
date: 2026-01-11
description: 使用 Aspose.Words 在 C# 中修復損壞的文件。了解如何設定復原模式、以復原方式載入 docx，並在發生錯誤時提示使用者，只需簡單幾步。
draft: false
keywords:
- recover corrupted document
- set recovery mode
- load docx with recovery
- prompt user on error
language: zh-hant
og_description: 在 C# 中透過設定復原模式、載入具復原功能的 DOCX，並在發生錯誤時提示使用者，以恢復損毀的文件。完整的逐步教學。
og_title: 在 C# 中恢復損壞的文件 – 快速指南
tags:
- Aspose.Words
- C#
- Document Recovery
title: 在 C# 中復原損毀文件 – 設定復原模式並提示使用者
url: /zh-hant/net/programming-with-loadoptions/recover-corrupted-document-in-c-set-recovery-mode-prompt-use/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中復原損毀文件 – 完整指南

有沒有試過打開一個在 Word 裡看起來正常，但在程式碼中拋出例外的 DOCX？你可能正面對 **recover corrupted document** 的情況。好消息是 Aspose.Words 為你提供了細緻的控制，讓你可以靜默修復、拋出例外，或是詢問使用者該怎麼處理這些檔案。

在本教學中，我們將逐步說明如何 **recover corrupted document** 檔案，從安裝函式庫、選擇正確的 **set recovery mode** 選項、**load docx with recovery**，到最後在發生錯誤時 **prompt user on error**。內容直截了當，提供一個完整且可直接放入任何 .NET 專案的可執行範例。

> **快速預覽：** 完成後，你將擁有一個能載入可能損毀的 `corrupt.docx`、記錄所有警告，並在復原失敗時詢問使用者是否繼續的主控台應用程式。

---

## 你需要的條件

- **.NET 6.0** 或更新版本（此程式碼亦可於 .NET Framework 4.6+ 上執行）。
- **Aspose.Words for .NET** – 透過 NuGet 安裝（`Install-Package Aspose.Words`）。
- 一個 **corrupt DOCX** 測試檔案（可透過十六進位編輯器或更改副檔名刻意損毀檔案）。
- 任意你喜歡的 IDE——Visual Studio、Rider，甚至 VS Code 都可以。

> *小技巧：* 請保留原始檔案的備份。復原過程可能會重新寫入文件的部分內容，避免遺失有效資訊。

## 步驟 1 – 安裝 Aspose.Words 並加入命名空間

首先，從 NuGet 取得函式庫，並在程式碼中引用所需的命名空間。

```csharp
// Install via Package Manager Console:
// Install-Package Aspose.Words

using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

這就是本教學其餘部分所需的全部。`Aspose.Words.Loading` 命名空間包含 `LoadOptions` 類別，這是 **set recovery mode** 的關鍵。

## 步驟 2 – 選擇復原模式（主要 H2 標題含關鍵字）

### 復原損毀文件 – 設定正確的復原模式

Aspose.Words 提供三種復原行為：

| 模式 | 發生情況 | 使用時機 |
|------|----------|----------|
| **PromptUser** | 顯示對話框（或自行實作提示），並嘗試修復檔案。 | 適用於使用者可自行決定的互動工具。 |
| **Silent** | 自動嘗試修復，無使用者介面。 | 適合批次作業或服務。 |
| **ThrowException** | 停止處理並拋出例外。 | 當需要嚴格驗證時使用。 |

以下示範如何將 **set recovery mode** 設為 `PromptUser`。若想使用靜默處理，只需更換列舉值即可。

```csharp
// Step 2: Configure LoadOptions with the desired recovery mode
LoadOptions loadOptions = new LoadOptions
{
    // Choose one of: RecoveryMode.PromptUser, RecoveryMode.Silent, RecoveryMode.ThrowException
    RecoveryMode = RecoveryMode.PromptUser
};
```

> **為什麼這很重要：** 透過明確的 **set recovery mode**，你告訴 Aspose.Words 其修復的積極程度。預設為 `PromptUser`，但明確設定可讓你的意圖清晰可見——對未來維護者以及搜尋引擎解析程式碼皆有幫助。

## 步驟 3 – 使用復原載入 DOCX

現在，我們將使用剛剛設定好的 `LoadOptions` 來 **load docx with recovery**。若檔案受損，Aspose.Words 會根據模式自行修復或發出警告。

```csharp
// Step 3: Load the potentially corrupted DOCX
string filePath = @"C:\Temp\corrupt.docx"; // adjust to your environment
Document document;

try
{
    document = new Document(filePath, loadOptions);
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
    // If you used ThrowException mode, you'll end up here.
    return;
}
```

`Document` 建構子負責主要工作。在 **PromptUser** 模式下，你會看到主控台提示（或若掛接 `LoadOptions` 事件則會出現自訂 UI）詢問是否繼續。於 **Silent** 模式時，方法只會盡力修復並繼續執行。

## 步驟 4 – 檢查警告並提示使用者

Aspose.Words 會將遇到的所有問題記錄在 `Warnings` 集合中。讓我們遍歷這些警告，並給予使用者決定後續動作的機會。

```csharp
// Step 4: Examine any warnings generated during loading
if (document.Warnings.Count > 0)
{
    Console.WriteLine("The following warnings were detected while loading the document:");
    foreach (WarningInfo warning in document.Warnings)
    {
        Console.WriteLine($"- {warning.Source}: {warning.Description}");
    }

    // Simple prompt – you can replace this with a GUI dialog if you prefer
    Console.Write("Do you want to continue processing this document? (y/n): ");
    string response = Console.ReadLine()?.Trim().ToLowerInvariant();

    if (response != "y")
    {
        Console.WriteLine("Operation aborted by the user.");
        return;
    }
}
else
{
    Console.WriteLine("Document loaded without any warnings.");
}
```

上述程式碼以主控台友善的方式 **prompt user on error**。若你在開發 Windows Forms 或 WPF 應用程式，只需將 `Console.ReadLine` 換成 `MessageBox` 或自訂對話框即可。

## 步驟 5 – 使用已復原的文件

此時文件已載入記憶體，並盡可能由 Aspose.Words 修復。你現在可以讀取內容、儲存為乾淨的副本，或執行任何需要的操作。

```csharp
// Example: Save a clean copy next to the original
string cleanPath = System.IO.Path.Combine(
    System.IO.Path.GetDirectoryName(filePath)!,
    "clean_copy.docx");

document.Save(cleanPath);
Console.WriteLine($"Clean copy saved to: {cleanPath}");
```

對損毀檔案執行完整程式時，主控台會輸出類似以下內容：

```
The following warnings were detected while loading the document:
- Document: The file contains an unexpected end tag.
Do you want to continue processing this document? (y/n): y
Clean copy saved to: C:\Temp\clean_copy.docx
```

若檔案本身沒有問題，則會顯示 “Document loaded without any warnings.”，且乾淨的副本會與原始檔案相同。

## 完整範例

以下是一個完整的程式範例，直接複製貼上至新的主控台專案，然後按 **F5** 執行。

```csharp
// RecoverCorruptedDocument.cs
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class RecoverCorruptedDocument
{
    static void Main()
    {
        // 1️⃣ Configure recovery mode
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.PromptUser // alternatives: Silent, ThrowException
        };

        // 2️⃣ Path to the possibly corrupted DOCX
        string filePath = @"C:\Temp\corrupt.docx";

        // 3️⃣ Attempt to load the document
        Document document;
        try
        {
            document = new Document(filePath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Show warnings and ask the user what to do
        if (document.Warnings.Count > 0)
        {
            Console.WriteLine("The following warnings were detected while loading the document:");
            foreach (WarningInfo warning in document.Warnings)
            {
                Console.WriteLine($"- {warning.Source}: {warning.Description}");
            }

            Console.Write("Do you want to continue processing this document? (y/n): ");
            string response = Console.ReadLine()?.Trim().ToLowerInvariant();

            if (response != "y")
            {
                Console.WriteLine("Operation aborted by the user.");
                return;
            }
        }
        else
        {
            Console.WriteLine("Document loaded without any warnings.");
        }

        // 5️⃣ Save a clean copy
        string cleanPath = System.IO.Path.Combine(
            System.IO.Path.GetDirectoryName(filePath)!,
            "clean_copy.docx");

        document.Save(cleanPath);
        Console.WriteLine($"Clean copy saved to: {cleanPath}");
    }
}
```

執行程式、損毀測試檔案，即可觀察復原過程。 🎉

## 邊緣案例與變化

| 情境 | 需要變更的項目 | 原因 |
|------|----------------|------|
| **Batch processing** (no user interaction) | 設定 `RecoveryMode = RecoveryMode.Silent` 並移除主控台提示。 | 讓流程自動持續執行。 |
| **Strict validation** (fail fast) | 使用 `RecoveryMode.ThrowException`。將載入呼叫包在 try/catch 中，並記錄例外。 | 確保絕不使用部分修復的檔案。 |
| **Custom UI** (WinForms/WPF) | 訂閱 `LoadOptions.LoadingProgress` 或使用 `Document.LoadOptions` 事件來顯示對話框。 | 提供比主控台更豐富的使用者體驗。 |
| **Large documents** (memory constraints) | 使用 `LoadOptions.LoadFormat = LoadFormat.Docx` 載入，並考慮使用 `Document.SaveOptions` 以串流方式輸出。 | 防止記憶體不足（OutOfMemory）例外。 |

## 實用技巧（E‑E‑A‑T 觀點）

- **在嘗試復原前務必保留備份**；復原過程可能會覆寫檔案的部分內容。  
- **將警告記錄至檔案** 以供日後分析；警告常指示根本原因（例如缺少部件、XML 損毀）。  
- **測試多種損毀類型**——截斷檔案、破壞 XML 標籤或變更 zip 結構，以觀察各模式的行為。  
- **定期升級 Aspose.Words**；新版會改進復原演算法並加入新警告類型。  
- **結合驗證**——復原後執行 `document.UpdateFields()` 與 `document.Save()`，確保文件完整可用。

## 結論

現在你已掌握在 C# 中透過 **set recovery mode**、**load docx with recovery**，以及在發生問題時 **prompt user on error** 來 **recover corrupted document** 檔案的方法。完整範例展示了一個乾淨、端對端的流程，適用於主控台應用、服務或 UI 專案。

接下來的步驟？可以在 WinForms 應用中將主控台提示換成模式對話框，或在背景工作中嘗試 **Silent** 模式，亦或將復原邏輯整合至 ASP.NET 上傳端點，讓使用者上傳損毀的 DOCX 後即時取得修復版本。

祝程式開發順利，願你的文件永遠完整！  

---

![Recover corrupted document example](/images/recover-corrupted-document.png "recover corrupted document")

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}