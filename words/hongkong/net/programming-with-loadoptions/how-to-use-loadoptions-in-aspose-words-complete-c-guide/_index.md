---
category: general
date: 2026-04-10
description: 如何在 Aspose.Words 中使用 LoadOptions 於載入文件時捕捉字體替換警告。學習一步一步的 C# 解決方案，並附完整程式碼範例。
draft: false
keywords:
- how to use loadoptions
- warningcallback
- font substitution warning
- aspose.words loadoptions example
- c# document loading
language: zh-hant
og_description: 如何在 Aspose.Words 中使用 LoadOptions 於載入文件時捕捉字體替換警告。本指南將帶領您完成完整的 C# 實作。
og_title: 如何在 Aspose.Words 中使用 LoadOptions – 完整 C# 指南
tags:
- Aspose.Words
- C#
- Document Processing
- Font Management
title: 如何在 Aspose.Words 中使用 LoadOptions – 完整 C# 指南
url: /zh-hant/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words 中使用 LoadOptions – 完整 C# 指南

在需要對文件載入進行精細控制時，如何在 Aspose.Words 中使用 LoadOptions 常常是一個障礙。在本教學中，我們將會示範**如何使用 LoadOptions**來捕捉字型替換警告，並在 C# 中對其作出回應。

如果你曾經開啟過一個引用了缺失字型的 DOCX，並且好奇為何輸出結果看起來怪怪的，那麼你來對地方了。我們將會從建立 `LoadOptions` 實例到在主控台印出警告細節，完整走過整個流程。最後，你將會得到一段可直接放入任何 .NET 專案的即用程式碼片段。

## 你將學到的內容

- 為何 `LoadOptions` 對可靠的文件匯入很重要。  
- 如何插入一個專門監控 **字型替換警告** 的 **WarningCallback**。  
- 載入 Word 檔案並啟用這些選項所需的完整程式碼。  
- 處理邊緣案例的技巧，例如包含多個缺失字型的文件。  

不需要外部文件說明——所有你需要的資訊都在此。

## 前置條件

| Requirement | Reason |
|-------------|--------|
| .NET 6.0 or later | 提供範例中使用的 C# 10 語法所需的執行環境。 |
| Aspose.Words for .NET (latest version) | 提供 `LoadOptions` 以及警告基礎建設的函式庫。 |
| A DOCX file that may reference fonts you don’t have installed | 用來觀察警告回呼的實際效果。 |
| Visual Studio 2022 (or any IDE you like) | 讓除錯與測試變得直觀。 |

如果你已經具備上述條件，太好了——讓我們直接進入主題。

## 步驟 1 – 建立 LoadOptions 物件並掛接 WarningCallback

在**如何使用 LoadOptions**時，你首先要做的事就是實例化它。關鍵在於將委派指派給 `WarningCallback`。每當 Aspose.Words 遇到想要通知你的情況時（尤其是缺少字型），此委派就會被觸發。

```csharp
using System;
using Aspose.Words;

// Step 1: Build LoadOptions with a warning listener.
LoadOptions loadOptions = new LoadOptions
{
    // The lambda receives the sender (unused) and a WarningInfo object.
    WarningCallback = (sender, args) =>
    {
        // We'll filter for font‑substitution warnings later.
        if (args.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        }
    }
};
```

**為何這很重要：** 若未設定回呼，Aspose.Words 會悄悄將缺失字型替換為預設字型，你可能永遠不會注意到視覺上的變化。註冊 `WarningCallback` 後，你即可即時取得每一次替換的紀錄，這對於保證品質的文件處理流程至關重要。

## 步驟 2 – 僅對字型替換警告作出回應

你可能會想知道回呼是否會被不相關的警告（例如已棄用的功能）淹沒。答案是*會*——但我們可以過濾它們。在上面的程式碼片段中，我們已經檢查 `args.WarningType == WarningType.FontSubstitution`。這行就是 **字型替換警告** 的防護，作為次要關鍵字讓輸出保持聚焦。

如果你需要處理其他類型的警告，只要擴充 `if` 區塊即可：

```csharp
if (args.WarningType == WarningType.FontSubstitution)
{
    // Existing handling…
}
else if (args.WarningType == WarningType.UnknownFileFormat)
{
    Console.WriteLine($"❓ Unknown format: {args.Description}");
}
```

此模式展示了 **warningcallback** 機制的彈性，讓你能針對關心的情境自訂回應。

## 步驟 3 – 使用已設定的 LoadOptions 載入文件

現在監聽器已就緒，最後一步是將 `LoadOptions` 實例傳入 `Document` 建構子。這就是 **Aspose.Words LoadOptions 範例** 真正發光發熱的時刻。

