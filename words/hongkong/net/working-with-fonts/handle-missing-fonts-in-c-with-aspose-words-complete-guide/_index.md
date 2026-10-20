---
category: general
date: 2026-02-26
description: 使用 Aspose.Words 在 C# 中處理缺少字型的情況。學習捕捉字型替代警告、實作 IWarningCallback，確保文件外觀正確。
draft: false
keywords:
- handle missing fonts
- Aspose.Words font warning
- C# LoadOptions
- IWarningCallback implementation
- document loading with missing fonts
- font substitution handling
language: zh-hant
og_description: 快速處理 C# 中缺少的字型。本指南示範如何使用 Aspose.Words 捕捉字型替代警告、實作 IWarningCallback，並驗證結果。
og_title: 在 C# 中處理缺失字型 – Aspose.Words 逐步教學
tags:
- Aspose.Words
- C#
- Document Processing
title: 使用 Aspose.Words 在 C# 中處理缺少字型 – 完整指南
url: /zh-hant/net/working-with-fonts/handle-missing-fonts-in-c-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中使用 Aspose.Words 處理缺失字型 – 完整指南

曾經在 C# 載入 Word 文件時需要 **處理缺失字型**，卻發現輸出結果怪怪的嗎？你並不孤單。當來源檔案引用了機器上未安裝的字型時，Aspose.Words 會悄悄替換成其他字型，這可能會破壞版面配置或品牌形象。  

好消息是：只要設定 **警告回呼 (warning callback)**，就能捕捉每一次字型替換事件、記錄下來，並決定是否提供替代字型。在本教學中，我們會一步步說明整個流程——從建立專案到驗證主控台輸出——讓你再也不會因為看不見的字型而吃驚。

> **你將得到**：一個可直接執行的 C# 主控台應用程式，會報告每個缺失的字型、說明警告產生的原因，並示範如何為處理程式加入自訂邏輯。

---

## 前置條件

- .NET 6.0 或更新版本（此程式碼同時適用於 .NET Core 與 .NET Framework）
- Visual Studio 2022（或任何你慣用的 C# IDE）
- Aspose.Words for .NET 的 **授權**（免費試用版可用於測試）
- 一份引用了你未安裝字型的 Word 文件（例如在 Linux 主機上缺少 *Comic Sans MS*）

只要具備上述條件，讓我們開始吧。

---

## 步驟 1：建立新主控台專案並加入 Aspose.Words

為了保持整潔，先從一個全新的主控台專案開始。

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
dotnet add package Aspose.Words
```

> **小技巧**：若想針對特定執行環境，可加上 `--framework net6.0` 參數。

這會下載最新的 Aspose.Words NuGet 套件，裡面包含我們稍後會用到的 `LoadOptions` 與 `IWarningCallback` 類型。

---

## 步驟 2：實作警告處理程式 (IWarningCallback)

Aspose.Words 在載入文件時，會為每個非致命問題拋出 `WarningInfo` 物件。透過實作 `IWarningCallback`，你可以自行決定如何處理這些警告。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

public class FontWarningHandler : IWarningCallback
{
    // This method is called automatically by Aspose.Words whenever a warning occurs.
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property contains the name of the missing font and the substitute used.
            Console.WriteLine($"⚠️ Missing font detected: {info.Description}");
        }
        // You could also log other warning types here if you wish.
    }
}
```

**為什麼重要**：若未設定處理程式，字型替換的警告會被悄悄忽略。將它們印出來後，你即可即時看到缺少了哪些字型，以及 Aspose.Words 改用了哪一個替代字型。

---

## 步驟 3：使用警告回呼設定 LoadOptions

