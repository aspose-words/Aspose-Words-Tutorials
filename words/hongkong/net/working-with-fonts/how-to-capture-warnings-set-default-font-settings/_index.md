---
category: general
date: 2026-03-19
description: 了解如何在 Aspose.Words 中捕捉警告、設定預設字型設定，以及在載入 Word 文件時偵測缺少的字型。
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: zh-hant
og_description: 如何在 Aspose.Words 中捕捉警告、設定預設字型設定，以及在載入 Word 文件時偵測缺少的字型。
og_title: 如何捕捉警告 – 設定預設字型
tags:
- Aspose.Words
- C#
- Document Processing
title: 如何擷取警告 – 設定預設字型設定
url: /zh-hant/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何捕捉警告 – 設定預設字型設定

**如何捕捉警告** 是在使用 Aspose.Words 時常見的需求，特別是當你的文件依賴於目標機器上可能不存在的特定字型時。是否曾打開過 DOCX，卻發現版面配置怪怪的？答案往往隱藏在缺少字型的警告中。

在本指南中，我們將逐步說明 **如何捕捉警告**，同時 **載入 Word 文件**、**設定預設字型設定**，最後 **偵測缺少的字型**，讓你能以程式方式回應。沒有冗餘說明——只提供完整、可執行的範例以及每行程式碼背後的原因。

> *小技巧：* 及早捕捉警告可以避免日後因版面異常而費時除錯。

---

## 需要的環境

- **Aspose.Words for .NET**（截至 2026 年的最新版本）。  
- .NET 開發環境（Visual Studio、Rider 或 VS Code）。  
- 一個引用了你 **未** 安裝字型的範例 DOCX（例如在 Linux 上沒有安裝 *Comic Sans MS*）。

就這些。除了 Aspose.Words，無需額外的 NuGet 套件。

---

## 步驟 1 – 為什麼需要捕捉警告

當 Aspose.Words 解析文件時，可能會遇到主機上不存在的字型。預設情況下，函式庫會靜默地替換為備用字型，這會改變換行、間距，甚至導致文字消失。

結合 **WarningCallback** 與 **FontSettings** 物件，你可以得到兩件事：

1. **可見性** – 為每一次替換取得 `WarningInfo` 條目。  
2. **可控性** – 事先設定預設字型，以減少視覺上的驚喜。

把它想像成安裝了一個「看門狗」，每當引擎在底層換零件時就會大聲提醒。

---

## 步驟 2 – 設定預設字型設定

第一個次要關鍵字 **set default font settings** 就出現在這裡。你需要建立一個 `FontSettings` 實例，並可選擇指向包含備用字型的資料夾。

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **為什麼這樣做？**  
> 若不指定備用字型，Aspose.Words 會挑選系統中第一個符合樣式的字型，這可能與原本的字型差異極大。設定已知的預設字型，可確保在不同機器上都有一致的呈現效果。

---

## 步驟 3 – 準備 Warning Callback 以捕捉警告

現在我們透過將 `WarningInfoCollection` 附加到載入選項，來 **how to capture warnings**。此集合會在載入過程中儲存所有產生的警告。

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

`WarningInfoCollection` 實作了 `IWarningCallback`，因此 Aspose.Words 會自動把每一個警告推入 `warningInfos`，不需要自行輪詢。

---

## 步驟 4 – 使用已設定好的選項載入 Word 文件

這裡正是第二個次要關鍵字 **load word document** 大顯身手的地方。我們透過 `LoadOptions` 實例，同時傳入 `FontSettings` 與 `WarningCallback`。

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

如果文件引用了未安裝的字型，警告回呼會捕捉到 `WarningType.FontSubstitution` 條目。

---

## 步驟 5 – 從收集到的警告中偵測缺少的字型

最後，我們透過遍歷收集到的警告，來回應第三個次要關鍵字 **detect missing fonts**。

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

典型的輸出會是：

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

這一行會精確告訴你缺少哪個字型以及使用了哪個備用字型——你可以將資訊寫入日誌、顯示給使用者，或甚至觸發自訂的字型安裝流程。

---

## 完整可執行範例

以下程式碼可直接貼到 Console 應用程式中。它示範了 **how to capture warnings**、**set default font settings**、**load word document**，以及 **detect missing fonts** 的完整流程。

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**預期結果：** 當指定的 DOCX 引用了未安裝的字型時，主控台會為每一次替換印出警告。若所有字型皆已安裝，則不會有任何輸出。

---

## 常見陷阱與邊緣案例

| 情況 | 為什麼會發生 | 如何處理 |
|-----------|----------------|------------------|
| **未出現警告** 但版面看起來不正確 | 文件可能使用了 *嵌入* 字型，Aspose.Words 會直接渲染而不進行替換。 | 檢查 `Document.HasEmbeddedFonts`，若需在其他機器使用，考慮將嵌入字型抽取出來。 |
| **Multiple warnings for the |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}