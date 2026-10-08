---
category: general
date: 2026-03-14
description: 使用 Aspose.Words 快速將 Word 轉換為 Markdown，並從 docx 中提取圖片。開發人員的逐步 C# 範例。
draft: false
keywords:
- convert word to markdown
- extract images from docx
- Aspose.Words C#
- markdown conversion tutorial
- docx image handling
language: zh-hant
og_description: 使用 Aspose.Words 將 Word 轉換為 Markdown 並從 docx 中提取圖片。請參考此詳細指南，輕鬆完成無憂轉換。
og_title: 將 Word 轉換為 Markdown – 完整 C# 教學
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: 將 Word 轉換為 Markdown – 完整指南（含圖片提取）
url: /zh-hant/net/programming-with-markdownsaveoptions/convert-word-to-markdown-full-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將 Word 轉換為 Markdown – 完整 C# 教學

有沒有曾經需要**將 Word 轉換為 Markdown**，卻不確定如何保留內嵌圖片？你並不孤單。許多開發者都會遇到文字能成功轉換，但圖片卻消失無蹤的問題。好消息是，只要幾行 C# 程式碼，加上功能強大的 Aspose.Words 函式庫，你就能一次完成**將 Word 轉換為 Markdown***以及***從 docx 中提取圖片**的操作。

在本教學中，我們將逐步說明你需要的全部步驟：從安裝 NuGet 套件、載入 `.docx` 檔案、設定 Markdown 儲存器，到撰寫回呼函式將每張圖片存入自訂資料夾並重新寫入圖片連結。完成後，你將得到一個可直接使用的 Markdown 檔案，以及一個整潔的 `resources` 目錄，內含原始 Word 文件中的所有圖片。

## 你將學到的內容

- 如何在 C# 專案中設定 Aspose.Words for .NET。  
- 完整的程式碼，能在保留圖片的同時**將 Word 轉換為 Markdown**。  
- 為何 `ResourceSavingCallback` 對於**從 docx 中提取圖片**至關重要。  
- 常見的陷阱（例如路徑分隔符、檔名重複）以及避免方法。  
- 快速驗證步驟，確保產生的 Markdown 正確渲染。

### 前置條件

| 需求 | 原因 |
|-------------|--------|
| .NET 6.0 或更新版本（或 .NET Framework 4.7+） | Aspose.Words 兩者皆支援；較新的執行環境可提供更佳效能。 |
| Visual Studio 2022（或任何 C# IDE） | 讓除錯與套件管理更為簡便。 |
| 需要網際網路連線以還原 NuGet 套件 | 函式庫會從官方來源下載。 |
| 一個包含文字**與**圖片的範例 `input.docx` | 以觀察圖片提取的實際效果。 |

不需要額外的第三方工具——Aspose.Words 會在底層自行處理所有工作。

---

## 步驟 1：透過 NuGet 安裝 Aspose.Words

首先，將 Aspose.Words 套件加入你的專案。開啟 **Package Manager Console** 並執行以下指令：

```powershell
Install-Package Aspose.Words
```

或者使用介面操作：右鍵點擊專案 → *Manage NuGet Packages* → 搜尋 “Aspose.Words” → 點擊 **Install**。此步驟會下載核心 DLL 以及稍後需要的 `Saving` 命名空間。

> **小技巧：** 固定版本（例如 `22.12.0`），以避免函式庫自動更新時產生意外的破壞性變更。

---

## 步驟 2：載入來源 Word 文件

函式庫就緒後，我們即可載入 `.docx` 檔案。請使用指向來源文件的絕對或相對路徑。

```csharp
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file. Replace the placeholder with your actual path.
Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

> **為何重要：** `Document` 會解析整個 Word 套件，讓我們能存取段落、表格，以及稍後要提取的隱藏圖片部件。

---

## 步驟 3：建立 Markdown 儲存選項

Aspose.Words 提供 `MarkdownSaveOptions` 類別，可讓我們微調轉換行為。至少先建立實例，之後再掛接回呼函式。

```csharp
// Instantiate the options object.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
```

你可以調整屬性，例如將 `ExportImagesAsBase64` 設為 `false`（因為我們需要分離的圖片檔案），或在需要將頁首頁尾匯入 Markdown 時設定 `ExportHeadersFooters`。

---

## 步驟 4：設定 ResourceSavingCallback – 從 DOCX 提取圖片

這是本教學的核心。`ResourceSavingCallback` 會在儲存器欲寫入**每個資源**（圖片、字型等）時觸發。透過自訂處理程式，我們可以決定圖片的存放位置以及 Markdown 檔案如何引用它。

```csharp
mdOptions.ResourceSavingCallback = new ResourceSavingCallback(
    (sender, args) =>
    {
        // 1️⃣ Define the folder where we’ll dump extracted pictures.
        string imageFolder = @"YOUR_DIRECTORY\resources\";

        // 2️⃣ Ensure the folder exists – create it on the fly.
        Directory.CreateDirectory(imageFolder);

        // 3️⃣ Preserve the original filename (e.g., Image1.png).
        string imageFileName = Path.GetFileName(args.FileName);
        string targetPath   = Path.Combine(imageFolder, imageFileName);

        // 4️⃣ Write the image stream to disk.
        using (FileStream fs = new FileStream(targetPath, FileMode.Create))
        {
            args.Stream.CopyTo(fs);
        }

        // 5️⃣ Tell the Markdown generator to use a relative path.
        //    This is the step that **extract images from docx** correctly.
        args.ResourceFileName = $"resources/{imageFileName}";
    });
