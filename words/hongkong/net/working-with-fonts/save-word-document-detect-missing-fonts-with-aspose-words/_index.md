---
category: general
date: 2026-03-22
description: 使用 Aspose.Words 保存 Word 文件並檢測缺失字型。了解如何追蹤缺失字型以及在 C# 中捕獲字型錯誤。
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: zh-hant
og_description: 在 C# 中儲存 Word 文件並偵測缺失字型。本指南說明如何追蹤缺失字型，並使用警告回呼捕捉字型錯誤。
og_title: 儲存 Word 文件 – 使用 Aspose.Words 偵測缺失字型
tags:
- Aspose.Words
- C#
- Document Processing
title: 儲存 Word 文件 – 使用 Aspose.Words 偵測缺少的字型
url: /zh-hant/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 儲存 Word 文件 – 偵測缺失字型與 Aspose.Words

有沒有曾經需要 **save word document**（儲存 Word 文件），但不確定裡面的某些字型是否能在往返過程中保留下來？這種情況比你想像的更常發生，特別是文件在不同字型庫的機器之間傳遞時。好消息是？Aspose.Words 為你提供內建的方式，在 **save word document**（儲存 Word 文件）時 **detect missing fonts**（偵測缺失字型），讓你可以記錄、警告，甚至在檔案呈現在使用者螢幕前先替換它們。

在本教學中，我們將逐步示範一個完整、可直接執行的範例，不僅能儲存 Word 文件，還能 **track missing fonts**（追蹤缺失字型）與 **capture font errors**（捕捉字型錯誤），方法是使用自訂的警告處理程式。完成後，你將清楚了解為什麼警告回呼很重要、如何掛接它，以及當發生字型替換時，主控台會顯示什麼樣的輸出。沒有多餘的說明——只要把以下程式碼直接放入 .NET 專案即可使用。

> **Prerequisites**  
> • .NET 6（或任何近期的 .NET Framework）已安裝  
> • Visual Studio 2022 或你慣用的 IDE  
> • 已取得 **Aspose.Words for .NET** 的授權副本（免費試用版可用於測試）  

如果你已具備上述條件，讓我們開始吧。

---

## 儲存 Word 文件並偵測缺失字型

核心概念很簡單：在呼叫 `Document.Save` 之前，將實作 `IWarningCallback` 的物件指派給 `Document.WarningCallback`。Aspose.Words 會在遇到每一個警告時呼叫此物件，包含當來源文件參考系統找不到的字型時產生的 **font substitution**（字型替換）警告。

```csharp
using Aspose.Words;
using Aspose.Words.Warning;

// Step 1: Create a warning handler that prints font substitution messages
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only react to font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// Step 2: Load a document that may contain missing fonts
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Step 3: Register the warning handler with the document
document.WarningCallback = new FontWarningHandler();

// Step 4: Save the document; any font substitution warnings will be output to the console
document.Save("YOUR_DIRECTORY/output.docx");
```

**你會看到的結果：**  
如果 `input.docx` 參考了未安裝的字型，主控台會印出類似以下的訊息：

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

這行訊息會精確告訴你哪個字型缺失，以及 Aspose.Words 使用了什麼替代字型——非常適合在檔案發佈前 **capture font errors**（捕捉字型錯誤）。

---

## 使用警告回呼追蹤缺失字型（逐步說明）

### 1️⃣ 安裝 Aspose.Words

在專案的 NuGet 主控台執行：

```bash
dotnet add package Aspose.Words
```

這會下載最新的穩定版（目前為 24.10）。保持函式庫為最新可確保取得最新的 **detect missing fonts** 功能與錯誤修正。

### 2️⃣ 定義警告處理程式

