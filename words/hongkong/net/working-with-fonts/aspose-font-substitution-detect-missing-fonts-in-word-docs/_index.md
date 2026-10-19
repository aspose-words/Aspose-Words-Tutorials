---
category: general
date: 2026-05-04
description: 學習如何使用 Aspose 字型替換，在載入 Word 文件時偵測缺失的字型並取得缺失字型的詳細資訊——一步一步指南。
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: zh-hant
og_description: 精通 Aspose 字型置換，於載入 Word 文件時偵測缺失字型，並以完整的 C# 程式碼取得缺失字型資訊。
og_title: Aspose 字體替換 – 偵測 Word 文件中缺失的字體
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose 字體替換：偵測 Word 文件中缺失的字體
url: /zh-hant/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose 字體替換 – 偵測 Word 文件中缺失的字體

有沒有想過為什麼同一個 Word 文件在不同的機器上顯示錯誤？通常是因為缺少字體，而 **Aspose font substitution** 是讓您在問題變成視覺災難之前發現這些缺口的工具。在本教學中，我們將示範如何在 **載入 Word 文件** 的同時 **偵測缺失的字體**，以及 **取得缺失字體** 的詳細資訊，以便您進行修復或替換。

我們將涵蓋從設定警告回呼到取得乾淨的缺失字體清單的全部內容。完成後，您將擁有一段可直接執行的 C# 程式碼，精確告訴您哪些字體未被找到，並了解這對文件完整性的影響。

---

## 前置條件 – 開始前您需要的項目

- **Aspose.Words for .NET** (建議使用 v23.12 或更新版本)。  
- .NET 開發環境 (Visual Studio、Rider，或 `dotnet` CLI)。  
- 一個刻意使用未安裝字體的範例 DOCX，命名為 `DocumentWithMissingFont.docx`。  
- 基本的 C# 知識——不需要高深技巧，只要能執行主控台應用程式即可。

如果上述任一項目您不熟悉，請先暫停並安裝 NuGet 套件：

```bash
dotnet add package Aspose.Words
```

就這樣。無需額外字體，亦無外部服務。

---

## 步驟 1：載入 Word 文件（並觸發字體檢查）

您首先要做的事就是 **載入 Word 文件**。Aspose.Words 會解析檔案，若找不到參考的字體，則會排入 *FontSubstitution* 警告。以下程式碼負責載入文件：

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **為何重要：** 及早載入文件讓 Aspose 有機會掃描所有文字、樣式及嵌入物件的執行。如果系統或自訂字體資料夾中找不到字體，稍後會收到警告。

---

## 步驟 2：附加警告回呼以捕捉替換事件

Aspose.Words 使用回呼機制通知您缺少字體等問題。將 `IWarningCallback` 的實作指派給 `doc.WarningCallback`，即可即時攔截每個警告。

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **專業提示：** 您可以透過組合模式包裝多個回呼（例如記錄、UI 更新），但在本教學中使用單一回呼即可保持簡潔。

---

## 步驟 3：實作字體替換警告回呼

現在我們定義實際執行工作的類別。回呼會收到 `WarningInfo` 物件；我們會篩選 `WarningType.FontSubstitution`，並將說明儲存起來以供之後使用。

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **發生了什麼：** 當 Aspose 發現缺少字體時，會產生類似「Font substitution: 'Comic Sans MS' was not found, using 'Arial' instead.」的警告。我們的回呼會列印該行並儲存。

---

## 步驟 4：處理文件（可選）並收集缺失字體

如果您只需要 **偵測缺失字體**，載入步驟已足夠——警告會自動觸發。然而，許多開發者在執行某些操作（例如儲存、轉換）後仍需 **取得缺失字體** 資訊。以下我們強制執行一個小操作——儲存為 PDF，以確保所有警告都被發出，然後取得收集的訊息。

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **預期的主控台輸出**（範例）：  
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

請注意，每一行都清楚說明原始字體以及 Aspose 所選擇的備用字體。這就是 **aspose font substitution** 報告的核心。

---

## 步驟 5：進階 – 使用自訂字體來源以減少替換

有時您 *確實* 擁有缺失的字體，只是未放在預設系統資料夾中。Aspose.Words 允許您透過 `FontSettings` 指向自訂目錄。加入此步驟可大幅降低替換警告的數量。

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **為何加入此步驟？** 若您在多台機器間分發文件，將所需字體打包於已知資料夾可確保所有地方的視覺外觀一致。這也使您的 **detect missing fonts** 程序更精確，因為 Aspose 會先檢查該資料夾再使用備用字體。

---

## 完整可執行範例

將上述所有步驟整合起來，以下是一個可直接複製貼上的主控台程式。將其儲存為 `Program.cs`，並使用 `dotnet run` 執行。

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**您應該看到的結果：** 若來源 DOCX 參考了您未安裝的字體，主控台會列印每個替換行並附上簡潔摘要。若所有字體皆存在，則會顯示 “No missing fonts were detected.” 訊息。

---

## 常見陷阱與避免方法

| 問題 | 為何會發生 | 解決方式 |
|------|------------|----------|
| **未出現警告** | 文件僅使用系統字體，或您已加入包含缺失字體的自訂資料夾。 | 確認 DOCX 確實參考了不可用的字體。您可以在 Word 中將段落改為罕見字體（例如 “Papyrus”）。 |
| **重複訊息** | 相同字體在多個文字段落中使用，導致多次警告。 | 若只需要唯一集合，可使用 `Distinct()` 去除重複。 |
| **大型文件效能下降** | 每個警告皆在 UI 執行緒上處理。 | 將載入工作放在背景任務中執行，或在後處理時使用 `Parallel.ForEach`。 |
| **備用字體不正確** | Aspose 的預設備用字體可能與您的品牌不符。 | 將 `FontSettings.SubstitutionSettings.DefaultFontName` 設為首選備用字體（例如 “Calibri”）。 |

---

## 延伸解決方案 – 匯出缺失字體為 JSON

如果您正在構建需要向客戶端回報缺失字體的 Web 服務，將清單序列化相當簡單：

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

現在您的 API 可以回傳乾淨的 JSON 資料，供其他系統使用。

---

## 結論

在本指南中，我們從頭到尾示範了 **Aspose font substitution**：載入 Word 文件、附加警告回呼、捕捉每個 *detect missing fonts* 事件，最後 **retrieve missing font** 資訊以供報告或修復。透過加入可選的自訂字體資料夾，您可以縮減替換清單，且只需少量程式碼即可將結果匯出為 JSON。

請記住，文件的視覺完整性取決於所使用的字體。使用此技巧後，您再也不會因意外的備用字體而感到驚訝。  
準備好邁出下一步了嗎？試著將此邏輯整合到更大的文件處理管線，或探索 Aspose.Words 的其他功能，例如字體嵌入（`doc.FontSettings.EmbeddedFonts`）。可能性無窮，您的使用者也會感謝您提供的精緻輸出。

---

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}