```

### 這段程式碼的作用

1. **建立** `resources` 子資料夾（若尚未存在）。  
2. **複製** 每個傳入的圖片串流至該資料夾，保留原始檔名以免混淆。  
3. **更新** Markdown 連結（`![alt](resources/Image1.png)`），讓讀者在檔案渲染時能看到圖片。

> **邊緣情況：** 若兩張圖片同名，後者會覆寫前者。為避免此情況，可在儲存前為檔名加上 GUID，或使用 `Path.GetUniqueFileName`（自訂輔助函式）來產生唯一檔名。

---

## 步驟 5：將文件儲存為 Markdown

掛接好回呼函式後，最後一步只需一行程式碼即可寫出 Markdown 檔案。

```csharp
// Choose the output path for the Markdown file.
string markdownPath = @"YOUR_DIRECTORY\output.md";

doc.Save(markdownPath, mdOptions);
```

此呼叫完成後，你將得到：

- `output.md` 包含 Markdown 文字與類似 `![Image1](resources/Image1.png)` 的圖片引用。  
- 一個 `resources` 資料夾，內含從原始 `.docx` 提取的所有圖片。

---

## 步驟 6：驗證結果

在任意 Markdown 檢視器（VS Code、GitHub、Typora）開啟 `output.md`。你應該能看到原始文件的標題、清單，以及**正確呈現的圖片**。若有圖片遺失，請：

1. 確認 `resources` 資料夾內是否有該檔案。  
2. 確保 Markdown 中的相對路徑（`resources/<filename>`）與資料夾名稱完全相符（Linux 上大小寫敏感）。  
3. 確認圖片檔案未損毀——直接在圖像檢視器中開啟檢查。

---

## 完整範例程式

以下為完整、可直接執行的程式。請將 `YOUR_DIRECTORY` 佔位符替換為實際的資料夾路徑。

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class WordToMarkdown
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Load the source Word document.
        // -------------------------------------------------
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // -------------------------------------------------
        // 2️⃣ Prepare Markdown save options.
        // -------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // Export images as separate files, not Base64.
            ExportImagesAsBase64 = false
        };

        // -------------------------------------------------
        // 3️⃣ Set up the callback to **extract images from docx**.
        // -------------------------------------------------
        mdOptions.ResourceSavingCallback = new ResourceSavingCallback(
            (sender, args) =>
            {
                string imageFolder = @"YOUR_DIRECTORY\resources\";
                Directory.CreateDirectory(imageFolder);

                string imageFileName = Path.GetFileName(args.FileName);
                string targetPath = Path.Combine(imageFolder, imageFileName);

                using (FileStream fs = new FileStream(targetPath, FileMode.Create))
                {
                    args.Stream.CopyTo(fs);
                }

                // Update the reference used inside the Markdown file.
                args.ResourceFileName = $"resources/{imageFileName}";
            });

        // -------------------------------------------------
        // 4️⃣ Save as Markdown.
        // -------------------------------------------------
        string outputPath = @"YOUR_DIRECTORY\output.md";
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("Conversion complete! Check output.md and the resources folder.");
    }
}
```

**預期輸出：** 開啟 `output.md`，你會看到類似以下內容：

```markdown
# Sample Title

Here is some introductory text.

![Image1](resources/Image1.png)

More paragraphs…

![Diagram](resources/Diagram.jpg)
```

所有圖片皆與文字並排顯示，與原始 Word 檔案中的呈現方式相同。

---

## 常見問題與注意事項

**Q: 我可以在提取時變更圖片格式嗎？**  
A: 可以。在回呼函式內，你可以在寫出之前重新編碼串流（例如轉為 PNG）。可使用 `System.Drawing` 或 `ImageSharp` 來操作 `args.Stream`。

**Q: 若 Word 文件內含 SVG 或 EMF 圖片該怎麼辦？**  
A: Aspose.Words 會預設將大多數向量格式轉為點陣 PNG。若需要保留原始向量，請設定 `mdOptions.ExportImageResolution`，並依需求處理串流。

**Q: 這在 Linux 上的 .NET Core 能運作嗎？**  
A: 完全可以。只要確保 `resources` 路徑使用正斜線（`/`）或如範例所示使用 `Path.Combine`。請記得 Linux 檔案系統區分大小寫，保持資料夾名稱一致。

**Q: 我要如何隱藏腳註或註解？**  
A: 在儲存之前調整 `mdOptions.ExportFootnotes` 或 `mdOptions.ExportComments` 屬性即可。

---

## 結論

我們剛剛介紹了一個**完整、端對端的 Word 轉換為 Markdown 解決方案**，同時能可靠地**從 docx 中提取圖片**。透過使用 Aspose.Words 的 `MarkdownSaveOptions` 與 `ResourceSavingCallback`，你可以細緻地控制文字轉換與圖片處理。程式碼自給自足，能在任何 .NET 平台上執行，且可輕鬆整合至現有工作流程中。

準備好進一步了嗎？可以考慮自動化批次轉換、將此邏輯整合至 ASP.NET API，或擴充回呼函式為每張提取的圖片產生縮圖。只要核心轉換已穩定，想做什麼都不成問題。

---

![將 Word 轉換為 Markdown 範例](convert-word-to-markdown.png "將 Word 轉換為 Markdown 範例")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}