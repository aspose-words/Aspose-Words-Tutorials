---
category: general
date: 2026-06-24
description: 如何使用 IWarningCallback 來偵測 Aspose.Words 文件中缺失的字型。了解完整、可執行的範例與最佳實踐。
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: zh-hant
og_description: 如何使用 IWarningCallback 於 Aspose.Words 中偵測缺失字型。請參考逐步指南，獲得完整、可投入生產的解決方案。
og_title: 如何使用 IWarningCallback – 偵測缺失字型
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: 如何使用 IWarningCallback – 使用 Aspose.Words 偵測缺少字型
url: /zh-hant/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 IWarningCallback – 偵測 Aspose.Words 中缺失的字型

在使用 Aspose.Words 並且需要在 DOCX 檔案中 **偵測缺失字型** 時，如何使用 **IWarningCallback** 是必備的。本指南將逐步示範完整的可直接複製貼上的範例，說明如何使用 IWarningCallback 捕捉字型替代警告、為何重要，以及取得警告後該怎麼處理。

如果你曾經開啟文件時因為未安裝自訂字型而看到亂碼，你一定深有體會。完成本教學後，你將擁有一套可靠的程式化方式來發現這類問題、記錄下來，甚至自動套用備用字型。

## 你將學到什麼

- **IWarningCallback** 的目的以及何時使用它。  
- 如何實作自訂的警告收集器，以隔離 **偵測缺失字型** 事件。  
- 將收集器接入 **LoadOptions**，以監控每一次文件載入。  
- 驗證輸出並處理邊緣情況（多個缺失字型、靜默警告等）。  

### 前置條件

- .NET 6.0 或更新版本（程式碼亦可於 .NET Framework 4.6+ 執行）。  
- 透過 NuGet 安裝 Aspose.Words for .NET（`Install-Package Aspose.Words`）。  
- 一個引用了機器上不存在字型的 DOCX 檔案（例如 `DocumentWithMissingFont.docx`）。  

不需要額外的函式庫——所有功能皆內建於 Aspose.Words。

---

## 如何使用 IWarningCallback 偵測 Aspose.Words 中缺失的字型

以下是 **完整、可執行的程式**。將其複製到新的 Console 專案中，調整檔案路徑後執行。你將看到每個缺字型警告的主控台輸出。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### 預期輸出

如果 `DocumentWithMissingFont.docx` 引用了名為 *“MyFancyFont”* 且未安裝的字型，將會看到類似以下的輸出：

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

每一行以 **[Missing Font]** 為前綴，皆由我們的 **IWarningCallback** 實作產生，證明我們成功 **偵測缺失字型**。

## 步驟 1：實作 IWarningCallback 介面

為什麼需要自訂類別？Aspose.Words 會因各種原因拋出 **warnings**——檔案格式問題、已棄用功能，以及對我們最重要的字型替代。透過實作 `IWarningCallback`，我們取得一個鉤子，能即時接收每個警告。針對 `WarningType.FontSubstitution` 進行過濾，即可聚焦於字型缺失的情況。

**小技巧：** 若需捕捉 *所有* 警告以作診斷，只要移除 `if` 判斷，並記錄每個 `info.Type` 即可。

## 步驟 2：將回呼接入 LoadOptions

`LoadOptions` 是告訴 Aspose.Words 如何處理輸入文件的入口。將 `WarningCallback` 設為我們收集器的實例，可確保整個載入過程都會觸發回呼。你可以在多個文件間重複使用同一個 `LoadOptions` 物件，對批次處理流程相當便利。

**常見問題：** *如果載入文件時未指定 LoadOptions 會怎樣？*  
**回答：** Aspose.Words 仍會在內部拋出警告，但若沒有回呼，這些警告會被靜默丟棄，且你失去 **偵測缺失字型** 的機會。

## 步驟 3：載入文件並捕捉缺字型警告

接受檔案路徑與 `LoadOptions` 的 `Document` 建構子負責主要工作。當檔案被解析時，任何缺失的字型都會觸發我們的 `FontWarningCollector.Warning` 方法。主控台輸出證明此機制有效。

**邊緣情況：** 單一文件可能引用多個不存在的字型。回呼會針對每個缺失字型觸發一次，因此會看到多行輸出——非常適合建立完整的報告。

## 為什麼使用 IWarningCallback 而非手動字型檢查？

你可以在載入後手動掃描文件的 `Run.Font` 屬性，但這需要文件先成功載入——若字型完全不存在則會失敗。警告系統在任何替代發生 **之前** 就運作，讓你能真實掌握缺失的字型。

此外，回呼作為載入管線的一部分執行，意味著你可以提前中止、即時替換字型，或在不額外遍歷文件樹的情況下記錄詳細診斷資訊。

## 優雅地處理多個缺失字型

如果預期會有大量缺失字型，建議將它們彙總至集合中：

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

載入完成後，你可以遍歷 `MissingFonts`，例如將它們寫入 CSV 檔供設計團隊使用。

## 加分項：將警告記錄至檔案

主控台輸出適合示範，但正式程式碼通常會記錄至永久儲存。將 `Console.WriteLine` 呼叫改為類似以下的寫法：

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

如此即可留下可供日後審查的稽核紀錄，滿足合規需求。

## 結論

我們已說明 **如何使用 IWarningCallback** 來 **偵測 Aspose.Words 中缺失的字型**，從實作回呼、接入 `LoadOptions` 到處理產生的警告。此方法可即時掌握字型相關問題，讓你在文件呈現前就能記錄、替換或提醒使用者。

接下來可以探索的方向：

- **備用字型**：在發生替代時以程式方式指定預設字型。  
- **批次處理**：遍歷資料夾內的文件，重複使用相同的 `AggregatingFontCollector`。  
- **使用者回饋**：將缺字型警告顯示於 UI 而非主控台。

在自己的專案中試試看吧——不再有神祕的亂碼，只有清晰且可行的診斷資訊。祝開發愉快！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，並在此基礎上延伸。每篇資源皆提供完整可執行的程式碼範例與逐步說明，協助你精通更多 API 功能，並在專案中探索其他實作方式。

- [如何載入 DOCX 並偵測缺失字型 – 完整 C# 指南](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [如何在 Aspose.Words 中偵測字型 – 處理警告與設定](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [如何在 Aspose.Words 中使用 LoadOptions – 完整指南](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}