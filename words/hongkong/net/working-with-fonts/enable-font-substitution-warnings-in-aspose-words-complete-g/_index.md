---
category: general
date: 2026-01-11
description: 啟用字型替代警告，以偵測 .NET 文件中缺少的字型。了解如何取得缺失的字型名稱以及使用 Aspose.Words 列出缺少的字型。
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: zh-hant
og_description: 在 Aspose.Words 中啟用字型替代警告，以偵測缺失的字型、取得缺失字型名稱，並列出文件中缺失的字型。
og_title: 啟用字型替換警告 – C# 逐步教學
tags:
- Aspose.Words
- C#
- Document Processing
title: 在 Aspose.Words 中啟用字型替換警告 – 完整指南
url: /zh-hant/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 啟用字型替換警告 – 完整指南

有沒有想過為什麼在伺服器上載入 Word 文件後，版面看起來稍有異常？很可能是原作者使用的字型在你的機器上不存在，Aspose.Words 會悄悄將其替換為最相近的字型。**啟用字型替換警告** 後，你即可立即知道缺少哪些字型、它們被替換成什麼，以及如何根據這些資訊採取行動。

在本教學中，我們將逐步示範一個實用的端到端範例，說明如何 **偵測缺少的字型**、取得 **get missing font name**，甚至 **列出缺少的字型** 以供報告。內容精簡，直接提供可立即套用於任何 .NET 專案的解決方案。

---

## 你將學會

- 如何設定 `LoadOptions` 讓 Aspose.Words 發出詳細的警告。
- 載入文件並列舉與字型相關警告的完整程式碼。
- 提取缺少的字型名稱及其替代字型，並輸出整齊的報告。
- 處理邊緣情況的技巧，例如文件中缺少數十種字型或使用自訂字型資料夾的情況。

### 前置條件

- .NET 6+（此程式碼亦相容於 .NET Framework 4.7+）
- Aspose.Words for .NET 23.10 或更新版本（可從 NuGet 取得）
- 一個引用了未安裝字型的範例 DOCX（此處稱為 `MissingFont.docx`）

如果你已具備上述條件，讓我們開始吧。

---

## 步驟 1：設定 LoadOptions 以啟用字型替換警告  

首先，你需要告訴 Aspose.Words 你在意缺少的字型。預設情況下，函式庫只會在內部記錄警告。將 `SubstitutionWarningLevel` 設為 `Typical`（或 `All` 以取得最詳細的輸出）即可開啟此功能。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**為什麼這很重要：**  
當設定了 `SubstitutionWarningLevel` 後，每當 Aspose.Words 找不到引用的字型時，會將 `FontSubstitutionWarning` 加入文件的 `Warnings` 集合。此集合是唯一可靠的方式，能在不手動解析文件的情況下 **偵測缺少的字型**。

> **專業提示：** 若你一次處理大量文件，且希望確保捕捉到每一次替換，請使用 `FontSubstitutionWarningLevel.All`。雖然會產生較多訊息，但能保證不會遺漏任何警告。

---

## 步驟 2：使用已設定的選項載入文件  

現在警告系統已就緒，使用剛剛準備好的 `LoadOptions` 載入 DOCX。路徑可以是絕對或相對路徑，只要確保檔案存在即可。

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**背後發生了什麼？**  
Aspose.Words 會解析文件的 XML，解析每個 `<w:font>` 元素，並檢查系統的字型目錄（以及你可能已加入 `FontSettings` 的任何自訂資料夾）。當找不到字型時，會記錄一則警告——這正是我們稍後 **列出缺少的字型** 所需要的資訊。

---

## 步驟 3：遍歷警告並提取缺少的字型詳細資訊  

文件載入記憶體後，`Warnings` 集合會保存所有 `FontSubstitutionWarning`。我們將遍歷它，篩選出相關類型，並輸出友善的報告。

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**預期輸出**（假設來源文件引用了未安裝的 `MyCustomFont`）：

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

請留意每筆條目同時提供了 **get missing font name**（`MyCustomFont`）以及替代字型（`Arial`）。這正是決定是否嵌入原始字型、向作者索取替代字型，或直接接受替換所需的資訊。

---

## 步驟 4（可選）：將資料收集到清單以便後續處理  

如果需要將報告匯出為 CSV、透過 API 傳送，或僅在記憶體中保留以供稍後使用，可將警告儲存於強型別清單中。

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

現在你已經以任何下游系統都能消費的格式 **列出缺少的字型**。無論是供儀表板使用或產生稽核日誌，資料皆已備妥。

---

## 步驟 5：處理邊緣情況與常見陷阱  

### 單次執行中多個缺少的字型  

大型企業範本常會引用數十種自訂字型。警告集合可能變得相當龐大，但上述的遍歷方式具線性擴展性，效能不會成問題。只需確保輸出易於閱讀——若需更深入的分析，可依頁面或樣式分組。

### 自訂字型資料夾  

如果將字型存放在非標準目錄（例如共享網路磁碟），請告訴 Aspose.Words 該去哪裡尋找：

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

在載入文件 *之前* 設定此項，可讓函式庫有機會找到字型，從而完全消除部分警告。

### 抑制特定警告  

有時你知道某些替換是可接受的（例如裝飾性字型，你不介意被替換）。可以在事後過濾掉這些警告：

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### 版本相容性  

`FontSubstitutionWarningLevel` 列舉自 Aspose.Words 20.12 起已穩定。若使用較舊版本，可能需要升級才能使用警告等級功能。

---

## 完整範例  

以下是結合上述所有步驟的完整可執行程式。將其貼到新的 Console 專案中，加入 Aspose.Words NuGet 套件，並將 `docPath` 指向引用了缺少字型的文件。

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

執行此程式將 **啟用字型替換警告**、**偵測缺少的字型**、**取得 get missing font name**，並在 Console 與 CSV 檔案中 **列出缺少的字型**。

---

## 結論  

我們已完整說明如何在 Aspose.Words 中 **啟用字型替換警告**，從最初的設定到提取乾淨的缺少字型清單。依照上述步驟，你即可稽核文件、確保視覺一致性，並避免在伺服器上渲染時出現意外問題。

接下來，你可能想探索：

- **將缺少的字型直接嵌入輸出 PDF 或 DOCX**（使用 `FontSettings.EmbeddedFonts`）。
- **根據產生的報告自動在建置代理上安裝字型**。
- **在 CI 流程中整合**，當關鍵字型缺失時使建置失敗。

試試看這些做法，你就能把簡單的警告系統轉變為完整的字型管理工作流程。

祝程式開發順利，願所有字型皆能被正確找到！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}