現在把處理程式掛到文件載入流程中。`LoadOptions` 允許在檔案解析前插入回呼。

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // 1️⃣ Tell Aspose.Words to use our FontWarningHandler.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // 2️⃣ Path to the Word file that contains missing fonts.
        string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

        // 3️⃣ Load the document with the custom options.
        Document doc = new Document(docPath, loadOptions);

        // At this point, any font‑substitution warning has already been printed.
        Console.WriteLine("✅ Document loaded successfully.");
    }
}
```

> **注意**：將 `YOUR_DIRECTORY` 替換成實際放置測試 `.docx` 的資料夾路徑。`LoadOptions` 必須傳入 `Document` 建構子；若省略，預設的靜默行為會生效。

---

## 步驟 4：執行應用程式並驗證輸出

編譯並執行：

```bash
dotnet run
```

如果文件引用了機器上不存在的字型（例如 *Papyrus*），你會看到類似以下的訊息：

```
⚠️ Missing font detected: The font 'Papyrus' was not found. Using 'Times New Roman' as a substitute.
✅ Document loaded successfully.
```

這一行即清楚說明了缺失的字型名稱以及 Aspose.Words 所選的備用字型。接下來，你可以決定嵌入缺失的字型、修改來源文件，或接受此替換結果。

---

## 步驟 5：進階 – 收集警告以供日後使用

有時你可能想先把警告存起來，而不是立即印出。下面示範如何把訊息聚合到 List 中。

```csharp
using System.Collections.Generic;

public class FontWarningCollector : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string msg = $"Missing font: {info.Description}";
            Messages.Add(msg);
        }
    }
}
```

並相應地更新 `Main`：

```csharp
static void Main()
{
    var collector = new FontWarningCollector();

    LoadOptions lo = new LoadOptions { WarningCallback = collector };
    Document doc = new Document(@"YOUR_DIRECTORY\DocumentWithMissingFont.docx", lo);

    Console.WriteLine("✅ Document loaded.");
    if (collector.Messages.Count > 0)
    {
        Console.WriteLine("\n--- Font Substitution Report ---");
        foreach (var m in collector.Messages)
            Console.WriteLine(m);
    }
}
```

現在你擁有一個可重複使用的清單，能寫入日誌檔、傳送至監控服務，或在 UI 上顯示。

---

## 步驟 6：常見陷阱與避免方式

| 問題 | 為何會發生 | 解決方式 |
|------|------------|----------|
| **沒有出現警告** | 回呼未正確掛載，或文件載入時未使用 `LoadOptions`。 | 確保在呼叫 `Document` 建構子 **之前** 設定 `LoadOptions.WarningCallback`。 |
| **訊息中的字型名稱不正確** | 部分字型已嵌入文件，Aspose.Words 會回報 *原始* 名稱，而非嵌入的名稱。 | 檢查來源檔案的字型參照；嵌入字型即可根除警告。 |
| **效能影響** | 為成千上萬的文件收集警告會增加開銷。 | 只在除錯時使用 `Console.WriteLine`；需要資料時才改用收集器。 |

---

## 視覺化摘要

![Handle missing fonts illustration showing warning callback flow](/images/handle-missing-fonts.png "Diagram of handling missing fonts with Aspose.Words")

*此圖（含主要關鍵字的替代文字）說明了在文件載入期間，警告回呼如何截取字型替換事件的流程。*

---

## 結論

現在你已掌握 **在 C# 中使用 Aspose.Words 處理缺失字型** 的方法。透過在 `LoadOptions` 中注入 `IWarningCallback`，即可完整掌握每一次字型替換事件，進行記錄或自訂處理，確保產生的文件保持預期的外觀與感受。

> **快速回顧**：  
> 1. 在主控台應用程式中加入 Aspose.Words。  
> 2. 實作 `FontWarningHandler`（或其他收集器）。  
> 3. 載入文件時以 `LoadOptions` 傳入回呼。  
> 4. 驗證主控台輸出或已儲存的警告。  

接下來，你可以探索 **嵌入缺失字型** (`FontSettings.SubstitutionSettings`) 或 **自動從企業字型伺服器下載字型**——這兩者都是本模式的自然延伸。

對 **Aspose.Words 字型警告**、**C# LoadOptions** 或 **載入缺失字型的文件** 有更多疑問嗎？歡迎留言，祝開發順利！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}