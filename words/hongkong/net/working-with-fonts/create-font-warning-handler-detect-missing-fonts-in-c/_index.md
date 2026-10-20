---
category: general
date: 2026-02-12
description: 建立字型警告處理程序，以偵測缺少的字型並追蹤 Aspose.Words 中缺少的字型。了解如何有效記錄警告。
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: zh-hant
og_description: 在 C# 中建立字型警告處理程式，以偵測缺少的字型，並學習在 Aspose.Words 替換字型時如何記錄警告。
og_title: 建立字型警告處理程式 – 偵測缺失字型
tags:
- Aspose.Words
- C#
- Document Processing
title: 建立字型警告處理程式 – 偵測 C# 中缺失的字型
url: /zh-hant/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立字型警告處理程式 – 偵測 C# 中缺少的字型

有沒有曾經需要 **create font warning handler**，因為 Word 文件在未提示的情況下自行替換了你未預期的字型？你並非唯一遇到此問題的人。當 Aspose.Words 載入一個引用了伺服器上不存在的字型的 DOCX 時，它會悄悄回退到預設字型——導致版面微妙地錯亂。

在本教學中，我們將精確示範如何 **detect missing fonts**、**track missing fonts**，以及 **how to log warnings**，讓你能在字型被替換前即時發現。完成後，你將擁有一個可重用的警告處理程式，能將每一次字型替換事件輸出到主控台（或任何你偏好的記錄器）。沒有神祕，只是清晰、可執行的程式碼。

## 前置條件

- .NET 6.0 或更新版本（API 與 .NET Framework 4.6+ 相同）
- 已安裝 Aspose.Words for .NET（`dotnet add package Aspose.Words`）
- 一個引用了未在你的機器上安裝的字型的 Word 檔案（例如 `MissingFont.docx`）

如果你已經具備上述條件，太好了——讓我們直接開始吧。

## 步驟 1：使用 Warning Callback 設定 LoadOptions  

當你想要 **create font warning handler** 時，第一件事就是告訴 Aspose.Words 在遇到問題時觸發回呼。`LoadOptions` 是用來保存此設定的容器。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**為什麼這很重要：**  
`LoadOptions` 是唯一可以插入 `IWarningCallback` 的地方。若未設定，Aspose.Words 仍會在內部記錄警告，但你無法看到。透過指派 `FontWarningHandler`，我們即可完全掌控缺少字型被替換時的處理方式。

## 步驟 2：實作 FontWarningHandler 類別  

現在我們真正撰寫 **create font warning handler** 程式碼。此類別實作 `IWarningCallback`，並在 Aspose.Words 發出每個警告時接收 `WarningInfo` 物件。

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**說明：**  
- `info.Type` 告訴我們警告的類別。我們關注 `WarningType.FontSubstitution`，因為它代表缺少字型。  
- `info.Description` 包含可供人閱讀的訊息，例如 *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”*  
- 透過 `Console.WriteLine` 寫入，我們即時 **log warnings**。在實際應用中，你可能會改用 `ILogger`、檔案寫入器，或遙測服務。

> **專業提示：** 若需收集所有缺少的字型以供日後報告，請將 `info.Description` 儲存於 `List<string>` 中，而不是直接印出。

## 步驟 3：使用已設定的 LoadOptions 載入文件  

有了回呼設定，載入文件時若缺少字型，便會自動觸發我們的處理程式。

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**你會看到的結果：**  
執行程式時會印出類似以下內容：

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

該行訊息證明你已成功 **detect missing fonts**，且現在正即時 **track missing fonts**。

## 步驟 4：驗證處理程式在不同情境下的運作  

很容易以為此處理程式只適用於 DOCX 檔案，但 Aspose.Words 支援多種格式。試著載入引用嵌入字型的 PDF，或較舊的 `.doc` 檔案。只要經過字型解析流程的任何格式，都會觸發相同的回呼。

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

如果 PDF 引用了未安裝的字型，你會得到相同的主控台輸出。這證明你的 **create font warning handler** 解決方案與格式無關。

## 步驟 5：擴充處理程式 – 記錄至檔案  

主控台輸出對示範很方便，但正式環境的程式通常會寫入日誌檔案。以下是一個快速的調整方式。

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

現在每當字型被替換時，訊息會被附加至 `font-warnings.log`。這符合 **how to log warnings** 的需求，並提供持久的稽核紀錄。

## 步驟 6：整合完整範例 – 可執行程式碼  

以下是完整程式碼，你可以直接複製貼上到 Console 應用程式中。沒有遺漏的部份，只需將檔案路徑換成自己的文件即可。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**預期結果：**  

- 主控台會印出每一行替換訊息。  
- `font-warnings.log` 現在包含每個缺少字型事件的時間戳記紀錄。  
- `output.pdf` 檔案會使用已替換的字型產生，確保即使原始字型不存在，轉換仍能成功。

## 常見問題與邊緣情況  

| 問題 | 答案 |
|----------|--------|
| *如果我想忽略特定字型該怎麼辦？* | 在 `Warning` 內，檢查 `info.Description` 中的字型名稱，對於你認為可以接受的字型提前 `return;`。 |
| *處理程式會對嵌入字型觸發嗎？* | 不會——嵌入字型始終對文件可用，因此不會產生替換警告。 |
| *我可以捕捉其他警告類型嗎（例如影像解析度問題）？* | 當然可以。移除 `if (info.Type == WarningType.FontSubstitution)` 的判斷，或為 `WarningType.ImageResolution` 加上額外的 `if` 區塊。 |
| *此處理程式是執行緒安全的嗎？* | 上述預設實作在寫入檔案時未使用同步機制。若在多執行緒情境下，請將檔案寫入包在 lock 中，或使用支援併發的記錄器。 |

## 後續步驟  

既然你已了解 **how to log warnings** 針對缺少的字型，接下來可能想要：

- **Detect missing fonts** 在批次匯入過程中偵測缺少的字型，並產生摘要報告。  
- **Track missing fonts** 跨多個文件追蹤缺少的字型，當特定字型頻繁出現時發送電子郵件警示。  
- **Integrate with a monitoring system**（例如 Azure Application Insights）以隨時間呈現字型替換趨勢。  

所有這些擴充功能皆建立在我們先前建立的 `IWarningCallback` 基礎之上。

---

*祝開發愉快！如果遇到特殊情況——例如自訂字型資料夾或網路共享——歡迎在下方留言。社群（以及我）都很樂意協助你微調字型警告策略。* 

![create font warning handler example](image-placeholder.png "create font warning handler example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}