---
category: general
date: 2026-02-24
description: 如何使用 Aspose.Words 檢測 Word 文件中的字型。了解如何設定回呼以及載入 Word 文件的完整程式碼範例。
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: zh-hant
og_description: 如何使用警告回呼檢測 Word 文件中的字型。本指南說明如何設定回呼並使用 Aspose.Words 載入 Word 文件。
og_title: 如何在 Word 文件中偵測字型 – 逐步 C# 教學
tags:
- C#
- Aspose.Words
- Document Processing
title: 如何在 Word 文件中偵測字型 – 完整 C# 指南
url: /zh-hant/net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文件中偵測字型 – 完整 C# 指南

有沒有想過 **如何偵測字型** 在載入 Word 檔時缺失？或許你曾遇過文件在編輯器中看起來沒問題，但產生的 PDF 卻在背後換掉了幾種字型。這是字型替換的典型徵兆，及早捕捉可以避免版面突如其來的錯亂。

在本教學中，我們將示範一個實用解法：使用 **Aspose.Words** 載入 `.docx`，掛載 warning callback，並 **如何設定回呼** 以回報每一次字型替換。完成後，你不只會知道 **如何偵測字型** 的程式寫法，還會了解 **如何設定回呼** 的正確方式，以及 **載入 Word 文件** 的安全作法——全部在一個可直接執行的 C# 範例中。

> **你將會得到**
> * 完整、可直接複製貼上的程式碼範例  
> * 每一行程式的逐步說明  
> * 處理多個缺失字型或自訂字型資料夾等邊緣情況的技巧  
> * 預期的主控台輸出，讓你驗證功能是否正常

---

## 前置條件

- .NET 6.0 或更新版本（程式碼亦可於 .NET Core 上執行）  
- Aspose.Words for .NET NuGet 套件（`Install-Package Aspose.Words`）  
- 一個刻意引用未安裝字型的 Word 檔（例如 `MissingFont.docx`）  
- Visual Studio、Rider，或任何你喜歡的編輯器  

不需要其他函式庫；其餘皆為標準 .NET 執行環境的一部份。

---

## 如何在 Word 文件中偵測字型

### 步驟 1：建立 Load Options 並掛載 Warning Callback

我們首先告訴 Aspose.Words，在載入檔案時若有任何問題要通知我們。這正是 **如何設定回呼** 發揮作用的地方。

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**為什麼這很重要：**  
`LoadOptions` 是自訂載入流程的入口。將 `FontWarningCollector` 的實例指派給 `WarningCallback` 後，Aspose.Words 會在每次以備援字型取代缺失字型時呼叫我們的 `Warning` 方法。這正是 **如何偵測字型** 在機器上不存在的核心機制。

---

### 步驟 2：準備 LoadOptions 物件

現在我們建立 `LoadOptions` 並掛上回呼。

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**專業提示：** 若需要控制 Aspose 從哪裡尋找替代字型，也可以在此設定 `loadOptions.FontSettings`。當伺服器上有私有字型資料夾時特別有用。

---

### 步驟 3：載入 Word 文件

選項準備好後，我們終於 **載入 Word 文件**。此時 Aspose 會解析 DOCX，若有缺失字型，回呼即會被觸發。

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**底層發生了什麼？**  
Aspose.Words 讀取 DOCX 的 XML 部分，解析每個 `<w:font>` 參照，並檢查系統字型集合。只要找不到對應的字型，就會以第一個符合條件的備援字型取代，並拋出 `FontSubstitution` 警告。

---

### 步驟 4：驗證輸出

執行程式並觀察主控台。每個缺失的字型都會出現類似以下的訊息：

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

如果文件中沒有缺失字型，主控台將保持沉默——表示 **如何偵測字型** 沒有找到任何問題。

---

### 步驟 5：完整可執行範例（Console App）

以下是一個可直接放入新 Console 專案的 `Program.cs`，內含前述所有程式碼，並加上一個小幫手讓除錯時主控台不會立即關閉。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**預期的主控台輸出**（範例）：

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

若將 `MissingFont.docx` 換成只使用已安裝字型的檔案，主控台只會顯示「Press any key…」那一行，證明偵測邏輯如預期運作。

---

## 常見問題與邊緣情況

### 若我要捕捉 *所有* 警告，而不只字型替換，該怎麼做？

只要移除 `if (info.Type == WarningType.FontSubstitution)` 的判斷即可。`WarningInfo` 物件內含 `Type` 列舉，你可以依不同情境（例如 `DocumentStructure`、`ImageLoading`）切換處理。

### 能否將警告寫入檔案而非主控台？

當然可以。將 `Console.WriteLine` 換成任意日誌框架的呼叫（`Serilog`、`NLog` 等）。回呼會在載入文件的同一執行緒上執行，請確保你的日誌實作是執行緒安全的。

### 在 Web 應用程式中會如何運作？

在 ASP.NET Core 中，通常會注入一個 singleton 的 `IWarningCallback` 實作，然後透過 `LoadOptions` 傳入。請避免直接寫入回應串流——改為寫入資料庫或記憶體集合，之後再透過 API 端點提供。

### 若自訂字型存放在非系統資料夾，該怎麼設定？

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

現在 Aspose.Words 會先在 `C:\MyCustomFonts` 搜尋，再退回系統字型，從而減少你看到的替換警告次數。

---

## 視覺摘要

![在 Aspose.Words 中偵測字型警告回呼](/images/font-warning-callback.png "使用警告回呼偵測字型的方法")

*此截圖顯示缺少字型被替換時的主控台輸出。alt 文字包含主要的 SEO 關鍵字。*

---

## 結論

你現在已掌握一套穩固、可投入生產環境的 **如何偵測字型** 模式，適用於任何使用 Aspose.Words 載入的 Word 檔。透過 **如何設定回呼**，即可即時掌握缺失或被替換的字型，同時也學會了正確的 **載入 Word 文件** 方法，讓程式碼保持乾淨且易於維護。

接下來的步驟是什麼？可以將回呼擴充為收集警告至清單，然後在 UI 或自動化報告中呈現。也可以探索 `FontSettings.SubstitutionSettings`，自行決定哪些字型會被選為備援。

隨意實驗——換掉文件、加入更多缺失字型，或將此邏輯整合到更大的文件處理流水線中。若遇到任何問題，歡迎在下方留言或於 GitHub 上私訊我。

祝開發順利，願你的文件永遠以預期的字型正確呈現！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}