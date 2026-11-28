---
category: general
date: 2026-01-10
description: 學習如何使用 LoadOptions 處理 Aspose.Words 中缺失的字型。逐步程式碼、技巧與最佳實踐，確保文件載入的穩健性。
draft: false
keywords:
- how to use loadoptions
- handle missing fonts
- Aspose.Words warning callback
- font substitution handling
- document loading options
language: zh-hant
og_description: 如何使用 LoadOptions 處理 Aspose.Words 中缺失的字型。獲取完整、可執行的範例，並附有說明與實用技巧。
og_title: 如何在 Aspose.Words 中使用 LoadOptions – 完整指南
tags:
- Aspose.Words
- C#
- .NET
title: 在 Aspose.Words 中使用 LoadOptions – 完整指南
url: /zh-hant/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words 中使用 LoadOptions – 完整指南

有沒有想過 **如何在載入可能缺少字型的 Word 文件時使用 LoadOptions**？你並不是唯一對此感到困惑的人。在許多實務專案中，文件會在不同機器之間傳遞，而目標系統往往沒有作者使用的精確字型。結果會是？意外的字型替換可能破壞版面、隱藏重要字元，或是看起來不符合品牌形象。

幸好，Aspose.Words 提供了一個乾淨的方式來 *處理缺少的字型*，只要使用帶有警告回呼的 `LoadOptions` 物件。本教學將教你 **如何使用 LoadOptions** 來捕捉字型替換警告、記錄它們，並讓你的處理流程更具韌性。

我們將涵蓋：

* 設定警告回呼類別  
* 使用該回呼配置 `LoadOptions`  
* 載入文件並追蹤缺少的字型  
* 疑難排解與擴充解決方案的技巧  

不需要外部文件說明——所有資訊都在此。

---

## 需要的環境

在開始之前，請確保你已具備：

* **Aspose.Words for .NET**（截至 2026 年的最新版本），透過 NuGet 安裝  
* .NET 開發環境（Visual Studio、Rider 或 VS Code）  
* 一個引用了你未安裝字型的範例 DOCX（以下稱為 `input.docx`）  

就這些——不需要額外的函式庫。

---

## 第一步 – 定義警告回呼以捕捉字型替換

第一個步驟是建立一個實作 `IWarningCallback` 的類別。Aspose.Words 會在遇到值得注意的情況（例如缺少字型）時呼叫其 `Warning` 方法。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Custom warning handler that prints font‑substitution messages to the console.
/// </summary>
class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**為什麼這很重要：**  
透過篩選 `WarningType.FontSubstitution`，我們可以避免來自其他警告（例如已棄用功能）的雜訊。回呼讓你完全掌控——你可以寫入檔案、拋出例外，甚至程式化地嵌入備用字型。

---

## 第二步 – 使用回呼設定 LoadOptions

現在有了處理器，我們需要告訴 Aspose.Words 使用它。這就是 **如何在實務中使用 LoadOptions** 的地方。

```csharp
// Create a LoadOptions instance and attach our custom callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCallback()
};
```

**小技巧：** `LoadOptions` 還提供許多其他開關（例如 `Password`、`LoadFormat`、`Encoding`）。你可以將它們串接使用，但在處理缺少字型時，`WarningCallback` 才是關鍵。

---

## 第三步 – 使用已配置的 Options 載入文件

有了 `LoadOptions` 後，載入文件變得相當直接。Aspose.Words 會自動在找不到字型時呼叫回呼。

```csharp
// Path to the DOCX that may reference unavailable fonts.
string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document while the warning callback monitors font issues.
Document doc = new Document(docPath, loadOptions);

// At this point you can continue processing the document—saving, editing, etc.
Console.WriteLine("✅ Document loaded successfully.");
```

**預期輸出：**  

如果 `input.docx` 使用了名為 *“GothicBold”*、但未安裝的字型，你會看到類似以下的訊息：

```
⚠️ Font substitution detected: Font substitution applied. Original font: GothicBold, Substituted font: Arial.
✅ Document loaded successfully.
```

警告行會 **在遇到缺少字型的那一刻** 顯示，讓你即時取得回饋。

---

## 第四步 – （可選）繼續處理文件

通常載入完檔案後，你會想做更多事。以下列出幾個常見的載入後動作，皆能與我們的警告設定無縫配合。

### 4.1 另存為 PDF

```csharp
// Convert to PDF – the substituted fonts are already baked into the layout.
doc.Save("output.pdf", SaveFormat.Pdf);
Console.WriteLine("📄 PDF saved as output.pdf");
```

### 4.2 使用已知的備用字型取代缺少的字型

如果你想指定特定的備用字型（例如 *“Calibri”*），可以在儲存前調整 `FontSettings`：

```csharp
var fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
    "GothicBold", new[] { "Calibri", "Arial" });

doc.FontSettings = fontSettings;
doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
Console.WriteLine("🔄 PDF saved with explicit fallback fonts.");
```

### 4.3 將所有警告寫入檔案