```csharp
// Step 3: Load the DOCX while the warning callback is active.
try
{
    Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    Console.WriteLine("✅ Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"🚨 Failed to load document: {ex.Message}");
}
```

**你會看到的結果：** 若 DOCX 引用了機器上未安裝的字型，主控台會輸出類似以下的訊息：

```
⚠️ Font substitution: Font 'Calibri Light' has been substituted with 'Arial'.
✅ Document loaded successfully.
```

此輸出證明你已成功**使用 LoadOptions**來監控字型問題。

## 完整可執行範例（直接複製貼上）

以下是完整的程式，你可以立即編譯並執行。它結合了上述三個步驟，加入了一些小細節（例如友善的橫幅），並示範錯誤處理。

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        Console.WriteLine("=== Aspose.Words LoadOptions Demo ===");

        // 1️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = (sender, args) =>
            {
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substitution: {args.Description}");
                }
            }
        };

        // 2️⃣ Attempt to load the document.
        try
        {
            // Replace the path with your own file that may contain missing fonts.
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            Console.WriteLine("✅ Document loaded without fatal errors.");

            // Optional: Do something with the document, e.g., save as PDF.
            // doc.Save("output.pdf");
        }
        catch (Exception e)
        {
            Console.WriteLine($"🚨 Error: {e.Message}");
        }

        Console.WriteLine("=== End of Demo ===");
    }
}
```

### 預期輸出

在缺少 `input.docx` 所引用字型的機器上執行程式，會得到類似以下的輸出：

```
=== Aspose.Words LoadOptions Demo ===
⚠️ Font substitution: Font 'Times New Roman' has been substituted with 'Arial'.
✅ Document loaded without fatal errors.
=== End of Demo ===
```

若所有字型皆已安裝，則只會看到成功訊息——不會出現任何警告行。

## 常見陷阱與專業技巧

- **陷阱：** 忘記設定 `WarningCallback`。程式仍會載入，但你會錯過替換的細節。  
  **專業技巧：** 建立 `LoadOptions` 後立即指派回呼；成本低且日後受益。

- **陷阱：** 使用相對路徑卻指向錯誤的資料夾。  
  **專業技巧：** 使用 `Path.Combine(Environment.CurrentDirectory, "input.docx")` 以取得更穩健的檔案查找方式。

- **陷阱：** 以為警告會中止載入。  
  **專業技巧：** 字型替換警告屬於*資訊性*，不會終止載入。若需更嚴格的驗證，可在回呼中於發生替換時拋出例外。

- **陷阱：** 在未安裝任何字型的伺服器上執行（例如極簡的 Docker 映像）。  
  **專業技巧：** 事先安裝所需字型或將其隨應用程式一起打包，然後使用回呼驗證在正式環境中不會發生替換。

## 何時使用 LoadOptions 與何時使用載入後檢查

你可能會問：「為什麼不在文件載入後再檢查？」答案在於效能與正確性。於載入 **期間** 處理警告，可在任何版面計算或 PDF 轉換發生前即時捕捉問題。這在批次處理管線中特別有價值，因為每多一步都會增加時間成本。

## 延伸範例：儲存所有替換字型的報告

若需要永久紀錄（例如合規需求），可修改回呼將訊息收集至清單，並在載入完成後寫入檔案：

```csharp
var substitutions = new List<string>();

loadOptions.WarningCallback = (s, a) =>
{
    if (a.WarningType == WarningType.FontSubstitution)
    {
        substitutions.Add(a.Description);
        Console.WriteLine($"⚠️ {a.Description}");
    }
};

// After loading:
File.WriteAllLines("font-substitutions.txt", substitutions);
```

現在你同時擁有主控台回饋與持久化的日誌。

## 相關主題，你可能想進一步探索

- **如何在 Aspose.Words 中嵌入自訂字型** – 徹底避免替換。  
- **使用 LoadOptions 限制文件大小** – 有助於防範惡意的大檔案。  
- **將 Word 轉換為 PDF 並保留排版字體** – 與警告回呼方式相得益彰。  

## 結論

我們已從頭到尾說明了在 Aspose.Words 中**如何使用 LoadOptions**：建立選項、掛接聚焦於 **字型替換警告** 的 `WarningCallback`，並自信地載入文件。完整範例即開即用，額外的技巧則可避免常見陷阱。

歡迎自行嘗試——將回呼換成其他警告類型、寫入資料庫，或整合至驗證上傳 Word 檔案的 Web 服務中。此模式彈性高、可靠，最重要的是讓你看見原本隱藏的字型替換過程，避免文件渲染被破壞。

祝程式開發順利，願你的文件永遠如預期般正確呈現！ 

![顯示在 Aspose.Words 中使用 LoadOptions 及警告回呼流程的圖示](https://example.com/images/loadoptions-flow.png "如何使用 LoadOptions 圖解")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}