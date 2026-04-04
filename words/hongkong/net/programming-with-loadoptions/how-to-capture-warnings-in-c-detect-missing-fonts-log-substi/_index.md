---
category: general
date: 2026-04-04
description: 學習如何使用 Aspose.Words 的 LoadOptions 在 C# 中捕捉警告、偵測缺少字型，以及記錄取代事件。
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: zh-hant
og_description: 如何捕獲警告、偵測缺少的字型，以及使用 Aspose.Words LoadOptions 在 C# 中記錄替換事件。
og_title: 如何在 C# 中捕捉警告 – 偵測缺少字型並記錄替代
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: 如何在 C# 中捕捉警告 – 偵測缺失字型並記錄取代
url: /zh-hant/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中捕捉警示 – 偵測缺少字型與記錄取代

有沒有想過 **如何捕捉警示**，當你載入一個缺少字型的 Word 文件時會彈出？你並不孤單。在許多實務專案中，字型在遷移過程中會遺失，而靜默的備用字型會破壞版面。好消息是？Aspose.Words 提供了一個簡潔的方式來監聽這些警示、偵測缺少的字型，甚至記錄每一次的取代，以便之後修正來源。

在本教學中，我們將逐步說明一個完整、可直接執行的解決方案，展示 **如何捕捉警示**、示範 **偵測缺少字型**，並說明 **如何記錄取代** 事件。完成後，你將擁有可重複使用的警示處理器、完整設定的 `LoadOptions` 物件，以及可供驗證的範例主控台輸出。

> **先決條件：** 需要透過 NuGet 安裝 Aspose.Words for .NET（v24.x 或更新版本），並具備基本的 C# 開發環境（如 Visual Studio 2022 或 VS Code 均可）。

---

## 載入文件時如何捕捉警示

此解決方案的核心是一個實作 `IWarningCallback` 介面的類別。Aspose.Words 會在文件載入過程中自動呼叫此回呼，針對所有產生的警示（包括字型取代警示）進行通知。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **為什麼要這麼做？**  
> 透過篩選 `WarningType.FontSubstitution`，我們可以避免與問題無關的警示（例如已棄用的功能）雜訊，使日誌僅聚焦於你關心的問題——缺少字型。

---

## 使用 Aspose.Words 偵測缺少字型

當文件引用的字型在機器上未安裝時，Aspose.Words 會以最相近的字型取代並拋出警示。我們上面的處理器會捕捉每一次發生，從而有效 **偵測缺少字型**。

要實際觀察其運作，我們需要設定 `LoadOptions` 並掛接此處理器：

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **小提示：** 若你想將警示收集起來以供之後處理（例如寫入檔案），可將 `Console.WriteLine` 改為將訊息加入 `List<string>` 的程式碼。

---

## 如何記錄取代事件

記錄只需要將警示輸出導向永久儲存即可。以下是一個簡易範例，將每筆取代警示寫入名為 `font-warnings.log` 的文字檔。

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **為什麼要寫入檔案？**  
> 永久性的日誌讓你能在多次執行間審核字型問題、自動化警示，或將資料匯入建置流程檢查。

---

## 完整可執行範例

將所有部件整合起來，以下是一個可直接複製、貼上並執行的獨立主控台應用程式。它同時示範 **如何捕捉警示**、**偵測缺少字型**，以及 **如何記錄取代**。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### 預期的主控台輸出

如果 `input.docx` 引用的字型未安裝，你會看到類似以下的訊息：

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

若改用 `FileLoggingWarningHandler`，相同的行將會連同時間戳記寫入 `font-warnings.log` 中。

![how to capture warnings console output](image-placeholder.png)

---

## 常見問題與邊緣情況

### 如果我需要捕捉 *所有* 警示，而不僅是字型取代該怎麼辦？

只要移除 `if (info.Type == WarningType.FontSubstitution)` 的判斷即可。回呼會收到所有警示類型（`WarningType.DegradedDocument`、`WarningType.UnexpectedContent` 等），之後可依 `info.Type` 分支，針對不同情況進行處理。

### 這只適用於 PDF 還是僅限 Word 文件？

`LoadOptions` 與 `IWarningCallback` 為 Aspose.Words 的組件，適用於 Word 相容格式（`.docx`、`.doc`、`.rtf`、`.html`）。若處理 PDF，則需使用 Aspose.PDF 自身的警示機制。

### 如何抑制警示而不是記錄它們？

將 `LoadOptions.WarningCallback = null`，或實作回呼但將方法本體留空。函式庫仍會在背後靜默完成字型取代。

### 執行緒安全性如何？

回呼實例會在載入文件的同一執行緒上被呼叫，因此除非在平行載入時共用同一處理器，否則不需額外同步。若有此需求，請使用鎖定機制或並行集合來保護共享資源（例如日誌檔）。

---

## 結論

我們已說明了如何從 Aspose.Words **捕捉警示**、展示了 **偵測缺少字型** 的方法，並解釋了 **如何記錄取代** 事件以供日後分析。只要將簡易的 `IWarningCallback` 實作插入 `LoadOptions`，即可完整掌握與字型相關的問題，而不會讓程式碼變得雜亂。

接下來的步驟？可嘗試將記錄器擴充為發送電子郵件、整合 Azure Monitor，或在建置伺服器上自動安裝缺少的字型。你也可以探索其他警示類型——`WarningType.DegradedDocument` 能提醒你哪些功能在轉換過程中遺失。

對字型處理或 Aspose.Words 有其他疑問嗎？歡迎留言或在 Aspose 論壇上開新議題。祝開發順利，願你的文件永遠以正確的字型呈現！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}