```csharp
class FileLoggingWarningCallback : IWarningCallback
{
    private readonly string _logPath = "load-warnings.log";

    public void Warning(WarningInfo info)
    {
        File.AppendAllText(_logPath,
            $"{DateTime.Now:u} - {info.WarningType}: {info.Description}{Environment.NewLine}");
    }
}

// Use it:
var loadOptionsWithFileLog = new LoadOptions
{
    WarningCallback = new FileLoggingWarningCallback()
};
```

這些程式碼片段說明了 **如何在基本案例之外使用 LoadOptions**，讓你在正式環境中擁有更大彈性。

---

## 常見問題與如何優雅地 **處理缺少字型**

| 常見問題 | 為什麼會發生 | 解決方式 / 緩解措施 |
|----------|--------------|----------------------|
| **未附加回呼** | 忘記設定 `WarningCallback`。 | 載入前務必建立 `LoadOptions` 實例並指派你的處理器。 |
| **回呼只列印，未儲存** | 在 Web 服務中，Console 輸出會消失。 | 用日誌框架（Serilog、NLog）取代 `Console.WriteLine`，或寫入永久儲存。 |
| **多個缺少字型，只報告第一個** | 回呼在第一個警告時拋出例外。 | 保持回呼輕量；除非真的要中止，否則不要拋例外。 |
| **替代字型外觀不符** | 預設替代可能選擇視覺差異大的字型。 | 使用 `FontSettings.SubstitutionSettings.FontSubstitutionRules` 來優先你的備用字型。 |
| **大型文件效能下降** | 警告回呼被呼叫上千次。 | 批次處理：先收集警告至清單，載入完成後再處理，或只篩選唯一字型名稱。 |

了解這些情境，可讓你 **處理缺少字型** 時不會出現意外。

---

## 完整範例 – 整合所有程式碼

以下是可直接執行的完整程式，示範整個流程。複製貼上到 Console 專案，加入 Aspose.Words NuGet 套件，即可立即運作。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions with our warning handler.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCallback()
        };

        // 2️⃣ Path to the source DOCX.
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        // 3️⃣ Load the document – any missing fonts trigger our callback.
        Document doc = new Document(sourcePath, loadOptions);
        Console.WriteLine("✅ Document loaded.");

        // 4️⃣ Optional: Save as PDF to see the final appearance.
        string pdfPath = Path.Combine(Environment.CurrentDirectory, "output.pdf");
        doc.Save(pdfPath, SaveFormat.Pdf);
        Console.WriteLine($"📄 PDF saved to {pdfPath}");

        // 5️⃣ (Bonus) Set explicit fallback font for a known missing font.
        var fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
            "GothicBold", new[] { "Calibri", "Arial" });
        doc.FontSettings = fontSettings;
        doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
        Console.WriteLine("🔄 PDF with explicit fallback saved.");
    }
}
```

**執行此程式** 會：

1. 將任何字型替換警告印到 Console。  
2. 將原始版面另存為 `output.pdf`。  
3. 再產生一個 PDF（`output-with-fallback.pdf`），強制使用 *Calibri* 或 *Arial* 作為備用字型。

---

## 常見問答 (FAQs)

**Q: 這個方法適用於 DOC、RTF 或 HTML 檔嗎？**  
A: 可以。`LoadOptions` 與格式無關，只要傳入正確的檔案路徑，警告回呼會在所有支援格式的缺少字型情況下觸發。

**Q: 可以完全抑制警告嗎？**  
A: 可以指派一個空的回呼（`new IWarningCallback { Warning = _ => {} }`）或將 `LoadOptions.WarningCallback = null`。但失去可見性可能會錯過關鍵的字型問題。

**Q: 若要以嵌入的字型取代缺少的字型，該怎麼做？**  
A: 使用 `FontSettings` 來嵌入替代字型檔案（`AddFontSource`），再結合替代規則即可達成無縫切換。

**Q: 回呼是執行緒安全的嗎？**  
A: 在平行載入大型文件時，回呼可能會被多執行緒同時呼叫。請確保任何共用資源（例如日誌檔）已做好同步處理。

---

## 結論

我們已完整說明 **如何在 Aspose.Words 中使用 LoadOptions** 來 **優雅地處理缺少字型**。透過自訂 `IWarningCallback`、將其掛載至 `LoadOptions`，再以此設定載入文件，你即可即時掌握所有字型替換事件。之後，你可以記錄、替換或嵌入備用字型，確保輸出外觀如預期。

關鍵步驟回顧：

1. 實作聚焦於 `WarningType.FontSubstitution` 的警告回呼。  
2. 把回呼注入 `LoadOptions` 物件。  
3. 使用該 Options 載入文件。  
4. （可選）依需求套用額外的字型規則或日誌機制。

歡迎自行實驗——把 Console 記錄器換成結構化日誌、為關鍵缺少字型加上電子郵件警報，或將此模式整合到更大的文件處理管線。無論是單一檔案或批次上千檔，這個方法都能良好擴展。

祝開發順利，願你的文件永遠以正確的字型呈現！

---

![how to use loadoptions example]

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}