---
category: general
date: 2026-02-21
description: 學習如何啟用警告、檢測缺失字型，以及如何使用 Aspose.Words 在 C# 中安全載入 docx。請跟隨逐步指南。
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: zh-hant
og_description: 如何啟用警告、偵測缺少字型，並正確載入 Aspose.Words 的 docx 檔案。附上完整程式碼範例。
og_title: 如何在載入 DOCX 時啟用警告並偵測缺失字型
tags:
- C#
- Aspose.Words
- Document processing
title: 如何在載入 DOCX 檔案時啟用警告並偵測缺少的字型
url: /zh-hant/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

.

Check any other markdown like **bold** etc. Keep bold markers.

Check blockquotes > lines.

Check list items.

Check headings.

Everything done.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在載入 DOCX 檔案時啟用警告並偵測缺少的字型

有沒有想過在缺少字型時**如何啟用警告**，以免它們悄悄搞亂文件的呈現？你並不孤單——大多數開發者都假設函式庫會自動「做好事」，結果卻在之後發現字型被替換卻毫無線索。  

在本教學中，我們將會示範**如何啟用警告**、**如何偵測缺少的字型**，以及使用 Aspose.Words for .NET 正確的**如何載入 docx**方式。完成後，你將擁有一個可直接執行的範例，會將所有字型替換警告印到主控台，讓你不再需要猜測檔案內部發生了什麼。

## 前置條件

- .NET 6.0 或更新版本（此程式碼亦可在 .NET Framework 4.7+ 上執行）  
- Visual Studio 2022 或任何你偏好的 C# IDE  
- **Aspose.Words** NuGet 套件 (`Install-Package Aspose.Words`)  
- 可能包含未在本機安裝字型的 DOCX 檔案（我們稱之為 `input.docx`）

> **專業提示：** 如果沒有測試檔，只要開啟一個使用自訂公司字型的 Word 文件，並另存為 `input.docx`。這樣即可觸發我們想要捕捉的警告。

## 解決方案概觀

1. **建立** 一個 `LoadOptions` 物件，並將 `FontSubstitutionWarnings` 設為開啟。  
2. **載入** DOCX 檔案，使用上述選項。  
3. **檢查** `WarningCallback` 集合中是否有 `FontSubstitution` 條目。  
4. **回應**——你可以記錄、顯示，甚至以程式方式取代缺少的字型。

以下我們將逐步說明每個步驟，解釋*為何*它重要，並提供完整可執行的程式碼片段。

---

## 步驟 1：安裝 Aspose.Words 並設定專案

在我們能**如何啟用警告**之前，我們需要支援此功能的函式庫。

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

或是在 Visual Studio 套件管理員主控台中執行：

```powershell
Install-Package Aspose.Words
```

> **為何需要此步驟？**  
> 若未安裝此套件，`LoadOptions`、`Document` 與警告基礎設施根本不存在。加入 NuGet 參考可確保取得最新的穩定版（截至本文撰寫時為 24.5）。

---

## 步驟 2：建立啟用字型替換警告的載入選項

**如何啟用警告** 的核心在 `LoadOptions` 類別。將 `FontSubstitutionWarnings` 設為 `true`，即可告訴引擎記錄每一次必須替換缺少字型的情況。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **為何要啟用此旗標？**  
> 預設情況下，Aspose.Words 會悄悄將缺少的字型換成備用字型（通常是 Arial）。這可能導致版面移位、字元不可見或品牌違規。開啟此旗標即可完整掌握情況。

---

## 步驟 3：使用已設定的選項載入 DOCX 檔案

既然我們已了解**如何載入 docx**且已開啟警告，接下來就實際執行載入。

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **底層發生了什麼？**  
> 解析 DOCX 時，Aspose.Words 會檢查每個 `<w:rFonts>` 元素。若指定的字型未安裝，會記錄 `FontSubstitution` 警告並退回使用預設字型。因為我們已啟用警告，這些條目會出現在 `document.WarningCallback.Warnings` 中。

---

## 步驟 4：取得並顯示字型替換警告

`WarningCallback` 屬性包含一個 `WarningInfoCollection`。遍歷它，篩選出 `WarningType.FontSubstitution`，並輸出訊息。

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**預期輸出**（範例）：

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **這些訊息該怎麼處理？**  
> 你可以將它們記錄到檔案、在 UI 中顯示，或觸發自訂的字型備援程序。關鍵是現在你已能*偵測缺少的字型*，不再需要之後猜測。

---

## 步驟 5：（可選）以特定備援字型取代缺少的字型

如果你有想要強制使用的公司字型，可以即時處理警告並取代缺少的字型。

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **為何要考慮這樣做？**  
> 它可確保所有產生的文件在視覺上保持一致，對於品牌合規至關重要。

---

## 完整、可執行的範例

以下是一個單一的 C# 檔案，你可以直接貼到 Console 應用程式中。它涵蓋了從安裝套件到印出警告的全部步驟。

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**執行方式**：在專案資料夾執行 `dotnet run`。若有缺少的字型，將會印出警告，且在儲存檔案前會套用可選的取代動作。

---

## 常見問題

### 這也適用於 PDF 轉換嗎？

可以。處理完警告後，你可以呼叫 `doc.Save("output.pdf")`，替換的字型會如同在 DOCX 中一樣出現在 PDF 中。

### 如果我想對特定字型抑制警告該怎麼辦？

你可以在迴圈中過濾——只要跳過 `Message` 中包含你想忽略的字型名稱的 `WarningInfo` 即可。

### 舊版 Aspose.Words 是否支援 `FontSubstitutionWarnings`？

此功能於 20.5 版首次加入。若仍使用較舊版本，請透過 NuGet 升級；API 變更向下相容。

---

## 結論

我們已說明**如何啟用警告**、示範**偵測缺少的字型**，並演示使用 Aspose.Words 正確的**如何載入 docx**方式，同時完整掌握字型替換情況。透過檢查 `document.WarningCallback.Warnings`，即可取得可靠的稽核紀錄——不再有悄悄的備援。

接下來的步驟？可將警告邏輯接入 Serilog 等日誌框架，或打造 UI 在文件發佈給使用者前標示缺少的字型。你也可以探索 `FontSettings` 類別，以更細緻地控制字型替換策略。

祝開發順利，願你的文件永遠如你所願正確呈現！ 

![說明從載入 DOCX 檔案到捕捉字型替換警告流程的圖示 – 如何在 Aspose.Words 中啟用警告](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}