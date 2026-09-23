---
category: general
date: 2026-02-10
description: 設定警告回呼以監察字型變更，當您在 Aspose.Words 中設定預設字型與預設匯入字型時。了解完整的逐步解決方案。
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: zh-hant
og_description: 設定警告回呼，以在配置預設字型及設定預設匯入字型時監測字型變更。請參考 Aspose.Words 完整教學。
og_title: 在 C# 中設定警告回呼 – 完整指南
tags:
- Aspose.Words
- C#
- Document Import
title: 在 C# 中設定警告回呼 – 完整字型處理指南
url: /zh-hant/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中設定警告回呼 – 完整字型處理指南

是否曾在載入 Word 文件時需要 **設定警告回呼**，同時又想 *設定預設字型*？你並不孤單。在許多實務專案——例如自動化報表產生器或文件轉換管線——缺少字型會悄悄破壞版面，而唯一能捕捉這類問題的方式，就是透過警告回呼 **監控字型變更**。

本教學將手把手示範如何使用 Aspose.Words for .NET **設定警告回呼**、**設定預設字型**，甚至 **設定預設匯入字型**。完成後，你將擁有可直接執行的程式碼片段，了解每個步驟的意義，並能因應自訂字型資料夾或靜默替換等邊緣情況進行調整。

---

## 前置條件

- .NET 6.0 以上（此程式碼亦支援 .NET Framework 4.6+）  
- Aspose.Words for .NET NuGet 套件（`Install-Package Aspose.Words`）  
- 一個放置備援字型的資料夾（例如 `fonts/Arial.ttf`）  
- 基本的 C# 主控台應用程式知識  

不需要其他額外函式庫。

---

## 步驟 1：建立 LoadOptions 並 **設定預設字型**

當你想要掌控字型處理時，第一件事就是建立 `LoadOptions` 實例。此物件告訴 Aspose.Words 在匯入時如何處理缺少的字型。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**為什麼重要：**  
如果來源文件參考的字型未安裝在伺服器上，Aspose.Words 會搜尋你提供的資料夾。這正是 **設定預設匯入字型** 的核心——你明確告訴函式庫在任何警告產生前，就先找好替代字型的路徑。

---

## 步驟 2：**設定警告回呼** 以 **監控字型變更**

Aspose.Words 會在必須替換字型（以及其他情況）時拋出 `WarningInfoCollection`。只要掛上處理程序，就能記錄或回應每一次的替換。

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**為什麼重要：**  
僅 **設定預設字型** 無法讓你稽核實際被替換的字型。回呼提供即時日誌，滿足 **監控字型變更** 的需求，並協助你在 CI 管線中及早發現意外的備援。

---

## 步驟 3：使用已備妥的選項載入文件

現在 `LoadOptions` 已完整設定，你可以安全載入任何 `.docx` 檔案。若發生字型替換，回呼會自動觸發。

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**你會看到的結果：**  
如果來源使用的字型不存在，主控台會印出類似以下訊息：

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

此輸出證實你已成功 **設定警告回呼**，且 **預設匯入字型** 已生效。

---

## 步驟 4：（可選）微調字型替換行為

有時你可能想把所有缺少的字型全部換成同一個字型族，無論原始請求為何。Aspose.Words 允許全域設定 *fallback font*。

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**何時使用：**  
若你要為品牌產出 PDF，且品牌僅允許有限的字型集合，這樣可以確保每份文件的字型一致，即使來源文件嘗試使用奇特字型也不會影響版面。

---

## 步驟 5：儲存或進一步處理文件

載入後，你可以繼續執行任何需要的處理——編輯、轉 PDF、擷取文字等。以下示範如何將文件存為 PDF，同時保留已替換的字型。

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

產生的 PDF 會在每處替換發生的地方顯示 fallback 字型，讓你直觀確認 **設定警告回呼** 已如預期運作。

---

## 常見陷阱與專業提示

| 陷阱 | 為何會發生 | 解決方式 |
|------|------------|----------|
| **回呼從未觸發** | `LoadOptions.WarningCallback` 沒有在載入文件 **之前** 指定。 | 一定要在呼叫 `new Document(...)` 之前先掛上回呼。 |
| **字型資料夾錯誤** | 路徑拼寫錯誤或缺少讀取權限。 | 確認資料夾存在且應用程式具備 `Read` 權限。為了可靠性建議使用絕對路徑。 |
| **大量替換，輸出雜訊** | 大型文件缺少多個字型。 | 只過濾 `WarningType.FontSubstitution`（如範例所示），或改寫入日誌檔而非直接印到主控台。 |
| **fallback 字型未套用** | 替代字型本身未放在機器上。 | 把 `.ttf`/`.otf` 檔放入 `SetFontsFolder` 指定的資料夾。Aspose.Words 會直接載入，無需 OS 安裝。 |

**專業小技巧：** 在 CI/CD 管線中執行時，將主控台輸出導向建置產物。如此即可保留每次建置期間所有字型替換的稽核紀錄。

---

## 完整可執行範例（直接複製貼上）

以下程式碼可直接放入新的 Console App 專案，內含所有步驟、using 陳述式與說明註解。

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**預期的主控台輸出**（假設 `Times New Roman` 缺失）：

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

執行程式後，開啟 `output.pdf`，即可看到所有缺字的地方已使用 fallback 字型呈現。

---

## 結論

現在你已掌握在 C# 中 **設定警告回呼**、**設定預設字型**、**監控字型變更**，以及 **設定預設匯入字型** 的完整生產模式。只要在載入前掛上警告收集器、將 `FontSettings` 指向可靠的字型資料夾，必要時再強制全域 fallback，即可完整掌握字型替換的可見性與控制，這正是任何穩健文件處理管線所必需的。

想更進一步嗎？試試以下延伸應用：

- 從資料庫 **動態載入字型**（於執行時呼叫 `FontSettings.SetFontsFolder`）。  
- **自訂警告處理程序**，將資訊寫入結構化日誌（JSON、CSV）以供分析。  
- **平行文件處理**，為每個執行緒建立獨立的 `LoadOptions`，避免互相干擾。

歡迎自行實驗、依照自家架構調整程式碼，並在留言區分享你的發現。祝開發順利！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}