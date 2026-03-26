---
category: general
date: 2026-03-25
description: 建立警告回呼以載入 Word 文件並偵測缺少的字型。了解如何在 Aspose.Words for .NET 中設定字型。
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: zh-hant
og_description: 建立警告回呼以載入 Word 文件，同時偵測缺少的字型。本指南說明如何在 Aspose.Words 中設定字型。
og_title: 建立警告回呼 – 載入 Word 文件並偵測缺少的字型
tags:
- Aspose.Words
- C#
- Font handling
title: 為載入 Word 文件建立警告回呼 – 完整指南
url: /zh-hant/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 建立警告回呼 – 載入 Word 文件並偵測缺少的字型

有沒有曾經在載入 Word 文件時需要 **建立警告回呼**，卻發現某些字型莫名消失？你並非唯一遇到這情況的人。在許多企業應用程式中，缺少字型會導致版面災難，若沒有適當的回呼，你甚至可能根本不會注意到這個問題。  

好消息是？使用 Aspose.Words for .NET，你可以 **載入 Word 文件**、**偵測缺少的字型**，以及 **設定字型設定**，只需幾行簡潔的程式碼。在本教學中，我們將逐步示範完整且可執行的範例，說明每個部分的重要性，並展示如何驗證警告回呼是否正常運作。

> **你將收穫**  
> * 一個完整的 C# 程式，可載入 DOCX、回報任何字型替換，並讓你自訂字型搜尋路徑。  
> * 了解 `FontSettings`、`LoadOptions` 與 `IWarningCallback` 類別。  
> * 處理邊緣案例（如嵌入字型或系統範圍字型資料夾）的技巧。

---

## 前置條件

- .NET 6+（或 .NET Framework 4.7.2+）搭配 C# 編譯器。  
- Aspose.Words for .NET NuGet 套件（`Install-Package Aspose.Words`）。  
- 一個範例 Word 檔案（`input.docx`），其中使用至少一種未安裝於機器上的字型（例如在精簡的 Windows 容器中未安裝的 *Calibri Light*）。  
- 基本熟悉 C# 主控台應用程式。

不需要額外的函式庫；所有功能皆內建於 Aspose.Words。

## 步驟 1：建立警告回呼以偵測缺少的字型

**主要** 的部分是一個實作 `IWarningCallback` 的類別。Aspose.Words 會在遇到需要發出警告的情況時呼叫此回呼——最常見的就是字型替換。

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**為什麼這很重要** – 若沒有回呼，你只能事後在日誌中篩選。即時處理警告可讓你決定是否中止載入、以備用字型取代缺少的字型，或僅將問題記錄下來以供日後檢閱。

## 步驟 2：設定 FontSettings 以自訂字型處理

在實際載入文件之前，我們可能需要告訴 Aspose.Words 在哪裡尋找系統上不存在的字型。這時就會用到 `FontSettings`。

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**為什麼這很重要** – 若將 Aspose.Words 指向包含缺少字型的資料夾，通常可以完全避免替換。若無法做到，使用合理的預設字型（例如 *Arial*）可確保文件可讀。

## 步驟 3：使用已設定的警告回呼載入 Word 文件

現在把所有部件結合起來：建立 `LoadOptions`、插入我們的 `FontSettings` 與 `FontWarningHandler`，最後載入文件。

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**為什麼這很重要** – `LoadOptions` 是唯一設定文件讀取方式的地方。透過同時提供字型設定與警告回呼，我們確保任何缺少的字型都會在正確位置搜尋，且立即回報。

## 步驟 4：驗證輸出 – 會看到什麼？

在主控台執行程式。若 `input.docx` 使用的字型既未安裝，也不在 `C:\SharedFonts` 中，你會看到類似以下的訊息：

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

若所有字型皆可用，警告行根本不會出現。這種即時回饋在自動化文件處理流程中極為寶貴，因為靜默的字型替換可能會破壞品牌指引。

## 步驟 5：常見陷阱與最佳實踐技巧

| 陷阱 | 如何避免 |
|---------|-----------------|
| **忘記引用 `Aspose.Words.Fonts`** | 確保在檔案頂部加入 `using Aspose.Words.Fonts;`，否則編譯器會抱怨缺少類型。 |
| **字型資料夾路徑錯誤** | 仔細檢查路徑，若有子資料夾請設定 `recursive: true`。可使用 `Path.GetFullPath` 進行除錯。 |
| **多個警告回呼** | Aspose.Words 只會使用最後指定的 `WarningCallback`。若需更複雜的邏輯，保留單一處理器並在內部委派。 |
| **在無 UI 的伺服器上執行** | 主控台寫入沒問題，但對於 Web 應用程式，建議改為寫入檔案或監控系統，而非 `Console.WriteLine`。 |
| **大型文件造成效能下降** | 在多次載入間重複使用同一個 `FontSettings` 實例；頻繁建立會增加成本。 |

**專業提示**：若需要*收集*警告以供日後分析，可在處理器內部使用 `List<string>` 儲存，而不是直接印出。

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

之後即可在文件載入後檢查 `handler.Messages`。

## 步驟 6：擴充解決方案 – 若需要嵌入備用字型該怎麼做？

有時你希望將缺少的字型*嵌入*至輸出 PDF，讓後續檢視器呈現完全相同的外觀。載入文件後，你可以強制嵌入：

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

此程式碼片段示範了相同的 **設定字型設定** 方法如何延伸至載入之外的情況。

## 完整可執行範例

以下是完整程式碼，你可以直接貼到新的 Console App 專案中。它包含了上述所有討論的部分。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**預期輸出**（當缺少字型時）：

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

若未發生替換，則僅顯示成功訊息。

## 結論

我們剛剛 **建立了警告回呼**，能在使用 Aspose.Words **載入 Word 文件** 時可靠地 **偵測缺少的字型**，同時示範了如何 **設定字型設定** 以控制程式庫搜尋字型的路徑與使用的備用字型。透過將 `FontSettings` 與 `LoadOptions` 結合，你即可完整掌握與字型相關的問題——不再有靜默的版面錯誤。

接下來的步驟？可以將 `FontWarningHandler` 換成寫入資料庫的記錄器，或試驗 **字型替換規則**，將特定缺少的字型對映到品牌批准的替代字型。若你的應用在容器化環境中執行，也可以探索從雲端儲存動態載入字型的方式。

對於特定的邊緣案例有疑問——例如處理 OpenType 功能或加密的 DOCX 檔案？歡迎在下方留言，祝編程愉快！  

![建立警告回呼示意圖](https://example.com/images/create-warning-callback.png "建立警告回呼示意圖")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}