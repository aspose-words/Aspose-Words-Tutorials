---
category: general
date: 2025-12-23
description: 學習如何修復損壞的 docx 檔案、使用復原模式、將方程式匯出為 LaTeX，以及在 C# 中產生唯一的圖片名稱。提供逐步程式碼與說明。
draft: false
keywords:
- recover corrupted docx
- how to use recovery mode
- export equations to latex
- generate unique image names
language: zh-hant
og_description: 修復受損的 docx 檔案，使用復原模式，將方程式匯出為 LaTeX，並在 C# 中使用 Aspose.Words 產生唯一的圖片名稱。
og_title: 修復損壞的 docx – 完整 C# 教學
tags:
- Aspose.Words
- C#
- Document Recovery
title: 恢復損毀的 docx – 完整指南：修復、將數學匯出為 LaTeX 及產生唯一圖片名稱
url: /zh-hant/net/programming-with-officemath/recover-corrupted-docx-full-guide-to-repair-export-math-to-l/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 復原損毀的 docx – 完整指南：修復、匯出數學式為 LaTeX 以及產生唯一的圖片名稱

是否曾經打開一個 **.docx** 卻因為檔案損毀而無法載入？你並不孤單。在許多實務專案中，損壞的 Word 檔案會卡住整個工作流程，但好消息是，你可以以程式方式 **復原損毀的 docx** 檔案。

在本教學中，我們將逐步說明 **復原損毀的 docx**、展示 **如何使用復原模式**、示範 **將方程式匯出為 LaTeX**，最後說明 **在儲存為 Markdown 時產生唯一的圖片名稱**。完成後，你將擁有一個可直接執行的 C# 程式，能一次處理上述所有工作。

## 前置條件

- .NET 6 或更新版本（此程式碼亦相容 .NET Framework 4.6+）。  
- Aspose.Words for .NET（免費試用版或授權版）。透過 NuGet 安裝：

```bash
dotnet add package Aspose.Words
```

- 基本的 C# 與檔案 I/O 知識。  
- 一個損毀的 `corrupt.docx` 檔案供測試（可透過截斷有效檔案來模擬損毀）。

> **小技巧：** 在開始之前先備份原始檔案——復原動作只有在覆寫來源檔案時才會是破壞性的。

## 步驟 1 – 使用復原模式復原損毀的 DOCX

首先，我們需要告訴 Aspose.Words 將傳入的檔案視為可能受損。這就是 **如何使用復原模式** 的關鍵所在。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load a possibly corrupted document using recovery mode
        // -----------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded successfully – recovery mode applied.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
            return;
        }

        // ---------------------------------------------------------------
        // Subsequent steps go here...
        // ---------------------------------------------------------------
    }
}
```

**為什麼這很重要：**  
啟用 `RecoveryMode.Recover` 後，Aspose.Words 會嘗試重建內部文件樹，跳過無法讀取的部分，同時盡可能保留內容。若未啟用此模式，`Document` 建構子會拋出例外，導致無法挽救檔案。

> **如果檔案已無法修復該怎麼辦？**  
> 函式庫仍會回傳一個 `Document` 物件，但可能缺少某些節點。你可以檢查 `doc.GetChildNodes(NodeType.Any, true).Count` 以了解存活的元素數量。

## 步驟 2 – 儲存為 Markdown 時將 Office Math 方程式匯出為 LaTeX

許多技術文件會使用 Office Math 撰寫方程式。若你需要將這些方程式轉成 LaTeX（例如在科學部落格上發表），可以請 Aspose.Words 為你完成轉換。

```csharp
        // -----------------------------------------------------------------
        // Step 2: Export Office Math equations to LaTeX in a Markdown file
        // -----------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        string markdownPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(markdownPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown with LaTeX equations saved to: {markdownPath}");
```

**運作原理：**  
`OfficeMathExportMode.LaTeX` 會指示儲存器將每個 `OfficeMath` 節點以 LaTeX 形式取代，並以 `$…$`（行內）或 `$$…$$`（顯示）包裹。產生的 Markdown 檔案即可直接供 Hugo、Jekyll 等靜態網站產生器使用。

> **邊緣情況：** 若原始文件包含複雜的方程式物件（例如矩陣），LaTeX 轉換可能會產生多行輸出。請檢查生成的 `.md`，確保符合你的格式需求。

## 步驟 3 – 儲存為 PDF 並控制浮動圖形的標籤

有時你需要同一文件的 PDF 版本，同時在意浮動圖形（圖片、文字方塊）在可及性方面的標籤方式。`ExportFloatingShapesAsInlineTag` 旗標讓你自行決定。

```csharp
        // -----------------------------------------------------------------
        // Step 3: Save as PDF with custom floating‑shape tagging
        // -----------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true // true → <Figure>, false → <Div>
        };

        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved with inline tags to: {pdfPath}");
