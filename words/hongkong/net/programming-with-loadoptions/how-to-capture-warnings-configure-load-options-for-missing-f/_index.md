---
category: general
date: 2026-03-30
description: 如何在載入 DOCX 檔案時捕捉警告 — 學習偵測缺少的字型、設定字型選項，以及在 C# 中設定載入選項。
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- configure font settings
- handle missing fonts
- set load options
language: zh-hant
og_description: 如何在載入 DOCX 檔案時捕捉警告 – 步驟說明，偵測缺少字型並在 C# 中設定字型
og_title: 如何捕捉警告 – 為缺失字型設定載入選項
tags:
- Aspose.Words
- C#
- Font management
title: 如何捕捉警告 – 為缺少字體設定載入選項
url: /zh-hant/net/programming-with-loadoptions/how-to-capture-warnings-configure-load-options-for-missing-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何捕獲警告 – 為缺失字體配置載入選項

有沒有想過 **如何捕獲警告**，當文件嘗試使用你未安裝的字體時會彈出？這種情況常令使用文字處理庫的開發者感到困惑，尤其是當你需要在字體缺失導致 PDF 匯出流程中斷之前 **偵測缺失字體** 時。

在本教學中，我們將示範一個實用、可直接執行的解決方案，**設定字體設定**、**設定載入選項**，並將每個替代警告輸出到主控台。完成後，你將清楚知道如何 **處理缺失字體**，讓應用程式更穩健、使用者更滿意。

## 你將學會

- 如何 **設定載入選項**，讓函式庫回報字體問題，而不是悄悄替換字體。
- 捕獲警告所需的 **字體設定** 步驟。
- 以程式方式 **偵測缺失字體** 並作出相應處理。
- 完整、可直接複製貼上的 C# 範例，適用於最新的 Aspose.Words for .NET（撰寫時為 v24.10）。
- 延伸此解決方案以記錄警告、使用自訂字體作為備援，或在關鍵字體缺失時中止處理的技巧。

> **先決條件：** 必須已安裝 Aspose.Words for .NET NuGet 套件 (`Install-Package Aspose.Words`)。不需要其他外部相依性。

---

## Step 1: 匯入命名空間並準備專案

首先，加入必要的 `using` 指示。這不只是樣板程式碼；它告訴編譯器 `LoadOptions`、`FontSettings` 與 `Document` 所在的位置。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

> **小技巧：** 若使用 .NET 6+，可啟用 *global using* 陳述式，免除在每個檔案中重複這些行。

---

## Step 2: 設定載入選項並啟用字體替代警告

捕獲 **如何捕獲警告** 的核心在於 `LoadOptions` 物件。建立一個全新的 `FontSettings` 實例，並將事件處理器連結至 `SubstitutionWarning`，即可讓函式庫在找不到請求的字體時發出警告。

```csharp
// Step 2: Create LoadOptions and turn on warning notifications
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Subscribe to the warning event – this is where we actually capture them
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // The warning message includes the missing font name and the fallback that was used
    Console.WriteLine($"[Font warning] {e.Message}");
};
```

**為什麼這很重要：** 若未訂閱此事件，Aspose.Words 會悄悄回退至預設字體，你永遠不會知道哪些字形被替換。透過監聽 `SubstitutionWarning`，即可取得完整的稽核紀錄——對於合規要求嚴格的環境尤為關鍵。

---

## Step 3: 使用已設定的選項載入文件

現在警告已經掛上，使用剛剛準備好的 `loadOptions` 載入 DOCX（或任何支援的格式）。`Document` 建構子會立即觸發字體檢查邏輯。

```csharp
// Step 3: Load a document that intentionally references a missing font
string filePath = @"C:\Docs\WithMissingFonts.docx";   // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

若檔案引用了例如 *“Comic Sans MS”*，而機器上只有 *“Arial”*，你會看到類似以下的訊息：

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
```

該行訊息會直接印到主控台，因為我們先前已掛上事件處理器。

---

## Step 4: 驗證並回應捕獲的警告

捕獲警告只是第一步；通常還需要決定後續動作。以下提供一個快速模式，將警告存入清單以便稍後分析——如果你想將它們寫入檔案或在關鍵字體缺失時中止匯入，這樣的做法相當便利。

