---
category: general
date: 2026-06-08
description: 學習如何在 Aspose.Words 中使用 LoadOptions 於文件匯入時偵測缺失字型。逐步指南，包含程式碼、說明與最佳實踐。
draft: false
keywords:
- how to use loadoptions
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- C# document loading
language: zh-hant
og_description: 如何在 Aspose.Words 中使用 LoadOptions 並在載入文件時偵測缺失字型。完整指南，附上程式碼與實用技巧。
og_title: 如何使用 LoadOptions 偵測缺少的字型
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  headline: How to Use LoadOptions to Detect Missing Fonts
  type: TechArticle
- description: Learn how to use LoadOptions in Aspose.Words to detect missing fonts
    during document import. Step-by-step guide with code, explanations, and best practices.
  name: How to Use LoadOptions to Detect Missing Fonts
  steps:
  - name: Create a Warning Handler
    text: Aspose.Words uses the `IWarningCallback` interface to notify you about non‑critical
      issues, such as font substitution. Implement the interface and decide what to
      do when a warning arrives.
  - name: Attach the Handler to LoadOptions
    text: Now we create a `LoadOptions` instance and tell it to use our `FontWarningHandler`.
      This is the point where **how to use LoadOptions** really shines.
  - name: Load the Document Using the Configured Options
    text: Finally, we feed the `LoadOptions` into the `Document` constructor. If the
      source file references a font that isn’t installed, Aspose.Words will fire the
      warning and your handler will print a message.
  - name: Multiple Documents in a Loop
    text: Often you’ll process a batch of files. The same `LoadOptions` instance can
      be reused, but remember that the `WarningCallback` persists across loads. If
      you need per‑document isolation, instantiate a fresh `LoadOptions` for each
      iteration.
  - name: Custom Font Substitution Logic
    text: 'Instead of merely logging, you might want to substitute a specific missing
      font with a corporate‑approved alternative. Extend the handler:'
  - name: Silencing Unwanted Warnings
    text: If you only care about font issues and want to suppress everything else,
      filter by `WarningType` as shown. Conversely, to log *all* warnings, drop the
      `if` check and output `info.WarningType` alongside `info.Description`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Font Management
title: 如何使用 LoadOptions 檢測缺失字型
url: /zh-hant/net/programming-with-loadoptions/how-to-use-loadoptions-to-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 LoadOptions 偵測缺少的字型

有沒有想過在使用 Aspose.Words 載入 Word 文件時 **如何使用 LoadOptions**？在本教學中，我們將會完整示範 **如何使用 LoadOptions** 來 **偵測缺少的字型**，並優雅地處理它們。無論您是構建文件轉換服務或報表引擎，缺少的字型都可能導致版面意外變化，因此必須盡早捕捉。

我們將會一步步說明——從設定警告回呼到解讀結果——讓您最後得到一個可直接放入任何 .NET 專案的完整 C# 範例。無需外部文件，全部自給自足。完成後，您將了解警告系統的存在原因、如何啟用，以及回呼觸發時該怎麼處理。

## 前置條件

在開始之前，請確保您已具備：

- **Aspose.Words for .NET**（任何近期版本；我們使用的 API 自 2022 年起已穩定）。
- .NET 開發環境（Visual Studio、Rider，或安裝 C# 擴充功能的 VS Code）。
- 一個參考了您機器上 **未** 安裝字型的範例 Word 檔 (`input.docx`)。

就這樣——不需要除 Aspose.Words 之外的額外 NuGet 套件。

## 如何在 Aspose.Words 中使用 LoadOptions

**LoadOptions** 類別是自訂文件讀取方式的入口。透過將警告回呼插入其中，您可以在 Aspose.Words 解析檔案的同時 **偵測缺少的字型**。讓我們一步步拆解。

### 步驟 1：建立警告處理程式

Aspose.Words 使用 `IWarningCallback` 介面通知您非致命問題，例如字型替代。實作此介面並決定在收到警告時要執行的動作。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

