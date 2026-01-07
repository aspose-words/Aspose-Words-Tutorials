---
category: general
date: 2026-01-06
description: 了解如何在載入文件時取得警告，以及如何使用 Aspose.Words 監控字型。本指南涵蓋警告回呼與字型替換追蹤。
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: zh-hant
og_description: 如何在 Aspose.Words 中取得警告？請依照此步驟教學，在載入文件時監控字型並捕捉替換訊息。
og_title: 如何在 Aspose.Words 中取得警告 – 監控字型
tags:
- Aspose.Words
- C#
- Font Monitoring
title: 如何在 Aspose.Words 中取得警告 – 監控 C# 字體
url: /zh-hant/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words 中取得警告 – 監控 C# 中的字型

有沒有想過當 Word 文件包含您未安裝的字型時，**如何取得警告**？這是常見的問題——您的應用程式會悄悄替換缺少的字型，而您卻不知情。好消息是，您可以掛接 Aspose.Words 的警告系統，並即時**監控字型**。

在本教學中，我們將完整示範如何捕捉字型替換警告、為什麼這很重要，以及取得資訊後該怎麼處理。無需外部文件，只要一個可直接貼到 Visual Studio 的完整範例即可執行。

> **專業提示：**如果您正在構建文件轉換流水線，提前記錄缺少的字型可避免後續產生的版面配置問題。

---

## 您需要的條件

- **Aspose.Words for .NET**（最新版本；自 v23.10 起 API 未變更）
- .NET 開發環境（Visual Studio、Rider，或安裝 C# 擴充功能的 VS Code）
- 一個引用了您未安裝字型的範例 `.docx`（例如 **“NonExistentFont”**）

就這些——不需要除 Aspose.Words 之外的其他 NuGet 套件。

---

## 第一步 – 設置警告收集器（標題中的主要關鍵字）

您首先需要一個地方即時儲存警告。Aspose.Words 在 `LoadOptions` 上提供了 `WarningCallback` 屬性，正是為此而設。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**為什麼這很重要：**  
當程式庫遇到缺少的字型時，它不會拋出例外，而是產生一個 `WarningInfo` 物件。透過自訂收集器，您可以完整掌握每一次的替換事件，從而**監控字型**，而不會被其他訊息淹沒。

---

## 第二步 – 使用啟用警告的選項載入文件

現在正式讀取檔案。前一步建立的 `LoadOptions` 會確保所有與字型相關的警告都被捕捉。

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**底層發生了什麼？**  
Aspose.Words 會解析 Word 檔案、解析字型，當找不到請求的字型時，會回退到替代字型（通常是 Arial）。此回退會觸發 `WarningType.FontSubstitution` 警告，並寫入 `warningCollector`。

---

## 第三步 – 檢查收集到的警告（標題中的主要關鍵字再次出現）

文件載入完成後，只需遍歷 `warningCollector`，將所有字型替換訊息印出即可。

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**預期輸出**（假設缺少的字型是 *“FancyScript”*）：

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

如果文件中包含多個未知字型，您會看到每個替換各佔一行——非常適合寫入日誌或觸發警報。

---

## 第四步 – 可選：將警告資訊寫入日誌或永久保存

在正式環境中，僅用 `Console.WriteLine` 通常不夠。以下範例示範如何將警告寫入 JSON 檔案，以便日後分析。

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

現在您擁有一份永久記錄，可供監控儀表板使用，甚至自動觸發缺少字型檔案的請求。

---

## 第五步 – 驗證結果並清理

執行程式。若看到替換訊息，即表示您已成功**取得警告**並開始**監控字型**。若沒有任何輸出，請再次確認測試文件確實引用了未安裝的字型。

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

零筆警告通常代表以下兩種情況：

1. 所有字型皆已在本機解決（可能字型已安裝），或
2. 文件未包含需要替換的字型參考。

---

## 常見問題與避免方法

| 問題 | 為何會發生 | 解決方式 |
|------|------------|----------|
| **沒有警告出現** | 字型實際上已存在於系統，或文件只使用內建字型。 | 在來源檔案中將字型名稱改成不可能的字串（例如 `XYZ123`），再重新測試。 |
| **警告過多（噪音）** | 在迴圈中載入多個文件卻未清除收集器。 | 為每個文件重新實例化 `WarningInfoCollection`，或在處理完畢後呼叫 `warningCollector.Clear()`。 |
| **效能影響** | 大量寫入磁碟會拖慢批次處理速度。 | 先在記憶體緩衝警告，批次寫入，或使用非同步 I/O。 |
| **缺少 `using Aspose.Words.Loading;`** | `LoadOptions` 類別位於此命名空間。 | 如步驟 1 所示，加入缺少的 `using` 指令。 |

---

## 延伸應用 – 監控其他類型的警告

除了字型替換，Aspose.Words 還會針對以下情況發出警告：

- **已棄用功能** (`WarningType.Deprecated`),
- **可能的資料遺失** (`WarningType.DataLoss`),
- **不支援的檔案格式** (`WarningType.UnsupportedFileFormat`)。

您可以在第 3 步擴充過濾條件，同時捕捉這些警告：

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

如此一來，您不僅**監控字型**，也能**取得所有警告**，全面掌握應用程式可能遭遇的問題。

---

## 完整可執行範例（直接複製貼上）

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**執行方式：**編譯專案、執行程式，即可看到警告被印出並保存。這就是 **如何取得警告** 以及 **如何監控字型** 的完整解答。

---

## 結論

您現在已掌握 **如何從 Aspose.Words 取得警告**，特別是字型替換情境，並學會 **如何在文件載入過程中監控字型**。透過掛接 `WarningCallback`、遍歷收集的 `WarningInfo` 物件，並視需要將資料永久保存，您即可對缺少字型事件擁有完整透明度——這是任何文件處理流水線的關鍵能力。

接下來的步驟？試著將警告過濾器擴展至資料遺失或已棄用功能的警告，或將 JSON 日誌整合至 Grafana 等監控儀表板。相同的模式適用於所有警告類型，讓您隨時掌握 Aspose.Words 可能拋出的任何問題。

祝開發順利，願您的文件永遠如您所預期的那樣正確呈現！

---

<img src="font-warnings.png" alt="how to get warnings in Aspose.Words" style="max-width:100%;">

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}