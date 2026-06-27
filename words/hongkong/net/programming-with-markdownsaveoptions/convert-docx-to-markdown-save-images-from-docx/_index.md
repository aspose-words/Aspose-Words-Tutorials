---
category: general
date: 2026-06-27
description: 使用 Aspose.Words 將 docx 轉換為 markdown 並儲存 docx 中的圖片。了解如何從 Word 檔案提取圖片以及將
  Word 文件匯出為 markdown。
draft: false
keywords:
- convert docx to markdown
- save images from docx
- extract images from word file
- export word document as markdown
language: zh-hant
og_description: 將 docx 轉換為 markdown 並儲存 docx 中的圖片。本指南說明如何從 Word 檔案提取圖片以及將 Word 文件匯出為
  markdown。
og_title: 將 docx 轉換為 markdown 並儲存 docx 中的圖片
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  headline: Convert docx to markdown & save images from docx
  type: TechArticle
- description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  name: Convert docx to markdown & save images from docx
  steps:
  - name: How the code works
    text: '- **Loading the document** (`new Document(inputPath)`) gives us an in‑memory
      representation of the Word file, complete with all its parts—paragraphs, tables,
      and **images**. - **`MarkdownSaveOptions`** is where the magic happens. By attaching
      a `ResourceSavingCallback`, we gain full control over eve'
  - name: Quick sanity check
    text: '- Does the Markdown file open without errors in VS Code’s preview pane?
      ✅ - Are all pictures displayed when you view the file on GitHub? ✅ - Did the
      `Images` directory contain one file per picture from the original `.docx`? ✅'
  - name: What’s next?
    text: '- **Style the Markdown** – add a front‑matter block for Jekyll or Hugo.
      - **Automate the pipeline** – embed this code in an Azure DevOps or GitHub Action
      step. - **Handle tables and footnotes** – explore other `MarkdownSaveOptions`
      flags like `ExportTableBorderStyles`.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Markdown
- Word
title: 將 docx 轉換為 markdown 並從 docx 中儲存圖片
url: /zh-hant/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-save-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 將 docx 轉換為 markdown 並從 docx 儲存圖片

有沒有想過如何 **convert docx to markdown** 而不遺失 Word 檔案中嵌入的圖片？你並不孤單——開發者常常需要一個乾淨的 Markdown 版報告，同時保留每個圖表、標誌或螢幕截圖。

在本教學中，我們將逐步說明一個完整、可直接執行的範例，該範例 **converts a .docx to Markdown**、**saves images from docx** 到您自行選擇的資料夾，並示範如何使用強大的 Aspose.Words 函式庫 **extract images from Word file**。最後，您還會知道如何以單行程式碼 **export Word document as markdown**。

## 您需要的條件

- .NET 6+（或 .NET Framework 4.7.2+）已安裝於您的機器  
- 參考 `Aspose.Words` 的 NuGet 套件（免費試用版亦可）  
- 一個包含至少一張圖片的範例 `input.docx`  
- 您喜歡的 IDE——Visual Studio、Rider，甚至 VS Code 都可以  

不需要額外的第三方工具，也不需要繁瑣的命令列操作。只要純粹的 C# 程式碼。

## Convert docx to markdown – 概觀

核心概念很簡單：

1. 載入來源 Word 文件。  
2. 告訴 Aspose.Words 您希望如何處理外部資源（例如圖片）。  
3. 將文件儲存為 Markdown，讓函式庫負責繁重的工作。

以下是 **完整、可執行的程式**。歡迎將它複製貼上到新的 Console 專案，然後按 `Ctrl+F5`。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load the source document that contains images
        // -----------------------------------------------------------------
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        Document doc = new Document(inputPath);

        // -----------------------------------------------------------------
        // Step 2: Configure Markdown save options with a custom callback
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This callback runs for each external resource (images, CSS, etc.)
            ResourceSavingCallback = (sender, args) =>
            {
                // ---------------------------------------------------------
                // Step 3a: Save images to a custom folder using a unique name
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.Image)
                {
                    string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
                    Directory.CreateDirectory(imageFolder); // ensures folder exists

                    // Use a GUID so we never clash with existing files
                    string uniqueName = Guid.NewGuid().ToString() + args.Extension;
                    args.SavePath = Path.Combine(imageFolder, uniqueName);
                }

                // ---------------------------------------------------------
                // Step 3b: Skip CSS files – they aren't needed for plain Markdown
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.CssStyleSheet)
                    args.Cancel = true;
            }
        };

        // -----------------------------------------------------------------
        // Step 4: Export the document to Markdown, applying the options
        // -----------------------------------------------------------------
        string outputPath = Path.Combine("YOUR_DIRECTORY", "output.md");
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("Conversion complete! Markdown saved to " + outputPath);
        Console.WriteLine("Images extracted to " + Path.Combine("YOUR_DIRECTORY", "Images"));
    }
}
```

### 程式碼運作原理

- **Loading the document** (`new Document(inputPath)`) 為我們提供 Word 檔案的記憶體表示，包含所有部件——段落、表格，以及 **images**。  
- **`MarkdownSaveOptions`** 是魔法發生的地方。透過掛接 `ResourceSavingCallback`，我們可以完全掌控 Aspose.Words 嘗試寫出的每個外部資源。  
- 在回呼函式中，我們透過檢查 `args.ResourceType == ResourceType.Image` 來 **extract images from Word file**。回呼會收到圖片的位元組、原始副檔名，以及我們即時建立的資料夾所設定的 `SavePath` 屬性。使用 `Guid.NewGuid()` 可保證檔名唯一，避免意外覆寫先前的執行結果。  
- 我們 **skip CSS** (`ResourceType.CssStyleSheet`)，因為純 Markdown 不需要樣式表。這樣可保持輸出整潔。  
- 最後，`doc.Save(outputPath, mdOptions)` 會寫入 Markdown 檔案，將 Word 結構替換為相應的 Markdown（標題變成 `#`，表格變成以管線分隔的列，依此類推）。