```

**為什麼要切換此旗標？**  
- `true` → 浮動圖形會變成 `<Figure>` 標籤，許多螢幕閱讀器會將其視為帶說明的獨立圖片。  
- `false` → 圖形會被包在通用的 `<Div>` 標籤中，可能會被輔助技術忽略。依你的可及性需求自行選擇。

## 步驟 4 – 匯出為 Markdown 並自訂圖片處理（產生唯一圖片名稱）

將 Word 文件儲存為 Markdown 時，所有內嵌圖片會寫入磁碟。預設情況下，它們會使用原始檔名，若同時處理多個文件於同一資料夾，容易發生名稱衝突。現在，我們在儲存過程中掛鉤，**自動產生唯一的圖片名稱**。

```csharp
        // -----------------------------------------------------------------
        // Step 4: Export to Markdown with custom image naming
        // -----------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                // Create a sub‑folder for markdown images if it doesn't exist
                string imageFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imageFolder);

                // Build a GUID‑based filename preserving the original extension
                string uniqueName = Guid.NewGuid().ToString() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imageFolder, uniqueName);
            }
        };

        string markdownPath2 = @"YOUR_DIRECTORY\out2.md";
        doc.Save(markdownPath2, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with uniquely named images saved to: {markdownPath2}");
```

**背後發生了什麼？**  
`ResourceSavingCallback` 會在儲存操作期間為每個外部資源（圖片、SVG 等）呼叫。回傳完整路徑即可決定檔案的存放位置與名稱。使用 GUID 可確保 **產生唯一的圖片名稱**，不需手動管理。

> **小提示：** 若你需要可預測的命名規則（例如根據圖片 alt 文字），可將 `Guid.NewGuid()` 改為 `resourceInfo.Name` 的雜湊值。

## 完整範例程式

將上述所有步驟整合，以下是可直接貼到 Console App 的完整程式碼：

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -------------------------------------------------------------
        // Load the possibly corrupted document (Recovery Mode)
        // -------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded with recovery mode.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Unable to load document: {ex.Message}");
            return;
        }

        // -------------------------------------------------------------
        // Export equations to LaTeX in Markdown
        // -------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        string mdMathPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(mdMathPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown (LaTeX) saved: {mdMathPath}");

        // -------------------------------------------------------------
        // Save as PDF with inline floating‑shape tags
        // -------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved: {pdfPath}");

        // -------------------------------------------------------------
        // Export Markdown with unique image names
        // -------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                string imgFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imgFolder);
                string uniqueFile = Guid.NewGuid() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imgFolder, uniqueFile);
            }
        };
        string mdImgPath = @"YOUR_DIRECTORY\out2.md";
        doc.Save(mdImgPath, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with unique images saved: {mdImgPath}");
    }
}
```

### 預期輸出

執行程式後，主控台會顯示類似以下訊息：

```
✅ Document loaded with recovery mode.
✅ Markdown (LaTeX) saved: YOUR_DIRECTORY\out.md
✅ PDF saved: YOUR_DIRECTORY\out.pdf
✅ Markdown with unique images saved: YOUR_DIRECTORY\out2.md
```

你會得到三個檔案：

| 檔案 | 用途 |
|------|------|
| `out.md` | Markdown，所有 Office Math 方程式皆以 LaTeX (`$…$` 或 `$$…$$`) 形式呈現。 |
| `out.pdf` | PDF，浮動圖形以 `<Figure>` 標籤標記，提升可及性。 |
| `out2.md` + `md_images\*` | Markdown 以及一個存放唯一命名（基於 GUID）圖片檔案的資料夾。 |

## 常見問題與邊緣案例

| 問題 | 解答 |
|------|------|
| **如果損毀的檔案沒有可復原的內容怎麼辦？** | Aspose.Words 仍會回傳 `Document` 物件，但可能是空的。請在後續處理前檢查 `doc.GetChildNodes(NodeType.Paragraph, true).Count`。 |
| **我可以更改 LaTeX 的分隔符嗎？** | 可以——將 `markdownMathOptions.MathDelimiter = "$$"` 設為顯示樣式分隔符。 |
| **需要手動釋放 `Document` 物件嗎？** | `Document` 類別實作 `IDisposable`。若一次處理多個檔案，建議使用 `using` 區塊以即時釋放原生資源。 |
| **如何保留原始圖片檔名？** | 在回呼函式內回傳 `Path.Combine(imageFolder, resourceInfo.Name)`。但請留意名稱衝突的風險。 |
| **GUID 方式在版本控制系統中安全嗎？** | GUID 在不同執行間保持唯一，但不易閱讀。若需可重現的名稱，可將原始名稱加上專案級鹽值後雜湊。 |

## 結論

我們示範了如何 **復原損毀的 docx** 檔案，並說明了 **如何使用

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}