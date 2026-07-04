---
category: general
date: 2026-04-21
description: 學習如何在 C# 中使用 Aspose.Words 偵測字型、捕獲警告、設定回呼以及列舉警告。一步一步的指南，助您可靠地處理字型。
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: zh-hant
og_description: 如何在 Aspose.Words 中偵測字型？本教學示範如何擷取警告、設定回呼以及於 C# 中列舉警告。
og_title: 如何在 Aspose.Words 中偵測字型 – 完整指南
tags:
- Aspose.Words
- C#
- Document Processing
title: 如何在 Aspose.Words 中偵測字型 – 完整指南
url: /zh-hant/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words 中偵測字型 – 完整指南

有沒有想過在載入 Word 文件時 **如何偵測字型** 缺失？這種情況比你想像的更常發生，特別是在處理舊版檔案或跨平台部署時。在本教學中，我們將逐步示範一個完整且可執行的範例，該範例 **捕獲警告**、**設定回呼**，以及 **列舉警告**，讓你隨時知道哪些字型被替換。

我們將使用 Aspose.Words for .NET（撰寫時的版本為 v24.9）以及純 C#。不需要外部服務，也不需要魔法——只要 API 加上幾行程式碼。完成後，你將能夠找出每一個字型替換、記錄它，甚至在關鍵字型缺失時決定是否中止載入。

### 需要的環境
- **Aspose.Words for .NET**（透過 NuGet 安裝：`Install-Package Aspose.Words`）
- .NET 6.0 或更新版本（此程式碼亦可在 .NET Framework 上執行）
- 一個引用了機器上不存在的字型（例如 “MyCustomFont.ttf”）的 DOCX 範例
- Visual Studio、Rider，或任何你慣用的 C# 編輯器

> **專業提示：** 若手邊沒有缺少字型的文件，只要將系統中的字型檔案重新命名，或是編輯 DOCX 的 XML 使其引用不存在的字型族，即可模擬此情況。

---

## 如何使用 Aspose.Words 偵測字型

核心概念是掛勾 Aspose.Words 的警告機制。當程式庫找不到所請求的字型時，會拋出 `WarningType.FontSubstitution` 警告。透過自訂 `IWarningCallback` 實作，你可以 **偵測字型** 在載入過程中被替換的情況。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **為什麼這樣可行：** Aspose.Words 會對每一個非關鍵問題呼叫 `Warning` 方法。將 `WarningInfo` 物件儲存起來後，你即可完整取得類型、訊息與上下文，正好能 **偵測字型** 替換的情形。

---

## 載入文件時如何捕獲警告

有了收集器之後，我們需要告訴 `LoadOptions` 使用它。這就是 **如何捕獲警告** 的關鍵步驟。

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **邊緣情況：** 若你是從串流載入文件（`new Document(stream, loadOptions)`），相同的回呼仍然適用——只要傳入串流而非檔案路徑即可。

此時文件已完整載入，但所有字型替換警告都安全地存放在 `warningCollector.Warnings` 中。

---

## 列舉警告並報告字型替換

最後，我們會遍歷收集到的警告，**列舉警告** 中專屬於字型替換的項目。此步驟將原始資料轉換為可讀的報告。

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**預期輸出**（範例）：

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

如果文件中沒有缺少的字型，迴圈將不會產生任何輸出——不必擔心。

---

## 完整可執行範例（所有步驟於單一檔案）

以下程式碼可直接貼到 Console 專案中。它將 **如何偵測字型**、**如何捕獲警告**、**如何設定回呼** 與 **如何列舉警告** 結合成一個完整流程。

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**執行此程式** 後會列印出 Aspose.Words 必須替換的每一個字型。你可以將輸出導向日誌檔、發出警報，或在關鍵字型缺失時中止載入。

---

## 常見問題與注意事項

### 若需要在缺少必要字型時停止載入該怎麼做？
你可以在回呼內檢查 `WarningInfo` 物件，當出現特定字型名稱時拋出例外。例外會中止載入，讓你完全掌控。

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### 這個方法能用於 PDF 或其他格式嗎？
可以。Aspose.Words 為 PDF、RTF、HTML 等格式使用相同的警告基礎建設。只要更換檔案副檔名，其他程式碼保持不變。

### 如何將警告寫入檔案而非 Console？
將 `Console.WriteLine` 換成你偏好的日誌框架（如 `Serilog`、`NLog` 等）。`WarningInfo` 類別提供 `Message`、`Source` 與 `Exception`，方便寫入詳細日誌。

### 這會影響效能嗎？
影響可以忽略不計——Aspose.Words 本身已在內部產生警告。加入回呼僅是把它們存入 List，時間複雜度為 O(n)（n 為警告數量）。對於一般文件而言，額外開銷遠低於總載入時間的 1 %。

---

## 視覺摘要

![如何在 Aspose.Words 中偵測字型 – 警告流程圖](https://example.com/images/font-detection-diagram.png "如何偵測字型")

*Alt text:* **如何偵測字型** – 圖示說明警告回呼、收集與列舉步驟。

---

## 結語

我們已說明如何在 Aspose.Words 中 **偵測字型**，方法包括 **捕獲警告**、**設定回呼** 與 **列舉警告**。完整程式碼範例展示了一套可直接套用於任何 .NET 應用程式的生產等級模式。

接下來，你可能想進一步探索：

- **如何捕獲其他問題的警告**（例如影像轉換失敗）
- **如何為自訂日誌框架設定回呼**
- **如何在批次作業中列舉多個文件的警告**
- 使用 **Aspose.Words.Fonts.FontSettings** 提供備援字型資料夾，從根本減少字型替換次數

試著把收集器調整成符合你日誌風格的方式，從此不會再因意外的字型替換而感到驚訝。若遇到任何怪異情況，歡迎在下方留言——祝開發順利！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}