## Save images from docx – 自訂資料夾策略

為什麼要使用自訂資料夾？想像一下您在為 CI pipeline 產生文件。您希望 Markdown 檔案與其資產並排放置，形成乾淨且可重現的版面配置。

```csharp
string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
Directory.CreateDirectory(imageFolder);
```

幾個 **專業提示**：

- **保持資料夾路徑相對於** 專案根目錄。如此 Markdown 檔案即可使用相對連結引用圖片（`![Alt text](Images/abc123.png)`），在 GitHub、GitLab 或任何靜態網站產生器上皆可正常運作。  
- **如果需要確定性的檔名**（例如，同一張圖片應始終得到相同的檔名），可將 GUID 改為圖片位元組的雜湊值：`MD5.Create().ComputeHash(args.Data)`。這是小幅調整，但對快取相當有用。

## Extract images from Word file – 邊緣情況

1. **多種圖片格式** – Aspose.Words 支援 PNG、JPEG、GIF、BMP，甚至 SVG。`args.Extension` 屬性已包含正確的副檔名，您無需自行猜測。  
2. **非常大的圖片** – 若來源文件包含高解析度照片，產生的檔案可能相當龐大。可考慮在回呼之後加入壓縮步驟，使用 `System.Drawing` 或 `ImageSharp`。  
3. **隱藏圖片** – Word 可能將圖片存於頁首/頁尾或文字方塊中。回呼會看到全部圖片，因此您會 **提取每一張** 圖片，而不僅是可見的。若只想要正文中的圖片，可在 `args.ImageIndex` 上加過濾或檢查 `args.ImageType`。

## Export Word document as markdown – 驗證結果

執行程式後，於任意 Markdown 檢視器開啟 `output.md`。您應該會看到類似以下的內容：

```markdown
# My Report

Here is an introductory paragraph.

![Image1](Images/3f9c2d1e-7a5b-4c9e-9f6a-2b4e5d6f7a8b.png)

More text follows...
```

請注意，圖片連結指向我們建立的 **Images** 資料夾。這正是成功 **export Word document as markdown** 操作的標誌。

### 快速檢查

- Markdown 檔案在 VS Code 的預覽窗格中能否順利開啟？✅  
- 在 GitHub 上檢視檔案時，所有圖片是否都有顯示？✅  
- `Images` 目錄是否包含原始 `.docx` 中每張圖片各一個檔案？✅  

若上述任一檢查失敗，請再次確認 `ResourceSavingCallback` 的邏輯，並確保 `YOUR_DIRECTORY` 佔位符指向可寫入的路徑。

## 常見陷阱與避免方法

| Pitfall | Why it happens | Fix |
|---------|----------------|-----|
| **圖片未顯示** | 回呼未被觸發，因為未指派 `ResourceSavingCallback`。 | 在呼叫 `doc.Save` 之前 **指派** 回呼。 |
| **Images 資料夾為空** | `args.Cancel = true` 不小心對所有資源都設定了。 | 僅取消 CSS (`ResourceType.CssStyleSheet`)，保留圖片不變。 |
| **Windows 上檔案路徑過長** | 使用深層巢狀資料夾加上 GUID 可能超過 260 個字元。 | 保持資料夾層級較淺，或在 Windows 10 以上啟用長路徑支援。 |
| **圖片檔名重複** | 使用 `DateTime.Now.Ticks` 取代 GUID 可能在快速迴圈中產生衝突。 | 使用 `Guid.NewGuid()` 以確保唯一性。 |

## 總結

我們剛剛 **converted docx to markdown**、**saved images from docx**，並示範如何在乾淨且可重複的方式下 **extract images from Word file** 同時 **export Word document as markdown**。整個流程仰賴 Aspose.Words 的 `ResourceSavingCallback`，讓您能細緻控制每個外部資產。

### 接下來做什麼？

- **Style the Markdown** – 為 Jekyll 或 Hugo 加入 front‑matter 區塊。  
- **Automate the pipeline** – 將此程式碼嵌入 Azure DevOps 或 GitHub Action 步驟。  
- **Handle tables and footnotes** – 探索其他 `MarkdownSaveOptions` 旗標，例如 `ExportTableBorderStyles`。  

歡迎自行調整資料夾結構、加入圖片壓縮，甚至透過將 `MarkdownSaveOptions` 換成 `HtmlSaveOptions` 來改為輸出 HTML。只要有堅實的 **convert docx to markdown** 基礎，想做的就沒有限制。

祝編程愉快，願您的文件始終既美觀 **又** 可機器讀取！

## 接下來該學什麼？

以下教學涵蓋與本指南緊密相關的主題，建立在本篇示範的技巧之上。每個資源皆提供完整可執行的程式碼範例與逐步說明，協助您精通更多 API 功能，並在自己的專案中探索替代實作方式。

- [Save Word Images – Convert Word to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Convert Word to Markdown – Embed Images as Base64](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)
- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}