```csharp
using System.Collections.Generic;

List<string> warningLog = new List<string>();

loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    string msg = $"[Font warning] {e.Message}";
    Console.WriteLine(msg);
    warningLog.Add(msg);
};

// Load the document (same as Step 3)
Document doc = new Document(filePath, loadOptions);

// Example decision: abort if any warning mentions "Times New Roman"
bool hasCriticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
if (hasCriticalMissing)
{
    Console.WriteLine("Critical font missing – aborting processing.");
    // You could throw, return an error code, etc.
}
else
{
    Console.WriteLine("Document loaded successfully with acceptable font fallbacks.");
}
```

**邊緣案例處理：**  
- **多個缺失字體：** 清單會為每一次替代產生一筆條目，方便你遍歷並產生詳細報告。  
- **自訂備援字體：** 若你有自己的字體檔案，可在載入前加入 `FontSettings`：`fontSettings.SetFontsFolder(@"C:\MyFonts", true);`。此時警告會顯示自訂備援字體，而非系統預設。

---

## Step 5: 完整可執行範例（直接複製貼上）

將上述所有步驟整合，以下是一個自包含的主控台應用程式，你現在即可編譯並執行。

```csharp
// Full example – how to capture warnings while loading a DOCX file
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare load options and enable warning events
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        List<string> warningLog = new List<string>();
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            string msg = $"[Font warning] {e.Message}";
            Console.WriteLine(msg);
            warningLog.Add(msg);
        };

        // 2️⃣ (Optional) Point to a folder with custom fonts if you have any
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

        // 3️⃣ Load the document – this triggers the warning capture
        string filePath = @"C:\Docs\WithMissingFonts.docx"; // change as needed
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ React to the captured warnings
        bool criticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
        if (criticalMissing)
        {
            Console.WriteLine("Critical font missing – aborting further processing.");
            // exit or throw as appropriate
            return;
        }

        Console.WriteLine("Document loaded – all fonts accounted for (or safely substituted).");
        // Continue with your processing (e.g., save as PDF, manipulate, etc.)
    }
}
```

**預期的主控台輸出**（當 DOCX 引用缺失字體時）：

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
Document loaded – all fonts accounted for (or safely substituted).
```

若缺少如 “Times New Roman” 這類 *關鍵* 字體，則會看到中止訊息。

---

## 常見問題與注意事項

| 問題 | 答案 |
|----------|--------|
| **是否必須呼叫 `SetFontsFolder` 才能捕獲警告？** | 不需要。警告事件在使用系統預設字體時亦會觸發。只有在想提供額外備援字體時才使用 `SetFontsFolder`。 |
| **此方式能在 .NET Core / .NET 5+ 上運作嗎？** | 完全可以。Aspose.Words 24.10 支援所有現代 .NET 執行環境。只要 NuGet 套件與目標框架相符即可。 |
| **如果想把警告寫入檔案而不是主控台，該怎麼做？** | 將 `Console.WriteLine(msg);` 替換為任意日誌呼叫，例如 `File.AppendAllText("font_warnings.log", msg + Environment.NewLine);`。 |
| **能否對特定字體抑制警告？** | 可以。在事件處理器內過濾：`if (e.FontName == "SomeFont") return;`，即可對個別字體實現細緻控制。 |
| **有沒有辦法把缺失字體視為錯誤？** | 在處理器內手動拋出例外，或在 `Document` 建構後根據旗標中止，如範例所示。 |

---

## 結論

現在你已掌握一套穩健、可投入生產環境的 **如何捕獲警告** 模式，能在載入含缺失字體的文件時即時偵測。透過 **偵測缺失字體**、**設定字體設定** 與 **設定載入選項**，你可以完整掌握字體替代事件，並自行決定是記錄、備援或中止處理。

接下來可將此邏輯整合至 PDF 轉換流程、加入自訂備援字體，或將警告清單送入監控系統。此方法可從小型工具擴展至企業級文件處理服務。

---

### 延伸閱讀與後續步驟

- **深入探索 FontSettings 功能** – 嵌入自訂字體、控制備援順序與授權注意事項。  
- **結合 PDF 轉換** – 捕獲警告後，呼叫 `doc.Save("output.pdf");`，並驗證 PDF 使用的字體是否如預期。  
- **自動化測試** – 撰寫單元測試載入已知缺失字體的文件，並斷言警告清單包含預期訊息。  

如果在實作過程中遇到問題或有改進想法，歡迎留言討論。祝開發順利！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}