為什麼需要單獨的類別？實作 `IWarningCallback` 能讓你將所有警告邏輯集中管理。你也可以把訊息寫入檔案、傳送遙測，或在缺失字型是工作流程的致命錯誤時拋出例外。

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only the warnings we care about
        if (info.Type == WarningType.FontSubstitution)
        {
            // Here we simply write to the console,
            // but you could replace this with any logging framework.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **Pro tip:** 若需要在多個文件間 **track missing fonts**（追蹤缺失字型），可以在處理程式內部使用 `List<string>` 儲存訊息，之後再對外提供報表。

### 3️⃣ 載入來源文件

`Document` 建構子可以接受檔案路徑、串流，甚至是原始位元組。大多數情況下，你會指向從使用者或其他系統收到的 `.docx` 檔案。

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

如果檔案很大，建議使用 `LoadOptions` 開啟延遲載入，以降低記憶體壓力。

### 4️⃣ 附加回呼

將實例指派給 `doc.WarningCallback`。從此之後，所有警告（包括字型替換）都會透過你的處理程式傳遞。

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ 儲存文件

現在可以安全地呼叫 `Save`。警告處理程式會在儲存過程中 **同步** 執行，因此你會立即看到輸出。

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

如果你想儲存為其他格式（PDF、HTML 等），相同的警告機制仍會生效——Aspose.Words 仍會在轉換前回報缺失字型。

---

## 捕捉字型錯誤 – 常見邊緣情況

雖然基本流程已涵蓋大多數情境，實務專案常會遇到一些小問題。以下列出可能的變化與對應處理方式。

### 標頭/頁腳中的缺失字型

標頭與頁腳是獨立節點，但警告系統會將它們視為與正文相同的字型。無需額外程式碼；回呼同樣會對這些字型觸發。只要確保載入完整文件（預設行為即如此）。

### 同一文件內多次替換

若文件使用了多種未知字型，處理程式會對每一次替換分別呼叫一次。為避免主控台被訊息淹沒，可考慮去除重複訊息：

```csharp
class FontWarningHandler : IWarningCallback
{
    private readonly HashSet<string> _seen = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution && _seen.Add(info.Description))
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

### 將警告轉為例外

有時缺失字型是致命問題。可在回呼內拋出例外以中止儲存：

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

記得將 `doc.Save` 包在 `try/catch` 區塊中，以優雅地處理例外。

---

## 驗證結果 – 期待的情形

儲存完成後，使用 Microsoft Word（或任何相容檢視器）開啟 `output.docx`。版面應與原始文件相同，但在主控台觀察到的替代字型會以備用字型呈現。若要再次確認，可：

1. 開啟 **File → Options → Advanced → Show document content → Use draft quality** —— 這會強制 Word 顯示所有隱藏的字型替換。
2. 使用 Word 的 **Replace Fonts** 對話框（`Ctrl+Shift+F`）查看實際嵌入的字型。

如果一切如預期，你已成功 **save word document** 同時 **detect missing fonts** 並 **capture font errors**。 🎉

---

## 完整可執行範例（直接複製貼上）

以下程式碼可直接放入新的 Console App 專案。只需將 `YOUR_DIRECTORY` 替換為你機器上的實際資料夾路徑。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warning;

namespace FontWarningDemo
{
    // Step 1: Create a warning handler that prints font substitution messages
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            // Only handle font‑substitution warnings
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Load a document that may contain missing fonts
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3: Register the warning handler with the document
            document.WarningCallback = new FontWarningHandler();

            // Step 4: Save the document; any font substitution warnings will be output to the console
            document.Save("YOUR_DIRECTORY/output.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**預期的主控台輸出**（範例）：

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

以上即是全部內容——沒有隱藏步驟，也不需要額外查閱文件。

---

## 結論

我們剛剛示範了如何在 **save word document** 時，同時 **detect missing fonts**、**track missing fonts** 與 **capture font errors**，方法是利用 Aspose.Words 的警告回呼。只要實作一個小型的 `IWarningCallback`，就能在儲存時完整掌握字型替換情況，讓你可以記錄、替換或中止操作。

準備好接受下一個挑戰了嗎？試著將回呼改寫成將警告寫入結構化的 JSON 日誌，或結合 Aspose.PDF 在保留字型資訊的同時進行轉檔。你也可以探索直接將缺失字型嵌入輸出檔——Aspose.Words 透過 `LoadOptions.FontSettings` 支援字型嵌入。

快去試試看，依你的工作流程調整程式碼，並告訴我們使用結果。祝開發順利！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}