// Step 1: Define a warning handler that will be notified of font substitutions.
class FontWarningHandler : IWarningCallback
{
    // The Process method is called for every warning Aspose.Words generates.
    public void Process(WarningInfo info)
    {
        // We're only interested in font substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

**為什麼這很重要：**  
如果沒有回呼，Aspose.Words 會悄悄將缺少的字型換成預設字型（通常是 Arial）。捕捉到 `FontSubstitution` 警告後，您可以記錄問題、提醒使用者，甚至以自訂的備援字型取代缺少的字型。

### 步驟 2：將處理程式附加至 LoadOptions

現在我們建立 `LoadOptions` 實例，並告訴它使用我們的 `FontWarningHandler`。這正是 **如何使用 LoadOptions** 發揮威力的關鍵時刻。

```csharp
using Aspose.Words.LoadOptions;

// Step 2: Create LoadOptions and attach the warning handler.
var loadOptions = new LoadOptions
{
    // The WarningCallback property accepts any IWarningCallback implementation.
    WarningCallback = new FontWarningHandler()
};
```

**為什麼這很重要：**  
`LoadOptions` 是許多匯入時設定（編碼、密碼等）的集中管理點。設定 `WarningCallback` 後，即可啟用輕量級、事件驅動的機制，適用於所有使用此選項載入的文件。

### 步驟 3：使用已設定的選項載入文件

最後，我們把 `LoadOptions` 傳入 `Document` 建構子。如果來源檔案引用了未安裝的字型，Aspose.Words 會觸發警告，您的處理程式將輸出訊息。

```csharp
// Step 3: Load the document using the configured LoadOptions.
// Any missing fonts will trigger the FontWarningHandler.
Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**您會看到的結果：**  
假設 `input.docx` 使用名為 *“MyCustomFont”* 的字型，而該字型未安裝於機器上，控制台輸出會類似：

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
```

如果所有字型皆已安裝，回呼將保持沉默——不會有輸出，也不會影響效能。

## 使用警告回呼偵測缺少的字型（次要關鍵字示範）

**detect missing fonts** 這個片語自然出現在上方標題中，加強了次要關鍵字的出現頻率。以下探討在實務專案中可能遇到的幾種變化。

### 迴圈中處理多個文件

通常您會一次處理一批檔案。同一個 `LoadOptions` 實例可以重複使用，但請記得 `WarningCallback` 會在多次載入間保留。如果需要每個文件獨立的警告環境，請在每次迭代時重新建立 `LoadOptions`。

```csharp
string[] files = Directory.GetFiles(@"C:\Docs", "*.docx");
foreach (var file in files)
{
    var options = new LoadOptions { WarningCallback = new FontWarningHandler() };
    var document = new Document(file, options);
    // Perform further processing...
}
```

### 自訂字型替代邏輯

如果不只想記錄，還想將特定缺少的字型替換為公司批准的替代字型，可擴充處理程式：

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Extract the missing font name from the description.
            string missingFont = info.Description.Split('\'')[1];
            // Choose a fallback based on your policy.
            string fallback = missingFont.Equals("MyCustomFont") ? "Calibri" : "Arial";
            Console.WriteLine($"Missing '{missingFont}'. Using fallback '{fallback}'.");
            // You could also modify FontSettings here if needed.
        }
    }
}
```

現在您不僅 **偵測缺少的字型**，還能自行決定如何取代它們。

### 靜音不需要的警告

如果您只關心字型問題，想要抑制其他所有警告，可如範例般依 `WarningType` 進行過濾。相反地，若想記錄 *所有* 警告，只要移除 `if` 判斷，並同時輸出 `info.WarningType` 與 `info.Description`。

## 完整、可執行範例

將上述步驟整合起來，以下是一個可直接編譯執行的完整程式。請將 `"YOUR_DIRECTORY/input.docx"` 替換為您的測試檔案路徑。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Process(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Ensure the Aspose.Words license is set if you have one.
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        string docPath = Path.Combine("YOUR_DIRECTORY", "input.docx");

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
            // You can now work with 'doc' – save, modify, export, etc.
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**預期的控制台輸出（當字型缺失時）：**

```
Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

如果沒有缺少的字型，您只會看到：

```
Document loaded successfully.
```

## 常見陷阱與專業提示

- **陷阱：** 忘記設定 `WarningCallback`。API 仍會替換字型，但您永遠不會得知此情況。  
  **專業提示：** 需要字型完整性時，務必附加處理程式；幾乎不會增加任何成本。

- **陷阱：** 

## 接下來該學什麼？

以下教學與本指南所示技巧緊密相關，並提供完整可執行的程式碼範例與逐步說明，協助您掌握更多 API 功能，或在自己的專案中探索其他實作方式。

- [如何在 Aspose.Words 中偵測字型 – 處理警告與設定](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [如何在 Aspose.Words 中擷取字型 – 完整指南](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [如何載入 DOCX 並偵測缺少的字型 – 完整 C# 指南](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}